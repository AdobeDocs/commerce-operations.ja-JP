---
title: Adobe Commerce 2.3.5 MariaDB のアップグレードの前提条件
description: Adobe Commerce 2.3.5 からアップグレードするためのAdobe Commerceデータベースの準備方法を説明します。
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 1abe86197de68336e10c50cab7ad38eebb098aeb
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---


# Adobe Commerce 2.3.5 アップグレードの前提条件

この記事では、バージョン 2.3.4 以前からAdobe Commerce 2.3.5 にアップグレードする際にデータベースを準備する方法について説明します。

このアップグレードでは、サポートチームがAdobe Commerceの要件を満たすために、クラウドインフラストラクチャ上の MariaDB を MariaDB 10.0 から 10.2 にアップグレードする必要があります。 Adobe Commerceバージョン 2.3.5 以降。

## 影響を受ける製品およびバージョン

Adobe Commerceバージョン 2.3.4 以前および MariaDB バージョン 10.0 以前を含む、クラウドインフラストラクチャ上のAdobe Commerce。

## アップグレード用のデータベースの準備

Adobe Commerceサポートチームがアップグレードプロセスを開始する前に、データベースを準備する必要があります。そのためには、以下の場所にあるすべてのテーブルの形式を変換します。 `COMPACT` から `DYNAMIC`. また、次のストレージエンジンタイプを変換する必要があります： `MyISAM` から `InnoDB`.

データベースを変換するプランとスケジュールを作成する際は、次のガイドラインに従ってください。

- 変換元 `COMPACT` から `DYNAMIC` 大規模なデータベースの場合、テーブルには数時間かかる場合があります。

- データの破損を防ぐには、サイトがライブ状態のときに変換を実行しないでください。

- サイトのトラフィックが少ない期間に、コンバージョン作業を完了します。

- サイトの切り替え先 [メンテナンスモード](../../../installation/tutorials/maintenance-mode.md) 実行前 `ALTER` コマンド

### データベーステーブルの変換

クラスター内の 1 つのノードでテーブルを変換できます。 変更は、クラスター内の他のコアノードにレプリケートされます。

1. クラウドインフラストラクチャ環境のAdobe Commerceから、SSH を使用してノード 1 に接続します。

1. MariaDB にログインします。

1. テーブル形式を変換します。

   - コンパクトからダイナミックフォーマットに変換するテーブルを指定します。

      ```mysql
      SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format 'Compact';
      ```

   - 表のサイズを決定して、変換処理のスケジュールを設定します。

      ```mysql
      SELECT table_schema as 'Database', table_name AS 'Table', round(((data_length + index_length) / 1024 / 1024), 2) 'Size in MB' FROM information_schema.TABLES ORDER BY (data_length + index_length) DESC;
      ```

      大きいテーブルは、変換に時間がかかります。 必要なメンテナンスウィンドウのタイミングを計画するために、テーブルのバッチをどの順序で変換するかに関して、サイトをメンテナンスモードに切り替えたり、サイトから切り替えたりする際には、適切に計画を立てる必要があります

   - すべてのテーブルを一度に 1 つずつ動的形式に変換します。

      ```mysql
      ALTER TABLE [ table name here ] ROW_FORMAT=DYNAMIC;
      ```

1. テーブルストレージエンジンを更新します。

   - 使用するテーブルの識別 `MyISAM` ストレージ。

      ```mysql
      SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
      ```

   - 使用するテーブルを変換 `MyISAM` ～への保管 `InnoDB` ストレージ。

      ```mysql
      ALTER TABLE [ table name here ] ENGINE=InnoDB;
      ```

1. 変換処理を確認します。

   変換処理の完了後に行ったコードデプロイメントによって、一部のテーブルが元の設定に戻る場合があるので、この手順が必要です。

   - MariaDB バージョン 10.2 へのスケジュールされたアップグレードの前日に、データベースにログインし、クエリを実行して形式とストレージエンジンを確認します。

      ```mysql
      SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
      ```

      ```mysql
      SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
      ```

   - テーブルが元に戻されている場合は、手順を繰り返して、テーブルフォーマットとストレージエンジンを変更します。

## 追加情報

[クラウドインフラストラクチャ上のAdobe Commerceのデータベースのベストプラクティス](../planning/database-on-cloud.md)
