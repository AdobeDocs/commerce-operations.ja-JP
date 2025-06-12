---
title: 'ACSD-46617: **[!UICONTROL Continue to Checkout]**ボタンは、小計が設定された最小注文額を超えるとグレー表示されます'
description: ACSD-46617 パッチを適用すると、小計が設定された最小注文額を超えていても**[!UICONTROL Continue to Checkout]** ボタンがグレー表示されるAdobe Commerceの問題が解決されます。
feature: Checkout, Orders
role: Admin
exl-id: 8e808fce-d31c-49ef-94e5-f5c89fffaa73
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-46617：小計が「[!UICONTROL Minimum Order Amount]」より大きい場合、「[!UICONTROL Continue to Checkout]」ボタンがグレー表示される

この ACSD-46617 パッチは、小計が設定された最小注文額より大きい場合でも、「**[!UICONTROL Continue to Checkout]**」ボタンがグレー表示される問題を解決します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24 がインストールされている場合に使用できます。 パッチ ID は ACSD-46617 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 ～ 2.4.5-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

小計が設定された最小注文額を超える場合でも、「**[!UICONTROL Continue to Checkout]**」ボタンはグレー表示されます。

<u> 再現手順 </u>:

1. Adobe Commerce管理者/ **[!UICONTROL Store]** / **[!UICONTROL Configuration]** / **[!UICONTROL Sales]** / **[!UICONTROL Minimum Order Amount]** に移動して、以下を設定します。
   * [!UICONTROL Enable]: *[!UICONTROL Yes]*
   * &#x200B;

     [!UICONTROL Minimum Amount]: *2*

1. [!UICONTROL Cart Price Rule] を作成します。
   * [!UICONTROL Coupon Code]: *[!UICONTROL TEST (optional)]*
   * [!UICONTROL Conditions]: *[!UICONTROL Keep empty]*
   * [!UICONTROL Actions]:
      * [!UICONTROL Apply]: *[!UICONTROL Percent of product price discount]*
      * &#x200B;

        [!UICONTROL Discount Amount]: *92*
      * [!UICONTROL Apply to Shipping Amount]: *[!UICONTROL Yes]*
1. 価格が 25 ドルの製品を作成します。
1. 商品を買い物かごに追加します。
1. 買い物かごに移動し、$5 **[!UICONTROL Flat Rate shipping]** の方法を選択し、クーポンコードを適用します。
1. チェックアウトに移動し、配送を完了して、「**[!UICONTROL Paytment]**」セクションに移動します。
1. 買い物かごに戻ります。

<u> 期待される結果 </u>:

$2.4 の総計が必要な金額$2 を超えているので、最小注文額に関するエラーはありません。

<u> 実際の結果 </u>:

* $2.4 の総計が最小注文金額$2 よりも大きい場合でも、最小注文金額に関するエラーがあります。
* 「**[!UICONTROL Continue to Checkout]**」ボタンは灰色表示になっています。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
