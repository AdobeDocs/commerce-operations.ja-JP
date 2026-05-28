---
title: ACSD-48773：間違ったストアから取得したポイントのメールテンプレート
description: ACSD-48773 パッチを適用して、報酬ポイントのメールテンプレートが間違ったストアから取得されるAdobe Commerceの問題を修正します。
feature: Admin Workspace, Communications, Marketing Tools, Orders, Personalization, Rewards
role: Admin
exl-id: db8b6196-3e13-4c1b-8ae8-040487180817
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 0%

---

# ACSD-48773：間違ったストアから取得したポイントのメールテンプレート

ACSD-48773 パッチは、報酬ポイントのメールテンプレートが間違ったストアから取得される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.26がインストールされている場合に利用できます。 パッチ IDはACSD-48773です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

バンドル製品がどのweb サイトにも割り当てられていない場合、製品価格のインデックスは機能しません。

<u>複製する手順</u>:

1. 2つのweb サイト、2つのストア、2つのストアビューを作成する。
1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Reviews]**&#x200B;に移動し、**[!UICONTROL Reviews]**&#x200B;を有効にします。
1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Store Email Addresses]**&#x200B;に移動します。
**[!DNL default website scope]**&#x200B;に切り替えて、**[!UICONTROL Customer Support Sender Email]** アドレスを設定します（例：*support_base@example.com*）。
**[!DNL second website scope]**&#x200B;に切り替えて、**[!UICONTROL Customer Support Sender Email]** アドレスを別の値に設定します（例：*support_second@example.com*）。
1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]** > **[!UICONTROL Share Customer Accounts]**&#x200B;に移動し、Web サイトごとに&#x200B;**[!UICONTROL Share Customer Accounts]** = *と設定します*。
1. **[!UICONTROL Reward Points]**&#x200B;で、次の値を設定します。
   **[!UICONTROL Enable Reward Points Functionality]** = *はい*
   **[!UICONTROL Enable Reward Points Functionality on Storefront]** = *はい*
   **[!UICONTROL Actions for Acquiring Reward Points by Customers]** > **[!UICONTROL Review Submission]**&#x200B;と設定&#x200B;**[!UICONTROL Review Submission]** = *150*
   **[!UICONTROL Email Notification Settings]** > **[!UICONTROL Email Sender]**&#x200B;と設定&#x200B;**[!UICONTROL Email Sender]** = *カスタマーサポート*
1. **[!UICONTROL Stores]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Reward Exchange Rates]**&#x200B;に移動し、**[!UICONTROL Points/Currency]**&#x200B;と&#x200B;**[!UICONTROL Currency/Points]**&#x200B;の両方の2番目のweb サイトの為替レートを設定します。
1. 2番目のweb サイトで顧客アカウントを作成します。
1. 2番目のweb サイトで顧客としてログインします。
1. **[!UICONTROL Balance Updates]**&#x200B;の&#x200B;**[!UICONTROL Subscribe]**&#x200B;を有効にしてください。
1. 製品レビューを送信。
1. **[!UICONTROL Marketing]** > **[!UICONTROL User Content]** > **[!UICONTROL Pending Reviews]**&#x200B;に移動します。
1. 新しいレビューのステータスを&#x200B;***[!UICONTROL Approved]***&#x200B;と&#x200B;**[!UICONTROL Save]**&#x200B;に変更します。
1. メールが届くのを待ちましょう。

<u>期待される結果</u>:

リワードポイントの更新メールは、2番目のweb サイトスコープで設定されたメール送信者が送信する必要があります。

<u>実際の結果</u>:

報酬ポイントの更新メールは、デフォルトのweb サイトスコープで設定されたメール送信者によって送信されました。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
