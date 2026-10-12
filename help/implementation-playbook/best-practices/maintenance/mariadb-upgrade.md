---
title: MariaDBのAdobe Commerce アップグレードの前提条件
description: MariaDBを以前のバージョンからアップグレードするようにAdobe Commerce データベースを準備する方法について説明します。
role: Developer
feature: Best Practices
exl-id: b86e471f-e81f-416b-a321-7aa1ac73d27c
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%
---

# MariaDBのアップグレードの前提条件

MariaDBを使用している場合は、クラウドインフラストラクチャ上のAdobe Commerceをアップグレードする前に、データベースソフトウェアをアップグレードする必要がある場合もあります。 例：

- Adobe Commerce 2.4.6 （MariaDB バージョン 10.5.1以降）
- MariaDB バージョン 10.3以前のAdobe Commerce 2.3.5

## Adobe Commerce 2.4.6

MariaDB 10.5.1以降、古い時間形式の列は、`SHOW CREATE TABLE`、`SHOW COLUMNS`、`DESCRIBE` ステートメントの出力および`INFORMATION_SCHEMA.COLUMNS` テーブルの`COLUMN_TYPE`列に`/* mariadb-5.3 */` コメントでマークされます。 [MariaDB ドキュメント &#x200B;](https://mariadb.com/kb/en/datetime/#internal-format)を参照してください。

MariaDB コメントにより、Adobe Commerceで日付列を適切なデータタイプにマッピングできないため、カスタムコードで予期しない動作が発生する可能性があります。

MariaDBを古いバージョンからバージョン 10.6にアップグレードする際の予期しない動作を避けるために、Adobeでは、列を新しい内部形式に移行することをお勧めします。

### デフォルト設定

MariaDB 10.1.2では、MySQL 5.6から新しい時間形式が導入されました。 システム変数`mysql56_temporal_format`を使用すると、alter テーブルの実行時またはデータベースの読み込み時に、データベースが古い日付形式を新しい日付形式に自動的に変換できます。 `mysql56_temporal_format`のデフォルト設定は、クラウドインフラストラクチャ上のAdobe Commerceで常に有効になっています。

### 日付列の移行

次のクエリは、MariaDBを10.5.1以降にアップグレードした後に移行する必要がある影響を受けるテーブルと列を示しています。

```mysql
SELECT * FROM INFORMATION_SCHEMA.`COLUMNS` WHERE TABLE_SCHEMA = DATABASE() AND COLUMN_TYPE LIKE '%mariadb%';
```

列を新しい内部日付形式に移行するには、データベースを再インポートするか、同じ列定義の特定された列でalterを実行する必要があります。 次のクエリは、必要な代替クエリを生成します。

```mysql
SELECT CONCAT( 'ALTER TABLE `', COALESCE(TABLE_NAME), '`', ' MODIFY ', '`', COALESCE(COLUMN_NAME), '`', ' ', COALESCE(DATA_TYPE), ' ', IF(COALESCE(IS_NULLABLE)='YES','NULL', 'NOT NULL'), IF(COLUMN_DEFAULT IS NOT NULL,CONCAT(' DEFAULT ',COLUMN_DEFAULT),' '), ' ', COALESCE(EXTRA), ' COMMENT \'', COALESCE(COLUMN_COMMENT), '\';' ) as sql_query FROM INFORMATION_SCHEMA.`COLUMNS` WHERE TABLE_SCHEMA = DATABASE() AND COLUMN_TYPE LIKE '%mariadb%';
```

>[!NOTE]
>
>予期しない動作を避けるために、新しいコードをデプロイする前に、列を新しい内部日付形式&#x200B;_に移行することが重要です。_

## Adobe Commerce 2.3.5

クラウドインフラストラクチャ上のMariaDB サービスをバージョン 10.0または10.2からバージョン 10.3、10.4、または10.5にアップグレードします。 MariaDB バージョン 10.3以降では、データベースで動的テーブル行フォーマットを使用する必要があり、Adobe CommerceではテーブルにInnoDB ストレージエンジンを使用する必要があります。 この記事では、これらのMariaDB要件に準拠するようにデータベースを更新する方法について説明します。

データベースの準備が完了したら、Adobe Commerce サポートチケットを送信して、Adobe Commerce アップグレードプロセスに進む前に、クラウドインフラストラクチャ上のMariaDB サービスバージョンを更新します。

### アップグレード用にデータベースを準備します

Adobe Commerce サポートチームがアップグレードプロセスを開始する前に、データベーステーブルを変換してデータベースを準備します。

- 行形式を`COMPACT`から`DYNAMIC`に変換
- ストレージ エンジンを`MyISAM`から`InnoDB`に変更します

コンバージョンを計画およびスケジュールする際には、次の点に注意してください。

- テーブル `COMPACT`から`DYNAMIC`に変換するには、大規模なデータベースで数時間かかる場合があります。

- データの破損を防ぐには、ライブサイトでコンバージョン作業を完了しないでください。

- トラフィックが少ない期間にサイトのコンバージョンを促進。

- データベーステーブルを変換するコマンドを実行する前に、サイトを[&#x200B; メンテナンスモード &#x200B;](../../../installation/tutorials/maintenance-mode.md)に切り替えます。

#### データベース テーブルの行の形式を変換

クラスター内の1つのノードのテーブルを変換できます。 変更は、他のサービスノードに自動的にレプリケートされます。

1. Adobe Commerce on cloud infrastructure環境から、SSHを使用してnode 1に接続します。

1. MariaDBにログインします。

1. コンパクト形式から動的形式に変換するテーブルを指定します。

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. コンバージョン作業をスケジュールできるように、テーブルサイズを決定します。

   ```mysql
   SELECT table_schema as 'Database', table_name AS 'Table', round(((data_length + index_length) / 1024 / 1024), 2) 'Size in MB' FROM information_schema.TABLES ORDER BY (data_length + index_length) DESC;
   ```

   大きなテーブルの場合、変換に時間がかかります。 表を確認し、優先順位と表サイズで変換作業をバッチ化して、必要なメンテナンスウィンドウを計画するのに役立ちます。

1. すべてのテーブルを1つずつ動的フォーマットに変換します。

   ```mysql
   ALTER TABLE [ table name here ] ROW_FORMAT=DYNAMIC;
   ```

#### データベース テーブル ストレージ形式の変換

クラスター内の1つのノードのテーブルを変換できます。 変更は、他のサービスノードに自動的にレプリケートされます。

Adobe Commerce Starter プロジェクトとAdobe Commerce Pro プロジェクトでは、ストレージ形式を変換するプロセスが異なります。

- スターターアーキテクチャの場合は、MySQL `ALTER` コマンドを使用して形式を変換します。
- Pro アーキテクチャでは、MySQL `CREATE`および`SELECT` コマンドを使用して、`InnoDB` ストレージを含むデータベーステーブルを作成し、既存のテーブルから新しいテーブルにデータをコピーします。 この方法では、変更がクラスター内のすべてのノードに確実にレプリケートされます。

**Adobe Commerce Pro プロジェクト用にテーブルのストレージ形式を変換**

1. `MyISAM` ストレージを使用するテーブルを識別します。

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. すべてのテーブルを1つずつ`InnoDB` ストレージ形式に変換します。

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


**Adobe Commerce スタータープロジェクト用のテーブルストレージ形式の変換**

1. `MyISAM` ストレージを使用するテーブルを識別します。

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. `MyISAM` ストレージを使用するテーブルを`InnoDB` ストレージに変換します。

   ```mysql
   ALTER TABLE [ table name here ] ENGINE=InnoDB;
   ```

#### データベースの変換を確認する

MariaDB バージョン 10.3、10.4、または10.6への予定されたアップグレードの前日に、すべてのテーブルに正しい行形式とストレージエンジンがあることを確認します。 変換を完了した後にコードをデプロイすると、一部のテーブルが元の設定に戻される場合があるため、検証が必要です。

1. データベースにログインします。

1. `COMPACT`行形式が引き続き存在するテーブルを確認します。

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. まだ`MyISAM` ストレージ形式を使用しているテーブルを確認します

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. テーブルが元に戻された場合は、手順を繰り返して、テーブルの行の形式とストレージエンジンを変更します。

### ストレージエンジンの変更

[MyISAM テーブルをInnoDB](../planning/database-on-cloud.md)に変換するを参照してください。
