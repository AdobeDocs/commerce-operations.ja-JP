---
title: 「ACSD-57315：取得ボタンをクリックするたびに、新しいトランザクションが  [!DNL PayPal Payflow Pro]  に作成される」
description: ACSD-57315 パッチを適用すると、[!UICONTROL Admin] ールバーのトランザクションを表示画面で「取得」ボタンをクリックするたびに新しいトランザクションが作成されるAdobe Commerceの問題が修正されます。 [!DNL PayPal Payflow Pro]  の例を以下に示します。
feature: Payments
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-57315:「取得」ボタンをクリックするたびに、[!DNL PayPal Payflow Pro] に新しいトランザクションが作成されます

ACSD-57315 パッチでは、[!UICONTROL Admin] ージのトランザクションの表示画面で「取得」ボタンをクリックするたびに [!DNL PayPal Payflow Pro] に新しいトランザクションが作成される問題が修正されています。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.48 がインストールされている場合に使用できます。 パッチ ID は ACSD-57315 です。 この問題はAdobe Commerce 2.5.0 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 ～ 2.4.6-p4

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

[!UICONTROL Admin] ージのトランザクションを表示画面で「取得」ボタンをクリックするたびに、[!DNL PayPal Payflow Pro] に新しいトランザクションが作成されます。

<u> 再現手順 </u>:

1. [!DNL PayPal Payflow Pro] の設定
1. トランザクションメソッドを *[!UICONTROL Sale]* に設定します。
1. *クレジットカード* を使用して注文します。
1. [!UICONTROL Admin] からトランザクションを開きます。
1. 「**[!UICONTROL Fetch]**」ボタンをクリックします。
1. 注文 [!DNL PayPal] 関連するトランザクションの勘定を確認します。

<u> 期待される結果 </u>:

新しい支払トランザクションは作成されません。

<u> 実際の結果 </u>:

既に支払いが行われた注文に対して、新しい支払いトランザクションが作成されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
