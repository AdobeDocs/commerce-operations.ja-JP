---
title: 'ACSD-64209: Cron スケジューラーが [!UICONTROL Ordered] ート引用符を除外せずに交渉可能な引用符を取得する'
description: ACSD-64209 パッチを適用すると、cron スケジューラーがステータス [!UICONTROL Ordered] の引用符を除外せずに交渉可能なすべての引用符を取得し、メールまたはメールがトリガーされるAdobe Commerceの問題が修正されます。
feature:  B2B, Communications
role: Admin, Developer
exl-id: 51ba0edc-ad0c-4e32-acd7-2337a62bff53
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-64209: Cron スケジューラーが [!UICONTROL Ordered] ート引用符を除外せずに交渉可能な引用符を取得する

ACSD-64209 パッチは、cron スケジューラーがステータス **[!UICONTROL Ordered]** の引用符を除外せずに交渉可能なすべての引用符を取得し、メールまたはメールがトリガーされる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 がインストールされている場合に使用できます。 パッチ ID は ACSD-64209 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

cron スケジューラーは、ステータスが **[!UICONTROL Ordered]** の引用符を除外せずに交渉可能なすべての引用符を取得し、メールまたはメールをトリガーします。

<u> 再現手順 </u>:


1. *管理者* サイドバーで、**[!UICONTROL Stores]**/*[!UICONTROL Settings]*/**[!UICONTROL Configuration]**/**[!UICONTROL B2B Features]** に移動し、「会社と B2B 見積」を有効にします。
1. *管理者*/**[!UICONTROL Stores]**/*[!UICONTROL Settings]*/**[!UICONTROL Configuration]**/**[!UICONTROL Sales]**/**[!UICONTROL Quotes]**/**[!UICONTROL General]** で、**[!UICONTROL Default Expiration Period]** を *1* に設定します。
1. 会社を作成してアクティブにし、会社管理者としてログインします。
1. 商品を買い物かごに追加します。
1. 見積もりを依頼します。
1. *管理者* サイドバーで、**[!UICONTROL Sales]**/**[!UICONTROL Quotes]** に移動します。
1. 作成した見積書を選択し、「**[!UICONTROL Send]**」をクリックして見積書を購買担当に送り返します。
1. ストアフロントで会社管理者としてログインします。
1. 見積もりを選択し、「**[!UICONTROL Proceed to checkout]**」をクリックして購入を完了します。
1. 見積もりの状態が **[!UICONTROL Ordered]** で、ストアフロントでこれ以上アクションを実行できないことを確認します。
1. `negotiable_quote_send_emails` cron ジョブをトリガーします。


<u> 期待される結果 </u>:

見積は注文されており、それ以上のアクションは実行できないので、見積の有効期限に関するメールを送信しないでください。

<u> 実際の結果 </u>:

*Quote expires soon* というメールが送信されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
