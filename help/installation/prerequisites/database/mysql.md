---
title: MySQL ガイドライン
description: 次の手順に従って、Adobe Commerceのオンプレミスインストール用に MySQL と MariaDB をインストールして設定します。
exl-id: dc5771a8-4066-445c-b1cd-9d5f449ec9e9
source-git-commit: 35664c30e438305036d3cfdd1dd1924966f6ced6
workflow-type: tm+mt
source-wordcount: '1053'
ht-degree: 0%

---

# 一般的な MySQL ガイドライン

参照： [必要システム構成](../../system-requirements.md) （サポートされている MySQL バージョン用）

Adobe _強く_ では、データベースを設定する際に、次の標準に従うことをお勧めします。

* Adobe Commerceが使用する [MySQL データベーストリガー](https://dev.mysql.com/doc/refman/8.0/en/triggers.html) インデックス再作成中のデータベースアクセスを改善する。 これらは、インデクサーモードがに設定されている場合に作成されます。 [スケジュール](../../../configuration/cli/manage-indexers.md#configure-indexers). カスタムトリガーは将来のAdobe Commerceとの互換性を失う可能性があるため、データベース内のカスタムトリガーはサポートされません。
* に慣れる [mysql トリガーに関して考えられる次の制限事項](https://dev.mysql.com/doc/mysql-reslimits-excerpt/8.0/en/stored-program-restrictions.html) 先に進む前に。
* データベースのセキュリティ体制を強化するには、 [`STRICT_ALL_TABLES`](https://dev.mysql.com/doc/refman/5.7/en/sql-mode.html#sqlmode_strict_all_tables) SQL モードを使用すると、不要なデータベースインタラクションを引き起こす可能性のある無効なデータ値を保存しないようにすることができます。
* Adobe Commerce _ではない_ mysql ステートメントベースのレプリケーションをサポートします。 を使用していることを確認してください。 _のみ_ [行ベースのレプリケーション](https://dev.mysql.com/doc/refman/8.0/en/replication-formats.html).

>[!WARNING]
>
>Adobe Commerceは現在を使用しています `CREATE TEMPORARY TABLE` トランザクション内のステートメント。以下に示します [互換性なし](https://dev.mysql.com/doc/refman/5.7/en/replication-gtids-restrictions.html) データベース実装では、次のような GTID ベースのレプリケーションを使用します [Google Cloud SQL の第 2 世代インスタンス](https://cloud.google.com/sql/docs/features#differences). Cloud SQL 8.0 用の MySQL を代替案として検討してください。

>[!NOTE]
>
>Web サーバーとデータベース・サーバーが異なるホスト上にある場合は、データベース・サーバー・ホスト上でこのトピックで説明されているタスクを実行し、次の項目を確認します [リモート MySQL データベース接続の設定](mysql-remote.md).

## Ubuntu への MySQL のインストール

Adobe Commerce 2.4 には、MySQL 8.0 のクリーンインストールが必要です。以下のリンクに従って、お使いのマシンに MySQL をインストールする手順を確認してください。

* [Ubuntu](https://ubuntu.com/server/docs/databases-mysql)
* [CentOS](https://dev.mysql.com/doc/refman/8.0/en/linux-installation-yum-repo.html)

多数の製品を読み込む場合は、の値を増やすことができます [`max_allowed_packet`](https://dev.mysql.com/doc/refman/5.6/en/program-variables.html) これは、デフォルトの 16 MB よりも大きいサイズです。

>[!NOTE]
>
>デフォルト値は、クラウドインフラストラクチャー上のAdobe Commerceに適用されます _および_ オンプレミスプロジェクト。 Adobe Commerce on cloud infrastructure Pro をご利用のお客様が増やすには、サポートチケットを開く必要があります `max_allowed_packet` の値。 Adobe Commerce on cloud infrastructure スターターを使用すると、 `/etc/mysql/mysql.cnf` ファイル。

値を増やすには、 `/etc/mysql/mysql.cnf` テキストエディターでファイルを開き、の値を探します `max_allowed_packet`. 変更をに保存します。 `mysql.cnf` ファイルを開き、テキストエディターを閉じて、MySQL （`service mysql restart`）に設定します。

オプションで、設定した値を確認するには、に次のコマンドを入力します `mysql>` プロンプト：

```sql
SHOW VARIABLES LIKE 'max_allowed_packet';
```

その後、 [データベースインスタンスの設定](#configuring-the-database-instance).

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
| `modified` | `timestamp` | 不可 | | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` 更新時 `CURRENT_TIMESTAMP` |
| `logdate` | `timestamp` | はい | | `NULL` | |
| `lognum` | `smallint unsigned` | 不可 | | `0` | |

次を除く _TINYINT （1）_、すべての整数のパディング（TINYINT > 1、SMALLINT、MEDIUMINT、INT、BIGINT）を `db_schema.xml` ファイル。

詳しくは、を参照してください [https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature](https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature).

### デフォルトの並べ替え順

8.0 より前のエントリは、外部キーで並べ替えられていました。 デフォルトの並べ替え順は、使用するエンジンによって異なります。
コードが特定の並べ替えに依存している場合は、常に並べ替え順を指定します。

### GROUP BY の非推奨の ASC 修飾子と DESC 修飾子

MySQL 8.0.13 以降、は非推奨になりました `ASC` または `DESC` の修飾子 `GROUP BY` 条項が削除されました。 以前に依存していたクエリ `GROUP BY` 並べ替えにより、以前の MySQL バージョンとは異なる結果が生成される場合があります。 特定の並べ替え順を生成するには、次を指定します `ORDER BY` 句。

## Commerceと MySQL 8

MySQL 8 を適切にサポートするために、Adobe Commerceにいくつかの変更が加えられました。

### クエリと挿入の動作

Adobe Commerceは、に SET SQL_MODE=&quot;を設定して、通常の検証動作を無効にしました。 `/lib/internal/Magento/Framework/DB/Adapter/Pdo/Mysql.php:424.`. 検証が無効の場合、MySQL がデータを切り捨てる可能性があります。 MySQL では、クエリの動作が変更されました。 `Select * on my_table where IP='127.0.0.1'` が結果を返さなくなりました。これは、IP アドレスが整数ではなく、文字列として正しく認識されるからです。

## Mysql 5.7 から MySQL 8 へのアップグレード

MySQL をバージョン 5.7 からバージョン 8 に適切にアップデートするには、次の手順に従う必要があります。

1. Adobe CommerceまたはMagento Open Sourceを 2.4.0 にアップグレードします。すべてをテストし、システムが期待どおりに動作することを確認します。
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

この節では、Adobe CommerceまたはMagento Open Sourceのデータベースインスタンスを作成する方法について説明します。 新しいデータベースインスタンスを使用することをお勧めしますが、必要に応じて、Adobe CommerceまたはMagento Open Sourceを既存のデータベースインスタンスと共にインストールできます。

MySQL データベースインスタンスを設定するには、次の手順に従います。

1. 任意のユーザーとしてデータベースサーバーにログインします。
1. MySQL コマンドプロンプトに移動します。

   ```bash
   mysql -u root -p
   ```

1. MySQL を入力 `root` プロンプトが表示されたらユーザーのパスワードを入力します。
1. 次のコマンドを表示されている順序で入力して、という名前のデータベースインスタンスを作成します。 `magento` ユーザー名 `magento`:

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

1. Enter `exit` をクリックして、コマンドプロンプトを終了します。

1. データベースを確認します。

   ```bash
   mysql -u magento -p
   ```

   MySQL モニターが表示された場合は、データベースが正しく作成されています。 エラーが表示された場合は、上記のコマンドを繰り返します。

1. Web サーバーとデータベース・サーバーが異なるホスト上にある場合は、データベース・サーバー・ホスト上でこのトピックで説明されているタスクを実行し、次の項目を確認します [リモート MySQL データベース接続の設定](mysql-remote.md).

   ビジネスに適したデータベースインスタンスを設定することをお勧めします。 データベースを設定する際は、次の点に注意してください。

   * インデクサーには、より高い値が必要です `tmp_table_size` および `max_heap_table_size` 値（例：64 M）。 を設定する場合 `batch_size` パラメーターを使用すると、その値をテーブルサイズの設定と共に調整して、インデクサーのパフォーマンスを向上させることができます。 を参照してください。 [最適化ガイド](../../../performance/configuration.md) を参照してください。

   * 最適なパフォーマンスを得るには、すべての MySQL とAdobe CommerceまたはMagento Open Sourceのインデックステーブルをメモリに保持できるようにします（例： `innodb_buffer_pool_size`）に設定します。

   * MariaDB 10.4 でのインデックス再作成は、他の MariaDB または MySQL バージョンに比べて時間がかかります。 参照： [設定のベストプラクティス](../../../performance/configuration.md#indexers).

1. MySQL の場合 `TIMESTAMP` アプリケーションの宣言型スキーマアーキテクチャが想定する環境設定および構成に従うフィールド、システム変数 `explicit_defaults_for_timestamp` に設定する必要があります。 `on`.

   参照：

   * [MySQL 5.7](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_explicit_defaults_for_timestamp)
   * [MariaDB](https://mariadb.com/kb/en/server-system-variables/#explicit_defaults_for_timestamp)

   この設定が有効になっていない場合、 `bin/magento setup:db:status` は常にと報告します `Declarative Schema is not up to date`.

>[!NOTE]
>
>この `explicit_defaults_for_timestamp` の設定は非推奨（廃止予定）です。 この設定は、今後の MySQL リリースで削除される非推奨の TIMESTAMP 動作を制御します。 これらの動作が削除されると、 `explicit_defaults_for_timestamp` の設定も削除されました。

>[!WARNING]
>
>クラウドインフラストラクチャプロジェクトのAdobe Commerceの場合、 `explicit_defaults_for_timestamp` mysql （MariaDB）のデフォルト設定は次のとおりです。 _オフ_.

{{$include /help/_includes/maria-db-config.md}}
