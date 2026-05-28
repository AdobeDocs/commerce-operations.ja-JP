---
title: ACSD-58685：無効な販売メールは、再有効化すると送信される
description: ACSD-58685 パッチを適用して、電子メールのコミュニケーションが無効になっている間に開始されたセールスメールが、電子メールのコミュニケーションが再度有効になると送信されるAdobe Commerceの問題を修正します。
feature: Configuration
role: Admin, Developer
exl-id: 773c0e0e-92c3-42b1-8fbf-fcb05e0e8311
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---

# ACSD-58685：無効な販売メールは、再有効化すると送信される

ACSD-58685 パッチでは、電子メール通信が無効になっている間に営業担当者が開始した電子メールが、電子メール通信が再度有効になると送信される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55がインストールされている場合に利用できます。 パッチ IDはACSD-58685です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

メール通信が無効になっている間に開始されたセールスメールは、メール通信が再度有効になると送信されます。

<u>複製する手順</u>:

1. **[!UICONTROL Sales]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Mail Sending Settings]**&#x200B;に移動し、**[!UICONTROL Disable Email Communications]**&#x200B;を&#x200B;*[!UICONTROL No]*&#x200B;に設定します。
1. **[!UICONTROL Sales]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales Emails]** > **[!UICONTROL General Settings]**&#x200B;に移動し、**[!UICONTROL Asynchronous Sending]**&#x200B;を&#x200B;*[!UICONTROL Yes]*&#x200B;に設定します。
1. 設定キャッシュをクリアします。
1. 注文する。
1. メールコミュニケーションの有効化：
1. 別の注文を行います。
1. cronを実行します。

<u>期待される結果</u>:

2回目の注文のメールのみが送信されます。

<u>実際の結果</u>:

1回目と2回目の両方の注文の電子メールが送信されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

[[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
