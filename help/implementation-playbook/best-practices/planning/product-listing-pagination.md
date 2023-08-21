---
title: 製品リストのページネーションのベストプラクティス
description: ストアフロントカタログの各ページに表示する製品の数を管理して、Adobe Commerceのパフォーマンスを最適化する方法について説明します。
role: User, Admin
feature: Best Practices, Catalog Management
exl-id: 473f23a9-53fb-41a6-9b3a-af7bd1208be0
source-git-commit: df8878a3fea19b8f1780b5037273e18b5a3f1373
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# 製品リストのページネーションのベストプラクティス

最高のパフォーマンスを得るには、1 ページに最大 48 個の製品を表示します。

買い物客が 1 つのページですべてのカテゴリ製品を表示できるようにAdobe Commerceを設定できます。 カテゴリ製品の数が 48 製品を大幅に超える場合、ストアフロントのページネーションコントロールのカタログ設定を更新します。

## 影響を受ける製品およびバージョン

[サポートされているすべてのバージョン](../../../release/versions.md) /:

- Adobe Commerce an cloud infrastructure
- Adobe Commerceオンプレミス

## 製品リスト設定の更新

どのカテゴリにも 48 個を超える製品がある場合は、ストアフロントカタログ設定を更新して、「 **1 ページのすべての製品を許可**.

このオプションを無効にした後、Adobe Commerceは製品リストストアフロントのページネーションコントロールを使用して、ストアフロントコンポーネントに表示される製品の数を管理します。 手順については、 [ページネーションコントロールの設定](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html#configure-the-pagination-controls).

## 追加情報

- [製品リストの設定](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html)
