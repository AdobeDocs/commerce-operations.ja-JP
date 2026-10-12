---
title: 'ACP2E-3977: [!UICONTROL Cap Reward Points Balance At] フィールドを空のままにすることはできません'
description: ACP2E-3977 パッチを適用して、**[!UICONTROL Rewards Points Balance Redemption Threshold]** フィールドが設定されたときに**[!UICONTROL Cap Reward Points Balance At]** フィールドを空のままにできず、検証エラーが発生するAdobe Commerceの問題を修正します。
feature: Configuration, Rewards
role: Admin, Developer
type: Troubleshooting
exl-id: 5275911f-4f8c-4b37-af11-24ceb69406c9
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 4069cee6-4dc8-5a83-81de-232af6a7c9e9
    internal-label: Rewards
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%
---
# ACP2E-3977: **[!UICONTROL Cap Reward Points Balance At]** フィールドを空のままにすることはできません

ACP2E-3977 パッチは、許可される必要がある場合でも&#x200B;**[!UICONTROL Cap Reward Points Balance At]** フィールドを空のままにできない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69がインストールされている場合に利用できます。 パッチ IDはACP2E-3977です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p10

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

空白のままにするとキャップが無効になるはずですが、**[!UICONTROL Cap Reward Points Balance At]**&#x200B;個の空のトリガーを検証エラーとして残します。

<u>複製する手順</u>:

1. **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Reward points]**&#x200B;に移動します。
1. **[!UICONTROL Rewards Points Balance Redemption Threshold]** = *30*&#x200B;と設定します。
1. **[!UICONTROL Cap Reward Points Balance At]**&#x200B;を空のままにします。
1. 保存。

<u>期待される結果</u>:

**[!UICONTROL Cap Reward Points Balance At]**&#x200B;の空の値は許可され、制限は無効になります。

<u>実際の結果</u>:

*キャップ報酬ポイントの残高が無効です。 残高は正の数値または空のままにする必要があります。 確認して、もう一度やり直してください。* エラーが表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
