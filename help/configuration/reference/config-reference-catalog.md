---
title: カタログ設定パス リファレンス
description: Adobe Commerce管理者設定のカタログ設定パスと値について説明します。 製品、カテゴリー、カタログ管理の設定オプションをご確認ください。
feature: Configuration, Catalog Management
exl-id: 19451443-228e-437d-a3eb-7dc968b9fb0d
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '900'
ht-degree: 0%

---

# カタログ設定パス リファレンス

このセクションでは、管理者の&#x200B;**ストア**/設定/**構成**/**カタログ**&#x200B;で使用できる変数名と構成パスを示します。

[`magento app:config:dump` コマンド ](../cli/export-configuration.md)は、これらの値をソース コントロールにある共有設定ファイル `app/etc/config.php`に書き込みます。 任意の構成設定を上書きする方法や、機密設定を設定する方法については、[環境変数を使用して構成設定を上書きする](override-config-settings.md#environment-variables)を参照してください。 このトピックでは、_not_&#x200B;に[機密値とシステム固有の値](config-reference-sens.md)が一覧表示されています。

## カタログパス

これらの設定値は、**ストア**/設定/**設定**/**カタログ**/**カタログ**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerceだけ？ |
|--------------|--------------|--------------|
| SKU用マスク | `catalog/fields_masks/sku` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Meta タイトルのマスク | `catalog/fields_masks/meta_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Meta キーワードのマスク | `catalog/fields_masks/meta_keyword` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Meta用マスク説明 | `catalog/fields_masks/meta_description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| リストモード | `catalog/frontend/list_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| グリッドで許可される値のページあたりの製品 | `catalog/frontend/grid_per_page_values` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| グリッドのページあたりの製品のデフォルト値 | `catalog/frontend/grid_per_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| リストで許可される値のページごとの製品 | `catalog/frontend/list_per_page_values` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| リストのページあたりの製品のデフォルト値 | `catalog/frontend/list_per_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 製品リストの並べ替え基準 | `catalog/frontend/default_sort_by` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ページごとのすべての製品を許可 | `catalog/frontend/list_allow_all` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| フラット カタログ カテゴリを使用 | `catalog/frontend/flat_catalog_category` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| フラットカタログ商品を使用 | `catalog/frontend/flat_catalog_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 製品ごとのスウォッチ | `catalog/frontend/swatches_per_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| レビューの書き込みを許可 | `catalog/review/allow_guest` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 製品価格が変更されたときにアラートを許可 | `catalog/productalert/allow_price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 価格アラートメールテンプレート | `catalog/productalert/email_price_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 商品が再入荷したときに通知する | `catalog/productalert/allow_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stock アラートメールテンプレート | `catalog/productalert/email_stock_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メール送信者に通知 | `catalog/productalert/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頻度 | `catalog/productalert_cron/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 開始時間 | `catalog/productalert_cron/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メール送信者のエラー | `catalog/productalert_cron/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メールテンプレートのエラー | `catalog/productalert_cron/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 現在のバージョンを表示 | `catalog/recently_products/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最近閲覧した商品のデフォルト数 | `catalog/recently_products/viewed_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最近比較した商品のデフォルト数 | `catalog/recently_products/compared_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 基本ビデオを自動開始 | `catalog/product_video/play_if_base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 関連動画を表示 | `catalog/product_video/show_related` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ビデオを自動的に再起動 | `catalog/product_video/video_auto_restart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| カタログ価格範囲 | `catalog/price/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デフォルトの製品価格 | `catalog/price/default_product_price` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 製品数の表示 | `catalog/layered_navigation/display_product_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 価格ナビゲーション ステップ計算 | `catalog/layered_navigation/price_range_calculation` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デフォルトの価格ナビゲーションステップ | `catalog/layered_navigation/price_range_step` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 価格間隔を1つの価格として表示 | `catalog/layered_navigation/one_price_interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 価格間隔最大数 | `catalog/layered_navigation/price_range_max_intervals` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 間隔除算の制限 | `catalog/layered_navigation/interval_division_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大深度 | `catalog/navigation/max_depth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小クエリ長 | `catalog/search/min_query_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クエリの最大長 | `catalog/search/max_query_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 検索エンジン | `catalog/search/engine` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Solr サーバータイムアウト | `catalog/search/solr_server_timeout` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 索引付けモード | `catalog/search/engine_commit_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 検索候補を有効にする | `catalog/search/search_suggestion_enabled` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 検索候補の数 | `catalog/search/search_suggestion_count` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 各候補の結果数を表示 | `catalog/search/search_suggestion_count_results_enabled` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 検索レコメンデーションを有効にする | `catalog/search/search_recommendations_enabled` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| おすすめ検索回数 | `catalog/search/search_recommendations_count` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 各レコメンデーションの結果数を表示 | `catalog/search/search_recommendations_count_results_enabled` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 一致させる最小条件 | `catalog/search/minimum_should_match` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 「カテゴリ/製品」 URLの生成の書き換え | `catalog/seo/generate_category_product_rewrites` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 人気の検索語 | `catalog/seo/search_terms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 製品URL サフィックス | `catalog/seo/product_url_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| カテゴリ URL サフィックス | `catalog/seo/category_url_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 製品URLにカテゴリーパスを使用 | `catalog/seo/product_use_categories` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| URL キーが変更された場合は、URLの永続的なリダイレクトを作成する | `catalog/seo/save_rewrites_history` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ページタイトル区切り記号 | `catalog/seo/title_separator` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| カテゴリに正規リンク Meta タグを使用する | `catalog/seo/category_canonical_tag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 商品にCanonical Link Meta タグを使用する | `catalog/seo/product_canonical_tag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効にする | `catalog/magento_catalogpermissions/enabled` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| カテゴリの閲覧を許可 | `catalog/magento_catalogpermissions/grant_catalog_category_view` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 顧客グループ | `catalog/magento_catalogpermissions/grant_catalog_category_view_groups` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| ランディングページ | `catalog/magento_catalogpermissions/restricted_landing_page` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 商品の価格を表示 | `catalog/magento_catalogpermissions/grant_catalog_product_price` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 顧客グループ | `catalog/magento_catalogpermissions/grant_catalog_product_price_groups` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| カートへの追加を許可 | `catalog/magento_catalogpermissions/grant_checkout_items` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 顧客グループ | `catalog/magento_catalogpermissions/grant_checkout_items_groups` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| カタログ検索を許可しない | `catalog/magento_catalogpermissions/deny_catalog_search` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| ダウンロードを有効にする注文項目のステータス | `catalog/downloadable/order_item_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デフォルトの最大ダウンロード数 | `catalog/downloadable/downloads_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 共有可能 | `catalog/downloadable/shareable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デフォルトのサンプルタイトル | `catalog/downloadable/samples_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デフォルトのリンクタイトル | `catalog/downloadable/links_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| リンクを新しいウィンドウで開く | `catalog/downloadable/links_target_new_window` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Content-Dispositionを使用 | `catalog/downloadable/content_disposition` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 買い物かごにダウンロード可能なアイテムが含まれている場合は、ゲストチェックアウトを無効にする | `catalog/downloadable/disable_guest_checkout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| JavaScript カレンダーの使用 | `catalog/custom_options/use_calendar` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 日付フィールドの順序 | `catalog/custom_options/date_fields_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 時間フォーマット | `catalog/custom_options/time_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 年範囲 | `catalog/custom_options/year_range` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| カタログイベント機能の有効化 | `catalog/magento_catalogevent/enabled` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| ストアフロントでカタログイベントウィジェットを有効にする | `catalog/magento_catalogevent/lister_output` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| イベントスライダーウィジェットに表示されるイベントの数 | `catalog/magento_catalogevent/lister_widget_limit` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| イベントスライダーウィジェットでクリックごとにスクロールするイベント | `catalog/magento_catalogevent/lister_widget_scroll` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 関連製品リストの最大製品数 | `catalog/magento_targetrule/related_position_limit` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 関連製品を表示 | `catalog/magento_targetrule/related_position_behavior` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 関連製品リストの製品の回転モード | `catalog/magento_targetrule/related_rotation_mode` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| クロスセル製品リストの最大製品数 | `catalog/magento_targetrule/crosssell_position_limit` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| クロスセル商品の表示 | `catalog/magento_targetrule/crosssell_position_behavior` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| クロスセル製品リストの製品の回転モード | `catalog/magento_targetrule/crosssell_rotation_mode` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| アップセル製品リストの最大製品数 | `catalog/magento_targetrule/upsell_position_limit` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| アップセル商品の表示 | `catalog/magento_targetrule/upsell_position_behavior` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| アップセル製品リストの製品の回転モード | `catalog/magento_targetrule/upsell_rotation_mode` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## 在庫パス

これらの設定値は、**ストア**/設定/**設定**/**カタログ**/**インベントリ**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerceだけ？ |
|--------------|--------------|--------------|
| 注文時に在庫を減らす | `cataloginventory/options/can_subtract` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 注文がキャンセルされたときに商品のステータスを在庫に設定 | `cataloginventory/options/can_back_in_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在庫切れ商品の表示 | `cataloginventory/options/show_out_of_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 左しきい値Xのみ | `cataloginventory/options/stock_threshold_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ストアフロントのStockで利用可能な製品を表示する | `cataloginventory/options/display_product_stock_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| カタログとの同期 | `cataloginventory/options/synchronize_with_catalog` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 在庫の管理 | `cataloginventory/item_options/manage_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| バックオーダー | `cataloginventory/item_options/backorders` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 延期されたStock更新プログラムの使用 | `cataloginventory/item_options/use_deferred_stock_update` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 買い物かごで許可される最大数量 | `cataloginventory/item_options/max_sale_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 在庫切れしきい値 | `cataloginventory/item_options/min_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 買い物かごで許可される最低数量 | `cataloginventory/item_options/min_sale_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 以下の数量を通知 | `cataloginventory/item_options/notify_stock_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 数量増分を有効にする | `cataloginventory/item_options/enable_qty_increments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 数量インクリメント | `cataloginventory/item_options/qty_increments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットメモ項目を自動的に在庫に戻す | `cataloginventory/item_options/auto_return` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 非同期的に実行 | `cataloginventory/bulk_operations/async` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 非同期バッチサイズ | `cataloginventory/bulk_operations/batch_size` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| プロバイダー | `cataloginventory/source_selection_distance_based/provider` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 計算モード | `cataloginventory/source_selection_distance_based_google/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 値 | `cataloginventory/source_selection_distance_based_google/value` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Visual Merchandiserのパス

[!BADGE PaaSのみ]{type=Informative url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce on Cloud プロジェクト（Adobeで管理されるPaaS インフラストラクチャ）とオンプレミス プロジェクトにのみ適用されます。"}

これらの設定値は、**ストア**/設定/**設定**/**カタログ**/**ビジュアルマーチャンダイザー**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerceだけ？ |
|--------------|--------------|--------------|
| カテゴリルールに表示される属性 | `visualmerchandiser/options/smart_attributes` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 最低在庫量しきい値 | `visualmerchandiser/options/minimum_stock_threshold` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| カラー属性コード | `visualmerchandiser/options/color_attribute_code` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| カラーの順序 | `visualmerchandiser/options/color_order` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## XML サイトマップのパス

これらの設定値は、**ストア**/設定/**設定**/**カタログ**/**XML サイトマップ**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerceだけ？ |
|--------------|--------------|--------------|
| 頻度 | `sitemap/category/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 優先度 | `sitemap/category/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頻度 | `sitemap/product/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 優先度 | `sitemap/product/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| サイトマップへの画像の追加 | `sitemap/product/image_include` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頻度 | `sitemap/page/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 優先度 | `sitemap/page/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効 | `sitemap/generate/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 開始時間 | `sitemap/generate/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頻度 | `sitemap/generate/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メール送信者のエラー | `sitemap/generate/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メールテンプレートのエラー | `sitemap/generate/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ファイルあたりのURLの最大数 | `sitemap/limit/max_lines` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大ファイルサイズ | `sitemap/limit/max_file_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Robots.txtへの送信を有効にする | `sitemap/search_engines/submission_robots` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## RSS フィード パス

これらの設定値は、**ストア**/設定/**設定**/**カタログ**/**RSS フィード**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerceだけ？ |
|--------------|--------------|--------------|
| RSSを有効にする | `rss/config/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| RSSを有効にする | `rss/wishlist/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新製品 | `rss/catalog/new` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定製品 | `rss/catalog/special` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クーポン/割引 | `rss/catalog/discounts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| トップレベルカテゴリ | `rss/catalog/category` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顧客の注文状況の通知 | `rss/order/status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 友達へのメールのパス

これらの設定値は、**ストア**/設定/**設定**/**カタログ**/**友達にメール**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerceだけ？ |
|--------------|--------------|--------------|
| 有効 | `sendfriend/email/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 電子メールテンプレートを選択 | `sendfriend/email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ゲストを許可 | `sendfriend/email/allow_guest` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大受信者数 | `sendfriend/email/max_recipients` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 1時間に送信された最大製品数 | `sendfriend/email/max_per_hour` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送信制限 | `sendfriend/email/check_by` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
