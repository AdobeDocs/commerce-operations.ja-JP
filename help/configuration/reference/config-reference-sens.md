---
title: 機密性の高いシステム固有のパス
description: システム固有の設定値と機密設定値の一覧を参照してください。
feature: Configuration, System
exl-id: 127880ab-7507-4e53-8b51-dfa6557d0b18
source-git-commit: 5a8e52d8eee1619697db40accb9775b92b4e8a9d
workflow-type: tm+mt
source-wordcount: '3702'
ht-degree: 0%

---

# 機密性の高いシステム固有の設定

このトピックでは、システム固有の設定と機密設定の構成パスを示します。

- The [`magento app:config:dump` command](../cli/export-configuration.md) は、システム固有の設定をシステム固有の設定ファイルに書き込みます。 `app/etc/env.php`です。 _not_ ソース管理下にある。 また、すべてのコマースインスタンスの共有設定をに書き込みます。 `app/etc/config.php`，このファイル _should_ ソース管理下にある。
- The [`magento config:sensitive:set` command](../cli/set-configuration-values.md) 機密設定を書き込みます。 `app/etc/env.php`.

  また、設定変数を使用して機密値を設定することもできます。詳しくは、 [環境変数を使用して設定を上書きする](../reference/override-config-settings.md#environment-variables).

その他の設定パスの一覧については、以下を参照してください。

- [支払を除くすべての構成パス](../reference/config-reference-general.md)
- [支払い設定パス](../reference/config-reference-payment.md).

>[!INFO]
>
>このトピックに記載されているすべての設定パスは機密性が高くなります。 The `System-specific?` 列には、どの値もシステム固有の値が表示されます。

## カテゴリに依存する一般的なパスとシステム固有のパス

この節では、以下の管理で使用できる変数名と設定パスを示します。 **ストア** /設定/ **設定** > **一般**.

### Web パスの機密性が高く、システム固有のパス

これらの設定値は、 **ストア** /設定/ **設定** > **一般** > **Web**.

| 名前 | 設定パス | コマースのみ？ | 暗号化？ | システム固有？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| ベース URL | `web/unsecure/base_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| ベースリンク URL | `web/unsecure/base_link_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| 静的ビューファイルのベース URL | `web/unsecure/base_static_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| ユーザーメディアファイルのベース URL | `web/unsecure/base_media_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| セキュアベース URL | `web/secure/base_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| セキュアベースリンク URL | `web/secure/base_link_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| 静的ビューファイルのセキュアベース URL | `web/secure/base_static_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| ユーザーメディアファイルのセキュアベース URL | `web/secure/base_media_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| デフォルトの Web URL | `web/default/front` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| デフォルトのルートなし URL | `web/default/no_route` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| Cookie のパス | `web/cookie/cookie_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| Cookie ドメイン | `web/cookie/cookie_domain` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| Cookie の有効期間 | `web/cookie/cookie_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| HTTP のみを使用 | `web/cookie/cookie_httponly` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| Cookie 制限モード | `web/cookie/cookie_restriction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

### 通貨の設定に関する機密性とシステム固有のパス

これらの設定値は、 **ストア** /設定/ **設定** > **一般** > **通貨の設定**.

| 名前 | 設定パス | コマースのみ？ | 暗号化？ | システム固有？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| エラーの電子メール受信者 | `currency/import/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### 電子メールアドレスを機密性の高いパスとシステム固有のパスに保存

これらの設定値は、 **ストア** /設定/ **電子メール設定** > **一般** > **電子メールアドレスを保存**.

| 名前 | 設定パス | コマースのみ？ | 暗号化？ | システム固有？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 送信者名 | `trans_email/ident_general/name` | | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 送信者の E メール | `trans_email/ident_general/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 送信者名 | `trans_email/ident_sales/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 送信者の E メール | `trans_email/ident_sales/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 送信者名 | `trans_email/ident_support/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 送信者の E メール | `trans_email/ident_support/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 送信者名 | `trans_email/ident_custom1/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 送信者の E メール | `trans_email/ident_custom1/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 送信者名 | `trans_email/ident_custom2/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 送信者の E メール | `trans_email/ident_custom2/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### 連絡先の機密性が高いパスとシステム固有のパス

これらの設定値は、 **ストア** /設定/ **設定** > **一般** > **連絡先**.

| 名前 | 設定パス | コマースのみ？ | 暗号化？ | システム固有？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| メール送信先 | `contact/email/recipient_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| メール送信者 | `contact/email/sender_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| メールテンプレート | `contact/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### New Relicでの機密性の高いシステム固有のパスのレポート作成

これらの設定値は、 **ストア** /設定/ **設定** > **一般** > **New Relic Reporting**.

| 名前 | 設定パス | コマースのみ？ | 暗号化？ | システム固有？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| New Relicアカウント ID | `newrelicreporting/general/account_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| New Relic Application ID | `newrelicreporting/general/app_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| New Relic API キー | `newrelicreporting/general/api` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| インサイト API キー | `newrelicreporting/general/insights_insert_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| New Relic API URL | `newrelicreporting/general/api_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| インサイト API URL | `newrelicreporting/general/insights_api_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## お客様は、カテゴリーに依存するパスとシステム固有のパスを使用

この節では、以下の管理で使用できる変数名と設定パスを示します。 **ストア** /設定/ **設定** > **顧客**.

### お客様の構成に応じたパスとシステム固有のパス

これらの設定値は、 **ストア** /設定/ **設定** > **顧客** > **顧客設定**.

| 名前 | 設定パス | コマースのみ？ | 暗号化？ | システム固有？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| デフォルトの電子メールドメイン | `customer/create_account/email_domain` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

## カタログカテゴリ

この節では、以下の管理で使用できる変数名と設定パスを示します。 **ストア** /設定/ **設定** > **カタログ**.

### カタログに依存するパスとシステムに固有のパス

これらの設定値は、 **ストア** /設定/ **設定** > **カタログ** > **カタログ**.

| 名前 | 設定パス | コマースのみ？ | 暗号化？ | システム固有？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| エラーの電子メール受信者 | `catalog/productalert_cron/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| YouTube API キー | `catalog/product_video/youtube_api_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| Solr サーバーのホスト名 | `catalog/search/solr_server_hostname` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| Solr サーバーポート | `catalog/search/solr_server_port` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| Solr サーバーユーザー名 | `catalog/search/solr_server_username` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| Solr サーバーのパスワード | `catalog/search/solr_server_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| Solr サーバーパス | `catalog/search/solr_server_path` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| Elasticsearchサーバーのホスト名 | `catalog/search/elasticsearch_server_hostname` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| Elasticsearchサーバーポート | `catalog/search/elasticsearch_server_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| Elasticsearchインデックスのプレフィックス | `catalog/search/elasticsearch_index_prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| ElasticsearchHTTP 認証を有効にする | `catalog/search/elasticsearch_enable_auth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| ElasticsearchHTTP ユーザ名 | `catalog/search/elasticsearch_username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| ElasticsearchHTTP パスワード | `catalog/search/elasticsearch_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| Elasticsearchサーバーのタイムアウト | `catalog/search/elasticsearch_server_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| ElasticsearchHTTP ユーザ名 | `catalog/search/elasticsearch_username` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | (`{{ site.baseurl }}`/common/images/cloud_env.png) |
| ElasticsearchHTTP パスワード | `catalog/search/elasticsearch_password` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | (`{{ site.baseurl }}`/common/images/cloud_env.png) |
| Elasticsearchサーバーのタイムアウト | `catalog/search/elasticsearch_server_timeout` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | (`{{ site.baseurl }}`/common/images/cloud_env.png) |
| OpenSearch Server ホスト名 | `catalog/search/opensearch_server_hostname` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | (`{{ site.baseurl }}`/common/images/cloud_env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| OpenSearch サーバーポート | `catalog/search/opensearch_server_port` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | (`{{ site.baseurl }}`/common/images/cloud_env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| OpenSearch インデックスのプレフィックス | `catalog/search/opensearch_index_prefix` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | (`{{ site.baseurl }}`/common/images/cloud_env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| OpenSearch HTTP Auth の有効化 | `catalog/search/opensearch_enable_auth` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | (`{{ site.baseurl }}`/common/images/cloud_env.png) |
| OpenSearch HTTP ユーザー名 | `catalog/search/opensearch_username` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | (`{{ site.baseurl }}`/common/images/cloud_env.png) |
| OpenSearch HTTP パスワード | `catalog/search/opensearch_password` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | (`{{ site.baseurl }}`/common/images/cloud_env.png) |
| OpenSearch Server タイムアウト | `catalog/search/opensearch_server_timeout` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | (`{{ site.baseurl }}`/common/images/cloud_env.png) |

{style="table-layout:auto"}

>[!NOTE]
>
>OpenSearch 設定は、Adobe Commerce 2.4.6 で導入されました。

### インベントリに依存するパスとシステム固有のパス

これらの設定値は、 **ストア** /設定/ **設定** > **カタログ** > **在庫**.

| 名前 | 設定パス | コマースのみ？ | 暗号化？ | システム固有？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Google API キー | `cataloginventory/source_selection_distance_based_google/api_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### XML サイトマップの機密パスとシステム固有のパス

これらの設定値は、 **ストア** /設定/ **設定** > **カタログ** > **XML サイトマップ**.

| 名前 | 設定パス | コマースのみ？ | 暗号化？ | システム固有？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| エラーの電子メール受信者 | `sitemap/generate/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## 販売カテゴリ

この節では、以下の管理で使用できる変数名と設定パスを示します。 **ストア** /設定/ **設定** > **セールス**.

### 出荷時の設定は、システム固有のパスに依存します。

これらの設定値は、 **ストア** /設定/ **設定** > **セールス** > **発送設定**.

| 名前 | 設定パス | コマースのみ？ | 暗号化？ | システム固有？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 国 | `shipping/origin/country_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 地域/州（米国） | `shipping/origin/region_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 郵便番号 | `shipping/origin/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 市区町村 | `shipping/origin/city` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 住所 | `shipping/origin/street_line1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 住所行 2 | `shipping/origin/street_line2` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| ライブアカウント | `carriers/ups/is_account_live` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

### セールスメールの機密性が高く、システム固有のパス

これらの設定値は、 **ストア** /設定/ **設定** > **セールス** > **セールスメール**.

| 名前 | 設定パス | コマースのみ？ | 暗号化？ | システム固有？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 注文メールコピーの送信先 | `sales_email/order/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 注文コメントのメールコピーの送信先 | `sales_email/order_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 請求書メールコピーの送付先 | `sales_email/invoice/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 請求書コメントのメールコピーの送信先 | `sales_email/invoice_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 出荷メールのコピーを次の宛先に送信 | `sales_email/shipment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 発送コメントのメールコピーの送付先 | `sales_email/shipment_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| クレジット・メモの電子メール・コピーの送付先 | `sales_email/creditmemo/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| クレジット・メモ注釈の電子メール・コピーの送付先 | `sales_email/creditmemo_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| ピックアップ準備完了のメールコピーの送信先 | `sales_email/temando_pickup/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### チェックアウトの機密性が高いパスとシステム固有のパス

これらの設定値は、 **ストア** /設定/ **設定** > **セールス** > **チェックアウト**.

| 名前 | 設定パス | コマースのみ？ | 暗号化？ | システム固有？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 支払い失敗メールコピーの送信先 | `checkout/payment_failed/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Google API の機密パスとシステム固有のパス

これらの設定値は、 **ストア** /設定/ **設定** > **セールス** > **Google API**.

| 名前 | 設定パス | コマースのみ？ | 暗号化？ | システム固有？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| コンテナ ID | `google/analytics/container_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### 配信方法に応じたパスとシステム固有のパス

これらの設定値は、 **ストア** /設定/ **設定** > **セールス** > **配信方法**.

| 名前 | 設定パス | コマースのみ？ | 暗号化？ | システム固有？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| ゲートウェイ URL | `carriers/usps/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| セキュアゲートウェイ URL | `carriers/usps/gateway_secure_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| タイトル | `carriers/usps/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ユーザー ID | `carriers/usps/userid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| パスワード | `carriers/usps/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| ユーザー ID | `carriers/ups/username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| パスワード | `carriers/ups/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| ライセンス番号にアクセス | `carriers/ups/access_license_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| トラッキング XML URL | `carriers/ups/tracking_xml_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| ゲートウェイ XML URL | `carriers/ups/gateway_xml_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 発送者番号 | `carriers/ups/shipper_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| デバッグ | `carriers/ups/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| アカウント ID | `carriers/fedex/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| キー | `carriers/fedex/key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| メートル番号 | `carriers/fedex/meter_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| パスワード | `carriers/fedex/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| アクセス ID | `carriers/dhl/id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| パスワード | `carriers/dhl/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| デバッグ | `carriers/dhl/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| アカウント番号 | `carriers/dhl/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| ゲートウェイ URL | `carriers/dhl/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックスモード | `carriers/fedex/sandbox_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### セールスに関する機密性の高いパスとシステム固有のパス

これらの設定値は、 **ストア** /設定/ **設定** > **セールス** > **セールス**.

| 名前 | 設定パス | コマースのみ？ | 暗号化？ | システム固有？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 連絡先名 | `sales/magento_rma/store_name` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 住所 | `sales/magento_rma/address` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 住所 | `sales/magento_rma/address1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 市区町村 | `sales/magento_rma/city` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 都道府県 | `sales/magento_rma/region_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 郵便番号 | `sales/magento_rma/zip` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 国 | `sales/magento_rma/country_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| RMA E メールコピーの送付先 | `sales_email/magento_rma/copy_to` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| RMA 承認 E メールコピーの送付先 | `sales_email/magento_rma_auth/copy_to` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| RMA コメントの電子メールコピーの送付先 | `sales_email/magento_rma_comment/copy_to` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| RMA コメントの電子メールコピーの送付先 | `sales_email/magento_rma_customer_comment/copy_to` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Google API パス

これらの設定値は、 **ストア** /設定/ **設定** > **セールス** > **Google API**.

| 名前 | 設定パス | コマースのみ？ | 暗号化？ | システム固有？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| アカウント番号 | `google/analytics/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## 詳細カテゴリ

この節では、以下の管理で使用できる変数名と設定パスを示します。 **ストア** /設定/ **設定** > **詳細**.

### 管理者に依存するパスとシステムに固有のパス

これらの設定値は、 **ストア** /設定/ **設定** > **詳細** > **管理者**.

| 名前 | 設定パス | コマースのみ？ | 暗号化？ | システム固有？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| カスタム管理 URL | `admin/url/custom` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| カスタム管理パス | `admin/url/custom_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### システムに依存するパスとシステムに固有のパス

これらの設定値は、 **ストア** /設定/ **設定** > **詳細** > **システム**.

| 名前 | 設定パス | コマースのみ？ | 暗号化？ | システム固有？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| エラーの電子メール受信者 | `system/magento_scheduled_import_export_log/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| アクセスリスト | `system/full_page_cache/varnish/access_list` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | | ![機密](/help/assets/configuration/cloud-sens.png) |
| エラーメール送信者 | `system/magento_scheduled_import_export_log/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | | ![機密](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### 開発者に依存するパスとシステムに固有のパス

これらの設定値は、 **ストア** /設定/ **設定** > **詳細** > **開発者**.

| 名前 | 設定パス | コマースのみ？ | 暗号化？ | システム固有？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 許可される IP（コンマ区切り） | `dev/restrict/allow_ips` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## 詳細カテゴリ

この節では、以下の管理で使用できる変数名と設定パスを示します。 **ストア** /設定/ **設定** > **詳細**.

### システムパス

これらの設定値は、 **ストア** /設定/ **設定** > **詳細** > **システム**.

| 名前 | 設定パス | コマースのみ？ | 暗号化？ | システム固有？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| ホスト | `system/smtp/host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| ポート (25) | `system/smtp/port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| バックエンドホスト | `system/full_page_cache/varnish/backend_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| バックエンドポート | `system/full_page_cache/varnish/backend_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### 開発者パス

これらの設定値は、 **ストア** /設定/ **設定** > **詳細** > **開発者**.

| 名前 | 設定パス | コマースのみ？ | 暗号化？ | システム固有？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| JS エラーをセッションストレージキーに記録 | `dev/js/session_storage_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

## 支払いに関する機密性の高いパスとシステム固有のパス

この節では、以下の管理で使用できる変数名と設定パスを示します。 **ストア** /設定/ **設定** > **セールス** > **支払い**.

### 一般変数

| 名前 | 設定パス | コマースのみ？ | 暗号化？ |
|--------------|--------------|--------------|--------------|
| 商家の国 | `paypal/general/merchant_country` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

>[!INFO]
>
>この変数の選択によって、どの変数を選択するかが決まります。 [国際パス](#international-paths) を使用できます。

### PayPal の機密パスとシステム固有のパス

| 名前 | 設定パス | コマースのみ？ | 暗号化？ | システム固有？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| PayPal マーチャントアカウントに関連付けられたメール（オプション） | `paypal/general/business_account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| マーチャントアカウント ID | `payment/paypal_express/merchant_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| Publisher ID | `payment/paypal_express_bml/publisher_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| パスワード | `paypal/fetch_reports/ftp_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| ログイン | `paypal/fetch_reports/ftp_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| カスタムエンドポイントのホスト名または IP アドレス | `paypal/fetch_reports/ftp_ip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックスモード | `paypal/fetch_reports/ftp_sandbox` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| デバッグモード | `payment/paypal_express/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| デバッグモード | `payment/paypal_billing_agreement/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| SFTP 資格情報 | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### PayPal Payflow Pro 機密性の高いシステム固有のパス

| 名前 | 設定パス | コマースのみ？ | 暗号化？ | システム固有？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| ユーザー | `payment/payflow_advanced/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| パスワード | `payment/payflow_advanced/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| カスタムパス | `paypal/fetch_reports/ftp_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| ユーザー | `payment/payflowpro/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| パスワード | `payment/payflowpro/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment/payflowpro/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| パートナー | `payment/payflowpro/partner` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| プロキシホスト | `payment/payflowpro/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| プロキシポート | `payment/payflowpro/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| デバッグモード | `payment/payflowpro/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| SFTP 資格情報 | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| クレジットカード設定 | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### PayPal Payflow Link 機密性の高いパスとシステム固有のパス

| 名前 | 設定パス | コマースのみ？ | 暗号化？ | システム固有？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| ユーザー | `payment/payflow_link/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| パスワード | `payment/payflow_link/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment/payflow_link/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| プロキシを使用 | `payment/payflow_link/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| プロキシホスト | `payment/payflow_link/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| プロキシポート | `payment/payflow_link/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![システム固有](/help/assets/configuration/cloud-env.png) |
| デバッグモード | `payment/payflow_link/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| URL をキャンセルして URL を返すための URL メソッド | `payment/payflow_link/url_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| デバッグモード | `payment/payflow_express/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| SFTP 資格情報 | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### PayPal Payments Pro 機密性の高いシステム固有のパス

| 名前 | 設定パス | コマースのみ？ | 暗号化？ | システム固有？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| API ユーザー名 | `paypal/wpp/api_username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| API パスワード | `paypal/wpp/api_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| API 署名 | `paypal/wpp/api_signature` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| API 証明書 | `paypal/wpp/api_cert` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| プロキシホスト | `paypal/wpp/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| プロキシポート | `paypal/wpp/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックスモード | `paypal/wpp/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| SFTP 資格情報 | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### PayPal Payments Pro ホスト型およびシステム固有のパス

| 名前 | 設定パス | コマースのみ？ | 暗号化？ | システム固有？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| デバッグモード | `payment/hosted_pro/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| SFTP 資格情報 | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Braintreeに依存するパスとシステムに固有のパス

| 名前 | 設定パス | コマースのみ？ | 暗号化？ | システム固有？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| マーチャント ID | `payment/braintree/merchant_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 公開鍵 | `payment/braintree/public_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 秘密鍵 | `payment/braintree/private_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| マーチャントアカウント ID | `payment/braintree/merchant_account_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| Kount Merchant ID | `payment/braintree/kount_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| マーチャント名の上書き | `payment/braintree_paypal/merchant_name_override` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 電話 | `payment/braintree/descriptor_phone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| URL | `payment/braintree/descriptor_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

### 小切手/通貨注文のパス

| 名前 | 設定パス | コマースのみ？ | 暗号化？ | システム固有？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| 小切手の送信先 | `payment/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 小切手の送信先 | `payment_us/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### 国際パス

| 名前 | 設定パス | コマースのみ？ | 暗号化？ | システム固有？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|--------------|
| トランザクションキー | `payment_au/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_au/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| ゲートウェイ URL | `payment_au/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクションの詳細 URL | `payment_au/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_au/cybersource/transaction_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| アクセスキー | `payment_au/cybersource/access_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| 秘密鍵 | `payment_au/cybersource/secret_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_au/cybersource/sandbox_flag` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| 支払い応答のパスワード | `payment_au/worldpay/response_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| リモート管理者認証パスワード | `payment_au/worldpay/auth_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックスモード | `payment_au/eway/sandbox_flag` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| ライブ API キー | `payment_au/eway/live_api_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| Live API のパスワード | `payment_au/eway/live_api_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| ライブクライアント側暗号化キー | `payment_au/eway/live_encryption_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックス API キー | `payment_au/eway/sandbox_api_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックス API パスワード | `payment_au/eway/sandbox_api_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックスクライアント側暗号化キー | `payment_au/eway/sandbox_encryption_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_es/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_es/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| ゲートウェイ URL | `payment_es/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクションの詳細 URL | `payment_es/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_es/cybersource/transaction_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| アクセスキー | `payment_es/cybersource/access_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| 秘密鍵 | `payment_es/cybersource/secret_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_es/cybersource/sandbox_flag` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| 支払い応答のパスワード | `payment_es/worldpay/response_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| リモート管理者認証パスワード | `payment_es/worldpay/auth_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクション用の MD5 シークレット | `payment_es/worldpay/md5_secret` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| デバッグ | `payment_es/worldpay/debug` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| サンドボックスモード | `payment_es/eway/sandbox_flag` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| ライブ API キー | `payment_es/eway/live_api_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| Live API のパスワード | `payment_es/eway/live_api_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| ライブクライアント側暗号化キー | `payment_es/eway/live_encryption_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックス API キー | `payment_es/eway/sandbox_api_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックス API パスワード | `payment_es/eway/sandbox_api_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックスクライアント側暗号化キー | `payment_es/eway/sandbox_encryption_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_nz/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_nz/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| ゲートウェイ URL | `payment_nz/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクションの詳細 URL | `payment_nz/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_nz/cybersource/sandbox_flag` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| テストモード | `payment_nz/worldpay/sandbox_flag` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| サンドボックスモード | `payment_nz/eway/sandbox_flag` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| ライブ API キー | `payment_nz/eway/live_api_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| Live API のパスワード | `payment_nz/eway/live_api_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| ライブクライアント側暗号化キー | `payment_nz/eway/live_encryption_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックス API キー | `payment_nz/eway/sandbox_api_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックス API パスワード | `payment_nz/eway/sandbox_api_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックスクライアント側暗号化キー | `payment_nz/eway/sandbox_encryption_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment/payflow_advanced/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| プロキシホスト | `payment/payflow_advanced/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| プロキシポート | `payment/payflow_advanced/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| デバッグモード | `payment/payflow_advanced/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| URL をキャンセルして URL を返すための URL メソッド | `payment/payflow_advanced/url_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| テストモード | `payment_us/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| ゲートウェイ URL | `payment_us/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクションの詳細 URL | `payment_us/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| アクセスキー | `payment_us/cybersource/access_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| 秘密鍵 | `payment_us/cybersource/secret_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_us/cybersource/sandbox_flag` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| テストモード | `payment_us/worldpay/sandbox_flag` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| サンドボックスモード | `payment_us/eway/sandbox_flag` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| ライブ API キー | `payment_us/eway/live_api_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| Live API のパスワード | `payment_us/eway/live_api_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| ライブクライアント側暗号化キー | `payment_us/eway/live_encryption_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックス API キー | `payment_us/eway/sandbox_api_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックス API パスワード | `payment_us/eway/sandbox_api_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックスクライアント側暗号化キー | `payment_us/eway/sandbox_encryption_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) |
| テストモード | `payment_gb/cybersource/sandbox_flag` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| テストモード | `payment_gb/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| ゲートウェイ URL | `payment_gb/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクションの詳細 URL | `payment_gb/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_gb/worldpay/sandbox_flag` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| サンドボックスモード | `payment_gb/eway/sandbox_flag` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| ライブ API キー | `payment_gb/eway/live_api_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| Live API のパスワード | `payment_gb/eway/live_api_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| ライブクライアント側暗号化キー | `payment_gb/eway/live_encryption_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックス API キー | `payment_gb/eway/sandbox_api_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックス API パスワード | `payment_gb/eway/sandbox_api_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックスクライアント側暗号化キー | `payment_gb/eway/sandbox_encryption_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_de/cybersource/transaction_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| アクセスキー | `payment_de/cybersource/access_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| 秘密鍵 | `payment_de/cybersource/secret_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_de/cybersource/sandbox_flag` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| トランザクションキー | `payment_de/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_de/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| ゲートウェイ URL | `payment_de/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクションの詳細 URL | `payment_de/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| 支払い応答のパスワード | `payment_de/worldpay/response_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| リモート管理者認証パスワード | `payment_de/worldpay/auth_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| デバッグ | `payment_de/worldpay/debug` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| サンドボックスモード | `payment_de/eway/sandbox_flag` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| ライブ API キー | `payment_de/eway/live_api_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| Live API のパスワード | `payment_de/eway/live_api_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| ライブクライアント側暗号化キー | `payment_de/eway/live_encryption_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックス API キー | `payment_de/eway/sandbox_api_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックス API パスワード | `payment_de/eway/sandbox_api_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックスクライアント側暗号化キー | `payment_de/eway/sandbox_encryption_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_other/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_other/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| ゲートウェイ URL | `payment_other/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクションの詳細 URL | `payment_other/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| トランザクションキー | `payment_other/cybersource/transaction_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| アクセスキー | `payment_other/cybersource/access_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| 秘密鍵 | `payment_other/cybersource/secret_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| 新しい注文ステータス | `payment_other/cybersource/order_status` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| テストモード | `payment_other/cybersource/sandbox_flag` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| 支払い応答のパスワード | `payment_other/worldpay/response_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| リモート管理者認証パスワード | `payment_other/worldpay/auth_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_other/worldpay/sandbox_flag` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| サンドボックスモード | `payment_other/eway/sandbox_flag` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| ライブ API キー | `payment_other/eway/live_api_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| Live API のパスワード | `payment_other/eway/live_api_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| ライブクライアント側暗号化キー | `payment_other/eway/live_encryption_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックス API キー | `payment_other/eway/sandbox_api_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックス API パスワード | `payment_other/eway/sandbox_api_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックスクライアント側暗号化キー | `payment_other/eway/sandbox_encryption_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_ca/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_ca/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| ゲートウェイ URL | `payment_ca/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクションの詳細 URL | `payment_ca/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_ca/cybersource/transaction_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| アクセスキー | `payment_ca/cybersource/access_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| 秘密鍵 | `payment_ca/cybersource/secret_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| 新しい注文ステータス | `payment_ca/cybersource/order_status` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| テストモード | `payment_ca/cybersource/sandbox_flag` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| 支払い応答のパスワード | `payment_ca/worldpay/response_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| リモート管理者認証パスワード | `payment_ca/worldpay/auth_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_ca/worldpay/sandbox_flag` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| サンドボックスモード | `payment_ca/eway/sandbox_flag` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| ライブ API キー | `payment_ca/eway/live_api_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| Live API のパスワード | `payment_ca/eway/live_api_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| ライブクライアント側暗号化キー | `payment_ca/eway/live_encryption_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックス API キー | `payment_ca/eway/sandbox_api_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックス API パスワード | `payment_ca/eway/sandbox_api_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックスクライアント側暗号化キー | `payment_ca/eway/sandbox_encryption_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_hk/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_hk/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| ゲートウェイ URL | `payment_hk/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクションの詳細 URL | `payment_hk/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_hk/cybersource/transaction_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| アクセスキー | `payment_hk/cybersource/access_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| 秘密鍵 | `payment_hk/cybersource/secret_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_hk/cybersource/sandbox_flag` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| 支払い応答のパスワード | `payment_hk/worldpay/response_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| リモート管理者認証パスワード | `payment_hk/worldpay/auth_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_hk/worldpay/sandbox_flag` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| ライブ API キー | `payment_hk/eway/live_api_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| Live API のパスワード | `payment_hk/eway/live_api_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| ライブクライアント側暗号化キー | `payment_hk/eway/live_encryption_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックス API キー | `payment_hk/eway/sandbox_api_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックス API パスワード | `payment_hk/eway/sandbox_api_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックスクライアント側暗号化キー | `payment_hk/eway/sandbox_encryption_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_jp/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_jp/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| ゲートウェイ URL | `payment_jp/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクションの詳細 URL | `payment_jp/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_jp/cybersource/transaction_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| アクセスキー | `payment_jp/cybersource/access_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| 秘密鍵 | `payment_jp/cybersource/secret_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| 新しい注文ステータス | `payment_jp/cybersource/order_status` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| テストモード | `payment_jp/cybersource/sandbox_flag` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| 支払い応答のパスワード | `payment_jp/worldpay/response_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| リモート管理者認証パスワード | `payment_jp/worldpay/auth_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_jp/worldpay/sandbox_flag` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| サンドボックスモード | `payment_jp/eway/sandbox_flag` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| ライブ API キー | `payment_jp/eway/live_api_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| Live API のパスワード | `payment_jp/eway/live_api_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| ライブクライアント側暗号化キー | `payment_jp/eway/live_encryption_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックス API キー | `payment_jp/eway/sandbox_api_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックス API パスワード | `payment_jp/eway/sandbox_api_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックスクライアント側暗号化キー | `payment_jp/eway/sandbox_encryption_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_fr/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_fr/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| ゲートウェイ URL | `payment_fr/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクションの詳細 URL | `payment_fr/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_fr/cybersource/transaction_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| アクセスキー | `payment_fr/cybersource/access_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| 秘密鍵 | `payment_fr/cybersource/secret_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_fr/cybersource/sandbox_flag` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| 支払い応答のパスワード | `payment_fr/worldpay/response_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| リモート管理者認証パスワード | `payment_fr/worldpay/auth_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_fr/worldpay/sandbox_flag` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |  | ![システム固有](/help/assets/configuration/cloud-env.png) |
| サンドボックスモード | `payment_fr/eway/sandbox_flag` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| ライブ API キー | `payment_fr/eway/live_api_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| Live API のパスワード | `payment_fr/eway/live_api_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| ライブクライアント側暗号化キー | `payment_fr/eway/live_encryption_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックス API キー | `payment_fr/eway/sandbox_api_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックス API パスワード | `payment_fr/eway/sandbox_api_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックスクライアント側暗号化キー | `payment_fr/eway/sandbox_encryption_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_it/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_it/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| ゲートウェイ URL | `payment_it/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクションの詳細 URL | `payment_it/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_it/cybersource/transaction_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| アクセスキー | `payment_it/cybersource/access_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| 秘密鍵 | `payment_it/cybersource/secret_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_it/cybersource/sandbox_flag` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| 支払い応答のパスワード | `payment_it/worldpay/response_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| リモート管理者認証パスワード | `payment_it/worldpay/auth_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| テストモード | `payment_it/worldpay/sandbox_flag` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| サンドボックスモード | `payment_it/eway/sandbox_flag` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | ![システム固有](/help/assets/configuration/cloud-env.png) |
| ライブ API キー | `payment_it/eway/live_api_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| Live API のパスワード | `payment_it/eway/live_api_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| ライブクライアント側暗号化キー | `payment_it/eway/live_encryption_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックス API キー | `payment_it/eway/sandbox_api_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックス API パスワード | `payment_it/eway/sandbox_api_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| サンドボックスクライアント側暗号化キー | `payment_it/eway/sandbox_encryption_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| API キー | `fraud_protection/signifyd/api_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| API URL | `fraud_protection/signifyd/api_url` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |  | ![システム固有](/help/assets/configuration/cloud-env.png) | ![機密](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| API ログイン ID | `payment_au/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_au/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 電子メール顧客 | `payment_au/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 商人のメール | `payment_au/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| リモート管理者のインストール ID | `payment_au/worldpay/admin_installation_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクション用の MD5 シークレット | `payment_au/worldpay/md5_secret` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 小切手の送信先 | `payment_es/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| API ログイン ID | `payment_es/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_es/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 電子メール顧客 | `payment_es/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 商人のメール | `payment_es/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| マーチャント ID | `payment_es/cybersource/merchant_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| プロファイル ID | `payment_es/cybersource/profile_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| リモート管理者のインストール ID | `payment_es/worldpay/admin_installation_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 |
| SFTP 資格情報 | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| API ログイン ID | `payment_nz/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_nz/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 電子メール顧客 | `payment_nz/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 商人のメール | `payment_nz/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| マーチャント ID | `payment_nz/cybersource/merchant_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_nz/cybersource/transaction_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| プロファイル ID | `payment_nz/cybersource/profile_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| アクセスキー | `payment_nz/cybersource/access_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 秘密鍵 | `payment_nz/cybersource/secret_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| インストール ID | `payment_nz/worldpay/installation_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 支払い応答のパスワード | `payment_nz/worldpay/response_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| リモート管理者のインストール ID | `payment_nz/worldpay/admin_installation_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| リモート管理者認証パスワード | `payment_nz/worldpay/auth_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクション用の MD5 シークレット | `payment_nz/worldpay/md5_secret` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| API ログイン ID | `payment_us/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_us/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_us/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 電子メール顧客 | `payment_us/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 商人のメール | `payment_us/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| マーチャント ID | `payment_us/cybersource/merchant_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_us/cybersource/transaction_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| プロファイル ID | `payment_us/cybersource/profile_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| インストール ID | `payment_us/worldpay/installation_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 支払い応答のパスワード | `payment_us/worldpay/response_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| リモート管理者のインストール ID | `payment_us/worldpay/admin_installation_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| リモート管理者認証パスワード | `payment_us/worldpay/auth_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクション用の MD5 シークレット | `payment_us/worldpay/md5_secret` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | | ![機密](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 小切手の送信先 | `payment_gb/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| マーチャント ID | `payment_gb/cybersource/merchant_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_gb/cybersource/transaction_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| プロファイル ID | `payment_gb/cybersource/profile_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| アクセスキー | `payment_gb/cybersource/access_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 秘密鍵 | `payment_gb/cybersource/secret_key` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| API ログイン ID | `payment_gb/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクションキー | `payment_gb/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_gb/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 電子メール顧客 | `payment_gb/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 商人のメール | `payment_gb/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | | ![機密](/help/assets/configuration/cloud-sens.png) |
| インストール ID | `payment_gb/worldpay/installation_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 支払い応答のパスワード | `payment_gb/worldpay/response_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| リモート管理者のインストール ID | `payment_gb/worldpay/admin_installation_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| リモート管理者認証パスワード | `payment_gb/worldpay/auth_password` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 小切手の支払先にする | `payment_de/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 小切手の送信先 | `payment_de/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| マーチャント ID | `payment_de/cybersource/merchant_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| プロファイル ID | `payment_de/cybersource/profile_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| API ログイン ID | `payment_de/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_de/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 電子メール顧客 | `payment_de/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 商人のメール | `payment_de/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| インストール ID | `payment_de/worldpay/installation_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| リモート管理者のインストール ID | `payment_de/worldpay/admin_installation_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクション用の MD5 シークレット | `payment_de/worldpay/md5_secret` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | | ![機密](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 小切手の支払先にする | `payment_other/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 小切手の送信先 | `payment_other/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| API ログイン ID | `payment_other/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_other/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 新しい注文ステータス | `payment_other/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 商人のメール | `payment_other/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| マーチャント ID | `payment_other/cybersource/merchant_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| プロファイル ID | `payment_other/cybersource/profile_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| インストール ID | `payment_other/worldpay/installation_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| リモート管理者のインストール ID | `payment_other/worldpay/admin_installation_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクション用の MD5 シークレット | `payment_other/worldpay/md5_secret` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 小切手の支払先にする | `payment_ca/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 小切手の送信先 | `payment_ca/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| API ログイン ID | `payment_ca/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_ca/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 新しい注文ステータス | `payment_ca/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 電子メール顧客 | `payment_ca/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 商人のメール | `payment_ca/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| マーチャント ID | `payment_ca/cybersource/merchant_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| プロファイル ID | `payment_ca/cybersource/profile_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| インストール ID | `payment_ca/worldpay/installation_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| リモート管理者のインストール ID | `payment_ca/worldpay/admin_installation_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクション用の MD5 シークレット | `payment_ca/worldpay/md5_secret` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | | ![機密](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 小切手の支払先にする | `payment_hk/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 小切手の送信先 | `payment_hk/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| API ログイン ID | `payment_hk/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_hk/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 電子メール顧客 | `payment_hk/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 商人のメール | `payment_hk/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| マーチャント ID | `payment_hk/cybersource/merchant_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| プロファイル ID | `payment_hk/cybersource/profile_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| インストール ID | `payment_hk/worldpay/installation_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| リモート管理者のインストール ID | `payment_hk/worldpay/admin_installation_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクション用の MD5 シークレット | `payment_hk/worldpay/md5_secret` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 署名フィールド | `payment_hk/worldpay/signature_fields` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 小切手の支払先にする | `payment_jp/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 小切手の送信先 | `payment_jp/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| API ログイン ID | `payment_jp/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_jp/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 電子メール顧客 | `payment_jp/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 商人のメール | `payment_jp/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| マーチャント ID | `payment_jp/cybersource/merchant_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| プロファイル ID | `payment_jp/cybersource/profile_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| インストール ID | `payment_jp/worldpay/installation_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| リモート管理者のインストール ID | `payment_jp/worldpay/admin_installation_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクション用の MD5 シークレット | `payment_jp/worldpay/md5_secret` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 署名フィールド | `payment_jp/worldpay/signature_fields` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 小切手の支払先にする | `payment_fr/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 小切手の送信先 | `payment_fr/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| API ログイン ID | `payment_fr/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_fr/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 電子メール顧客 | `payment_fr/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 商人のメール | `payment_fr/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| マーチャント ID | `payment_fr/cybersource/merchant_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| プロファイル ID | `payment_fr/cybersource/profile_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| インストール ID | `payment_fr/worldpay/installation_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| リモート管理者のインストール ID | `payment_fr/worldpay/admin_installation_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクション用の MD5 シークレット | `payment_fr/worldpay/md5_secret` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 署名フィールド | `payment_fr/worldpay/signature_fields` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| SFTP 資格情報 | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 小切手の支払先にする | `payment_it/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 小切手の送信先 | `payment_it/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| API ログイン ID | `payment_it/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_it/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 電子メール顧客 | `payment_it/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 商人のメール | `payment_it/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| マーチャント ID | `payment_it/cybersource/merchant_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| プロファイル ID | `payment_it/cybersource/profile_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | ![暗号化済み](/help/assets/configuration/cloud-enc.png) | | ![機密](/help/assets/configuration/cloud-sens.png) |
| インストール ID | `payment_it/worldpay/installation_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| リモート管理者のインストール ID | `payment_it/worldpay/admin_installation_id` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| トランザクション用の MD5 シークレット | `payment_it/worldpay/md5_secret` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) | | | ![機密](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}
