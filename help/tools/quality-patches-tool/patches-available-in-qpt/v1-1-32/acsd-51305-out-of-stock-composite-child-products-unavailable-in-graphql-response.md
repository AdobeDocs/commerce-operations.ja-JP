---
title: ACSD-51305：在庫切れの複合子商品がGraphQLの対応で利用できません
description: ACSD-51305 パッチを適用して、在庫切れの複合子商品がGraphQLのレスポンスで利用できないAdobe Commerceの問題を修正します。
feature: Categories, GraphQL, Orders, Products
role: Admin
exl-id: 110bb332-2032-4aaf-b95e-971fc3382262
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%
---
# ACSD-51305：在庫切れの複合子商品がGraphQLの対応で利用できません

ACSD-51305 パッチは、GraphQLの対応で在庫切れの複合子商品が利用できない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.32がインストールされている場合に利用できます。 パッチ IDはACSD-51305です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

GraphQLの対応では、在庫切れの複合子商品は利用できません。

<u>複製する手順</u>:

1. Admin Web サイトにログインします。
1. カテゴリ（cat1、id=3）を作成します。
1. *simple1*&#x200B;商品を作成します（在庫切れで、個別に表示されないため、*cat1*&#x200B;に割り当てられます）。
1. *simple2*&#x200B;商品を作成します（在庫あり、個別に表示されないため、*cat1*&#x200B;に割り当てられます）。
1. *simple1*&#x200B;および&#x200B;*simple2*&#x200B;子商品をラジオボタン *option1*&#x200B;商品として&#x200B;*bundle1*&#x200B;商品を作成し、*cat1* カテゴリーに割り当てます。
1. **[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]**&#x200B;に移動します。

   * **[!UICONTROL Display Out of Stock Products]**&#x200B;を&#x200B;*はい*&#x200B;に設定します。

1. ストアフロントで&#x200B;*bundle1*&#x200B;製品を開き、*simple1*&#x200B;と&#x200B;*simple2*&#x200B;の両方の子製品がストアフロント内に表示されていることを確認します。
1. 次のGraphQL クエリを実行します。

   ```GraphQL
   {
       categoryList(filters: { ids: { in: ["3"] } }) {
           id
           name
           products(pageSize: 8, sort: { position: ASC }) {
               total_count
               items {
                   id
                   sku
                   name
                   ... on BundleProduct {
                       url_key
                       items {
                           title
                           sku
                           options {
                               quantity
                               position
                               is_default
                               product {
                                   id
                                   name
                                   sku
                               }
                           }
                       }
                   }
               }
           }
       }
   }
   ```

<u>期待される結果</u>:

**[!UICONTROL Options]** ブロック内の&#x200B;**[!UICONTROL Product]** セクションが空ではありません。

<u>実際の結果</u>:

**[!UICONTROL Options]** ブロック内の&#x200B;**[!UICONTROL Product]** セクションが空です。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
