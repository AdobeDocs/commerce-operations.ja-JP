---
title: カテゴリ設定のベストプラクティス
description: カタログ内のカテゴリの数を制限してサイトのパフォーマンスを最大化するためのベストプラクティスについて説明します。
role: Admin
feature: Best Practices
exl-id: c6834b32-9ee8-4a4a-932c-9726f3feee3f
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# カテゴリ設定のベストプラクティス

最高のパフォーマンスを得るには、Adobe Commerceサイトのカテゴリの推奨数を超えないように設定してください。

- Adobe Commerceバージョン 2.4.2 以降の場合は、最大 6,000 個のカテゴリを設定します
- Adobe Commerceバージョン 2.3.x および 2.4.0 から 2.4.1-p1 の場合、最大 3,000 個のカテゴリを設定します。

## 影響を受ける製品およびバージョン

[サポートされているすべてのバージョン](../../../release/versions.md) /:

- Adobe Commerce an cloud infrastructure
- Adobe Commerceオンプレミス

## 製品数を削減

カテゴリの数を減らすには、次の方法を使用します。

- 属性とカスタムオプションを使用して独自の製品機能を管理
- 非アクティブなカテゴリを削除
- ナビゲーションでのカタログの深さの最適化

## パフォーマンスへの潜在的な影響

カテゴリの数が推奨される最大数を超えると、次の方法でサイトのパフォーマンスに影響を与える可能性があります。

- キャッシュされていないカタログページの応答時間が明確に増加
- 管理者からカテゴリを管理する際の長時間の実行とタイムアウト
- 対応するデータベーステーブルのサイズの増加
- インデックステーブルが大きいと、 `[category/product relation index\]`
- カテゴリ・ツリーの構築、メニューの取得、カテゴリ・ルールの管理操作を完了するまでの処理時間が短縮

## 追加情報

- [カテゴリ：概要](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/categories.html)
- [ナビゲーションの概要](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation.html)
- [製品の割り当て](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- [Adobe Commerce on cloud infrastructure:ストア設定のベストプラクティス](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
