---
title: 前提条件を完了
description: 次の前提条件の手順を完了して、アップグレード用のAdobe Commerce プロジェクトを準備します。
exl-id: f7775900-1d10-4547-8af0-3d1283d9b89e
source-git-commit: df185e21f918d32ed5033f5db89815b5fc98074f
workflow-type: tm+mt
source-wordcount: '1866'
ht-degree: 0%

---

# アップグレードの前提条件の完了

Adobe Commerceの実行に必要な事項を理解することが重要です。 最初に、アップグレード先のバージョンの [ 必要システム構成 ](../../installation/system-requirements.md) を確認する必要があります。

システム要件を確認した後、システムをアップグレードする前に次の前提条件を満たす必要があります。

* すべてのソフトウェアを更新する
* サポートされている検索エンジンがインストールされていることを確認します
* データベース テーブル形式を変換
* 開いているファイルの上限を設定
* Cron ジョブが実行中であることを確認
* `DATA_CONVERTER_BATCH_SIZE` を設定
* ファイルシステムの権限の確認
* `pub/` ディレクトリルートの設定
* Composer アップデート プラグインのインストール

## すべてのソフトウェアを更新する

[ システム要件 ](../../installation/system-requirements.md) には、Adobe Commerce リリースでテストされているサードパーティソフトウェアのバージョンが正確に記載されています。

