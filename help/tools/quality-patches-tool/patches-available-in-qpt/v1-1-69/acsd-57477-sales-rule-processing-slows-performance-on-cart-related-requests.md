---
title: ACSD-57477：販売ルールの処理により、買い物かごに関連するリクエストのパフォーマンスが低下する
description: ACSD-57477 パッチを適用すると、多数の製品属性（1000 属性など）が使用可能なプロジェクトで、Commerceが変数を使用して AddProductsToCart Adobe Commerce操作を実行する際に、GraphQLがこれらの製品属性をすべて読み込もうとすると AddProductsToCart GraphQL操作でパフォーマンスの問題が発生する Product の問題を修正できます。
feature: GraphQL, Shopping Cart
role: Admin, Developer
type: Troubleshooting
source-git-commit: 00fce49fbe5432a16324937e0430a08ec7c41188
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---


# ACSD-57477：販売ルールの処理により、買い物かごに関連するリクエストのパフォーマンスが低下する

ACSD-57477 パッチでは、販売ルールの処理によって買い物かごに関連するリクエストのパフォーマンスが低下する問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 がインストールされている場合に使用できます。 パッチ ID は ACSD-57477 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p11

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

パラメーターをGraphQL変数として送信すると、販売ルールの処理によって買い物かごに関連するリクエストのパフォーマンスが低下します。

<u> 再現手順 </u>:

1. 1000 の製品属性を追加します。
1. 以下のGraphQL クエリを使用して、買い物かごを作成します。

   ```
   mutation {createEmptyCart}{noformat}
   ```

1. 以下のGraphQL クエリを使用して、商品を買い物かごに追加します。

   ```
   mutation AddProductsToCart($cartId: String!, $products: [CartItemInput!]!) {
       addProductsToCart(cartId: $cartId, cartItems: $products) {
         cart {
           id
           __typename
         }
         __typename
       }
     }
   ```

1. これらの変数を設定します。

   ```
   {
     "cartId": "id_here",
     "products": [
       {
         "sku": "product_dynamic_1",
         "parent_sku": "product_dynamic_1",
         "quantity": 1
       }
     ]
   }
   ```

1. この問題は、パラメーターをGraphQL変数として送信した場合にのみ発生します。 GraphQLのクエリ自体にパラメーターを含めると、この問題は発生しません。
1. GraphQLのクエリ自体にパラメーターを追加した後、同じ **買い物かごに追加** リクエストを送信します。

   ```
   mutation {
    addProductsToCart(
      cartId: "id_here"
      cartItems:  [
       {
         sku: "product_dynamic_1",
         parent_sku: "product_dynamic_1",
         quantity: 1
       }
     ]
    ) {
      cart {
           id
           __typename
         }
         __typename
    }
   }
   ```

<u> 期待される結果 </u>:

`AddProductsToCart` GraphQLの操作パフォーマンスは低下しないようにしてください。

<u> 実際の結果 </u>:

パラメーターが変数として送信されると、すべての製品属性が読み込まれるので、`AddProductsToCart` GraphQLの操作パフォーマンスが低下します。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドの
* クラウドインフラストラクチャー上のAdobe Commerce:[ アップグレードとパッチ適用 ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) クラウドインフラストラクチャー上のCommerce ガイド

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]：品質向上パッチを適用するためのセルフサービス ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) ツール（『ツールガイド』）
