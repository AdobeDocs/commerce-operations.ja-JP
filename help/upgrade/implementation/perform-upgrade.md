---
title: アップグレードの実行
description: 次の手順に従って、Adobe CommerceまたはMagento Open Sourceプロジェクトをアップグレードします。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 0%

---


# アップグレードの実行

ソフトウェアをインストールした場合は、次の方法でAdobe CommerceまたはMagento Open Sourceアプリケーションをコマンドラインからアップグレードできます。

- を使用したメタパッケージのダウンロード `composer create-project` コマンドを使用します。
- 圧縮アーカイブをインストールしています。

>[!NOTE]
>
>GitHub リポジトリを複製した場合は、この方法を使用してアップグレードしないでください。 代わりに、 [Git ベースのインストールのアップグレード](../developer/git-installs.md) を参照してください。

以下の手順は、Composer を使用してアップグレードする方法を示しています。 Adobe Commerce 2.4.2 では、Composer 2 のサポートが導入されました。 &lt;2.4.1 からアップグレードする場合は、まず Composer 1 を使用して、Composer 2 と互換性のあるバージョン（例：2.4.2）にアップグレードする必要があります _前_ 2.4.2 以降のアップグレードの場合は、Composer 2 にアップグレードします。 さらに、 [サポート対象バージョン](../../installation/system-requirements.md) PHP の

>[!WARNING]
>
>Adobe CommerceとMagento Open Sourceのアップグレード手順が変更されました。 新しいバージョンの `magento/composer-root-update-plugin` パッケージ ( [前提条件](../prepare/prerequisites.md)) をクリックします。 また、アップグレード用のコマンドは、 `composer require magento/<package_name>` から `composer require-commerce magento/<package_name>`.

## 始める前に

次を完了する必要があります： [アップグレードの前提条件](../prepare/prerequisites.md) をクリックして、アップグレードプロセスを開始する前に環境を準備します。

## パッケージの管理

>[!NOTE]
>
>様々なリリースレベルを指定する際のヘルプについては、この節の最後の例を参照してください。 例えば、マイナーリリース、品質パッチ、セキュリティパッチなどです。 Adobe Commerceのお客様は、GA(General Availability) の日付の 2 週間前にパッチにアクセスできます。 リリース前のパッケージは、Composer でのみ使用できます。 GA になるまで、ダウンロードポータルや GitHub で見つけることはできません。 Composer でこれらのパッケージが見つからない場合は、Adobe Commerceサポートにお問い合わせください。

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

   _Magento Open Source:_

   ```bash
   bin/magento cron:remove
   ```

1. すべてのメッセージキューコンシューマーを手動で起動し、すべてのメッセージが消費されるようにします。

   ```bash
   bin/magento cron:run --group=consumers
   ```

   cron ジョブが完了するのを待ちます。 ジョブのステータスを監視するには、プロセスビューアを使用するか、 `ps aux | grep 'bin/magento queue'` すべてのプロセスが完了するまで、コマンドを複数回実行します。

1. のバックアップを作成する `composer.json` ファイル。

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

   コマンドオプションは次のとおりです。

   - `<product>`  — （必須）アップグレードするパッケージです。 オンプレミスでのインストールの場合、この値は次のいずれかである必要があります。 `product-community-edition` または `product-enterprise-edition`.

   - `<version>`  — （必須）アップグレード先のAdobe CommerceまたはMagento Open Sourceのバージョン。 例： `2.4.3`.

   - `--no-update`  — （必須）依存関係の自動更新を無効にします。

   - `--interactive-root-conflicts`  — （オプション）以前のバージョンの最新の値、またはアップグレード先のバージョンと一致しないカスタマイズ値をインタラクティブに表示および更新できます。

   - `--force-root-updates`  — （オプション）予期されたMagento値を持つ競合するすべてのカスタム値を上書きします。

   - `--help`  — （オプション）プラグインの使用状況の詳細を示します。
   どちらも `--interactive-root-conflicts` nor `--force-root-updates` を指定した場合、コマンドは競合している既存の値を保持し、警告メッセージを表示します。 プラグインについて詳しくは、 [プラグインの使用 README](https://github.com/magento/composer-root-update-plugin/blob/develop/src/Magento/ComposerRootUpdatePlugin/README.md).

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

### 例 — マイナーリリース

マイナーリリースには、新機能、品質修正およびセキュリティ修正が含まれています。 Composer を使用してマイナーリリースを指定します。 例えば、Magento Open Source2.4.3 のメタパッケージを指定するには、次のようにします。

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.0 --no-update
```

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.0 --no-update
```

### 例 — 品質パッチ

品質パッチには主に機能が含まれる _および_ セキュリティの修正。 ただし、新しい後方互換性のある機能を含めることができます。 Composer を使用して、品質パッチをダウンロードします。 例えば、Magento Open Source2.4.1 のメタパッケージを指定するには、次のようにします。

```bash
composer require-commerce magento/product-community-edition 2.4.3 --no-update
```

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.3 --no-update
```

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.3 --no-update
```

### 例 — セキュリティパッチ

セキュリティパッチにはセキュリティ修正のみが含まれています。 これらは、アップグレードプロセスをより迅速かつ容易にするように設計されています。

セキュリティパッチでは、Composer の命名規則を使用します `2.4.x-px`. Composer を使用してパッチを指定します。

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.3-p1 --no-update
```

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.3-p1 --no-update
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

ストアフロント URL を Web ブラウザーで開き、アップグレードが成功したかどうかを確認します。 アップグレードに失敗した場合、ストアフロントは正しく読み込まれません。

アプリケーションが  `We're sorry, an error has occurred while generating this email.` エラー：

1. リセット [ファイルシステムの所有権と権限](../../installation/prerequisites/file-system/configure-permissions.md) を使用して `root` 権限。
1. 次のディレクトリをクリアします。
   - `var/cache/`
   - `var/page_cache/`
   - `generated/code/`
1. Web ブラウザーでストアフロントを再度確認してください。
