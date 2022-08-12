---
title: 「 [!UICONTROL Indexing] タブ"
description: 詳しくは、 [!UICONTROL Indexing] タブ [!DNL Observation for Adobe Commerce].
source-git-commit: 1f334f329b72b715afa7f3617b1ce2fb8004f816
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# この [!UICONTROL Indexing] タブ

この **[!UICONTROL Indexing]** tab は、インデックス作成に関する問題を説明し、潜在的な原因を特定しようとします。

## [!UICONTROL Core index invalidated]

![コアインデックスが無効化されました](../../assets/tools/observation-for-adobe-commerce/indexing-tab-1.jpg)

この **[!UICONTROL Core index invalidated]** frame は、選択した期間にわたるインデックス作成の無効化を調べます。 他のリソースを集中的に消費する Cron と同時にインデックス作成がおこなわれると、サイトリソースに大きな負荷がかかります。

* &#39;%Catalog 製品ルールのインデクサーが無効化されました%&#39;) (&#39;catalog_product_rule_idx_reset&#39;)
* &#39;%Catalog Rule Product Indexer が無効化されました%&#39;) (&#39;catalog_rule_product_idx_reset&#39;)
* &#39;%Catalog Search インデクサーは無効化されました%&#39;) （&#39;catalog_search_idx_reset&#39;として）
* &#39;%Category Products インデクサーが無効化されました%&#39;) (&#39;category_products_idx_reset&#39;)
* &#39;%Customer Grid インデクサーは無効化されました%&#39;) （&#39;customer_grid_idx_reset&#39;として）
* &#39;%Design Config グリッドインデクサーが無効化されました%&#39;) (&#39;design_config_grid_idx_
* &#39;%Product Categories インデクサーが無効化されました%&#39;) (&#39;product_categories_idx_reset&#39;)
* &#39;%Product EAV インデクサーが無効化されました%&#39;) &#39;product_eav_idx_reset&#39;
* &#39;%Product Price インデクサーは無効化されました%&#39;) （&#39;product_price_idx_reset&#39;として）
* &#39;%Stock インデクサーは無効化されました%&#39;) &#39;stock_idx_reset&#39;
* &#39;%Inventory インデクサーは無効化されました%&#39;) (&#39;inventory_idx_reset&#39;)
* &#39;%Inventory インデクサーは無効化されました%&#39;) (&#39;inventory_idx_reset&#39;)
* &#39;%Sales Rule インデクサは無効化されました%&#39;) (&#39;sales_rule_idx_reset&#39;)

## [!UICONTROL Core index rebuilds]

![コアインデックスの再構築](../../assets/tools/observation-for-adobe-commerce/indexing-tab-2.jpg)

この **[!UICONTROL Core index rebuilds]** frame は、選択した期間にわたるコアインデックスの再構築を調べます。 次に、インデックスの再構築が完了したことを示す文字列をログから解析します。

* &#39;%Catalog 製品規則インデックスが再構築されました%&#39;) &#39;catalog_product_rule_idx&#39;
* &#39;%Catalog Rule Product インデックスが再構築されました%&#39;) &#39;catalog_rule_product_idx&#39;
* &#39;%Catalog 検索インデックスが再構築されました%&#39;) &#39;catalog_search_idx&#39;
* &#39;%Category 製品インデックスが正常に再構築されました%&#39;) &#39;category_products_idx&#39;
* &#39;%Customer Grid インデックスが再構築されました%&#39;) &#39;customer_grid_idx&#39;
* &#39;%Design Config Grid インデックスが再構築されました%&#39;) &#39;design_config_grid_idx&#39;
* &#39;%Product Categories インデックスは再構築されました%&#39;) &#39;product_categories_idx&#39;
* &#39;%Product EAV インデックスが再構築されました%&#39;) &#39;product_eav_idx&#39;
* &#39;%Product Price index has been rebuilded%&#39;) as &#39;product_price_idx&#39;
* &#39;%Stock インデックスは再構築されました%&#39;) &#39;stock_idx&#39;
* &#39;%Inventory インデックスが正常に再構築されました%&#39;) &#39;inventory_idx&#39;
* %Product/Target ルールインデックスが正常に再構築されました%&#39;)&#39;prod_target_rule_idx&#39;
* &#39;%Sales Rule インデックスが正常に再構築されました%&#39;) &#39;sales_rule_idx&#39;


## [!UICONTROL catalogsearch index table(s)]

![catalogsearch インデックステーブル](../../assets/tools/observation-for-adobe-commerce/indexing-tab-3.jpg)

この **[!UICONTROL catalogsearch index table(s)]** frame は、選択した期間の catalogsearch インデックステーブルを調べます。 このクエリは、テーブル名に&#39;%catalogsearch%&#39;が含まれるテーブルに対するデータストア操作の期間を調べています。

## [!UICONTROL product index table(s)]

![製品インデックステーブル](../../assets/tools/observation-for-adobe-commerce/indexing-tab-4.jpg)

この **[!UICONTROL product index table(s)]** frame は、選択した期間の製品インデックステーブルを調べます。 このクエリは、テーブル名に&#39;%product%&#39;が含まれるテーブルに対するデータストア操作の期間を調べています。
