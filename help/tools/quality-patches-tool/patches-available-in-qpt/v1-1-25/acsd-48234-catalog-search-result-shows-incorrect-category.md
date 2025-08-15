---
title: ACSD-48234:[!UICONTROL Display Out of Stock Products] が有効な場合に、カタログ検索結果のカテゴリ項目数が正しくない
description: '[!UICONTROL Display Out of Stock Products] オプションが有効な場合に、カタログ検索結果に誤ったカテゴリ項目数が表示されるAdobe Commerceの問題を修正するために、ACSD-48234 パッチを適用してください。'
feature: Admin Workspace, Categories, Catalog Management, Orders, Products, Search
role: Admin
exl-id: c177f12d-2db5-48e2-8f88-ff589cea4dd4
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-48234：有効になっているカタログ検索結果に、誤ったカテゴリ項目数 **[!UICONTROL Display Out of Stock Products]** 表示される

ACSD-48234 パッチは、**[!UICONTROL Display Out of Stock Products]** オプションが有効な場合に、カタログ検索結果に誤ったカテゴリ項目数が表示される問題を解決します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25 がインストールされている場合に使用できます。 パッチ ID は ACSD-48234 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。


## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerce バージョンとの互換性：**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 ～ 2.4.5-p4

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

「**[!UICONTROL Display Out of Stock Products]**」オプションが有効な場合、カタログ検索結果に誤ったカテゴリ項目数が表示される。

<u> 再現手順 </u>:

1. **[!UICONTROL Stores]**/**[!UICONTROL Attributes]**/**[!UICONTROL Product]** に移動し、属性 **[!UICONTROL color]** 開きます。
1. オレンジと緑など、2 つのオプションを追加します。 属性を保存します。
1. **[!UICONTROL Stores]**/**[!UICONTROL Attributes]**/**[!UICONTROL Attribute Set]** に移動し、**[!UICONTROL color]** 属性を **[!UICONTROL Default]** 属性セットに追加します。
1. **[!UICONTROL Stores]**/**[!UICONTROL Settings]**/**[!UICONTROL Configuration]**/**[!UICONTROL CATALOG]**/**[!UICONTROL Inventory]**/**[!UICONTROL Stock Options]** に移動し、「**[!UICONTROL Display Out of Stock Products]**」を「_はい_」に設定します。
1. カテゴリ「cat1」を作成します。
1. 2 つの製品を作成します。
   1. 名前：prod1、色：オレンジ、カテゴリ：cat1。
   1. 名前：prod2、色：緑、カテゴリ：cat1。
1. ストアフロントの cat1 カテゴリを開きます。
1. レイヤ ナビゲーションでオレンジ色を選択します。

<u> 期待される結果 </u>:

prod1 製品のみが表示されます。

<u> 実際の結果 </u>:

prod1 製品と prod2 製品の両方が表示されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
