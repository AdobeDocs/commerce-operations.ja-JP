---
title: カタログ設定パスの参照
description: カタログ設定値の一覧を参照してください。
source-git-commit: bd1bf6edd131ec93902246e95ce857b509f2a619
workflow-type: tm+mt
source-wordcount: '827'
ht-degree: 0%

---


# カタログ設定パスの参照

この節では、以下の管理で使用できる変数名と設定パスを示します。 **ストア** /設定/ **設定** > **カタログ**.

この [`magento app:config:dump` command](../cli/export-configuration.md) は、これらの値を共有設定ファイルに書き込みます。 `app/etc/config.php`（ソース管理下に置く必要があります） オプションで設定を上書きしたり、機密設定を設定したりするには、 [環境変数を使用して設定を上書きする](override-config-settings.md#environment-variables). このトピックでは、 _not_ リスト [機密性の高いシステム固有の値](config-reference-sens.md).

## カタログパス

これらの設定値は、 **ストア** /設定/ **設定** > **カタログ** > **カタログ**.

| 名前 | 設定パス | コマースのみ？ |
|--------------|--------------|--------------|
| SKU のマスク | `catalog/fields_masks/sku` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メタタイトルのマスク | `catalog/fields_masks/meta_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メタキーワードのマスク | `catalog/fields_masks/meta_keyword` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メタ説明のマスク | `catalog/fields_masks/meta_description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| リストモード | `catalog/frontend/list_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| グリッドの許容値の 1 ページあたりの製品数 | `catalog/frontend/grid_per_page_values` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| グリッドのデフォルト値の 1 ページあたりの製品 | `catalog/frontend/grid_per_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 許可された値リストの 1 ページあたりの製品数 | `catalog/frontend/list_per_page_values` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| リストの 1 ページあたりの製品のデフォルト値 | `catalog/frontend/list_per_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 製品リストの並べ替え基準 | `catalog/frontend/default_sort_by` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 1 ページのすべての製品を許可 | `catalog/frontend/list_allow_all` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| フラットカタログカテゴリを使用 | `catalog/frontend/flat_catalog_category` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| フラットカタログ製品を使用 | `catalog/frontend/flat_catalog_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 製品ごとのスウォッチ | `catalog/frontend/swatches_per_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ゲストによるレビュー書き込みを許可 | `catalog/review/allow_guest` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 製品価格が変更されたときにアラートを許可 | `catalog/productalert/allow_price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 価格アラートメールテンプレート | `catalog/productalert/email_price_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 製品が在庫に戻ったときにアラートを許可 | `catalog/productalert/allow_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在庫アラートメールテンプレート | `catalog/productalert/email_stock_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| アラートメール送信者 | `catalog/productalert/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頻度 | `catalog/productalert_cron/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 開始時間 | `catalog/productalert_cron/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| エラーメール送信者 | `catalog/productalert_cron/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| エラーメールテンプレート | `catalog/productalert_cron/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 現在の項目で表示 | `catalog/recently_products/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最近表示されたデフォルトの製品数 | `catalog/recently_products/viewed_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最近比較されたデフォルトの製品数 | `catalog/recently_products/compared_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自動開始の基本ビデオ | `catalog/product_video/play_if_base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 関連ビデオを表示 | `catalog/product_video/show_related` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ビデオを自動的に再起動 | `catalog/product_video/video_auto_restart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| カタログ価格範囲 | `catalog/price/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デフォルトの製品価格 | `catalog/price/default_product_price` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 製品数を表示 | `catalog/layered_navigation/display_product_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 価格ナビゲーションのステップの計算 | `catalog/layered_navigation/price_range_calculation` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デフォルトの価格ナビゲーション手順 | `catalog/layered_navigation/price_range_step` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 価格間隔を 1 つの価格として表示 | `catalog/layered_navigation/one_price_interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 価格間隔の最大数 | `catalog/layered_navigation/price_range_max_intervals` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 間隔の除算の制限 | `catalog/layered_navigation/interval_division_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大深さ | `catalog/navigation/max_depth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クエリの長さの最小値 | `catalog/search/min_query_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クエリの最大長 | `catalog/search/max_query_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 検索エンジン | `catalog/search/engine` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Solr サーバーのタイムアウト | `catalog/search/solr_server_timeout` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| インデックスモード | `catalog/search/engine_commit_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 検索候補を有効にする | `catalog/search/search_suggestion_enabled` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 検索候補数 | `catalog/search/search_suggestion_count` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 各提案の結果数を表示 | `catalog/search/search_suggestion_count_results_enabled` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 検索Recommendationsの有効化 | `catalog/search/search_recommendations_enabled` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 検索Recommendations数 | `catalog/search/search_recommendations_count` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 各レコメンデーションの結果数を表示 | `catalog/search/search_recommendations_count_results_enabled` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 一致する最小キーワード数 | `catalog/search/minimum_should_match` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| よく読まれる検索語句 | `catalog/seo/search_terms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 製品 URL サフィックス | `catalog/seo/product_url_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| カテゴリ URL サフィックス | `catalog/seo/category_url_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 製品 URL にカテゴリパスを使用 | `catalog/seo/product_use_categories` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| URL キーが変更された場合の URL の永続的なリダイレクトの作成 | `catalog/seo/save_rewrites_history` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ページタイトル区切り記号 | `catalog/seo/title_separator` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| カテゴリに正規リンクメタタグを使用する | `catalog/seo/category_canonical_tag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 製品に正規リンクメタタグを使用する | `catalog/seo/product_canonical_tag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効にする | `catalog/magento_catalogpermissions/enabled` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 閲覧カテゴリを許可 | `catalog/magento_catalogpermissions/grant_catalog_category_view` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 顧客グループ | `catalog/magento_catalogpermissions/grant_catalog_category_view_groups` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| ランディングページ | `catalog/magento_catalogpermissions/restricted_landing_page` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 製品価格を表示 | `catalog/magento_catalogpermissions/grant_catalog_product_price` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 顧客グループ | `catalog/magento_catalogpermissions/grant_catalog_product_price_groups` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 買い物かごへの追加を許可 | `catalog/magento_catalogpermissions/grant_checkout_items` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 顧客グループ | `catalog/magento_catalogpermissions/grant_checkout_items_groups` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| カタログ検索の許可を解除 | `catalog/magento_catalogpermissions/deny_catalog_search` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| ダウンロードを有効にするための注文項目のステータス | `catalog/downloadable/order_item_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デフォルトの最大ダウンロード数 | `catalog/downloadable/downloads_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 共有可能 | `catalog/downloadable/shareable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デフォルトのサンプルタイトル | `catalog/downloadable/samples_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デフォルトのリンクタイトル | `catalog/downloadable/links_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| リンクを新しいウィンドウで開く | `catalog/downloadable/links_target_new_window` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Content-Disposition を使用 | `catalog/downloadable/content_disposition` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 買い物かごにダウンロード可能な項目が含まれる場合、ゲストのチェックアウトを無効にする | `catalog/downloadable/disable_guest_checkout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| JavaScript カレンダーを使用 | `catalog/custom_options/use_calendar` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 日付フィールドの注文 | `catalog/custom_options/date_fields_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 時間形式 | `catalog/custom_options/time_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 年の範囲 | `catalog/custom_options/year_range` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| カタログイベント機能の有効化 | `catalog/magento_catalogevent/enabled` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| Storefront でカタログイベントウィジェットを有効にする | `catalog/magento_catalogevent/lister_output` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| イベントスライダーウィジェットに表示するイベント数 | `catalog/magento_catalogevent/lister_widget_limit` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| イベントスライダーウィジェットでクリックごとにスクロールするイベント | `catalog/magento_catalogevent/lister_widget_scroll` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 関連製品リストの製品の最大数 | `catalog/magento_targetrule/related_position_limit` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 関連製品を表示 | `catalog/magento_targetrule/related_position_behavior` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 関連製品リストの製品の回転モード | `catalog/magento_targetrule/related_rotation_mode` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| クロス販売製品リストの製品の最大数 | `catalog/magento_targetrule/crosssell_position_limit` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| クロス販売製品を表示 | `catalog/magento_targetrule/crosssell_position_behavior` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| クロス販売製品リストの製品のローテーションモード | `catalog/magento_targetrule/crosssell_rotation_mode` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| アップセル製品リストの製品の最大数 | `catalog/magento_targetrule/upsell_position_limit` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| アップセル製品を表示 | `catalog/magento_targetrule/upsell_position_behavior` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| アップセル製品リストの製品のローテーションモード | `catalog/magento_targetrule/upsell_rotation_mode` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |

{style=&quot;table-layout:auto&quot;}

## 在庫パス

これらの設定値は、 **ストア** /設定/ **設定** > **カタログ** > **在庫**.

| 名前 | 設定パス | コマースのみ？ |
|--------------|--------------|--------------|
| 注文が行われたときに在庫を減らす | `cataloginventory/options/can_subtract` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 注文がキャンセルされたときに品目のステータスを在庫に設定 | `cataloginventory/options/can_back_in_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在庫切れの製品を表示 | `cataloginventory/options/show_out_of_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| X の左しきい値のみ | `cataloginventory/options/stock_threshold_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ストアフロントでの製品の在庫状況の表示 | `cataloginventory/options/display_product_stock_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| カタログと同期 | `cataloginventory/options/synchronize_with_catalog` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 在庫の管理 | `cataloginventory/item_options/manage_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| バックオーダー | `cataloginventory/item_options/backorders` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 遅延在庫更新を使用 | `cataloginventory/item_options/use_deferred_stock_update` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 買い物かごで許可される最大数量 | `cataloginventory/item_options/max_sale_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在庫切れしきい値 | `cataloginventory/item_options/min_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 買い物かごで許可される最小数量 | `cataloginventory/item_options/min_sale_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 次の数量の通知 | `cataloginventory/item_options/notify_stock_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 数量増分の有効化 | `cataloginventory/item_options/enable_qty_increments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 数量増分 | `cataloginventory/item_options/qty_increments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットメモ項目を在庫に自動的に返却 | `cataloginventory/item_options/auto_return` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 非同期で実行 | `cataloginventory/bulk_operations/async` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 非同期バッチサイズ | `cataloginventory/bulk_operations/batch_size` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| プロバイダー | `cataloginventory/source_selection_distance_based/provider` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 計算モード | `cataloginventory/source_selection_distance_based_google/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 値 | `cataloginventory/source_selection_distance_based_google/value` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Visual Merchandiser のパス

これらの設定値は、 **ストア** /設定/ **設定** > **カタログ** > **Visual Merchandiser**.

| 名前 | 設定パス | コマースのみ？ |
|--------------|--------------|--------------|
| カテゴリルールに表示される属性 | `visualmerchandiser/options/smart_attributes` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 最小在庫しきい値 | `visualmerchandiser/options/minimum_stock_threshold` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 色属性コード | `visualmerchandiser/options/color_attribute_code` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 色の順序 | `visualmerchandiser/options/color_order` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |

{style=&quot;table-layout:auto&quot;}

## XML サイトマップのパス

これらの設定値は、 **ストア** /設定/ **設定** > **カタログ** > **XML サイトマップ**.

| 名前 | 設定パス | コマースのみ？ |
|--------------|--------------|--------------|
| 頻度 | `sitemap/category/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 優先度 | `sitemap/category/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頻度 | `sitemap/product/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 優先度 | `sitemap/product/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| サイトマップに画像を追加 | `sitemap/product/image_include` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頻度 | `sitemap/page/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 優先度 | `sitemap/page/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効 | `sitemap/generate/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 開始時間 | `sitemap/generate/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頻度 | `sitemap/generate/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| エラーメール送信者 | `sitemap/generate/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| エラーメールテンプレート | `sitemap/generate/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ファイルあたりの URL の最大数 | `sitemap/limit/max_lines` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大ファイルサイズ | `sitemap/limit/max_file_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Robots.txt への送信を有効にする | `sitemap/search_engines/submission_robots` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## RSS フィードのパス

これらの設定値は、 **ストア** /設定/ **設定** > **カタログ** > **RSS フィード**.

| 名前 | 設定パス | コマースのみ？ |
|--------------|--------------|--------------|
| RSS を有効にする | `rss/config/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| RSS を有効にする | `rss/wishlist/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新製品 | `rss/catalog/new` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特別製品 | `rss/catalog/special` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クーポン/割引 | `rss/catalog/discounts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| トップレベルカテゴリ | `rss/catalog/category` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顧客の注文ステータスの通知 | `rss/order/status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## 友達への電子メールのパス

これらの設定値は、 **ストア** /設定/ **設定** > **カタログ** > **友達への電子メール**.

| 名前 | 設定パス | コマースのみ？ |
|--------------|--------------|--------------|
| 有効 | `sendfriend/email/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メールテンプレートを選択 | `sendfriend/email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ゲストを許可 | `sendfriend/email/allow_guest` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大受信者数 | `sendfriend/email/max_recipients` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 1 時間で送信される最大製品数 | `sendfriend/email/max_per_hour` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送信制限 | `sendfriend/email/check_by` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}
