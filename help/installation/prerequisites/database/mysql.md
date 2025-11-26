---
title: MySQL ガイドライン
description: 次の手順に従って、Adobe Commerceのオンプレミスインストール用に MySQL と MariaDB をインストールして設定します。
exl-id: dc5771a8-4066-445c-b1cd-9d5f449ec9e9
source-git-commit: 2d17da1f8cbda1462839ad2fa3ea569833443827
workflow-type: tm+mt
source-wordcount: '1037'
ht-degree: 0%

---

# 一般的な MySQL ガイドライン

サポートされている MySQL のバージョンについては、[&#x200B; システム要件 &#x200B;](../../system-requirements.md) を参照してください。

Adobe _強く_ は、データベースを設定する際に、次の標準に従うことをお勧めします。

* Adobe Commerceでは、[MySQL データベーストリガー](https://dev.mysql.com/doc/refman/8.0/en/triggers.html) を使用して、インデックス再作成中のデータベースアクセスを改善します。 これらは、インデクサーモードが「[&#x200B; スケジュール &#x200B;](../../../configuration/cli/manage-indexers.md#configure-indexers)」に設定されている場合に作成されます。 カスタムトリガーは将来のAdobe Commerceとの互換性を失う可能性があるため、データベース内のカスタムトリガーはサポートされません。
* 続行する前に [MySQL のトリガーに関する潜在的な制限 &#x200B;](https://dev.mysql.com/doc/mysql-reslimits-excerpt/8.0/en/stored-program-restrictions.html) について確認してください。
* データベースのセキュリティ体制を強化するには、[`STRICT_ALL_TABLES`](https://dev.mysql.com/doc/refman/5.7/en/sql-mode.html#sqlmode_strict_all_tables) SQL モードを有効にして、不要なデータベース操作を引き起こす可能性のある無効なデータ値の保存を防ぎます。
* Adobe Commerceでは、MySQL 文ベースのレプリケーションはサポート _れていません_。 必ず _only_[&#x200B; 行ベースのレプリケーション &#x200B;](https://dev.mysql.com/doc/refman/8.0/en/replication-formats.html) を使用してください。

>[!WARNING]
>
>Adobe Commerceは現在、トランザクション内で `CREATE TEMPORARY TABLE` ステートメントを使用しています。これは [&#x200B; データベース実装と互換性がない &#x200B;](https://dev.mysql.com/doc/refman/5.7/en/replication-gtids-restrictions.html)、[Google Cloud SQL 第 2 世代インスタンス &#x200B;](https://cloud.google.com/sql/docs/features#differences) などの GTID ベースのレプリケーションを使用します。 Cloud SQL 8.0 用の MySQL を代替案として検討してください。

>[!NOTE]
>
>Web サーバーとデータベースサーバーが異なるホスト上にある場合は、データベースサーバーホスト上でこのトピックで説明されているタスクを実行してから、[&#x200B; リモート MySQL データベース接続の設定 &#x200B;](mysql-remote.md) を参照してください。

## Ubuntu への MySQL のインストール

Adobe Commerce 2.4 には、MySQL 8.0 のクリーンインストールが必要です。以下のリンクに従って、お使いのマシンに MySQL をインストールする手順を確認してください。

* [Ubuntu](https://ubuntu.com/server/docs/databases-mysql)
* [CentOS](https://dev.mysql.com/doc/refman/8.0/en/linux-installation-yum-repo.html)

多数の製品を読み込む場合は、デフォルトの 16 MB よりも大きい [`max_allowed_packet`](https://dev.mysql.com/doc/refman/5.6/en/program-variables.html) の値を増やすことができます。

>[!NOTE]
>
>デフォルト値は、クラウドインフラストラクチャー上のAdobe Commerce _およびオンプレミスのプロジェクト_ 適用されます。 Adobe Commerce on cloud infrastructure Pro をご利用のお客様は、`max_allowed_packet` の価値を高めるために、サポートチケットを開く必要があります。 Adobe Commerce on cloud infrastructure スターターを使用すると、`/etc/mysql/mysql.cnf` ファイルの設定を更新することで価値を高めることができます。

値を増やすには、`/etc/mysql/mysql.cnf` ファイルをテキストエディターで開き、`max_allowed_packet` の値を探します。 `mysql.cnf` ファイルへの変更を保存し、テキストエディターを閉じて、MySQL （`service mysql restart`）を再起動します。

オプションで設定した値を確認するには、`mysql>` のプロンプトで次のコマンドを入力します。

```sql
SHOW VARIABLES LIKE 'max_allowed_packet';
```

次に、[&#x200B; データベースインスタンスを設定 &#x200B;](#configuring-the-database-instance) します。

## MySQL 8 の変更

Adobe Commerce 2.4 では、MySQL 8 がサポートされるようになりました。
この節では、開発者が認識しておくべき、MySQL 8 の主な変更点について説明します。

### 整数タイプ （パディング）の幅を削除

整数データ型（TINYINT、SMALLINT、MEDIUMINT、INT、BIGINT）の表示幅の仕様は、MySQL 8.0.17 で非推奨（廃止予定）となりました。出力にデータ型の定義を含むステートメントは、TINYINT （1）を除き、整数型の表示幅を表示しなくなりました。 MySQL コネクタは、TINYINT （1）列が BOOLEAN 列として生成されることを前提としています。 この例外により、ユーザーは引き続きその前提を立てることができます。

#### 例

mysql 8.19 での admin_user について説明します。

| フィールド | タイプ | ヌル | キー | デフォルト | 追加 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| user\_id | `int unsigned` | 不可 | PRI | `NULL` | `auto_increment` |
| `firstname` | `varchar(32)` | はい | | `NULL` | |
| `lastname` | `varchar(32`） | はい | | `NULL` | |
| `email` | `varchar(128)` | はい | | `NULL` | |
| `username` | `varchar(40)` | はい | UNI | `NULL` | |
| `password` | `varchar(255)` | 不可 | | `NULL` | |
| `created` | `timestamp` | 不可 | | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` |
| `modified` | `timestamp` | 不可 | | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` on update `CURRENT_TIMESTAMP` |
| `logdate` | `timestamp` | はい | | `NULL` | |
| `lognum` | `smallint unsigned` | 不可 | | `0` | |

_TINYINT （1）_ を除き、すべての整数パディング （TINYINT > 1, SMALLINT, MEDIUMINT, INT, BIGINT）は `db_schema.xml` ファイルから削除する必要があります。

詳しくは、[https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature](https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature) を参照してください。

### デフォルトの並べ替え順

8.0 より前のエントリは、外部キーで並べ替えられていました。 デフォルトの並べ替え順は、使用するエンジンによって異なります。
コードが特定の並べ替えに依存している場合は、常に並べ替え順を指定します。

### GROUP BY の非推奨の ASC 修飾子と DESC 修飾子

MySQL 8.0.13 以降、廃止された `ASC` 句または `DESC` 句の `GROUP BY` 修飾子は削除されました。 以前に `GROUP BY` の並べ替えに依存していたクエリが、以前の MySQL バージョンとは異なる結果になる場合があります。 指定した並べ替え順を生成するには、`ORDER BY` 句を指定します。

## Commerceと MySQL 8

MySQL 8 を適切にサポートするために、Adobe Commerceにいくつかの変更が加えられました。

### クエリと挿入の動作

Adobe Commerceは、`/lib/internal/Magento/Framework/DB/Adapter/Pdo/Mysql.php:424.` で SET SQL_MODE=&quot;を設定して、通常の検証動作を無効にしました。 検証が無効の場合、MySQL がデータを切り捨てる可能性があります。 MySQL では、クエリの動作が変更されました。`Select * on my_table where IP='127.0.0.1'` では、IP アドレスが整数ではなく文字列として正しく認識されるようになり、結果を返さなくなりました。

## Mysql 5.7 から MySQL 8 へのアップグレード

MySQL をバージョン 5.7 からバージョン 8 に適切にアップデートするには、次の手順に従う必要があります。

1. Adobe Commerceを 2.4.0 にアップグレードします。
すべてをテストし、システムが期待どおりに動作することを確認します。
1. メンテナンスモードを有効にする：

   ```bash
   bin/magento maintenance:enable
   ```

1. データベースのバックアップを作成します。

   ```bash
   bin/magento setup:backup --db
   ```

1. MySQL をバージョン 8 にアップデートします。
1. バックアップしたデータを MySQL に読み込みます。
1. キャッシュのクリーンアップ：

   ```bash
   bin/magento cache:clean
   ```

1. メンテナンスモードを無効にする：

   ```bash
   bin/magento maintenance:disable
   ```

## データベースインスタンスの設定

この節では、Adobe Commerceのデータベースインスタンスを作成する方法について説明します。 新しいデータベースインスタンスを使用することをお勧めしますが、既存のデータベースインスタンスを使用してAdobe Commerceをインストールすることもできます。

MySQL データベースインスタンスを設定するには、次の手順に従います。

1. 任意のユーザーとしてデータベースサーバーにログインします。
1. MySQL コマンドプロンプトに移動します。

   ```bash
   mysql -u root -p
   ```

1. プロンプトが表示されたら、MySQL `root` ユーザーのパスワードを入力します。
1. 次のコマンドを表示されている順序で入力して、`magento` という名前のデータベース・インスタンスをユーザー名 `magento` で作成します。

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

1. コマンドプロンプトを終了するには、`exit` と入力します。

1. データベースを確認します。

   ```bash
   mysql -u magento -p
   ```

   MySQL モニターが表示された場合は、データベースが正しく作成されています。 エラーが表示された場合は、上記のコマンドを繰り返します。

1. Web サーバーとデータベースサーバーが異なるホスト上にある場合は、データベースサーバーホスト上でこのトピックで説明されているタスクを実行してから、[&#x200B; リモート MySQL データベース接続の設定 &#x200B;](mysql-remote.md) を参照してください。

   ビジネスに適したデータベースインスタンスを設定することをお勧めします。 データベースを設定する際は、次の点に注意してください。

   * インデクサーには、より高い `tmp_table_size` と `max_heap_table_size` の値（例：64 M）が必要です。 `batch_size` パラメーターを設定すると、インデクサーのパフォーマンスを向上させるために、テーブルサイズの設定と共にその値を調整できます。 詳しくは、『 [&#x200B; 最適化ガイド &#x200B;](../../../performance/configuration.md) を参照してください。

   * 最適なパフォーマンスを得るには、すべての MySQL およびAdobe Commerce インデックステーブルをメモリに保持できるようにします（例：`innodb_buffer_pool_size` を設定）。

   * MariaDB 10.4 でのインデックス再作成は、他の MariaDB または MySQL バージョンに比べて時間がかかります。 [&#x200B; 設定のベストプラクティス &#x200B;](../../../performance/configuration.md#indexers) を参照してください。

1. MySQL `TIMESTAMP` フィールドがアプリケーションの宣言型スキーマアーキテクチャが想定する環境設定および構成に従うようにするには、システム変数 `explicit_defaults_for_timestamp` を `on` に設定する必要があります。

   参照：

   * [MySQL 5.7](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_explicit_defaults_for_timestamp)
   * [MariaDB](https://mariadb.com/kb/en/server-system-variables/#explicit_defaults_for_timestamp)

   この設定が有効になっていない場合、`bin/magento setup:db:status` は常に `Declarative Schema is not up to date` を報告します。

>[!NOTE]
>
>`explicit_defaults_for_timestamp` 設定は非推奨（廃止予定）です。 この設定は、今後の MySQL リリースで削除される非推奨の TIMESTAMP 動作を制御します。 これらの動作を削除すると、`explicit_defaults_for_timestamp` 設定も削除されます。

>[!WARNING]
>
>クラウドインフラストラクチャプロジェクト上のAdobe Commerceの場合、MySQL （MariaDB）の `explicit_defaults_for_timestamp` 設定はデフォルトで _オフ_ になっています。

{{$include /help/_includes/maria-db-config.md}}

<!-- Last updated from includes: 2025-11-25 11:39:51 -->
