---
title: アップグレードの実行
description: Adobe Commerceのオンプレミス導入をアップグレードするには、次の手順に従います。
exl-id: 9183f1d2-a8dd-4232-bdee-7c431e0133df
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 0%

---


# アップグレードの実行

次の方法でソフトウェアをインストールした場合、コマンドラインからAdobe Commerce アプリケーションの&#x200B;_オンプレミス_&#x200B;のデプロイメントをアップグレードできます。

- `composer create-project` コマンドを使用してComposer メタパッケージをダウンロードしています。
- 圧縮アーカイブのインストール。

>[!NOTE]
>
>- クラウドインフラストラクチャプロジェクト上のAdobe Commerceについては、「クラウドガイド」の「[Commerce バージョンのアップグレード &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html?lang=ja)」を参照してください。
>- GitHub リポジトリをクローンした場合は、この方法を使用してアップグレードしないでください。 [Git ベースのインストールのアップグレード &#x200B;](../developer/git-installs.md)を参照してください。

次の手順では、Composer パッケージマネージャーを使用してアップグレードする方法を示します。 Adobe Commerce 2.4.2では、Composer 2のサポートが導入されました。 &lt;2.4.1からアップグレードする場合は、まずComposer 1 _before_ アップグレードを使用してComposer 2と互換性のあるバージョン（2.4.2など）にアップグレードし、2.4.2を超えるアップグレードを実行する必要があります。 さらに、PHPの[&#x200B; サポートされているバージョン &#x200B;](../../installation/system-requirements.md)を実行している必要があります。

>[!WARNING]
>
>Adobe Commerceのアップグレード手順が変更されました。 新しいバージョンの`magento/composer-root-update-plugin` パッケージをインストールする必要があります（[前提条件](../prepare/prerequisites.md)を参照）。 さらに、アップグレード用のコマンドが`composer require magento/<package_name>`から`composer require-commerce magento/<package_name>`に変更されました。

## 始める前に

アップグレード プロセスを開始する前に、環境を準備するには、[&#x200B; アップグレードの前提条件](../prepare/prerequisites.md)を完了する必要があります。

>[!IMPORTANT]
>
>Adobe Commerce バージョン 2.4.6-p13には、`magento/inventory-composer-installer` パッケージが含まれていません。これは、下位互換性のない変更を含む古いマイナーバージョンからスムーズにアップグレードするために必要です。<br>
>2.3から2.4.6-p13にアップグレードする場合は、アップグレードする前に次のコマンドを実行して`magento/inventory-composer-installer` パッケージをインストールします。>`composer require magento/inventory-composer-installer`

## パッケージの管理

>[!NOTE]
>
>様々なリリースレベルを指定する方法については、この節の最後にある例を参照してください。 例えば、品質パッチやセキュリティパッチなどです。 Composerでこれらのパッケージが見つからない場合は、Adobe Commerce サポートにお問い合わせください。

1. メンテナンスモードに切り替えて、アップグレードプロセス中にストアにアクセスできないようにします。

   ```shell
   bin/magento maintenance:enable
   ```

   その他のオプションについては、[&#x200B; メンテナンスモードを有効または無効にする](../../installation/tutorials/maintenance-mode.md)を参照してください。 オプションで、[&#x200B; カスタムメンテナンスモードページ &#x200B;](../troubleshooting/maintenance-mode-options.md)を作成できます。

1. メッセージキューコンシューマーなどの非同期プロセスの実行中にアップグレードプロセスを開始すると、データが破損する可能性があります。 データの破損を防ぐには、すべてのcron ジョブを無効にします。

   _Adobe Commerce（クラウドインフラストラクチャ上） :_

   ```shell
   ./vendor/bin/ece-tools cron:disable
   ```

   _Magento Open Source :_

   ```shell
   bin/magento cron:remove
   ```

1. すべてのメッセージキューのコンシューマーを手動で開始して、すべてのメッセージが確実に消費されるようにします。

   ```shell
   bin/magento cron:run --group=consumers
   ```

   cron ジョブが完了するのを待ちます。 すべてのプロセスが完了するまで、プロセスビューアを使用するか、`ps aux | grep 'bin/magento queue'` コマンドを複数回実行することで、ジョブのステータスを監視できます。

1. `composer.json` ファイルのバックアップを作成します。

   ```shell
   cp composer.json composer.json.bak
   ```

1. ニーズに基づいて特定のパッケージを追加または削除します。

   例えば、Magento Open SourceからAdobe Commerceにアップグレードする場合は、Magento Open Source パッケージを削除します。

   ```shell
   composer remove magento/product-community-edition --no-update
   ```

   サンプルデータをアップグレードすることもできます。

   ```shell
   composer require <sample data module-1>:<version> ... <sample data module-n>:<version> --no-update
   ```

   - _Adobe Commerce :_

     ```shell
     composer require magento/module-bundle-sample-data:100.4.* magento/module-widget-sample-data:100.4.* magento/module-theme-sample-data:100.4.* magento/module-catalog-sample-data:100.4.* magento/module-customer-sample-data:100.4.* magento/module-cms-sample-data:100.4.*  magento/module-catalog-rule-sample-data:100.4.* magento/module-sales-rule-sample-data:100.4.* magento/module-review-sample-data:100.4.* magento/module-tax-sample-data:100.4.* magento/module-sales-sample-data:100.4.* magento/module-grouped-product-sample-data:100.4.* magento/module-downloadable-sample-data:100.4.* magento/module-msrp-sample-data:100.4.* magento/module-configurable-sample-data:100.4.* magento/module-product-links-sample-data:100.4.* magento/module-wishlist-sample-data:100.4.* magento/module-swatches-sample-data:100.4.* magento/sample-data-media:100.4.* magento/module-offline-shipping-sample-data:100.4.* magento/module-gift-card-sample-data:100.4.* magento/module-customer-balance-sample-data:100.4.* magento/module-target-rule-sample-data:100.4.* magento/module-gift-registry-sample-data:100.4.* magento/module-multiple-wishlist-sample-data:100.4.* --no-update
     ```

   - _Magento Open Source :_

     ```shell
     composer require magento/module-bundle-sample-data:100.4.* magento/module-widget-sample-data:100.4.* magento/module-theme-sample-data:100.4.* magento/module-catalog-sample-data:100.4.* magento/module-customer-sample-data:100.4.* magento/module-cms-sample-data:100.4.*  magento/module-catalog-rule-sample-data:100.4.* magento/module-sales-rule-sample-data:100.4.* magento/module-review-sample-data:100.4.* magento/module-tax-sample-data:100.4.* magento/module-sales-sample-data:100.4.* magento/module-grouped-product-sample-data:100.4.* magento/module-downloadable-sample-data:100.4.* magento/module-msrp-sample-data:100.4.* magento/module-configurable-sample-data:100.4.* magento/module-product-links-sample-data:100.4.* magento/module-wishlist-sample-data:100.4.* magento/module-swatches-sample-data:100.4.* magento/sample-data-media:100.4.* magento/module-offline-shipping-sample-data:100.4.* --no-update
     ```

1. 次の`composer require-commerce` コマンド構文を使用してインスタンスをアップグレードします。

   ```shell
   composer require-commerce magento/<product> <version> --no-update [--interactive-root-conflicts] [--force-root-updates] [--help]
   ```

   コマンドオプションには次のものが含まれます。

   - `<product>` – （必須）アップグレードするパッケージ。 オンプレミス インストールの場合、この値は`product-community-edition`または`product-enterprise-edition`である必要があります。

   - `<version>` – （必須）アップグレードするAdobe Commerceのバージョン。 例：`2.4.3`。

   - `--no-update` – （必須）依存関係の自動更新を無効にします。

   - `--interactive-root-conflicts` – （オプション）以前のバージョンの古い値、またはアップグレードするバージョンと一致しないカスタマイズされた値をインタラクティブに表示して更新できます。

   - `--force-root-updates` – （オプション）競合するすべてのカスタム値を、想定されるCommerce値で上書きします。

   - `--help` – （オプション）プラグインの使用状況に関する詳細を提供します。

   `--interactive-root-conflicts`と`--force-root-updates`のどちらも指定しない場合、コマンドは競合している既存の値を保持し、警告メッセージを表示します。 プラグインについて詳しくは、[&#x200B; プラグインの使用状況README](https://github.com/magento/composer-root-update-plugin/blob/develop/src/Magento/ComposerRootUpdatePlugin/README.md)を参照してください。

1. 依存関係を更新します。

   ```shell
   composer update
   ```

### 例 – 使用可能なバージョンのリスト

使用可能な2.4.x バージョンの完全なリストを表示するには、次の手順を実行します。

_Magento Open Source_:

```shell
composer show magento/product-community-edition 2.4.* --available | grep -m 1 versions
```

_Adobe Commerce_:

```shell
composer show magento/product-enterprise-edition 2.4.* --available | grep -m 1 versions
```

### 例 – 品質パッチ

品質パッチには、主に機能的な&#x200B;_および_&#x200B;のセキュリティ修正が含まれています。 しかし、新しい後方互換性のある機能を含むことがあります。 Composerを使用して、高品質のパッチをダウンロードします。

_Adobe Commerce_:

```shell
composer require-commerce magento/product-enterprise-edition 2.4.6 --no-update
```

_Magento Open Source_:

```shell
composer require-commerce magento/product-community-edition 2.4.6 --no-update
```

### 例 – セキュリティパッチ

セキュリティパッチにはセキュリティ修正のみが含まれています。 アップグレードプロセスをより迅速かつ容易に行えるように設計されています。 セキュリティパッチでは、Composerの命名規則`2.4.x-px`が使用されます。

_Adobe Commerce_:

```shell
composer require-commerce magento/product-enterprise-edition 2.4.6-p3 --no-update
```

_Magento Open Source_:

```shell
composer require-commerce magento/product-community-edition 2.4.6-p3 --no-update
```

## メタデータを更新

1. 必要に応じて、`composer.json` ファイルの`"name"`、`"version"`および`"description"` フィールドを更新します。

   >[!NOTE]
   >
   >`composer.json` ファイルのメタデータの更新は、完全に表面的で、機能しません。

1. アップデートの適用。

   ```shell
   composer update
   ```

1. `var/`と`generated/`個のサブディレクトリをクリアします。

   ```shell
   rm -rf var/cache/*
   ```

   ```shell
   rm -rf var/page_cache/*
   ```

   ```shell
   rm -rf generated/code/*
   ```

   >[!NOTE]
   >
   >RedisやMemcachedなどのファイルシステム以外のキャッシュストレージを使用する場合は、そのキャッシュも手動でクリアする必要があります。

1. データベーススキーマとデータを更新します。

   ```shell
   bin/magento setup:upgrade
   ```

1. メンテナンスモードを無効にします。

   ```shell
   bin/magento maintenance:disable
   ```

1. _（オプション）_ Varnishを再起動します。

   ページのキャッシュにVarnishを使用する場合は、再起動します。

   ```shell
   service varnish restart
   ```

## 作品を確認する

アップグレードが成功したかどうかを確認するには、web ブラウザーでストアフロント URLを開きます。 アップグレードに失敗した場合、ストアフロントが正しく読み込まれません。

アプリケーションが`We're sorry, an error has occurred while generating this email.` エラーで失敗した場合：

1. [&#x200B; ファイルシステムの所有権と権限](../../installation/prerequisites/file-system/configure-permissions.md)を`root`権限を持つユーザーとしてリセットします。
1. 次のディレクトリをクリアします。
   - `var/cache/`
   - `var/page_cache/`
   - `generated/code/`
1. もう一度web ブラウザーでストアフロントを確認します。
