---
title: ACSD-46617：小計が設定された最小注文金額を超えると、**[!UICONTROL Continue to Checkout]** ボタンがグレー表示される
description: ACSD-46617 パッチを適用して、小計が設定された最小注文金額を超えていても**[!UICONTROL Continue to Checkout]** ボタンがグレー表示されるAdobe Commerceの問題を解決します。
feature: Checkout, Orders
role: Admin
exl-id: 8e808fce-d31c-49ef-94e5-f5c89fffaa73
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# ACSD-46617：小計が「[!UICONTROL Minimum Order Amount]」を超えると、「[!UICONTROL Continue to Checkout]」ボタンがグレー表示される

このACSD-46617 パッチは、小計が設定された最小注文額を超えていても、**[!UICONTROL Continue to Checkout]** ボタンがグレー表示される問題を解決します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24がインストールされている場合に利用できます。 パッチ IDはACSD-46617です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

小計が設定された最低注文金額を超えている場合でも、**[!UICONTROL Continue to Checkout]** ボタンはグレー表示されます。

<u>複製する手順</u>:

1. Adobe Commerce Admin > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Minimum Order Amount]**&#x200B;に移動し、以下を設定します。
   * [!UICONTROL Enable]: *[!UICONTROL Yes]*
   * &#x200B;
     [!UICONTROL Minimum Amount]: *2*

1. [!UICONTROL Cart Price Rule]を作成します。
   * [!UICONTROL Coupon Code]: *[!UICONTROL TEST (optional)]*
   * [!UICONTROL Conditions]: *[!UICONTROL Keep empty]*
   * [!UICONTROL Actions]:
     * [!UICONTROL Apply]: *[!UICONTROL Percent of product price discount]*
     * &#x200B;
       [!UICONTROL Discount Amount]: *92*
     * [!UICONTROL Apply to Shipping Amount]: *[!UICONTROL Yes]*
1. 25 ドルの価格で商品を作成します。
1. 商品をカートに追加します。
1. ショッピングカートに移動し、$5 **[!UICONTROL Flat Rate shipping]**&#x200B;方法を選択してクーポンコードを適用します。
1. チェックアウトに移動し、配送を完了し、**[!UICONTROL Paytment]** セクションに移動します。
1. ショッピングカートに戻ります。

<u>期待される結果</u>:

最低注文金額に関連するエラーはありません。総計2.4 ドルは、必要な金額2 ドルを超えています。

<u>実際の結果</u>:

* 総注文額2.4 ドルが最低注文額2 ドルを超える場合でも、最低注文額に関連するエラーが発生します。
* **[!UICONTROL Continue to Checkout]** ボタンがグレー表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
