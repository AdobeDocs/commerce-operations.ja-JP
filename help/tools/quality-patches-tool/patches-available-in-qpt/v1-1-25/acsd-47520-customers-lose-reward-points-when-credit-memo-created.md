---
title: ACSD-47520：クレジットメモが作成されると、顧客は報酬ポイントを失います
description: ACSD-47520 パッチを適用して、クレジットメモの作成時にお客様が報酬ポイントを失うAdobe Commerceの問題を修正します。
feature: Admin Workspace, Cache, Orders, Rewards, Returns
role: Admin
exl-id: 09104451-e9f0-4ddb-b019-8aa34630edb9
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# ACSD-47520：クレジットメモが作成されると、顧客は報酬ポイントを失います

ACSD-47520 パッチは、クレジットメモの作成時に顧客が報酬ポイントを失う問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.25がインストールされている場合に利用できます。 パッチ IDはACSD-47520です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました
* Adobe Commerce（すべてのデプロイメント方法） 2.4.5

**Adobe Commerceのバージョンとの互換性：**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 - 2.4.5-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

クレジットメモを作成すると、顧客はポイントを失います。

<u>複製する手順</u>:

1. Adobe Commerce Admin > **[!UICONTROL Store]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Reward Points]**&#x200B;に移動します。
1. 設定を変更します。
   * **[!UICONTROL Enable Reward Points Functionality]** = _はい_
   * **[!UICONTROL Enable Reward Points Functionality on Storefront]** = _はい_
   * **[!UICONTROL Customers May See Reward Points History]** = _はい_
   * **[!UICONTROL Refund Reward Points Automatically]** = _No_
   * **[!UICONTROL Deduct Reward Points from Refund Amount Automatically]** = _はい_
1. 管理者/**[!UICONTROL Store]** / **[!UICONTROL Other Settings]** / **[!UICONTROL Reward Exchange Rates]**&#x200B;に移動し、**[!UICONTROL Add New Rate]**&#x200B;をクリックします。
1. 新しいレート（1:1）を追加し、キャッシュをフラッシュします。
1. 顧客を作成し、このアカウントに10点の報酬ポイントを追加します。
1. Admin > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Create New Order]** >前の手順で作成した顧客を選択に移動します。
1. 価格が報酬ポイントよりも大きい商品を選択します。
1. 任意の支払い方法と報酬ポイントを介して注文します。
1. 注文の請求書を作成します。
1. クレジットメモを作成しますが、報酬ポイントは返金しません。

<u>期待される結果</u>:

* 管理者は報酬ポイントを返金できます。

* 注文ステータスがクローズされます。

<u>実際の結果</u>:

* ポイントを返金する方法はありません。

* 注文ステータスは&#x200B;**[!UICONTROL Completed]**&#x200B;です。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
