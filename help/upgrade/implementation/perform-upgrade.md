---
title: アップグレードの実行
description: 次の手順に従って、Adobe Commerceのオンプレミスデプロイメントをアップグレードします。
exl-id: 9183f1d2-a8dd-4232-bdee-7c431e0133df
source-git-commit: 0cee0ab36274758b583c04dbee8251ce3b78e559
workflow-type: tm+mt
source-wordcount: '742'
ht-degree: 0%

---


# アップグレードの実行

アップグレード可能 _オンプレミス_ 次の方法でソフトウェアをインストールした場合は、コマンドラインからAdobe CommerceまたはMagento Open Sourceアプリケーションのデプロイメントを実行します。

- を使用した Composer メタパッケージのダウンロード `composer create-project` コマンドを使用します。
- 圧縮アーカイブをインストールしています。

>[!NOTE]
>
>- Adobe Commerce on cloud infrastructure プロジェクトについては、 [コマースバージョンをアップグレード](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html) 」を参照してください。
>- GitHub リポジトリを複製した場合は、この方法を使用してアップグレードしないでください。 詳しくは、 [Git ベースのインストールのアップグレード](../developer/git-installs.md).

以下の手順は、Composer パッケージマネージャーを使用したアップグレード方法を示しています。 Adobe Commerce 2.4.2 では、Composer 2 のサポートが導入されました。 &lt;2.4.1 からアップグレードする場合は、まず Composer 1 を使用して、Composer 2 と互換性のあるバージョン（例えば、2.4.2）にアップグレードする必要があります _前_ 2.4.2 以降のアップグレードの場合は、Composer 2 にアップグレードします。 さらに、 [サポート対象バージョン](../../installation/system-requirements.md) PHP の

>[!WARNING]
>
>Adobe CommerceとMagento Open Sourceのアップグレード手順が変更されました。 新しいバージョンの `magento/composer-root-update-plugin` パッケージ ( [前提条件](../prepare/prerequisites.md)) をクリックします。 また、アップグレード用のコマンドは、 `composer require magento/<package_name>` から `composer require-commerce magento/<package_name>`.

## 始める前に

次を完了する必要があります： [アップグレードの前提条件](../prepare/prerequisites.md) をクリックして、アップグレードプロセスを開始する前に環境を準備します。

## パッケージの管理

>[!NOTE]
>
>様々なリリースレベルを指定する際のヘルプについては、この節の最後の例を参照してください。 たとえば、品質パッチとセキュリティパッチ。 Composer でこれらのパッケージが見つからない場合は、Adobe Commerceサポートにお問い合わせください。

1. メンテナンスモードに切り替えて、アップグレードプロセス中にストアにアクセスできないようにします。

   ```bash
   bin/magento maintenance:enable
   ```

   詳しくは、 [メンテナンスモードを有効または無効にする](../../installation/tutorials/maintenance-mode.md) 」を参照してください。 オプションで、 [カスタムメンテナンスモードページ](../troubleshooting/maintenance-mode-options.md).

1. メッセージキューコンシューマーなどの非同期プロセスの実行中にアップグレードプロセスを開始すると、データが破損する可能性があります。 データの破損を防ぐには、すべての cron ジョブを無効にします。

   _Adobe Commerce on cloud infrastructure:_

   ```bash
   ./vendor/bin/ece-tools cron:disable
   ```

   _MAGENTO OPEN SOURCE:_

   ```bash
   bin/magento cron:remove
   ```

1. すべてのメッセージキューコンシューマーを手動で開始し、すべてのメッセージが消費されていることを確認します。

   ```bash
   bin/magento cron:run --group=consumers
   ```

   cron ジョブが完了するのを待ちます。 ジョブのステータスを監視するには、プロセスビューアを使用するか、 `ps aux | grep 'bin/magento queue'` すべてのプロセスが完了するまで、コマンドを複数回実行します。

1. のバックアップを作成します。 `composer.json` ファイル。

   ```bash
   cp composer.json composer.json.bak
   ```

1. 必要に応じて、特定のパッケージを追加または削除します。

   例えば、Magento Open SourceからAdobe Commerceにアップグレードする場合は、Magento Open Sourceパッケージを削除します。

   ```bash
   composer remove magento/product-community-edition --no-update
   ```

   サンプルデータをアップグレードすることもできます。

   ```bash
   composer require <sample data module-1>:<version> ... <sample data module-n>:<version> --no-update
   ```

   - _ADOBE COMMERCE:_

     ```bash
     composer require magento/module-bundle-sample-data:100.4.* magento/module-widget-sample-data:100.4.* magento/module-theme-sample-data:100.4.* magento/module-catalog-sample-data:100.4.* magento/module-customer-sample-data:100.4.* magento/module-cms-sample-data:100.4.*  magento/module-catalog-rule-sample-data:100.4.* magento/module-sales-rule-sample-data:100.4.* magento/module-review-sample-data:100.4.* magento/module-tax-sample-data:100.4.* magento/module-sales-sample-data:100.4.* magento/module-grouped-product-sample-data:100.4.* magento/module-downloadable-sample-data:100.4.* magento/module-msrp-sample-data:100.4.* magento/module-configurable-sample-data:100.4.* magento/module-product-links-sample-data:100.4.* magento/module-wishlist-sample-data:100.4.* magento/module-swatches-sample-data:100.4.* magento/sample-data-media:100.4.* magento/module-offline-shipping-sample-data:100.4.* magento/module-gift-card-sample-data:100.4.* magento/module-customer-balance-sample-data:100.4.* magento/module-target-rule-sample-data:100.4.* magento/module-gift-registry-sample-data:100.4.* magento/module-multiple-wishlist-sample-data:100.4.* --no-update
     ```

   - _MAGENTO OPEN SOURCE:_

     ```bash
     composer require magento/module-bundle-sample-data:100.4.* magento/module-widget-sample-data:100.4.* magento/module-theme-sample-data:100.4.* magento/module-catalog-sample-data:100.4.* magento/module-customer-sample-data:100.4.* magento/module-cms-sample-data:100.4.*  magento/module-catalog-rule-sample-data:100.4.* magento/module-sales-rule-sample-data:100.4.* magento/module-review-sample-data:100.4.* magento/module-tax-sample-data:100.4.* magento/module-sales-sample-data:100.4.* magento/module-grouped-product-sample-data:100.4.* magento/module-downloadable-sample-data:100.4.* magento/module-msrp-sample-data:100.4.* magento/module-configurable-sample-data:100.4.* magento/module-product-links-sample-data:100.4.* magento/module-wishlist-sample-data:100.4.* magento/module-swatches-sample-data:100.4.* magento/sample-data-media:100.4.* magento/module-offline-shipping-sample-data:100.4.* --no-update
     ```

