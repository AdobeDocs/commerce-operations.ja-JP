---
title: 機密パスとシステム固有のパス
description: システム固有の設定値や機密性の高い設定値のリストを参照してください。
feature: Configuration, System
exl-id: 127880ab-7507-4e53-8b51-dfa6557d0b18
source-git-commit: e5a1c5634124831c8d5a95df6818ec30c372e8dd
workflow-type: tm+mt
source-wordcount: '3676'
ht-degree: 0%

---

# 機密およびシステム固有の設定

このトピックでは、システム固有の設定や機密性の高い設定の構成パスを示します。

- [`magento app:config:dump` コマンドは ](../cli/export-configuration.md) システム固有の設定をシステム固有の構成ファイル `app/etc/env.php` に書き込みます。このファイルはソース管理下に _る_ べきではありません。 また、すべてのCommerce インスタンスの共有設定を `app/etc/config.php` に書き込みます。このファイルは _ソース管理_ になっている必要があります。
- [`magento config:sensitive:set` コマンドは ](../cli/set-configuration-values.md) 重要な設定を `app/etc/env.php` に書き込みます。

  [ 環境変数を使用して構成設定を上書きする ](../reference/override-config-settings.md#environment-variables) で説明されているように、環境変数を使用して機密性の高い値を設定することもできます。

その他の設定パスのリストについては、以下を参照してください。

- [支払いを除くすべての構成パス](../reference/config-reference-general.md)
- [ 支払い設定パス ](../reference/config-reference-payment.md)。

>[!INFO]
>
>このトピックにリストされている設定パスはすべて大文字と小文字が区別されます。 `System-specific?` の列は、どの値もシステムに固有であるかを示します。

## 一般的なカテゴリ依存パスとシステム固有のパス

この節では、**ストア**/設定/**設定**/**一般** の管理でオプションに使用できる変数名と設定パスを示します。

### Web パスを区別するパスとシステム固有のパス

これらの設定値は、管理者の **ストア**/設定/**設定**/**一般**/**Web** で利用できます。

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ | システム固有？ | 機密？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| ベース URL | `web/unsecure/base_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| ベースリンク URL | `web/unsecure/base_link_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| 静的ビューファイルのベース URL | `web/unsecure/base_static_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| ユーザーメディアファイルのベース URL | `web/unsecure/base_media_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| セキュアなベース URL | `web/secure/base_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| セキュアベースリンク URL | `web/secure/base_link_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| 静的ビューファイルのセキュア ベース URL | `web/secure/base_static_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| ユーザーメディアファイルのセキュアベース URL | `web/secure/base_media_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| 既定の Web URL | `web/default/front` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| デフォルトのルートなし URL | `web/default/no_route` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| Cookie のパス | `web/cookie/cookie_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| Cookie ドメイン | `web/cookie/cookie_domain` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| Cookie の有効期間 | `web/cookie/cookie_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| HTTP のみを使用 | `web/cookie/cookie_httponly` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| Cookie 制限モード | `web/cookie/cookie_restriction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

### 通貨設定に依存するパスとシステム固有のパス

これらの設定値は、管理者の **ストア**/設定/**設定**/**一般**/**通貨設定** で使用できます。

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ | システム固有？ | 機密？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| エラーの E メール受信者 | `currency/import/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### メールアドレスを区別するパスとシステム固有のパスを保存する

これらの設定値は、管理者の **ストア**/設定/**E メール設定**/**一般**/**E メールアドレスを保存** で使用できます。

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ | システム固有？ | 機密？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 送信者名 | `trans_email/ident_general/name` | | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 送信者のメール | `trans_email/ident_general/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 送信者名 | `trans_email/ident_sales/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 送信者のメール | `trans_email/ident_sales/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 送信者名 | `trans_email/ident_support/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 送信者のメール | `trans_email/ident_support/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 送信者名 | `trans_email/ident_custom1/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 送信者のメール | `trans_email/ident_custom1/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 送信者名 | `trans_email/ident_custom2/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 送信者のメール | `trans_email/ident_custom2/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### 連絡先の機密パスとシステム固有のパス

これらの設定値は、管理者の **ストア**/設定/**設定**/**一般**/**連絡先** で利用できます。

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ | システム固有？ | 機密？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Send Emails To | `contact/email/recipient_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| E メール送信者 | `contact/email/sender_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| E メール テンプレート | `contact/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### New Relic レポートの機密パスとシステム固有のパス

これらの設定値は、管理者の **ストア**/設定/**設定**/**一般**/6&rbrace;New Relic レポート **で利用できます。**

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ | システム固有？ | 機密？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| New Relic アカウント ID | `newrelicreporting/general/account_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| New Relic アプリケーション ID | `newrelicreporting/general/app_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| New Relic API キー | `newrelicreporting/general/api` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| Insights API キー | `newrelicreporting/general/insights_insert_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| New Relic API の URL | `newrelicreporting/general/api_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| インサイト API の URL | `newrelicreporting/general/insights_api_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## 顧客カテゴリ依存のパスとシステム固有のパス

この節では、**ストア**/設定/**設定**/**顧客** の管理でオプションに使用できる変数名と設定パスを示します。

### 顧客設定に依存する、システム固有のパス

これらの設定値は、管理者の **ストア**/設定/**設定**/**顧客**/**顧客設定** で利用できます。

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ | システム固有？ | 機密？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| デフォルトのメールドメイン | `customer/create_account/email_domain` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

## カタログカテゴリ

この節では、**ストア**/設定/**設定**/**カタログ** の管理でオプションに使用できる変数名と設定パスを示します。

### カタログに依存するパスとシステム固有のパス

これらの設定値は、管理者の **ストア**/設定/**設定**/**カタログ**/**カタログ** で使用できます。

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ | システム固有？ | 機密？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| エラーの E メール受信者 | `catalog/productalert_cron/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| YouTube API キー | `catalog/product_video/youtube_api_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| Solr サーバーホスト名 | `catalog/search/solr_server_hostname` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| Solr サーバーポート | `catalog/search/solr_server_port` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| Solr サーバーのユーザー名 | `catalog/search/solr_server_username` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| Solr サーバーのパスワード | `catalog/search/solr_server_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| Solr サーバーのパス | `catalog/search/solr_server_path` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| Elasticsearch Server Hostname | `catalog/search/elasticsearch_server_hostname` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| Elasticsearch サーバーポート | `catalog/search/elasticsearch_server_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| Elasticsearch インデックスプレフィックス | `catalog/search/elasticsearch_index_prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| Elasticsearch HTTP 認証を有効にする | `catalog/search/elasticsearch_enable_auth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| Elasticsearch HTTP ユーザー名 | `catalog/search/elasticsearch_username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| Elasticsearch HTTP パスワード | `catalog/search/elasticsearch_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| Elasticsearch Server Timeout | `catalog/search/elasticsearch_server_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| Elasticsearch HTTP ユーザー名 | `catalog/search/elasticsearch_username` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| Elasticsearch HTTP パスワード | `catalog/search/elasticsearch_password` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| Elasticsearch Server Timeout | `catalog/search/elasticsearch_server_timeout` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| OpenSearch Server Hostname | `catalog/search/opensearch_server_hostname` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| OpenSearch サーバーポート | `catalog/search/opensearch_server_port` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| OpenSearch インデックス プレフィックス | `catalog/search/opensearch_index_prefix` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| OpenSearch HTTP 認証を有効にする | `catalog/search/opensearch_enable_auth` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| OpenSearch HTTP ユーザー名 | `catalog/search/opensearch_username` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| OpenSearch HTTP パスワード | `catalog/search/opensearch_password` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| OpenSearch Server タイムアウト | `catalog/search/opensearch_server_timeout` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

>[!NOTE]
>
>OpenSearch 設定は、Adobe Commerce 2.4.6 で導入されました。

### 在庫機密のパスとシステム固有のパス

これらの設定値は、管理者の **ストア**/設定/**設定**/**カタログ**/**在庫** で使用できます。

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ | システム固有？ | 機密？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Google API キー | `cataloginventory/source_selection_distance_based_google/api_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### XML サイトマップを区別するパスとシステム固有のパス

これらの設定値は、管理者の **ストア**/設定/**設定**/**カタログ**/**XML サイトマップ** で使用できます。

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ | システム固有？ | 機密？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| エラーの E メール受信者 | `sitemap/generate/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## 販売カテゴリ

このセクションでは、**ストア**/設定/**設定**/**セールス** の管理でオプションに使用できる変数名と設定パスを示します。

### 出荷設定に依存するパスおよびシステム固有のパス

これらの設定値は、管理者の **Stores**/設定/**Configuration**/**Sales**/**Shipping Settings** で使用できます。

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ | システム固有？ | 機密？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 国 | `shipping/origin/country_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 地域/都道府県 | `shipping/origin/region_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 郵便番号 | `shipping/origin/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 市区町村 | `shipping/origin/city` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 番地 | `shipping/origin/street_line1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 住所 2 | `shipping/origin/street_line2` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| Live アカウント | `carriers/ups/is_account_live` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

### 販売 E メールに関する機密パスとシステム固有のパス

これらの設定値は、管理者の **Stores**/設定/**Configuration**/**Sales**/**Sales Emails** で使用できます。

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ | システム固有？ | 機密？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 注文 E メール コピーの送信先 | `sales_email/order/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 注文コメントの E メール コピーの送信先 | `sales_email/order_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 請求書 E メール コピーの送信先 | `sales_email/invoice/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 請求書コメント E メール コピーの送信先 | `sales_email/invoice_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 出荷電子メールのコピーの送信先 | `sales_email/shipment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 出荷コメント E メール コピーの送信先 | `sales_email/shipment_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| クレジット メモ E メール コピーの送信先 | `sales_email/creditmemo/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| クレジット メモ コメント E メール コピーの送信先 | `sales_email/creditmemo_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 集荷準備完了 E メールのコピーの送信先 | `sales_email/temando_pickup/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### チェックアウト時に区別されるパスとシステム固有のパス

これらの設定値は、管理者の **ストア**/設定/**設定**/**営業**/**チェックアウト** で利用できます。

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ | システム固有？ | 機密？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 支払失敗 E メールのコピーの送信先 | `checkout/payment_failed/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Google API を区別するパスとシステム固有のパス

これらの設定値は、管理者の **Stores**/設定/**Configuration**/**Sales**/6&rbrace;Google API **で利用できます。**

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ | システム固有？ | 機密？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| コンテナ Id | `google/analytics/container_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### 配信方法に依存する、システム固有のパス

これらの設定値は、管理者の **ストア**/設定/**設定**/**営業**/**配信方法** で使用できます。

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ | システム固有？ | 機密？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| ゲートウェイ URL | `carriers/usps/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| Secure Gateway URL | `carriers/usps/gateway_secure_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| タイトル | `carriers/usps/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ユーザー ID | `carriers/usps/userid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| パスワード | `carriers/usps/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| ユーザー ID | `carriers/ups/username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| パスワード | `carriers/ups/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| アクセス ライセンス番号 | `carriers/ups/access_license_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トラッキング XML URL | `carriers/ups/tracking_xml_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| ゲートウェイ XML URL | `carriers/ups/gateway_xml_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 荷送人番号 | `carriers/ups/shipper_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| デバッグ | `carriers/ups/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| アカウント ID | `carriers/fedex/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| キー | `carriers/fedex/key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| メートル番号 | `carriers/fedex/meter_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| パスワード | `carriers/fedex/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| アクセス ID | `carriers/dhl/id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| パスワード | `carriers/dhl/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| デバッグ | `carriers/dhl/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| アカウント番号 | `carriers/dhl/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| ゲートウェイ URL | `carriers/dhl/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| サンドボックスモード | `carriers/fedex/sandbox_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### 営業機密およびシステム固有のパス

これらの設定値は、管理者の **Stores**/設定/**Configuration**/**Sales**/**Sales** で使用できます。

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ | システム固有？ | 機密？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 連絡先名 | `sales/magento_rma/store_name` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 番地 | `sales/magento_rma/address` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 番地 | `sales/magento_rma/address1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 市区町村 | `sales/magento_rma/city` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 都道府県 | `sales/magento_rma/region_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 郵便番号 | `sales/magento_rma/zip` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 国 | `sales/magento_rma/country_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| RMA メールのコピーの送信先 | `sales_email/magento_rma/copy_to` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| RMA 認証メールのコピーの送信先 | `sales_email/magento_rma_auth/copy_to` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| RMA コメントメールのコピーの送信先 | `sales_email/magento_rma_comment/copy_to` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| RMA コメントメールのコピーの送信先 | `sales_email/magento_rma_customer_comment/copy_to` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Google API のパス

これらの設定値は、管理者の **Stores**/設定/**Configuration**/**Sales**/6&rbrace;Google API **で利用できます。**

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ | システム固有？ | 機密？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| アカウント番号 | `google/analytics/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## 詳細カテゴリ

この節では、**ストア**/設定/**設定**/**詳細** の管理でオプションに使用できる変数名と設定パスを示します。

### 管理者を区別するパスとシステム固有のパス

これらの設定値は、管理者の **ストア**/設定/**設定**/**詳細**/**管理** で利用できます。

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ | システム固有？ | 機密？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| カスタム管理 URL | `admin/url/custom` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| カスタム管理パス | `admin/url/custom_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### システム依存パスとシステム固有のパス

これらの設定値は、管理者の **ストア**/設定/**設定**/**詳細**/**システム** で利用できます。

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ | システム固有？ | 機密？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| エラーの E メール受信者 | `system/magento_scheduled_import_export_log/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| アクセスリスト | `system/full_page_cache/varnish/access_list` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| エラーのメール送信者 | `system/magento_scheduled_import_export_log/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### 開発者依存のパスとシステム固有のパス

これらの設定値は、管理者の **ストア**/設定/**設定**/**詳細**/**開発者** で利用できます。

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ | システム固有？ | 機密？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 許可された IP （コンマ区切り） | `dev/restrict/allow_ips` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## 詳細カテゴリ

この節では、**ストア**/設定/**設定**/**詳細** の管理でオプションに使用できる変数名と設定パスを示します。

### システムパス

これらの設定値は、管理者の **ストア**/設定/**設定**/**詳細**/**システム** で利用できます。

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ | システム固有？ | 機密？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| ホスト | `system/smtp/host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| ポート （25） | `system/smtp/port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| バックエンドホスト | `system/full_page_cache/varnish/backend_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| バックエンドポート | `system/full_page_cache/varnish/backend_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### 開発者パス

これらの設定値は、管理者の **ストア**/設定/**設定**/**詳細**/**開発者** で利用できます。

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ | システム固有？ | 機密？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| JS エラーをセッションストレージキーに記録 | `dev/js/session_storage_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

## 支払に依存するパスとシステム固有のパス

この節では、**ストア**/設定/**設定**/**営業**/**支払い** の管理でオプションに使用できる変数名と設定パスを示します。

### 一般変数

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ |
|--------------|--------------|--------------|--------------|
| 商社国 | `paypal/general/merchant_country` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

>[!INFO]
>
>この変数の選択によって、使用できる [ 国際パス ](#international-paths) が決まります。

### PayPal 固有のパスとシステム固有のパス

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ | システム固有？ | 機密？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| PayPal マーチャントアカウントに関連付けられたメール （オプション） | `paypal/general/business_account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| マーチャントアカウント ID | `payment/paypal_express/merchant_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 発行者 ID | `payment/paypal_express_bml/publisher_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| パスワード | `paypal/fetch_reports/ftp_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| ログイン | `paypal/fetch_reports/ftp_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| カスタム エンドポイント ホスト名または IP アドレス | `paypal/fetch_reports/ftp_ip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| サンドボックスモード | `paypal/fetch_reports/ftp_sandbox` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| デバッグモード | `payment/paypal_express/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| デバッグモード | `payment/paypal_billing_agreement/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| SFTP 資格情報 | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### PayPal Payflow Pro 機密およびシステム固有のパス

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ | システム固有？ | 機密？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| ユーザー | `payment/payflow_advanced/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| パスワード | `payment/payflow_advanced/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| カスタムパス | `paypal/fetch_reports/ftp_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| ユーザー | `payment/payflowpro/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| パスワード | `payment/payflowpro/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment/payflowpro/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| パートナー | `payment/payflowpro/partner` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| プロキシホスト | `payment/payflowpro/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| プロキシポート | `payment/payflowpro/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| デバッグモード | `payment/payflowpro/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| SFTP 資格情報 | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| クレジットカードの設定 | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### PayPal Payflow リンク依存およびシステム固有のパス

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ | システム固有？ | 機密？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| ユーザー | `payment/payflow_link/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| パスワード | `payment/payflow_link/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment/payflow_link/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| プロキシを使用 | `payment/payflow_link/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| プロキシホスト | `payment/payflow_link/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| プロキシポート | `payment/payflow_link/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| デバッグモード | `payment/payflow_link/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| URL をキャンセルして URL を返す URL メソッド | `payment/payflow_link/url_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| デバッグモード | `payment/payflow_express/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| SFTP 資格情報 | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### PayPal Payments Pro の機密パスとシステム固有のパス

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ | システム固有？ | 機密？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| API ユーザー名 | `paypal/wpp/api_username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| API パスワード | `paypal/wpp/api_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| API 署名 | `paypal/wpp/api_signature` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| API 証明書 | `paypal/wpp/api_cert` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| プロキシホスト | `paypal/wpp/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| プロキシポート | `paypal/wpp/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| サンドボックスモード | `paypal/wpp/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| SFTP 資格情報 | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### PayPal Payments Pro ホスト型の機密パスおよびシステム固有のパス

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ | システム固有？ | 機密？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| デバッグモード | `payment/hosted_pro/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| SFTP 資格情報 | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Braintreeを区別するパスとシステム固有のパス

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ | システム固有？ | 機密？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| マーチャント ID | `payment/braintree/merchant_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 公開鍵 | `payment/braintree/public_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 秘密鍵 | `payment/braintree/private_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| マーチャントアカウント ID | `payment/braintree/merchant_account_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| Kount マーチャント ID | `payment/braintree/kount_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 商社名を上書き | `payment/braintree_paypal/merchant_name_override` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 電話 | `payment/braintree/descriptor_phone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| URL | `payment/braintree/descriptor_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

### 小切手/為替パス

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ | システム固有？ | 機密？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 小切手の送信先 | `payment/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 小切手の送信先 | `payment_us/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### 国際的な道筋

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ | システム固有？ | 機密？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| トランザクションキー | `payment_au/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_au/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| ゲートウェイ URL | `payment_au/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションの詳細 URL | `payment_au/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_au/cybersource/transaction_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| アクセスキー | `payment_au/cybersource/access_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 秘密鍵 | `payment_au/cybersource/secret_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_au/cybersource/sandbox_flag` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| 支払い応答パスワード | `payment_au/worldpay/response_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| リモート管理承認パスワード | `payment_au/worldpay/auth_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| サンドボックスモード | `payment_au/eway/sandbox_flag` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| Live API キー | `payment_au/eway/live_api_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| Live API パスワード | `payment_au/eway/live_api_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| ライブクライアントサイドの暗号化キー | `payment_au/eway/live_encryption_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| サンドボックス API キー | `payment_au/eway/sandbox_api_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| Sandbox API パスワード | `payment_au/eway/sandbox_api_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| サンドボックスのクライアントサイド暗号化キー | `payment_au/eway/sandbox_encryption_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_es/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_es/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| ゲートウェイ URL | `payment_es/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションの詳細 URL | `payment_es/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_es/cybersource/transaction_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| アクセスキー | `payment_es/cybersource/access_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 秘密鍵 | `payment_es/cybersource/secret_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_es/cybersource/sandbox_flag` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| 支払い応答パスワード | `payment_es/worldpay/response_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| リモート管理承認パスワード | `payment_es/worldpay/auth_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションの MD5 シークレット | `payment_es/worldpay/md5_secret` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| デバッグ | `payment_es/worldpay/debug` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| サンドボックスモード | `payment_es/eway/sandbox_flag` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| Live API キー | `payment_es/eway/live_api_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| Live API パスワード | `payment_es/eway/live_api_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| ライブクライアントサイドの暗号化キー | `payment_es/eway/live_encryption_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| サンドボックス API キー | `payment_es/eway/sandbox_api_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| Sandbox API パスワード | `payment_es/eway/sandbox_api_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| サンドボックスのクライアントサイド暗号化キー | `payment_es/eway/sandbox_encryption_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_nz/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_nz/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| ゲートウェイ URL | `payment_nz/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションの詳細 URL | `payment_nz/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_nz/cybersource/sandbox_flag` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| テストモード | `payment_nz/worldpay/sandbox_flag` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| サンドボックスモード | `payment_nz/eway/sandbox_flag` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| Live API キー | `payment_nz/eway/live_api_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| Live API パスワード | `payment_nz/eway/live_api_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| ライブクライアントサイドの暗号化キー | `payment_nz/eway/live_encryption_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| サンドボックス API キー | `payment_nz/eway/sandbox_api_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| Sandbox API パスワード | `payment_nz/eway/sandbox_api_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| サンドボックスのクライアントサイド暗号化キー | `payment_nz/eway/sandbox_encryption_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment/payflow_advanced/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| プロキシホスト | `payment/payflow_advanced/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| プロキシポート | `payment/payflow_advanced/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| デバッグモード | `payment/payflow_advanced/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| URL をキャンセルして URL を返す URL メソッド | `payment/payflow_advanced/url_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| テストモード | `payment_us/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| ゲートウェイ URL | `payment_us/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションの詳細 URL | `payment_us/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| アクセスキー | `payment_us/cybersource/access_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 秘密鍵 | `payment_us/cybersource/secret_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_us/cybersource/sandbox_flag` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| テストモード | `payment_us/worldpay/sandbox_flag` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| サンドボックスモード | `payment_us/eway/sandbox_flag` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| Live API キー | `payment_us/eway/live_api_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| Live API パスワード | `payment_us/eway/live_api_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| ライブクライアントサイドの暗号化キー | `payment_us/eway/live_encryption_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| サンドボックス API キー | `payment_us/eway/sandbox_api_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| Sandbox API パスワード | `payment_us/eway/sandbox_api_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| サンドボックスのクライアントサイド暗号化キー | `payment_us/eway/sandbox_encryption_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| テストモード | `payment_gb/cybersource/sandbox_flag` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| テストモード | `payment_gb/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| ゲートウェイ URL | `payment_gb/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションの詳細 URL | `payment_gb/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_gb/worldpay/sandbox_flag` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| サンドボックスモード | `payment_gb/eway/sandbox_flag` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| Live API キー | `payment_gb/eway/live_api_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| Live API パスワード | `payment_gb/eway/live_api_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| ライブクライアントサイドの暗号化キー | `payment_gb/eway/live_encryption_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| サンドボックス API キー | `payment_gb/eway/sandbox_api_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| Sandbox API パスワード | `payment_gb/eway/sandbox_api_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| サンドボックスのクライアントサイド暗号化キー | `payment_gb/eway/sandbox_encryption_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_de/cybersource/transaction_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| アクセスキー | `payment_de/cybersource/access_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 秘密鍵 | `payment_de/cybersource/secret_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_de/cybersource/sandbox_flag` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| トランザクションキー | `payment_de/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_de/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| ゲートウェイ URL | `payment_de/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションの詳細 URL | `payment_de/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 支払い応答パスワード | `payment_de/worldpay/response_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| リモート管理承認パスワード | `payment_de/worldpay/auth_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| デバッグ | `payment_de/worldpay/debug` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| サンドボックスモード | `payment_de/eway/sandbox_flag` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| Live API キー | `payment_de/eway/live_api_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| Live API パスワード | `payment_de/eway/live_api_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| ライブクライアントサイドの暗号化キー | `payment_de/eway/live_encryption_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| サンドボックス API キー | `payment_de/eway/sandbox_api_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| Sandbox API パスワード | `payment_de/eway/sandbox_api_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| サンドボックスのクライアントサイド暗号化キー | `payment_de/eway/sandbox_encryption_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_other/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_other/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| ゲートウェイ URL | `payment_other/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションの詳細 URL | `payment_other/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| トランザクションキー | `payment_other/cybersource/transaction_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| アクセスキー | `payment_other/cybersource/access_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 秘密鍵 | `payment_other/cybersource/secret_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 新規注文ステータス | `payment_other/cybersource/order_status` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| テストモード | `payment_other/cybersource/sandbox_flag` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| 支払い応答パスワード | `payment_other/worldpay/response_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| リモート管理承認パスワード | `payment_other/worldpay/auth_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_other/worldpay/sandbox_flag` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| サンドボックスモード | `payment_other/eway/sandbox_flag` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| Live API キー | `payment_other/eway/live_api_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| Live API パスワード | `payment_other/eway/live_api_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| ライブクライアントサイドの暗号化キー | `payment_other/eway/live_encryption_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| サンドボックス API キー | `payment_other/eway/sandbox_api_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| Sandbox API パスワード | `payment_other/eway/sandbox_api_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| サンドボックスのクライアントサイド暗号化キー | `payment_other/eway/sandbox_encryption_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_ca/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_ca/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| ゲートウェイ URL | `payment_ca/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションの詳細 URL | `payment_ca/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_ca/cybersource/transaction_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| アクセスキー | `payment_ca/cybersource/access_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 秘密鍵 | `payment_ca/cybersource/secret_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 新規注文ステータス | `payment_ca/cybersource/order_status` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| テストモード | `payment_ca/cybersource/sandbox_flag` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| 支払い応答パスワード | `payment_ca/worldpay/response_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| リモート管理承認パスワード | `payment_ca/worldpay/auth_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_ca/worldpay/sandbox_flag` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| サンドボックスモード | `payment_ca/eway/sandbox_flag` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| Live API キー | `payment_ca/eway/live_api_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| Live API パスワード | `payment_ca/eway/live_api_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| ライブクライアントサイドの暗号化キー | `payment_ca/eway/live_encryption_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| サンドボックス API キー | `payment_ca/eway/sandbox_api_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| Sandbox API パスワード | `payment_ca/eway/sandbox_api_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| サンドボックスのクライアントサイド暗号化キー | `payment_ca/eway/sandbox_encryption_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_hk/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_hk/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| ゲートウェイ URL | `payment_hk/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションの詳細 URL | `payment_hk/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_hk/cybersource/transaction_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| アクセスキー | `payment_hk/cybersource/access_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 秘密鍵 | `payment_hk/cybersource/secret_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_hk/cybersource/sandbox_flag` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 支払い応答パスワード | `payment_hk/worldpay/response_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| リモート管理承認パスワード | `payment_hk/worldpay/auth_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_hk/worldpay/sandbox_flag` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| Live API キー | `payment_hk/eway/live_api_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| Live API パスワード | `payment_hk/eway/live_api_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| ライブクライアントサイドの暗号化キー | `payment_hk/eway/live_encryption_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| サンドボックス API キー | `payment_hk/eway/sandbox_api_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| Sandbox API パスワード | `payment_hk/eway/sandbox_api_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| サンドボックスのクライアントサイド暗号化キー | `payment_hk/eway/sandbox_encryption_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_jp/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_jp/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| ゲートウェイ URL | `payment_jp/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションの詳細 URL | `payment_jp/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_jp/cybersource/transaction_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| アクセスキー | `payment_jp/cybersource/access_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 秘密鍵 | `payment_jp/cybersource/secret_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 新規注文ステータス | `payment_jp/cybersource/order_status` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| テストモード | `payment_jp/cybersource/sandbox_flag` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| 支払い応答パスワード | `payment_jp/worldpay/response_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| リモート管理承認パスワード | `payment_jp/worldpay/auth_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_jp/worldpay/sandbox_flag` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| サンドボックスモード | `payment_jp/eway/sandbox_flag` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| Live API キー | `payment_jp/eway/live_api_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| Live API パスワード | `payment_jp/eway/live_api_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| ライブクライアントサイドの暗号化キー | `payment_jp/eway/live_encryption_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| サンドボックス API キー | `payment_jp/eway/sandbox_api_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| Sandbox API パスワード | `payment_jp/eway/sandbox_api_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| サンドボックスのクライアントサイド暗号化キー | `payment_jp/eway/sandbox_encryption_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_fr/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_fr/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| ゲートウェイ URL | `payment_fr/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションの詳細 URL | `payment_fr/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_fr/cybersource/transaction_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| アクセスキー | `payment_fr/cybersource/access_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 秘密鍵 | `payment_fr/cybersource/secret_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_fr/cybersource/sandbox_flag` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| 支払い応答パスワード | `payment_fr/worldpay/response_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| リモート管理承認パスワード | `payment_fr/worldpay/auth_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_fr/worldpay/sandbox_flag` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |  | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| サンドボックスモード | `payment_fr/eway/sandbox_flag` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| Live API キー | `payment_fr/eway/live_api_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| Live API パスワード | `payment_fr/eway/live_api_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| ライブクライアントサイドの暗号化キー | `payment_fr/eway/live_encryption_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| サンドボックス API キー | `payment_fr/eway/sandbox_api_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| Sandbox API パスワード | `payment_fr/eway/sandbox_api_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| サンドボックスのクライアントサイド暗号化キー | `payment_fr/eway/sandbox_encryption_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_it/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_it/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| ゲートウェイ URL | `payment_it/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションの詳細 URL | `payment_it/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_it/cybersource/transaction_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| アクセスキー | `payment_it/cybersource/access_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 秘密鍵 | `payment_it/cybersource/secret_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_it/cybersource/sandbox_flag` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| 支払い応答パスワード | `payment_it/worldpay/response_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| リモート管理承認パスワード | `payment_it/worldpay/auth_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_it/worldpay/sandbox_flag` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| サンドボックスモード | `payment_it/eway/sandbox_flag` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | ![ システム固有 ](/help/assets/configuration/cloud-env.png) |
| Live API キー | `payment_it/eway/live_api_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| Live API パスワード | `payment_it/eway/live_api_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| ライブクライアントサイドの暗号化キー | `payment_it/eway/live_encryption_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| サンドボックス API キー | `payment_it/eway/sandbox_api_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| Sandbox API パスワード | `payment_it/eway/sandbox_api_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| サンドボックスのクライアントサイド暗号化キー | `payment_it/eway/sandbox_encryption_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| API キー | `fraud_protection/signifyd/api_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| API の URL | `fraud_protection/signifyd/api_url` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |  | ![ システム固有 ](/help/assets/configuration/cloud-env.png) | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| API ログイン ID | `payment_au/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| マーチャント MD5 | `payment_au/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 顧客に E メール通知 | `payment_au/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 販売者の電子メール | `payment_au/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| リモート管理者インストール ID | `payment_au/worldpay/admin_installation_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションの MD5 シークレット | `payment_au/worldpay/md5_secret` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 小切手の送信先 | `payment_es/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| API ログイン ID | `payment_es/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| マーチャント MD5 | `payment_es/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 顧客に E メール通知 | `payment_es/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 販売者の電子メール | `payment_es/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| マーチャント ID | `payment_es/cybersource/merchant_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| プロファイル ID | `payment_es/cybersource/profile_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| リモート管理者インストール ID | `payment_es/worldpay/admin_installation_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 |
| SFTP 資格情報 | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| API ログイン ID | `payment_nz/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| マーチャント MD5 | `payment_nz/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 顧客に E メール通知 | `payment_nz/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 販売者の電子メール | `payment_nz/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| マーチャント ID | `payment_nz/cybersource/merchant_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_nz/cybersource/transaction_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| プロファイル ID | `payment_nz/cybersource/profile_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| アクセスキー | `payment_nz/cybersource/access_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 秘密鍵 | `payment_nz/cybersource/secret_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| インストール ID | `payment_nz/worldpay/installation_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 支払い応答パスワード | `payment_nz/worldpay/response_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| リモート管理者インストール ID | `payment_nz/worldpay/admin_installation_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| リモート管理承認パスワード | `payment_nz/worldpay/auth_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションの MD5 シークレット | `payment_nz/worldpay/md5_secret` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| API ログイン ID | `payment_us/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_us/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| マーチャント MD5 | `payment_us/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 顧客に E メール通知 | `payment_us/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 販売者の電子メール | `payment_us/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| マーチャント ID | `payment_us/cybersource/merchant_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_us/cybersource/transaction_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| プロファイル ID | `payment_us/cybersource/profile_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| インストール ID | `payment_us/worldpay/installation_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 支払い応答パスワード | `payment_us/worldpay/response_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| リモート管理者インストール ID | `payment_us/worldpay/admin_installation_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| リモート管理承認パスワード | `payment_us/worldpay/auth_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションの MD5 シークレット | `payment_us/worldpay/md5_secret` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 小切手の送信先 | `payment_gb/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| マーチャント ID | `payment_gb/cybersource/merchant_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_gb/cybersource/transaction_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| プロファイル ID | `payment_gb/cybersource/profile_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| アクセスキー | `payment_gb/cybersource/access_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 秘密鍵 | `payment_gb/cybersource/secret_key` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| API ログイン ID | `payment_gb/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_gb/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| マーチャント MD5 | `payment_gb/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 顧客に E メール通知 | `payment_gb/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 販売者の電子メール | `payment_gb/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| インストール ID | `payment_gb/worldpay/installation_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 支払い応答パスワード | `payment_gb/worldpay/response_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| リモート管理者インストール ID | `payment_gb/worldpay/admin_installation_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| リモート管理承認パスワード | `payment_gb/worldpay/auth_password` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 小切手を支払先にする | `payment_de/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 小切手の送信先 | `payment_de/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| マーチャント ID | `payment_de/cybersource/merchant_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| プロファイル ID | `payment_de/cybersource/profile_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| API ログイン ID | `payment_de/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| マーチャント MD5 | `payment_de/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 顧客に E メール通知 | `payment_de/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 販売者の電子メール | `payment_de/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| インストール ID | `payment_de/worldpay/installation_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| リモート管理者インストール ID | `payment_de/worldpay/admin_installation_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションの MD5 シークレット | `payment_de/worldpay/md5_secret` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 小切手を支払先にする | `payment_other/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 小切手の送信先 | `payment_other/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| API ログイン ID | `payment_other/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| マーチャント MD5 | `payment_other/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 新規注文ステータス | `payment_other/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 販売者の電子メール | `payment_other/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| マーチャント ID | `payment_other/cybersource/merchant_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| プロファイル ID | `payment_other/cybersource/profile_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| インストール ID | `payment_other/worldpay/installation_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| リモート管理者インストール ID | `payment_other/worldpay/admin_installation_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションの MD5 シークレット | `payment_other/worldpay/md5_secret` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 小切手を支払先にする | `payment_ca/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 小切手の送信先 | `payment_ca/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| API ログイン ID | `payment_ca/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| マーチャント MD5 | `payment_ca/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 新規注文ステータス | `payment_ca/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 顧客に E メール通知 | `payment_ca/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 販売者の電子メール | `payment_ca/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| マーチャント ID | `payment_ca/cybersource/merchant_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| プロファイル ID | `payment_ca/cybersource/profile_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| インストール ID | `payment_ca/worldpay/installation_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| リモート管理者インストール ID | `payment_ca/worldpay/admin_installation_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションの MD5 シークレット | `payment_ca/worldpay/md5_secret` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 小切手を支払先にする | `payment_hk/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 小切手の送信先 | `payment_hk/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| API ログイン ID | `payment_hk/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| マーチャント MD5 | `payment_hk/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 顧客に E メール通知 | `payment_hk/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 販売者の電子メール | `payment_hk/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| マーチャント ID | `payment_hk/cybersource/merchant_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| プロファイル ID | `payment_hk/cybersource/profile_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| インストール ID | `payment_hk/worldpay/installation_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| リモート管理者インストール ID | `payment_hk/worldpay/admin_installation_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションの MD5 シークレット | `payment_hk/worldpay/md5_secret` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 署名フィールド | `payment_hk/worldpay/signature_fields` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 小切手を支払先にする | `payment_jp/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 小切手の送信先 | `payment_jp/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| API ログイン ID | `payment_jp/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| マーチャント MD5 | `payment_jp/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 顧客に E メール通知 | `payment_jp/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 販売者の電子メール | `payment_jp/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| マーチャント ID | `payment_jp/cybersource/merchant_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| プロファイル ID | `payment_jp/cybersource/profile_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| インストール ID | `payment_jp/worldpay/installation_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| リモート管理者インストール ID | `payment_jp/worldpay/admin_installation_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションの MD5 シークレット | `payment_jp/worldpay/md5_secret` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 署名フィールド | `payment_jp/worldpay/signature_fields` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 小切手を支払先にする | `payment_fr/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 小切手の送信先 | `payment_fr/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| API ログイン ID | `payment_fr/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| マーチャント MD5 | `payment_fr/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 顧客に E メール通知 | `payment_fr/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 販売者の電子メール | `payment_fr/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| マーチャント ID | `payment_fr/cybersource/merchant_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| プロファイル ID | `payment_fr/cybersource/profile_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| インストール ID | `payment_fr/worldpay/installation_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| リモート管理者インストール ID | `payment_fr/worldpay/admin_installation_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションの MD5 シークレット | `payment_fr/worldpay/md5_secret` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 署名フィールド | `payment_fr/worldpay/signature_fields` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 小切手を支払先にする | `payment_it/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 小切手の送信先 | `payment_it/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| API ログイン ID | `payment_it/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| マーチャント MD5 | `payment_it/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 顧客に E メール通知 | `payment_it/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 販売者の電子メール | `payment_it/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| マーチャント ID | `payment_it/cybersource/merchant_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| プロファイル ID | `payment_it/cybersource/profile_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| インストール ID | `payment_it/worldpay/installation_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| リモート管理者インストール ID | `payment_it/worldpay/admin_installation_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| トランザクションの MD5 シークレット | `payment_it/worldpay/md5_secret` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | | | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}
