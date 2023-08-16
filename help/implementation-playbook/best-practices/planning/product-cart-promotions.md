---
title: プロモーション設定のベストプラクティス
description: コマースストアのパフォーマンスを最適化するためのセールスルールとクーポンコードの設定に関するベストプラクティスを説明します。
role: User
feature: Best Practices, Price Rules, Shopping Cart
exl-id: 6e177836-b8da-4e55-842c-e12ff54ffaf5
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# プロモーション設定のベストプラクティス

最高のパフォーマンスを得るには、次のベストプラクティスに従って、買い物かご内の品目の販売とプロモーションを設定します。

- **販売ルール（買い物かごの価格ルール）** — すべての Web サイトに対して 1,000 以下の買い物かご価格ルールを設定
   - 未使用のルールを管理および削除します。
   - 最も効率的な照合をおこなうために、厳密なルール条件（属性やカテゴリフィルターなど）を追加します。
- **クーポン**—
   - データベース内のクーポンの合計数が 250,000 未満であることを確認します。
   - 未使用および期限切れのクーポンを削除します。
   - キャンペーン要件を満たすのに必要なクーポン数のみを生成します。

## 影響を受ける製品およびバージョン

[サポートされているすべてのバージョン](../../../release/versions.md) /:

- Adobe Commerce an cloud infrastructure
- Adobe Commerceオンプレミス

## パフォーマンスへの潜在的な影響

買い物かごの価格ルールまたはクーポンの推奨最大数を超えると、次の方法でサイトのパフォーマンスに影響を与える可能性があります。

- 製品が買い物かごに追加される際の応答時間が増加しました。
- ミニカートの読み込みとレンダリングに要する時間が増加しました。
- 買い物かごページのレンダリングに要する時間が長くなりました。
- レンダリング時間が長くなりました。 **合計** ブロックを「チェックアウト」ページに追加します。
- クーポンの適用には、2 秒以上かかる場合があります。

## 追加情報

- [マーケティングキャンペーンとプロモーションについて](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#campaigns)
- [買い物かごの価格ルール](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart.html)
- [チュートリアル：買い物かごの価格ルールの作成](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/marketing/cart-price-rules.html)
- [クーポンコード](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html)
- [Adobe Commerce on cloud infrastructure：ストア設定のベストプラクティス](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
