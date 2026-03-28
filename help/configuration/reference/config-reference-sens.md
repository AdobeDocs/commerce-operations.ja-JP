---
title: 機密性の高いシステム固有のパス
description: Adobe Commerceの機密性の高いシステム固有の設定パスについて説明します。 安全な設定と環境変数管理。
feature: Configuration, System
exl-id: 127880ab-7507-4e53-8b51-dfa6557d0b18
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '4206'
ht-degree: 0%

---

# 機密設定やシステム固有の設定

このトピックでは、システム固有の設定と機密性の高い設定の設定パスをリストします。

- [`magento app:config:dump` コマンド ](../cli/export-configuration.md)は、システム固有の設定をシステム固有の設定ファイル `app/etc/env.php`に書き込みます。これは、_not_&#x200B;がソース管理にあるはずです。 また、すべてのCommerce インスタンスの共有設定を`app/etc/config.php`に書き込みます。このファイル _はソース管理に含まれている必要があります_。
- [`magento config:sensitive:set` コマンド ](../cli/set-configuration-values.md)は、機密性の高い設定を`app/etc/env.php`に書き込みます。

  [環境変数を使用して構成設定を上書きする](../reference/override-config-settings.md#environment-variables)で説明しているように、構成変数を使用して機密値を設定することもできます。

その他の設定パスのリストについては、次を参照してください。

- [支払いを除くすべての設定パス](../reference/config-reference-general.md)
- [支払設定パス ](../reference/config-reference-payment.md)。

>[!INFO]
>
>このトピックに記載されているすべての設定パスは機密性があります。 `System-specific?`列には、システム固有の値も表示されます。

## 一般カテゴリの機密パスとシステム固有パス

このセクションでは、管理者の&#x200B;**ストア**/設定/**構成**/**一般**&#x200B;のオプションで使用できる変数名と構成パスを示します。

### Web パスの機密性の高いパスとシステム固有のパス

これらの設定値は、**Stores**/設定/**Configuration**/**General**/**Web**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerce版サポート | 暗号化？ | システム固有ですか？ | 繊細な？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| ベース URL | `web/unsecure/base_url` |  | | システム固有 | |
| ベースリンク URL | `web/unsecure/base_link_url` |  | | システム固有 | |
| 静的ビューファイルのベース URL | `web/unsecure/base_static_url` |  | | システム固有 | |
| ユーザーメディアファイルのベース URL | `web/unsecure/base_media_url` |  | | システム固有 | |
| セキュアベース URL | `web/secure/base_url` |  | | システム固有 | |
| セキュアベースリンク URL | `web/secure/base_link_url` |  | | システム固有 | |
| 静的ビューファイルのセキュアベース URL | `web/secure/base_static_url` |  | | システム固有 | |
| ユーザーメディアファイルのセキュアベース URL | `web/secure/base_media_url` |  | | システム固有 | |
| 既定のWeb URL | `web/default/front` |  | | システム固有 | |
| デフォルトのルートなしURL | `web/default/no_route` |  | | システム固有 | |
| Cookie パス | `web/cookie/cookie_path` |  | | システム固有 | |
| Cookie ドメイン | `web/cookie/cookie_domain` |  | | システム固有 | |
| Cookieの有効期間 | `web/cookie/cookie_lifetime` |  | | システム固有 | |
| HTTPのみを使用 | `web/cookie/cookie_httponly` |  | | システム固有 | |
| Cookie制限モード | `web/cookie/cookie_restriction` |  | | システム固有 | |

{style="table-layout:auto"}

### 通貨設定の機密性の高いシステム固有のパス

これらの設定値は、**ストア**/設定/**設定**/**一般**/**通貨セットアップ**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerce版サポート | 暗号化？ | システム固有ですか？ | 繊細な？ |
| --- | --- | --- | --- | --- | --- |
| メール受信者のエラー | `currency/import/error_email` |  | | | 機密 |

{style="table-layout:auto"}

### メールアドレスの機密パスとシステム固有パスを保存する

これらの設定値は、**ストア**/設定/**メール設定**/**一般**/**ストアメールアドレス**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerce版サポート | 暗号化？ | システム固有ですか？ | 繊細な？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 送信者名 | `trans_email/ident_general/name` | | | | 機密 |
| 送信者のメール | `trans_email/ident_general/email` |  | | | 機密 |
| 送信者名 | `trans_email/ident_sales/name` |  | | | 機密 |
| 送信者のメール | `trans_email/ident_sales/email` |  | | | 機密 |
| 送信者名 | `trans_email/ident_support/name` |  | | | 機密 |
| 送信者のメール | `trans_email/ident_support/email` |  | | | 機密 |
| 送信者名 | `trans_email/ident_custom1/name` |  | | | 機密 |
| 送信者のメール | `trans_email/ident_custom1/email` |  | | | 機密 |
| 送信者名 | `trans_email/ident_custom2/name` |  | | | 機密 |
| 送信者のメール | `trans_email/ident_custom2/email` |  | | | 機密 |

{style="table-layout:auto"}

### 機密性の高いシステム固有のパスに連絡

これらの設定値は、**ストア**/設定/**設定**/**一般**/**連絡先**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerce版サポート | 暗号化？ | システム固有ですか？ | 繊細な？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| メール送信先 | `contact/email/recipient_email` |  | | | 機密 |
| メール送信者 | `contact/email/sender_email_identity` |  | | | 機密 |
| メールテンプレート | `contact/email/email_template` |  | | | 機密 |

{style="table-layout:auto"}

### New Relicのレポート機能では、機密性の高いパスやシステム固有のパスを

これらの設定値は、**Stores**/Settings > **Configuration** > **General** > **New Relic Reporting**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerce版サポート | 暗号化？ | システム固有ですか？ | 繊細な？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| New Relic アカウント ID | `newrelicreporting/general/account_id` |  | | | 機密 |
| New Relic アプリケーション ID | `newrelicreporting/general/app_id` |  | | | 機密 |
| New Relic API キー | `newrelicreporting/general/api` |  | 暗号化 | | 機密 |
| Insights API キー | `newrelicreporting/general/insights_insert_key` |  | 暗号化 | | 機密 |
| NEW RELIC API URL | `newrelicreporting/general/api_url` |  | | システム固有 | 機密 |
| インサイト API URL | `newrelicreporting/general/insights_api_url` |  | | システム固有 | 機密 |

{style="table-layout:auto"}

## 顧客カテゴリの機密性の高いパスとシステム固有のパス

このセクションでは、管理者の&#x200B;**ストア**/設定/**構成**/**顧客**&#x200B;のオプションで使用できる変数名と構成パスを一覧表示します。

### 顧客設定の機密性の高いパスとシステム固有のパス

これらの設定値は、**Stores**/設定/**Configuration**/**Customers**/**Customer Configuration**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerce版サポート | 暗号化？ | システム固有ですか？ | 繊細な？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| デフォルトのメールドメイン | `customer/create_account/email_domain` |  | | システム固有 | |

{style="table-layout:auto"}

## カタログカテゴリ

このセクションでは、管理者の&#x200B;**ストア**/設定/**構成**/**カタログ**&#x200B;で使用できる変数名と構成パスを示します。

### カタログの機密性の高いパスとシステム固有のパス

これらの設定値は、**ストア**/設定/**設定**/**カタログ**/**カタログ**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerce版サポート | 暗号化？ | システム固有ですか？ | 繊細な？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| メール受信者のエラー | `catalog/productalert_cron/error_email` |  | | | 機密 |
| YouTube API キー | `catalog/product_video/youtube_api_key` |  | | | 機密 |
| Solr サーバーホスト名 | `catalog/search/solr_server_hostname` | Commerce Enterpriseのみ | | システム固有 | 機密 |
| Solr サーバーポート | `catalog/search/solr_server_port` | Commerce Enterpriseのみ | | システム固有 | 機密 |
| Solr Server ユーザー名 | `catalog/search/solr_server_username` | Commerce Enterpriseのみ | | システム固有 | 機密 |
| Solr サーバーパスワード | `catalog/search/solr_server_password` | Commerce Enterpriseのみ | | システム固有 | 機密 |
| Solr サーバーパス | `catalog/search/solr_server_path` | Commerce Enterpriseのみ | | システム固有 | 機密 |
| Elasticsearch Server ホスト名 | `catalog/search/elasticsearch_server_hostname` |  | | システム固有 | 機密 |
| Elasticsearch Server Port | `catalog/search/elasticsearch_server_port` |  | | システム固有 | 機密 |
| Elasticsearch インデックスプレフィックス | `catalog/search/elasticsearch_index_prefix` |  | | システム固有 | 機密 |
| Elasticsearch HTTP Authを有効にする | `catalog/search/elasticsearch_enable_auth` |  | | システム固有 | |
| Elasticsearch HTTP ユーザー名 | `catalog/search/elasticsearch_username` |  | | システム固有 | |
| Elasticsearch HTTP パスワード | `catalog/search/elasticsearch_password` |  | | システム固有 | |
| Elasticsearch Serverのタイムアウト | `catalog/search/elasticsearch_server_timeout` |  | | システム固有 | |
| Elasticsearch HTTP ユーザー名 | `catalog/search/elasticsearch_username` | | | システム固有 | |
| Elasticsearch HTTP パスワード | `catalog/search/elasticsearch_password` | | | システム固有 | |
| Elasticsearch Serverのタイムアウト | `catalog/search/elasticsearch_server_timeout` | | | システム固有 | |
| OpenSearch Server ホスト名 | `catalog/search/opensearch_server_hostname` | | | システム固有 | 機密 |
| OpenSearch Server ポート | `catalog/search/opensearch_server_port` | | | システム固有 | 機密 |
| OpenSearch インデックスの接頭辞 | `catalog/search/opensearch_index_prefix` | | | システム固有 | 機密 |
| OpenSearch HTTP認証を有効にする | `catalog/search/opensearch_enable_auth` | | | システム固有 | |
| OpenSearch HTTP Username | `catalog/search/opensearch_username` | | | システム固有 | |
| OpenSearch HTTP パスワード | `catalog/search/opensearch_password` | | | システム固有 | |
| OpenSearch Serverのタイムアウト | `catalog/search/opensearch_server_timeout` | | | システム固有 | |

{style="table-layout:auto"}

>[!NOTE]
>
>OpenSearchの設定は、Adobe Commerce 2.4.6で導入されました。

### 在庫の機密性の高いパスとシステム固有のパス

これらの設定値は、**ストア**/設定/**設定**/**カタログ**/**インベントリ**&#x200B;の管理者で使用できます。

|名前|設定パス | Commerce バージョンのサポート |暗号化されていますか？ | システム固有か？ |機密性？ | |
|--------------|--------------|--------------|--------------|--------------|--------------||
| Google API キー| `cataloginventory/source_selection_distance_based_google/api_key` | |暗号化| |機密性|

### XML サイトマップの機密パスとシステム固有パス

これらの設定値は、**ストア**/設定/**設定**/**カタログ**/**XML サイトマップ**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerce版サポート | 暗号化？ | システム固有ですか？ | 繊細な？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| メール受信者のエラー | `sitemap/generate/error_email` |  | | | 機密 |

{style="table-layout:auto"}

## 販売カテゴリ

このセクションでは、管理者の&#x200B;**ストア**/設定/**構成**/**セールス**&#x200B;のオプションで使用できる変数名と構成パスをリストします。

### 配送設定の機密性の高いパスとシステム固有のパス

これらの設定値は、**ストア**/設定/**設定**/**セールス**/**出荷設定**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerce版サポート | 暗号化？ | システム固有ですか？ | 繊細な？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 国 | `shipping/origin/country_id` |  | | | 機密 |
| 地域/州 | `shipping/origin/region_id` |  | | | 機密 |
| 郵便番号 | `shipping/origin/postcode` |  | | | 機密 |
| 市区町村 | `shipping/origin/city` |  | | | 機密 |
| 住所 | `shipping/origin/street_line1` |  | | | 機密 |
| 住所2行目 | `shipping/origin/street_line2` |  | | | 機密 |
| ライブアカウント | `carriers/ups/is_account_live` |  | | システム固有 | |

{style="table-layout:auto"}

### セールスメールの機密性の高いパスとシステム固有のパス

これらの設定値は、**Stores** / 設定/**Configuration** / **Sales** / **Sales Email**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerce版サポート | 暗号化？ | システム固有ですか？ | 繊細な？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 注文メールのコピーの送信先 | `sales_email/order/copy_to` |  | | | 機密 |
| 注文コメントの電子メール コピーの送信先 | `sales_email/order_comment/copy_to` |  | | | 機密 |
| 請求書メール コピーの送信先 | `sales_email/invoice/copy_to` |  | | | 機密 |
| 請求書コメント電子メールのコピーの送信先 | `sales_email/invoice_comment/copy_to` |  | | | 機密 |
| 送信メールのコピー先 | `sales_email/shipment/copy_to` |  | | | 機密 |
| 出荷コメント電子メールのコピーの送信先 | `sales_email/shipment_comment/copy_to` |  | | | 機密 |
| クレジットメモ電子メールのコピーを送信先 | `sales_email/creditmemo/copy_to` |  | | | 機密 |
| クレジットメモの注釈メールのコピーの送信先 | `sales_email/creditmemo_comment/copy_to` |  | | | 機密 |
| 受け取り準備メールのコピーの送信先 | `sales_email/temando_pickup/copy_to` |  | | | 機密 |

{style="table-layout:auto"}

### チェックアウトの機密性の高いパスとシステム固有のパス

これらの設定値は、**ストア**/設定/**設定**/**セールス**/**チェックアウト**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerce版サポート | 暗号化？ | システム固有ですか？ | 繊細な？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 支払い失敗した電子メール コピーの送信先 | `checkout/payment_failed/copy_to` |  | | | 機密 |

{style="table-layout:auto"}

### Google APIの機密性の高いパスとシステム固有のパス

これらの設定値は、**Stores**/Settings > **Configuration** > **Sales** > **Google API**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerce版サポート | 暗号化？ | システム固有ですか？ | 繊細な？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| コンテナ ID | `google/analytics/container_id` | Commerce Enterpriseのみ | | | 機密 |

{style="table-layout:auto"}

### 配信メソッドの機密性の高いシステム固有のパス

これらの設定値は、**ストア**/設定/**設定**/**セールス**/**配信方法**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerce版サポート | 暗号化？ | システム固有ですか？ | 繊細な？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| ゲートウェイ URL | `carriers/usps/gateway_url` |  | | | 機密 |
| セキュアゲートウェイ URL | `carriers/usps/gateway_secure_url` |  | | | 機密 |
| タイトル | `carriers/usps/title` |  | | | |
| ユーザー ID | `carriers/usps/userid` |  | 暗号化 | | 機密 |
| パスワード | `carriers/usps/password` |  | 暗号化 | | 機密 |
| ユーザー ID | `carriers/ups/username` |  | 暗号化 | | 機密 |
| パスワード | `carriers/ups/password` |  | 暗号化 | | 機密 |
| アクセス ライセンス番号 | `carriers/ups/access_license_number` |  | 暗号化 | | 機密 |
| トラッキング XML URL | `carriers/ups/tracking_xml_url` |  | | | 機密 |
| ゲートウェイ XML URL | `carriers/ups/gateway_xml_url` |  | | | 機密 |
| シッパー番号 | `carriers/ups/shipper_number` |  | | | 機密 |
| デバッグ | `carriers/ups/debug` |  | | | 機密 |
| アカウント ID | `carriers/fedex/account` |  | 暗号化 | | 機密 |
| キー | `carriers/fedex/key` |  | 暗号化 | | 機密 |
| メーター番号 | `carriers/fedex/meter_number` |  | 暗号化 | | 機密 |
| パスワード | `carriers/fedex/password` |  | 暗号化 | | 機密 |
| アクセス ID | `carriers/dhl/id` |  | 暗号化 | | 機密 |
| パスワード | `carriers/dhl/password` |  | 暗号化 | | 機密 |
| デバッグ | `carriers/dhl/debug` |  | | | |
| アカウント番号 | `carriers/dhl/account` |  | | | 機密 |
| ゲートウェイ URL | `carriers/dhl/gateway_url` |  | | | 機密 |
| サンドボックスモード | `carriers/fedex/sandbox_mode` |  | | | 機密 |

{style="table-layout:auto"}

### セールスに敏感な人やシステム固有のパス

これらの設定値は、**Stores**/設定/**Configuration**/**Sales**/**Sales**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerce版サポート | 暗号化？ | システム固有ですか？ | 繊細な？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 連絡先名 | `sales/magento_rma/store_name` | Commerce Enterpriseのみ | | | 機密 |
| 住所 | `sales/magento_rma/address` | Commerce Enterpriseのみ | | | 機密 |
| 住所 | `sales/magento_rma/address1` |  | | | 機密 |
| 市区町村 | `sales/magento_rma/city` | Commerce Enterpriseのみ | | | 機密 |
| 都道府県 | `sales/magento_rma/region_id` | Commerce Enterpriseのみ | | | 機密 |
| 郵便番号 | `sales/magento_rma/zip` | Commerce Enterpriseのみ | | | 機密 |
| 国 | `sales/magento_rma/country_id` | Commerce Enterpriseのみ | | | 機密 |
| RMA電子メールコピーの送信先 | `sales_email/magento_rma/copy_to` | Commerce Enterpriseのみ | | | 機密 |
| RMA承認メールのコピーをに送信 | `sales_email/magento_rma_auth/copy_to` | Commerce Enterpriseのみ | | | 機密 |
| RMA コメント電子メール コピーの送信先 | `sales_email/magento_rma_comment/copy_to` | Commerce Enterpriseのみ | | | 機密 |
| RMA コメント電子メール コピーの送信先 | `sales_email/magento_rma_customer_comment/copy_to` | Commerce Enterpriseのみ | | | 機密 |

{style="table-layout:auto"}

### Google API パス

これらの設定値は、**Stores**/Settings > **Configuration** > **Sales** > **Google API**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerce版サポート | 暗号化？ | システム固有ですか？ | 繊細な？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| アカウント番号 | `google/analytics/account` |  | | | 機密 |

{style="table-layout:auto"}

## 高度なカテゴリ

このセクションでは、管理者の&#x200B;**ストア**/設定/**構成**/**詳細**&#x200B;のオプションで使用できる変数名と構成パスを示します。

### 管理者機密パスとシステム固有パス

これらの設定値は、**Stores** / 設定/**Configuration** / **Advanced** / **Admin**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerce版サポート | 暗号化？ | システム固有ですか？ | 繊細な？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| カスタム管理者URL | `admin/url/custom` |  | | | 機密 |
| カスタム管理パス | `admin/url/custom_path` |  | | | 機密 |

{style="table-layout:auto"}

### システムに依存するパスとシステム固有のパス

これらの設定値は、**Stores**/設定/**Configuration**/**Advanced**/**System**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerce版サポート | 暗号化？ | システム固有ですか？ | 繊細な？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| メール受信者のエラー | `system/magento_scheduled_import_export_log/error_email` |  | | | 機密 |
| アクセスリスト | `system/full_page_cache/varnish/access_list` |  |  | | 機密 |
| メール送信者のエラー | `system/magento_scheduled_import_export_log/error_email_identity` |  |  | | 機密 |

{style="table-layout:auto"}

### 開発者の機密パスとシステム固有パス

これらの設定値は、**ストア**/設定/**設定**/**詳細**/**開発者**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerce版サポート | 暗号化？ | システム固有ですか？ | 繊細な？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 許可されたIP （コンマ区切り） | `dev/restrict/allow_ips` |  | | システム固有 | 機密 |

{style="table-layout:auto"}

## 高度なカテゴリ

このセクションでは、管理者の&#x200B;**ストア**/設定/**構成**/**詳細**&#x200B;のオプションで使用できる変数名と構成パスを示します。

### システムパス

これらの設定値は、**Stores**/設定/**Configuration**/**Advanced**/**System**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerce版サポート | 暗号化？ | システム固有ですか？ | 繊細な？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| ホスト | `system/smtp/host` |  | | システム固有 | 機密 |
| ポート （25） | `system/smtp/port` |  | | システム固有 | 機密 |
| バックエンドホスト | `system/full_page_cache/varnish/backend_host` |  | | システム固有 | 機密 |
| バックエンドポート | `system/full_page_cache/varnish/backend_port` |  | | システム固有 | 機密 |

{style="table-layout:auto"}

### 開発者用パス

これらの設定値は、**ストア**/設定/**設定**/**詳細**/**開発者**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerce版サポート | 暗号化？ | システム固有ですか？ | 繊細な？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| セッションストレージキーへのJS エラーのログ記録 | `dev/js/session_storage_key` | ![Commerce以外](/help/assets/configuration/red-x.png) | | システム固有 | |

{style="table-layout:auto"}

## 支払いに敏感なシステム固有のパス

このセクションでは、**ストア**/設定/**設定**/**セールス**/**支払**&#x200B;の管理画面でオプションで使用できる変数名と設定パスを示します。

### 一般変数

| 名前 | 設定パス | Commerce版サポート | 暗号化？ |
|--------------|--------------|--------------|--------------|
| 加盟店の国 | `paypal/general/merchant_country` |  | 機密 |

{style="table-layout:auto"}

>[!INFO]
>
>この変数を選択すると、使用できる[国際パス ](#international-paths)が決まります。

### PayPalの機密パスとシステム固有のパス

| 名前 | 設定パス | Commerce版サポート | 暗号化？ | システム固有ですか？ | 繊細な？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| PayPal加盟店アカウントに関連付けられたメール（オプション） | `paypal/general/business_account` |  | | | 機密 |
| 加盟店アカウント ID | `payment/paypal_express/merchant_id` |  | | | 機密 |
| 発行者ID | `payment/paypal_express_bml/publisher_id` |  | | | 機密 |
| パスワード | `paypal/fetch_reports/ftp_password` |  | 暗号化 | | 機密 |
| ログイン | `paypal/fetch_reports/ftp_login` |  | 暗号化 | | 機密 |
| カスタムエンドポイントホスト名またはIP アドレス | `paypal/fetch_reports/ftp_ip` |  | | システム固有 | 機密 |
| サンドボックスモード | `paypal/fetch_reports/ftp_sandbox` |  | | システム固有 | |
| デバッグモード | `payment/paypal_express/debug` |  | | システム固有 | |
| デバッグモード | `payment/paypal_billing_agreement/debug` |  | | システム固有 | |
| SFTP資格情報 | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 機密 |

{style="table-layout:auto"}

### PayPal Payflow Proの機密性の高いシステム固有のパス

| 名前 | 設定パス | Commerce版サポート | 暗号化？ | システム固有ですか？ | 繊細な？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| ユーザー | `payment/payflow_advanced/user` |  | 暗号化 | | 機密 |
| パスワード | `payment/payflow_advanced/pwd` |  | 暗号化 | | 機密 |
| カスタムパス | `paypal/fetch_reports/ftp_path` |  | | システム固有 | 機密 |
| ユーザー | `payment/payflowpro/user` |  | 暗号化 | | 機密 |
| パスワード | `payment/payflowpro/pwd` |  | 暗号化 | システム固有 | 機密 |
| テストモード | `payment/payflowpro/sandbox_flag` |  | | システム固有 | |
| パートナー | `payment/payflowpro/partner` |  | | | 機密 |
| プロキシホスト | `payment/payflowpro/proxy_host` |  | | システム固有 | 機密 |
| プロキシポート | `payment/payflowpro/proxy_port` |  | | システム固有 | 機密 |
| デバッグモード | `payment/payflowpro/debug` |  | | システム固有 | |
| SFTP資格情報 | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | システム固有 | |
| クレジットカード設定 | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/heading_cc` |  | | | 機密 |

{style="table-layout:auto"}

### PayPal Payflow機密性の高いシステム固有のパスをリンク

| 名前 | 設定パス | Commerce版サポート | 暗号化？ | システム固有ですか？ | 繊細な？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| ユーザー | `payment/payflow_link/user` |  | 暗号化 | | 機密 |
| パスワード | `payment/payflow_link/pwd` |  | 暗号化 | | 機密 |
| テストモード | `payment/payflow_link/sandbox_flag` |  | | システム固有 | |
| プロキシを使用 | `payment/payflow_link/use_proxy` |  | | システム固有 | |
| プロキシホスト | `payment/payflow_link/proxy_host` |  | | システム固有 | |
| プロキシポート | `payment/payflow_link/proxy_port` |  |  | システム固有 | |
| デバッグモード | `payment/payflow_link/debug` |  | | システム固有 | |
| URLをキャンセルおよびURLを返すためのURL メソッド | `payment/payflow_link/url_method` |  | | システム固有 | |
| デバッグモード | `payment/payflow_express/debug` |  | | システム固有 | |
| SFTP資格情報 | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` |  | | | 機密 |

{style="table-layout:auto"}

### PayPal Payments Proの機密性の高いシステム固有のパス

| 名前 | 設定パス | Commerce版サポート | 暗号化？ | システム固有ですか？ | 繊細な？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| API ユーザー名 | `paypal/wpp/api_username` |  | 暗号化 | | 機密 |
| API パスワード | `paypal/wpp/api_password` |  | 暗号化 | | 機密 |
| API署名 | `paypal/wpp/api_signature` |  | 暗号化 | | 機密 |
| API証明書 | `paypal/wpp/api_cert` |  | | | 機密 |
| プロキシホスト | `paypal/wpp/proxy_host` |  | | システム固有 | 機密 |
| プロキシポート | `paypal/wpp/proxy_port` |  | | システム固有 | 機密 |
| サンドボックスモード | `paypal/wpp/sandbox_flag` |  | | システム固有 | |
| SFTP資格情報 | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | 機密 |

{style="table-layout:auto"}

### PayPal Payments Pro ホストされた機密およびシステム固有のパス

| 名前 | 設定パス | Commerce版サポート | 暗号化？ | システム固有ですか？ | 繊細な？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| デバッグモード | `payment/hosted_pro/debug` |  | | システム固有 | |
| SFTP資格情報 | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | 機密 |
| SFTP資格情報 | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | 機密 |

{style="table-layout:auto"}

### Braintreeの機密パスとシステム固有パス

| 名前 | 設定パス | Commerce版サポート | 暗号化？ | システム固有ですか？ | 繊細な？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 加盟店ID | `payment/braintree/merchant_id` |  | | | 機密 |
| 公開鍵 | `payment/braintree/public_key` |  | 暗号化 | | 機密 |
| 秘密鍵 | `payment/braintree/private_key` |  | 暗号化 | | 機密 |
| 加盟店アカウント ID | `payment/braintree/merchant_account_id` |  | | | 機密 |
| Kount Merchant ID | `payment/braintree/kount_id` |  | | | 機密 |
| マーチャント名を上書き | `payment/braintree_paypal/merchant_name_override` |  | | | 機密 |
| 電話 | `payment/braintree/descriptor_phone` |  | | | 機密 |
| URL | `payment/braintree/descriptor_url` |  | | システム固有 | |

{style="table-layout:auto"}

### 小切手/為替パス

| 名前 | 設定パス | Commerce版サポート | 暗号化？ | システム固有ですか？ | 繊細な？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 小切手の送信先 | `payment/checkmo/mailing_address` |  | | | 機密 |
| 小切手の送信先 | `payment_us/checkmo/mailing_address` |  | | | 機密 |

{style="table-layout:auto"}

### 国際パス

| 名前 | 設定パス | Commerce版サポート | 暗号化？ | システム固有ですか？ | 繊細な？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| トランザクションキー | `payment_au/authorizenet_directpost/trans_key` |  | 暗号化 | システム固有 | 機密 |
| テストモード | `payment_au/authorizenet_directpost/test` |  | | システム固有 | |
| ゲートウェイ URL | `payment_au/authorizenet_directpost/cgi_url` |  | | システム固有 | 機密 |
| トランザクション詳細URL | `payment_au/authorizenet_directpost/cgi_url_td` |  | | システム固有 | 機密 |
| トランザクションキー | `payment_au/cybersource/transaction_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| アクセスキー | `payment_au/cybersource/access_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| 秘密鍵 | `payment_au/cybersource/secret_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| テストモード | `payment_au/cybersource/sandbox_flag` | Commerce Enterpriseのみ | | システム固有 | |
| 支払い応答パスワード | `payment_au/worldpay/response_password` | Commerce Enterpriseのみ | | システム固有 | 機密 |
| リモート管理者認証パスワード | `payment_au/worldpay/auth_password` | Commerce Enterpriseのみ | | システム固有 | 機密 |
| サンドボックスモード | `payment_au/eway/sandbox_flag` | Commerce Enterpriseのみ | | システム固有 | |
| ライブ API キー | `payment_au/eway/live_api_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| ライブ API パスワード | `payment_au/eway/live_api_password` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| ライブクライアントサイド暗号化キー | `payment_au/eway/live_encryption_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| サンドボックス API キー | `payment_au/eway/sandbox_api_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| サンドボックス API パスワード | `payment_au/eway/sandbox_api_password` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| サンドボックスのクライアントサイド暗号化キー | `payment_au/eway/sandbox_encryption_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| トランザクションキー | `payment_es/authorizenet_directpost/trans_key` |  | 暗号化 | システム固有 | 機密 |
| テストモード | `payment_es/authorizenet_directpost/test` |  | | システム固有 | |
| ゲートウェイ URL | `payment_es/authorizenet_directpost/cgi_url` |  | | システム固有 | 機密 |
| トランザクション詳細URL | `payment_es/authorizenet_directpost/cgi_url_td` |  | | システム固有 | 機密 |
| トランザクションキー | `payment_es/cybersource/transaction_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| アクセスキー | `payment_es/cybersource/access_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| 秘密鍵 | `payment_es/cybersource/secret_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| テストモード | `payment_es/cybersource/sandbox_flag` | Commerce Enterpriseのみ | | システム固有 | |
| 支払い応答パスワード | `payment_es/worldpay/response_password` | Commerce Enterpriseのみ | | システム固有 | 機密 |
| リモート管理者認証パスワード | `payment_es/worldpay/auth_password` | Commerce Enterpriseのみ | | システム固有 | 機密 |
| トランザクションのMD5 シークレット | `payment_es/worldpay/md5_secret` | Commerce Enterpriseのみ | | システム固有 | 機密 |
| デバッグ | `payment_es/worldpay/debug` | Commerce Enterpriseのみ | | システム固有 | |
| サンドボックスモード | `payment_es/eway/sandbox_flag` | Commerce Enterpriseのみ | | システム固有 | |
| ライブ API キー | `payment_es/eway/live_api_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| ライブ API パスワード | `payment_es/eway/live_api_password` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| ライブクライアントサイド暗号化キー | `payment_es/eway/live_encryption_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| サンドボックス API キー | `payment_es/eway/sandbox_api_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| サンドボックス API パスワード | `payment_es/eway/sandbox_api_password` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| サンドボックスのクライアントサイド暗号化キー | `payment_es/eway/sandbox_encryption_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| トランザクションキー | `payment_nz/authorizenet_directpost/trans_key` |  | 暗号化 | システム固有 | 機密 |
| テストモード | `payment_nz/authorizenet_directpost/test` |  | | システム固有 | |
| ゲートウェイ URL | `payment_nz/authorizenet_directpost/cgi_url` |  | | システム固有 | 機密 |
| トランザクション詳細URL | `payment_nz/authorizenet_directpost/cgi_url_td` |  | | システム固有 | 機密 |
| テストモード | `payment_nz/cybersource/sandbox_flag` | Commerce Enterpriseのみ | | システム固有 | |
| テストモード | `payment_nz/worldpay/sandbox_flag` | Commerce Enterpriseのみ | | システム固有 | |
| サンドボックスモード | `payment_nz/eway/sandbox_flag` | Commerce Enterpriseのみ | | システム固有 | |
| ライブ API キー | `payment_nz/eway/live_api_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| ライブ API パスワード | `payment_nz/eway/live_api_password` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| ライブクライアントサイド暗号化キー | `payment_nz/eway/live_encryption_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| サンドボックス API キー | `payment_nz/eway/sandbox_api_key` | Commerce Enterpriseのみ | 暗号化 | | 機密 |
| サンドボックス API パスワード | `payment_nz/eway/sandbox_api_password` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| サンドボックスのクライアントサイド暗号化キー | `payment_nz/eway/sandbox_encryption_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| テストモード | `payment/payflow_advanced/sandbox_flag` |  | | システム固有 | |
| プロキシホスト | `payment/payflow_advanced/proxy_host` |  | | システム固有 | 機密 |
| プロキシポート | `payment/payflow_advanced/proxy_port` |  | | システム固有 | |
| デバッグモード | `payment/payflow_advanced/debug` |  | | システム固有 | |
| URLをキャンセルおよびURLを返すためのURL メソッド | `payment/payflow_advanced/url_method` |  | | システム固有 | |
| テストモード | `payment_us/authorizenet_directpost/test` |  | | システム固有 | |
| ゲートウェイ URL | `payment_us/authorizenet_directpost/cgi_url` |  | | システム固有 | 機密 |
| トランザクション詳細URL | `payment_us/authorizenet_directpost/cgi_url_td` |  | | システム固有 | 機密 |
| アクセスキー | `payment_us/cybersource/access_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| 秘密鍵 | `payment_us/cybersource/secret_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| テストモード | `payment_us/cybersource/sandbox_flag` | Commerce Enterpriseのみ | | システム固有 | |
| テストモード | `payment_us/worldpay/sandbox_flag` | Commerce Enterpriseのみ | | システム固有 | |
| サンドボックスモード | `payment_us/eway/sandbox_flag` | Commerce Enterpriseのみ | | システム固有 | |
| ライブ API キー | `payment_us/eway/live_api_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| ライブ API パスワード | `payment_us/eway/live_api_password` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| ライブクライアントサイド暗号化キー | `payment_us/eway/live_encryption_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| サンドボックス API キー | `payment_us/eway/sandbox_api_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| サンドボックス API パスワード | `payment_us/eway/sandbox_api_password` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| サンドボックスのクライアントサイド暗号化キー | `payment_us/eway/sandbox_encryption_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | |
| テストモード | `payment_gb/cybersource/sandbox_flag` | Commerce Enterpriseのみ | | システム固有 | |
| テストモード | `payment_gb/authorizenet_directpost/test` |  | | システム固有 | |
| ゲートウェイ URL | `payment_gb/authorizenet_directpost/cgi_url` |  | | システム固有 | 機密 |
| トランザクション詳細URL | `payment_gb/authorizenet_directpost/cgi_url_td` |  | | システム固有 | 機密 |
| テストモード | `payment_gb/worldpay/sandbox_flag` | Commerce Enterpriseのみ | | システム固有 | |
| サンドボックスモード | `payment_gb/eway/sandbox_flag` | Commerce Enterpriseのみ | | システム固有 | |
| ライブ API キー | `payment_gb/eway/live_api_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| ライブ API パスワード | `payment_gb/eway/live_api_password` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| ライブクライアントサイド暗号化キー | `payment_gb/eway/live_encryption_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| サンドボックス API キー | `payment_gb/eway/sandbox_api_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| サンドボックス API パスワード | `payment_gb/eway/sandbox_api_password` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| サンドボックスのクライアントサイド暗号化キー | `payment_gb/eway/sandbox_encryption_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| トランザクションキー | `payment_de/cybersource/transaction_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| アクセスキー | `payment_de/cybersource/access_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| 秘密鍵 | `payment_de/cybersource/secret_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| テストモード | `payment_de/cybersource/sandbox_flag` | Commerce Enterpriseのみ | | システム固有 | |
| トランザクションキー | `payment_de/authorizenet_directpost/trans_key` |  | 暗号化 | システム固有 | 機密 |
| テストモード | `payment_de/authorizenet_directpost/test` |  | | システム固有 | |
| ゲートウェイ URL | `payment_de/authorizenet_directpost/cgi_url` |  | | システム固有 | 機密 |
| トランザクション詳細URL | `payment_de/authorizenet_directpost/cgi_url_td` |  | | システム固有 | 機密 |
| 支払い応答パスワード | `payment_de/worldpay/response_password` | Commerce Enterpriseのみ | | システム固有 | 機密 |
| リモート管理者認証パスワード | `payment_de/worldpay/auth_password` | Commerce Enterpriseのみ | | システム固有 | 機密 |
| デバッグ | `payment_de/worldpay/debug` | Commerce Enterpriseのみ | | システム固有 | |
| サンドボックスモード | `payment_de/eway/sandbox_flag` | Commerce Enterpriseのみ | | システム固有 | |
| ライブ API キー | `payment_de/eway/live_api_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| ライブ API パスワード | `payment_de/eway/live_api_password` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| ライブクライアントサイド暗号化キー | `payment_de/eway/live_encryption_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| サンドボックス API キー | `payment_de/eway/sandbox_api_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| サンドボックス API パスワード | `payment_de/eway/sandbox_api_password` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| サンドボックスのクライアントサイド暗号化キー | `payment_de/eway/sandbox_encryption_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| トランザクションキー | `payment_other/authorizenet_directpost/trans_key` |  | 暗号化 | システム固有 | 機密 |
| テストモード | `payment_other/authorizenet_directpost/test` |  | | システム固有 | 機密 |
| ゲートウェイ URL | `payment_other/authorizenet_directpost/cgi_url` |  | | システム固有 | 機密 |
| トランザクション詳細URL | `payment_other/authorizenet_directpost/cgi_url_td` |  | | システム固有 | |
| トランザクションキー | `payment_other/cybersource/transaction_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| アクセスキー | `payment_other/cybersource/access_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| 秘密鍵 | `payment_other/cybersource/secret_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| 新規注文ステータス | `payment_other/cybersource/order_status` | Commerce Enterpriseのみ | | システム固有 | |
| テストモード | `payment_other/cybersource/sandbox_flag` | Commerce Enterpriseのみ | | システム固有 | |
| 支払い応答パスワード | `payment_other/worldpay/response_password` | Commerce Enterpriseのみ | | システム固有 | 機密 |
| リモート管理者認証パスワード | `payment_other/worldpay/auth_password` | Commerce Enterpriseのみ | | システム固有 | 機密 |
| テストモード | `payment_other/worldpay/sandbox_flag` | Commerce Enterpriseのみ | | システム固有 | |
| サンドボックスモード | `payment_other/eway/sandbox_flag` | Commerce Enterpriseのみ | | システム固有 | |
| ライブ API キー | `payment_other/eway/live_api_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| ライブ API パスワード | `payment_other/eway/live_api_password` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| ライブクライアントサイド暗号化キー | `payment_other/eway/live_encryption_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| サンドボックス API キー | `payment_other/eway/sandbox_api_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| サンドボックス API パスワード | `payment_other/eway/sandbox_api_password` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| サンドボックスのクライアントサイド暗号化キー | `payment_other/eway/sandbox_encryption_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| トランザクションキー | `payment_ca/authorizenet_directpost/trans_key` |  | 暗号化 | システム固有 | 機密 |
| テストモード | `payment_ca/authorizenet_directpost/test` |  | | システム固有 | |
| ゲートウェイ URL | `payment_ca/authorizenet_directpost/cgi_url` |  | | システム固有 | 機密 |
| トランザクション詳細URL | `payment_ca/authorizenet_directpost/cgi_url_td` |  | | システム固有 | 機密 |
| トランザクションキー | `payment_ca/cybersource/transaction_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| アクセスキー | `payment_ca/cybersource/access_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| 秘密鍵 | `payment_ca/cybersource/secret_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| 新規注文ステータス | `payment_ca/cybersource/order_status` | Commerce Enterpriseのみ | | | |
| テストモード | `payment_ca/cybersource/sandbox_flag` | Commerce Enterpriseのみ | | システム固有 | |
| 支払い応答パスワード | `payment_ca/worldpay/response_password` | Commerce Enterpriseのみ | | システム固有 | |
| リモート管理者認証パスワード | `payment_ca/worldpay/auth_password` | Commerce Enterpriseのみ | | システム固有 | 機密 |
| テストモード | `payment_ca/worldpay/sandbox_flag` | Commerce Enterpriseのみ | | システム固有 | |
| サンドボックスモード | `payment_ca/eway/sandbox_flag` | Commerce Enterpriseのみ | | システム固有 | |
| ライブ API キー | `payment_ca/eway/live_api_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| ライブ API パスワード | `payment_ca/eway/live_api_password` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| ライブクライアントサイド暗号化キー | `payment_ca/eway/live_encryption_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| サンドボックス API キー | `payment_ca/eway/sandbox_api_key` | Commerce Enterpriseのみ | 暗号化 | | 機密 |
| サンドボックス API パスワード | `payment_ca/eway/sandbox_api_password` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| サンドボックスのクライアントサイド暗号化キー | `payment_ca/eway/sandbox_encryption_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| トランザクションキー | `payment_hk/authorizenet_directpost/trans_key` |  | 暗号化 | システム固有 | 機密 |
| テストモード | `payment_hk/authorizenet_directpost/test` |  | | システム固有 | |
| ゲートウェイ URL | `payment_hk/authorizenet_directpost/cgi_url` |  | | | 機密 |
| トランザクション詳細URL | `payment_hk/authorizenet_directpost/cgi_url_td` |  | | システム固有 | 機密 |
| トランザクションキー | `payment_hk/cybersource/transaction_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| アクセスキー | `payment_hk/cybersource/access_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| 秘密鍵 | `payment_hk/cybersource/secret_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| テストモード | `payment_hk/cybersource/sandbox_flag` | Commerce Enterpriseのみ | | システム固有 | 機密 |
| 支払い応答パスワード | `payment_hk/worldpay/response_password` | Commerce Enterpriseのみ | | システム固有 | 機密 |
| リモート管理者認証パスワード | `payment_hk/worldpay/auth_password` | Commerce Enterpriseのみ | | システム固有 | 機密 |
| テストモード | `payment_hk/worldpay/sandbox_flag` | Commerce Enterpriseのみ | | システム固有 | 機密 |
| ライブ API キー | `payment_hk/eway/live_api_key` | Commerce Enterpriseのみ | 暗号化 | | 機密 |
| ライブ API パスワード | `payment_hk/eway/live_api_password` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| ライブクライアントサイド暗号化キー | `payment_hk/eway/live_encryption_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| サンドボックス API キー | `payment_hk/eway/sandbox_api_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| サンドボックス API パスワード | `payment_hk/eway/sandbox_api_password` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| サンドボックスのクライアントサイド暗号化キー | `payment_hk/eway/sandbox_encryption_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| トランザクションキー | `payment_jp/authorizenet_directpost/trans_key` |  | 暗号化 | システム固有 | 機密 |
| テストモード | `payment_jp/authorizenet_directpost/test` |  | | システム固有 | |
| ゲートウェイ URL | `payment_jp/authorizenet_directpost/cgi_url` |  | | システム固有 | 機密 |
| トランザクション詳細URL | `payment_jp/authorizenet_directpost/cgi_url_td` |  | | システム固有 | 機密 |
| トランザクションキー | `payment_jp/cybersource/transaction_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| アクセスキー | `payment_jp/cybersource/access_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| 秘密鍵 | `payment_jp/cybersource/secret_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| 新規注文ステータス | `payment_jp/cybersource/order_status` | Commerce Enterpriseのみ | | システム固有 | |
| テストモード | `payment_jp/cybersource/sandbox_flag` | Commerce Enterpriseのみ | | システム固有 | |
| 支払い応答パスワード | `payment_jp/worldpay/response_password` | Commerce Enterpriseのみ | | システム固有 | 機密 |
| リモート管理者認証パスワード | `payment_jp/worldpay/auth_password` | Commerce Enterpriseのみ | | システム固有 | 機密 |
| テストモード | `payment_jp/worldpay/sandbox_flag` | Commerce Enterpriseのみ | | システム固有 | |
| サンドボックスモード | `payment_jp/eway/sandbox_flag` | Commerce Enterpriseのみ | | システム固有 | |
| ライブ API キー | `payment_jp/eway/live_api_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| ライブ API パスワード | `payment_jp/eway/live_api_password` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| ライブクライアントサイド暗号化キー | `payment_jp/eway/live_encryption_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| サンドボックス API キー | `payment_jp/eway/sandbox_api_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| サンドボックス API パスワード | `payment_jp/eway/sandbox_api_password` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| サンドボックスのクライアントサイド暗号化キー | `payment_jp/eway/sandbox_encryption_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| トランザクションキー | `payment_fr/authorizenet_directpost/trans_key` |  | 暗号化 | システム固有 | 機密 |
| テストモード | `payment_fr/authorizenet_directpost/test` |  | | システム固有 | |
| ゲートウェイ URL | `payment_fr/authorizenet_directpost/cgi_url` |  | | システム固有 | 機密 |
| トランザクション詳細URL | `payment_fr/authorizenet_directpost/cgi_url_td` |  | | システム固有 | 機密 |
| トランザクションキー | `payment_fr/cybersource/transaction_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| アクセスキー | `payment_fr/cybersource/access_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| 秘密鍵 | `payment_fr/cybersource/secret_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| テストモード | `payment_fr/cybersource/sandbox_flag` | Commerce Enterpriseのみ | | システム固有 | |
| 支払い応答パスワード | `payment_fr/worldpay/response_password` | Commerce Enterpriseのみ | | システム固有 | 機密 |
| リモート管理者認証パスワード | `payment_fr/worldpay/auth_password` | Commerce Enterpriseのみ | | システム固有 | 機密 |
| テストモード | `payment_fr/worldpay/sandbox_flag` | Commerce Enterpriseのみ |  | システム固有 | |
| サンドボックスモード | `payment_fr/eway/sandbox_flag` | Commerce Enterpriseのみ | | システム固有 | |
| ライブ API キー | `payment_fr/eway/live_api_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| ライブ API パスワード | `payment_fr/eway/live_api_password` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| ライブクライアントサイド暗号化キー | `payment_fr/eway/live_encryption_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| サンドボックス API キー | `payment_fr/eway/sandbox_api_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| サンドボックス API パスワード | `payment_fr/eway/sandbox_api_password` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| サンドボックスのクライアントサイド暗号化キー | `payment_fr/eway/sandbox_encryption_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| トランザクションキー | `payment_it/authorizenet_directpost/trans_key` |  | 暗号化 | システム固有 | 機密 |
| テストモード | `payment_it/authorizenet_directpost/test` |  | | システム固有 | |
| ゲートウェイ URL | `payment_it/authorizenet_directpost/cgi_url` |  | | システム固有 | 機密 |
| トランザクション詳細URL | `payment_it/authorizenet_directpost/cgi_url_td` |  | | システム固有 | 機密 |
| トランザクションキー | `payment_it/cybersource/transaction_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| アクセスキー | `payment_it/cybersource/access_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| 秘密鍵 | `payment_it/cybersource/secret_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| テストモード | `payment_it/cybersource/sandbox_flag` | Commerce Enterpriseのみ | | システム固有 | |
| 支払い応答パスワード | `payment_it/worldpay/response_password` | Commerce Enterpriseのみ | | システム固有 | 機密 |
| リモート管理者認証パスワード | `payment_it/worldpay/auth_password` | Commerce Enterpriseのみ | | システム固有 | 機密 |
| テストモード | `payment_it/worldpay/sandbox_flag` | Commerce Enterpriseのみ | | システム固有 | |
| サンドボックスモード | `payment_it/eway/sandbox_flag` | Commerce Enterpriseのみ | | システム固有 | |
| ライブ API キー | `payment_it/eway/live_api_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| ライブ API パスワード | `payment_it/eway/live_api_password` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| ライブクライアントサイド暗号化キー | `payment_it/eway/live_encryption_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| サンドボックス API キー | `payment_it/eway/sandbox_api_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| サンドボックス API パスワード | `payment_it/eway/sandbox_api_password` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| サンドボックスのクライアントサイド暗号化キー | `payment_it/eway/sandbox_encryption_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| API キー | `fraud_protection/signifyd/api_key` | Commerce Enterpriseのみ | 暗号化 | システム固有 | 機密 |
| API URL | `fraud_protection/signifyd/api_url` | Commerce Enterpriseのみ |  | システム固有 | 機密 |
| SFTP資格情報 | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 機密 |
| SFTP資格情報 | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 機密 |
| SFTP資格情報 | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | 機密 |
| API ログイン ID | `payment_au/authorizenet_directpost/login` |  | 暗号化 | | 機密 |
| マーチャント MD5 | `payment_au/authorizenet_directpost/trans_md5` |  | 暗号化 | | 機密 |
| 電子メール顧客 | `payment_au/authorizenet_directpost/email_customer` |  | | | 機密 |
| 加盟店のメール | `payment_au/authorizenet_directpost/merchant_email` |  | | | 機密 |
| リモート管理者インストール ID | `payment_au/worldpay/admin_installation_id` | Commerce Enterpriseのみ | | | 機密 |
| トランザクションのMD5 シークレット | `payment_au/worldpay/md5_secret` | Commerce Enterpriseのみ | | | 機密 |
| SFTP資格情報 | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 機密 |
| SFTP資格情報 | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | 機密 |
| SFTP資格情報 | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 機密 |
| 小切手の送信先 | `payment_es/checkmo/mailing_address` |  | | | 機密 |
| API ログイン ID | `payment_es/authorizenet_directpost/login` |  | 暗号化 | | 機密 |
| マーチャント MD5 | `payment_es/authorizenet_directpost/trans_md5` |  | 暗号化 | | 機密 |
| 電子メール顧客 | `payment_es/authorizenet_directpost/email_customer` |  | | | 機密 |
| 加盟店のメール | `payment_es/authorizenet_directpost/merchant_email` |  | | | 機密 |
| 加盟店ID | `payment_es/cybersource/merchant_id` | Commerce Enterpriseのみ | 暗号化 | | 機密 |
| プロファイル ID | `payment_es/cybersource/profile_id` | Commerce Enterpriseのみ | 暗号化 | | 機密 |
| リモート管理者インストール ID | `payment_es/worldpay/admin_installation_id` | Commerce Enterpriseのみ | | | 機密 |
| SFTP資格情報 | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 機密 |
| SFTP資格情報 | | | | | |
| SFTP資格情報 | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 機密 |
| SFTP資格情報 | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | 機密 |
| API ログイン ID | `payment_nz/authorizenet_directpost/login` |  | 暗号化 | | 機密 |
| マーチャント MD5 | `payment_nz/authorizenet_directpost/trans_md5` |  | 暗号化 | | 機密 |
| 電子メール顧客 | `payment_nz/authorizenet_directpost/email_customer` |  | | | 機密 |
| 加盟店のメール | `payment_nz/authorizenet_directpost/merchant_email` |  | | | 機密 |
| 加盟店ID | `payment_nz/cybersource/merchant_id` | Commerce Enterpriseのみ | 暗号化 | | 機密 |
| トランザクションキー | `payment_nz/cybersource/transaction_key` | Commerce Enterpriseのみ | 暗号化 | | 機密 |
| プロファイル ID | `payment_nz/cybersource/profile_id` | Commerce Enterpriseのみ | 暗号化 | | 機密 |
| アクセスキー | `payment_nz/cybersource/access_key` | Commerce Enterpriseのみ | 暗号化 | | 機密 |
| 秘密鍵 | `payment_nz/cybersource/secret_key` | Commerce Enterpriseのみ | 暗号化 | | 機密 |
| インストール ID | `payment_nz/worldpay/installation_id` | Commerce Enterpriseのみ | | | 機密 |
| 支払い応答パスワード | `payment_nz/worldpay/response_password` | Commerce Enterpriseのみ | | | 機密 |
| リモート管理者インストール ID | `payment_nz/worldpay/admin_installation_id` | Commerce Enterpriseのみ | | | 機密 |
| リモート管理者認証パスワード | `payment_nz/worldpay/auth_password` | Commerce Enterpriseのみ | | | 機密 |
| トランザクションのMD5 シークレット | `payment_nz/worldpay/md5_secret` | Commerce Enterpriseのみ | | | 機密 |
| SFTP資格情報 | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 機密 |
| SFTP資格情報 | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_sftp` |  | | | 機密 |
| SFTP資格情報 | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | 機密 |
| SFTP資格情報 | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 機密 |
| SFTP資格情報 | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | 機密 |
| SFTP資格情報 | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` |  | | | 機密 |
| API ログイン ID | `payment_us/authorizenet_directpost/login` |  | 暗号化 | | 機密 |
| トランザクションキー | `payment_us/authorizenet_directpost/trans_key` |  | 暗号化 | | 機密 |
| マーチャント MD5 | `payment_us/authorizenet_directpost/trans_md5` |  | 暗号化 | | 機密 |
| 電子メール顧客 | `payment_us/authorizenet_directpost/email_customer` |  | | | 機密 |
| 加盟店のメール | `payment_us/authorizenet_directpost/merchant_email` |  | | | 機密 |
| 加盟店ID | `payment_us/cybersource/merchant_id` | Commerce Enterpriseのみ | 暗号化 | | 機密 |
| トランザクションキー | `payment_us/cybersource/transaction_key` | Commerce Enterpriseのみ | 暗号化 | | 機密 |
| プロファイル ID | `payment_us/cybersource/profile_id` | Commerce Enterpriseのみ | 暗号化 | | 機密 |
| インストール ID | `payment_us/worldpay/installation_id` | Commerce Enterpriseのみ | | | 機密 |
| 支払い応答パスワード | `payment_us/worldpay/response_password` | Commerce Enterpriseのみ | | | 機密 |
| リモート管理者インストール ID | `payment_us/worldpay/admin_installation_id` | Commerce Enterpriseのみ | | | 機密 |
| リモート管理者認証パスワード | `payment_us/worldpay/auth_password` | Commerce Enterpriseのみ | | | 機密 |
| トランザクションのMD5 シークレット | `payment_us/worldpay/md5_secret` | Commerce Enterpriseのみ | | | 機密 |
| SFTP資格情報 | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  |  | | 機密 |
| SFTP資格情報 | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | 機密 |
| SFTP資格情報 | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 機密 |
| 小切手の送信先 | `payment_gb/checkmo/mailing_address` |  | | | 機密 |
| 加盟店ID | `payment_gb/cybersource/merchant_id` | Commerce Enterpriseのみ | 暗号化 | | 機密 |
| トランザクションキー | `payment_gb/cybersource/transaction_key` | Commerce Enterpriseのみ | 暗号化 | | 機密 |
| プロファイル ID | `payment_gb/cybersource/profile_id` | Commerce Enterpriseのみ | 暗号化 | | 機密 |
| アクセスキー | `payment_gb/cybersource/access_key` | Commerce Enterpriseのみ | 暗号化 | | 機密 |
| 秘密鍵 | `payment_gb/cybersource/secret_key` | Commerce Enterpriseのみ | 暗号化 | | 機密 |
| API ログイン ID | `payment_gb/authorizenet_directpost/login` |  | 暗号化 | | 機密 |
| トランザクションキー | `payment_gb/authorizenet_directpost/trans_key` |  | 暗号化 | | 機密 |
| マーチャント MD5 | `payment_gb/authorizenet_directpost/trans_md5` |  | 暗号化 | | 機密 |
| 電子メール顧客 | `payment_gb/authorizenet_directpost/email_customer` |  | | | 機密 |
| 加盟店のメール | `payment_gb/authorizenet_directpost/merchant_email` |  |  | | 機密 |
| インストール ID | `payment_gb/worldpay/installation_id` | Commerce Enterpriseのみ | | | 機密 |
| 支払い応答パスワード | `payment_gb/worldpay/response_password` | Commerce Enterpriseのみ | | | 機密 |
| リモート管理者インストール ID | `payment_gb/worldpay/admin_installation_id` | Commerce Enterpriseのみ | | | 機密 |
| リモート管理者認証パスワード | `payment_gb/worldpay/auth_password` | Commerce Enterpriseのみ | | | 機密 |
| SFTP資格情報 | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 機密 |
| 小切手の支払先 | `payment_de/checkmo/payable_to` |  | | | 機密 |
| 小切手の送信先 | `payment_de/checkmo/mailing_address` |  | | | 機密 |
| 加盟店ID | `payment_de/cybersource/merchant_id` | Commerce Enterpriseのみ | 暗号化 | | 機密 |
| プロファイル ID | `payment_de/cybersource/profile_id` | Commerce Enterpriseのみ | 暗号化 | | 機密 |
| API ログイン ID | `payment_de/authorizenet_directpost/login` |  | 暗号化 | | 機密 |
| マーチャント MD5 | `payment_de/authorizenet_directpost/trans_md5` |  | 暗号化 | | 機密 |
| 電子メール顧客 | `payment_de/authorizenet_directpost/email_customer` |  | | | 機密 |
| 加盟店のメール | `payment_de/authorizenet_directpost/merchant_email` |  | | | 機密 |
| インストール ID | `payment_de/worldpay/installation_id` | Commerce Enterpriseのみ | | | |
| リモート管理者インストール ID | `payment_de/worldpay/admin_installation_id` | Commerce Enterpriseのみ | | | 機密 |
| トランザクションのMD5 シークレット | `payment_de/worldpay/md5_secret` | Commerce Enterpriseのみ | | | 機密 |
| SFTP資格情報 | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  |  | | 機密 |
| SFTP資格情報 | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 機密 |
| 小切手の支払先 | `payment_other/checkmo/payable_to` |  | | | 機密 |
| 小切手の送信先 | `payment_other/checkmo/mailing_address` |  | | | 機密 |
| API ログイン ID | `payment_other/authorizenet_directpost/login` |  | 暗号化 | | 機密 |
| マーチャント MD5 | `payment_other/authorizenet_directpost/trans_md5` |  | 暗号化 | | 機密 |
| 新規注文ステータス | `payment_other/authorizenet_directpost/order_status` |  | | | 機密 |
| 加盟店のメール | `payment_other/authorizenet_directpost/merchant_email` |  | | | 機密 |
| 加盟店ID | `payment_other/cybersource/merchant_id` | Commerce Enterpriseのみ | 暗号化 | | 機密 |
| プロファイル ID | `payment_other/cybersource/profile_id` | Commerce Enterpriseのみ | 暗号化 | | 機密 |
| インストール ID | `payment_other/worldpay/installation_id` | Commerce Enterpriseのみ | | | 機密 |
| リモート管理者インストール ID | `payment_other/worldpay/admin_installation_id` | Commerce Enterpriseのみ | | | 機密 |
| トランザクションのMD5 シークレット | `payment_other/worldpay/md5_secret` | Commerce Enterpriseのみ | | | 機密 |
| SFTP資格情報 | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 機密 |
| SFTP資格情報 | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 機密 |
| SFTP資格情報 | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | 機密 |
| SFTP資格情報 | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | 機密 |
| SFTP資格情報 | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` |  | | | 機密 |
| 小切手の支払先 | `payment_ca/checkmo/payable_to` |  | | | 機密 |
| 小切手の送信先 | `payment_ca/checkmo/mailing_address` |  | | | 機密 |
| API ログイン ID | `payment_ca/authorizenet_directpost/login` |  | 暗号化 | | 機密 |
| マーチャント MD5 | `payment_ca/authorizenet_directpost/trans_md5` |  | 暗号化 | | 機密 |
| 新規注文ステータス | `payment_ca/authorizenet_directpost/order_status` |  | | | 機密 |
| 電子メール顧客 | `payment_ca/authorizenet_directpost/email_customer` |  | | | 機密 |
| 加盟店のメール | `payment_ca/authorizenet_directpost/merchant_email` |  | | | 機密 |
| 加盟店ID | `payment_ca/cybersource/merchant_id` | Commerce Enterpriseのみ | 暗号化 | | 機密 |
| プロファイル ID | `payment_ca/cybersource/profile_id` | Commerce Enterpriseのみ | 暗号化 | | 機密 |
| インストール ID | `payment_ca/worldpay/installation_id` | Commerce Enterpriseのみ | | | 機密 |
| リモート管理者インストール ID | `payment_ca/worldpay/admin_installation_id` | Commerce Enterpriseのみ | | | 機密 |
| トランザクションのMD5 シークレット | `payment_ca/worldpay/md5_secret` | Commerce Enterpriseのみ | | | 機密 |
| SFTP資格情報 | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 機密 |
| SFTP資格情報 | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  |  | | 機密 |
| SFTP資格情報 | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 機密 |
| 小切手の支払先 | `payment_hk/checkmo/payable_to` |  | | | 機密 |
| 小切手の送信先 | `payment_hk/checkmo/mailing_address` |  | | | 機密 |
| API ログイン ID | `payment_hk/authorizenet_directpost/login` |  | 暗号化 | | 機密 |
| マーチャント MD5 | `payment_hk/authorizenet_directpost/trans_md5` |  | 暗号化 | | 機密 |
| 電子メール顧客 | `payment_hk/authorizenet_directpost/email_customer` |  | | | 機密 |
| 加盟店のメール | `payment_hk/authorizenet_directpost/merchant_email` |  | | | 機密 |
| 加盟店ID | `payment_hk/cybersource/merchant_id` | Commerce Enterpriseのみ | 暗号化 | | 機密 |
| プロファイル ID | `payment_hk/cybersource/profile_id` | Commerce Enterpriseのみ | 暗号化 | | 機密 |
| インストール ID | `payment_hk/worldpay/installation_id` | Commerce Enterpriseのみ | | | 機密 |
| リモート管理者インストール ID | `payment_hk/worldpay/admin_installation_id` | Commerce Enterpriseのみ | | | 機密 |
| トランザクションのMD5 シークレット | `payment_hk/worldpay/md5_secret` | Commerce Enterpriseのみ | | | 機密 |
| 署名フィールド | `payment_hk/worldpay/signature_fields` | Commerce Enterpriseのみ | | | 機密 |
| SFTP資格情報 | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 機密 |
| SFTP資格情報 | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | 機密 |
| SFTP資格情報 | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 機密 |
| 小切手の支払先 | `payment_jp/checkmo/payable_to` |  | | | 機密 |
| 小切手の送信先 | `payment_jp/checkmo/mailing_address` |  | | | 機密 |
| API ログイン ID | `payment_jp/authorizenet_directpost/login` |  | 暗号化 | | 機密 |
| マーチャント MD5 | `payment_jp/authorizenet_directpost/trans_md5` |  | 暗号化 | | 機密 |
| 電子メール顧客 | `payment_jp/authorizenet_directpost/email_customer` |  | | | 機密 |
| 加盟店のメール | `payment_jp/authorizenet_directpost/merchant_email` |  | | | 機密 |
| 加盟店ID | `payment_jp/cybersource/merchant_id` | Commerce Enterpriseのみ | 暗号化 | | 機密 |
| プロファイル ID | `payment_jp/cybersource/profile_id` | Commerce Enterpriseのみ | 暗号化 | | 機密 |
| インストール ID | `payment_jp/worldpay/installation_id` | Commerce Enterpriseのみ | | | |
| リモート管理者インストール ID | `payment_jp/worldpay/admin_installation_id` | Commerce Enterpriseのみ | | | 機密 |
| トランザクションのMD5 シークレット | `payment_jp/worldpay/md5_secret` | Commerce Enterpriseのみ | | | 機密 |
| 署名フィールド | `payment_jp/worldpay/signature_fields` | Commerce Enterpriseのみ | | | 機密 |
| SFTP資格情報 | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 機密 |
| SFTP資格情報 | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | 機密 |
| SFTP資格情報 | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 機密 |
| 小切手の支払先 | `payment_fr/checkmo/payable_to` |  | | | 機密 |
| 小切手の送信先 | `payment_fr/checkmo/mailing_address` |  | | | 機密 |
| API ログイン ID | `payment_fr/authorizenet_directpost/login` |  | 暗号化 | | 機密 |
| マーチャント MD5 | `payment_fr/authorizenet_directpost/trans_md5` |  | 暗号化 | | 機密 |
| 電子メール顧客 | `payment_fr/authorizenet_directpost/email_customer` |  | | | 機密 |
| 加盟店のメール | `payment_fr/authorizenet_directpost/merchant_email` |  | | | 機密 |
| 加盟店ID | `payment_fr/cybersource/merchant_id` | Commerce Enterpriseのみ | 暗号化 | | 機密 |
| プロファイル ID | `payment_fr/cybersource/profile_id` | Commerce Enterpriseのみ | 暗号化 | | 機密 |
| インストール ID | `payment_fr/worldpay/installation_id` | Commerce Enterpriseのみ | | | 機密 |
| リモート管理者インストール ID | `payment_fr/worldpay/admin_installation_id` | Commerce Enterpriseのみ | | | 機密 |
| トランザクションのMD5 シークレット | `payment_fr/worldpay/md5_secret` | Commerce Enterpriseのみ | | | 機密 |
| 署名フィールド | `payment_fr/worldpay/signature_fields` | Commerce Enterpriseのみ | | | 機密 |
| SFTP資格情報 | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 機密 |
| SFTP資格情報 | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | 機密 |
| SFTP資格情報 | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | 機密 |
| 小切手の支払先 | `payment_it/checkmo/payable_to` |  | | | 機密 |
| 小切手の送信先 | `payment_it/checkmo/mailing_address` |  | | | 機密 |
| API ログイン ID | `payment_it/authorizenet_directpost/login` |  | 暗号化 | | 機密 |
| マーチャント MD5 | `payment_it/authorizenet_directpost/trans_md5` |  | 暗号化 | | 機密 |
| 電子メール顧客 | `payment_it/authorizenet_directpost/email_customer` |  | | | 機密 |
| 加盟店のメール | `payment_it/authorizenet_directpost/merchant_email` |  | | | 機密 |
| 加盟店ID | `payment_it/cybersource/merchant_id` | Commerce Enterpriseのみ | 暗号化 | | 機密 |
| プロファイル ID | `payment_it/cybersource/profile_id` | Commerce Enterpriseのみ | 暗号化 | | 機密 |
| インストール ID | `payment_it/worldpay/installation_id` | Commerce Enterpriseのみ | | | 機密 |
| リモート管理者インストール ID | `payment_it/worldpay/admin_installation_id` | Commerce Enterpriseのみ | | | 機密 |
| トランザクションのMD5 シークレット | `payment_it/worldpay/md5_secret` | Commerce Enterpriseのみ | | | 機密 |

{style="table-layout:auto"}
