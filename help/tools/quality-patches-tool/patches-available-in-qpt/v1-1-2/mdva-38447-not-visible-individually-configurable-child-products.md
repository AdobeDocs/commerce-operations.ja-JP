---
title: MDVA-38447：設定可能な子商品がGraphQL応答で返され、MySQL クエリが遅い
description: MDVA-38447 Adobe Commerce パッチでは、「Not visible individually （個別に表示されない）」設定可能な子商品がGraphQL レスポンスで返され、カテゴリフィルターを使用したGraphQL商品クエリで MySQL の処理に時間がかかる問題を修正しました。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.2 がインストールされている場合に利用できます。 パッチ ID は MDVA-38447。 この問題はAdobe Commerce 2.4.4 で修正される予定であることに注意してください。
feature: B2B, GraphQL, Categories, Configuration, Products, Services
role: Admin
exl-id: d97297c5-e8e8-407b-b43b-033937426fe2
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# MDVA-38447：設定可能な子商品がGraphQL応答で返され、MySQL クエリが遅い

MDVA-38447 Adobe Commerce パッチでは、「Not visible individually （個別に表示されない）」設定可能な子商品がGraphQL レスポンスで返され、カテゴリフィルターを使用したGraphQL商品クエリで MySQL の処理に時間がかかる問題を修正しました。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.2 がインストールされている場合に使用できます。 パッチ ID は MDVA-38447。 この問題はAdobe Commerce 2.4.4 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 ～ 2.4.3

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

「個別に表示されない」設定可能な子商品がGraphQL応答で返され、カテゴリフィルターを使用したGraphQL商品クエリの低速な MySQL クエリが返されます。

<u> 前提条件 </u>:

B2B モジュールをインストールする必要があります。

<u> 再現手順 </u>:

1. シンプルな製品を「**個別には表示されない** に設定して、設定可能な製品を作成します。
1. **full reindex** を実行します。
1. 次のような **GraphQL クエリ** 実行します。

<pre>getfilteredProducts （
  $filter: ProductAttributeFilterInput!
  $sort: ProductAttributeSortInput!
  $search：文字列
  $pageSize: Int!
  $currentPage: Int!
） &lbrace;
  products （
    フィルター：$filter
    並べ替え：$sort
    検索：$search
    pageSize: $pageSize
    currentPage: $currentPage
  ） &lbrace;
    total_count
    page_info &lbrace;
      total_pages
      current_page
      page_size
    &rbrace;
    項目 &lbrace;
      名前
      sku
    &rbrace;
  &rbrace;
&rbrace;</pre>

変数：

<pre>{"filter":{"user_group":{"eq":"}},"search":"config-100","sort":{},"pageSize":200,"currentPage":1}
</pre>

<u> 期待される結果 </u>:

表示が「個別に表示されない」に設定されている製品は、応答では返されません。

<u> 実際の結果 </u>:

表示が「個別に表示されない」に設定されている製品が、応答で返されます。

## パッチの適用

個々のパッチを適用するには、デプロイメントタイプに応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

Adobe Commerce用の高品質パッチの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチについては、[QPT で使用可能なパッチ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) の節を参照してください。
