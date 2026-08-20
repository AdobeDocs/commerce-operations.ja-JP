---
title: 'ACSD-60234: [!DNL PayPal] では、割引が適用された場合に誤った金額が表示されます'
description: ACSD-60234 パッチを適用して、Adobe Commerceの問題を修正します。割引が支払い方法を通じて適用された場合、 [!DNL PayPal] に誤った金額が表示されます。
feature: Products, Configuration
role: Admin, Developer
exl-id: 2ce7bde5-02a4-4989-80d6-ab1be0ca5fe9
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-60234: [!DNL PayPal]では、割引が適用されたときに誤った金額が表示されます

ACSD-60234 パッチは、支払い方法で割引が適用された場合に[!DNL PayPal]に誤った金額が表示される問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.51がインストールされている場合に利用できます。 パッチ IDはACSD-60234です。 この問題は、Adobe Commerce 2.5.0で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p2

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

支払い方法で割引が適用された場合、[!DNL PayPal]に誤った金額が表示されます。

<u>複製する手順</u>:

1. *[!DNL PayPal Express]*&#x200B;を&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Sales]** > **[!UICONTROL Payment methods]** > **[!DNL PayPal]** > **[!UICONTROL Express checkout]**&#x200B;に設定します。
   * [!UICONTROL Enable In-Context Checkout]には[!UICONTROL Yes]または[!UICONTROL NO]を指定できます。両方のシナリオで問題が再現されます。
1. *[!UICONTROL Cart Rule]*&#x200B;を&#x200B;**[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Cart Price Rules]** > **[!UICONTROL Add New Rule]**&#x200B;に作成します。
   * 条件：これらの条件がすべてtrueの場合：*[!UICONTROL Payment Method]*&#x200B;は&#x200B;*[!DNL PayPal Express Checkout]*&#x200B;です。
   * アクション：任意のアクション。
1. 商品を作成する。
1. ストアフロントに移動し、商品をカートに追加してから、チェックアウトの&#x200B;**[!UICONTROL Payment Method]** ステップに進みます。
1. *[!DNL PayPal Express]*&#x200B;を選択し、割引が正しく適用されていることを確認してください。
1. 「**[!DNL PayPal]**」ボタンをクリックします。
1. ログインして、ポップアップの内容を確認します。

<u>期待される結果</u>:

[!DNL PayPal]に渡される支払い金額には、カート内の割引が含まれます。

<u>実際の結果</u>:

支払う合計金額には割引は含まれておりません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!DNL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
