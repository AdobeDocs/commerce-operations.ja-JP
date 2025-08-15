---
title: 「[!UICONTROL Indexing]」タブ
description: '[!UICONTROL Indexing] の「 [!DNL Observation for Adobe Commerce]」タブについて説明します。'
exl-id: c7e123b7-2d0c-49d4-9f76-128939dc02a8
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# 「[!UICONTROL Indexing]」タブ

「**[!UICONTROL Indexing]**」タブでは、インデックス作成に関する問題の説明と潜在的な原因の特定を試みます。

## [!UICONTROL Core index invalidated]

![ コアインデックスが無効化されました ](../../assets/tools/observation-for-adobe-commerce/indexing-tab-1.jpg)

**[!UICONTROL Core index invalidated]** のフレームでは、選択した期間におけるインデックス作成の無効化を確認します。 インデックス作成が他のリソースを大量に消費する [!DNL crons] と同時に行われる場合は、サイトリソースに大きな負荷がかかります。

* `%Catalog Product Rule indexer has been invalidated%`） as `catalog_product_rule_idx_reset`
* `%Catalog Rule Product indexer has been invalidated%`） as `catalog_rule_product_idx_reset`
* `%Catalog Search indexer has been invalidated%`） as `catalog_search_idx_reset`
* `%Category Products indexer has been invalidated%`） as `category_products_idx_reset`
* `%Customer Grid indexer has been invalidated%`） as `customer_grid_idx_reset`
* `%Design Config Grid indexer has been invalidated%`） as `design_config_grid_idx_`
* `%Product Categories indexer has been invalidated%`） as `product_categories_idx_reset`
* `%Product EAV indexer has been invalidated%`） as `product_eav_idx_reset`
* `%Product Price indexer has been invalidated%`） as `product_price_idx_reset`
* `%Stock indexer has been invalidated%`） as `stock_idx_reset`
* `%Inventory indexer has been invalidated%`） as `inventory_idx_reset`
* `%Inventory indexer has been invalidated%`） as `inventory_idx_reset`
* `%Sales Rule indexer has been invalidated%`） as `sales_rule_idx_reset`

## [!UICONTROL Core index rebuilds]

![ コアインデックスの再構築 ](../../assets/tools/observation-for-adobe-commerce/indexing-tab-2.jpg)

**[!UICONTROL Core index rebuilds]** フレームは、選択した期間のコアインデックス再構築を確認します。 次に、インデックスの再構築完了を示すために、ログから解析される文字列を示します。

* `%Catalog Product Rule index has been rebuilt%`） as `catalog_product_rule_idx`
* `%Catalog Rule Product index has been rebuilt%`） as `catalog_rule_product_idx`
* `%Catalog Search index has been rebuilt%`） as `catalog_search_idx`
* `%Category Products index has been rebuilt successfully%`） as `category_products_idx`
* `%Customer Grid index has been rebuilt%`） as `customer_grid_idx`
* `%Design Config Grid index has been rebuilt%`） as `design_config_grid_idx`
* `%Product Categories index has been rebuilt%`） as `product_categories_idx`
* `%Product EAV index has been rebuilt%`） as `product_eav_idx`
* `%Product Price index has been rebuilt%`） as `product_price_idx`
* `%Stock index has been rebuilt%`） as `stock_idx`
* `%Inventory index has been rebuilt successfully%`） as `inventory_idx`
* `%Product/Target Rule index has been rebuilt successfully%`） as `prod_target_rule_idx`
* `%Sales Rule index has been rebuilt successfully%`） as `sales_rule_idx`


## [!UICONTROL catalogsearch index table(s)]

![ カタログ検索インデックス テーブル ](../../assets/tools/observation-for-adobe-commerce/indexing-tab-3.jpg)

**[!UICONTROL catalogsearch index table(s)]** のフレームは、選択した期間のカタログ検索インデックステーブルを調べます。 このクエリは、テーブル名に `%catalogsearch%` が含まれるテーブルに対するデータストア操作の時間を調べます。

## [!UICONTROL product index table(s)]

![ 製品インデックステーブル ](../../assets/tools/observation-for-adobe-commerce/indexing-tab-4.jpg)

**[!UICONTROL product index table(s)]** フレームは、選択した期間の製品インデックステーブルを調べます。 このクエリは、テーブル名に `%product%` が含まれるテーブルに対するデータストア操作の時間を調べます。
