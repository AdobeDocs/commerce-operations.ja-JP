---
title: アップグレードの実行
description: Adobe Commerceのオンプレミスデプロイメントをアップグレードするには、次の手順に従います。
exl-id: 9183f1d2-a8dd-4232-bdee-7c431e0133df
source-git-commit: 4cf6f81ce43ddcccf20db12b8735f29a151d420d
workflow-type: tm+mt
source-wordcount: '769'
ht-degree: 0%

---


# アップグレードの実行

次の方法でインストールした場合は、コマンドラインからAdobe Commerce アプリケーションの _オンプレミス_ デプロイメントをアップグレードできます。

- `composer create-project` コマンドを使用して Composer メタパッケージをダウンロードします。
- 圧縮されたアーカイブをインストールしています。

>[!NOTE]
>
>- クラウドインフラストラクチャプロジェクトのAdobe Commerceについては、クラウドガイドの [Commerce バージョンのアップグレード &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html?lang=ja) を参照してください。
>- GitHub リポジトリのクローンを作成した場合は、この方法を使用してアップグレードしないでください。 [Git ベースのインストールのアップグレード &#x200B;](../developer/git-installs.md) を参照してください。

以下の手順は、Composer パッケージ マネージャを使用してアップグレードする方法を示しています。 Adobe Commerce 2.4.2 では、Composer 2 のサポートが導入されました。 &lt;2.4.1 からアップグレードする場合は、まず Composer 1 を使用して Composer 2 と互換性のあるバージョン（たとえば 2.4.2）にアップグレードする必要があります _前に_ 2.4.2 を超えるアップグレードについては Composer 2 にアップグレードします）。 また、PHP の [&#x200B; サポート対象バージョン &#x200B;](../../installation/system-requirements.md) を実行する必要があります。

>[!WARNING]
>
>Adobe Commerceのアップグレード手順が変更されました。 `magento/composer-root-update-plugin` パッケージの新しいバージョンをインストールする必要があります（[&#x200B; 前提条件 &#x200B;](../prepare/prerequisites.md) を参照）。 また、アップグレード用のコマンドが `composer require magento/<package_name>` から `composer require-commerce magento/<package_name>` に変更されました。

## 始める前に

アップグレードプロセスを開始する前に、[&#x200B; アップグレードの前提条件 &#x200B;](../prepare/prerequisites.md) を満たして、環境を準備する必要があります。

>[!IMPORTANT]
>
>Adobe Commerce バージョン 2.4.6-p13 には、下位互換性のない変更を含む古いマイナーバージョンからのスムーズなアップグレードに必要な `magento/inventory-composer-installer` パッケージが含まれていません。<br>
>&#x200B;>2.3 から 2.4.6-p13 にアップグレードする場合は、アップグレードする前に次のコマンドを実行して `magento/inventory-composer-installer` パッケージをインストールします。
>&#x200B;>`composer require magento/inventory-composer-installer`

## パッケージの管理

>[!NOTE]
>
>様々なリリースレベルの指定に関するヘルプについては、このセクションの最後にある例を参照してください。 例えば、品質向上パッチやセキュリティパッチなどです。 Composer でこれらのパッケージが見つからない場合は、Adobe Commerce サポートにお問い合わせください。

1. メンテナンスモードに切り替えて、アップグレードプロセス中にストアにアクセスできないようにします。

   ```bash
   bin/magento maintenance:enable
   ```

   その他のオプションについては、[&#x200B; メンテナンスモードの有効化または無効化 &#x200B;](../../installation/tutorials/maintenance-mode.md) を参照してください。 オプションで、[&#x200B; カスタムメンテナンスモードページ &#x200B;](../troubleshooting/maintenance-mode-options.md) を作成できます。

1. メッセージキューコンシューマーなどの非同期プロセスの実行中にアップグレードプロセスを開始すると、データが破損する可能性があります。 データの破損を防ぐには、すべての cron ジョブを無効にします。

   クラウドインフラストラクチャー上のAdobe Commerce（_A） :_

   ```bash
   ./vendor/bin/ece-tools cron:disable
   ```

   Magento Open Source（_D） :_

   ```bash
   bin/magento cron:remove
   ```

1. すべてのメッセージキューコンシューマーを手動で開始して、すべてのメッセージが消費されるようにします。

   ```bash
   bin/magento cron:run --group=consumers
   ```

   cron ジョブが完了するのを待ちます。 ジョブのステータスは、プロセスビューアで監視することも、すべてのプロセスが完了するまで `ps aux | grep 'bin/magento queue'` コマンドを複数回実行して監視することもできます。

1. `composer.json` ファイルのバックアップを作成します。

   ```bash
   cp composer.json composer.json.bak
   ```

1. 必要に応じて、特定のパッケージを追加または削除します。

   例えば、Magento Open SourceからAdobe Commerceにアップグレードする場合は、Magento Open Source パッケージを削除します。

   ```bash
   composer remove magento/product-community-edition --no-update
   ```

   サンプルデータをアップグレードすることもできます。

   ```bash
   composer require <sample data module-1>:<version> ... <sample data module-n>:<version> --no-update
   ```

   - Adobe Commerce（_D） :_

     ```bash
     composer require magento/module-bundle-sample-data:100.4.* magento/module-widget-sample-data:100.4.* magento/module-theme-sample-data:100.4.* magento/module-catalog-sample-data:100.4.* magento/module-customer-sample-data:100.4.* magento/module-cms-sample-data:100.4.*  magento/module-catalog-rule-sample-data:100.4.* magento/module-sales-rule-sample-data:100.4.* magento/module-review-sample-data:100.4.* magento/module-tax-sample-data:100.4.* magento/module-sales-sample-data:100.4.* magento/module-grouped-product-sample-data:100.4.* magento/module-downloadable-sample-data:100.4.* magento/module-msrp-sample-data:100.4.* magento/module-configurable-sample-data:100.4.* magento/module-product-links-sample-data:100.4.* magento/module-wishlist-sample-data:100.4.* magento/module-swatches-sample-data:100.4.* magento/sample-data-media:100.4.* magento/module-offline-shipping-sample-data:100.4.* magento/module-gift-card-sample-data:100.4.* magento/module-customer-balance-sample-data:100.4.* magento/module-target-rule-sample-data:100.4.* magento/module-gift-registry-sample-data:100.4.* magento/module-multiple-wishlist-sample-data:100.4.* --no-update
     ```

   - Magento Open Source（_D） :_

     ```bash
     composer require magento/module-bundle-sample-data:100.4.* magento/module-widget-sample-data:100.4.* magento/module-theme-sample-data:100.4.* magento/module-catalog-sample-data:100.4.* magento/module-customer-sample-data:100.4.* magento/module-cms-sample-data:100.4.*  magento/module-catalog-rule-sample-data:100.4.* magento/module-sales-rule-sample-data:100.4.* magento/module-review-sample-data:100.4.* magento/module-tax-sample-data:100.4.* magento/module-sales-sample-data:100.4.* magento/module-grouped-product-sample-data:100.4.* magento/module-downloadable-sample-data:100.4.* magento/module-msrp-sample-data:100.4.* magento/module-configurable-sample-data:100.4.* magento/module-product-links-sample-data:100.4.* magento/module-wishlist-sample-data:100.4.* magento/module-swatches-sample-data:100.4.* magento/sample-data-media:100.4.* magento/module-offline-shipping-sample-data:100.4.* --no-update
     ```

1. 次の `composer require-commerce` コマンド構文を使用してインスタンスをアップグレードします。

   ```bash
   composer require-commerce magento/<product> <version> --no-update [--interactive-root-conflicts] [--force-root-updates] [--help]
   ```

   次のようなコマンドオプションがあります。

   - `<product>` – （必須）アップグレードするパッケージ。 オンプレミスのインストールの場合、この値は `product-community-edition` または `product-enterprise-edition` である必要があります。

   - `<version>` – （必須）アップグレード先のAdobe Commerceのバージョン。 例：`2.4.3`。

   - `--no-update` – （必須）依存関係の自動更新を無効にします。

   - `--interactive-root-conflicts` – （オプション）以前のバージョンの古い値や、アップグレード先のバージョンと一致しないカスタマイズされた値を、インタラクティブに表示および更新できます。

   - `--force-root-updates` – （任意）競合するカスタム値をすべて、期待されるCommerce値で上書きします。

   - `--help` – （任意）プラグインの使用方法の詳細を提供します。

   `--interactive-root-conflicts` も `--force-root-updates` も指定されていない場合、コマンドは競合する既存の値を保持し、警告メッセージを表示します。 このプラグインについて詳しくは、[&#x200B; プラグインの使用方法の README](https://github.com/magento/composer-root-update-plugin/blob/develop/src/Magento/ComposerRootUpdatePlugin/README.md) を参照してください。

1. 依存関係を更新します。

   ```bash
   composer update
   ```

### 例 – 使用可能なバージョンのリスト

使用可能な 2.4.x バージョンの完全なリストを表示するには：

_Magento Open Source_:

```bash
composer show magento/product-community-edition 2.4.* --available | grep -m 1 versions
```

_Adobe Commerce_:

```bash
composer show magento/product-enterprise-edition 2.4.* --available | grep -m 1 versions
```

### 例 – 品質パッチ

品質向上パッチには、主に機能 _および_ セキュリティ修正が含まれています。 ただし、下位互換性のある新しい機能が含まれることもあります。 Composer を使用して品質パッチをダウンロードします。

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.6 --no-update
```

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.6 --no-update
```

### 例 – セキュリティパッチ

セキュリティパッチには、セキュリティ修正のみが含まれています。 これらは、アップグレードプロセスをより速く、より簡単にするように設計されています。 セキュリティパッチでは、Composer の命名規則 `2.4.x-px` を使用します。

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.6-p3 --no-update
```

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.6-p3 --no-update
```

## メタデータを更新

1. 必要に応じて、`"name"` ファイルの `"version"`、`"description"`、`composer.json` フィールドを更新します。

   >[!NOTE]
   >
   >`composer.json` ファイル内のメタデータの更新は、機能するのではなく、完全に表面的なものです。

1. 更新を適用します。

   ```bash
   composer update
   ```

1. `var/` サブディレクトリと `generated/` サブディレクトリをクリアします。

   ```bash
   rm -rf var/cache/*
   ```

   ```bash
   rm -rf var/page_cache/*
   ```

   ```bash
   rm -rf generated/code/*
   ```

   >[!NOTE]
   >
   >Redis や Memcached など、ファイルシステム以外のキャッシュストレージを使用する場合は、手動でキャッシュをクリアする必要があります。

1. データベーススキーマとデータを更新します。

   ```bash
   bin/magento setup:upgrade
   ```

1. メンテナンスモードを無効にします。

   ```bash
   bin/magento maintenance:disable
   ```

1. _（任意）_ ワニスを再起動します。

   ページのキャッシュに Varnish を使用する場合は、再起動します。

   ```bash
   service varnish restart
   ```

## 作業内容を確認する

アップグレードが成功したかどうかを確認するには、web ブラウザーでストアフロント URL を開きます。 アップグレードに失敗した場合、ストアフロントが正しく読み込まれません。

アプリケーションが `We're sorry, an error has occurred while generating this email.` エラーで失敗した場合：

1. [&#x200B; ファイルシステムの所有権と権限 &#x200B;](../../installation/prerequisites/file-system/configure-permissions.md) を `root` 権限を持つユーザーとしてリセットします。
1. 次のディレクトリをクリアします。
   - `var/cache/`
   - `var/page_cache/`
   - `generated/code/`
1. Web ブラウザーでストアフロントを再度確認します。
