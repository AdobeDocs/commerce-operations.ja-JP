---
title: 'ACSD-60234: [!DNL PayPal]  割引が適用されている場合に、間違った金額が表示される'
description: ACSD-60234 パッチを適用すると、支払い方法を通じて割引が適用された際に  [!DNL PayPal]  が誤った金額を表示するAdobe Commerceの問題を修正できます。
feature: Products, Configuration
role: Admin, Developer
exl-id: 2ce7bde5-02a4-4989-80d6-ab1be0ca5fe9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-60234：割引が適用されると、[!DNL PayPal] に間違った金額が表示される

ACSD-60234 パッチは、支払い方法を通じて割引が適用され [!DNL PayPal] 際に誤った金額が表示される問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.51 がインストールされている場合に使用できます。 パッチ ID は ACSD-60234 です。 この問題はAdobe Commerce 2.5.0 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p2

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

支払方法 [!DNL PayPal] 割引が適用される場合、正しくない金額が表示されます。

<u> 再現手順 </u>:

1. *[!DNL PayPal Express]*/**[!UICONTROL Stores]**/**[!UICONTROL Config]**/**[!UICONTROL Sales]**/**[!UICONTROL Payment methods]**/**[!DNL PayPal]** で **[!UICONTROL Express checkout]** を設定します。
   * [!UICONTROL Enable In-Context Checkout][!UICONTROL Yes] たは [!UICONTROL NO] の場合がありますが、この問題はどちらのシナリオでも発生します。
1. *[!UICONTROL Cart Rule]*/**[!UICONTROL Marketing]**/**[!UICONTROL Promotions]**/**[!UICONTROL Cart Price Rules]** で **[!UICONTROL Add New Rule]** を作成します。
   * 条件：これらの条件がすべて true の場合：*[!UICONTROL Payment Method]* は *[!DNL PayPal Express Checkout]* です。
   * アクション：任意のアクション。
1. 商品を作成します。
1. ストアフロントに移動し、商品を買い物かごに追加して、チェックアウトの **[!UICONTROL Payment Method]** の手順に移動します。
1. *[!DNL PayPal Express]* を選択し、割引が正しく適用されていることを検証してください。
1. **[!DNL PayPal]** ボタンをクリックします。
1. ログインし、ポップアップの内容を確認します。

<u> 期待される結果 </u>:

[!DNL PayPal] に渡される支払い金額には、買い物かごにある割引が含まれます。

<u> 実際の結果 </u>:

合計支払額には割引は含まれません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja): Search for patches[!DNL Quality Patches Tool]」を参照してください。
