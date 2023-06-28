---
title: 製品制限のベストプラクティス
description: サイトのパフォーマンスを最大化するために、製品在庫管理単位 (SKU) を設定する際のベストプラクティスについて説明します。
role: Admin
feature: Best Practices, Catalogs
exl-id: 37af7b92-05ac-4a4f-9009-11e8d9f95c2f
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# 製品 SKU 設定のベストプラクティス

パフォーマンスを最大限に高めるために、有効な製品在庫管理単位 (SKU) の推奨最大数は 2 億 4200 万です。 この有効な製品 SKU の最大値は、次のように計算されます。

```text
Effective SKU = N[SKUs] x N[Stores] x N[Customer groups]
```

ここで、

- N は、そのカテゴリの項目数を表します。
- 顧客グループには、追加の顧客グループが作成されるので、共有カタログが含まれます。

有効な SKU の数が上限を超えると、製品データの取得が遅くなり、管理パネルの操作やインデックス作成が完了するまでの時間が長くなります。

## 影響を受ける製品およびバージョン

[サポートされているすべてのバージョン](../../../release/versions.md) /:

- Adobe Commerce an cloud infrastructure
- Adobe Commerceオンプレミス

## 製品数を削減

次の戦略を使用して、製品数 (SKU) を減らします。

- 乗数を最小化 —
   - Web サイトを統合すると、乗数が減ります。 50,000 個の SKU、10 個の Web サイト、10 個の顧客グループがある場合、「有効な SKU 数」は 500 万個になります。 5 つの顧客グループを削除すると、有効な SKU 数が 250 万に削減されます。
   - カスタム価格設定に代替の製品機能を使用して、共有カタログと顧客グループの乗数を置き換えます。
   - 店舗内の有効な SKU 数に対する乗数として、顧客グループと共有カタログの両方が機能します。
- カタログの再構築：
   - カテゴリに割り当てる製品の数を減らします。
   - Web サイト、顧客グループ、共有カタログ、製品数、設定可能な製品オプション数を減らして、SKU 数を減らす
- 個別の製品を作成する代わりに、カスタムオプションを使用して、より多くの製品バリエーションを提供します。
- 有効な SKU には、価格が店舗や顧客グループごとに異なるように指定される場合があるので、価格が変わる可能性がある値が多数含まれる可能性があると考えます。
- モジュールなどの未使用のシステムコンポーネントを非アクティブ化または削除します。 (  [モジュールのアンインストール](../../../installation/tutorials/uninstall-modules.md).)
- 外部の Platform Management System(PMS) で製品を管理します。

## 追加情報

- [製品の作成](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [製品の割り当て](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- [共有カタログの操作](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared.html)
- クラウドインフラストラクチャ： [複数の Web サイトおよびストアを設定する](https://devdocs.magento.com/cloud/project/project-multi-sites.html)
- オンプレミス： [複数の Web サイトまたはストア](../../../configuration/multi-sites/ms-overview.md)
- [Adobe Commerce on cloud infrastructure:ストア設定のベストプラクティス](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
