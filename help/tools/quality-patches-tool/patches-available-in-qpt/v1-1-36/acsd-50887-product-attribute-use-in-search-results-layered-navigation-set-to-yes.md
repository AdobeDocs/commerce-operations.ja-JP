---
title: 'ACSD-50887: *[!UICONTROL Use in Search Results Layered Navigation]* オプションを指定せずに*[!UICONTROL Use in Search]*を [ はい ] に設定'
description: ACSD-50887 パッチを適用すると、Adobe Commerceの問題が修正されます。この問題では、*[!UICONTROL Use in Search]* オプションも*Yes*に設定されていない場合に、product 属性プロパティ*[!UICONTROL Use in Search Results Layered Navigation]*を*Yes*に設定できます。
feature: Attributes, Products, Search, Storefront
role: Admin, Developer
exl-id: 5e797121-c386-4aca-9139-0a02a60be38a
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-50887:*[!UICONTROL Use in Search]* オプションを指定せずに *[!UICONTROL Use in Search Results Layered Navigation]* を *はい* に設定する

ACSD-50887 パッチでは、*[!UICONTROL Use in Search]* オプションも *Yes* に設定されていない状態で、product 属性プロパティの *[!UICONTROL Use in Search Results Layered Navigation]* が *Yes* に設定される問題が修正されています。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.36 がインストールされている場合に使用できます。 パッチ ID は ACSD-50887 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 ～ 2.4.6-p2

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

製品属性プロパティ *[!UICONTROL Use in Search Results Layered Navigation]* は *はい* に設定できます。*[!UICONTROL Use in Search]* オプションも *はい* に設定する必要はありません。

これらの設定は、一緒に使用するように設計されています。 パッチを適用した状態で *[!UICONTROL Use in Search]* オプションを *いいえ* に設定すると、*[!UICONTROL Use in Search Results Layered Navigation]* オプションも *いいえ* に設定されているかのように機能します。

<u> 再現手順 </u>:

1. 管理者で、**[!UICONTROL Stores]** / **[!UICONTROL Attribute]** / **[!UICONTROL Product]** に移動し、複数選択タイプの属性を作成して、以下を設定します。

   * *[!UICONTROL Use in Search]= No*
   * *[!UICONTROL Use in Layered Navigation]= （任意のオプション）*
   * *[!UICONTROL Use in Search Results Layered Navigation]=はい*
   * *Name = Test_attribute*
   * *オプション*:
      * *ステッカー*
      * *ピッカー*

1. 新しい属性をデフォルトの属性セットに追加します。
1. 2 つの製品を作成します。

   1. 最初の製品：
      * 名前= ステッカー
      * 価格、数量、重量を 1 に設定
      * Test_attribute = select option *ステッカー*

   1. 2 番目の製品：
      * 名前= ピッカー
      * 価格、数量、重量を 1 に設定
      * Test_attribute =両方のオプションを選択します

1. 再インデックス `catalogsearch_fulltext` 実行します。

   `bin/magento indexer:reindex catalogsearch_fulltext`

1. 店頭で *ステッカー* という言葉で検索します。

<u> 期待される結果 </u>:

製品 *Sticker* のみが返されます。これは、*[!UICONTROL Use in Search]* が *No* に設定されている場合、[!DNL Elasticsearch] が Test_attribute のインデックスを作成しないためです。

<u> 実際の結果 </u>:

両方の製品が返されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
