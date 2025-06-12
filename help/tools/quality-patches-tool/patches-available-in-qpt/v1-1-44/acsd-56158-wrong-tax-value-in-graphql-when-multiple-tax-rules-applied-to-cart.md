---
title: ACSD-56158：複数の税務処理基準が買い物かごに適用された場合の、GraphQL応答の誤った税額
description: 複数の税務処理基準が買い物かごに適用されている場合に、GraphQL応答で表示される税金値が正しくないAdobe Commerceの問題を修正するために、ACSD-56158 パッチを適用してください。
feature: GraphQL, Taxes
role: Admin, Developer
exl-id: dc22861c-cd41-402f-be37-d02c02b59433
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# ACSD-56158：複数の税務処理基準が買い物かごに適用された場合の、GraphQL応答の誤った税額

ACSD-56158 パッチでは、複数の税務処理基準が買い物かごに適用されている場合に、GraphQL応答で表示される税額が正しくない問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.44 がインストールされている場合に使用できます。 パッチ ID は ACSD-56158 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p5

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p5 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

複数の税務処理基準が買い物かごに適用されている場合、GraphQLの応答で表示される税額が正しくありません。

<u> 再現手順 </u>:

1. 米国住所を持つ顧客を作成します。
1. 管理パネルに移動します。
1. 100 ドルの値段で商品を作りなさい。
1. 米国の住所に 2 つの税率を作成します。1 つは 10% 用、もう 1 つは 5% 用です。
1. **[!UICONTROL Stores]**/**[!UICONTROL Taxes]**/**[!UICONTROL Tax Rule]** から米国の 2 つの税務処理基準を設定します。
1. 1 つのルールに 1 つの税率を割り当てます。
1. フロントエンドから、米国アドレスを持つ顧客としてログインし、商品を買い物かごに追加します。
1. GraphQLを介して顧客トークンを生成します。
1. GraphQLから買い物かご ID を生成します。
1. GraphQL経由でお客様の買い物かごを取得して、適用された税金が正しいことを確認します。

   ```GraphQL
   {
       cart(cart_id: "o3Yqt6zkn8ncOzFxGnR1IWdT..") {
           id
           email
           billing_address {
               city
               country {
                   code
                   label
               }
               firstname
               lastname
               company
               postcode
               vat_id
               region {
                   code
                   label
               }
               street
               telephone
           }
           shipping_addresses {
               firstname
               lastname
               company
               street
               city
               postcode
               vat_id
               region {
                   code
                   label
               }
               country {
                   code
                   label
               }
               telephone
               available_shipping_methods {
                   amount {
                       currency
                       value
                   }
                   available
                   carrier_code
                   carrier_title
                   error_message
                   method_code
                   method_title
                   price_excl_tax {
                       value
                       currency
                   }
                   price_incl_tax {
                       value
                       currency
                   }
               }
               selected_shipping_method {
                   amount {
                       value
                       currency
                   }
                   carrier_code
                   carrier_title
                   method_code
                   method_title
               }
           }
           available_payment_methods {
               code
               title
           }
           selected_payment_method {
               code
               title
           }
           applied_coupons {
               code
           }
           prices {
               grand_total {
                   value
                   currency
               }
               subtotal_excluding_tax {
                   value
                   currency
               }
               subtotal_including_tax {
                   value
                   currency
               }
               applied_taxes {
                   label
                   amount {
                       currency
                       value
                   }
               }
           }
       }
   }    
   ```

<u> 期待される結果 </u>:

各税率には、独自の税額が表示されます。

```
"applied_taxes": [
    {
        "label": "US-CA-*-Rate 1",
        "amount": {
            "currency": "USD",
            "value": 10
        }
    },
    {
        "label": "US-CA-*-Rate 2",
        "amount": {
            "currency": "USD",
            "value": 5
        }
    }
]
```

<u> 実際の結果 </u>:

各処理基準に対して戻される税額合計：

```
"applied_taxes": [
    {
        "label": "US-CA-*-Rate 1",
        "amount": {
            "currency": "USD",
            "value": 15
        }
    },
    {
        "label": "US-CA-*-Rate 2",
        "amount": {
            "currency": "USD",
            "value": 15
        }
    }
]
```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
