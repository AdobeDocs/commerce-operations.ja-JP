---
title: 'ACSD-64209: Cron スケジューラーは、[!UICONTROL Ordered]個の引用符を除外せずに交渉可能な引用符を取得します'
description: ACSD-64209 パッチを適用して、cron スケジューラーがステータス [!UICONTROL Ordered]を持つ引用符を除外せずにすべての交渉可能な引用符を取得し、電子メールまたは電子メールがトリガーされるAdobe Commerceの問題を修正します。
feature: B2B, Communications
role: Admin, Developer
exl-id: 51ba0edc-ad0c-4e32-acd7-2337a62bff53
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bb03f6c4-cab9-560e-9d02-5816e1808d17
    internal-label: Communications
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 4a03af2383a03584c88feb83e7ad726a42cab2d6
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%
---
# ACSD-64209: Cron スケジューラーは、[!UICONTROL Ordered]個の引用符を除外せずに交渉可能な引用符を取得します

ACSD-64209 パッチでは、cron スケジューラーがステータス **[!UICONTROL Ordered]**&#x200B;の引用符を除外せずに、すべての交渉可能な引用符を取得し、電子メールまたは電子メールがトリガーされる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61がインストールされている場合に利用できます。 パッチ IDはACSD-64209です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

cron スケジューラーは、ステータス **[!UICONTROL Ordered]**&#x200B;を持つ引用符を除外せずに、すべての交渉可能な引用符を取得し、電子メールまたは電子メールをトリガーします。

<u>複製する手順</u>:


1. *管理者* サイドバーで、**[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL B2B Features]**&#x200B;に移動し、会社とB2B Quoteを有効にします。
1. **[!UICONTROL Default Expiration Period]**&#x200B;を&#x200B;*管理者* > **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** > **[!UICONTROL General]**&#x200B;の&#x200B;*1*&#x200B;に設定します。
1. 会社を作成してアクティベートし、会社の管理者としてログインします。
1. 商品をカートに追加する。
1. 見積もりを依頼。
1. *管理者* サイドバーで、**[!UICONTROL Sales]** > **[!UICONTROL Quotes]**&#x200B;に移動します。
1. 作成した見積もりを選択し、**[!UICONTROL Send]**&#x200B;をクリックして、見積もりを購入者に送り返します。
1. ストアフロントの会社管理者としてログインします。
1. 見積もりを選択し、**[!UICONTROL Proceed to checkout]**&#x200B;をクリックして購入を完了します。
1. 見積のステータスが&#x200B;**[!UICONTROL Ordered]**&#x200B;であり、ストアフロントでこれ以上アクションが実行できないことを確認してください。
1. `negotiable_quote_send_emails` cron ジョブをトリガーします。


<u>期待される結果</u>:

見積もりが注文され、それ以上のアクションを実行できないため、見積もりの有効期限に関するメールを送信しないでください。

<u>実際の結果</u>:

メール *見積もりは間もなく期限切れになります*&#x200B;が送信されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
