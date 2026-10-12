---
title: 'ACSD-51857: ''aggregate_sales_report_bestsellers_data''のスロークロンジョブがパフォーマンスに影響する'
description: 遅いcron job 'aggregate_sales_report_bestsellers_data'が大規模な'sales_order'および'sales_order_item' データベーステーブルに影響するAdobe Commerceの問題を修正するには、ACSD-51857 パッチを適用します。
exl-id: 48e9852d-2cf6-411c-adf6-f91ac7743338
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
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
source-wordcount: '401'
ht-degree: 0%
---
# ACSD-51857: `aggregate_sales_report_bestsellers_data`のスロークロンジョブがパフォーマンスに影響する

ACSD-51857 パッチは、遅いcron ジョブ `aggregate_sales_report_bestsellers_data`が大きな`sales_order`および`sales_order_item` データベーステーブルに影響を与える問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.34がインストールされている場合に利用できます。 パッチ IDはACSD-51857です。 この問題は、Adobe Commerce 2.4.7で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

`aggregate_sales_report_bestsellers_data`のCron ジョブのパフォーマンスが、`sales_order`および`sales_order_item` データベーステーブルで遅くなっています。

これを解決するために、レポートのデータを取得するメインのデータクエリが、より効率的なフォームに書き換えられました。 サブクエリを使用してデータサブセットを決定するようになりました。

サブクエリをできるだけ早く機能させるために、`sales_order` データベーステーブル `SALES_ORDER_STORE_STATE_CREATED`に対して、`store_id`、`state`、および`created_at`列に基づいて新しいインデックスが追加されました。

<u>前提条件</u>

毎日大量の注文を確保する。

<u>複製する手順</u>

1. `aggregate_sales_report_bestsellers_data` cron ジョブを実行します。
1. 管理者ダッシュボードの「**[!UICONTROL Bestsellers]**」タブに表示するデータを確認します。

<u>期待される結果</u>:

「**[!UICONTROL Configuration]**」タブの「*[!UICONTROL Quantity per source]*」は空にしないでください。

<u>実際の結果</u>:

**[!UICONTROL Configuration]** タブの&#x200B;*[!UICONTROL Quantity per source]*&#x200B;は空です。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
