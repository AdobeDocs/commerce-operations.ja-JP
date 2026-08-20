---
title: 'ACSD-50887: *[!UICONTROL Use in Search Results Layered Navigation]*は、*[!UICONTROL Use in Search]* オプションなしで「はい」に設定されています'
description: ACSD-50887 パッチを適用して、*[!UICONTROL Use in Search]* オプションも*Yes*に設定されずにproduct attribute プロパティ *[!UICONTROL Use in Search Results Layered Navigation]*を*Yes*に設定できるAdobe Commerceの問題を修正します。
feature: Attributes, Products, Search, Storefront
role: Admin, Developer
exl-id: 5e797121-c386-4aca-9139-0a02a60be38a
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# ACSD-50887: *[!UICONTROL Use in Search Results Layered Navigation]*&#x200B;が&#x200B;*[!UICONTROL Use in Search]* オプションなしで&#x200B;*Yes*&#x200B;に設定されました

ACSD-50887 パッチでは、*[!UICONTROL Use in Search]* オプションも&#x200B;*Yes*&#x200B;に設定されずに、製品属性プロパティ *[!UICONTROL Use in Search Results Layered Navigation]*&#x200B;を&#x200B;*Yes*&#x200B;に設定できる問題が修正されました。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.36がインストールされている場合に利用できます。 パッチ IDはACSD-50887です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

製品属性プロパティ *[!UICONTROL Use in Search Results Layered Navigation]*&#x200B;は、*[!UICONTROL Use in Search]* オプションも&#x200B;*Yes*&#x200B;に設定しなくても、*Yes*&#x200B;に設定できます。

これらの設定は一緒に使用するように設計されています。 パッチが適用された場合、*[!UICONTROL Use in Search]* オプションが&#x200B;*No*&#x200B;に設定されている場合、*[!UICONTROL Use in Search Results Layered Navigation]* オプションは非表示になり、*No*&#x200B;にも設定されているかのように動作します。

<u>複製する手順</u>:

1. 管理者で、**[!UICONTROL Stores]** > **[!UICONTROL Attribute]** > **[!UICONTROL Product]**&#x200B;に移動し、multiselect タイプを持つ属性を作成して、次を設定します。

   * *[!UICONTROL Use in Search]= No*
   * *[!UICONTROL Use in Layered Navigation]= （任意のオプション）*
   * *[!UICONTROL Use in Search Results Layered Navigation]=はい*
   * *名前= テスト属性*
   * *オプション*:
     * *ステッカー*
     * *ピッカー*

1. 新しい属性をデフォルトの属性セットに追加します。
1. 2つの製品を作成します。

   1. 最初の製品：
      * 名前= ステッカー
      * 価格、数量、重量を1に設定
      * Test_attribute = オプション *ステッカー*&#x200B;を選択

   1. 2つ目の製品：
      * 名前=ピッカー
      * 価格、数量、重量を1に設定
      * Test_attribute =両方のオプションを選択

1. `catalogsearch_fulltext`のインデックス再作成を実行：

   `bin/magento indexer:reindex catalogsearch_fulltext`

1. ストアフロントで「*sticker*」という単語で検索します。

<u>期待される結果</u>:

*[!UICONTROL Use in Search]*&#x200B;が&#x200B;*No*&#x200B;に設定されている場合、[!DNL Elasticsearch]はTest_attributeのインデックスを作成しないため、製品&#x200B;*ステッカー*&#x200B;のみが返されます。

<u>実際の結果</u>:

両方の製品が返品されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
