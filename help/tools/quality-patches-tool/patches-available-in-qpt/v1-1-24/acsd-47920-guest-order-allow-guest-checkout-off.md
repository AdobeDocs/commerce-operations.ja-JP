---
title: ACSD-47920：ゲストユーザーは、オフの場合でも、REST API を使用して注文 [!UICONTROL Allow Guest Checkout] きます
description: ACSD-47920 パッチを適用すると、サー [!UICONTROL Allow Guest Checkout] スがオフになっている場合でも、ゲストユーザーとして REST API を介して注文できるAdobe Commerceの問題を修正できます。
feature: REST, Checkout, Orders
role: Admin
exl-id: 27c74803-a3f3-46bc-9eb8-8e2c72c30cd9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-47920：ゲストユーザーは、オフの場合でも、REST API を使用して注文 **[!UICONTROL Allow Guest Checkout]** きます

ACSD-47920 パッチは、**[!UICONTROL Allow Guest Checkout]** ールがオフになっている場合でも、ゲストユーザーとして REST API を介して注文できる問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24 がインストールされている場合に使用できます。 パッチ ID は ACSD-47920 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 ～ 2.4.5-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

**[!UICONTROL Allow Guest Checkout]** ールがオフになっている場合でも、Rest API を介してゲストユーザーとして注文できます。

<u> 再現手順 </u>:

1. Adobe Commerce管理者/ **[!UICONTROL Stores]** / **[!UICONTROL Settings]** / **[!UICONTROL Configuration]** / **[!UICONTROL Sales]** / **[!UICONTROL Sales]** / **[!UICONTROL Checkout]** / **[!UICONTROL Checkout Options]** に移動し、**[!UICONTROL Allow Guest Checkout]** を _いいえ_ に設定します。
1. REST API を使用して、買い物かごに製品を追加し、注文します。

<u> 期待される結果 </u>:

「_いいえ_」に設定されている場合、ゲストチェックアウト API **[!UICONTROL Allow Guest Checkout]** エラー *[!UICONTROL Sorry, guest checkout is not available]* を返します。

<u> 実際の結果 </u>:

Guest checkout API は、**[!UICONTROL Allow Guest Checkout]** が _No_ に設定されている場合でも注文できます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
