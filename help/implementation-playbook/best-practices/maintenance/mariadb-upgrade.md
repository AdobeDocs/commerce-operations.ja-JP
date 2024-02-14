---
title: Adobe Commerce MariaDB のアップグレードの前提条件
description: MariaDB を以前のバージョンからアップグレードするためのAdobe Commerceデータベースの準備方法を説明します。
role: Developer
feature: Best Practices
exl-id: b86e471f-e81f-416b-a321-7aa1ac73d27c
source-git-commit: fb449f0ee7d503d0c7ba60bf6bfbe3f528060606
workflow-type: tm+mt
source-wordcount: '865'
ht-degree: 0%

---


# MariaDB のアップグレードの前提条件

クラウドインフラストラクチャ上のAdobe Commerceをアップグレードする前に、MariaDB を使用している場合は、データベースソフトウェアのアップグレードも必要になる場合があります。 例：

- Adobe Commerce 2.4.6（MariaDB バージョン 10.5.1 以降を使用）
- Adobe Commerce 2.3.5（MariaDB バージョン 10.3 以前）

## Adobe Commerce 2.4.6

MariaDB 10.5.1 以降、古い一時形式の列は、 `/* mariadb-5.3 */` 出力内のコメント `SHOW CREATE TABLE`, `SHOW COLUMNS`, `DESCRIBE` ステートメント、および `COLUMN_TYPE` 列 `INFORMATION_SCHEMA.COLUMNS` 表。 [MariaDB のドキュメントを参照してください。](https://mariadb.com/kb/en/datetime/#internal-format).

Adobe Commerceは、MariaDB コメントが原因で、日付列を適切なデータ型にマッピングできません。カスタムコードで予期しない動作が発生する可能性があります。

MariaDB を古いバージョンからバージョン 10.6 にアップグレードする際の予期しない動作を避けるため、Adobeでは列を新しい内部形式に移行することをお勧めします。

### デフォルトの設定

MariaDB 10.1.2 では、MySQL 5.6 から新しい一時形式が導入されました。The `mysql56_temporal_format` システム変数を使用すると、alter テーブルの実行時やデータベースのインポート時に、古い日付形式を新しい形式に自動的に変換できます。 のデフォルト設定 `mysql56_temporal_format` は、クラウドインフラストラクチャ上のAdobe Commerceで常に有効になっています。

### 日付列を移行

次のクエリは、MariaDB を 10.5.1 以降にアップグレードした後に移行する必要がある、影響を受けるテーブルと列を示しています。

```mysql
SELECT * FROM INFORMATION_SCHEMA.`COLUMNS` WHERE TABLE_SCHEMA = DATABASE() AND COLUMN_TYPE LIKE '%mariadb%';
```

列を新しい内部日付フォーマットに移行するには、データベースを再インポートするか、同じ列定義を持つ識別された列で alter を実行する必要があります。 次のクエリは、必要な alter クエリを生成します。

```mysql
SELECT CONCAT( 'ALTER TABLE `', COALESCE(TABLE_NAME), '`', ' MODIFY ', '`', COALESCE(COLUMN_NAME), '`', ' ', COALESCE(DATA_TYPE), ' ', IF(COALESCE(IS_NULLABLE)='YES','NULL', 'NOT NULL'), IF(COLUMN_DEFAULT IS NOT NULL,CONCAT(' DEFAULT ',COLUMN_DEFAULT),' '), ' ', COALESCE(EXTRA), ' COMMENT \'', COALESCE(COLUMN_COMMENT), '\';' ) as sql_query FROM INFORMATION_SCHEMA.`COLUMNS` WHERE TABLE_SCHEMA = DATABASE() AND COLUMN_TYPE LIKE '%mariadb%';
```

>[!NOTE]
>
>列を新しい内部日付形式に移行することが重要です _前_ 新しいコードをデプロイして、予期しない動作を回避すること。

## Adobe Commerce 2.3.5

クラウドインフラストラクチャ上の MariaDB サービスをバージョン 10.0 または 10.2 からバージョン 10.3、10.4、10.5 にアップグレードします。MariaDB バージョン 10.3 以降では、データベースで動的テーブル行形式を使用する必要があり、Adobe Commerceではテーブルに InnoDB ストレージエンジンを使用します。 この記事では、MariaDB の要件に準拠するようにデータベースを更新する方法を説明します。

データベースを準備したら、Adobe Commerceサポートチケットを送信して、Adobe Commerceのアップグレードプロセスに進む前に、クラウドインフラストラクチャ上の MariaDB サービスのバージョンを更新します。

### アップグレード用のデータベースの準備

Adobe Commerceサポートチームがアップグレードプロセスを開始する前に、データベーステーブルを変換してデータベースを準備します。

- 行の形式の変換元 `COMPACT` から `DYNAMIC`
- 次のストレージエンジンを変更： `MyISAM` から `InnoDB`

変換を計画およびスケジュールする際は、次の点に注意してください。

- 変換元 `COMPACT` から `DYNAMIC` 大規模なデータベースの場合、テーブルには数時間かかる場合があります。

- データの破損を防ぐには、実稼働サイトで変換作業を完了しないでください。

- サイトのトラフィックが少ない期間に、コンバージョン作業を完了します。

- サイトの切り替え先 [メンテナンスモード](../../../installation/tutorials/maintenance-mode.md) データベーステーブルを変換するコマンドを実行する前に、次の手順を実行します。

#### データベーステーブルの行形式を変換

クラスター内の 1 つのノードでテーブルを変換できます。 変更は、他のサービスノードに自動的にレプリケートされます。

1. クラウドインフラストラクチャ環境のAdobe Commerceから、SSH を使用してノード 1 に接続します。

1. MariaDB にログインします。

1. コンパクト形式からダイナミック形式に変換するテーブルを指定します。

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

#### データベーステーブルストレージ形式の変換

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

1. 使用するテーブルを変換する `MyISAM` ～への保管 `InnoDB` ストレージ。

   ```mysql
   ALTER TABLE [ table name here ] ENGINE=InnoDB;
   ```

#### データベース変換の検証

MariaDB バージョン 10.3、10.4、または 10.6 へのスケジュールされたアップグレードの前日に、すべてのテーブルに正しい行フォーマットとストレージエンジンが含まれていることを確認します。 変換処理の完了後にコードをデプロイすると、一部のテーブルが元の設定に戻る場合があるので、検証が必要です。

1. データベースにログインします。

1. まだ `COMPACT` 行の書式を設定します。

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. まだ `MyISAM` ストレージ形式

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. テーブルが元に戻されている場合は、手順を繰り返して、テーブル行のフォーマットとストレージエンジンを変更します。

### ストレージエンジンの変更

詳しくは、 [MyISAM テーブルを InnoDB に変換](../planning/database-on-cloud.md).
