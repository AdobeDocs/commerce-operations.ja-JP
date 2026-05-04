---
title: MySQL ガイドライン
description: Adobe Commerceのオンプレミスインストール用にMySQLとMariaDBをインストールして設定するには、次の手順に従います。
exl-id: dc5771a8-4066-445c-b1cd-9d5f449ec9e9
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '1177'
ht-degree: 0%

---

# 一般的なMySQL ガイドライン

サポートされているバージョンのMySQLについては、[必要システム構成](../../system-requirements.md)を参照してください。

Adobe _strongly_&#x200B;では、データベースを設定する際に、次の標準に従うことをお勧めします。

* Adobe Commerceでは、インデックス再作成時のデータベースアクセスを向上させるために[MySQL データベーストリガー](https://dev.mysql.com/doc/refman/8.4/en/triggers.html)を使用しています。 これらは、インデクサーモードが[&#x200B; スケジュール &#x200B;](../../../configuration/cli/manage-indexers.md#configure-indexers)に設定されている場合に作成されます。 カスタムトリガーは、将来のAdobe Commerce バージョンとの互換性が失われる可能性があるため、データベース内のカスタムトリガーはサポートされません。
* 続行する前に、[これらの潜在的なMySQL トリガーの制限事項](https://dev.mysql.com/doc/refman/8.4/en/stored-program-restrictions.html)を確認してください。
* データベースのセキュリティ体制を強化するには、[`STRICT_ALL_TABLES`](https://dev.mysql.com/doc/refman/8.4/en/sql-mode.html#sqlmode_strict_all_tables) SQL モードを有効にして、無効なデータ値を保存しないようにします。これにより、データベースの不要なインタラクションが発生する可能性があります。
* Adobe Commerceでは、_not_&#x200B;はMySQL ステートメント ベースのレプリケーションをサポートしていません。 _only_ [行ベースのレプリケーション &#x200B;](https://dev.mysql.com/doc/refman/8.4/en/replication-formats.html)を使用していることを確認してください。

>[!WARNING]
>
>Adobe Commerceは現在、トランザクション内で`CREATE TEMPORARY TABLE` ステートメントを使用しています。トランザクション内では[互換性がありません](https://dev.mysql.com/doc/refman/8.4/en/replication-gtids-restrictions.html)。データベース実装では、[Google Cloud SQLの第2世代インスタンス &#x200B;](https://docs.cloud.google.com/sql/docs/features#differences)など、GTID ベースのレプリケーションを使用しています。 MySQL for Cloud SQL 8.0を代替手段として検討してください。

>[!NOTE]
>
>Web サーバーとデータベース サーバーが異なるホスト上にある場合は、このトピックで説明したタスクをデータベース サーバー上で実行し、[&#x200B; リモート MySQL データベース接続の設定](mysql-remote.md)を参照してください。

## UbuntuでのMySQLのインストール

Adobe Commerce 2.4は、インストールするリリースに応じて、異なるMySQL 8 バージョンをサポートしています。 [必要システム構成](../../system-requirements.md)に記載されているバージョンを使用し、次のリンクに従って、お使いのコンピューターにMySQLをインストールする手順を確認してください。

* [Ubuntu](https://ubuntu.com/server/docs/databases-mysql/)
* [CentOS](https://dev.mysql.com/doc/refman/8.4/en/linux-installation-yum-repo.html)

大量の製品をインポートする場合は、[`max_allowed_packet`](https://dev.mysql.com/doc/refman/8.4/en/server-system-variables.html#sysvar_max_allowed_packet)の値をデフォルトの16 MBよりも大きい値に増やすことができます。

>[!NOTE]
>
>デフォルト値は、クラウドインフラストラクチャ _および_&#x200B;のオンプレミスプロジェクトのAdobe Commerceに適用されます。 Adobe Commerce on cloud infrastructure Proのお客様は、`max_allowed_packet`の値を増やすためにサポートチケットを開く必要があります。 Adobe Commerce on cloud infrastructure Starterのお客様は、`/etc/mysql/mysql.cnf` ファイルの設定を更新することで、値を増やすことができます。

値を増やすには、テキストエディターで`/etc/mysql/mysql.cnf` ファイルを開き、`max_allowed_packet`の値を見つけます。 `mysql.cnf` ファイルに変更を保存し、テキストエディターを閉じて、MySQL （`service mysql restart`）を再起動します。

オプションで設定した値を確認するには、`mysql>` プロンプトで次のコマンドを入力します。

```sql
SHOW VARIABLES LIKE 'max_allowed_packet';
```

次に、[&#x200B; データベースインスタンスを設定します](#configuring-the-database-instance)。

## MySQL 8の変更

Adobe Commerce 2.4では、MySQL 8のサポートが追加されました。
この節では、開発者が認識すべきMySQL 8の主な変更点について説明します。

### 整数型の幅を削除しました（パディング）

整数データ型（TINYINT、SMALLINT、MEDIUMINT、INT、BIGINT）の表示幅仕様は、MySQL 8.0.17で廃止されました。 出力にデータ型定義を含むステートメントでは、TINYINT （1）を除き、整数型の表示幅が表示されなくなりました。 MySQL コネクタは、TINYINT （1）列がBOOLEAN列として始まったと仮定します。 この例外は、彼らがその仮定を作り続けることを可能にします。

#### 例

mysql 8.19でのadmin_userの説明

| フィールド | タイプ | Null | キー | Default | Extra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| user\_id | `int unsigned` | いいえ | PRI | `NULL` | `auto_increment` |
| `firstname` | `varchar(32)` | はい | | `NULL` | |
| `lastname` | `varchar(32`) | はい | | `NULL` | |
| `email` | `varchar(128)` | はい | | `NULL` | |
| `username` | `varchar(40)` | はい | UNI | `NULL` | |
| `password` | `varchar(255)` | いいえ | | `NULL` | |
| `created` | `timestamp` | いいえ | | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` |
| `modified` | `timestamp` | いいえ | | `CURRENT_TIMESTAMP` | 更新`CURRENT_TIMESTAMP`の`DEFAULT_GENERATED` |
| `logdate` | `timestamp` | はい | | `NULL` | |
| `lognum` | `smallint unsigned` | いいえ | | `0` | |

_TINYINT （1）_&#x200B;を除き、すべての整数パディング （TINYINT > 1、SMALLINT、MEDIUMINT、INT、BIGINT）を`db_schema.xml` ファイルから削除する必要があります。

詳しくは、[https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature](https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature)を参照してください。

### ビヘイビアーによるデフォルトの順序

8.0以前は、エントリは外部キーでソートされていました。 デフォルトの並べ替え順序は、使用するエンジンによって異なります。
コードが特定のソートに依存する場合は、常にソート順序を指定します。

### GROUP BYのASCおよびDESC修飾子は非推奨

MySQL 8.0.13の時点で、`GROUP BY`句の非推奨の`ASC`または`DESC`修飾子が削除されました。 以前に`GROUP BY`の並べ替えに依存していたクエリは、以前のMySQL バージョンとは異なる結果を生成する可能性があります。 指定された並べ替え順序を生成するには、`ORDER BY`句を指定します。

## CommerceとMySQL 8

MySQL 8を適切にサポートするために、Adobe Commerceにいくつかの変更がありました。

### クエリと挿入の動作

Adobe Commerceは、`/lib/internal/Magento/Framework/DB/Adapter/Pdo/Mysql.php:424.`でSET SQL_MODE=&quot;を設定することにより、通常の検証動作を無効にしました。 検証を無効にすると、MySQLでデータが切り捨てられる可能性があります。 MySQLでは、クエリの動作が変更されました。IP アドレスが整数ではなく文字列として正しく表示されるようになったため、`Select * on my_table where IP='127.0.0.1'`は結果を返しません。

## MySQL 5.7からMySQL 8へのアップグレード

MySQLをバージョン 5.7からバージョン 8に正しく更新するには、次の手順に従う必要があります。

1. Adobe Commerceを2.4.0にアップグレードします。
あらゆる要素をテストし、システムが期待通りに動作することを確認します。
1. メンテナンスモードを有効にする：

   ```shell
   bin/magento maintenance:enable
   ```

1. データベースのバックアップを作成します。

   ```shell
   bin/magento setup:backup --db
   ```

1. MySQLをバージョン 8に更新します。
1. バックアップしたデータをMySQLにインポートします。
1. キャッシュをクリーニングします。

   ```shell
   bin/magento cache:clean
   ```

1. メンテナンスモードを無効にする：

   ```shell
   bin/magento maintenance:disable
   ```

## データベースインスタンスの設定

この節では、Adobe Commerceのデータベースインスタンスを作成する方法について説明します。 新しいデータベースインスタンスを作成することをお勧めしますが、オプションで既存のデータベースインスタンスにAdobe Commerceをインストールできます。

MySQL データベースインスタンスを設定するには：

1. 任意のユーザーとしてデータベース・サーバにログインします。
1. MySQL コマンドプロンプトに移動します。

   ```shell
   mysql -u root -p
   ```

1. プロンプトが表示されたら、MySQL `root` ユーザーのパスワードを入力します。
1. ユーザー名`magento`の`magento`という名前のデータベースインスタンスを作成するには、次のコマンドを順に入力します。

   ```sql
   create database magento;
   ```

   ```sql
   create user 'magento'@'localhost' IDENTIFIED BY 'magento';
   ```

   ```sql
   GRANT ALL ON magento.* TO 'magento'@'localhost';
   ```

   ```sql
   flush privileges;
   ```

1. コマンド プロンプトを終了するには、`exit`と入力します。

1. データベースを確認します。

   ```shell
   mysql -u magento -p
   ```

   MySQL モニターが表示される場合は、データベースを適切に作成しました。 エラーが表示された場合は、上記のコマンドを繰り返します。

1. Web サーバーとデータベース サーバーが異なるホスト上にある場合は、このトピックで説明したタスクをデータベース サーバー上で実行し、[&#x200B; リモート MySQL データベース接続の設定](mysql-remote.md)を参照してください。

   ビジネスに適したデータベースインスタンスを設定することをお勧めします。 データベースを設定する際は、次の点に注意してください。

   * インデクサーには、より大きな`tmp_table_size`値と`max_heap_table_size`値（64 Mなど）が必要です。 `batch_size` パラメーターを設定する場合は、その値をテーブルサイズ設定と共に調整して、インデクサーのパフォーマンスを向上させることができます。 詳しくは、[最適化ガイド &#x200B;](../../../performance/configuration.md)を参照してください。

   * 最適なパフォーマンスを得るには、すべてのMySQLおよびAdobe Commerce インデックステーブルをメモリに保持できることを確認します（例：`innodb_buffer_pool_size`）。

   * MariaDB 10.4でのインデックス再作成は、他のMariaDBまたはMySQL バージョンと比較してより多くの時間がかかります。 [設定のベストプラクティス &#x200B;](../../../performance/configuration.md#indexers)を参照してください。

1. MySQL `TIMESTAMP` フィールドが、アプリケーションの宣言型スキーマアーキテクチャで期待される環境設定と構成に従うには、システム変数`explicit_defaults_for_timestamp`を`on`に設定する必要があります。

   参照：

   * [MySQL 8.4](https://dev.mysql.com/doc/refman/8.4/en/server-system-variables.html#sysvar_explicit_defaults_for_timestamp)
   * [MariaDB](https://mariadb.com/docs/server/server-management/variables-and-modes/server-system-variables#explicit_defaults_for_timestamp)

   この設定が有効になっていない場合、`bin/magento setup:db:status`は常に`Declarative Schema is not up to date`を報告します。

>[!NOTE]
>
>`explicit_defaults_for_timestamp`設定は非推奨です。 この設定は、将来のMySQL リリースで削除される非推奨のTIMESTAMP ビヘイビアーを制御します。 これらのビヘイビアーが削除されると、`explicit_defaults_for_timestamp`設定も削除されます。

>[!WARNING]
>
>クラウドインフラストラクチャプロジェクト上のAdobe Commerceの場合、MySQL （MariaDB）の`explicit_defaults_for_timestamp`設定はデフォルトで&#x200B;_OFF_&#x200B;になります。

{{$include /help/_includes/maria-db-config.md}}

<!-- Last updated from includes: 2025-11-25 11:39:51 -->
