---
title: 「ACSD-61200：売上合計の計算における割引税補償の修正」
description: ACSD-61200 パッチを適用すると、売上合計の計算に*[!UICONTROL Discount Tax Compensation Amount]*と*[!UICONTROL Shipping Discount Tax Compensation Amount]*が欠落し、受注データとクーポンレポートのデータに不一致が生じるAdobe Commerceの問題が修正されます。
feature: Reporting, Taxes
role: Admin, Developer
source-git-commit: 61259d8e059cd813a84907e4baef873b2cc8cad0
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# ACSD-61200：売上合計の計算で割引税報酬を修正します

ACSD-61200 パッチでは、*[!UICONTROL Total Amount]* および *[!UICONTROL Total Amount Actual]* の計算で *[!UICONTROL Discount Tax Compensation Amount]* および *[!UICONTROL Shipping Discount Tax Compensation Amount]* が欠落し、その結果、受注データとクーポン・レポート・データの間に不一致が生じる問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 がインストールされている場合に使用できます。 パッチ ID は ACSD-61200 です。 この問題はAdobe Commerce バージョン 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

- Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerce バージョンとの互換性：**

- Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

販売合計の計算に *[!UICONTROL Discount Tax Compensation Amount]* と *[!UICONTROL Shipping Discount Tax Compensation Amount]* が見つからないため、販売注文およびクーポンレポートのデータが不正確です。

<u> 再現手順 </u>:

1. [!UICONTROL Tax Zone] と [!UICONTROL Tax Rule] を作成します。
1. 次の税金構成を設定します。
   - **[!UICONTROL Tax Class for Shipping]** = [!UICONTROL Taxable Goods]
   - **[!UICONTROL Catalog Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Shipping Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Apply Discount on Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Product Prices in Catalog]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Shipping Prices]** = [!UICONTROL Including Tax]
1. 受注、請求書およびクレジット・メモの次の表示設定を更新します。
   - **[!UICONTROL Display Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Subtotal]**= [!UICONTROL Including Tax]
   - **[!UICONTROL Display Shipping Amount]** = [!UICONTROL Including Tax]
1. クーポン付きの [!UICONTROL Cart Price Rule] を 10% 割引で作成します。
1. クーポンを使用して注文を完了し、請求書と出荷を生成します。
1. **[!UICONTROL Reports]**/**[!UICONTROL Sales]**/**[!UICONTROL Coupons]** に移動し、レポートを生成します。
1. 注文概要のデータとレポートのデータを比較します。

<u> 期待される結果 </u>:

*[!UICONTROL Total Amount]* と *[!UICONTROL Total Amount Actual]* の計算には、*[!UICONTROL Discount Tax Compensation Amount]* と *[!UICONTROL Shipping Discount Tax Compensation Amount]* の両方が含まれ、注文概要とレポートデータが一致します。

<u> 実際の結果 </u>:

*[!UICONTROL Discount Tax Compensation Amount]* と *[!UICONTROL Shipping Discount Tax Compensation Amount]* が計算に含まれていないため、販売注文データとクーポン レポート データが一致しません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

- Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
- クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

[[!DNL Quality Patches Tool]  リリース済み：『ツールガイド』の品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
