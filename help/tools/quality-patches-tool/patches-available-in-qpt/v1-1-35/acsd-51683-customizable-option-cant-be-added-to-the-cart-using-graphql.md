---
title: ACSD-51683:GraphQLを使用してカスタマイズ可能なオプションを買い物かごに追加できない
description: ACSD-51683 パッチを適用すると、GraphQLを使用してカスタマイズ可能なオプションを買い物かごに追加できないAdobe Commerceの問題を修正できます。
feature: GraphQL
role: Admin
exl-id: 9cdf71aa-3dea-4f8c-b4d6-d6f192a9710d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-51683:GraphQLを使用してカスタマイズ可能なオプションを買い物かごに追加できない

ACSD-51683 パッチは、GraphQLを使用してカスタマイズ可能なオプションを買い物かごに追加できない問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.35 がインストールされている場合に使用できます。 パッチ ID は ACSD-51683 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

GraphQLを使用してカスタマイズ可能なオプションを買い物かごに追加することはできません。

<u> 再現手順 </u>:

1. カスタマイズ可能な **テキストフィールド** オプションを使用して、シンプルな製品を作成します。
1. [ 買い物かごに追加 ](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/add-product-to-cart/) 作成された商品と、GraphQLを介した必要なカスタマイズ可能なオプション。
1. [ 買い物かご ](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/queries/cart/)GraphQL リクエストを送信して、買い物かご内の商品とその詳細を確認します。

<u> 期待される結果 </u>

GraphQL応答の `Customizable_options` セクションには、商品を買い物かごに追加する際に提供されたデータが含まれています。

<u> 実績 </u>

GraphQL応答の `Customizable_options` セクションが空です。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
