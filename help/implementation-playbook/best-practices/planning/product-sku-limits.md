---
title: 製品制限のベストプラクティス
description: サイトのパフォーマンスを最大化するために、製品在庫管理単位 (SKU) を設定する際のベストプラクティスについて説明します。
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 3a187ae8c066e56df0d7f4981d26ffb934f64576
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 製品 SKU 設定のベストプラクティス

パフォーマンスを最大限に高めるために、有効な製品在庫管理単位 (SKU) の推奨最大数は 2 億 4200 万です。 この有効な製品の最大数は、次のように計算されます。

```text
Effective SKU = N\[SKUs\] * Stores/Websites * Customer Groups
```

有効な SKU の数が上限を超えると、製品データの取得が遅くなり、管理操作が完了するまでの時間が長くなります。

## 影響を受ける製品およびバージョン

[サポートされているすべてのバージョン](../../../release/versions.md) /:

- Adobe Commerce an cloud infrastructure
- Adobe Commerceオンプレミス

## 製品数を削減

次の戦略を使用して、製品数 (SKU) を減らします。

- 乗数を最小化 —
   - ストアや Web サイトを移動すると、乗数が減ります。 50,000 個の SKU、10 個の Web サイト、10 個の顧客グループがある場合、「有効な SKU 数」は 500 万個になります。 5 つの顧客グループを削除すると、有効な SKU 数が 250 万に削減されます。
   - カスタム価格設定に代替の製品機能を使用して、共有カタログと顧客グループの乗数を置き換えます。
- カタログの再構築：
   - カテゴリに割り当てる製品の数を減らします。
   - 店舗、Web サイト、顧客グループまたは製品数を減らして、SKU 数を減らします。
- 個別の製品を作成する代わりに、カスタムオプションを使用して、より多くの製品バリエーションを提供します。
- モジュールなどの未使用のシステムコンポーネントを非アクティブ化または削除します。 (  [モジュールのアンインストール](../../../installation/tutorials/uninstall-modules.md).)
- 外部の Platform Management System(PMS) で製品を管理します。

## 追加情報

- [製品の作成](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [製品の割り当て](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- クラウドインフラストラクチャ： [複数の Web サイトおよびストアを設定する](https://devdocs.magento.com/cloud/project/project-multi-sites.html)
- オンプレミス： [複数の Web サイトまたはストア](../../../configuration/multi-sites/ms-overview.md)
- [Adobe Commerce on cloud infrastructure:ストア設定のベストプラクティス](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
