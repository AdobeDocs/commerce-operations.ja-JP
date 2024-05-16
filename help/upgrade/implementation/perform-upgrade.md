---
title: アップグレードの実行
description: Adobe Commerceのオンプレミスデプロイメントをアップグレードするには、次の手順に従います。
exl-id: 9183f1d2-a8dd-4232-bdee-7c431e0133df
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '730'
ht-degree: 0%

---


# アップグレードの実行

アップグレードできます _オンプレミス_ コマンドラインからのAdobe Commerce アプリケーションのデプロイメント（以下を行ってソフトウェアをインストールした場合）

- を使用した Composer メタパッケージのダウンロード `composer create-project` コマンド。
- 圧縮されたアーカイブをインストールしています。

>[!NOTE]
>
>- クラウドインフラストラクチャプロジェクトのAdobe Commerceについては、次を参照してください [Commerceのバージョンのアップグレード](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html) （クラウドガイド内）
>- GitHub リポジトリのクローンを作成した場合は、この方法を使用してアップグレードしないでください。 参照： [Git ベースのインストールのアップグレード](../developer/git-installs.md).

以下の手順は、Composer パッケージ マネージャを使用してアップグレードする方法を示しています。 Adobe Commerce 2.4.2 では、Composer 2 のサポートが導入されました。 &lt;2.4.1 からアップグレードする場合は、まず Composer 1 を使用して、Composer 2 と互換性のあるバージョン（2.4.2 など）にアップグレードする必要があります _次の前_ 2.4.2 以降のアップグレードの場合は、Composer 2 にアップグレードします。 また、を実行している必要があります [サポート対象バージョン](../../installation/system-requirements.md) （PHP の場合）

>[!WARNING]
>
>Adobe Commerceのアップグレード手順が変更されました。 新しいバージョンのをインストールする必要があります `magento/composer-root-update-plugin` パッケージ（ [前提条件](../prepare/prerequisites.md)）に設定します。 また、アップグレード用のコマンドはから変更されました。 `composer require magento/<package_name>` 対象： `composer require-commerce magento/<package_name>`.

## 始める前に

を完了する必要があります [アップグレードの前提条件](../prepare/prerequisites.md) アップグレード処理を開始する前に環境を準備します。

## パッケージの管理

>[!NOTE]
>
>様々なリリースレベルの指定に関するヘルプについては、このセクションの最後にある例を参照してください。 例えば、品質向上パッチやセキュリティパッチなどです。 Composer でこれらのパッケージが見つからない場合は、Adobe Commerce サポートにお問い合わせください。

1. メンテナンスモードに切り替えて、アップグレードプロセス中にストアにアクセスできないようにします。

   ```bash
   bin/magento maintenance:enable
   ```

   参照： [メンテナンスモードの有効化または無効化](../../installation/tutorials/maintenance-mode.md) （その他のオプション）。 オプションで、 [カスタムメンテナンスモードページ](../troubleshooting/maintenance-mode-options.md).

1. メッセージキューコンシューマーなどの非同期プロセスの実行中にアップグレードプロセスを開始すると、データが破損する可能性があります。 データの破損を防ぐには、すべての cron ジョブを無効にします。

   _クラウドインフラストラクチャー上のAdobe Commerce:_

   ```bash
   ./vendor/bin/ece-tools cron:disable
   ```

   _Magento Open Source:_

   ```bash
   bin/magento cron:remove
   ```

1. すべてのメッセージキューコンシューマーを手動で開始して、すべてのメッセージが消費されるようにします。

   ```bash
   bin/magento cron:run --group=consumers
   ```

   cron ジョブが完了するのを待ちます。 ジョブのステータスは、プロセスビューアで監視できます。また、 `ps aux | grep 'bin/magento queue'` すべてのプロセスが完了するまで、コマンドを複数回実行します。

