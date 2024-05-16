---
title: この [!UICONTROL Indexing] タブ
description: について説明します [!UICONTROL Indexing] タブ / [!DNL Observation for Adobe Commerce].
exl-id: c7e123b7-2d0c-49d4-9f76-128939dc02a8
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# この [!UICONTROL Indexing] タブ

この **[!UICONTROL Indexing]** tab は、インデックス作成に関する問題の説明と潜在的な原因の特定を試みます。

## [!UICONTROL Core index invalidated]

![コアインデックスが無効です](../../assets/tools/observation-for-adobe-commerce/indexing-tab-1.jpg)

この **[!UICONTROL Core index invalidated]** フレームでは、選択した期間でのインデックス作成の無効化を確認します。 インデックス作成が、その他のリソースを大量に消費するタイミングで行われている場合 [!DNL crons]を使用すると、サイトリソースに大きな負荷がかかります。

* `%Catalog Product Rule indexer has been invalidated%`）を次として `catalog_product_rule_idx_reset`
* `%Catalog Rule Product indexer has been invalidated%`）を次として `catalog_rule_product_idx_reset`
* `%Catalog Search indexer has been invalidated%`）を次として `catalog_search_idx_reset`
* `%Category Products indexer has been invalidated%`）を次として `category_products_idx_reset`
* `%Customer Grid indexer has been invalidated%`）を次として `customer_grid_idx_reset`
* `%Design Config Grid indexer has been invalidated%`）を次として `design_config_grid_idx_`
* `%Product Categories indexer has been invalidated%`）を次として `product_categories_idx_reset`
* `%Product EAV indexer has been invalidated%`）を次として `product_eav_idx_reset`
* `%Product Price indexer has been invalidated%`）を次として `product_price_idx_reset`
* `%Stock indexer has been invalidated%`）を次として `stock_idx_reset`
* `%Inventory indexer has been invalidated%`）を次として `inventory_idx_reset`
* `%Inventory indexer has been invalidated%`）を次として `inventory_idx_reset`
* `%Sales Rule indexer has been invalidated%`）を次として `sales_rule_idx_reset`

## [!UICONTROL Core index rebuilds]

![コアインデックスの再構築](../../assets/tools/observation-for-adobe-commerce/indexing-tab-2.jpg)

この **[!UICONTROL Core index rebuilds]** フレームは、選択した期間のコアインデックス再構築を確認します。 次に、インデックスの再構築完了を示すために、ログから解析される文字列を示します。

* `%Catalog Product Rule index has been rebuilt%`）を次として `catalog_product_rule_idx`
* `%Catalog Rule Product index has been rebuilt%`）を次として `catalog_rule_product_idx`
* `%Catalog Search index has been rebuilt%`）を次として `catalog_search_idx`
* `%Category Products index has been rebuilt successfully%`）を次として `category_products_idx`
* `%Customer Grid index has been rebuilt%`）を次として `customer_grid_idx`
* `%Design Config Grid index has been rebuilt%`）を次として `design_config_grid_idx`
* `%Product Categories index has been rebuilt%`）を次として `product_categories_idx`
* `%Product EAV index has been rebuilt%`）を次として `product_eav_idx`
* `%Product Price index has been rebuilt%`）を次として `product_price_idx`
* `%Stock index has been rebuilt%`）を次として `stock_idx`
* `%Inventory index has been rebuilt successfully%`）を次として `inventory_idx`
* `%Product/Target Rule index has been rebuilt successfully%`）を次として `prod_target_rule_idx`
* `%Sales Rule index has been rebuilt successfully%`）を次として `sales_rule_idx`


## [!UICONTROL catalogsearch index table(s)]

![catalogsearch インデックス テーブル](../../assets/tools/observation-for-adobe-commerce/indexing-tab-3.jpg)

この **[!UICONTROL catalogsearch index table(s)]** frame は、選択した期間のカタログ検索インデックステーブルを調べます。 このクエリは、を含んだテーブルに対するデータストア操作の時間を調べます。 `%catalogsearch%` テーブル名で。

## [!UICONTROL product index table(s)]

![製品インデックステーブル](../../assets/tools/observation-for-adobe-commerce/indexing-tab-4.jpg)

この **[!UICONTROL product index table(s)]** フレームは、選択した期間の製品インデックステーブルを調べます。 このクエリは、を含んだテーブルに対するデータストア操作の時間を調べます。 `%product%` テーブル名で。
