---
title: 一般的な設定パスの参照
description: 一般的な設定値と詳細な設定値の一覧を参照してください。
feature: Configuration, Observability, Roles/Permissions, System
exl-id: 3c557746-5182-4929-aebf-5b6fe76f0d8f
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '965'
ht-degree: 0%

---

# 一般的および高度な設定パスのリファレンス

このトピックでは、一般的な設定パスと高度な設定パス、および _not_ [機密性の高いシステム固有の値](config-reference-sens.md). この [`magento app:config:dump` command](../cli/export-configuration.md) は、これらの値を共有設定ファイルに書き込みます。 `app/etc/config.php`（ソース管理下に置く必要があります）

オプションで設定を上書きしたり、機密設定を設定したりするには、 [環境変数を使用して設定を上書きする](override-config-settings.md#environment-variables).

## 一般カテゴリ

この節では、以下の管理で使用できる変数名と設定パスを示します。 **ストア** /設定/ **設定** > **一般**.

### 一般パス

これらの設定値は、 **ストア** /設定/ **設定** /一般/ **一般**.

| 名前 | 設定パス | コマースのみ？ | 敏感？ |
|--------------|--------------|--------------|--------------|
| デフォルトの国 | `general/country/default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![機密](/help/assets/configuration/cloud-sens.png) |
| 国を許可 | `general/country/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![機密](/help/assets/configuration/cloud-sens.png) |
| の郵便番号はオプションです。 | `general/country/optional_zip_countries` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![機密](/help/assets/configuration/cloud-sens.png) |
| 欧州連合 (EU) 諸国 | `general/country/eu_countries` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![機密](/help/assets/configuration/cloud-sens.png) |
| 上位の宛先 | `general/country/destinations` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| の状態は必須です | `general/region/state_required` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 国のオプションの場合に州を選択することを許可 | `general/region/display_all` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| タイムゾーン | `general/locale/timezone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| ロケール | `general/locale/code` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 重量単位 | `general/locale/weight_unit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 週の最初の曜日 | `general/locale/firstday` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 週末 | `general/locale/weekend` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| アクセス制限 | `general/restriction/is_active` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |  |
| 制限モード | `general/restriction/mode` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |  |
| 起動ページ | `general/restriction/http_redirect` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |  |
| ランディングページ | `general/restriction/cms_page` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |  |
| HTTP 応答 | `general/restriction/http_status` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |  |
| ストア名 | `general/store_information/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| ストアの電話番号 | `general/store_information/phone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 営業時間の保存 | `general/store_information/hours` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 国 | `general/store_information/country_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 地域/都道府県 | `general/store_information/region_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 郵便番号 | `general/store_information/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 市区町村 | `general/store_information/city` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 住所 | `general/store_information/street_line1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| 住所行 2 | `general/store_information/street_line2` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| VAT 番号 | `general/store_information/merchant_vat_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| シングルストアモードを有効にする | `general/single_store_mode/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |

{style="table-layout:auto"}

### Web パス

これらの設定値は、 **ストア** /設定/ **設定** > **一般** > **Web**.

| 名前 | 設定パス | コマースのみ？ |
|--------------|--------------|--------------|
| ストアコードを URL に追加 | `web/url/use_store` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ベース URL に自動リダイレクト | `web/url/redirect_to_base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Web サーバーの書き換えを使用 | `web/seo/use_rewrites` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Storefront でのセキュア URL の使用 | `web/secure/use_in_frontend` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 管理でのセキュア URL の使用 | `web/secure/use_in_adminhtml` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTTP Strict Transport Security(HSTS) の有効化 | `web/secure/enable_hsts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 安全でない要求のアップグレード | `web/secure/enable_upgrade_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| オフローダーヘッダー | `web/secure/offloader_header` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CMS ホームページ | `web/default/cms_home_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CMS ルートページなし | `web/default/cms_no_route` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CMS Cookie ページがない | `web/default/cms_no_cookies` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CMS ページのパンくずリストを表示 | `web/default/show_cms_breadcrumbs` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cookie の有効期間 | `web/cookie/cookie_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTTP のみを使用 | `web/cookie/cookie_httponly` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cookie 制限モード | `web/cookie/cookie_restriction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| REMOTE_ADDR の検証 | `web/session/use_remote_addr` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTTP_VIA を検証 | `web/session/use_http_via` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTTP_X_FORWARDED_FOR を検証します | `web/session/use_http_x_forwarded_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTTP_USER_AGENT の検証 | `web/session/use_http_user_agent` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Storefront で SID を使用 | `web/session/use_frontend_sid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cookie が無効な場合は CMS ページにリダイレクト | `web/browser_capabilities/cookies` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| JavaScript が無効な場合に通知を表示 | `web/browser_capabilities/javascript` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ローカルストレージが無効な場合に通知を表示 | `web/browser_capabilities/local_storage` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### 通貨設定パス

これらの設定値は、 **ストア** /設定/ **設定** > **一般** > **通貨の設定**.

| 名前 | 設定パス | コマースのみ？ |
|--------------|--------------|--------------|
| 基準通貨 | `currency/options/base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デフォルトの表示通貨 | `currency/options/default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 許可されている通貨 | `currency/options/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Yahoo Finance Exchange | `TBD` |  |
| Fixer.io | `TBD` |  |
| Webservicex | `TBD` |  |
| 接続タイムアウト（秒） | `currency/yahoofinance/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 接続タイムアウト（秒） | `currency/fixerio/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 接続タイムアウト（秒） | `currency/webservicex/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効 | `currency/import/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| サービス | `currency/import/service` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 開始時間 | `currency/import/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頻度 | `currency/import/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| エラーの電子メール受信者 | `currency/import/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| エラーメール送信者 | `currency/import/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| エラーメールテンプレート | `currency/import/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### 連絡先のパス

これらの設定値は、 **ストア** /設定/ **設定** > **一般** > **連絡先**.

| 名前 | 設定パス | コマースのみ？ |
|--------------|--------------|--------------|
| お問い合わせの有効化 | `contact/contact/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メール送信先 | `contact/email/recipient_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メール送信者 | `contact/email/sender_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メールテンプレート | `contact/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### レポートのパス

これらの設定値は、 **ストア** /設定/ **設定** > **一般** > **レポート**.

| 名前 | 設定パス | コマースのみ？ |
|--------------|--------------|--------------|
| 年度累計開始 | `reports/dashboard/ytd_start` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 今月の開始 | `reports/dashboard/mtd_start` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### コンテンツ管理パス

これらの設定値は、 **ストア** /設定/ **設定** > **一般** > **コンテンツ管理**.

| 名前 | 設定パス | コマースのみ？ |
|--------------|--------------|--------------|
| WYSIWYG Editor の有効化 | `cms/wysiwyg/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| WYSIWYG for Catalog でのメディアコンテンツに対する静的 URL の使用 | `cms/wysiwyg/use_static_urls_in_catalog` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 階層機能の有効化 | `cms/hierarchy/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 階層メタデータの有効化 | `cms/hierarchy/metadata_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 階層メニューのデフォルトのレイアウト | `cms/hierarchy/menu_layout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### New Relicレポートパス

これらの設定値は、 **ストア** /設定/ **設定** > **一般** > **New Relic Reporting**.

| 名前 | 設定パス | コマースのみ？ |
|--------------|--------------|--------------|
| New Relic統合の有効化 | `newrelicreporting/general/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Relic Application Name | `newrelicreporting/general/app_name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cron を有効にする | `newrelicreporting/cron/enable_cron` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 詳細カテゴリ

この節では、以下の管理で使用できる変数名と設定パスを示します。 **ストア** /設定/ **設定** > **詳細**.

### 管理パス

これらの設定値は、 **ストア** /設定/ **設定** > **詳細** > **管理者**.

| 名前 | 設定パス | コマースのみ？ |
|--------------|--------------|--------------|
| パスワードを忘れたメールテンプレート | `admin/emails/forgot_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メール送信者を忘れてリセット | `admin/emails/forgot_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ユーザー通知テンプレート | `admin/emails/user_notification_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 起動ページ | `admin/startup/menu_item_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| カスタム管理 URL を使用 | `admin/url/use_custom` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| カスタム管理パスを使用 | `admin/url/use_custom_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 管理者アカウントの共有 | `admin/security/admin_account_sharing` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パスワードリセット保護の種類 | `admin/security/password_reset_protection_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 回復リンクの有効期限（時間） | `admin/security/password_reset_link_expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パスワードリセット要求の最大数 | `admin/security/max_number_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パスワードリセット要求の最小間隔 | `admin/security/min_time_between_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| URL に秘密鍵を追加 | `admin/security/use_form_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ログインでは大文字と小文字が区別されます | `admin/security/use_case_sensitive_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 管理セッションの有効期間（秒） | `admin/security/session_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ロックアウトアカウントに対する最大ログイン失敗数 | `admin/security/lockout_failures` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ロックアウト時間（分） | `admin/security/lockout_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パスワードの有効期間（日数） | `admin/security/password_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パスワードの変更 | `admin/security/password_is_forced` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| グラフを有効にする | `admin/dashboard/enable_charts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 管理での CAPTCHA の有効化 | `admin/captcha/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| フォント | `admin/captcha/font` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Forms | `admin/captcha/forms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 表示モード | `admin/captcha/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ログイン失敗の回数 | `admin/captcha/failed_attempts_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CAPTCHA タイムアウト（分） | `admin/captcha/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| シンボル数 | `admin/captcha/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CAPTCHA で使用されるシンボル | `admin/captcha/symbols` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 大文字と小文字を区別 | `admin/captcha/case_sensitive` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効なアクション | `admin/magento_logging/actions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### システムパス

これらの設定値は、 **ストア** /設定/ **設定** > **詳細** > **システム**.

| 名前 | 設定パス | コマースのみ？ |
|--------------|--------------|--------------|
| 成功したメッセージの有効期間 | `system/mysqlmq/successful_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 次の後に処理中のメッセージを再試行 | `system/mysqlmq/retry_inprogress_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 失敗したメッセージの有効期間 | `system/mysqlmq/failed_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新しいメッセージの有効期間 | `system/mysqlmq/new_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 次の間隔でスケジュールを生成 | `system/cron/index/schedule_generate_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 事前スケジュール | `system/cron/index/schedule_ahead_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 内で実行されない場合にミス | `system/cron/index/schedule_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 履歴クリーンアップ間隔 | `system/cron/index/history_cleanup_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 成功履歴の有効期間 | `system/cron/index/history_success_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 失敗履歴の有効期間 | `system/cron/index/history_failure_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 別のプロセスを使用 | `system/cron/index/use_separate_process` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 次の間隔でスケジュールを生成 | `system/cron/default/schedule_generate_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 事前スケジュール | `system/cron/default/schedule_ahead_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 内で実行されない場合にミス | `system/cron/default/schedule_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 履歴クリーンアップ間隔 | `system/cron/default/history_cleanup_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 成功履歴の有効期間 | `system/cron/default/history_success_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 失敗履歴の有効期間 | `system/cron/default/history_failure_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 次の間隔でスケジュールを生成 | `system/cron/staging/schedule_generate_every` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 事前スケジュール | `system/cron/staging/schedule_ahead_for` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 内で実行されない場合にミス | `system/cron/staging/schedule_lifetime` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 履歴クリーンアップ間隔 | `system/cron/staging/history_cleanup_every` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 成功履歴の有効期間 | `system/cron/staging/history_success_lifetime` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 失敗履歴の有効期間 | `system/cron/staging/history_failure_lifetime` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 別のプロセスを使用 | `system/cron/staging/use_separate_process` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 次の間隔でスケジュールを生成 | `system/cron/catalog/event/schedule_generate_every` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 事前スケジュール | `system/cron/catalog/event/schedule_ahead_for` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 内で実行されない場合にミス | `system/cron/catalog/event/schedule_lifetime` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 履歴クリーンアップ間隔 | `system/cron/catalog/event/history_cleanup_every` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 成功履歴の有効期間 | `system/cron/catalog/event/history_success_lifetime` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 失敗履歴の有効期間 | `system/cron/catalog/event/history_failure_lifetime` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 別のプロセスを使用 | `system/cron/catalog/event/use_separate_process` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 別のプロセスを使用 | `system/cron/default/use_separate_process` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メール通信の無効化 | `system/smtp/disable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Return-Path を設定 | `system/smtp/set_return_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Return-Path Email | `system/smtp/return_path_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| インストール済みの通貨 | `system/currency/installed` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTTPS を使用してフィードを取得 | `system/adminnotification/use_https` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 更新頻度 | `system/adminnotification/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最終更新日 | `system/adminnotification/last_update` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールされたバックアップの有効化 | `system/backup/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| バックアップの種類 | `system/backup/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 開始時間 | `system/backup/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頻度 | `system/backup/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メンテナンスモード | `system/backup/maintenance` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ログエントリの有効期間、日数 | `system/rotation/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ログのアーカイブ頻度 | `system/rotation/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Caching Application | `system/full_page_cache/caching_application` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 公開コンテンツの TTL | `system/full_page_cache/ttl` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 猶予期間 | `system/full_page_cache/varnish/grace_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 設定を書き出し | `system/full_page_cache/varnish/export_button_version4` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ログに保存された日数 | `system/bulk/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メディアストレージ | `system/media_storage_configuration/media_storage` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メディアデータベースを選択 | `system/media_storage_configuration/media_database` （Commerce 2.4.3 で非推奨） | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 環境更新時間 | `system/media_storage_configuration/configuration_update_time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ファイルを保存、日 | `system/magento_scheduled_import_export_log/save_days` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールされたファイル履歴のクリーニングを有効にする | `system/magento_scheduled_import_export_log/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 開始時間 | `system/magento_scheduled_import_export_log/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頻度 | `system/magento_scheduled_import_export_log/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| エラーメールテンプレート | `system/magento_scheduled_import_export_log/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### 開発者パス

これらの設定値は、 **ストア** /設定/ **設定** > **詳細** > **開発者**.

| 名前 | 設定パス | コマースのみ？ |
|--------------|--------------|--------------|
| ワークフロータイプ | `dev/front_end_development_workflow/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Symlinks を許可 | `dev/template/allow_symlink` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Html を縮小 | `dev/template/minify_html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ストアフロントのテンプレートパスヒントを有効にする | `dev/debug/template_hints_storefront` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 管理者のテンプレートパスヒントを有効にする | `dev/debug/template_hints_admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ヒントにブロック名を追加する | `dev/debug/template_hints_blocks` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ファイルにログ | `dev/debug/debug_logging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| syslog にログ | `dev/syslog/syslog_logging` |  |
| Storefront が有効 | `dev/translate_inline/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 管理者に対して有効 | `dev/translate_inline/active_admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| JavaScript ファイルの結合 | `dev/js/merge_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| JavaScript のバンドルを有効にする | `dev/js/enable_js_bundling` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| JavaScript ファイルの縮小 | `dev/js/minify_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 翻訳戦略 | `dev/js/translate_strategy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| JS エラーをセッションストレージに記録 | `dev/js/session_storage_logging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CSS ファイルを結合 | `dev/css/merge_css_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CSS ファイルの縮小 | `dev/css/minify_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 画像アダプタ | `dev/image/default_adapter` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 静的ファイルに署名 | `dev/static/sign` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 非同期インデックス作成 | `dev/grid/async_indexing` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ユーザー定義属性をキャッシュ | `dev/caching/cache_user_defined_attributes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
