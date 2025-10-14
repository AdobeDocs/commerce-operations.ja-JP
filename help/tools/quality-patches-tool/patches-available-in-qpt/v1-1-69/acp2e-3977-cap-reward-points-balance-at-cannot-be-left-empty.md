---
title: 'ACP2E-3977: [!UICONTROL Cap Reward Points Balance At] フィールドを空白にすることはできません'
description: ACP2E-3977 パッチを適用して、**[!UICONTROL Cap Reward Points Balance At]** フィールドが設定されている場合に**[!UICONTROL Rewards Points Balance Redemption Threshold]** フィールドを空のままにできず、検証エラーが発生するAdobe Commerceの問題を修正してください。
feature: Configuration, Rewards
role: Admin, Developer
type: Troubleshooting
exl-id: 5275911f-4f8c-4b37-af11-24ceb69406c9
source-git-commit: 83ce590c5078d70f0414276e2f03a71bdcdad321
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# ACP2E-3977: **[!UICONTROL Cap Reward Points Balance At]** フィールドを空白にすることはできません

ACP2E-3977 パッチは、フィールドを許可する必要がある場合でも、**[!UICONTROL Cap Reward Points Balance At]** のフィールドを空のままにできない問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 がインストールされている場合に使用できます。 パッチ ID は ACP2E-3977 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p10

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

空 **[!UICONTROL Cap Reward Points Balance At]**&#x200B;トリガーを残すと、空白の場合はキャップを無効にする必要がありますが、検証エラーが発生します。

<u> 再現手順 </u>:

1. **[!UICONTROL Stores]**/**[!UICONTROL Settings]**/**[!UICONTROL Configuration]**/**[!UICONTROL Customers]**/**[!UICONTROL Reward points]** に移動します。
1. **[!UICONTROL Rewards Points Balance Redemption Threshold]** = *30* を設定します。
1. 空のままに **[!UICONTROL Cap Reward Points Balance At]** ます。
1. 保存します。

<u> 期待される結果 </u>:

**[!UICONTROL Cap Reward Points Balance At]** の空の値は許可され、制限を無効にします。

<u> 実際の結果 </u>:

*キャップ報酬ポイントの残高が無効です。 残高は正の数にするか、空のままにする必要があります。 確認して、もう一度試してください。エラ* が表示されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 &#x200B;](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [&#x200B; アップグレードとパッチ &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
