---
title: MariaDB のAdobe Commerce アップグレードの前提条件
description: Adobe Commerce データベースを準備して、以前のバージョンから MariaDB をアップグレードする方法を説明します。
role: Developer
feature: Best Practices
exl-id: b86e471f-e81f-416b-a321-7aa1ac73d27c
source-git-commit: fb449f0ee7d503d0c7ba60bf6bfbe3f528060606
workflow-type: tm+mt
source-wordcount: '865'
ht-degree: 0%

---


# MariaDB のアップグレードの前提条件

MariaDB を使用している場合は、クラウドインフラストラクチャー上のAdobe Commerceをアップグレードする前に、データベースソフトウェアをアップグレードする必要がある場合もあります。 例：

- Adobe Commerce 2.4.6 （MariaDB バージョン 10.5.1 以降）
- Adobe Commerce 2.3.5 と MariaDB バージョン 10.3 以前

## Adobe Commerce 2.4.6

MariaDB 10.5.1 以降、古いテンポラル形式の列は、`SHOW CREATE TABLE`、`SHOW COLUMNS`、`DESCRIBE` 文の出力および `INFORMATION_SCHEMA.COLUMNS` テーブルの `COLUMN_TYPE` 列に `/* mariadb-5.3 */` コメントでマークされます。 [MariaDB ドキュメントを参照してください ](https://mariadb.com/kb/en/datetime/#internal-format)。

MariaDB コメントが原因で、Adobe Commerceが日付列を適切なデータタイプにマッピングできず、カスタムコードで予期しない動作が起こる可能性があります。

MariaDB を旧バージョンからバージョン 10.6 にアップグレードする際の予期しない動作を避けるために、Adobeでは列を新しい内部フォーマットに移行することをお勧めします。

### デフォルトの設定

MariaDB 10.1.2 では、MySQL 5.6 から新しい時間形式が導入されました。`mysql56_temporal_format` システム変数を使用すると、alter table の実行時またはデータベースのインポート時に、データベースで古い日付形式を新しい日付形式に自動的に変換できます。 `mysql56_temporal_format` のデフォルト設定は、クラウドインフラストラクチャー上のAdobe Commerceで常に有効になっています。

### 日付列を移行

次のクエリは、MariaDB を 10.5.1 以降にアップグレードした後に移行する必要がある、影響を受けるテーブルと列を示しています。

```mysql
SELECT * FROM INFORMATION_SCHEMA.`COLUMNS` WHERE TABLE_SCHEMA = DATABASE() AND COLUMN_TYPE LIKE '%mariadb%';
```

列を新しい内部日付形式に移行するには、データベースを再インポートするか、同じ列定義で識別された列で alter を実行する必要があります。 次のクエリは、必要な変更クエリを生成します。

```mysql
SELECT CONCAT( 'ALTER TABLE `', COALESCE(TABLE_NAME), '`', ' MODIFY ', '`', COALESCE(COLUMN_NAME), '`', ' ', COALESCE(DATA_TYPE), ' ', IF(COALESCE(IS_NULLABLE)='YES','NULL', 'NOT NULL'), IF(COLUMN_DEFAULT IS NOT NULL,CONCAT(' DEFAULT ',COLUMN_DEFAULT),' '), ' ', COALESCE(EXTRA), ' COMMENT \'', COALESCE(COLUMN_COMMENT), '\';' ) as sql_query FROM INFORMATION_SCHEMA.`COLUMNS` WHERE TABLE_SCHEMA = DATABASE() AND COLUMN_TYPE LIKE '%mariadb%';
```

>[!NOTE]
>
>予期しない動作を避けるために、新しいコードをデプロイする _前_ に、列を新しい内部日付形式に移行することが重要です。

## Adobe Commerce 2.3.5

クラウドインフラストラクチャー上の MariaDB サービスをバージョン 10.0 または 10.2 からバージョン 10.3、10.4 または 10.5 にアップグレードします。MariaDB バージョン 10.3 以降では、動的テーブル行形式を使用するようにデータベースを必要とし、Adobe Commerceでは、テーブル用に InnoDB ストレージエンジンを使用する必要があります。 この記事では、これらの MariaDB 要件に準拠するようにデータベースを更新する方法について説明します。

データベースを準備したら、Adobe Commerceのアップグレードプロセスに進む前に、Adobe Commerce サポートチケットを送信して、クラウドインフラストラクチャ上の MariaDB サービスバージョンを更新します。

### アップグレード用にデータベースを準備

Adobe Commerce サポートチームがアップグレードプロセスを開始する前に、データベーステーブルを変換してデータベースを準備します。

- 行形式を `COMPACT` から `DYNAMIC` に変換します
- ストレージエンジンを `MyISAM` から `InnoDB` に変更します

コンバージョンを計画およびスケジュールする際は、次の点に注意してください。

- 大規模なデータベースでは、`COMPACT` テーブルから `DYNAMIC` テーブルへの変換に数時間かかる場合があります。

- データの破損を防ぐには、ライブサイトでコンバージョン作業を完了しないようにします。

- サイトのトラフィックが少ない時間帯にコンバージョン作業を完了します。

- データベーステーブルを変換するコマンドを実行する前に、サイトを [ メンテナンスモード ](../../../installation/tutorials/maintenance-mode.md) に切り替えます。

#### データベース テーブル行の形式を変換する

クラスター内の 1 つのノードでテーブルを変換できます。 変更内容は、他のサービスノードに自動的にレプリケートされます。

1. クラウドインフラストラクチャー上のAdobe Commerceから、SSH を使用して Node 1 に接続します。

1. MariaDB にログインします。

1. コンパクト形式から動的形式に変換するテーブルを特定します。

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. 変換作業をスケジュールできるように、テーブルサイズを決定します。

   ```mysql
   SELECT table_schema as 'Database', table_name AS 'Table', round(((data_length + index_length) / 1024 / 1024), 2) 'Size in MB' FROM information_schema.TABLES ORDER BY (data_length + index_length) DESC;
   ```

   テーブルが大きいと、変換に時間がかかります。 テーブルをレビューし、優先度別およびテーブルサイズ別に変換作業をバッチ化して、必要なメンテナンスウィンドウを計画するのに役立ちます。

1. すべてのテーブルを 1 つずつ動的形式に変換します。

   ```mysql
   ALTER TABLE [ table name here ] ROW_FORMAT=DYNAMIC;
   ```

#### データベーステーブルのストレージ形式の変換

クラスター内の 1 つのノードでテーブルを変換できます。 変更内容は、他のサービスノードに自動的にレプリケートされます。

ストレージ形式を変換するプロセスは、Adobe Commerce Starter とAdobe Commerce Pro プロジェクトで異なります。

- スターターアーキテクチャの場合は、MySQL `ALTER` コマンドを使用して形式を変換します。
- Pro アーキテクチャでは、MySQL `CREATE` および `SELECT` コマンドを使用して、`InnoDB` ストレージを含むデータベーステーブルを作成し、既存のテーブルから新しいテーブルにデータをコピーします。 この方法では、変更がクラスター内のすべてのノードに確実にレプリケートされます。

**Adobe Commerce Pro プロジェクトのテーブルストレージフォーマットの変換**

1. `MyISAM` ストレージを使用するテーブルを識別します。

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. すべてのテーブル `InnoDB` 一度に 1 つずつストレージ形式に変換します。

   - 名前の競合を防ぐために、既存のテーブルの名前を変更します。

     ```mysql
     RENAME TABLE <existing_table> <table_old>;
     ```

   - 既存のテーブルのデータを使用して、`InnoDB` ストレージを使用するテーブルを作成します。

     ```mysql
     CREATE TABLE <existing_table> ENGINE=InnoDB SELECT * from <table_old>;
     ```

   - 新しいテーブルに必要なデータがすべて含まれていることを確認します。

   - 名前を変更した元のテーブルを削除します。


**Adobe Commerce スタータープロジェクトのテーブルストレージ形式の変換**

1. `MyISAM` ストレージを使用するテーブルを識別します。

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. `MyISAM` ストレージを使用するテーブルを `InnoDB` ストレージに変換します。

   ```mysql
   ALTER TABLE [ table name here ] ENGINE=InnoDB;
   ```

#### データベース変換の検証

MariaDB バージョン 10.3、10.4、または 10.6 への予定アップグレードの前日に、すべてのテーブルのロー形式とストレージ・エンジンが正しいことを確認します。 検証が必要なのは、変換が完了した後にコードのデプロイメントを行うと、一部のテーブルが元の設定に戻る場合があるためです。

1. データベースにログインします。

1. `COMPACT` 行の形式がまだ残っているテーブルを確認します。

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. `MyISAM` ストレージ形式をまだ使用しているテーブルがないかどうかを確認します

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. テーブルが元に戻された場合は、手順を繰り返してテーブル行の形式とストレージエンジンを変更します。

### ストレージエンジンの変更

[MyISAM テーブルの InnoDB への変換 ](../planning/database-on-cloud.md) を参照してください。