1. のバックアップを作成 `composer.json` ファイル。

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

   - _Adobe Commerce:_

     ```bash
     composer require magento/module-bundle-sample-data:100.4.* magento/module-widget-sample-data:100.4.* magento/module-theme-sample-data:100.4.* magento/module-catalog-sample-data:100.4.* magento/module-customer-sample-data:100.4.* magento/module-cms-sample-data:100.4.*  magento/module-catalog-rule-sample-data:100.4.* magento/module-sales-rule-sample-data:100.4.* magento/module-review-sample-data:100.4.* magento/module-tax-sample-data:100.4.* magento/module-sales-sample-data:100.4.* magento/module-grouped-product-sample-data:100.4.* magento/module-downloadable-sample-data:100.4.* magento/module-msrp-sample-data:100.4.* magento/module-configurable-sample-data:100.4.* magento/module-product-links-sample-data:100.4.* magento/module-wishlist-sample-data:100.4.* magento/module-swatches-sample-data:100.4.* magento/sample-data-media:100.4.* magento/module-offline-shipping-sample-data:100.4.* magento/module-gift-card-sample-data:100.4.* magento/module-customer-balance-sample-data:100.4.* magento/module-target-rule-sample-data:100.4.* magento/module-gift-registry-sample-data:100.4.* magento/module-multiple-wishlist-sample-data:100.4.* --no-update
     ```

   - _Magento Open Source:_

     ```bash
     composer require magento/module-bundle-sample-data:100.4.* magento/module-widget-sample-data:100.4.* magento/module-theme-sample-data:100.4.* magento/module-catalog-sample-data:100.4.* magento/module-customer-sample-data:100.4.* magento/module-cms-sample-data:100.4.*  magento/module-catalog-rule-sample-data:100.4.* magento/module-sales-rule-sample-data:100.4.* magento/module-review-sample-data:100.4.* magento/module-tax-sample-data:100.4.* magento/module-sales-sample-data:100.4.* magento/module-grouped-product-sample-data:100.4.* magento/module-downloadable-sample-data:100.4.* magento/module-msrp-sample-data:100.4.* magento/module-configurable-sample-data:100.4.* magento/module-product-links-sample-data:100.4.* magento/module-wishlist-sample-data:100.4.* magento/module-swatches-sample-data:100.4.* magento/sample-data-media:100.4.* magento/module-offline-shipping-sample-data:100.4.* --no-update
     ```

1. 次を使用してインスタンスをアップグレードします `composer require-commerce` コマンド構文：

   ```bash
   composer require-commerce magento/<product> <version> --no-update [--interactive-root-conflicts] [--force-root-updates] [--help]
   ```

   次のようなコマンドオプションがあります。

   - `<product>`  – （必須）アップグレードするパッケージ。 オンプレミスのインストールの場合、この値はである必要があります `product-community-edition` または `product-enterprise-edition`.

   - `<version>`  – （必須）アップグレード先のAdobe Commerceのバージョン。 例： `2.4.3`.

   - `--no-update`  – （必須）依存関係の自動更新を無効にします。

   - `--interactive-root-conflicts`  – （オプション）以前のバージョンの古い値や、アップグレード先のバージョンと一致しないカスタマイズされた値を、インタラクティブに表示および更新できます。

   - `--force-root-updates`  – （オプション）競合するカスタム値をすべて、期待されるCommerce値で上書きします。

   - `--help`  – （任意）プラグインの使用方法の詳細を提供します。

   どちらでもない場合 `--interactive-root-conflicts` nor `--force-root-updates` を指定すると、コマンドは競合する既存の値を保持し、警告メッセージを表示します。 このプラグインの詳細については、 [プラグイン使用状況の README](https://github.com/magento/composer-root-update-plugin/blob/develop/src/Magento/ComposerRootUpdatePlugin/README.md).

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

品質向上パッチには、主に機能性パッチが含まれています _および_ セキュリティの修正。 ただし、下位互換性のある新しい機能が含まれることもあります。 Composer を使用して品質パッチをダウンロードします。

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.6 --no-update
```

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.6 --no-update
```

### 例 – セキュリティパッチ

セキュリティパッチには、セキュリティ修正のみが含まれています。 これらは、アップグレードプロセスをより速く、より簡単にするように設計されています。 セキュリティパッチでは、Composer 命名規則を使用します `2.4.x-px`.

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.6-p3 --no-update
```

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.6-p3 --no-update
```

## メタデータを更新

1. を更新 `"name"`, `"version"`、および `"description"` のフィールド `composer.json` 必要に応じて、ファイルを作成します。

   >[!NOTE]
   >
   >でのメタデータの更新 `composer.json` ファイルは完全に表面的であり、機能していません。

1. 更新を適用します。

   ```bash
   composer update
   ```

1. をクリア `var/` および `generated/` サブディレクトリ：

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

1. _（オプション）_ ワニスを再起動します。

   ページのキャッシュに Varnish を使用する場合は、再起動します。

   ```bash
   service varnish restart
   ```

## 作業内容を確認する

アップグレードが成功したかどうかを確認するには、web ブラウザーでストアフロント URL を開きます。 アップグレードに失敗した場合、ストアフロントが正しく読み込まれません。

アプリケーションがで失敗した場合  `We're sorry, an error has occurred while generating this email.` エラー：

1. Reset [ファイルシステムの所有権と権限](../../installation/prerequisites/file-system/configure-permissions.md) as a のユーザー `root` 権限。
1. 次のディレクトリをクリアします。
   - `var/cache/`
   - `var/page_cache/`
   - `generated/code/`
1. Web ブラウザーでストアフロントを再度確認します。
