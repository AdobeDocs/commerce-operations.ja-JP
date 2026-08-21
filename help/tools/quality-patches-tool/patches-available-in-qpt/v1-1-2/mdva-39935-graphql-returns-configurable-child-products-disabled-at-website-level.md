---
title: 'MDVA-39935: GraphQLは、web サイトレベルで無効になっている設定可能な子商品を返します'''
description: MDVA-39935 Adobe Commerce パッチは、GraphQLがweb サイトレベルで無効な設定可能な子製品を返す問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.2がインストールされている場合に利用できます。 パッチ IDはMDVA-39935です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。
feature: GraphQL, Configuration, Products
role: Admin
exl-id: b86b1595-ddd5-41ce-b126-287046462561
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# MDVA-39935:GraphQLが、web サイトレベルで無効になっている設定可能な子商品を返す

MDVA-39935 Adobe Commerce パッチは、GraphQLがweb サイトレベルで無効な設定可能な子製品を返す問題を修正します。 このパッチは、[品質パッチツール （QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.2がインストールされている場合に使用できます。 パッチ IDはMDVA-39935です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p1

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.1 - 2.4.3

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

GraphQLは、web サイトレベルで無効にした後でも、設定可能な子商品を返します。

<u>複製する手順</u>:

1. **ストア** > **設定** > **カタログ** > **在庫** > **在庫オプション** > **在庫切れ商品の表示** > **はい**&#x200B;の下で、在庫切れ商品の表示オプションを有効にします。
1. 2つ以上の&#x200B;**シンプル製品**&#x200B;を持つ&#x200B;**構成可能な製品**&#x200B;を選択します。
1. **シンプル製品**&#x200B;を無効にし、**構成可能な製品**&#x200B;を保存します。
1. GraphQLを使用して&#x200B;**Configurable Product** データを取得します。

<pre>
  <code class="language-graphql">
&lbrace;
  products(filter: { sku: { eq: "cp1" } }) &lbrace;
    items &lbrace;
      __typename
      name
      sku
      ... on ConfigurableProduct &lbrace;
        variants &lbrace;
          product &lbrace;
            __typename
            name
            sku
            color
            stock_status
          &rbrace;
        &rbrace;
      &rbrace;
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

<u>期待される結果</u>:

バリアントの結果には、無効な製品は表示されません。

<u>実際の結果</u>:

バリアントの結果で、無効な製品データが取得されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメントタイプに応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

Adobe Commerceの高品質なパッチについて詳しくは、次を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、「QPT[&#128279;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で使用可能な パッチ」セクションを参照してください。
