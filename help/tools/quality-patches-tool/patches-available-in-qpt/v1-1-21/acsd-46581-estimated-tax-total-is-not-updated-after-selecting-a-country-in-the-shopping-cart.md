---
title: 'ACSD-46581: ショッピングカートで国を選択した後、推定税額が更新されない'
description: ACSD-46581 パッチを適用して、ショッピングカート内の国を切り替えた後に税率が更新されないAdobe Commerceの問題を解決します。
feature: Orders, Shopping Cart
role: Admin
exl-id: 45800055-8556-4f87-8938-c6be5d82938d
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# ACSD-46581: ショッピングカートで国を選択した後、推定税額が更新されない

このACSD-46581 パッチは、ショッピングカート内の国を切り替えた後に税率が更新されない問題を解決します。 出荷方法を選択した後にのみ更新されます。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.21がインストールされている場合に利用できます。 パッチ IDはACSD-46581です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました
* Adobe Commerce（すべてのデプロイメント方法） 2.4.1-p1

**Adobe Commerceのバージョンとの互換性：**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 - 2.4.5

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ショッピングカート内の国を切り替えた後、税率は更新されません。

<u>複製する手順</u>:

1. Adobe Commerce Adminで、**[!UICONTROL Stores]** > **[!UICONTROL Tax Zone and Rates]**&#x200B;に移動します。
1. **[!UICONTROL Country]** = _米国_、**[!UICONTROL State]** = _*_、**[!UICONTROL Rate]** = _8.25_&#x200B;の新しい税率を作成します。
1. **[!UICONTROL Country]** = _インド_、**[!UICONTROL State]** = _*_、**[!UICONTROL Rate]** = _10_&#x200B;の新しい税率を作成します。
1. 米国とインドの両方の税率を使用する税ルールを作成します。
1. **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Shipping Methods]**&#x200B;に移動し、複数の配送方法（_定額料金_&#x200B;と&#x200B;_送料無料_&#x200B;など）を有効にします。
1. **[!UICONTROL Taxable Goods]**&#x200B;税区分を使用して簡単な製品を作成します。
1. ストアのフロントのカートに商品を追加します。
1. 買い物かごを開いて税額を確認します。
1. 米国のデフォルトの税金設定が適用され、8.25%の税率に基づいて税金が計算されます。
1. 国をインドに切り替える。

<u>期待される結果</u>:

インドに切り替えると税額が10%に変わりました。

<u>実際の結果</u>:

税額は、ショッピングカートの合計セクションで同じままです。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
