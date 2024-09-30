---
title: 「ACSD-47232:[!UICONTROL Same as Billing Address] がオンの場合、クーポンが適用されない」
description: ACSD-47232 パッチを適用すると、[!UICONTROL Same as Billing Address] がオンの場合にクーポンが適用されないAdobe Commerceの問題を修正できます。
feature: Orders, Shipping/Delivery
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-47232: [!UICONTROL Same as Billing Address] がオンの場合、クーポンは適用されません

ACSD-47232 パッチは、**[!UICONTROL Same as Billing Address]** がチェックされたときにクーポンが適用されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.23 がインストールされている場合に使用できます。 パッチ ID は ACSD-47232 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 ～ 2.4.5-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

**[!UICONTROL Same as Billing Address]** がオンの場合、クーポンは適用されません。

<u> 再現手順 </u>:

1. Adobe Commerceをインストールします。
1. 重み= *8* のシンプルな製品を作成します。
1. デフォルトの請求先と配送先住所で新しい顧客を作成します。
1. クーポンを使用して買い物かご価格ルールを作成します。
   * **[!UICONTROL Conditions]** のセクションで、*合計ウェイトが 5 以上* を追加します
1. [!UICONTROL Commerce] Admin で新しい注文を作成してみてください。
   * 作成したばかりの顧客を使用します
   * 製品を追加
   * クーポンを適用してみてください

<u> 期待される結果 </u>:

クーポンが適用されます。

<u> 実際の結果 </u>:

次のようなエラーが発生します。*123 クーポンコードが無効です。 コードを確認して、もう一度試してください。*

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。