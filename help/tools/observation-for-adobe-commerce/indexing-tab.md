---
title: 「[!UICONTROL Indexing]」タブ
description: '[!DNL Observation for Adobe Commerce]の「[!UICONTROL Indexing]」タブについて説明します。'
exl-id: c7e123b7-2d0c-49d4-9f76-128939dc02a8
feature: Configuration, Observability
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 4239b8a6-e74f-567d-a7a5-b98b9ead0ea4
    internal-label: Observability
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
source-wordcount: '177'
ht-degree: 0%
---
# 「[!UICONTROL Indexing]」タブ

「**[!UICONTROL Indexing]**」タブは、インデックス作成に関する問題を説明し、潜在的な原因を特定しようとします。

## [!UICONTROL Core index invalidated]

![&#x200B; コアインデックスが無効になりました](../../assets/tools/observation-for-adobe-commerce/indexing-tab-1.jpg)

**[!UICONTROL Core index invalidated]** フレームは、選択した期間のインデックス無効化を確認します。 他のリソースを多く使用する[!DNL crons]と同時にインデックス作成を行う場合、サイト リソースに大きな負荷がかかります。

* `%Catalog Product Rule indexer has been invalidated%`）を`catalog_product_rule_idx_reset`として
* `%Catalog Rule Product indexer has been invalidated%`）を`catalog_rule_product_idx_reset`として
* `%Catalog Search indexer has been invalidated%`）を`catalog_search_idx_reset`として
* `%Category Products indexer has been invalidated%`）を`category_products_idx_reset`として
* `%Customer Grid indexer has been invalidated%`）を`customer_grid_idx_reset`として
* `%Design Config Grid indexer has been invalidated%`）を`design_config_grid_idx_`として
* `%Product Categories indexer has been invalidated%`）を`product_categories_idx_reset`として
* `%Product EAV indexer has been invalidated%`）を`product_eav_idx_reset`として
* `%Product Price indexer has been invalidated%`）を`product_price_idx_reset`として
* `%Stock indexer has been invalidated%`）を`stock_idx_reset`として
* `%Inventory indexer has been invalidated%`）を`inventory_idx_reset`として
* `%Inventory indexer has been invalidated%`）を`inventory_idx_reset`として
* `%Sales Rule indexer has been invalidated%`）を`sales_rule_idx_reset`として

## [!UICONTROL Core index rebuilds]

![&#x200B; コアインデックスの再構築](../../assets/tools/observation-for-adobe-commerce/indexing-tab-2.jpg)

**[!UICONTROL Core index rebuilds]** フレームは、選択した時間枠でコアインデックスの再構築を確認します。 インデックスの再構築の完了を示すために、ログから解析される文字列を以下に示します。

* `%Catalog Product Rule index has been rebuilt%`）を`catalog_product_rule_idx`として
* `%Catalog Rule Product index has been rebuilt%`）を`catalog_rule_product_idx`として
* `%Catalog Search index has been rebuilt%`）を`catalog_search_idx`として
* `%Category Products index has been rebuilt successfully%`）を`category_products_idx`として
* `%Customer Grid index has been rebuilt%`）を`customer_grid_idx`として
* `%Design Config Grid index has been rebuilt%`）を`design_config_grid_idx`として
* `%Product Categories index has been rebuilt%`）を`product_categories_idx`として
* `%Product EAV index has been rebuilt%`）を`product_eav_idx`として
* `%Product Price index has been rebuilt%`）を`product_price_idx`として
* `%Stock index has been rebuilt%`）を`stock_idx`として
* `%Inventory index has been rebuilt successfully%`）を`inventory_idx`として
* `%Product/Target Rule index has been rebuilt successfully%`）を`prod_target_rule_idx`として
* `%Sales Rule index has been rebuilt successfully%`）を`sales_rule_idx`として


## [!UICONTROL catalogsearch index table(s)]

![&#x200B; カタログ検索インデックス テーブル &#x200B;](../../assets/tools/observation-for-adobe-commerce/indexing-tab-3.jpg)

**[!UICONTROL catalogsearch index table(s)]** フレームは、選択した時間枠のカタログ検索インデックス テーブルを参照します。 このクエリは、テーブル名に`%catalogsearch%`が含まれるテーブルに対するデータストア操作の期間を調べています。

## [!UICONTROL product index table(s)]

![製品インデックステーブル &#x200B;](../../assets/tools/observation-for-adobe-commerce/indexing-tab-4.jpg)

**[!UICONTROL product index table(s)]** フレームは、選択した期間の製品インデックステーブルを参照します。 このクエリは、テーブル名に`%product%`が含まれるテーブルに対するデータストア操作の期間を調べています。
