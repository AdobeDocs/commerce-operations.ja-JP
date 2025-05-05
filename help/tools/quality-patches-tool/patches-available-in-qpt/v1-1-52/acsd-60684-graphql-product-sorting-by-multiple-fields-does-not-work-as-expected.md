---
title: '「ACSD-60684: [!DNL GraphQL]  複数フィールドでの製品の並べ替えが期待どおりに動作しない」'
description: ACSD-60684 パッチを適用すると、変数で並べ替えを渡した場合に  [!DNL GraphQL]  複数フィールドで並べ替えが機能しないAdobe Commerceの問題を修正できます。
feature: GraphQL, Products, Search
role: Admin, Developer
source-git-commit: 279036e9e7247ce915820a4b00173644ee7252b1
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# ACSD-60684：複数のフィールド [!DNL GraphQL] よる製品の並べ替えが期待どおりに動作しない

ACSD-60684 パッチは、複数のフィールドで並べ替え [!DNL GraphQL] れた製品が、変数で並べ替えを渡した場合に機能しない問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.52 がインストールされている場合に使用できます。 パッチ ID は ACSD-60684 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p6

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

複数 [!DNL GraphQL] フィールドで製品を並べ替えても、期待どおりに動作しません。

<u> 再現手順 </u>:

1. A、B、C という名前の 3 つの製品を作成します。
1. 次の [!DNL GraphQL] を使用して、製品を取得します。

   ```
   query FindProducts($search: String, $filter:ProductAttributeFilterInput!, $pageSize: Int!, $currentPage: Int!, $sort: ProductAttributeSortInput!){
       products(search: $search, filter: $filter, pageSize: $pageSize, currentPage: $currentPage, sort: $sort){
           total_count
           page_info{total_pages}
           items{
               __typename
               url_key
               sku
               name
               stock_status
               price_range{
                   minimum_price{
                       final_price{
                           value
                           currency
                       }
                   }
               }
           }
       }
   } 
   ```

   変数：

   ```
   {
       "search": null,
       "filter": {
   
       },
       "pageSize": 24,
       "currentPage": 1,
       "sort": {
           "name": "ASC"
       }
   }  
   ```

1. `sort` : `DESC` を使用してクエリを繰り返します。

<u> 期待される結果 </u>:

結果は適切に並べ替えられます。

<u> 実際の結果 </u>:

選択されている並べ替えは適用されていません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
