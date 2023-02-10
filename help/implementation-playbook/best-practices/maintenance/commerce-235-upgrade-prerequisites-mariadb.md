---
title: Adobe Commerce 2.3.5 MariaDB のアップグレードの前提条件
description: Adobe Commerce 2.3.5 からアップグレードするためのAdobe Commerceデータベースの準備方法を説明します。
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: bc38dd658401d3cd4c64159b1b2b2efe89979a93
workflow-type: tm+mt
source-wordcount: '641'
ht-degree: 0%

---


# MariaDB のアップグレードの前提条件

Adobe Commerce 2.3.4 以前から新しいバージョンにアップグレードするには、クラウドインフラストラクチャ上の MariaDB サービスをバージョン 10.0 または 10.2 からバージョン 10.3 または 10.4 にアップグレードする必要があります。 この記事では、MariaDB の要件に準拠するようにデータベースを更新する方法を説明します。

データベースを準備したら、Adobe Commerceサポートチケットを送信して、Adobe Commerceのアップグレードプロセスに進む前に、クラウドインフラストラクチャ上の MariaDB サービスのバージョンを更新します。

## 影響を受ける製品およびバージョン

Adobe Commerceバージョン 2.3.4 以前および MariaDB バージョン 10.0 以前を含む、クラウドインフラストラクチャ上のAdobe Commerce。

## アップグレード用のデータベースの準備

Adobe Commerceサポートチームがアップグレードプロセスを開始する前に、データベーステーブルを変換してデータベースを準備します。

- 行の形式の変換元 `COMPACT` から `DYNAMIC`
- 次のストレージエンジンを変更： `MyISAM` から `InnoDB`

変換を計画およびスケジュールする際は、次の点に注意してください。

- 変換元 `COMPACT` から `DYNAMIC` 大規模なデータベースの場合、テーブルには数時間かかる場合があります。

- データの破損を防ぐには、実稼働サイトで変換作業を完了しないでください。

- サイトのトラフィックが少ない期間に、コンバージョン作業を完了します。

- サイトの切り替え先 [メンテナンスモード](../../../installation/tutorials/maintenance-mode.md) データベーステーブルを変換するコマンドを実行する前に、次の手順を実行します。

### データベーステーブルの行形式を変換

クラスター内の 1 つのノードでテーブルを変換できます。 変更は、他のサービスノードに自動的にレプリケートされます。

1. クラウドインフラストラクチャ環境のAdobe Commerceから、SSH を使用してノード 1 に接続します。

1. MariaDB にログインします。

1. コンパクトからダイナミックフォーマットに変換するテーブルを指定します。

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. 表のサイズを決定して、変換処理のスケジュールを設定します。

   ```mysql
   SELECT table_schema as 'Database', table_name AS 'Table', round(((data_length + index_length) / 1024 / 1024), 2) 'Size in MB' FROM information_schema.TABLES ORDER BY (data_length + index_length) DESC;
   ```

   大きいテーブルは、変換に時間がかかります。 テーブルを確認し、優先度とテーブルサイズで変換作業をバッチ処理して、必要なメンテナンスウィンドウの計画に役立てます。

1. すべてのテーブルを一度に 1 つずつ動的形式に変換します。

   ```mysql
   ALTER TABLE [ table name here ] ROW_FORMAT=DYNAMIC;
   ```

### データベーステーブルストレージ形式の変換

クラスター内の 1 つのノードでテーブルを変換できます。 変更は、他のサービスノードに自動的にレプリケートされます。

ストレージ形式の変換プロセスは、Adobe Commerce Starter プロジェクトとAdobe Commerce Pro プロジェクトで異なります。

- スターターアーキテクチャの場合は、MySQL を使用します。 `ALTER` コマンドを使用して形式を変換します。
- Pro アーキテクチャでは、MySQL を使用します。 `CREATE` および `SELECT` を使用してデータベーステーブルを作成するコマンド `InnoDB` データを保存し、既存のテーブルから新しいテーブルにコピーします。 このメソッドは、変更がクラスター内のすべてのノードにレプリケートされることを保証します。

**Adobe Commerce Pro プロジェクト用のテーブルストレージ形式の変換**

1. 使用するテーブルの識別 `MyISAM` ストレージ。

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. すべてのテーブルの変換先 `InnoDB` ストレージフォーマットを一度に 1 つずつ。

   - 名前の競合を防ぐために、既存のテーブルの名前を変更します。

      ```mysql
      RENAME TABLE <existing_table> <table_old>;
      ```

   - を使用するテーブルの作成 `InnoDB` 既存のテーブルのデータを使用したストレージ。

      ```mysql
      CREATE TABLE <existing_table> ENGINE=InnoDB SELECT * from <table_old>;
      ```

   - 新しいテーブルに必要なデータがすべて含まれていることを確認します。

   - 名前を変更した元のテーブルを削除します。


**Adobe Commerce Starter プロジェクト用のテーブルストレージ形式の変換**

1. 使用するテーブルの識別 `MyISAM` ストレージ。

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. 使用するテーブルを変換 `MyISAM` ～への保管 `InnoDB` ストレージ。

   ```mysql
   ALTER TABLE [ table name here ] ENGINE=InnoDB;
   ```

### データベース変換の検証

MariaDB バージョン 10.2 へのスケジュールされたアップグレードの前日に、すべてのテーブルに正しい行フォーマットとストレージエンジンが含まれていることを確認します。 変換処理の完了後にコードをデプロイすると、一部のテーブルが元の設定に戻る場合があるので、検証が必要です。

1. データベースにログインします。

1. まだ `COMPACT` 行の書式。

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. まだ `MyISAM` ストレージ形式

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. テーブルが元に戻されている場合は、手順を繰り返して、テーブル行のフォーマットとストレージエンジンを変更します。

## ストレージエンジンの変更

詳しくは、 [MyISAM テーブルを InnoDB に変換](../planning/database-on-cloud.md).

## 追加情報

- [クラウドインフラストラクチャ上のAdobe Commerceのデータベースのベストプラクティス](../planning/database-on-cloud.md)
- [Cloud 上のAdobe Commerceの MariaDB を 10.0 から 12.0 に更新しました。](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/upgrade-mariadb-10.0-to-10.2-for-magento-commerce-cloud.html)

