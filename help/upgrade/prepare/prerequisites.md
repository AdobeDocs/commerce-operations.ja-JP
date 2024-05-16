---
title: 前提条件を完了
description: 次の前提条件の手順を完了して、アップグレード用のAdobe Commerce プロジェクトを準備します。
exl-id: f7775900-1d10-4547-8af0-3d1283d9b89e
source-git-commit: fb449f0ee7d503d0c7ba60bf6bfbe3f528060606
workflow-type: tm+mt
source-wordcount: '1604'
ht-degree: 0%

---

# アップグレードの前提条件の完了

Adobe Commerceの実行に必要な事項を理解することが重要です。 最初にを確認する必要があります [必要システム構成](../../installation/system-requirements.md) アップグレード先のバージョンの場合。

システム要件を確認した後、システムをアップグレードする前に次の前提条件を満たす必要があります。

* すべてのソフトウェアを更新する
* サポートされている検索エンジンがインストールされていることを確認します
* データベース テーブル形式を変換
* 開いているファイルの上限を設定
* Cron ジョブが実行中であることを確認
* を設定 `DATA_CONVERTER_BATCH_SIZE`
* ファイルシステムの権限の確認
* を `pub/` ディレクトリルート
* Composer アップデート プラグインのインストール

## すべてのソフトウェアを更新する

この [必要システム構成](../../installation/system-requirements.md) Adobe Commerce リリースでテストされているサードパーティソフトウェアのバージョンを正確に説明する。

