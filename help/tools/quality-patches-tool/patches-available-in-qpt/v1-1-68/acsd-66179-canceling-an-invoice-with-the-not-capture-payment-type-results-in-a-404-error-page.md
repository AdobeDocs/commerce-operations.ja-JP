---
title: ACSD-66179:[!UICONTROL Not Capture] 支払タイプの請求書を取り消すと、404 エラーページが表示される
description: ACSD-66179 パッチを適用すると、[!UICONTROL Not Capture] 支払いタイプの請求書をキャンセルすると 404 エラーページが発生するAdobe Commerceの問題を修正できます。
feature: Orders, Payments
role: Admin, Developer
type: Troubleshooting
exl-id: a7c1827d-fe28-40e2-9ec6-a04b4a5d33ee
source-git-commit: a35beeb278ac3b72701c54ac7727fd5423e687e7
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# ACSD-66179:[!UICONTROL Not Capture] 支払タイプの請求書を取り消すと、404 エラーページが表示される

ACSD-66179 パッチでは、*[!UICONTROL Not Capture]* の支払いタイプで作成された請求書をキャンセルすると、404 エラーページが発生する問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 がインストールされている場合に使用できます。 パッチ ID は ACSD-66179 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p5

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p11 - 2.4.4-p14、2.4.5-p10 - 2.4.5-p13、2.4.6-p8 - 2.4.6-p11、2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

*[!UICONTROL Not Capture]* 支払タイプで作成された請求書をキャンセルすると、404 エラーページが表示されます。

<u> 再現手順 </u>:

1. PayPal Express Checkout などの支払い方法を使用して注文を作成します。
1. 請求書を作成します。 **[!UICONTROL Amount]** を *[!UICONTROL Not Capture]* に設定し、請求書を発行します。
1. 作成した請求書を開き、「**[!UICONTROL Cancel]**」を選択します。

<u> 期待される結果 </u>:

1. 請求書は正常にキャンセルされました。
1. 成功メッセージ「*請求書を取り消しました。* が表示されます。

<u> 実際の結果 </u>:

404 エラーページが表示されます。*ページが見つかりません。*

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
