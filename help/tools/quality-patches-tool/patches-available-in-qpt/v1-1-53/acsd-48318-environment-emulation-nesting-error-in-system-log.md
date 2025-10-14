---
title: ACSD-48318：環境エミュレーションの「system.log」でのネスティングエラー
description: ACSD-48318 パッチを適用すると、請求書のメールが送信されるたびに「system.log」に「main.ERROR:Environment emulation nesting is not allowed*」というエラーメッセージが表示されるAdobe Commerceの問題が修正されます。
feature: System, Orders
role: Admin, Developer
exl-id: 24af18de-80dd-4e0a-bdf9-5b9c075fc608
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# ACSD-48318:`system.log` での環境エミュレーションのネスト エラー

ACSD-48318 パッチでは、請求書のメールが送信されるたびにエラーメッセージ *main.ERROR:Environment エミュレーションのネストが許可されていません* が `system.log` に表示される問題を修正しています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53 がインストールされている場合に使用できます。 パッチ ID は ACSD-48318 です。 この問題はAdobe Commerce 2.4.7 で修正されていることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

「*環境エミュレーションのネストは許可されていません*」というエラーメッセージが、請求書のメールを送信するたびに `system.log` に表示されます。

<u> 再現手順 </u>:

1. 注文を行い、請求書を生成します。
1. 管理者から請求書を開き、「**[!UICONTROL Send Email]**」をクリックします。
1. 「*」をクリックして、* クレジット・メモ *および* 出荷 **[!UICONTROL Send Email]** に対して同じ手順に従います。

<u> 期待される結果 </u>:

`system.log` にエラーはありません。

<u> 実際の結果 </u>:

`system.log` が *main.ERROR であふれています：環境エミュレーションのネストは許可されていません* エラー。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 &#x200B;](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [&#x200B; アップグレードとパッチ &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

[[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
