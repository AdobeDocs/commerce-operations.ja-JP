---
title: 「MDVA-42341:「categoryList」GraphQL クエリで結果がフィルタリングされない」
description: MDVA-42341 パッチでは、リクエストに Store ヘッダーが含まれている場合に「categoryList」GraphQL クエリが結果をフィルタリングしない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches） 1.1.8 がインストールされている場合に利用できます。 パッチ ID は MDVA-42341。 この問題はAdobe Commerce 2.4.4 で修正される予定であることに注意してください。
feature: GraphQL, Categories
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# MDVA-42341:&quot;categoryList&quot; GraphQL クエリで結果がフィルターされない

MDVA-42341 パッチでは、リクエストに Store ヘッダーが含まれている場合に「categoryList」GraphQL クエリが結果をフィルタリングしない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)1.1.8 がインストールされている場合に使用できます。 パッチ ID は MDVA-42341。 この問題はAdobe Commerce 2.4.4 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

リクエストにストアヘッダーがある場合、「categoryList」GraphQL クエリで結果がフィルタリングされない。

<u> 再現手順 </u>:

1. 新しいルートカテゴリを作成して、**root2** という名前を付けます。
1. 2 つ目の Web サイト / ストア / ストレビューを作成し、**root2** を新しいストアに割り当てます。
1. 「デフォルトのルートカテゴリ = category1」の下に新しいカテゴリを作成します。
1. GraphQL リクエストを使用して、2 番目の web サイトのカテゴリリストを取得します（Header store = new を使用）。

<pre>
<code class="language-graphql">
&lbrace;
  categoryList(filters: {name: {match: "category1"}}) &lbrace;
    uid
    level
    name
    breadcrumbs &lbrace;
      category_uid
      category_name
      category_level
      category_url_key
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

<u> 期待される結果 </u>:

「新規」ストアヘッダーを使用しているため、デフォルトのルートカテゴリのカテゴリは、応答に表示されません。

<u> 実際の結果 </u>:

デフォルトのルートカテゴリのカテゴリは、結果で使用できます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
