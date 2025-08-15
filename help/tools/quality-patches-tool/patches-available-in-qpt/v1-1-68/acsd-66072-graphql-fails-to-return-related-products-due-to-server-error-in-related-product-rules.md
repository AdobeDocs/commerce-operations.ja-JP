---
title: ACSD-66072:GraphQLが関連商品を商品詳細ページに返さない
description: 関連する商品ルールが設定されている際に内部サーバーエラーが原因で関連商品が商品詳細ページのGraphQLから返されないAdobe Commerceの問題を修正するため、ACSD-66072 パッチを適用します。
feature: GraphQL, Products
role: Admin, Developer
type: Troubleshooting
exl-id: a706a710-aed3-41a4-bc87-3150e9ba95f7
source-git-commit: 8bb921704239d2b4622931a7814759bda5e9401f
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# ACSD-66072:GraphQLが関連商品を商品詳細ページに返さない

ACSD-66072 パッチでは、設定時の内部サーバーエラーが原因で関連商品が商品詳細ページのGraphQLから返されない問題を修正し **[!UICONTROL Related Products Rule]** います。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 がインストールされている場合に使用できます。 パッチ ID は ACSD-66072 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p8

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

**[!UICONTROL Related Products Rule]** が設定されている場合、内部サーバーエラーが原因で、関連商品が商品詳細ページのGraphQLを介して返されません。

<u> 再現手順 </u>:

1. 設定可能な製品を作成します。
   * **製品 1**: `config1` と `option1`
   * **製品 2**: `config2` と `option2`

1. 製品を作成してカテゴリに割り当てる
   * **新規カテゴリ** を作成します。
   * 両方の製品（`config1` と `config2`）をこのカテゴリに割り当てます。

1. **[!UICONTROL Marketing]**/**[!UICONTROL Promotions]**/**[!UICONTROL Related Products Rule]** に移動し、次の設定を使用して新しいルールを作成します。

   * **[!UICONTROL Priority]**: 1
   * **[!UICONTROL Applies To]**: **[!UICONTROL Related Products]**
   * **[!UICONTROL Result Limit]**: 10
   * **[!UICONTROL Products to Match]**: **[!UICONTROL Attribute Set is Default]**
   * **[!UICONTROL Products to Display]**: `Product Category is the Same as Matched Product Categories`

1. 次のMagento CLI コマンドを実行します。

   ```bash
   bin/magento indexer:reindex
   bin/magento cache:clean
   ```

1. 次のペイロードで POST リクエストを `../graphql` に送信します。

   ```
   query getRelatedProductsForProductPage($urlKey: String!) 
   {
       products(filter: { url_key: { eq: $urlKey } }) 
       {
           items {
               id
               __typename
               uid
               url_key
               name
               sku
               related_products {
                   id
                   uid
                   name
                   sku
                   stock_status
                   url_key
                   small_image {
                       url
                       __typename
                       }
                       thumbnail {
                           url
                           __typename
                           }
                           image {
                               url
                               __typename
                               }
                               price_range {
                                   maximum_price {
                                       regular_price {
                                           currency
                                           value
                                           __typename
                                           }
                                           __typename
                                           }
                                           minimum_price {
                                               discount {
                                                   amount_off
                                                   percent_off
                                                   __typename
                                                   }
                                                   final_price {
                                                       currency
                                                       value
                                                       __typename
                                                       }
                                                       regular_price {
                                                           currency
                                                           value
                                                           __typename}
                                                           __typename}
                                                           __typename}
                                                           __typename
                                                           }
                                                           }
                                                           __typename
                                                           }
                                                           }
   ```

<u> 期待される結果 </u>:

クエリを実行すると、関連商品（`config1`）が返されます。

<u> 実際の結果 </u>:

```graphql
{
    "errors": [
        {
            "message": "Internal server error",
            "locations": [
                {
                    "line": 10,
                    "column": 7
                }
            ],
            "path": [
                "products",
                "items",
                0,
                "related_products"
            ]
        }
    ],
    "data": {
        "products": {
            "items": [
                {
                    "id": 4,
                    "__typename": "ConfigurableProduct",
                    "uid": "NA==",
                    "url_key": "config2",
                    "name": "config2",
                    "sku": "config2",
                    "related_products": null
                }
            ],
            "__typename": "Products"
        }
    }
}
```

`var/log/exception.log` ファイルには、次の内容が含まれます。

```
report.ERROR: Deprecated Functionality: explode(): Passing null to parameter #2 ($string) of type string is deprecated in /home/magento2ee/app/code/Magento/TargetRule/Model/ResourceModel/Index.php on line 557
```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
