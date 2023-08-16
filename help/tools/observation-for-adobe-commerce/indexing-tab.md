---
title: The [!UICONTROL Indexing] タブ
description: 詳しくは、 [!UICONTROL Indexing] タブ [!DNL Observation for Adobe Commerce].
exl-id: c7e123b7-2d0c-49d4-9f76-128939dc02a8
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# The [!UICONTROL Indexing] タブ

The **[!UICONTROL Indexing]** tab は、インデックス作成に関する問題を説明し、潜在的な原因を特定しようとします。

## [!UICONTROL Core index invalidated]

![コアインデックスが無効化されました](../../assets/tools/observation-for-adobe-commerce/indexing-tab-1.jpg)

The **[!UICONTROL Core index invalidated]** frame は、選択した期間にわたるインデックス作成の無効化を調べます。 インデックス作成が他のリソースを集中的に消費する場合と同時におこなわれる場合 [!DNL crons]の場合、サイトのリソースに大きな負荷がかかります。

* `%Catalog Product Rule indexer has been invalidated%`) として `catalog_product_rule_idx_reset`
* `%Catalog Rule Product indexer has been invalidated%`) として `catalog_rule_product_idx_reset`
* `%Catalog Search indexer has been invalidated%`) として `catalog_search_idx_reset`
* `%Category Products indexer has been invalidated%`) として `category_products_idx_reset`
* `%Customer Grid indexer has been invalidated%`) として `customer_grid_idx_reset`
* `%Design Config Grid indexer has been invalidated%`) として `design_config_grid_idx_`
* `%Product Categories indexer has been invalidated%`) として `product_categories_idx_reset`
* `%Product EAV indexer has been invalidated%`) として `product_eav_idx_reset`
* `%Product Price indexer has been invalidated%`) として `product_price_idx_reset`
* `%Stock indexer has been invalidated%`) として `stock_idx_reset`
* `%Inventory indexer has been invalidated%`) として `inventory_idx_reset`
* `%Inventory indexer has been invalidated%`) として `inventory_idx_reset`
* `%Sales Rule indexer has been invalidated%`) として `sales_rule_idx_reset`

## [!UICONTROL Core index rebuilds]

![コアインデックスの再構築](../../assets/tools/observation-for-adobe-commerce/indexing-tab-2.jpg)

The **[!UICONTROL Core index rebuilds]** frame は、選択した期間にわたるコアインデックスの再構築を調べます。 次に、インデックスの再構築が完了したことを示すためにログから解析される文字列を示します。

* `%Catalog Product Rule index has been rebuilt%`) として `catalog_product_rule_idx`
* `%Catalog Rule Product index has been rebuilt%`) として `catalog_rule_product_idx`
* `%Catalog Search index has been rebuilt%`) として `catalog_search_idx`
* `%Category Products index has been rebuilt successfully%`) として `category_products_idx`
* `%Customer Grid index has been rebuilt%`) として `customer_grid_idx`
* `%Design Config Grid index has been rebuilt%`) として `design_config_grid_idx`
* `%Product Categories index has been rebuilt%`) として `product_categories_idx`
* `%Product EAV index has been rebuilt%`) として `product_eav_idx`
* `%Product Price index has been rebuilt%`) として `product_price_idx`
* `%Stock index has been rebuilt%`) として `stock_idx`
* `%Inventory index has been rebuilt successfully%`) として `inventory_idx`
* `%Product/Target Rule index has been rebuilt successfully%`) として `prod_target_rule_idx`
* `%Sales Rule index has been rebuilt successfully%`) として `sales_rule_idx`


## [!UICONTROL catalogsearch index table(s)]

![catalogsearch インデックステーブル](../../assets/tools/observation-for-adobe-commerce/indexing-tab-3.jpg)

The **[!UICONTROL catalogsearch index table(s)]** frame は、選択した期間の catalogsearch インデックステーブルを調べます。 このクエリは、 `%catalogsearch%` 」と入力します。

## [!UICONTROL product index table(s)]

![製品インデックステーブル](../../assets/tools/observation-for-adobe-commerce/indexing-tab-4.jpg)

The **[!UICONTROL product index table(s)]** frame は、選択した期間の製品インデックステーブルを調べます。 このクエリは、 `%product%` 」と入力します。
