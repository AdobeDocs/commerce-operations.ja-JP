---
title: 'ACSD-45817: GraphQL製品の変異により、設定可能なすべてのバリエーションが与えられます'
description: ACSD-45817 パッチでは、特定のストアのGraphQL「製品」のミューテーションが、リクエストされたストアに割り当てられていないものを含む、設定可能なすべてのバリエーションを返す問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.18がインストールされている場合に利用できます。 パッチ IDはACSD-45817です。 この問題はAdobe Commerce 2.4.4で修正されています。
feature: GraphQL, Configuration, Products
role: Admin
exl-id: f00e9a8e-c18b-4fa8-b7c6-c228b6a22a2c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---

# ACSD-45817: GraphQL製品の変異により、設定可能なすべてのバリエーションが与えられます

ACSD-45817 パッチは、特定のストアのGraphQL `products`のミューテーションが、リクエストされたストアに割り当てられていないものも含め、設定可能なすべてのバリエーションを返す問題を修正します。 このパッチは、[品質パッチツール（QPT） ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18がインストールされている場合に使用できます。 パッチ IDはACSD-45817です。 この問題はAdobe Commerce 2.4.4で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.3-p3

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

特定のストアに対するGraphQL `products`のミューテーションは、リクエストされたストアに割り当てられていないものも含め、設定可能なすべてのバリエーションを返します。

<u>前提条件</u>:

2番目のweb サイト、2番目のストア、2番目のストアビューを作成します。

<u>複製する手順</u>:

1. 「configurable-a」と「configurable-b」の2つのサブプロダクトを持つコンフィグ可能な製品を作成します。
1. 両方のweb サイトに設定可能な製品を割り当てます。
1. 2番目のweb サイトに「configurable-a」バリエーションを1つだけ割り当てます。
1. **ストアフロント**&#x200B;に移動し、2番目のweb サイトに切り替えて、設定可能な製品を開きます。
1. 「configurable-a」という子オプションが1つだけ表示されていることを確認します。
1. `POST: /graphql` エンドポイントと`Headers: "store" = "new"`を使用してGraphQL クエリを実行します

   ```GraphQL
   {
     products(filter: { sku: { eq: "configurable" } }) {
       items {
         id
         attribute_set_id
         name
         sku
         __typename
         price_range{
           minimum_price{
             regular_price{
               value
               currency
             }
           }
         }
         categories {
           id
         }
         ... on ConfigurableProduct {
           configurable_options {
             id
             attribute_id_v2
             label
             position
             use_default
             attribute_code
             values {
               value_index
               label
             }
             product_id
           }
           variants {
             product {
               id
               name
               sku
               attribute_set_id
               ... on PhysicalProductInterface {
                 weight
               }
               price_range{
                 minimum_price{
                   regular_price{
                     value
                     currency
                   }
                 }
               }
             }
             attributes {
               uid
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

<u>期待される結果</u>:

「configurable-b」バリエーションは、2番目のweb サイトに割り当てられていないため、応答に表示しないでください。

<u>実際の結果</u>:

応答に「configurable-b」バリエーションが表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
