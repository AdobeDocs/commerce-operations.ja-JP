---
title: 「ACSD-44938：ゲストユーザーのGraphQL リクエストで VAT_ID を適用できない」
description: ACSD-44938 パッチは、ゲストユーザーのGraphQL リクエストで VAT_ID を適用できない問題を修正しました。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches） 1.1.18 がインストールされている場合に利用できます。 パッチ ID は ACSD-44938 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。
feature: Admin Workspace, GraphQL
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# ACSD-44938: ゲストユーザーのGraphQL リクエストで VAT_ID を適用できません

ACSD-44938 パッチは、ゲストユーザーのGraphQL リクエストで VAT_ID を適用できない問題を修正しました。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)1.1.18 がインストールされている場合に使用できます。 パッチ ID は ACSD-44938 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 ～ 2.4.3-p3

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

ゲストユーザーのGraphQL リクエストには VAT_ID を適用できません。

<u> 再現手順 </u>:

1. 開発者向けドキュメントの [GraphQL チュートリアル ](https://devdocs.magento.com/guides/v2.4/graphql/tutorials/checkout/checkout-shopping-cart.html) に記載されている手順に従って、買い物かごを作成します。
1. GraphQLを使用して、ゲストユーザーに VAT_ID を適用してみてください。

<u> 期待される結果 </u>:

VAT_ID は、登録済みの顧客と同じ方法で適用できます。 開発者向けドキュメントの [createCustomerAddress mutation](https://devdocs.magento.com/guides/v2.4/graphql/mutations/create-customer-address.html) の記事を参照してください。

<u> 実際の結果 </u>:

GraphQLを使用しているゲストユーザーに VAT_ID を適用することはできません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
