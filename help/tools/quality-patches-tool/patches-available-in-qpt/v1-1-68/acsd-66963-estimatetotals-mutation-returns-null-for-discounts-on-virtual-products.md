---
title: 'ACSD-66963: 「estimateTotals」ミューテーションが、仮想製品の割引に対して null を返す'
description: ACSD-66963 パッチを適用すると、「estimateTotals」がバーチャル商品のみを含む買い物かごに割引コードが適用された場合に割引のために*null*を返すAdobe Commerceの問題が修正されます。
feature: GraphQL
role: Admin, Developer
type: Troubleshooting
source-git-commit: 0eede09026df98426cd3b6b1550be274c26d7e13
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---


# ACSD-66963：仮想製品の割引に対して `estimateTotals` mutation が null を返す

ACSD-66963 パッチは、仮想製品のみを含む買 `estimateTotals` 物かごに割引コードが適用された場合に、割引のために *null* が返される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 がインストールされている場合に使用できます。 パッチ ID は ACSD-66963 です。 この問題はAdobe Commerce 2.4.8 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

仮想製品のみを含む買い物かごに割引コードが適用された場合、割引に対して `estimateTotals` ミューテーションは *null* を返します。

<u> 再現手順 </u>:

1. 仮想製品のみを含む買い物かごを作成します。
1. 割引コードを適用します。

   ```
   mutation {
     estimateTotals(
       input: {
         cart_id: "cart_id",
         address: {
           country_code: US,
           postcode: "78732",
           region: {
             region_code: "TX"
           }
         },
         shipping_method: {
           carrier_code: "{$shipping}",
           method_code: "{$shipping}"
         }
       }
     ) {
       cart {
         prices {
           discounts {
             amount {
               value
               currency
             }
             label
             coupon {
               code
             }
             applied_to
             type
           }
         }
       }
     }
   }
   ```

<u> 期待される結果 </u>:

仮想商品のみを含む買い物かごには、割引情報が含まれています。

    &quot;&#39;
    &lbrace;
    &quot;data&quot;: &lbrace;
    &quot;estimateTotals&quot;: &lbrace;
    &quot;cart&quot;: &lbrace;
    &quot;prices&quot;: &lbrace;
    &quot;discounts&quot;: &lbrack;
    &lbrace;
    &quot;amount&quot;: &lbrace;
    &quot;value&quot;: 100.5,
    &quot;currency&quot;: &quot;USD&quot;
    &rbrace;,
    &quot;label&quot;: &quot;テスト用の 2 番目の割引コード&quot;,
    &quot;coupon&quot;: &lbrace;
    &quot;コード&quot;: &quot;z3r0c00l&quot;
    &rbrace;,
    &quot;applied_to&quot;: &quot;ITEM&quot;,
    &quot;type&quot;: null
    &rbrace;
     
     
     
     
     
     {}
     
     
&rbrack; 次の値を使用します
<u> 実際の結果 </u>:

仮想商品のみを含む買い物かごに対して、割引情報が *null* として返されます。

    &quot;&#39;
    &lbrace;
    &quot;data&quot;: &lbrace;
    &quot;estimateTotals&quot;: &lbrace;
    &quot;cart&quot;: &lbrace;
    &quot;prices&quot;: &lbrace;
    &quot;discounts&quot;: null
    &rbrace;
    &rbrace;
    &rbrace;
    &rbrace;,
    &quot;extensions&quot;: {}
    &rbrace;
    &quot;&#39;

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
