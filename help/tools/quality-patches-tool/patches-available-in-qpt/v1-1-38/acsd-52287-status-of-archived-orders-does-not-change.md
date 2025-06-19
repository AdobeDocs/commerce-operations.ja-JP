---
title: 'ACSD-52287: アーカイブ済オーダーのステータスは変更されない'
description: ACSD-52287 パッチを適用すると、クレジットメモが送信された後、アーカイブされた注文のステータスがグリッド上で*完了*から*クローズ*に変わらないAdobe Commerceの問題を修正できます。
feature: Orders, Checkout
role: Admin, Developer
exl-id: 012f49ba-fdc1-4e1e-87fe-7b9c661f231b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# ACSD-52287: アーカイブ済オーダーのステータスは変更されない

ACSD-52287 パッチは、クレジット・メモが送信された後、アーカイブ済の注文のステータスがグリッド上で *完了* から *クローズ* に変更されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.38 がインストールされている場合に使用できます。 パッチ ID は ACSD-52287 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 ～ 2.4.6-p2

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

クレジット・メモが発行された後、アーカイブ済受注のステータスがグリッド上で *完了* から *クローズ* に変更されることはありません。

<u> 再現手順 </u>:

1. *[!UICONTROL Asynchronous Indexing]* の設定
   * 管理者サイドバーで、**[!UICONTROL Stores]**/**[!UICONTROL Settings]**/**[!UICONTROL Configuration]** に移動します。
   * 左側のパネルで「**[!UICONTROL Advanced]**」セクションを展開し、その下 **[!UICONTROL Developer]** 選択します。
   * 「**[!UICONTROL Grid Settings]**」セクションを展開します。
   * *[!UICONTROL Asynchronous indexing]* を *はい* に設定します。
   * 「**[!UICONTROL Save Config]**」をクリックします。
1. *[!UICONTROL Order Archive]* を設定します。
   * 管理者サイドバーで、**[!UICONTROL Stores]**/**[!UICONTROL Settings]**/**[!UICONTROL Configuration]** に移動します。
   * 左側のパネルで「**[!UICONTROL Sales]**」セクションを展開し、その下 **[!UICONTROL Sales]** 選択します。
   * 「**[!UICONTROL Orders, Invoices, Shipments, Credit Memos Archiving]**」セクションを展開します。
   * *[!UICONTROL Enable Archiving]* を *はい* に設定します（残りの設定はデフォルトのままにします）。
   * 「**[!UICONTROL Save Config]**」をクリックします。
1. フロントエンドに注文します。
1. *[!UICONTROL Admin Order Grid]* に表示するには、[!DNL cron] を実行します。
1. 注文のステータスを *完了* に更新するには、注文を請求および出荷します。
1. [!DNL cron] を実行して、*[!UICONTROL Sales Order Grid]* を最新の注文ステータスで更新します。
1. 注文をアーカイブします。
1. *[!UICONTROL Archived order grid]* に行きなさい。
1. [!UICONTROL Credit Memo] アーカイブされた注文を開き、[!UICONTROL Order status] を作成してオフラインで注文を返金します。*Closed*。
1. [!DNL cron] を数回実行します。
1. 新しい注文ステータスの *[!UICONTROL Archived order grid]* を確認します。

<u> 期待される結果 </u>:

注文が *クローズ* と表示されます。

<u> 実際の結果 </u>:

注文が *完了* と表示されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
