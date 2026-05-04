---
title: ACSD-57477：販売ルールの処理により、カート関連のリクエストのパフォーマンスが低下する
description: Acsd-57477 パッチを適用して、使用可能な製品属性が多いプロジェクト（例えば、1000個の属性）で、AddProductsToCart GraphQL オペレーションが変数で実行される場合、Commerceはこれらの製品属性をすべて読み込もうとし、AddProductsToCart GraphQL オペレーションからパフォーマンスの問題が発生するAdobe Commerceの問題を修正します。
feature: GraphQL, Shopping Cart
role: Admin, Developer
type: Troubleshooting
exl-id: 3944b4d4-09c0-49a4-9a7e-8e1758d9d73c
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# ACSD-57477：販売ルールの処理により、カート関連のリクエストのパフォーマンスが低下する

ACSD-57477 パッチは、販売ルール処理によってカート関連のリクエストのパフォーマンスが遅くなる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69がインストールされている場合に利用できます。 パッチ IDはACSD-57477です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p11

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

GraphQL変数としてパラメーターを送信すると、販売ルール処理によってカート関連のリクエストのパフォーマンスが低下します。

<u>複製する手順</u>:

1. 1,000個の製品属性を追加。
1. 以下のGraphQL クエリを使用してカートを作成します。

   ```graphql
   mutation {createEmptyCart}{noformat}
   ```

1. 以下のGraphQL クエリを使用して、商品をカートに追加します。

   ```graphql
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

   ```json
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

1. この問題は、パラメーターをGraphQL変数として送信する場合にのみ発生します。 GraphQL クエリ自体にパラメーターを含めると、この問題は発生しません。
1. GraphQL クエリ自体にパラメーターを追加した後、同じ&#x200B;**Add To Cart** リクエストを送信します。

   ```graphql
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

<u>期待される結果</u>:

`AddProductsToCart` GraphQL操作のパフォーマンスを低下させないでください。

<u>実際の結果</u>:

パラメーターが変数として送信されると、すべての製品属性が読み込まれるため、`AddProductsToCart` GraphQL操作のパフォーマンスが低下します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > Commerce クラウドインフラストラクチャ上のパッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」ガイド

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール
