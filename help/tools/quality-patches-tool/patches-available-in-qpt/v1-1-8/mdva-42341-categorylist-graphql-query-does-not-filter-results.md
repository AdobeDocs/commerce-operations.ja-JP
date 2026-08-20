---
title: 'MDVA-42341: "categoryList" GraphQL クエリで結果がフィルタリングされない'
description: MDVA-42341 パッチは、リクエストにStore ヘッダーがある場合、「categoryList」GraphQL クエリが結果をフィルタリングしない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.8がインストールされている場合に利用できます。 パッチ IDはMDVA-42341です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。
feature: GraphQL, Categories
role: Admin
exl-id: 56b81385-6db0-4e62-8e2b-bccfc9e0a581
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-42341: &quot;categoryList&quot; GraphQL クエリで結果がフィルタリングされない

MDVA-42341 パッチは、リクエストにStore ヘッダーがある場合、「categoryList」GraphQL クエリが結果をフィルタリングしない問題を解決します。 このパッチは、[品質パッチツール （QPT） ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.8がインストールされている場合に使用できます。 パッチ IDはMDVA-42341です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

「categoryList」GraphQL クエリは、リクエストにStore ヘッダーがある場合、結果をフィルタリングしません。

<u>複製する手順</u>:

1. 新しいルート カテゴリを作成し、**root2**&#x200B;という名前を付けます。
1. 2つ目のWeb サイト/ストア/ストアレビューを作成し、新しいストアに&#x200B;**root2**&#x200B;を割り当てます。
1. デフォルトのルートカテゴリ = category1の下に新しいカテゴリを作成します。
1. GraphQL リクエストを使用して、2番目のweb サイトのカテゴリリストを取得します（Header store = newを使用）。

<pre>
<code class="language-graphql">
{
  categoryList(filters: {name: {match: "category1"}}) {
    uid
    level
    name
    breadcrumbs {
      category_uid
      category_name
      category_level
      category_url_key
    }
  }
}
</code>
</pre>

<u>期待される結果</u>:

デフォルトのルートカテゴリのカテゴリは、「新しい」ストアヘッダーを使用しているため、応答にリストされません。

<u>実際の結果</u>:

デフォルトのルートカテゴリのカテゴリは、結果で使用できます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
