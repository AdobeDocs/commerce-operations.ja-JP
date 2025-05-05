---
title: 'ACP2E-3705: 「MAGE_INDEXER_INDEXER_THREADS_COUNT」が設定されている場合、「indexer_update_all_views」 cron 実行が失敗します'
description: ACP2E-3705 パッチを適用して、「MAGE_INDEXER_THREADS_COUNT」が設定されている場合に「indexer_update_all_views」 cron の実行が失敗するAdobe Commerceの問題を修正してください。
feature: Catalog Management, B2B
role: Admin, Developer
source-git-commit: 4f719c62fdd9fd960548799c9872f73c76997278
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---


# ACP2E-3705:`MAGE_INDEXER_THREADS_COUNT` が設定されている場合、`indexer_update_all_views` cron 実行が失敗する

>[!NOTE]
>
>このパッチは、バージョン 2.4.7 以降の [ACSD-64112](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-59/acsd-64112-indexer-update-all-views-cron-execution-fails.md) に代わるものです。

ACP2E-3705 パッチは、`MAGE_INDEXER_THREADS_COUNT` が設定されているときに `indexer_update_all_views` cron 実行が失敗する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 がインストールされている場合に使用できます。 パッチ ID は ACP2E-3705 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

`MAGE_INDEXER_THREADS_COUNT` が *2* より大きい値に設定されている場合、`indexer_update_all_views` cron の実行は失敗します。特に、B2B が有効になっている [!UICONTROL Customer Segments] インデクサーに影響します。

<u> 再現手順 </u>:

1. QPT パッチ [ACSD-64112](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-59/acsd-64112-indexer-update-all-views-cron-execution-fails.md) を適用します。
1. **[!UICONTROL Admin]**/**[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL Catalog]**/**[!UICONTROL Category permissions]** に移動します。
1. **[!UICONTROL Category Permissions]** を有効にします。
1. 次のインデクサーを **[!UICONTROL Update on Schedule]** モードに設定します。

   ```
   bin/magento indexer:set-mode schedule catalogpermissions_category catalogpermissions_product
   ```

1. いくつかの製品を作成してカテゴリに割り当てます。
1. 完全な再インデックスを実行します。
1. カテゴリに移動し、**[!UICONTROL Category Permissions]** を設定します。
1. *8*`indexer_update_all_views` 設定した cron ジョブ `MAGE_INDEXER_THREADS_COUNT` 実行します。

<u> 期待される結果 </u>:

再インデックスがエラーなしで完了しました。

<u> 実際の結果 </u>:

`indexer_update_all_views` cron ジョブで次のエラーが発生します。

```
Magento\Framework\DB\Adapter\TableNotFoundException: SQLSTATE[42S02]: Base table or view not found: 1146 Table 'magento.catalogpermissions_category_cl__tmp67acb6582cec12_69065236' doesn't exist, query was: SELECT MAX(id) as max, COUNT(*) as cnt FROM (SELECT `catalogpermissions_category_cl__tmp67acb6582cec12_69065236`.* FROM
```


## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* Adobe Commerce on Cloud Infrastructure: アップグレードとパッチ > Commerce on Cloud Infrastructure ガイドのパッチの適用

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
