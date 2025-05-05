---
title: ACSD-58685：無効な販売 E メールは、再有効化すると送信されます
description: ACSD-58685 パッチを適用すると、メール通信が無効になっている場合に開始した営業メールが、メール通信が再度有効になると送信されるAdobe Commerceの問題を修正できます。
feature: Configuration
role: Admin, Developer
source-git-commit: db495f2dbf307f9da42b6dc4fc7bed1e6af1d307
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# ACSD-58685：無効な販売 E メールは、再有効化すると送信されます

ACSD-58685 パッチは、メール通信が無効な場合に開始された販売メールが、メール通信が再度有効になると送信される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 がインストールされている場合に使用できます。 パッチ ID は ACSD-58685 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

メール通信が無効な場合に開始した販売メールは、メール通信が再度有効になると送信されます。

<u> 再現手順 </u>:

1. **[!UICONTROL Sales]**/**[!UICONTROL Configuration]**/**[!UICONTROL Advanced]**/**[!UICONTROL System]**/**[!UICONTROL Mail Sending Settings]** に移動し、**[!UICONTROL Disable Email Communications]** を *[!UICONTROL No]* に設定します。
1. **[!UICONTROL Sales]**/**[!UICONTROL Configuration]**/**[!UICONTROL Sales]**/**[!UICONTROL Sales Emails]**/**[!UICONTROL General Settings]** に移動し、**[!UICONTROL Asynchronous Sending]** を *[!UICONTROL Yes]* に設定します。
1. 設定キャッシュをクリアします。
1. 注文します。
1. メール通信を有効にします。
1. 別の注文を行います。
1. cron を実行します。

<u> 期待される結果 </u>:

2 番目の注文のメールのみが送信されます。

<u> 実際の結果 </u>:

1 通目と 2 通目の両方の注文に対してメールが送信されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

[[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
