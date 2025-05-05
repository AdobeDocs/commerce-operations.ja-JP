---
title: ACSD-62332：商品リスト GraphQL クエリが 10,000 個の商品に制限され、現在のページを 1 に設定している商品  [!DNL Live Search]  リスト
description: ACSD-62332 パッチを適用すると、Adobe Commerceの商品リストのGraphQL クエリが total_count の 10,000 個の商品に制限され、where [!DNL Live Search] GraphQLでクエリされた場合、検索条件でページ *2 ではなく*1*に現在のページが設定されるの問題が修正されます。
feature: GraphQL, Products, Search
role: Admin, Developer
source-git-commit: 276fe6ca8d1166a8f4254aca5d49cbb4b1aa607b
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-62332：商品リストのGraphQL クエリが 10,000 個の商品に制限され、[!DNL Live Search] が現在のページを 1 に設定している

>[!NOTE]
>
>このパッチは、[ACSD-55100](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-46/acsd-55100-graphql-does-not-return-products-beyond-10k-in-the-search-results.md) の更新バージョンであり、バージョン 2.4.6 ～ 2.4.6-p8 の [ACSD-52801](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-40/acsd-52801-graphql-product-filter-query-not-showing-partial-match-results.md) に代わるものです。 詳しくは、対応する記事を参照してください。

ACSD-62332 パッチは、商品リストのGraphQL クエリが 10,000 個の商品 `total_count` に制限され、GraphQL経由でクエリされ [!DNL Live Search] ときに検索条件で現在のページがページ *2* ではなく *1* に設定される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 がインストールされている場合に使用できます。 パッチ ID は ACSD-62332 です。 この問題はAdobe Commerce 2.4.7 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

GraphQLの商品リストに関するクエリは、total_count が 10,000 個の商品に制限されています。[!DNL Live Search] の場合、GraphQLでクエリすると、検索条件で現在のページがページ *2* ではなく *1* に設定されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。


## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
