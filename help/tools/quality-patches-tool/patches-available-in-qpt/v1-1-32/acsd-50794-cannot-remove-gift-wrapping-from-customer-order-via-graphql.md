---
title: 'ACSD-50794: GraphQLを介してお客様からの注文からギフトラッピングを削除できない'
description: ACSD-50794 パッチを適用して、GraphQLを介してお客様の注文からギフトラッピングを削除できないAdobe Commerceの問題を修正します。
feature: Gift, GraphQL, Orders
role: Admin
exl-id: e088fb18-89d3-47e4-ad02-54068c1ab653
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# ACSD-50794: GraphQLを介してお客様からの注文からギフトラッピングを削除できない

ACSD-50794 パッチでは、GraphQLを介してお客様の注文からギフトラッピングを削除できない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.32がインストールされている場合に利用できます。 パッチ IDはACSD-50794です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

お客様は、GraphQLを介して、お客様の注文からギフトラッピングを削除することはできません。

<u>複製する手順</u>:

1. フロントエンドから顧客を構築する。
1. シンプルな商品の作成。
1. *[!UICONTROL Gift Messages]*&#x200B;を有効にするには、**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Gift Options]**&#x200B;に移動し、*[!UICONTROL Allow Gift Messages]* = *[!UICONTROL Yes]*&#x200B;を設定します。
1. **[!UICONTROL Stores]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Gift Wrapping]**&#x200B;に移動して、*[!UICONTROL Gift Wrapping]*&#x200B;を作成します。
1. 顧客トークンを取得します。
1. 空のカート、customerCartを作成します。
   * 商品をカートに追加：`addProductsToCart`個の変異
   * 請求先住所を設定：`setBillingAddressOnCart`変更
   * 配送先住所の設定：`setShippingAddressesOnCart`の変更
   * 配送方法を設定：`setShippingMethodsOnCart`の変異（定額制）
   * 支払い方法を設定：`setPaymentMethodOnCart`の変更（チェックモ）
1. 次に、このカートクエリで&#x200B;*Uid*&#x200B;をラッピングするギフトを確認します。

   ```GraphQL
   {
     cart(cart_id: "{{CART_ID}}") {
       available_gift_wrappings{
           uid
       }
   }
   }
   ```

1. `setGiftOptionsOnCart`を使用してギフトのラップを設定します。
1. cart: cart クエリを確認します。
1. `setGiftOptionsOnCart` （値をnullに設定）を使用してギフトのラップを解除します。
1. 繰り返しますが、「cart: cart」クエリを確認します。
1. 順序の変更：`placeOrder`個。
1. 顧客クエリの実行：顧客。

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

<u>期待される結果</u>:

ユーザーがギフトラップを設定し、設定を解除すると、顧客クエリはnullを返します。

<u>実際の結果</u>:

顧客の問い合わせは、適用されたギフトの包装を引き続き返します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
