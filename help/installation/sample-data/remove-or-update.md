---
title: サンプルデータモジュールの削除または更新
description: Adobe Commerce サンプルデータモジュールを管理するには、次の手順に従います。
exl-id: d23f999f-18bf-449b-be23-bdf392dda539
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 0%

---

# サンプルデータモジュールの削除または更新

主な内容：

* [Adobe Commerce インストール `composer.json`からサンプルデータモジュール &#x200B;](#remove-sample-data-modules)を削除します。 このオプションを選択すると、*not*&#x200B;がデータベースからサンプルデータを削除します。

* [&#x200B; サンプルデータの更新を準備します](#prepare-to-update-sample-data) （例えば、Magento アプリケーションを更新する前）。

## サンプルデータモジュールの削除

次のコマンドを入力します。

```shell
bin/magento sampledata:remove
```

サンプルデータモジュールの完全なリストは次のとおりです。

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

## サンプルデータの更新の準備

このコマンドを使用すると、Adobe Commerceを更新する前にサンプルデータを更新できます。

更新用のサンプルデータを準備するには、次のコマンドを入力します。

```shell
bin/magento sampledata:reset
```

その後、[&#x200B; アプリケーションを更新します](../tutorials/uninstall.md#update-the-application)。
