---
title: 'ACSD-53309: カスタマイズ可能なオプションと[!UICONTROL Regular Price] ラベルに対する税アプリケーションが不完全です'
description: カスタマイズ可能なオプションが選択されているときに'[!UICONTROL Regular Price]' ラベルに税金が完全に適用されないAdobe Commerceの問題を修正するには、ACSD-53309 パッチを適用します。
feature: Taxes, Shipping/Delivery
role: Admin, Developer
exl-id: 7f4a8923-11dd-48b2-9d97-77de5c2b24ce
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 20%

---

# ACSD-53309: カスタマイズ可能なオプションと&#39;[!UICONTROL Regular Price]&#39; ラベルの税アプリケーションが不完全です

ACSD-53309 パッチは、カスタマイズ可能なオプションが選択されているときに、&#39;[!UICONTROL Regular Price]&#39; ラベルに税金が完全に適用されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.43がインストールされている場合に利用できます。 パッチ IDはACSD-53309です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

カスタマイズ可能なオプションが選択されている場合、税金が&#39;[!UICONTROL Regular Price]&#39; ラベルに完全に反映されません。

<u>複製する手順</u>:

1. Admin パネルにログインします。
1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Tax]**&#x200B;に移動して、税設定を構成します。

   * [!UICONTROL Tax Classes]:

     * [!UICONTROL Tax Class for Shipping] = [!UICONTROL Taxable Goods]
     * [!UICONTROL Tax Class for Gift Options] = [!UICONTROL Taxable Goods]

   * [!UICONTROL Calculation Settings]:

     * [!UICONTROL Catalog Prices] = [!UICONTROL Including Tax]
     * [!UICONTROL Shipping Prices] = [!UICONTROL Including Tax]
     * [!UICONTROL Apply Discount On Prices] = [!UICONTROL Including Tax]

   * [!UICONTROL Default Tax Destination Calculation]:

     * [!UICONTROL Default Post Code] = *

   * [!UICONTROL Price Display Settings]:

     * [!UICONTROL Display Product Prices In Catalog] = [!UICONTROL Including Tax]
     * [!UICONTROL Display Shipping Prices] = [!UICONTROL Including Tax]

   * [!UICONTROL Shopping Cart Display Settings]:

     * [!UICONTROL Display Prices] = [!UICONTROL Including Tax]
     * [!UICONTROL Display Subtotal] = [!UICONTROL Including Tax]
     * [!UICONTROL Display Shipping Amount] = [!UICONTROL Including Tax]

1. **[!UICONTROL Shipping Settings]** > **[!UICONTROL Origin]** > **[!UICONTROL Country]** = *United Kingdom*&#x200B;に設定します。

1. 次の&#x200B;*[!UICONTROL Tax Rate]*&#x200B;と&#x200B;*[!UICONTROL Tax Rules]*&#x200B;を作成します。

   * [!UICONTROL Country] =米国
   * [!UICONTROL Zip Code] = *
   * [!UICONTROL State] = *
   * [!UICONTROL Rate] = 20%
1. シンプルな製品を作成し、以下を設定します。
   * [!UICONTROL Price = 110]
   * [!UICONTROL Special Price = 100]
   * ドロップダウンで、「type」を「custom」オプションに設定し、価格を「15%」に設定します
1. ストアフロントで作成したシンプルなアイテムについては、製品ページを参照してください。
1. 作成したカスタムオプション *15%*&#x200B;を選択します。

<u>期待される結果</u>:

* 選択したカスタムオプションに20%の税金が適用されます。
* &#39;[!UICONTROL Regular Price]&#39; = 151.80.

<u>実際の結果</u>:

* 選択したカスタムオプションには20%の税金が適用されません。
* &#39;[!UICONTROL Regular Price]&#39; = 148.50.

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
