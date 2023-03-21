---
title: 前提条件
description: 前提条件の手順を完了して、Adobe Commerceプロジェクトのアップグレードを準備します。
source-git-commit: 5f86717d79569cac3f95a4c10a55b48f92858466
workflow-type: tm+mt
source-wordcount: '1639'
ht-degree: 0%

---


# アップグレードの前提条件

Adobe Commerceの実行に何が必要かを理解することが重要です。 まず、 [システム要件](../../installation/system-requirements.md) アップグレード先のバージョンの

必要システム構成を確認した後、システムをアップグレードする前に、次の前提条件を満たす必要があります。

* すべてのソフトウェアを更新
* サポートされている検索エンジンがインストールされていることを確認します。
* データベーステーブル形式の変換
* 開くファイルの制限を設定する
* Cron ジョブが実行中であることを確認します。
* 設定 `DATA_CONVERTER_BATCH_SIZE`
* ファイルシステムの権限の検証
* を `pub/` ディレクトリルート
* Composer の更新プラグインをインストールします。

## すべてのソフトウェアを更新

この [システム要件](../../installation/system-requirements.md) Adobe Commerceリリースでテストされたサードパーティソフトウェアのバージョンを正確に説明します。

環境内のすべてのシステム要件と依存関係を更新していることを確認します。 PHP を参照 [7.4](https://www.php.net/manual/en/migration74.php), PHP [8.0](https://www.php.net/manual/en/migration80.php), PHP [8.1](https://www.php.net/manual/en/migration81.php)、および [必要な PHP 設定](../../installation/prerequisites/php-settings.md#php-settings).

>[!NOTE]
>
>Adobe Commerce on cloud infrastructure Pro プロジェクトの場合、 [サポート](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) ステージング環境と実稼動環境でサービスをインストールまたは更新するためのチケット。 必要なサービスの変更を示し、更新した `.magento.app.yaml` および `services.yaml` ファイルと PHP のバージョンをチケット内で指定します。 Cloud インフラストラクチャチームがプロジェクトを更新するまでに最大 48 時間かかる場合があります。 詳しくは、 [サポートされるソフトウェアとサービス](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html#supported-software-and-services).

## サポートされている検索エンジンがインストールされていることを確認します。

Adobe Commerceでは、Elasticsearchを使用するために、ソフトウェアまたは OpenSearch をインストールする必要があります。

**2.3.x から 2.4 にアップグレードする場合** 2.3.x インスタンスで、カタログ検索エンジンとして MySQL、Elasticsearch、またはサードパーティの拡張機能を使用しているかどうかを確認する必要があります。 結果によって、必要な作業が決まります _前_ 2.4 へのアップグレード

**2.3.x または 2.4.x のリリース行内でパッチリリースをアップグレードする場合**(Elasticsearch7.x が既にインストールされている場合 ) [OpenSearch に移行](opensearch-migration.md).

コマンドラインまたは管理者を使用して、カタログ検索エンジンを決定できます。

* 次を入力します。 `bin/magento config:show catalog/search/engine` コマンドを使用します。 このコマンドは、 `mysql`, `elasticsearch` ( これはElasticsearch2 が設定されていることを示します )。 `elasticsearch5`, `elasticsearch6`, `elasticsearch7`またはカスタム値。サードパーティの検索エンジンがインストールされていることを示します。 2.4.6 より前のバージョンでは、 `elasticsearch7` Elasticsearch7 または OpenSearch エンジンの値。 バージョン 2.4.6 以降では、 `opensearch` OpenSearch エンジンの値。

* 管理者から、 **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** > **[!UICONTROL Search Engine]** フィールドに入力します。

次の節では、2.4.0 にアップグレードする前に実行する必要のあるアクションについて説明します。

### MySQL

2.4 以降、MySQL はサポート対象のカタログ検索エンジンではなくなりました。 アップグレードする前に、Elasticsearchまたは OpenSearch をインストールして設定する必要があります。 このプロセスの手引きとして、次のリソースを使用します。

* [インストールとElasticsearch](../../configuration/search/overview-search.md)
* [インストールElasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
* 設定 [nginx](../../installation/prerequisites/search-engine/configure-nginx.md) または [Apache](../../installation/prerequisites/search-engine/configure-apache.md) 検索エンジンを使用する
* [コマースでElasticsearchを使用するように設定](../../configuration/search/configure-search-engine.md) と再インデックス

一部のサードパーティカタログ検索エンジンは、Adobe Commerce検索エンジンの上で動作します。 ベンダーに問い合わせて、拡張機能を更新する必要があるかどうかを判断してください。

#### MariaDB

{{$include /help/_includes/maria-db-config.md}}

### 検索エンジン

2.4.0 にアップグレードする前に、Elasticsearch7.6 以降または OpenSearch 1.2 をインストールして設定する必要があります。Adobeは、Elasticsearch2.x、5.x および 6.x をサポートしなくなりました。 [検索エンジンの設定](../../configuration/search/configure-search-engine.md) 内 _設定ガイド_ サポート対象のバージョンにアップグレードした後にElasticsearchを実行する必要があるタスクについて説明します。

参照： [アップグレードElasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) データのバックアップ、移行に関する潜在的な問題の検出、アップグレードのテストを実稼動環境にデプロイする前に行う手順について詳しくは、 現在のバージョンのElasticsearchに応じて、完全なクラスターの再起動が必要な場合と不要な場合があります。

Elasticsearchには Java Development Kit(JDK)1.8 以降が必要です。 詳しくは、 [Java Software Development Kit(JDK) のインストール](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) をクリックして、インストールされている JDK のバージョンを確認します。

#### OpenSearch

OpenSearch は、Elasticsearch7.10.2のオープンソースのフォークで、Elasticsearchのライセンスの変更に続いています。 Adobe Commerceの次のリリースでは、OpenSearch のサポートが導入されています。

* 2.4.6 （OpenSearch は別のモジュールと設定を持っています）
* 2.4.5
* 2.4.4
* 2.4.3-p2
* 2.3.7-p3

以下が可能です。 [Elasticsearchから OpenSearch への移行](opensearch-migration.md) 上記（またはそれ以降）のバージョンのAdobe Commerceにアップグレードする場合にのみ有効です。

OpenSearch には JDK 1.8 以降が必要です。 詳しくは、 [Java Software Development Kit(JDK) のインストール](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) をクリックして、インストールされている JDK のバージョンを確認します。

[検索エンジンの設定](../../configuration/search/configure-search-engine.md) では、検索エンジンを変更した後に実行する必要があるタスクについて説明します。

#### アップグレードElasticsearch

Elasticsearch8.x のサポートは、Adobe Commerce 2.4.6 で導入されました。次の手順は、Elasticsearchを 7.x から 8.x にアップグレードする例を示しています。

1. Elasticsearch7.x サーバーを 8.x にアップグレードし、が起動して実行されていることを確認します。 詳しくは、 [Elasticsearch文書](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html).

1. を有効にします。 `id_field_data` フィールドで次の設定を `elasticsearch.yml` ファイルを作成し、Elasticsearch8.x サービスを再起動します。

   ```yaml
   indices:
     id_field_data:
       enabled: true
   ```

   >[!INFO]
   >
   >Elasticsearch8.x をサポートするために、Adobe Commerce 2.4.6 では `indices.id_field_data` プロパティはデフォルトで、 `_id` フィールド `docvalue_fields` プロパティ。

1. Adobe Commerceプロジェクトのルートディレクトリで、Composer の依存関係を更新して、 `Magento_Elasticsearch7` モジュールとインストール `Magento_Elasticsearch8` モジュール。

   ```bash
   composer require magento/module-elasticsearch-8 --update-with-all-dependencies
   ```

1. プロジェクトコンポーネントを更新します。

   ```bash
   bin/magento setup:upgrade
   ```

1. [設定Elasticsearch](../../configuration/search/configure-search-engine.md#configure-your-search-engine-from-the-admin) 内 [!DNL Admin].

1. カタログインデックスを再インデックスします。

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. 有効なキャッシュタイプからすべての項目を削除します。

   ```bash
   bin/magento cache:clean
   ```

#### ダウングレードElasticsearch

誤ってサーバー上のElasticsearchのバージョンをアップグレードした場合や、他の理由でダウングレードする必要がある場合は、Adobe Commerceプロジェクトの依存関係も更新する必要があります。 例えば、Elasticsearch8.x から 7.x にダウングレードするには、次のようにします。

1. Elasticsearch8.x サーバーを 7.x にダウングレードし、が起動して実行されていることを確認します。 詳しくは、 [Elasticsearch文書](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html).

1. Adobe Commerceプロジェクトのルートディレクトリで、Composer の依存関係を更新して、 `Magento_Elasticsearch8` モジュールとそのコンポーザーの依存関係とインストール `Magento_Elasticsearch7` モジュール。

   ```bash
   composer remove magento/module-elasticsearch-8
   ```

1. プロジェクトコンポーネントを更新します。

   ```bash
   bin/magento setup:upgrade
   ```

1. [設定Elasticsearch](../../configuration/search/configure-search-engine.md#configure-your-search-engine-from-the-admin) 内 [!DNL Admin].

1. カタログインデックスを再インデックスします。

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. 有効なキャッシュタイプからすべての項目を削除します。

   ```bash
   bin/magento cache:clean
   ```

### サードパーティの拡張機能

拡張機能とAdobe Commerceリリースの互換性が完全にあるかどうかについては、検索エンジンのベンダーに問い合わせることをお勧めします。

## データベーステーブル形式の変換

すべてのデータベーステーブルの形式は、次の形式から変換する必要があります： `COMPACT` から `DYNAMIC`. また、次のストレージエンジンタイプを変換する必要があります： `MyISAM` から `InnoDB`. 詳しくは、 [ベストプラクティス](../../implementation-playbook/best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.md).

## 開くファイルの制限を設定する

開くファイルの制限 (ulimit) を設定すると、長いクエリ文字列の複数の再帰呼び出しや、 `bin/magento setup:rollback` コマンドを使用します。 このコマンドは、UNIX シェルごとに異なります。 詳しくは、個々のフレーバーを参照してください。 `ulimit` コマンドを使用します。

Adobeでは、開くファイルを設定することをお勧めします [制限](https://ss64.com/bash/ulimit.html) 値に `65536` または複数の値を指定できますが、必要に応じて、より大きな値を使用できます。 コマンドラインで ulimit を設定するか、ユーザーのシェルに対して永続的な設定を指定できます。

コマンドラインから ulimit を設定するには、次の手順に従います。

1. 次に切り替え： [ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md).
1. 制限をに設定します。 `65536`.

   ```bash
   ulimit -n 65536
   ```

Bash シェルに値を設定するには、次の手順を実行します。

1. 次に切り替え： [ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md).
1. 開く `/home/<username>/.bashrc` をクリックします。
1. 次の行を追加します。

   ```bash
   ulimit -n 65536
   ```

1. 変更を `.bashrc` ファイルを開き、テキストエディタを終了します。

>[!IMPORTANT]
>
>この場合、 `pcre.recursion_limit` プロパティを `php.ini` ファイルを作成する必要があります。

## Cron ジョブが実行中であることを確認します。

UNIX タスクスケジューラ `cron` は、毎日のAdobe Commerce操作にとって重要です。 インデックス再作成、ニュースレター、電子メール、サイトマップなどのスケジュールを設定します。 いくつかの機能を使用するには、ファイルシステムの所有者として少なくとも 1 つの cron ジョブを実行する必要があります。

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

cron が動作しないもう 1 つの症状は、管理画面で次のエラーが発生することです。

![](../../assets/upgrade-guide/cron-not-running.png)

エラーを確認するには、 **システムメッセージ** を次のようにして、ウィンドウの上部に表示します。

![](../../assets/upgrade-guide/system-messages.png)

詳しくは、 [cron の設定と実行](../../configuration/cli/configure-cron-jobs.md) を参照してください。

## DATA_CONVERTER_BATCH_SIZE を設定

Adobe Commerce 2.4 には、一部のデータをシリアル化から JSON に変換する必要があるセキュリティ強化が含まれています。 この変換はアップグレード中に発生し、データベース内のデータ量に応じて時間がかかる場合があります。

次の表が最も影響を受けます。

* `catalogrule`
* `core_config_data`
* `magento_reward_history`
* `quote_payment`
* `quote`
* `sales_order_payment`
* `sales_order`
* `salesrule`
* `url_rewrite`

大量のデータがある場合は、環境変数の値を設定してパフォーマンスを向上させることができます。 `DATA_CONVERTER_BATCH_SIZE`. デフォルトでは、値はに設定されています。 `50,000`.

環境変数を設定するには：

1. 次に切り替え： [ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md).
1. 変数を設定します。

   ```bash
   export DATA_CONVERTER_BATCH_SIZE=100000
   ```

   >[!NOTE]
   >
   > `DATA_CONVERTER_BATCH_SIZE` メモリが必要です。最初にテストしないで、大きな値（約 1 GB）に設定しないでください。

1. アップグレードが完了したら、変数の設定を解除できます。

   ```bash
   unset DATA_CONVERTER_BATCH_SIZE
   ```

## ファイルシステムの権限の検証

セキュリティ上の理由から、Adobe Commerceにはファイルシステムに対する特定の権限が必要です。 権限は _[所有権](../../upgrade/prepare/prerequisites.md#verify-file-system-permissions)_. 所有権によって、ファイル・システム上で誰がアクションを実行できるかが決まります。権限は、ユーザーが実行できる操作を決定します。

ファイルシステム内のディレクトリは、 [ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md) グループ化します。

ファイルシステムの権限が正しく設定されていることを確認するには、アプリケーションサーバーにログインするか、ホスティングプロバイダーの File Manager アプリケーションを使用します。

例えば、アプリケーションが `/var/www/html/magento2`:

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

* ほとんどのファイルは `-rw-rw----`は、 `660`
* `drwxrwx---` = `770`
* `-rw-rw-rw-` = `666`
* ファイルシステムの所有者は、 `magento_user`

詳細を確認するには、次のコマンドを入力します。

```bash
ls -la /var/www/html/magento2/pub
```

これは、Adobe Commerceがのサブディレクトリに静的ファイルアセットをデプロイするからです `pub`では、そこで権限と所有権も検証することをお勧めします。

詳しくは、 [ファイル・システムの権限と所有権](../../installation/prerequisites/file-system/overview.md).

## を `pub/` ディレクトリルート

詳しくは、 [セキュリティを向上させるために docroot を変更](../../installation/tutorials/docroot.md) を参照してください。

## Composer の更新プラグインをインストールします。

この [`magento/composer-root-update-plugin`](https://github.com/magento/composer-root-update-plugin) Composer プラグインは、ルートプロジェクトに対して行う必要のある変更を解決します `composer.json` ファイルを更新してから、新しい製品要件に更新してください。

プラグインは、手動アップグレードを部分的に自動化し、依存関係の競合を特定して手動で修正する代わりに、特定して解決するのに役立ちます。

プラグインをインストールするには：

1. パッケージを `composer.json` ファイル。

   ```bash
   composer require magento/composer-root-update-plugin ~2.0 --no-update
   ```

1. 依存関係を更新します。

   ```bash
   composer update
   ```
