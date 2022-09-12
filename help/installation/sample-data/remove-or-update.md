---
title: サンプルデータモジュールを削除または更新
description: 以下の手順に従って、Adobe CommerceおよびMagento Open Sourceサンプルデータモジュールを管理します。
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---


# サンプルデータモジュールを削除または更新

このトピックでは、以下の方法について説明します。

* [サンプルデータモジュールの削除](#remove-sample-data-modules) Adobe CommerceまたはMagento Open Sourceのインストールから `composer.json`. このオプションは、 *not* データベースからサンプルデータを削除します。

* [サンプルデータ更新の準備](#prepare-to-update-sample-data) ( 例えば、アプリケーションアプリケーションを更新する前にMagento)。

## サンプルデータモジュールの削除

次のコマンドを入力します。

```bash
bin/magento sampledata:remove
```

サンプルデータモジュールの完全なリストは次のとおりです。

Adobe CommerceとMagento Open Source:

* `magento/module-bundle-sample-data`
* `magento/module-catalog-rule-sample-data`
* `magento/module-catalog-sample-data`
* `magento/module-cms-sample-data`
* `magento/module-configurable-sample-data`
* `magento/module-customer-sample-data`
* `magento/module-downloadable-sample-data`
* `magento/module-grouped-product-sample-data`
* `magento/module-msrp-sample-data`
* `magento/module-offline-shipping-sample-data`
* `magento/module-product-links-sample-data`
* `magento/module-review-sample-data`
* `magento/module-sales-rule-sample-data`
* `magento/module-sales-sample-data`
* `magento/module-sample-data`
* `magento/module-swatches-sample-data`
* `magento/module-tax-sample-data`
* `magento/module-theme-sample-data`
* `magento/module-widget-sample-data`
* `magento/module-wishlist-sample-data`
* `magento/sample-data-media`

Adobe Commerceのみ：

* `magento/module-customer-balance-sample-data`
* `magento/module-gift-card-sample-data`
* `magento/module-gift-registry-sample-data`
* `magento/module-multiple-wishlist-sample-data`
* `magento/module-target-rule-sample-data`

## サンプルデータ更新の準備

このコマンドを使用すると、Adobe CommerceまたはMagento Open Sourceを更新する前にサンプルデータを更新できます。

更新用のサンプルデータを準備するには、次のコマンドを入力します。

```bash
bin/magento sampledata:reset
```

その後 [アプリの更新](../tutorials/uninstall.md#update-the-application).
