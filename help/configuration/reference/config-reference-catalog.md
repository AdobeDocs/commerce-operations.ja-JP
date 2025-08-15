---
title: カタログ設定パスのリファレンス
description: カタログ設定値のリストを参照します。
feature: Configuration, Catalog Management
exl-id: 19451443-228e-437d-a3eb-7dc968b9fb0d
source-git-commit: 47bda51cdcab964c37d9f652d467d69d795d8641
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 0%

---

# カタログ設定パスのリファレンス

この節では、**ストア**/設定/**設定**/**カタログ** の管理でオプションに使用できる変数名と設定パスを示します。

[`magento app:config:dump` コマンドは ](../cli/export-configuration.md) これらの値をソース管理にある共有構成ファイル `app/etc/config.php` に書き込みます。 任意の構成設定を上書きしたり、重要な設定を指定したりするには、[ 環境変数を使用して構成設定を上書き ](override-config-settings.md#environment-variables) を参照してください。 このトピックでは _機密の値とシステム固有の値_ は [ 表示されません ](config-reference-sens.md)。

## カタログパス

これらの設定値は、管理者の **ストア**/設定/**設定**/**カタログ**/**カタログ** で使用できます。

| 名前 | 設定パス | Commerceのみ？ |
|--------------|--------------|--------------|
| SKU のマスク | `catalog/fields_masks/sku` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メタタイトルのマスク | `catalog/fields_masks/meta_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メタキーワードのマスク | `catalog/fields_masks/meta_keyword` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メタ説明のマスク | `catalog/fields_masks/meta_description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| リストモード | `catalog/frontend/list_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| グリッド許容値の 1 ページあたりの製品数 | `catalog/frontend/grid_per_page_values` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| グリッドのデフォルト値の 1 ページあたりの製品数 | `catalog/frontend/grid_per_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| リスト許可値のページあたりの製品数 | `catalog/frontend/list_per_page_values` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| リストの 1 ページあたりの製品数のデフォルト値 | `catalog/frontend/list_per_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 商品リストの並べ替え基準 | `catalog/frontend/default_sort_by` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 1 ページにすべての製品を許可 | `catalog/frontend/list_allow_all` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| フラット カタログ カテゴリを使用 | `catalog/frontend/flat_catalog_category` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| フラットカタログ製品を使用 | `catalog/frontend/flat_catalog_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 製品ごとのスウォッチ | `catalog/frontend/swatches_per_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ゲストがレビューを書くことを許可 | `catalog/review/allow_guest` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 製品価格の変更時にアラートを許可 | `catalog/productalert/allow_price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 価格アラートメールテンプレート | `catalog/productalert/email_price_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 製品が再入荷したときにアラートを表示する | `catalog/productalert/allow_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在庫アラートメールテンプレート | `catalog/productalert/email_stock_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| アラートメールの送信者 | `catalog/productalert/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頻度 | `catalog/productalert_cron/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 開始時刻 | `catalog/productalert_cron/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| エラーのメール送信者 | `catalog/productalert_cron/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| エラーメールテンプレート | `catalog/productalert_cron/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 現在のを表示 | `catalog/recently_products/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デフォルトの最近表示された製品数 | `catalog/recently_products/viewed_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デフォルトの最近比較された製品数 | `catalog/recently_products/compared_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自動開始の基本ビデオ | `catalog/product_video/play_if_base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 関連ビデオを表示 | `catalog/product_video/show_related` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ビデオを自動再起動 | `catalog/product_video/video_auto_restart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| カタログの価格スコープ | `catalog/price/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デフォルトの製品価格 | `catalog/price/default_product_price` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 製品数を表示 | `catalog/layered_navigation/display_product_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 価格ナビゲーション・ステップの計算 | `catalog/layered_navigation/price_range_calculation` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デフォルトの価格ナビゲーションステップ | `catalog/layered_navigation/price_range_step` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 価格間隔を 1 つの価格として表示 | `catalog/layered_navigation/one_price_interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 価格間隔の最大数 | `catalog/layered_navigation/price_range_max_intervals` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 間隔の分割制限 | `catalog/layered_navigation/interval_division_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大深度 | `catalog/navigation/max_depth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小クエリ長 | `catalog/search/min_query_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クエリの最大長 | `catalog/search/max_query_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 検索エンジン | `catalog/search/engine` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Solr Server Timeout | `catalog/search/solr_server_timeout` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| インデックス作成モード | `catalog/search/engine_commit_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 検索候補を有効にする | `catalog/search/search_suggestion_enabled` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 検索候補の数 | `catalog/search/search_suggestion_count` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 各提案の結果数を表示 | `catalog/search/search_suggestion_count_results_enabled` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 検索レコメンデーションを有効にする | `catalog/search/search_recommendations_enabled` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| お勧め数を検索 | `catalog/search/search_recommendations_count` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 各レコメンデーションの結果数を表示 | `catalog/search/search_recommendations_count_results_enabled` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 一致する最小用語 | `catalog/search/minimum_should_match` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 「カテゴリ/製品」 URL の書き換えを生成 | `catalog/seo/generate_category_product_rewrites` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| よく使用される検索用語 | `catalog/seo/search_terms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 製品 URL サフィックス | `catalog/seo/product_url_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| カテゴリ URL サフィックス | `catalog/seo/category_url_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 製品 URL にカテゴリパスを使用 | `catalog/seo/product_use_categories` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| URL キーが変更された場合に URL の永続的なリダイレクトを作成 | `catalog/seo/save_rewrites_history` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ページタイトルセパレーター | `catalog/seo/title_separator` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| カテゴリに正規リンクメタタグを使用 | `catalog/seo/category_canonical_tag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 製品に正規リンクメタタグを使用 | `catalog/seo/product_canonical_tag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enable （有効） | `catalog/magento_catalogpermissions/enabled` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 閲覧を許可カテゴリ | `catalog/magento_catalogpermissions/grant_catalog_category_view` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 顧客グループ | `catalog/magento_catalogpermissions/grant_catalog_category_view_groups` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| ランディングページ | `catalog/magento_catalogpermissions/restricted_landing_page` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 製品価格を表示 | `catalog/magento_catalogpermissions/grant_catalog_product_price` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 顧客グループ | `catalog/magento_catalogpermissions/grant_catalog_product_price_groups` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| カートへの追加を許可 | `catalog/magento_catalogpermissions/grant_checkout_items` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 顧客グループ | `catalog/magento_catalogpermissions/grant_checkout_items_groups` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| カタログ検索を許可しない基準 | `catalog/magento_catalogpermissions/deny_catalog_search` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| ダウンロードを有効にするアイテムの状態を注文する | `catalog/downloadable/order_item_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デフォルトの最大ダウンロード数 | `catalog/downloadable/downloads_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 共有可能 | `catalog/downloadable/shareable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デフォルトのサンプルタイトル | `catalog/downloadable/samples_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 既定のリンク タイトル | `catalog/downloadable/links_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| リンクを新しいウィンドウで開く | `catalog/downloadable/links_target_new_window` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Content-Disposition の使用 | `catalog/downloadable/content_disposition` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 買い物かごにダウンロード可能なアイテムが含まれている場合、ゲストのチェックアウトを無効にする | `catalog/downloadable/disable_guest_checkout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| JavaScript カレンダーの使用 | `catalog/custom_options/use_calendar` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 日付フィールドの順序 | `catalog/custom_options/date_fields_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 時刻の形式 | `catalog/custom_options/time_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 年の範囲 | `catalog/custom_options/year_range` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| カタログイベント機能の有効化 | `catalog/magento_catalogevent/enabled` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| ストアフロントでのカタログイベントウィジェットの有効化 | `catalog/magento_catalogevent/lister_output` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| イベントスライダーウィジェットに表示されるイベントの数 | `catalog/magento_catalogevent/lister_widget_limit` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| イベントスライダーウィジェットでクリックごとにスクロールするイベント | `catalog/magento_catalogevent/lister_widget_scroll` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 関連製品リストの最大製品数 | `catalog/magento_targetrule/related_position_limit` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 関連製品を表示 | `catalog/magento_targetrule/related_position_behavior` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 関連商品リスト内の商品のローテーションモード | `catalog/magento_targetrule/related_rotation_mode` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| クロスセル製品リストの最大製品数 | `catalog/magento_targetrule/crosssell_position_limit` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| クロスセル製品を表示 | `catalog/magento_targetrule/crosssell_position_behavior` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| クロスセル製品リスト内の製品のローテーションモード | `catalog/magento_targetrule/crosssell_rotation_mode` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| アップセル製品リストの最大製品数 | `catalog/magento_targetrule/upsell_position_limit` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| アップセル製品の表示 | `catalog/magento_targetrule/upsell_position_behavior` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| アップセル製品リスト内の製品のローテーションモード | `catalog/magento_targetrule/upsell_rotation_mode` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## 在庫パス

これらの設定値は、管理者の **ストア**/設定/**設定**/**カタログ**/**在庫** で使用できます。

| 名前 | 設定パス | Commerceのみ？ |
|--------------|--------------|--------------|
| 注文時に在庫を減らす | `cataloginventory/options/can_subtract` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 注文がキャンセルされたときに品目の状態を在庫に設定します | `cataloginventory/options/can_back_in_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在庫切れ商品の表示 | `cataloginventory/options/show_out_of_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| X 左しきい値のみ | `cataloginventory/options/stock_threshold_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 店頭で商品の在庫状況を表示する | `cataloginventory/options/display_product_stock_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| カタログと同期 | `cataloginventory/options/synchronize_with_catalog` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 在庫の管理 | `cataloginventory/item_options/manage_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| バックオーダー | `cataloginventory/item_options/backorders` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 繰延在庫更新を使用 | `cataloginventory/item_options/use_deferred_stock_update` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 買い物かごで許可される最大数量 | `cataloginventory/item_options/max_sale_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在庫切れのしきい値 | `cataloginventory/item_options/min_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 買い物かごで許可される最小数量 | `cataloginventory/item_options/min_sale_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 以下の数量を通知 | `cataloginventory/item_options/notify_stock_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 数量増分を有効にする | `cataloginventory/item_options/enable_qty_increments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 数量の増分 | `cataloginventory/item_options/qty_increments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジット・メモ品目を自動的に在庫に戻す | `cataloginventory/item_options/auto_return` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 非同期で実行 | `cataloginventory/bulk_operations/async` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 非同期バッチサイズ | `cataloginventory/bulk_operations/batch_size` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| プロバイダ | `cataloginventory/source_selection_distance_based/provider` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 計算モード | `cataloginventory/source_selection_distance_based_google/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 値 | `cataloginventory/source_selection_distance_based_google/value` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## ビジュアルマーチャンダイザーパス

[!BADGE PaaS のみ &#x200B;]{type=Informative url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce on Cloud プロジェクト（Adobeが管理する PaaS インフラストラクチャ）およびオンプレミスプロジェクトにのみ適用されます。"}

これらの設定値は、管理者の **ストア**/設定/**設定**/**カタログ**/**ビジュアルマーチャンダイザー** で使用できます。

| 名前 | 設定パス | Commerceのみ？ |
|--------------|--------------|--------------|
| カテゴリルールに表示される属性 | `visualmerchandiser/options/smart_attributes` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 最小在庫しきい値 | `visualmerchandiser/options/minimum_stock_threshold` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| カラー属性コード | `visualmerchandiser/options/color_attribute_code` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 色の順序 | `visualmerchandiser/options/color_order` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## XML サイトマップのパス

これらの設定値は、管理者の **ストア**/設定/**設定**/**カタログ**/**XML サイトマップ** で使用できます。

| 名前 | 設定パス | Commerceのみ？ |
|--------------|--------------|--------------|
| 頻度 | `sitemap/category/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 優先度 | `sitemap/category/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頻度 | `sitemap/product/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 優先度 | `sitemap/product/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| サイトマップへの画像の追加 | `sitemap/product/image_include` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頻度 | `sitemap/page/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 優先度 | `sitemap/page/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `sitemap/generate/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 開始時刻 | `sitemap/generate/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頻度 | `sitemap/generate/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| エラーのメール送信者 | `sitemap/generate/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| エラーメールテンプレート | `sitemap/generate/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ファイルあたりの最大 URL 数 | `sitemap/limit/max_lines` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大ファイルサイズ | `sitemap/limit/max_file_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Robots.txt への送信を有効にする | `sitemap/search_engines/submission_robots` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## RSS フィードのパス

これらの設定値は、管理者の **ストア**/設定/**設定**/**カタログ**/**RSS フィード** で利用できます。

| 名前 | 設定パス | Commerceのみ？ |
|--------------|--------------|--------------|
| RSS を有効にする | `rss/config/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| RSS を有効にする | `rss/wishlist/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新製品 | `rss/catalog/new` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特産品 | `rss/catalog/special` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クーポン/割引 | `rss/catalog/discounts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| トップレベルカテゴリ | `rss/catalog/category` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顧客注文ステータス通知 | `rss/order/status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 友人へのメールのパス

これらの設定値は、管理者の **ストア**/設定/**設定**/**カタログ**/**友達にメールで送信** で利用できます。

| 名前 | 設定パス | Commerceのみ？ |
|--------------|--------------|--------------|
| Enabled | `sendfriend/email/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メールテンプレートを選択 | `sendfriend/email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ゲストに許可 | `sendfriend/email/allow_guest` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大受信者数 | `sendfriend/email/max_recipients` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 1 時間以内に送信された最大製品数 | `sendfriend/email/max_per_hour` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送信者を制限 | `sendfriend/email/check_by` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
