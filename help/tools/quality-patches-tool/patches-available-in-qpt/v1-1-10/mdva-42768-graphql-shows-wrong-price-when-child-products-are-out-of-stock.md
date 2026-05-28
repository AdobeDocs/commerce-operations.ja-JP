---
title: MDVA-42768：子商品の在庫切れでGraphQLが誤った価格を表示する
description: MDVA-42768 パッチでは、子商品の設定可能な商品が在庫切れになった場合に、GraphQLで誤った価格が表示される問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.10がインストールされている場合に利用できます。 パッチ IDはMDVA-42768です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。
feature: GraphQL, Orders, Products
role: Admin
exl-id: 9f6ab418-2267-4548-952a-17dc8295f632
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 0%

---

# MDVA-42768：子商品の在庫切れでGraphQLが誤った価格を表示する

MDVA-42768 パッチでは、子商品の設定可能な商品が在庫切れになった場合に、GraphQLで誤った価格が表示される問題を修正します。 このパッチは、[品質パッチツール（QPT） ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10がインストールされている場合に使用できます。 パッチ IDはMDVA-42768です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.4 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

設定可能な商品の子商品が在庫切れになっていて、「在庫切れ商品を表示」設定が有効になっている場合、GraphQL クエリは商品の通常価格を&#x200B;**0**&#x200B;と表示します。

<u>前提条件</u>:

サンプルデータがインストールされます。

<u>複製する手順</u>:

1. Commerce管理者で「**Stores** > **Configuration** > **Catalog** > **Inventory**」に移動して、「在庫切れ商品を表示」設定を有効にします。
1. 設定可能な製品を作成し、シンプルな子製品を割り当てます。
1. バリエーション （シンプル）商品の在庫を&#x200B;**在庫切れ**&#x200B;に設定します。
1. 再インデックス：
1. 次のGraphQL クエリを実行します。

   ```GraphQL
   query {
     products(filter: { sku: { eq: "MH01" } }) {
       items {
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
           maximum_price {
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

1. 応答セクション `minimum_price` > `regular price`を確認してください。

<u>期待される結果</u>:

通常の最低価格は、応答として0として表示されません。

<u>実際の結果</u>:

通常の最低価格= 0です。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
