---
title: 'MDVA-39935: GraphQLは、web サイトレベルで無効になっている設定可能な子商品を返します'''
description: MDVA-39935 Adobe Commerce パッチは、GraphQLがweb サイトレベルで無効な設定可能な子製品を返す問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.2がインストールされている場合に利用できます。 パッチ IDはMDVA-39935です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。
feature: GraphQL, Configuration, Products
role: Admin
exl-id: b86b1595-ddd5-41ce-b126-287046462561
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# MDVA-39935:GraphQLが、web サイトレベルで無効になっている設定可能な子商品を返す

MDVA-39935 Adobe Commerce パッチは、GraphQLがweb サイトレベルで無効な設定可能な子製品を返す問題を修正します。 このパッチは、[品質パッチツール （QPT） ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2がインストールされている場合に使用できます。 パッチ IDはMDVA-39935です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p1

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.1 - 2.4.3

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

GraphQLは、web サイトレベルで無効にした後でも、設定可能な子商品を返します。

<u>複製する手順</u>:

1. **ストア** > **設定** > **カタログ** > **在庫** > **在庫オプション** > **在庫切れ商品の表示** > **はい**&#x200B;の下で、在庫切れ商品の表示オプションを有効にします。
1. 2つ以上の&#x200B;**シンプル製品**&#x200B;を持つ&#x200B;**構成可能な製品**&#x200B;を選択します。
1. **シンプル製品**&#x200B;を無効にし、**構成可能な製品**&#x200B;を保存します。
1. GraphQLを使用して&#x200B;**Configurable Product** データを取得します。

<pre>
  <code class="language-graphql">
{
  products(filter: { sku: { eq: "cp1" } }) {
    items {
      __typename
      name
      sku
      ... on ConfigurableProduct {
        variants {
          product {
            __typename
            name
            sku
            color
            stock_status
          }
        }
      }
    }
  }
}
</code>
</pre>

<u>期待される結果</u>:

バリアントの結果には、無効な製品は表示されません。

<u>実際の結果</u>:

バリアントの結果で、無効な製品データが取得されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメントタイプに応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

Adobe Commerceの高品質なパッチについて詳しくは、次を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、「QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で使用可能な[ パッチ」セクションを参照してください。
