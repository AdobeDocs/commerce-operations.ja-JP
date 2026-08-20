---
title: ACSD-52287：アーカイブされた注文のステータスが変更されない
description: ACSD-52287 パッチを適用して、クレジットメモが送信された後、アーカイブされた注文のステータスが*完了*から*クローズ*に変わらないAdobe Commerceの問題を修正します。
feature: Orders, Checkout
role: Admin, Developer
exl-id: 012f49ba-fdc1-4e1e-87fe-7b9c661f231b
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# ACSD-52287：アーカイブされた注文のステータスが変更されない

ACSD-52287 パッチは、クレジットメモが送信された後、グリッド上のアーカイブされた注文のステータスが&#x200B;*完了*&#x200B;から&#x200B;*終了*&#x200B;に変更されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.38がインストールされている場合に利用できます。 パッチ IDはACSD-52287です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

クレジットメモが送信された後、グリッドの&#x200B;*完了*&#x200B;から&#x200B;*終了*&#x200B;にアーカイブされた注文のステータスが変更されません。

<u>複製する手順</u>:

1. *[!UICONTROL Asynchronous Indexing]*&#x200B;を設定します。
   * 管理者サイドバーで、**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**&#x200B;に移動します。
   * 左側のパネルで「**[!UICONTROL Advanced]**」セクションを展開し、下の「**[!UICONTROL Developer]**」を選択します。
   * **[!UICONTROL Grid Settings]** セクションを展開します。
   * *[!UICONTROL Asynchronous indexing]*&#x200B;を&#x200B;*はい*&#x200B;に設定します。
   * **[!UICONTROL Save Config]**&#x200B;をクリックします。
1. *[!UICONTROL Order Archive]*&#x200B;を設定します。
   * 管理者サイドバーで、**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**&#x200B;に移動します。
   * 左側のパネルで「**[!UICONTROL Sales]**」セクションを展開し、下の「**[!UICONTROL Sales]**」を選択します。
   * **[!UICONTROL Orders, Invoices, Shipments, Credit Memos Archiving]** セクションを展開します。
   * *[!UICONTROL Enable Archiving]*&#x200B;を&#x200B;*Yes*&#x200B;に設定します（残りの設定はデフォルトのままにします）。
   * **[!UICONTROL Save Config]**&#x200B;をクリックします。
1. フロントエンドで注文します。
1. 注文が&#x200B;*[!UICONTROL Admin Order Grid]*&#x200B;に表示されるように[!DNL cron]を実行します。
1. 請求書と発送：注文ステータスを&#x200B;*完了*&#x200B;に更新する注文です。
1. [!DNL cron]を実行して、最新の注文状況で&#x200B;*[!UICONTROL Sales Order Grid]*&#x200B;を更新します。
1. 注文をアーカイブします。
1. *[!UICONTROL Archived order grid]*&#x200B;に移動します。
1. アーカイブされた注文を開き、[!UICONTROL Credit Memo]を作成してオフラインで注文を返金し、[!UICONTROL Order status]: *クローズ*&#x200B;します。
1. [!DNL cron]を数回実行します。
1. 新しい注文ステータスについては、*[!UICONTROL Archived order grid]*&#x200B;を確認してください。

<u>期待される結果</u>:

注文は&#x200B;*Closed*&#x200B;と表示されます。

<u>実際の結果</u>:

注文は&#x200B;*完了*&#x200B;と表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
