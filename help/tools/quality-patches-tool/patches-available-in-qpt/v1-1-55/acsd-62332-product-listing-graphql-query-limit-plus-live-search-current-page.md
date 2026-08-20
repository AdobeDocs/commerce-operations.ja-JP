---
title: ACSD-62332：製品リスト GraphQL クエリが10,000個の製品に制限され、現在のページが [!DNL Live Search] に1に設定されました
description: ACSD-62332 パッチを適用して、GraphQL クエリがtotal_countに制限されているAdobe Commerceの問題を修正します。GraphQLを介してクエリを実行すると、検索条件で*2*ではなく*1*に現在のページが [!DNL Live Search] 設定されます。
feature: GraphQL, Products, Search
role: Admin, Developer
exl-id: 3623a337-32e9-468b-a82b-6a7f7fa943c9
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-62332：製品リスト GraphQL クエリが10,000個の製品に制限され、[!DNL Live Search]が現在のページを1に設定します

>[!NOTE]
>
>このパッチは、[ACSD-55100](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-46/acsd-55100-graphql-does-not-return-products-beyond-10k-in-the-search-results.md)の更新バージョンであり、2.4.6 ～ 2.4.6-p8 バージョンの[ACSD-52801](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-40/acsd-52801-graphql-product-filter-query-not-showing-partial-match-results.md)に置き換わります。 詳しくは、対応する記事を参照してください。

ACSD-62332 パッチでは、GraphQLを介してクエリを実行する際に、商品リストのGraphQL クエリが10,000個の商品の`total_count`に制限され、[!DNL Live Search]が検索条件のページ *2*&#x200B;ではなく&#x200B;*1*&#x200B;に現在のページを設定する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55がインストールされている場合に利用できます。 パッチ IDはACSD-62332です。 Adobe Commerce 2.4.7で問題が修正されていることに注意してください。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

GraphQL クエリの商品リストは、合計数が10,000件に制限されており、[!DNL Live Search]はGraphQLを介してクエリを実行した場合、検索条件のページ *2*&#x200B;ではなく、現在のページを&#x200B;*1*&#x200B;に設定します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。


## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
