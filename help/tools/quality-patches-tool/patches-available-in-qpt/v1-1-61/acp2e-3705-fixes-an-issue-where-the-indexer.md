---
title: 'ACP2E-3705: ''MAGE_INDEXER_THREADS_COUNT''が設定されていると、''indexer_update_all_views'' cronの実行が失敗する'
description: ACP2E-3705 パッチを適用して、「MAGE_INDEXER_THREADS_COUNT」が設定されているときに「indexer_update_all_views」 cronの実行が失敗するAdobe Commerceの問題を修正します。
feature: Catalog Management, B2B
role: Admin, Developer
exl-id: 111325fa-8ed5-45f9-9e68-b52f4425d253
type: Troubleshooting
source-git-commit: 319f3232d1ba5f5ed7cdd10ce85b9d7ffbeec89a
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACP2E-3705: `MAGE_INDEXER_THREADS_COUNT`が設定されているときに`indexer_update_all_views` cronの実行が失敗する

>[!NOTE]
>
>このパッチは、バージョン 2.4.7以降の[ACSD-64112](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-59/acsd-64112-indexer-update-all-views-cron-execution-fails.md)に置き換わります。

ACP2E-3705 パッチは、`MAGE_INDEXER_THREADS_COUNT`が設定されているときに`indexer_update_all_views` cronの実行が失敗する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61がインストールされている場合に利用できます。 パッチ IDはACP2E-3705です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

`MAGE_INDEXER_THREADS_COUNT`が&#x200B;*2*&#x200B;より大きい値に設定されていると、`indexer_update_all_views` cronの実行が失敗します。特に、B2Bが有効になっている[!UICONTROL Customer Segments] インデクサーに影響します。

<u>複製する手順</u>:

1. QPT パッチ [ACSD-64112](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-59/acsd-64112-indexer-update-all-views-cron-execution-fails.md)を適用します。
1. **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Category permissions]**&#x200B;に移動します。
1. **[!UICONTROL Category Permissions]**&#x200B;を有効にします。
1. 次のインデクサーを&#x200B;**[!UICONTROL Update on Schedule]** モードに設定します。

   ```shell
   bin/magento indexer:set-mode schedule catalogpermissions_category catalogpermissions_product
   ```

1. いくつかの商品を作成し、カテゴリに割り当てます。
1. 完全なインデックス再作成を実行します。
1. カテゴリに移動し、**[!UICONTROL Category Permissions]**&#x200B;を設定します。
1. `MAGE_INDEXER_THREADS_COUNT`が&#x200B;*8*&#x200B;に設定された`indexer_update_all_views` cron ジョブを実行します。

<u>期待される結果</u>:

インデックスの再作成はエラーなしで完了します。

<u>実際の結果</u>:

`indexer_update_all_views` cron ジョブで次のエラーが発生しました：

```text
Magento\Framework\DB\Adapter\TableNotFoundException: SQLSTATE[42S02]: Base table or view not found: 1146 Table 'magento.catalogpermissions_category_cl__tmp67acb6582cec12_69065236' doesn't exist, query was: SELECT MAX(id) as max, COUNT(*) as cnt FROM (SELECT `catalogpermissions_category_cl__tmp67acb6582cec12_69065236`.* FROM
```


## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* Adobe Commerce オンクラウドインフラストラクチャ：アップグレードとパッチ/パッチの適用については、Commerce オンクラウドインフラストラクチャガイドを参照してください。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
* Commerce Configuration Guideの[&#x200B; パラレルモードでのインデックス再作成](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers#reindexing-in-parallel-mode)。
