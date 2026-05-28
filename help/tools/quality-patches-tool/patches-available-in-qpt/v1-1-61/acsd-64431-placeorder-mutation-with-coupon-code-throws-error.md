---
title: 'ACSD-64431: リクエスト内のクーポンコードを持つ「placeOrder」の突然変異が内部サーバーエラーをスローする'
description: ACSD-64431 パッチを適用して、リクエスト内のクーポンコード情報を含む「placeOrder」変異が注文を正常に配置する代わりに内部サーバーエラーをスローするAdobe Commerceの問題を修正します。
feature: GraphQL, Orders, Promotions/Events
role: Admin, Developer
exl-id: 13918f3e-842b-4b2e-b2e2-2d8add542a87
type: Troubleshooting
source-git-commit: 319f3232d1ba5f5ed7cdd10ce85b9d7ffbeec89a
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-64431: リクエスト内のクーポンコードを持つ「placeOrder」の突然変異が内部サーバーエラーをスローする

ACSD-64431 パッチは、リクエストにクーポンコード情報を含む`placeOrder`の突然変異が、注文を正常に配置する代わりに内部サーバーエラーをスローする問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61がインストールされている場合に利用できます。 パッチ IDはACSD-64431です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

リクエストにクーポンコード情報が含まれている`placeOrder`の突然変異は、注文を正常に配置する代わりに、内部エラーをスローします。

<u>複製する手順</u>:

1. _SKU 2836611_&#x200B;でシンプルな商品を作成します。
1. **[!UICONTROL Cart Price Rule]**&#x200B;を作成し、**[!UICONTROL Coupon]**&#x200B;を`Specific Coupon`に設定し、_TEST1234_&#x200B;をクーポンコードとして入力します。
1. 顧客の作成：

   ```graphql
   mutation {
   createCustomer(
       input: {
       firstname: "John"
       lastname: "Doe"
       email: "john.doe@example.com"
       password: "b1b2b3l@w+"
       is_subscribed: true
       }
   ) {
       customer {
       firstname
       lastname
       email
       is_subscribed
       }
   }
   }
   ```

1. 顧客トークンを生成します。 このトークンは、その後のリクエストに使用できます。

   ```graphql
   mutation {
   generateCustomerToken(email: "john.doe@example.com", password: "b1b2b3l@w+") {
       token
   }
   }
   ```

1. 空のカートを作成します。 カート IDを保存し、その後のリクエストに使用します。

   ```graphql
   mutation {
       createEmptyCart
   } 
   ```

1. 商品をカートに追加します。

   ```graphql
   mutation {
       addProductsToCart(
           cartId: "xxxx"
           cartItems: [{ quantity: 1, sku: "2836611" }]
       ) {
           cart {
               itemsV2 {
                   items {
                       product {
                           name
                           sku
                       }
                       ... on ConfigurableCartItem {
                           configurable_options {
                               configurable_product_option_uid
                               value_label
                           }
                       }
                       quantity
                   }
                   total_count
                   page_info {
                       page_size
                       current_page
                       total_pages
                   }
               }
           }
           user_errors {
               code
               message
           }
       }
   }
   ```

1. クーポンの適用：

   ```graphql
   mutation {
       applyCouponToCart(input: { cart_id: "xxxx", coupon_code: "TEST1234" }) {
           cart {
               itemsV2 {
                   items {
                       product {
                           name
                       }
                       quantity
                   }
                   total_count
                   page_info {
                       page_size
                       current_page
                       total_pages
                   }
               }
               applied_coupons {
                   code
               }
               prices {
                   grand_total {
                       value
                       currency
                   }
               }
           }
       }
   }
   ```

1. 配送先住所の設定：

   ```graphql
   mutation {
       setShippingAddressesOnCart(
           input: {
               cart_id: "xxxxx"
               shipping_addresses: [
                   {
                       address: {
                           firstname: "John"
                           lastname: "Doe"
                           company: "Company Name"
                           street: ["3320 N Crescent Dr", "Beverly Hills"]
                           city: "Los Angeles"
                           region: "CA"
                           region_id: 12
                           postcode: "90210"
                           country_code: "US"
                           telephone: "123-456-0000"
                           save_in_address_book: false
                       }
                   }
               ]
           }
       ) {
           cart {
               shipping_addresses {
                   firstname
                   lastname
                   company
                   street
                   city
                   region {
                       code
                       label
                   }
                   postcode
                   telephone
                   country {
                       code
                       label
                   }
                   available_shipping_methods {
                       carrier_code
                       carrier_title
                       method_code
                       method_title
                   }
               }
           }
       }
   }
   ```

1. 配送方法を設定する：

   ```graphql
   mutation {
       setShippingMethodsOnCart(
           input: {
               cart_id: "xxxx"
               shipping_methods: [{ carrier_code: "flatrate", method_code: "flatrate" }]
           }
       ) {
           cart {
               shipping_addresses {
                   selected_shipping_method {
                       carrier_code
                       carrier_title
                       method_code
                       method_title
                       amount {
                           value
                           currency
                       }
                   }
               }
           }
       }
   }
   ```

1. 請求先住所の設定：

   ```graphql
   mutation {
       setBillingAddressOnCart(
           input: {
               cart_id: "xxxx"
               billing_address: {
                   address: {
                       firstname: "John"
                       lastname: "Doe"
                       company: "Company Name"
                       street: ["64 Strawberry Dr", "Beverly Hills"]
                       city: "Los Angeles"
                       region: "CA"
                       region_id: 12
                       postcode: "90210"
                       country_code: "US"
                       telephone: "123-456-0000"
                       save_in_address_book: true
                   }
               }
           }
       ) {
           cart {
               billing_address {
                   firstname
                   lastname
                   company
                   street
                   city
                   region {
                       code
                       label
                   }
                   postcode
                   telephone
                   country {
                       code
                       label
                   }
               }
           }
       }
   }
   ```

1. 決済方法を設定する：

   ```graphql
   mutation {
       setPaymentMethodOnCart(
           input: { cart_id: "xxxx", payment_method: { code: "checkmo" } }
       ) {
           cart {
               selected_payment_method {
                   code
               }
           }
       }
   }
   ```

1. 注文する：

   ```graphql
   mutation {
   placeOrder(
       input: {
       cart_id: "{{cart_id}}"
       }
   ) {
       orderV2 {
       number
       token
       }
       errors {
       message
       code
       }
   }
   }
   ```


<u>期待される結果</u>:

注文する必要があります。

<u>実際の結果</u>:

次のエラーメッセージが表示されます。
`"message": "Internal server error"`

`exception.log`に次のエラーが含まれています：

```text
    report.ERROR: "discount_model" value should be specifiedGraphQL (1:135)
    1: mutation { placeOrder(input: {cart_id: "xxxx"}) { orderV2 { total { discounts { amount { currency value } coupon { code } } } } errors { message code } } }
```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
