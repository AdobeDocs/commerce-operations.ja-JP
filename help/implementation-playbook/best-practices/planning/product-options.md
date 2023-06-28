---
title: 製品オプション設定のベストプラクティス
description: 製品オプションの数を制限して、Adobe Commerceのパフォーマンスを最適化します。
role: Admin
feature: Best Practices, Catalogs
exl-id: 7571a163-798a-40be-b26f-4a184bceb809
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# 製品オプションのベストプラクティス

最高のパフォーマンスを得るには、1 つの製品につき最大 100 個の製品オプションを設定します。

## 影響を受ける製品およびバージョン

[サポートされているすべてのバージョン](../../../release/versions.md) /:

- Adobe Commerce an cloud infrastructure
- Adobe Commerceオンプレミス

## 製品オプションの削減

サイトのパフォーマンスを最高にするには、次の戦略を使用して製品オプションの数を減らします。

- 複雑な製品とカスタムオプションを製品バリエーションのソースとして設定します。
- すべての製品に適用されるグローバルな製品テンプレートやオプションコンテナを作成する代わりに、属性セットを使用して、ターゲット属性とオプションを持つ特定の製品テンプレートを作成します。
- 外部の製品管理システム (PMS) を通じて製品情報を管理します。

## パフォーマンスへの影響の可能性

多くの製品オプションを設定すると、すべての読み取りおよび書き込み操作で各製品に対して取得されるデータの量が増加し、次の結果が得られます。

- SQL クエリトラフィックの増加以上 `JOIN` 操作を実行すると、データベースのスループットが向上します。
- Adobe Commerceインデックスおよび全文検索インデックスのサイズを増やしました。

上記の増加は、次の方法でサイトのパフォーマンスに影響を与える可能性があります。

- 属性に多くのオプションを含む製品に関連するほとんどのストアフロントシナリオに対して、応答時間が長くなりました。
- 特にプロモーションルール管理を含む属性リストやツリー取得に関連するシナリオで、タイムアウトにつながる可能性のある、管理での製品管理操作の完了に要する時間が大幅に増加しました。
- インポートとエクスポート、共有カタログ内の複数の製品へのカスタム価格の割り当てなど、非同期の一括操作を完了するバルクアクションをブロックできます。

## 追加情報

- [製品の作成](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [製品属性設定のベストプラクティス](product-attributes-and-options.md)
- [バルクアクションログ](https://docs.magento.com/user-guide/system/action-log-bulk-actions.html)
- [在庫一括処理 API](https://developer.adobe.com/commerce/webapi/rest/inventory/bulk-inventory/)
- [トレーニング：Adobe Commerceを使用したカタログと製品の管理](https://learning.adobe.com/catalog/adobe_commerce/cours000000000098643.html)
