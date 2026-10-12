---
title: 'MDVA-40601: GraphQLを介してスケジュールされた更新によって変更されたカテゴリに関するデータを取得できない'
description: MDVA-40601 Adobe Commerce品質パッチは、GraphQLを通じて予定された更新によって変更されたカテゴリに関する情報を取得する際にエラーが発生する問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.3がインストールされている場合に利用できます。 パッチ IDはMDVA-40601です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。
feature: Categories, GraphQL
role: Admin
exl-id: c50e9f77-66eb-4c4c-b0b5-b77db84a4a0b
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%
---
# MDVA-40601: GraphQLを介してスケジュールされた更新によって変更されたカテゴリに関するデータを取得できない

MDVA-40601 Adobe Commerce品質パッチは、GraphQLを通じて予定された更新によって変更されたカテゴリに関する情報を取得する際にエラーが発生する問題を修正します。 このパッチは、[品質パッチツール （QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.3がインストールされている場合に使用できます。 パッチ IDはMDVA-40601です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.3.3および2.4.2

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.3.1 - 2.4.2-p2

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

GraphQLを介してスケジュールされた更新によって変更されたカテゴリに関する情報を取得しようとすると、エラーが発生します。

<u>複製する手順</u>:

1. 次に示すように、サブカテゴリを持つカテゴリ構造を設定します。

   <pre>
   <code class="language-graphql">
   - Root
    - Some category
         - Some child category
   </code>
   </pre>

1. 「一部のカテゴリ」 ID 49でGraphQL クエリを実行します。

   <pre>
    <code class="language-graphql">
    query &lbrace;
     category(id: 49) &lbrace;
      name
      children &lbrace;
        name
       &rbrace;
     &rbrace;
   &rbrace;
   </code>
   </pre>

   施策：

   <pre>
    <code class="language-graphql">
    &lbrace;
      "data": &lbrace;
        "category": &lbrace;
          "name": "Some category",
          "children": &lbrack;
            &lbrace;
              "name": "Some child category"
            &rbrace;
          &rbrack;
        &rbrace;
      &rbrace;
    &rbrace;
    </code>
    </pre>

1. 別のカテゴリ名を持つ「一部のカテゴリ」のスケジュール更新を作成します。
1. スケジュール更新がアクティブ化されるのを待ちます。
1. 上記と同じクエリを実行します。

<u>期待される結果</u>:

同じ結果が表示されますが、更新されたカテゴリ名が表示されます。

<u>実際の結果</u>:

次のエラーが表示されます。

<pre>
<code class="language-graphql">
&lbrace;
  "errors": &lbrack;
    &lbrace;
      "debugMessage": "uasort() expects parameter 1 to be array, string given",
      "message": "Internal server error",
      "extensions": &lbrace;
        "category": "internal"
      &rbrace;,
      "locations": &lbrack;
        &lbrace;
          "line": 2,
          "column": 3
        &rbrace;
      &rbrack;,
      "path": &lbrack;
        "category"
      &rbrack;
    &rbrace;
  &rbrack;,
  "data": &lbrace;
    "category": null
  &rbrace;
&rbrace;
</code>
</pre>

## パッチを適用する

個別のパッチを適用するには、デプロイメントタイプに応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

Adobe Commerceの高品質なパッチについて詳しくは、次を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、「QPT[&#128279;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で使用可能な パッチ」セクションを参照してください。
