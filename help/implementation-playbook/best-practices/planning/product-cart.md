---
title: 製品カートのベストプラクティス
description: 買い物かご内の製品数を制限して、Adobe Commerceのパフォーマンスを最適化する方法を説明します。
role: User
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---


# 製品カート管理のベストプラクティス

パフォーマンスを最高にするには、次のガイドラインに従って、Adobe CommerceとMagento Open Sourceの買い物かごの上限を管理します。

- バージョン 2.3.x ～ 2.4.2 の場合、買い物かご内で最大 100 個の製品を使用できます。
- バージョン 2.4.3 以降では、販売ルール機能の強化により、買い物かごの最大数が 750 に増えました。


バージョン 2.3.x ～ 2.4.2 では、買い物かごの品目の制限に基づく期待されるパフォーマンスは次のとおりです。

- 最大 **100** 買い物かご内の製品 — 製品が機能し、応答時間のパフォーマンス目標を満たしている。
- 最大 **300** 買い物かご内の製品 — 製品は機能しますが、応答時間はターゲットを上回って増加します。
- 上 **500** 買い物かご内の製品 — 買い物かごとチェックアウトフローが機能する保証はありません

## 影響を受ける製品およびバージョン

[サポートされているすべてのバージョン](../../../release/versions.md) /:

- Adobe Commerce an cloud infrastructure
- Adobe Commerceオンプレミス

## 買い物かごの項目数の削減

次の戦略を使用して、買い物かごの項目数を管理します

- 行数が少ない、複数の小さな注文に分割するには、 [!UICONTROL Add Item by SKU] 機能。
- 項目のリストの読み込みに必要なカスタムロジックと買い物かごのカスタマイズのみを追加します。

## パフォーマンスへの潜在的な影響

買い物かごに商品が推奨最大数を超えると、次の方法でサイトのパフォーマンスに影響を与える可能性があります。

- データ取得操作、買い物かご項目の検証、価格ルールの適用確認、税金および合計計算に関する応答時間が増加しました。
- 買い物かごビュー、チェックアウトフロー、実行のレンダリングを含む、ミニカートのレンダリングの応答時間が増加しました。
- ミニカートが存在するすべてのサイトページの読み込み時間が増加しました。

## 追加情報

- [製品オプションの設定](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-options.html)
- [買い物かごの管理](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/shopping-assisted-cart-manage.html)