環境内のすべてのシステム要件と依存関係を更新していることを確認してください。 PHP を参照 [7.4](https://www.php.net/manual/en/migration74.php), PHP [8.0](https://www.php.net/manual/en/migration80.php), PHP [8.1](https://www.php.net/manual/en/migration81.php)、および [必須の PHP 設定](../../installation/prerequisites/php-settings.md#php-settings).

>[!NOTE]
>
>Adobe Commerce on cloud infrastructure Pro プロジェクトの場合は、を作成する必要があります。 [サポート](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) ステージング環境および実稼動環境でサービスをインストールまたは更新するためのチケット。 必要なサービス変更を示し、更新済みの内容を含める `.magento.app.yaml` および `services.yaml` チケット内のファイルと PHP バージョン。 クラウドインフラストラクチャチームがプロジェクトを更新するまで、最大 48 時間かかる場合があります。 参照： [サポート対象のソフトウェアとサービス](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html#supported-software-and-services).

## サポートされている検索エンジンがインストールされていることを確認します

Adobe Commerceを使用するには、Elasticsearchまたは OpenSearch をインストールする必要があります。

**2.3.x から 2.4 にアップグレードする場合**&#x200B;を使用している場合は、2.3.x インスタンスのカタログ検索エンジンとして、MySQL、Elasticsearchまたはサードパーティの拡張機能を使用しているかどうかを確認する必要があります。 その結果によって、何をしなければならないかが決まります _次の前_ 2.4 へのアップグレード。

**2.3.x または 2.4.x のリリース行内でパッチ リリースをアップグレードしている場合** Elasticsearch 7.x が既にインストールされている場合は、次の手順を実行できます [opensearch への移行](opensearch-migration.md).

コマンドラインまたは管理者を使用して、カタログ検索エンジンを決定できます。

* を入力 `bin/magento config:show catalog/search/engine` コマンド。 コマンドは、次の値を返します `mysql`, `elasticsearch` （Elasticsearch 2 が設定されていることを示します）。 `elasticsearch5`, `elasticsearch6`, `elasticsearch7`、またはサードパーティの検索エンジンをインストールしたことを示すカスタム値。 2.4.6 より前のバージョンの場合は、 `elasticsearch7` Elasticsearch 7 または OpenSearch エンジンの値。 バージョン 2.4.6 以降では、を使用します。 `opensearch` opensearch エンジンの値。

* 管理者で、の値を確認します。 **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** > **[!UICONTROL Search Engine]** フィールド。

以下の節では、2.4.0 にアップグレードする前に実行する必要があるアクションについて説明します。

### MySQL

2.4 以降、MySQL はサポートされるカタログ検索エンジンではなくなりました。 アップグレードする前に、Elasticsearchまたは OpenSearch をインストールして構成する必要があります。 このプロセスのガイドとして役立つ次のリソースを使用します。

* [Elasticsearchのインストールと設定](../../configuration/search/overview-search.md)
* [Elasticsearchのインストール](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
* 設定 [nginx](../../installation/prerequisites/search-engine/configure-nginx.md) または [Apache](../../installation/prerequisites/search-engine/configure-apache.md) 検索エンジンを操作するには
* [Elasticsearchを使用するようにCommerceを設定する](../../configuration/search/configure-search-engine.md) および再インデックス

一部のサードパーティのカタログ検索エンジンは、Adobe Commerce検索エンジンの上で実行されます。 拡張機能を更新する必要があるかどうかを判断するには、ベンダーにお問い合わせください。

#### MariaDB

{{$include /help/_includes/maria-db-config.md}}

### 検索エンジン

2.4.0 にアップグレードする前に、Elasticsearch 7.6 以降または OpenSearch 1.2 をインストールして設定する必要があります。Adobeは、Elasticsearch 2.x、5.x および 6.x をサポートしなくなりました。 [検索エンジン設定](../../configuration/search/configure-search-engine.md) が含まれる _設定ガイド_ では、Elasticsearchをサポート対象のバージョンにアップグレードした後に実行する必要があるタスクについて説明します。

こちらを参照してください [Elasticsearchのアップグレード](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) データのバックアップ、潜在的な移行の問題の検出、実稼動環境にデプロイする前のアップグレードのテストに関する完全な手順について説明します。 現在のElasticsearchのバージョンに応じて、クラスターの完全な再起動は必要な場合と不要な場合があります。

Elasticsearchには、Java Development Kit （JDK） 1.8 以降が必要です。 参照： [Java Software Development Kit （JDK）をインストールします。](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) インストールされている JDK のバージョンを確認します。

#### OpenSearch

OpenSearch は、Elasticsearchのライセンスの変更に伴い、Elasticsearch 7.10.2 のオープンソースのフォークになりました。 Adobe Commerceの次のリリースでは、OpenSearch のサポートが導入されています。

* 2.4.6 （OpenSearch には別のモジュールと設定があります）
* 2.4.5
* 2.4.4
* 2.4.3-p2
* 2.3.7-p3

次のことができます [Elasticsearchから OpenSearch への移行](opensearch-migration.md) 上記の（またはそれ以降の）Adobe Commerceのバージョンにアップグレードする場合のみ。

OpenSearch には JDK 1.8 以降が必要です。 参照： [Java Software Development Kit （JDK）をインストールします。](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) インストールされている JDK のバージョンを確認します。

[検索エンジン設定](../../configuration/search/configure-search-engine.md) 検索エンジンを変更した後に実行する必要があるタスクについて説明します。

#### アップグレードElasticsearch

Elasticsearch 8.x のサポートは、Adobe Commerce 2.4.6 で導入されました。以下の手順は、Elasticsearchを 7.x から 8.x にアップグレードする例を示しています。

1. Elasticsearch 7.x サーバを 8.x にアップグレードし、が稼働していることを確認します。 を参照してください。 [Elasticsearchドキュメント](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html).

1. を有効にする `id_field_data` フィールドで、次の設定をに追加します `elasticsearch.yml` にファイルを保存し、Elasticsearch 8.x サービスを再起動します。

   ```yaml
   indices:
     id_field_data:
       enabled: true
   ```

   >[!INFO]
   >
   >Elasticsearch 8.x をサポートするために、Adobe Commerce 2.4.6 では `indices.id_field_data` プロパティはデフォルトで次を使用します `_id` のフィールド `docvalue_fields` プロパティ。

1. Adobe Commerce プロジェクトのルート ディレクトリで、Composer の依存関係を更新して、 `Magento_Elasticsearch7` モジュールとインストール `Magento_Elasticsearch8` モジュール。

   ```bash
   composer require magento/module-elasticsearch-8 --update-with-all-dependencies
   ```

1. プロジェクトコンポーネントを更新します。

   ```bash
   bin/magento setup:upgrade
   ```

1. [Elasticsearchの設定](../../configuration/search/configure-search-engine.md#configure-your-search-engine-from-the-admin) が含まれる [!DNL Admin].

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

1. Elasticsearch 8.x サーバを 7.x にダウングレードし、が稼働していることを確認します。 を参照してください。 [Elasticsearchドキュメント](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html).

1. Adobe Commerce プロジェクトのルート ディレクトリで、Composer の依存関係を更新して、 `Magento_Elasticsearch8` モジュールとその Composer の依存関係およびインストール `Magento_Elasticsearch7` モジュール。

   ```bash
   composer remove magento/module-elasticsearch-8
   ```

1. プロジェクトコンポーネントを更新します。

   ```bash
   bin/magento setup:upgrade
   ```

1. [Elasticsearchの設定](../../configuration/search/configure-search-engine.md#configure-your-search-engine-from-the-admin) が含まれる [!DNL Admin].

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

すべてのデータベース テーブルの形式を変換する必要があります。 `COMPACT` 対象： `DYNAMIC`. また、次の場所からストレージエンジンタイプを変換する必要があります `MyISAM` 対象： `InnoDB`. 参照： [ベストプラクティス](../../implementation-playbook/best-practices/maintenance/mariadb-upgrade.md).

## 開いているファイルの上限を設定

開いているファイル数の制限（ulimit）を設定すると、長いクエリ文字列を何度も繰り返し呼び出したり、 `bin/magento setup:rollback` コマンド。 このコマンドは、UNIX シェルごとに異なります。 詳細については、それぞれのフレーバーを参照してください `ulimit` コマンド。

Adobeでは、開いているファイルを設定することをお勧めします [ulimit](https://ss64.com/bash/ulimit.html) の値に `65536` 以上の値を指定できますが、必要に応じて、より大きな値を使用できます。 ulimit は、コマンドラインで設定することも、ユーザーのシェルの恒久的な設定にすることもできます。

コマンドラインから ulimit を設定するには：

1. に切り替え [ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md).
1. ulimit をに設定 `65536`.

   ```bash
   ulimit -n 65536
   ```

Bash シェルに値を設定するには：

1. に切り替え [ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md).
1. 開く `/home/<username>/.bashrc` テキストエディター。
1. 次の行を追加します。

   ```bash
   ulimit -n 65536
   ```

1. 変更をに保存します。 `.bashrc` ファイルを開き、テキストエディターを終了します。

>[!IMPORTANT]
>
>の値は設定しないことをお勧めします `pcre.recursion_limit` のプロパティ `php.ini` 失敗の通知がない場合、ロールバックが不完全になる可能性があるためです。

## Cron ジョブが実行中であることを確認

UNIX のタスク スケジューラ `cron` は、Adobe Commerceの日々の業務にとって重要です。 インデックス再作成、ニュースレター、メール、サイトマップなどのスケジュールを設定します。 いくつかの機能では、ファイルシステムの所有者として少なくとも 1 つの cron ジョブを実行する必要があります。

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

![](../../assets/upgrade-guide/cron-not-running.png)

エラーを表示するには、次をクリックします： **システムメッセージ** ウィンドウの上部に次のように表示されます。

![](../../assets/upgrade-guide/system-messages.png)

参照： [Cron の設定と実行](../../configuration/cli/configure-cron-jobs.md) を参照してください。

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

データが大量にある場合は、環境変数の値を設定することでパフォーマンスを向上できます。 `DATA_CONVERTER_BATCH_SIZE`. デフォルトでは、値はに設定されています。 `50,000`.

環境変数を設定するには：

1. に切り替え [ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md).
1. 次の変数を設定します。

   ```bash
   export DATA_CONVERTER_BATCH_SIZE=100000
   ```

   >[!NOTE]
   >
   > `DATA_CONVERTER_BATCH_SIZE` メモリが必要です。最初にテストせずに、大きな値（約 1 GB）に設定しないでください。

1. アップグレードが完了したら、この変数の設定を解除できます。

   ```bash
   unset DATA_CONVERTER_BATCH_SIZE
   ```

## ファイルシステムの権限の確認

セキュリティ上の理由から、Adobe Commerceにはファイルシステムに対する特定の権限が必要です。 権限がと異なります _[所有権](../../upgrade/prepare/prerequisites.md#verify-file-system-permissions)_. 所有権によってファイルシステムに対してアクションを実行できるユーザーが決まり、権限によってユーザーが実行できる操作が決まります。

ファイルシステム内のディレクトリは、 [ファイル・システム所有者](../../installation/prerequisites/file-system/overview.md) グループ。

ファイルシステムの権限が正しく設定されていることを確認するには、アプリケーションサーバーにログインするか、ホスティングプロバイダーの file manager アプリケーションを使用します。

例えば、アプリケーションがにインストールされている場合は、次のコマンドを入力します。 `/var/www/html/magento2`:

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

* ほとんどのファイルは次のとおりです `-rw-rw----`。これは `660`
* `drwxrwx---` = `770`
* `-rw-rw-rw-` = `666`
* ファイルシステムの所有者は `magento_user`

詳細情報を取得するには、次のコマンドを入力します。

```bash
ls -la /var/www/html/magento2/pub
```

Adobe Commerceは静的ファイルアセットをのサブディレクトリにデプロイするからです。 `pub`で、権限と所有権を確認することもお勧めします。

詳しくは、を参照してください [ファイルシステムの権限と所有権](../../installation/prerequisites/file-system/overview.md).

## を `pub/` ディレクトリルート

参照： [セキュリティを向上させるために docroot を変更する](../../installation/tutorials/docroot.md) を参照してください。

## Composer アップデート プラグインのインストール

この [`magento/composer-root-update-plugin`](https://github.com/magento/composer-root-update-plugin) Composer プラグインは、ルート プロジェクトに対して行う必要がある変更を解決します `composer.json` 新しい製品要件に更新する前に、このファイルを開いてください。

このプラグインは、依存関係の競合を手動で特定および修正するのではなく、特定して解決を支援することで、手動アップグレードを部分的に自動化します。

プラグインをインストールするには：

1. パッケージを `composer.json` ファイル。

   ```bash
   composer require magento/composer-root-update-plugin ~2.0 --no-update
   ```

1. 依存関係を更新します。

   ```bash
   composer update
   ```
