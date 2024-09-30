---
title: 「ACSD-50794:GraphQL経由でお客様の注文からギフトラッピングを削除できない」
description: ACSD-50794 パッチを適用すると、GraphQLを介してお客様の注文からギフトラッピングを削除できないAdobe Commerceの問題を修正できます。
feature: Gift, GraphQL, Orders
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# ACSD-50794:GraphQL経由でお客様の注文からギフトラッピングを削除できない

ACSD-50794 パッチを使用すると、GraphQL経由でお客様の注文からギフトラッピングを削除できない問題が修正されます。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.32 がインストールされている場合に使用できます。 パッチ ID は ACSD-50794 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.1 ～ 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

GraphQLを使用して、お客様の注文からギフト包装を削除することはできません。

<u> 再現手順 </u>:

1. フロントエンドから顧客を作成します。
1. シンプルな製品を作成します。
1. **[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL Sales]**/**[!UICONTROL Gift Options]** に移動して *[!UICONTROL Gift Messages]* を有効にし、*[!UICONTROL Allow Gift Messages]*=*[!UICONTROL Yes]* を設定します。
1. **[!UICONTROL Stores]**/**[!UICONTROL Other Settings]**/**[!UICONTROL Gift Wrapping]** に移動して、*[!UICONTROL Gift Wrapping]* を作成します。
1. 顧客トークンを取得します。
1. 空の買い物かごである customerCart を作成します。
   * 買い物かごへの商品の追加：`addProductsToCart` ミューテーション
   * 請求先住所の設定：`setBillingAddressOnCart` ミューテーション
   * 配送先住所の設定：`setShippingAddressesOnCart` mutation
   * 配送方法を設定：`setShippingMethodsOnCart` mutation （flatrate）
   * 支払い方法を設定：`setPaymentMethodOnCart` mutation （checkmo）
1. 次に、この買い物かごクエリでギフト包装 *Uid* を確認します。

   ```GraphQL
   {
     cart(cart_id: "{{CART_ID}}") {
       available_gift_wrappings{
           uid
       }
   }
   }
   ```

1. `setGiftOptionsOnCart` を使用してギフトラップを設定します。
1. 買い物かご：買い物かごクエリを確認します。
1. `setGiftOptionsOnCart` を使用してギフト ラップの設定を解除します（値を null に設定します）。
1. もう一度、cart:cart クエリを確認します。
1. Place order: `placeOrder` mutation.
1. 顧客クエリ「customer」を実行します。

   ```GraphQL
   query {
     customer {
       firstname
       middlename
       lastname
       suffix
       email
       orders {
           items {
               order_date
               gift_wrapping {
                   design
                   uid
               }
           }
       }
       addresses {
         firstname
         middlename
         lastname
         street
         city
         region {
           region_code
           region
         }
         postcode
         country_code
         telephone
       }
     }
   }
   ```

<u> 期待される結果 </u>:

ユーザーがギフトラップを設定して設定解除すると、顧客クエリは null を返します。

<u> 実際の結果 </u>:

顧客クエリは、適用されたとおりにギフトラッピングを返します。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
