---
title: MDVA-38447：設定可能な子プロダクトがGraphQLのレスポンスで返され、MySQL クエリが遅くなる
description: MDVA-38447 Adobe Commerce パッチでは、GraphQLのレスポンスで設定可能な子製品が「個別に表示されない」と返され、カテゴリーフィルターを使用したGraphQL製品クエリのMySQL クエリが遅くなる問題が修正されました。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.2がインストールされている場合に利用できます。 パッチ IDはMDVA-38447です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。
feature: B2B, GraphQL, Categories, Configuration, Products, Services
role: Admin
exl-id: d97297c5-e8e8-407b-b43b-033937426fe2
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 1%
---
# MDVA-38447：設定可能な子プロダクトがGraphQLのレスポンスで返され、MySQL クエリが遅くなる

MDVA-38447 Adobe Commerce パッチでは、GraphQLのレスポンスで設定可能な子製品が「個別に表示されない」と返され、カテゴリーフィルターを使用したGraphQL製品クエリのMySQL クエリが遅くなる問題が修正されました。 このパッチは、[品質パッチツール （QPT） ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.2がインストールされている場合に使用できます。 パッチ IDはMDVA-38447です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.3

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

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
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

Adobe Commerceの高品質なパッチについて詳しくは、次を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、「QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で使用可能な[ パッチ」セクションを参照してください。
