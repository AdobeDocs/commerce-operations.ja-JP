---
title: ACSD-60344：自動承認を含む [!UICONTROL Purchase Order] を使用した際の重複注文確認メール
description: ACSD-60344 パッチを適用すると、自動承認された [!UICONTROL Purchase Order] を使用するときに重複注文確認メールが送信されるAdobe Commerceの問題を修正できます。
feature: Purchase Orders
role: Admin, Developer
exl-id: c4d415ee-b1ac-4094-9209-19b91f9a7666
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 0%

---

# ACSD-60344：自動承認を含む *[!UICONTROL Purchase Order]* を使用した際の重複注文確認メール

ACSD-60344 パッチは、自動承認を備えた *[!UICONTROL Purchase Order]* を使用した場合に、重複注文確認メールが送信される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 がインストールされている場合に使用できます。 パッチ ID は ACSD-60344 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p4

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3


>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

自動承認を含む *[!UICONTROL Purchase Order]* を使用すると、重複注文確認メールが送信されます。

<u> 前提条件 </u>

B2B モジュールと *[!UICONTROL Purchase Order]* を有効にします。

<u> 再現手順 </u>:

1. 会社アカウントを作成し、その *[!UICONTROL Purchase Order]* を有効にします。
1. 通常のユーザーアカウントを作成し、会社ユーザーとして会社アカウントに追加します。
1. このアカウントを使用して注文します。
1. cron を実行してメールを確認します。

<u> 期待される結果 </u>:

1 件の注文につき、1 件の注文確認メールのみが受信されます。

<u> 実際の結果 </u>:

2 通の注文確認メールが受信されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 &#x200B;](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [&#x200B; アップグレードとパッチ &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。


## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