環境内のすべてのシステム要件と依存関係を更新していることを確認してください。 PHP [7.4](https://www.php.net/manual/en/migration74.php)、PHP [8.0](https://www.php.net/manual/en/migration80.php)、PHP [8.1](https://www.php.net/manual/en/migration81.php)、および [ 必要な PHP 設定 ](../../installation/prerequisites/php-settings.md#php-settings) を参照してください。

>[!NOTE]
>
>Cloud infrastructure Pro プロジェクトのAdobe Commerceの場合、ステージング環境と実稼動環境でサービスをインストールまたは更新するための [ サポート ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) チケットを作成する必要があります。 必要なサービスの変更を示し、更新した `.magento.app.yaml` ファイルと `services.yaml` ファイル、および PHP バージョンをチケットに含めます。 クラウドインフラストラクチャチームがプロジェクトを更新するまで、最大 48 時間かかる場合があります。 [ サポートされるソフトウェアとサービス ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html#supported-software-and-services) を参照してください。

## サポートされている検索エンジンがインストールされていることを確認します

Adobe Commerceを使用するには、Elasticsearchまたは OpenSearch がインストールされている必要があります。

**2.3.x から 2.4 にアップグレードする場合**、2.3.x インスタンスのカタログ検索エンジンとして、MySQL、Elasticsearch、サードパーティの拡張機能のいずれかを使用しているかどうかを確認する必要があります。 結果によって、2.4 にアップグレードする _前に_ 実行する必要がある作業が決まります。

**2.3.x または 2.4.x のリリース行内でパッチリリースをアップグレードしている場合**、Elasticsearch 7.x が既にインストールされている場合は、オプションで [OpenSearch に移行 ](opensearch-migration.md) できます。

コマンドラインまたは管理者を使用して、カタログ検索エンジンを決定できます。

* `bin/magento config:show catalog/search/engine` コマンドを入力します。 このコマンドは、`mysql`、`elasticsearch` （Elasticsearch 2 が設定されていることを示す）、`elasticsearch5`、`elasticsearch6`、`elasticsearch7` の値、またはサードパーティの検索エンジンがインストールされていることを示すカスタム値を返します。 2.4.6 より前のバージョンの場合は、Elasticsearch 7 または OpenSearch エンジンの `elasticsearch7` 値を使用します。 バージョン 2.4.6 以降では、OpenSearch エンジンに `opensearch` の値を使用します。

* 管理者で、**[!UICONTROL Stores]** / [!UICONTROL Settings] / **[!UICONTROL Configuration]** / **[!UICONTROL Catalog]** / **[!UICONTROL Catalog]** / **[!UICONTROL Catalog Search]** / **[!UICONTROL Search Engine]** フィールドの値を確認します。

以下の節では、2.4.0 にアップグレードする前に実行する必要があるアクションについて説明します。

### MySQL

2.4 以降、MySQL はサポートされるカタログ検索エンジンではなくなりました。 アップグレードする前に、Elasticsearchまたは OpenSearch をインストールして設定する必要があります。 このプロセスのガイドとして役立つ次のリソースを使用します。

* [Elasticsearchのインストールと設定](../../configuration/search/overview-search.md)
* [Elasticsearchのインストール ](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
* 検索エンジンと連携するように [nginx](../../installation/prerequisites/search-engine/configure-nginx.md) または [Apache](../../installation/prerequisites/search-engine/configure-apache.md) を設定する
* [Elasticsearchを使用するようにCommerceを設定して ](../../configuration/search/configure-search-engine.md) インデックスを再作成します。

一部のサードパーティのカタログ検索エンジンは、Adobe Commerce検索エンジンの上で実行されます。 拡張機能を更新する必要があるかどうかを判断するには、ベンダーにお問い合わせください。

### MySQL 8.4 の変更

Adobe added support for MySQL 8.4 in the 2.4.8 release.
This section describes major changes to MySQL 8.4 that developers should be aware of.

#### Deprecated non-standard key

外部キーとして一意でないキーや部分的なキーを使用することは非標準であり、MySQL 8.4 では非推奨です。MySQL 8.4.0 以降では、[`restrict_fk_on_non_standard_key`](https://dev.mysql.com/doc/refman/8.4/en/server-system-variables.html#sysvar_restrict_fk_on_non_standard_key) を `OFF` に設定するか、`--skip-restrict-fk-on-non-standard-key` オプションを使用してサーバーを起動することで、このようなキーを明示的に有効にする必要があります。

#### MySQL 8.0 （またはそれ以前のバージョン）から MySQL 8.4 へのアップグレード

MySQL をバージョン 8.0 からバージョン 8.4 に適切にアップグレードするには、次の手順に従う必要があります。

1. メンテナンスモードを有効にする：

   ```bash
   bin/magento maintenance:enable
   ```

1. データベースのバックアップを作成します。

   ```bash
   bin/magento setup:backup --db
   ```

1. MySQL をバージョン 8.4 にアップグレードしてください。
1. `my.cnf` ファイルの `[mysqld]` で、`restrict_fk_on_non_standard_key` を `OFF` に設定します。

   ```bash
   [mysqld]
   restrict_fk_on_non_standard_key = OFF 
   ```

   >[!WARNING]
   >
   >`restrict_fk_on_non_standard_key` の値を `OFF` に変更しない場合、読み込み時に次のエラーが発生します。
   >
   ```sql
   > ERROR 6125 (HY000) at line 2164: Failed to add the foreign key constraint. Missing unique key for constraint 'CAT_PRD_FRONTEND_ACTION_PRD_ID_CAT_PRD_ENTT_ENTT_ID' in the referenced table 'catalog_product_entity'
   >```
1. MySQL サーバーを再起動します。
1. バックアップしたデータを MySQL に読み込みます。
1. キャッシュのクリーンアップ：

   ```bash
   bin/magento cache:clean
   ```

1. メンテナンスモードを無効にする：

   ```bash
   bin/magento maintenance:disable
   ```

#### MariaDB

{{$include /help/_includes/maria-db-config.md}}

### 検索エンジン

2.4.0 にアップグレードする前に、Elasticsearch 7.6 以降または OpenSearch 1.2 をインストールして設定する必要があります。Adobeは、Elasticsearch 2.x、5.x および 6.x をサポートしなくなりました。_設定ガイド_ の [ 検索エンジンの設定 ](../../configuration/search/configure-search-engine.md) では、Elasticsearchをサポートされているバージョンにアップグレードした後に実行する必要があるタスクについて説明しています。

データのバックアップ、潜在的な移行の問題の検出、実稼動環境にデプロイする前のアップグレードのテストに関する手順について詳しくは、[Elasticsearchのアップグレード ](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) を参照してください。 現在のElasticsearchのバージョンに応じて、クラスターの完全な再起動は必要な場合も必要ない場合もあります。

Elasticsearchには、Java Development Kit （JDK） 1.8 以降が必要です。 インストールされている JDK のバージョンを確認するには、[Java Software Development Kit （JDK）をインストールする ](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) を参照してください。

#### OpenSearch

OpenSearch is an open-source fork of Elasticsearch 7.10.2, following Elasticsearch&#39;s licensing change. Adobe Commerceの次のリリースでは、OpenSearch のサポートが導入されています。

* 2.4.6 （OpenSearch には別のモジュールと設定があります）
* 2.4.5
* 2.4.4
* 2.4.3-p2
* 2.3.7-p3

[Elasticsearchから OpenSearch への移行 ](opensearch-migration.md) は、上記のAdobe Commerceまたはそれ以降のバージョンにアップグレードする場合にのみ実行できます。

OpenSearch には JDK 1.8 以降が必要です。 インストールされている JDK のバージョンを確認するには、[Java Software Development Kit （JDK）をインストールする ](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) を参照してください。

[ 検索エンジン設定 ](../../configuration/search/configure-search-engine.md) では、検索エンジンを変更した後に実行する必要があるタスクについて説明します。

#### Elasticsearchのアップグレード

Elasticsearch 8.x のサポートは、Adobe Commerce 2.4.6 で導入されました。次の手順は、Elasticsearchを 7.x から 8.x にアップグレードする例を示しています。

>[!NOTE]
>
>今後の 2.4.8 リリースでは、Elasticsearch 8 モジュールがデフォルトで含まれており、別途インストールする必要がなくなるので、これらの手順は必要ありません。

1. Elasticsearch 7.x サーバーを 8.x にアップグレードし、が稼働していることを確認します。 [Elasticsearch ドキュメント ](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html) を参照してください。

1. `elasticsearch.yml` ファイルに次の設定を追加し、Elasticsearch 8.x サービスを再起動して、「`id_field_data`」フィールドを有効にします。

   ```yaml
   indices:
     id_field_data:
       enabled: true
   ```

   >[!INFO]
   >
   >Elasticsearch 8.x をサポートするために、Adobe Commerce 2.4.6 では `indices.id_field_data` プロパティがデフォルトで許可されず、`docvalue_fields` プロパティの `_id` フィールドが使用されます。

1. Adobe Commerce プロジェクトのルート ディレクトリで、Composer の依存関係を更新して `Magento_Elasticsearch7` モジュールを削除し、`Magento_Elasticsearch8` モジュールをインストールします。

   ```bash
   composer require magento/module-elasticsearch-8 --update-with-all-dependencies
   ```

   `psr/http-message` で依存関係エラーが発生した場合は、をクリックして次のトラブルシューティングのセクションを展開してください。

   +++トラブルシューティング

   Elasticsearch 8 のインストール中、特に `psr/http-message` との間で依存関係の競合が発生した場合は、次の手順に従ってこの問題を解決できます。

   1. First, require the Elasticsearch 8 module without updating other dependencies:

      ```bash
      composer require magento/module-elasticsearch-8 --no-update
      ```

   1. 次に、Elasticsearch 8 モジュールと `aws/aws-sdk-php` パッケージを更新します。

      ```bash
      composer update magento/module-elasticsearch-8 aws/aws-sdk-php -W
      ```

   この方法は、PHP 8.3 の 2.4.7-p4 で動作します。この問題は、`aws/aws-sdk-php` が `psr/http-message >= 2.0` を必要とし、競合を引き起こす可能性があるために発生します。 上記の手順は、これらの依存関係の問題を解決するのに役立ちます。

+++

1. プロジェクトコンポーネントを更新します。

   ```bash
   bin/magento setup:upgrade
   ```

1. [!DNL Admin] で [Elasticsearchを設定 ](../../configuration/search/configure-search-engine.md#configure-your-search-engine-from-the-admin) します。

1. カタログインデックスを再インデックス化します。

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. 有効なキャッシュタイプからすべての項目を削除します。

   ```bash
   bin/magento cache:clean
   ```

#### ダウングレードElasticsearch

誤ってサーバー上のElasticsearchのバージョンをアップグレードした場合や、他の理由でダウングレードが必要と判断した場合は、Adobe Commerce プロジェクトの依存関係も更新する必要があります。 例えば、Elasticsearch 8.x から 7.x にダウングレードするには、次のようにします

1. Elasticsearch 8.x サーバーを 7.x にダウングレードし、が起動して実行中であることを確認します。 [Elasticsearch ドキュメント ](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html) を参照してください。

1. Adobe Commerce プロジェクトのルート ディレクトリで、Composer 依存関係を更新して `Magento_Elasticsearch8` モジュールとその Composer 依存関係を削除し、`Magento_Elasticsearch7` モジュールをインストールします。

   ```bash
   composer remove magento/module-elasticsearch-8
   ```

1. プロジェクトコンポーネントを更新します。

   ```bash
   bin/magento setup:upgrade
   ```

1. [!DNL Admin] で [Elasticsearchを設定 ](../../configuration/search/configure-search-engine.md#configure-your-search-engine-from-the-admin) します。

1. カタログインデックスを再インデックス化します。

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. 有効なキャッシュタイプからすべての項目を削除します。

   ```bash
   bin/magento cache:clean
   ```

### サードパーティの拡張機能

使用している拡張機能がAdobe Commerce リリースと完全に互換性があるかどうかを確認するには、検索エンジンのベンダーにお問い合わせください。

## データベース テーブル形式を変換

すべてのデータベース テーブルの形式を `COMPACT` から `DYNAMIC` に変換する必要があります。 また、ストレージエンジンのタイプを `MyISAM` から `InnoDB` に変換する必要があります。 [ ベストプラクティス ](../../implementation-playbook/best-practices/maintenance/mariadb-upgrade.md) を参照してください。

## 開いているファイルの上限を設定

開いているファイル数の制限（ulimit）を設定すると、長いクエリ文字列を何度も繰り返し呼び出したり、`bin/magento setup:rollback` コマンドを使用する際の問題によって発生する障害を回避できます。 このコマンドは、UNIX シェルごとに異なります。 `ulimit` コマンドの詳細については、個々のフレーバーを参照してください。

Adobeでは、開いているファイル [ulimit](https://ss64.com/bash/ulimit.html) を `65536` 以上の値に設定することをお勧めしますが、必要に応じて大きな値を使用できます。 ulimit は、コマンドラインで設定することも、ユーザーのシェルの恒久的な設定にすることもできます。

コマンドラインから ulimit を設定するには：

1. [ ファイルシステム所有者 ](../../installation/prerequisites/file-system/overview.md) に切り替えます。
1. ulimit を `65536` に設定します。

   ```bash
   ulimit -n 65536
   ```

Bash シェルに値を設定するには：

1. [ ファイルシステム所有者 ](../../installation/prerequisites/file-system/overview.md) に切り替えます。
1. `/home/<username>/.bashrc` をテキストエディターで開きます。
1. 次の行を追加します。

   ```bash
   ulimit -n 65536
   ```

1. 変更内容を `.bashrc` ファイルに保存し、テキストエディターを終了します。

>[!IMPORTANT]
>
>`php.ini` ファイルの `pcre.recursion_limit` プロパティの値は設定しないことをお勧めします。設定すると、エラー通知のない不完全なロールバックが生じる可能性があるからです。

## Cron ジョブが実行中であることを確認

UNIX タスクスケジューラー `cron` は、Adobe Commerceの日々の操作にとって重要です。 インデックス再作成、ニュースレター、メール、サイトマップなどのスケジュールを設定します。 いくつかの機能では、ファイルシステムの所有者として少なくとも 1 つの cron ジョブを実行する必要があります。

cron ジョブが正しく設定されていることを確認するには、ファイルシステムの所有者として次のコマンドを入力して crontab を確認します。

>[!NOTE]
>
>crontab は、cron ジョブの実行を担当する設定ファイルです。

```bash
crontab -l
```

次のような結果が表示されます。

```cron
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

Cron が実行されていないもう 1 つの症状は、Admin で次のエラーが発生することです。

![ システムメッセージ - cron が実行されていない ](../../assets/upgrade-guide/cron-not-running.png)

このエラーを確認するには、次のように、ウィンドウの上部にある **システムメッセージ** をクリックします。

![ システムメッセージ通知 ](../../assets/upgrade-guide/system-messages.png)

詳しくは、[cron の設定と実行 ](../../configuration/cli/configure-cron-jobs.md) を参照してください。

## Set DATA_CONVERTER_BATCH_SIZE

Adobe Commerce 2.4 には、一部のデータをシリアル化されたから JSON に変換する必要があるセキュリティ強化が含まれています。 この変換はアップグレード中に行われ、データベースに含まれるデータの量によっては、長い時間がかかる場合があります。

最も影響を受けるのは、次の表です。

* `catalogrule`
* `core_config_data`
* `magento_reward_history`
* `quote_payment`
* `quote`
* `sales_order_payment`
* `sales_order`
* `salesrule`
* `url_rewrite`

データが大量にある場合は、環境変数 `DATA_CONVERTER_BATCH_SIZE` の値を設定することでパフォーマンスを向上できます。 デフォルトでは、値は `50,000` に設定されています。

環境変数を設定するには：

1. [ ファイルシステム所有者 ](../../installation/prerequisites/file-system/overview.md) に切り替えます。
1. 次の変数を設定します。

   ```bash
   export DATA_CONVERTER_BATCH_SIZE=100000
   ```

   >[!NOTE]
   >
   > `DATA_CONVERTER_BATCH_SIZE` にはメモリが必要です。最初にテストせずに、大きな値（約 1 GB）に設定しないでください。

1. アップグレードが完了したら、この変数の設定を解除できます。

   ```bash
   unset DATA_CONVERTER_BATCH_SIZE
   ```

## ファイルシステムの権限の確認

セキュリティ上の理由から、Adobe Commerceにはファイルシステムに対する特定の権限が必要です。 権限は _[所有権](../../upgrade/prepare/prerequisites.md#verify-file-system-permissions)_ とは異なります。 Ownership determines who can perform actions on the file system; permissions determine what the user can do.

ファイルシステム内のディレクトリは、[ ファイルシステム所有者 ](../../installation/prerequisites/file-system/overview.md) グループによって書き込み可能でなければなりません。

ファイルシステムの権限が正しく設定されていることを確認するには、アプリケーションサーバーにログインするか、ホスティングプロバイダーの file manager アプリケーションを使用します。

例えば、アプリケーションが `/var/www/html/magento2` にインストールされている場合は、次のコマンドを入力します。

```bash
ls -l /var/www/html/magento2
```

サンプル出力：

```console
total 1028
drwxrwx---. 12 magento_user apache   4096 Jun  7 07:55 .
drwxr-xr-x.  3 root         root     4096 May 11 14:29 ..
drwxrwx---.  4 magento_user apache   4096 Jun  7 07:53 app
drwxrwx---.  2 magento_user apache   4096 Jun  7 07:53 bin
-rw-rw----.  1 magento_user apache 439792 Apr 27 21:23 CHANGELOG.md
-rw-rw----.  1 magento_user apache   3422 Apr 27 21:23 composer.json
-rw-rw----.  1 magento_user apache 425214 Apr 27 21:27 composer.lock
-rw-rw----.  1 magento_user apache   3425 Apr 27 21:23 CONTRIBUTING.md
-rw-rw----.  1 magento_user apache  10011 Apr 27 21:23 CONTRIBUTOR_LICENSE_AGREEMENT.html
-rw-rw----.  1 magento_user apache    631 Apr 27 21:23 COPYING.txt
drwxrwx---.  4 magento_user apache   4096 Jun  7 07:53 dev
-rw-rw----.  1 magento_user apache   2926 Apr 27 21:23 Gruntfile.js
-rw-rw----.  1 magento_user apache   7592 Apr 27 21:23 .htaccess
-rw-rw----.  1 magento_user apache   6419 Apr 27 21:23 .htaccess.sample
drwxrwx---.  4 magento_user apache   4096 Jun  7 07:53 lib
-rw-rw----.  1 magento_user apache  10376 Apr 27 21:23 LICENSE_AFL.txt
-rw-rw----.  1 magento_user apache  30634 Apr 27 21:23 LICENSE_EE.txt
-rw-rw----.  1 magento_user apache  10364 Apr 27 21:23 LICENSE.txt
-rw-rw----.  1 magento_user apache   4108 Apr 27 21:23 nginx.conf.sample
-rw-rw----.  1 magento_user apache   1427 Apr 27 21:23 package.json
-rw-rw----.  1 magento_user apache   1659 Apr 27 21:23 .php_cs
-rw-rw----.  1 magento_user apache    804 Apr 27 21:23 php.ini.sample
drwxrwx---.  2 magento_user apache   4096 Jun  7 07:53 phpserver
drwxrwx---.  6 magento_user apache   4096 Jun  7 07:53 pub
-rw-rw----.  1 magento_user apache   2207 Apr 27 21:23 README_EE.md
drwxrwx---.  7 magento_user apache   4096 Jun  7 07:53 setup
-rw-rw----.  1 magento_user apache   3731 Apr 27 21:23 .travis.yml
drwxrwx---.  7 magento_user apache   4096 Jun  7 07:53 update
drwxrws---. 11 magento_user apache   4096 Jun 13 16:05 var
drwxrws---. 29 magento_user apache   4096 Jun  7 07:53 vendor
```

サンプル出力の説明については、次を参照してください。

* ほとんどのファイルは `-rw-rw----` で、これは `660` です
* `drwxrwx---` = `770`
* `-rw-rw-rw-` = `666`
* ファイルシステムの所有者は `magento_user`

詳細情報を取得するには、次のコマンドを入力します。

```bash
ls -la /var/www/html/magento2/pub
```

Adobe Commerceは静的ファイルアセットを `pub` のサブディレクトリにデプロイするので、権限と所有権を確認することもお勧めします。

詳しくは、[ ファイルシステムの権限と所有権 ](../../installation/prerequisites/file-system/overview.md) を参照してください。

## `pub/` ディレクトリルートの設定

詳しくは、[ セキュリティを強化するための docroot の変更 ](../../installation/tutorials/docroot.md) を参照してください。

## Composer アップデート プラグインのインストール

[`magento/composer-root-update-plugin`](https://github.com/magento/composer-root-update-plugin) Composer プラグインは、新しい製品要件に更新する前に、ルート プロジェクト `composer.json` ファイルに加える必要がある変更を解決します。

このプラグインは、依存関係の競合を手動で特定および修正するのではなく、特定して解決を支援することで、手動アップグレードを部分的に自動化します。

プラグインをインストールするには：

1. パッケージを `composer.json` ファイルに追加します。

   ```bash
   composer require magento/composer-root-update-plugin ~2.0 --no-update
   ```

1. 依存関係を更新します。

   ```bash
   composer update
   ```
