---
title: 'ACSD-51857: 「aggregate_sales_report_bestsellers_data」の cron ジョブの遅延がパフォーマンスに影響を与える'
description: ACSD-51857 パッチを適用すると、cron ジョブ「aggregate_sales_report_bestsellers_data」が大きな「sales_order」および「sales_order_item」データベーステーブルに影響を与えるAdobe Commerceの問題が修正されます。
exl-id: 48e9852d-2cf6-411c-adf6-f91ac7743338
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-51857:`aggregate_sales_report_bestsellers_data` の cron ジョブが遅いとパフォーマンスに影響する

ACSD-51857 パッチを適用すると、低速な cron ジョブ `aggregate_sales_report_bestsellers_data` が大きな `sales_order` および `sales_order_item` のデータベーステーブルに影響を与える問題が修正されます。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.34 がインストールされている場合に使用できます。 パッチ ID は ACSD-51857 です。 この問題はAdobe Commerce 2.4.7 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 ～ 2.4.6-p2

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

`sales_order` および `sales_order_item` のデータベーステーブルでは、`aggregate_sales_report_bestsellers_data` の Cron ジョブのパフォーマンスが遅い。

これを解決するために、レポートのデータを取得するメインのデータクエリを、より効率的なフォームに書き直しました。 サブクエリを使用してデータのサブセットを決定するようになりました。

サブクエリができるだけ速く機能するように、`store_id`、`state`、`created_at` の列に基づいて `SALES_ORDER_STORE_STATE_CREATED` という新しいインデックスが `sales_order` データベーステーブルに追加されました。

<u> 前提条件 </u>

毎日多数の注文を確認してください。

<u> 再現手順 </u>

1. `aggregate_sales_report_bestsellers_data` cron ジョブを実行します。
1. 管理ダッシュボードの「**[!UICONTROL Bestsellers]**」タブに表示するデータを確認します。

<u> 期待される結果 </u>:

「**[!UICONTROL Configuration]**」タブの *[!UICONTROL Quantity per source]* は空にしないでください。

<u> 実際の結果 </u>:

「**[!UICONTROL Configuration]**」タブの *[!UICONTROL Quantity per source]* が空です。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
