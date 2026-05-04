---
title: 'ACSD-55100: [!DNL GraphQL] が検索結果で10,000件を超える商品を返さない'
description: ACSD-55100 パッチを適用して、GraphQLが検索結果で*10k*を超える商品を返さないAdobe Commerceの問題を修正します。
feature: GraphQL, Products, Search
role: Admin, Developer
exl-id: f08b62b9-ed56-4eca-b7e7-6e2bd99df01f
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%

---

# ACSD-55100: [!DNL GraphQL]が検索結果で10,000件を超える商品を返さない

>[!NOTE]
>
>バージョン 2.4.6 ～ 2.4.6-p8で同じ問題を解決するために、更新されたパッチ （[ACSD-62332](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-62332-product-listing-graphql-query-limit-plus-live-search-current-page.md)）がリリースされました。 詳しくは、[ACSD-62332](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-62332-product-listing-graphql-query-limit-plus-live-search-current-page.md)を参照してください。

ACSD-55100 パッチは、[!DNL GraphQL]が検索結果で&#x200B;*10 k*&#x200B;を超える製品を返さない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.46がインストールされている場合に利用できます。 パッチ IDはACSD-55100です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

[!DNL GraphQL]は、検索結果で&#x200B;*10,000*&#x200B;を超える商品を返しません。

<u>前提条件</u>:

**[!DNL OpenSearch]**&#x200B;の場合は、使用可能な最新バージョンを使用していることを確認してください。

報告された問題を解決するには、**[!DNL OpenSearch]** 2.5.0以降に利用可能で、`opensearch-project/opensearch-php` パッケージのバージョン 2.2が必要な特定時点の機能が導入されます。

ただし、バージョン 2.0.1より小さい必要がある`opensearch-project/opensearch-php` パッケージへの依存関係を指定する`magento/magento-cloud-metapackage`との競合があります。


この依存関係は、[opensearch-project/opensearch-php] パッケージを最新バージョン 2.2に更新することを防ぎます。

その結果、次のエラーが発生し、*10,000*&#x200B;を超える製品に対してnull結果が返されます。

`Namespace [createPointInTime] not found in /vendor/opensearch-project/opensearch-php/src/OpenSearch/Client.php:135`

既存の依存関係により、`composer.json` ファイルにバージョンを直接追加し、`opensearch-project/opensearch-php` パッケージをバージョン 2.2に更新することが困難になっています。

この問題を解決するには、メインの`composer.json` ファイルのrequire ブロックの下に次の行を含めます。 その後、再デプロイして、問題のあるパッケージを最新バージョンに更新します。

`"opensearch-project/opensearch-php": "2.2.0 as 2.0.0",`

<u>複製する手順</u>:

1. *15k*&#x200B;個の商品を含むカタログを生成します。
1. [!DNL GraphQL]を送信：

```graphql
    query {
    products(
    filter: {
    # category_id:{eq:""}
    }
    , pageSize: 5, currentPage: 1

    ) {
    total_count
    page_info {
    current_page
    page_size
    total_pages
     }

     aggregations {

    attribute_code
    count
    label
    options {
    label
    value

    }
    }

    items {
    uid
    sku
    is_for_clearance
    categories {
    name
    breadcrumbs {
    category_name
    category_uid
    }
    display_mode
    description
    }
    }
    }
    }
```

<u>期待される結果</u>:

Total_count = *15k*
すべての製品を表示できるはずです。

<u>実際の結果</u>:

Total_count = *10k*
*10,000* バッチの後に表示する商品を取得できません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
