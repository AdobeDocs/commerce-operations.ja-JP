---
title: 'ACSD-61133: ''sales_clean_quotes'' cron は、未承認の発注書から見積を削除します'
description: ACSD-61133 パッチを適用して、「sales_clean_quotes」 cron が未承認の発注書から見積もりを削除するAdobe Commerceの問題を修正してください。
feature: B2B, Purchase Orders
role: Admin, Developer
exl-id: 06979d4b-08ea-40fe-a211-3d950c9afb47
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-61133:`sales_clean_quotes` cron は未承認発注から見積を削除します

ACSD-61133 パッチは、`sales_clean_quotes` cron が未承認の発注書から見積もりを削除する問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.53 がインストールされている場合に使用できます。 パッチ ID は ACSD-61133 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p1

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p5 - 2.4.4-p11、2.4.5-p4 - 2.4.5-p10 および 2.4.6-p2 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

`sales_clean_quotes` cron は未承認の発注書から見積もりを削除します。 *[B2B 発注書]* は、cron によって削除されるので、購入注文に関連付けられた見積もりの注文に変換できません。

<u> 前提条件 </u>:

Adobe Commerce [!UICONTROL B2B] モジュールがインストールされ、有効になっています。

<u> 再現手順 </u>:

1. *[!UICONTROL B2B Purchase Order]* 機能を有効にします。
1. 会社を作成します。
1. *[!UICONTROL Purchase Order]* を作成します。
1. 見積もりが期限切れになり、cron によって削除されるまで待ちます。 見積もりの有効期限は、**[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL Sales]**/**[!UICONTROL Quotes]**/**[!UICONTROL General]**/**[!UICONTROL Default Expiration Period configuration]** で設定できます。
1. *[!UICONTROL My Purchase Order in Customer Dashboard]* または `placeOrderForPurchaseOrder` のミューテーションを使用して、*[!UICONTROL Purchase Order]* を注文 [!DNL GraphQL] 変換します。

<u> 期待される結果 </u>:

アクティブな *[!UICONTROL Purchase Order]* に関連付けられた見積もりは、Cron によって期限切れとして削除されません。 注文は、ストアフロントまたは [!DNL GraphQL] 経由で正常に行われました。

<u> 実際の結果 </u>:

注文が行われず、ストアフロントにエラーが表示されるか、[!DNL GraphQL] 応答で返されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
