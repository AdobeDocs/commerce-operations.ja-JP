---
title: 'ACSD-54319: *[!UICONTROL Products in Carts]* レポートで製品価格がゼロになる'
description: ACSD-54319 パッチを適用して、*[!UICONTROL Products in Carts]* レポートで製品価格がゼロになるAdobe Commerceの問題を修正します
feature: Reporting, Products
role: Admin, Developer
exl-id: 10052d32-99f8-4b45-9fe9-a4c45bcaaa44
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-54319: *[!UICONTROL Products in Carts]* レポートで製品価格がゼロに表示される

ACSD-54319 パッチは、*[!UICONTROL Products in Carts]* レポートで製品価格がゼロになる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.40がインストールされている場合に利用できます。 パッチ IDはACSD-54319です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.5-p5

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

*[!UICONTROL Products in Carts]* レポートで製品価格がゼロと表示されます。

<u>複製する手順</u>:

1. **[!UICONTROL Catalog Price Scope]**&#x200B;を&#x200B;**[!UICONTROL Website]**&#x200B;に設定します（**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Price]** > **[!UICONTROL Catalog Price Scope]**）。
1. **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**&#x200B;から2番目のWeb サイトを作成します。
1. **[!UICONTROL Catalog]** > **[!UICONTROL Products]**&#x200B;から商品を作成します。
1. この製品を2番目のweb サイトにのみ割り当てます。
1. 2番目のweb サイトから商品をカートに追加します。
1. **[!UICONTROL Admin]** > **[!UICONTROL Reports]** > **[!UICONTROL Marketing]** > **[!UICONTROL Products In Carts]** グリッドに移動します。
1. *[!UICONTROL Products In Carts]* グリッドの&#x200B;*[!UICONTROL Price]*&#x200B;列を確認してください。

<u>期待される結果</u>:

*[!UICONTROL Products in Carts]* レポートグリッドで製品価格がゼロではありません。

<u>実際の結果</u>:

*[!UICONTROL Products in Carts]* レポートグリッドの製品価格がゼロです。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