1. 次を使用してインスタンスをアップグレードします `composer require-commerce` コマンドの構文：

   ```bash
   composer require-commerce magento/<product> <version> --no-update [--interactive-root-conflicts] [--force-root-updates] [--help]
   ```

   コマンドオプションは次のとおりです。

   - `<product>`  — （必須）アップグレードするパッケージです。 オンプレミスでのインストールの場合、この値は次のいずれかである必要があります。 `product-community-edition` または `product-enterprise-edition`.

   - `<version>`  — （必須）アップグレード先のAdobe CommerceまたはMagento Open Sourceのバージョン。 例： `2.4.3`.

   - `--no-update`  — （必須）依存関係の自動更新を無効にします。

   - `--interactive-root-conflicts`  — （オプション）以前のバージョンの最新の値、またはアップグレード先のバージョンと一致しないカスタマイズ値をインタラクティブに表示および更新できます。

   - `--force-root-updates`  — （オプション）予期された Commerce 値を持つ競合するすべてのカスタム値を上書きします。

   - `--help`  — （オプション）プラグインの使用状況の詳細を示します。

   どちらでもない場合 `--interactive-root-conflicts` nor `--force-root-updates` を指定した場合、コマンドは競合している既存の値を保持し、警告メッセージを表示します。 プラグインについて詳しくは、 [プラグインの使用 README](https://github.com/magento/composer-root-update-plugin/blob/develop/src/Magento/ComposerRootUpdatePlugin/README.md).

1. 依存関係を更新します。

   ```bash
   composer update
   ```

### 例 — 使用可能なバージョンのリスト

利用可能な 2.4.x バージョンの完全なリストを確認するには：

_Magento Open Source_:

```bash
composer show magento/product-community-edition 2.4.* --available | grep -m 1 versions
```

_Adobe Commerce_:

```bash
composer show magento/product-enterprise-edition 2.4.* --available | grep -m 1 versions
```

### 例 — 品質パッチ

品質パッチには主に機能が含まれる _および_ セキュリティの修正。 ただし、新しい後方互換性のある機能を含めることができます。 Composer を使用して、品質パッチをダウンロードします。

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.6 --no-update
```

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.6 --no-update
```

### 例 — セキュリティパッチ

セキュリティパッチにはセキュリティ修正のみが含まれています。 これらは、アップグレードプロセスをより迅速かつ容易にするように設計されています。 セキュリティパッチでは、Composer の命名規則を使用します。 `2.4.x-px`.

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.6-p3 --no-update
```

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.6-p3 --no-update
```

## メタデータを更新

1. を更新します。 `"name"`, `"version"`、および `"description"` フィールド `composer.json` 必要に応じてファイルを作成します。

   >[!NOTE]
   >
   >のメタデータの更新 `composer.json` ファイルは完全に表面的であり、機能的ではありません。

1. 更新を適用します。

   ```bash
   composer update
   ```

1. 次をクリア： `var/` および `generated/` サブディレクトリ：

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
   >Redis や Memcached など、ファイルシステム以外のキャッシュストレージを使用する場合は、キャッシュを手動でクリアする必要があります。

1. データベーススキーマとデータを更新します。

   ```bash
   bin/magento setup:upgrade
   ```

1. メンテナンスモードを無効にします。

   ```bash
   bin/magento maintenance:disable
   ```

1. _（オプション）_ ワニスを再起動します。

   Vanish をページのキャッシュに使用する場合は、次の手順で再起動します。

   ```bash
   service varnish restart
   ```

## 作業内容を確認する

アップグレードが成功したかどうかを確認するには、Web ブラウザーでストアフロント URL を開きます。 アップグレードに失敗した場合、ストアフロントは正しく読み込まれません。

アプリケーションが  `We're sorry, an error has occurred while generating this email.` エラー：

1. リセット [ファイル・システムの所有権と権限](../../installation/prerequisites/file-system/configure-permissions.md) を使用して `root` 権限。
1. 次のディレクトリをクリアします。
   - `var/cache/`
   - `var/page_cache/`
   - `generated/code/`
1. Web ブラウザーでストアフロントを再度確認してください。
