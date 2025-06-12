---
title: 'ACSD-57394: [!DNL GraphQL] の複数の並べ替え属性による製品の並べ替えが正しくありません'
description: ' [!DNL GraphQL] で複数の並べ替え属性を使用した場合に、商品が正しく並べ替えられないAdobe Commerceの問題を修正するために、ACSD-57394 パッチを適用してください。'
feature: GraphQL, Products
role: Admin, Developer
exl-id: 3e4ca535-37ed-4363-ba6c-968eb53b98b3
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-57394:[!DNL GraphQL] の複数の並べ替え属性による製品の並べ替えが正しくありません

ACSD-57394 パッチは、[!DNL GraphQL] で複数の並べ替え属性を使用した場合に、製品が正しく並べ替えられない問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.48 がインストールされている場合に使用できます。 パッチ ID は ACSD-57394 です。 この問題はAdobe Commerce 2.5.0 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p4

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

[!DNL GraphQL] で複数の並べ替え属性を使用すると、製品が誤って並べ替えられます。

<u> 再現手順 </u>:

1. 価格と名前が異なる製品をいくつか作成します。
1. カテゴリを作成し、作成した製品を割り当てます。
1. いくつかの *並べ替え* 属性を含む、作成されたカテゴリの [!DNL GraphQL] しい製品クエリを送信します。 例：

   ```
   {
   products(
     currentPage: 1
     pageSize: 10
     filter: {
       category_id: {
         eq :"3"
       }
     }
     sort: {  price: DESC, name: ASC, position: ASC
     }
   ){
   items{
     name
     sku
   
       price_range {
           minimum_price {
   
         regular_price {
           value
           currency
         }
         final_price {
           value
           currency
         }
         discount {
           amount_off
           percent_off
         }
               }
           }
      }
     }
    }
   ```

1. *sort* 属性を作成した後、応答を確認します。

<u> 期待される結果 </u>:

商品は正しい順序で返されます。 製品を複数の属性で並べ替えても機能します。

<u> 実際の結果 </u>:

商品が正しい順序で返されません。 製品を複数の属性で並べ替えても機能しません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
