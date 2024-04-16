---
title: サンプルデータモジュールを削除または更新
description: Adobe Commerce サンプルデータモジュールを管理するには、次の手順に従います。
exl-id: d23f999f-18bf-449b-be23-bdf392dda539
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---

# サンプルデータモジュールを削除または更新

このトピックでは、次の方法について説明します。

* [サンプルデータモジュールの削除](#remove-sample-data-modules) Adobe CommerceまたはMagento Open Sourceのインストールから `composer.json`. このオプション *ではない* データベースからサンプルデータを削除します。

* [サンプルデータ更新の準備](#prepare-to-update-sample-data) （例えば、Magentoアプリケーションをアップデートする前に）。

## サンプルデータモジュールの削除

次のコマンドを入力します。

```bash
bin/magento sampledata:remove
```

サンプルデータモジュールの完全なリストを次に示します。

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

## サンプルデータ更新の準備

このコマンドを使用すると、Adobe CommerceまたはMagento Open Sourceを更新する前に、サンプルデータを更新できます。

更新用のサンプルデータを準備するには、次のコマンドを入力します。

```bash
bin/magento sampledata:reset
```

その後、 [アプリケーションの更新](../tutorials/uninstall.md#update-the-application).
