---
title: 'MDVA-40601: GraphQLを介してスケジュールされた更新によって変更されたカテゴリに関するデータを取得できない'
description: MDVA-40601 Adobe Commerce品質パッチは、GraphQLを通じて予定された更新によって変更されたカテゴリに関する情報を取得する際にエラーが発生する問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.3がインストールされている場合に利用できます。 パッチ IDはMDVA-40601です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。
feature: Categories, GraphQL
role: Admin
exl-id: c50e9f77-66eb-4c4c-b0b5-b77db84a4a0b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---

# MDVA-40601: GraphQLを介してスケジュールされた更新によって変更されたカテゴリに関するデータを取得できない

MDVA-40601 Adobe Commerce品質パッチは、GraphQLを通じて予定された更新によって変更されたカテゴリに関する情報を取得する際にエラーが発生する問題を修正します。 このパッチは、[品質パッチツール （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3がインストールされている場合に使用できます。 パッチ IDはMDVA-40601です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.3.3および2.4.2

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.3.1 - 2.4.2-p2

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

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
    query {
     category(id: 49) {
      name
      children {
        name
       }
     }
   }
   </code>
   </pre>

   施策：

   <pre>
    <code class="language-graphql">
    {
      "data": {
        "category": {
          "name": "Some category",
          "children": [
            {
              "name": "Some child category"
            }
          ]
        }
      }
    }
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
{
  "errors": [
    {
      "debugMessage": "uasort() expects parameter 1 to be array, string given",
      "message": "Internal server error",
      "extensions": {
        "category": "internal"
      },
      "locations": [
        {
          "line": 2,
          "column": 3
        }
      ],
      "path": [
        "category"
      ]
    }
  ],
  "data": {
    "category": null
  }
}
</code>
</pre>

## パッチを適用する

個別のパッチを適用するには、デプロイメントタイプに応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

Adobe Commerceの高品質なパッチについて詳しくは、次を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、「QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で使用可能な[ パッチ」セクションを参照してください。
