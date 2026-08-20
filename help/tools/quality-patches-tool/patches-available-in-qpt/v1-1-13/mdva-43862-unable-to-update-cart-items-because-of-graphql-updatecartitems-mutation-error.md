---
title: MDVA-43862：お客様がGraphQL UpdateCartItemsの変更エラーが原因で買い物かごのアイテムを更新できない
description: MDVA-43862 パッチは、GraphQL UpdateCartItemsの変更エラーにより、お客様が買い物かごのアイテムを更新できない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.13がインストールされている場合に利用できます。 パッチ IDはMDVA-43862です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。
feature: GraphQL, Orders, Shopping Cart
role: Admin
exl-id: d8a2579f-58f5-4407-8006-d58794a84b1f
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---

# MDVA-43862：お客様がGraphQL UpdateCartItemsの変更エラーが原因で買い物かごのアイテムを更新できない

MDVA-43862 パッチは、GraphQL UpdateCartItemsの変更エラーにより、お客様が買い物かごのアイテムを更新できない問題を解決します。 このパッチは、[品質パッチツール（QPT） ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.13がインストールされている場合に使用できます。 パッチ IDはMDVA-43862です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p1、2.4.2-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.3 - 2.4.4

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

GraphQL UpdateCartItems mutation エラーが発生したため、お客様は買い物かご商品を更新できません。

<u>複製する手順</u>:

1. 1つのシンプル（MH01-XL-Gray）を割り当てて、設定可能な製品（MH01）を作成します。
1. Commerce Admin > **Catalog** > **Products** > **SKU** > **MH01** > **Customable Options**&#x200B;に移動します。
1. 製品にカスタムオプションを追加します。
   * オプションタイトル：Option1
   * オプションタイプ：フィールド
   * 必須：はい
   * 価格：10.00
   * 価格タイプ：固定
   * SKU: MHC1
   * 最大文字数：25
1. 以下のGraphQL クエリを実行して、カート IDを生成します。

   ```GraphQL
   mutation {
     createEmptyCart
   }
   ```

1. カート ID コードを書き留めます。
1. 以下のクエリを実行して、設定可能な商品をカートに追加します。

   ```GraphQL
   mutation {
   addConfigurableProductsToCart(
   input: {
       cart_id: "<cart ID from above step>",
       cart_items: [{
       parent_sku: "MH01",
       data: {
           quantity: 1,
           sku: "MH01-XL-Gray"
           },
           customizable_options: {
               id: 1,
               value_string: "2"
               }
           }
       ]
   }
   )
   {
   cart {
     items {
       uid
       quantity
       product {
         name
         sku
       }
       ... on ConfigurableCartItem {
         configurable_options {
           option_label
         }
       }
     }
   }
   }
   }
   ```

1. カートに設定可能な項目が入力されていることがわかります。
1. 返されたUIDをメモします。
1. 繰り返しますが、以下のクエリを実行してカート項目を更新します。

   ```GraphQL
   mutation {
     updateCartItems(
       input: {
         cart_id: "<cart ID from previous step>",
         cart_items: [
           {
             cart_item_uid: "<uid from previous step>"
             quantity: 3,
             customizable_options:[{
                 id: 1,
                 value_string: "67"
             }]
           }
         ]
       }
     ){
       cart {
         items {
           uid
           product {
             name
           }
           quantity
         }
         prices {
           grand_total{
             value
             currency
           }
         }
       }
     }
   }
   ```

1. 応答を観察します。

<u>期待される結果</u>:

カートは何の問題もなく更新されます。

<u>実際の結果</u>:

次のエラーが表示されます。

```GraphQL
{
  "errors": [
    {
      "message": "Could not update cart item: You need to choose options for your item.",
      "extensions": {
        "category": "graphql-input"
      },
      "locations": [
        {
          "line": 2,
          "column": 3
        }
      ],
      "path": [
        "updateCartItems"
      ]
    }
  ],
  "data": {
    "updateCartItems": null
  }
}
```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
