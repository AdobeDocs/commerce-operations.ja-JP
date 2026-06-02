---
title: MDVA-38447：設定可能な子プロダクトがGraphQLのレスポンスで返され、MySQL クエリが遅くなる
description: MDVA-38447 Adobe Commerce パッチでは、GraphQLのレスポンスで設定可能な子製品が「個別に表示されない」と返され、カテゴリーフィルターを使用したGraphQL製品クエリのMySQL クエリが遅くなる問題が修正されました。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.2がインストールされている場合に利用できます。 パッチ IDはMDVA-38447です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。
feature: B2B, GraphQL, Categories, Configuration, Products, Services
role: Admin
exl-id: d97297c5-e8e8-407b-b43b-033937426fe2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 0%

---

# MDVA-38447：設定可能な子プロダクトがGraphQLのレスポンスで返され、MySQL クエリが遅くなる

MDVA-38447 Adobe Commerce パッチでは、GraphQLのレスポンスで設定可能な子製品が「個別に表示されない」と返され、カテゴリーフィルターを使用したGraphQL製品クエリのMySQL クエリが遅くなる問題が修正されました。 このパッチは、[品質パッチツール （QPT） ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2がインストールされている場合に使用できます。 パッチ IDはMDVA-38447です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.3

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

「個別に表示されない」設定可能な子商品は、GraphQLのレスポンスで返され、カテゴリーフィルターを使用したGraphQL商品クエリのMySQL クエリが遅くなります。

<u>前提条件</u>:

B2B モジュールをインストールする必要があります。

<u>複製する手順</u>:

1. **個別に表示されない**&#x200B;に設定されたシンプルな製品を使用して、設定可能な製品を作成します。
1. **完全なインデックス**&#x200B;を実行します。
1. 次のように&#x200B;**GraphQL クエリ**&#x200B;を実行します。

<pre>クエリ getFilteredProducts （
  $filter: ProductAttributeFilterInput!
  $sort: ProductAttributeSortInput!
  $search：文字列
  $pageSize: Int!
  $currentPage: Int!
) {
  products （
    filter: $filter
    sort: $sort
    search: $search
    pageSize: $pageSize
    currentPage: $currentPage
  ) {
    total_count
    page_info {
      total_pages
      current_page
      page_size
    }
    items {
      name
      sku
    }
  }
}</pre>

変数：

<pre>{"filter":{"user_group":{"eq":"}},"search":"config-100","sort":{},"pageSize":200,"currentPage":1}
</pre>

<u>期待される結果</u>:

「個別に表示されない」に設定された表示がある製品は、応答として返されません。

<u>実際の結果</u>:

「個別に表示されない」に設定された表示レベルの製品は、応答として返されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメントタイプに応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

Adobe Commerceの高品質なパッチについて詳しくは、次を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、「QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で使用可能な[ パッチ」セクションを参照してください。
