---
title: MySQL ガイドライン
description: MySQL と MariaDB をインストールして、Adobe CommerceとMagento Open Sourceのオンプレミスインストール用に設定するには、次の手順に従います。
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '1179'
ht-degree: 0%

---


# 一般的な MySQL ガイドライン

詳しくは、 [必要システム構成](../../system-requirements.md) を参照してください。

Adobe _強く_ では、データベースを設定する際に、次の標準を遵守することをお勧めします。

* Adobe CommerceとMagento Open Sourceの使用 [MySQL データベーストリガー](https://dev.mysql.com/doc/refman/8.0/en/triggers.html) インデックス再作成時のデータベースアクセスを改善する。 インデクサーモードが [スケジュール](../../../configuration/cli/manage-indexers.md#configure-indexers). カスタムトリガーは将来のAdobe CommerceおよびMagento Open Sourceトリガーと互換性がなくなる可能性があるので、このアプリケーションはデータベース内のカスタムバージョンをサポートしていません。
* に慣れてください。 [MySQL の潜在的なトリガー制限](https://dev.mysql.com/doc/mysql-reslimits-excerpt/8.0/en/stored-program-restrictions.html) 続行する前に
* データベースのセキュリティの姿勢を強化するには、 [`STRICT_ALL_TABLES`](https://dev.mysql.com/doc/refman/5.7/en/sql-mode.html#sqlmode_strict_all_tables) 無効なデータ値の保存を防ぐ SQL モード。データベースとのやり取りが望ましくない可能性があります。
* Adobe CommerceとMagento Open Sourceド _not_ は、MySQL 文ベースのレプリケーションをサポートします。 必ず _のみ_ [行ベースのレプリケーション](https://dev.mysql.com/doc/refman/8.0/en/replication-formats.html).

>[!WARNING]
>
>Adobe CommerceとMagento Open Sourceは現在 `CREATE TEMPORARY TABLE` 取引内の明細書 ( [互換性がない](https://dev.mysql.com/doc/refman/5.7/en/replication-gtids-restrictions.html) データベース実装では、GTID ベースのレプリケーションを使用します ( 例： [Google Cloud SQL 第 2 世代インスタンス](https://cloud.google.com/sql/docs/features#differences). Cloud SQL 8.0 の場合は、MySQL を代わりに使用すると考えてください。

>[!NOTE]
>
>Web サーバーとデータベース・サーバーが異なるホスト上にある場合は、このトピックで説明するタスクをデータベース・サーバー・ホスト上で実行し、次を参照してください。 [リモート MySQL データベース接続を設定する](mysql-remote.md).

## Ubuntu への MySQL のインストール

Adobe CommerceおよびMagento Open Source2.4 では、MySQL 8.0 をクリーンインストールする必要があります。お使いのマシンに MySQL をインストールする手順については、以下のリンクを参照してください。

* [Ubuntu](https://ubuntu.com/server/docs/databases-mysql)
* [CentOS](https://dev.mysql.com/doc/refman/8.0/en/linux-installation-yum-repo.html)

大量の製品を読み込む場合は、 [`max_allowed_packet`](https://dev.mysql.com/doc/refman/5.6/en/program-variables.html) はデフォルトの 16 MB より大きくなります。

>[!NOTE]
>
>デフォルト値は、クラウドインフラストラクチャ上のAdobe Commerceに適用されます _および_ オンプレミスプロジェクト。 Adobe Commerce on cloud infrastructure Pro のお客様は、 `max_allowed_packet` の値です。 クラウドインフラストラクチャ上のAdobe Commerce Starter のお客様は、 `/etc/mysql/mysql.cnf` ファイル。

値を増やすには、 `/etc/mysql/mysql.cnf` ファイルを編集し、 `max_allowed_packet`. 変更を `mysql.cnf` ファイルを閉じ、テキストエディタを閉じて MySQL (`service mysql restart`) をクリックします。

設定した値をオプションで確認するには、次のコマンドを `mysql>` プロンプト：

```sql
SHOW VARIABLES LIKE 'max_allowed_packet';
```

すると、 [データベースインスタンスの設定](#configuring-the-database-instance).

## MySQL 8 の変更

Adobe CommerceおよびMagento Open Source2.4 に対して、MySQL 8 のサポートを追加しました。
ここでは、開発者が認識する必要がある MySQL 8 の大きな変更について説明します。

### 整数タイプ（パディング）の幅を削除しました。

MySQL 8.0.17 では、整数データ型 (TINYINT, SMALLINT, MEDIAMINT, INT, BIGINT) の表示幅の指定が廃止されました。出力に data-type 定義を含むステートメントは、TINYINT(1) を除き、整数型の表示幅を示しません。 MySQL コネクタは、TINYINT(1) 列が BOOLEAN 列として生成されたことを想定しています。 この例外により、ユーザーは引き続きその前提を提示できます。

#### 例

mysql 8.19 の admin_user について説明する

| フィールド | タイプ | Null | キー | デフォルト | 追加 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| user\_id | `int unsigned` | いいえ | PRI | `NULL` | `auto_increment` |
| `firstname` | `varchar(32)` | はい |  | `NULL` |  |
| `lastname` | `varchar(32`) | はい |  | `NULL` |  |
| `email` | `varchar(128)` | はい |  | `NULL` |  |
| `username` | `varchar(40)` | はい | UNI | `NULL` |  |
| `password` | `varchar(255)` | いいえ |  | `NULL` |  |
| `created` | `timestamp` | いいえ |  | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` |
| `modified` | `timestamp` | いいえ |  | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` 更新時 `CURRENT_TIMESTAMP` |
| `logdate` | `timestamp` | はい |  | `NULL` |  |
| `lognum` | `smallint unsigned` | いいえ |  | `0` |  |

例外 _TINYINT(1)_、すべての整数パディング (TINYINT > 1, SMALLINT, MEDIAMINT, INT, BIGINT) を `db_schema.xml` ファイル。

詳しくは、 [https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature](https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature).

### デフォルトの並べ替え順の動作

8.0 以前は、エントリは外部キーで並べ替えられていました。 デフォルトの並べ替え順は、使用するエンジンによって異なります。
コードが特定の並べ替えに依存する場合は、常に並べ替え順を指定します。

### GROUP BY の非推奨の ASC 修飾子と DESC 修飾子

MySQL 8.0.13 以降、非推奨 `ASC` または `DESC` 次の条件を満たす `GROUP BY` 節が削除されました。 以前に依存していたクエリ `GROUP BY` 並べ替えを実行すると、以前の MySQL バージョンとは異なる結果が生じる場合があります。 特定の並べ替え順を生成するには、 `ORDER BY` 句を使用します。

## Commerce と MySQL 8

MySQL 8 を適切にサポートするために、Adobe CommerceとMagento Open Sourceにいくつかの変更が加えられました。

### クエリと挿入の動作

Adobe CommerceとMagento Open Sourceは、 `/lib/internal/Magento/Framework/DB/Adapter/Pdo/Mysql.php:424.`. 検証が無効になっている場合、MySQL がデータを切り捨てる可能性があります。 MySQL で、クエリの動作が変更されました。 `Select * on my_table where IP='127.0.0.1'` IP アドレスが整数ではなく文字列として適切に表示されるようになったので、は結果を返さなくなりました。

## MySQL 5.7 から MySQL 8 へのアップグレード

MySQL をバージョン 5.7 からバージョン 8 に適切に更新するには、次の手順に従う必要があります。

1. Adobe CommerceまたはMagento Open Sourceを 2.4.0 にアップグレードします。すべてをテストし、システムが期待どおりに動作することを確認します。
1. メンテナンスモードを有効にする：

   ```bash
   bin/magento maintenance:enable
   ```

1. データベースのバックアップを作成する：

   ```bash
   bin/magento setup:backup --db
   ```

1. MySQL をバージョン 8 に更新しました。
1. バックアップしたデータを MySQL にインポートします。
1. キャッシュをクリーンアップします。

   ```bash
   bin/magento cache:clean
   ```

1. メンテナンスモードを無効にする：

   ```bash
   bin/magento maintenance:disable
   ```

## データベースインスタンスの設定

この節では、Adobe CommerceまたはMagento Open Source用のデータベースインスタンスを作成する方法について説明します。 新しいデータベースインスタンスを使用することをお勧めしますが、必要に応じて、既存のデータベースインスタンスとAdobe CommerceまたはMagento Open Sourceをインストールすることもできます。

MySQL データベースインスタンスを設定するには：

1. 任意のユーザーとしてデータベースサーバーにログインします。
1. MySQL コマンドプロンプトに移動します。

   ```bash
   mysql -u root -p
   ```

1. MySQL を入力 `root` ユーザーのパスワードを求められた場合。
1. 次のコマンドを、図の順序で入力して、という名前のデータベースインスタンスを作成します。 `magento` ユーザー名 `magento`:

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

1. 入力 `exit` をクリックして、コマンドプロンプトを終了します。

1. データベースを検証します。

   ```bash
   mysql -u magento -p
   ```

   MySQL モニタが表示される場合は、データベースが正しく作成されています。 エラーが表示される場合は、上記のコマンドを繰り返します。

1. Web サーバーとデータベース・サーバーが異なるホスト上にある場合は、このトピックで説明するタスクをデータベース・サーバー・ホスト上で実行し、次を参照してください。 [リモート MySQL データベース接続を設定する](mysql-remote.md).

   ビジネスに応じて、データベースインスタンスを適切に設定することをお勧めします。 データベースを設定する際は、次の点に注意してください。

   * インデクサーは高い値を必要とします `tmp_table_size` および `max_heap_table_size` の値（例：64 M）。 次に `batch_size` パラメータを使用すると、テーブルサイズ設定と共にその値を調整して、インデクサーのパフォーマンスを向上させることができます。 詳しくは、 [最適化ガイド](../../../performance/configuration.md) を参照してください。

   * 最適なパフォーマンスを得るには、すべての MySQL およびAdobe CommerceまたはMagento Open Sourceインデックステーブルをメモリに保持できるようにします ( 例えば、 `innodb_buffer_pool_size`) をクリックします。

   * MariaDB 10.4 でのインデックス再作成は、他の MariaDB または MySQL バージョンと比べて時間がかかります。 詳しくは、 [設定のベストプラクティス](../../../performance/configuration.md#indexers).

1. MySQL の場合 `TIMESTAMP` アプリケーションの宣言的スキーマアーキテクチャ（システム変数）で期待される環境設定と構成に従うフィールド `explicit_defaults_for_timestamp` は、次のように設定する必要があります `on`.

   参照：

   * [MySQL 5.7](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_explicit_defaults_for_timestamp)
   * [MariaDB](https://mariadb.com/kb/en/server-system-variables/#explicit_defaults_for_timestamp)

   この設定が有効でない場合、 `bin/magento setup:db:status` 常に `Declarative Schema is not up to date`.

>[!NOTE]
>
>この `explicit_defaults_for_timestamp` の設定は非推奨です。 この設定は、将来の MySQL リリースで削除される、非推奨の TIMESTAMP 動作を制御します。 これらの動作が削除されると、 `explicit_defaults_for_timestamp` 設定も削除されます。

>[!WARNING]
>
>Adobe Commerce on cloud infrastructure プロジェクトの場合、 `explicit_defaults_for_timestamp` MySQL (MariaDB) の設定のデフォルト値はです。 _オフ_.

MariaDB 10.4 でのインデックス再作成は、他の MariaDB または MySQL バージョンと比べて時間がかかります。 インデックスの再作成を高速化するには、次の MariaDB 設定パラメーターを設定することをお勧めします。

* optimizer_switch=&#39;rowid_filter=off&#39;
* optimizer_use_condition_selectivity = 1
