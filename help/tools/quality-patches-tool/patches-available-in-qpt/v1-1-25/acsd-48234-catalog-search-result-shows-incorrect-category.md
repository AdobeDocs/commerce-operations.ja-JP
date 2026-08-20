---
title: 'ACSD-48234: [!UICONTROL Display Out of Stock Products]が有効になっている場合、カタログの検索結果のカテゴリ項目数が正しくありません'
description: 「[!UICONTROL Display Out of Stock Products]」オプションが有効になっている場合に、カタログの検索結果に誤ったカテゴリ項目数が表示されるAdobe Commerceの問題を修正するには、ACSD-48234 パッチを適用します。
feature: Admin Workspace, Categories, Catalog Management, Orders, Products, Search
role: Admin
exl-id: c177f12d-2db5-48e2-8f88-ff589cea4dd4
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-48234: カタログの検索結果で、無効なカテゴリ項目数&#x200B;**[!UICONTROL Display Out of Stock Products]**&#x200B;が有効になっていることが表示される

ACSD-48234 パッチは、**[!UICONTROL Display Out of Stock Products]** オプションが有効になっている場合に、カタログの検索結果に誤ったカテゴリ項目数が表示される問題を解決します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.25がインストールされている場合に利用できます。 パッチ IDはACSD-48234です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。


## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました
* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 - 2.4.5-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

**[!UICONTROL Display Out of Stock Products]** オプションが有効になっている場合、カタログの検索結果に間違ったカテゴリ項目数が表示されます。

<u>複製する手順</u>:

1. **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**&#x200B;に移動し、**[!UICONTROL color]**&#x200B;属性を開きます。
1. 2つのオプション（オレンジや緑など）を追加します。 属性を保存します。
1. **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**&#x200B;に移動し、**[!UICONTROL color]**&#x200B;属性を&#x200B;**[!UICONTROL Default]**&#x200B;属性セットに追加します。
1. **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]**&#x200B;に移動し、**[!UICONTROL Display Out of Stock Products]**&#x200B;を&#x200B;_はい_&#x200B;に設定します。
1. カテゴリ「cat1」を作成します。
1. 2つの製品を作成します。
   1. 名前：prod1、色：オレンジ、カテゴリ：cat1。
   1. 名前：prod2、色：緑、カテゴリ：cat1。
1. ストアフロントでcat1 カテゴリを開きます。
1. レイヤーナビゲーションでオレンジ色を選択します。

<u>期待される結果</u>:

prod1製品のみが表示されます。

<u>実際の結果</u>:

prod1とprod2の両方の製品が表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
