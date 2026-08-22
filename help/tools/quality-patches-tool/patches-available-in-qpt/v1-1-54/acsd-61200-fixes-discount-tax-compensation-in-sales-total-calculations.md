---
title: ACSD-61200：売上合計の計算における割引税補償を修正します
description: ACSD-61200 パッチを適用して、*[!UICONTROL Discount Tax Compensation Amount]*と*[!UICONTROL Shipping Discount Tax Compensation Amount]*が売上合計の計算に含まれていないAdobe Commerceの問題を修正し、受注データとクーポンレポートデータの間に不一致が生じる問題を修正します。
feature: Reporting, Taxes
role: Admin, Developer
exl-id: eb908827-de29-4b2c-b094-b5db0931cd52
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 13%

---

# ACSD-61200：売上合計の計算における割引税補償を修正します

ACSD-61200 パッチでは、*[!UICONTROL Total Amount]*&#x200B;および&#x200B;*[!UICONTROL Total Amount Actual]*&#x200B;の計算で&#x200B;*[!UICONTROL Discount Tax Compensation Amount]*&#x200B;と&#x200B;*[!UICONTROL Shipping Discount Tax Compensation Amount]*&#x200B;が見つからない問題が修正され、販売注文データとクーポンレポートデータの間に不一致が生じます。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54がインストールされている場合に利用できます。 パッチ IDはACSD-61200です。 この問題は、Adobe Commerce バージョン 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

- Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerceのバージョンとの互換性：**

- Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

販売合計の計算に&#x200B;*[!UICONTROL Discount Tax Compensation Amount]*&#x200B;および&#x200B;*[!UICONTROL Shipping Discount Tax Compensation Amount]*&#x200B;が欠落しているため、販売注文およびクーポン レポート データの不正確さ。

<u>複製する手順</u>:

1. [!UICONTROL Tax Zone]と[!UICONTROL Tax Rule]を作成します。
1. 次の税金構成を設定します。
   - **[!UICONTROL Tax Class for Shipping]** = [!UICONTROL Taxable Goods]
   - **[!UICONTROL Catalog Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Shipping Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Apply Discount on Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Product Prices in Catalog]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Shipping Prices]** = [!UICONTROL Including Tax]
1. 注文、請求書、クレジットメモの次の表示設定を更新します。
   - **[!UICONTROL Display Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Subtotal]**= [!UICONTROL Including Tax]
   - **[!UICONTROL Display Shipping Amount]** = [!UICONTROL Including Tax]
1. クーポン付きの[!UICONTROL Cart Price Rule]を作成して10%割引を受けます。
1. クーポンを使用して注文を完了し、請求書と配送を生成します。
1. **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL Coupons]**&#x200B;に移動して、レポートを生成します。
1. 順序の概要のデータとレポートのデータを比較します。

<u>期待される結果</u>:

*[!UICONTROL Total Amount]*&#x200B;と&#x200B;*[!UICONTROL Total Amount Actual]*&#x200B;の計算には、*[!UICONTROL Discount Tax Compensation Amount]*&#x200B;と&#x200B;*[!UICONTROL Shipping Discount Tax Compensation Amount]*&#x200B;の両方が含まれており、注文概要とレポートデータが一致しています。

<u>実際の結果</u>:

*[!UICONTROL Discount Tax Compensation Amount]*&#x200B;と&#x200B;*[!UICONTROL Shipping Discount Tax Compensation Amount]*&#x200B;が計算に見つからないため、販売注文データとクーポン レポート データが一致しません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

- Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
- クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

[[!DNL Quality Patches Tool]  リリース：ツール ガイドの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
