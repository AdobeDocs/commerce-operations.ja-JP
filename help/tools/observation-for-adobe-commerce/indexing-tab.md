---
title: 「 [!UICONTROL Indexing] タブ"
description: 詳しくは、 [!UICONTROL Indexing] タブ [!DNL Observation for Adobe Commerce].
source-git-commit: e6038d6f0add9d01d650914b35a1daba885fa7f8
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# この [!UICONTROL Indexing] タブ

この **[!UICONTROL Indexing]** tab は、インデックス作成に関する問題を説明し、潜在的な原因を特定しようとします。

## [!UICONTROL Core index invalidated]

![コアインデックスが無効化されました](../../assets/tools/observation-for-adobe-commerce/indexing-tab-1.jpg)

この **[!UICONTROL Core index invalidated]** frame は、選択した期間にわたるインデックス作成の無効化を調べます。 インデックス作成が他のリソースを集中的に消費する場合と同時におこなわれる場合 [!DNL crons]の場合、サイトのリソースに大きな負荷がかかります。

* `%Catalog Product Rule indexer has been invalidated%`) `catalog_product_rule_idx_reset`
* `%Catalog Rule Product indexer has been invalidated%`) `catalog_rule_product_idx_reset`
* `%Catalog Search indexer has been invalidated%`) `catalog_search_idx_reset`
* `%Category Products indexer has been invalidated%`) `category_products_idx_reset`
* `%Customer Grid indexer has been invalidated%`) `customer_grid_idx_reset`
* `%Design Config Grid indexer has been invalidated%`) `design_config_grid_idx_`
* `%Product Categories indexer has been invalidated%`) `product_categories_idx_reset`
* `%Product EAV indexer has been invalidated%`) `product_eav_idx_reset`
* `%Product Price indexer has been invalidated%`) `product_price_idx_reset`
* `%Stock indexer has been invalidated%`) `stock_idx_reset`
* `%Inventory indexer has been invalidated%`) `inventory_idx_reset`
* `%Inventory indexer has been invalidated%`) `inventory_idx_reset`
* `%Sales Rule indexer has been invalidated%`) `sales_rule_idx_reset`

## [!UICONTROL Core index rebuilds]

![コアインデックスの再構築](../../assets/tools/observation-for-adobe-commerce/indexing-tab-2.jpg)

この **[!UICONTROL Core index rebuilds]** frame は、選択した期間にわたるコアインデックスの再構築を調べます。 次に、インデックスの再構築が完了したことを示す文字列をログから解析します。

* `%Catalog Product Rule index has been rebuilt%`) `catalog_product_rule_idx`
* `%Catalog Rule Product index has been rebuilt%`) `catalog_rule_product_idx`
* `%Catalog Search index has been rebuilt%`) `catalog_search_idx`
* `%Category Products index has been rebuilt successfully%`) `category_products_idx`
* `%Customer Grid index has been rebuilt%`) `customer_grid_idx`
* `%Design Config Grid index has been rebuilt%`) `design_config_grid_idx`
* `%Product Categories index has been rebuilt%`) `product_categories_idx`
* `%Product EAV index has been rebuilt%`) `product_eav_idx`
* `%Product Price index has been rebuilt%`) `product_price_idx`
* `%Stock index has been rebuilt%`) `stock_idx`
* `%Inventory index has been rebuilt successfully%`) `inventory_idx`
* `%Product/Target Rule index has been rebuilt successfully%`) `prod_target_rule_idx`
* `%Sales Rule index has been rebuilt successfully%`) `sales_rule_idx`


## [!UICONTROL catalogsearch index table(s)]

![catalogsearch インデックステーブル](../../assets/tools/observation-for-adobe-commerce/indexing-tab-3.jpg)

この **[!UICONTROL catalogsearch index table(s)]** frame は、選択した期間の catalogsearch インデックステーブルを調べます。 このクエリは、 `%catalogsearch%` 」と入力します。

## [!UICONTROL product index table(s)]

![製品インデックステーブル](../../assets/tools/observation-for-adobe-commerce/indexing-tab-4.jpg)

この **[!UICONTROL product index table(s)]** frame は、選択した期間の製品インデックステーブルを調べます。 このクエリは、 `%product%` 」と入力します。
