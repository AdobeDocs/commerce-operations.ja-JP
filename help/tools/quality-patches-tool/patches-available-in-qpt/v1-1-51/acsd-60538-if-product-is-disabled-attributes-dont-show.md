---
title: ACSD-60538：製品が [!UICONTROL All Store Views] で無効になっている場合、属性が正しく表示されない
description: ACSD-60538 パッチを適用すると、Adobe Commerceの問題が修正されます。この問題では、商品が*すべてのストアビュー*で無効になっており、特定のストアビュースコープでのみ有効になっている場合、GraphQL レスポンスで商品の属性が正しく表示されず、商品が正しく表示されません。
feature: Attributes, GraphQL
role: Admin, Developer
exl-id: 2ea9de11-b750-4ab6-9cc7-e940e1791f22
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# ACSD-60538：製品が *[!UICONTROL All Store Views]* で無効になっている場合、属性が正しく表示されない

ACSD-60538 パッチは、*[!UICONTROL All Store Views]* で商品が無効になり、特定のストアビュースコープでのみ有効になっている場合、GraphQL レスポンスで商品の属性が正しく表示されず、商品が正しく表示されない問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.51 がインストールされている場合に使用できます。 パッチ ID は ACSD-60538 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p1

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.7 ～ 2.4.7-p2

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

商品が *[!UICONTROL All Store Views]* で無効になり、特定のストアビュー範囲でのみ有効になっている場合、GraphQLの応答で商品の属性が正しく表示されず、商品が正しく表示されません。

<u> 前提条件 </u>:

在庫モジュールがインストールされています。

<u> 再現手順 </u>:

1. *color* 属性と 3 つの子製品（*青*、*黒*、*茶色*）を持つ設定可能な製品を作成します。
1. *スコープで、関連付けられている 2 つの子製品（* 青 *および* 黒 *[!UICONTROL All Store Views]*）を無効にします。
1. スコープに移動 **[!UICONTROL Store View]** ます。
1. スコープで子製品（*青* および *黒*） *[!UICONTROL Store View]* 有効にします。
1. 以下のGraphQL リクエストを実行します。

   ```GraphQL
   {
     products(filter: { sku: { eq: "SKU" } }) {
       items {
           ... on ConfigurableProduct {
             configurable_options {
               attribute_id,
               attribute_code,
            values {
             value_index
             label
           }
       }
       variants {
         product {
           sku
         }
         attributes {
           label
           code
           value_index
          }
         }
        }
       }
      }
     }  
   ```

<u> 期待される結果 </u>:

GraphQLの応答には、関連付けられた子製品の属性値が含まれます。これらの製品は、*[!UICONTROL All Store Views]* で無効になり、*[!UICONTROL Store View]* スコープで有効になります。

<u> 実際の結果 </u>:

GraphQL応答では、商品が *[!UICONTROL All Store Views]* で無効になっており、*[!UICONTROL Store View]* スコープで有効になっている場合、関連付けられた子商品の属性値が空です。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
