---
title: 一般設定パスのリファレンス
description: Adobe Commerceの一般設定パスと高度な設定パスおよび値について説明します。 システム、セキュリティ、管理構成のオプションを確認します。
feature: Configuration, Observability, Roles/Permissions, System
exl-id: 3c557746-5182-4929-aebf-5b6fe76f0d8f
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '971'
ht-degree: 0%

---

# 一般設定パスおよび詳細設定パスのリファレンス

このトピックでは、一般的な設定パスと高度な設定パスおよび _非機密_ システム固有の値 [ を一覧表示 ](config-reference-sens.md) ます。 [`magento app:config:dump` コマンドは ](../cli/export-configuration.md) これらの値をソース管理にある共有構成ファイル `app/etc/config.php` に書き込みます。

任意の構成設定を上書きしたり、重要な設定を指定したりするには、[ 環境変数を使用して構成設定を上書き ](override-config-settings.md#environment-variables) を参照してください。

## 一般カテゴリ

この節では、**ストア**/設定/**設定**/**一般** の管理でオプションに使用できる変数名と設定パスを示します。

### 一般パス

これらの設定値は、管理者の **ストア**/設定/**設定**/一般/**一般** で利用できます。

| 名前 | 設定パス | Commerceのみ？ | 機密？ |
|--------------|--------------|--------------|--------------|
| デフォルトの国 | `general/country/default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 国を許可 | `general/country/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 郵便番号はオプションです | `general/country/optional_zip_countries` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| EU 諸国 | `general/country/eu_countries` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ 機密 ](/help/assets/configuration/cloud-sens.png) |
| 上位の宛先 | `general/country/destinations` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 状態が必要な対象： | `general/region/state_required` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 国のオプションである場合に州を選択できるようにする | `general/region/display_all` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| タイムゾーン | `general/locale/timezone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Locale | `general/locale/code` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| 重み単位 | `general/locale/weight_unit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| 週の最初の曜日 | `general/locale/firstday` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| 週末日数 | `general/locale/weekend` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| アクセス制限 | `general/restriction/is_active` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | |
| 制限モード | `general/restriction/mode` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | |
| スタートアップページ | `general/restriction/http_redirect` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | |
| ランディングページ | `general/restriction/cms_page` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | |
| HTTP 応答 | `general/restriction/http_status` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | |
| ストア名 | `general/store_information/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| 店舗電話番号 | `general/store_information/phone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| 営業時間の保存 | `general/store_information/hours` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| 国 | `general/store_information/country_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| 地域/都道府県 | `general/store_information/region_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| 郵便番号 | `general/store_information/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| 市区町村 | `general/store_information/city` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| 番地 | `general/store_information/street_line1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| 住所 2 | `general/store_information/street_line2` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| VAT 番号 | `general/store_information/merchant_vat_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| シングルストアモードを有効にする | `general/single_store_mode/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |

{style="table-layout:auto"}

### Web パス

これらの設定値は、管理者の **ストア**/設定/**設定**/**一般**/**Web** で利用できます。

| 名前 | 設定パス | Commerceのみ？ |
|--------------|--------------|--------------|
| Url にストアコードを追加 | `web/url/use_store` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ベース URL への自動リダイレクト | `web/url/redirect_to_base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Web サーバーの書き換えの使用 | `web/seo/use_rewrites` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ストアフロントでセキュアな URL を使用 | `web/secure/use_in_frontend` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 管理者でセキュア URL を使用 | `web/secure/use_in_adminhtml` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTTP Strict Transport Security （HSTS）を有効にする | `web/secure/enable_hsts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 安全でない要求のアップグレード | `web/secure/enable_upgrade_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| オフローダーヘッダー | `web/secure/offloader_header` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CMS ホームページ | `web/default/cms_home_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 「CMSルートなし」ページ | `web/default/cms_no_route` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CMSの Cookie 禁止ページ | `web/default/cms_no_cookies` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CMSページのパンくずリストを表示 | `web/default/show_cms_breadcrumbs` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cookie の有効期間 | `web/cookie/cookie_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTTP のみを使用 | `web/cookie/cookie_httponly` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cookie 制限モード | `web/cookie/cookie_restriction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| REMOTE_ADDR を検証する | `web/session/use_remote_addr` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTTP_VIA を検証 | `web/session/use_http_via` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTTP_X_FORWARDED_FOR を検証 | `web/session/use_http_x_forwarded_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Http_USER_AGENT を検証する | `web/session/use_http_user_agent` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ストアフロントで SID を使用 | `web/session/use_frontend_sid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cookie が無効の場合はCMSページにリダイレクト | `web/browser_capabilities/cookies` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| JavaScriptが無効の場合に通知を表示 | `web/browser_capabilities/javascript` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ローカルストレージが無効の場合に通知を表示 | `web/browser_capabilities/local_storage` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### 通貨設定パス

これらの設定値は、管理者の **ストア**/設定/**設定**/**一般**/**通貨設定** で使用できます。

| 名前 | 設定パス | Commerceのみ？ |
|--------------|--------------|--------------|
| 基準通貨 | `currency/options/base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 既定の表示通貨 | `currency/options/default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 許可される通貨 | `currency/options/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Yahoo Finance Exchange | `TBD` | |
| Fixer.io | `TBD` | |
| Webservicex | `TBD` | |
| 接続タイムアウト （秒） | `currency/yahoofinance/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 接続タイムアウト （秒） | `currency/fixerio/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 接続タイムアウト （秒） | `currency/webservicex/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `currency/import/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| サービス | `currency/import/service` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 開始時刻 | `currency/import/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頻度 | `currency/import/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| エラーの E メール受信者 | `currency/import/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| エラーのメール送信者 | `currency/import/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| エラーメールテンプレート | `currency/import/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### 連絡先のパス

これらの設定値は、管理者の **ストア**/設定/**設定**/**一般**/**連絡先** で利用できます。

| 名前 | 設定パス | Commerceのみ？ |
|--------------|--------------|--------------|
| Enable Contact Us | `contact/contact/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Send Emails To | `contact/email/recipient_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E メール送信者 | `contact/email/sender_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E メール テンプレート | `contact/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### レポートパス

これらの設定値は、管理者の **ストア**/設定/**設定**/**一般**/**レポート** で利用できます。

| 名前 | 設定パス | Commerceのみ？ |
|--------------|--------------|--------------|
| 年初から年初まで | `reports/dashboard/ytd_start` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 今月の開始日 | `reports/dashboard/mtd_start` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### コンテンツ管理のパス

これらの設定値は、管理者の **ストア**/設定/**設定**/**一般**/**コンテンツ管理** で利用できます。

| 名前 | 設定パス | Commerceのみ？ |
|--------------|--------------|--------------|
| WYSIWYG Editor の有効化 | `cms/wysiwyg/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| カタログ用のWYSIWYGにおけるメディアコンテンツの静的 URL の使用 | `cms/wysiwyg/use_static_urls_in_catalog` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 階層機能を有効にする | `cms/hierarchy/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 階層メタデータの有効化 | `cms/hierarchy/metadata_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 階層メニューの既定のレイアウト | `cms/hierarchy/menu_layout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### New Relic レポートのパス

これらの設定値は、管理者の **ストア**/設定/**設定**/**一般**/6}New Relic レポート **で利用できます。**

| 名前 | 設定パス | Commerceのみ？ |
|--------------|--------------|--------------|
| New Relic統合の有効化 | `newrelicreporting/general/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Relic アプリケーション名 | `newrelicreporting/general/app_name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cron の有効化 | `newrelicreporting/cron/enable_cron` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 詳細カテゴリ

この節では、**ストア**/設定/**設定**/**詳細** の管理でオプションに使用できる変数名と設定パスを示します。

### 管理パス

これらの設定値は、管理者の **ストア**/設定/**設定**/**詳細**/**管理** で利用できます。

| 名前 | 設定パス | Commerceのみ？ |
|--------------|--------------|--------------|
| パスワードを忘れた場合の E メール テンプレート | `admin/emails/forgot_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メールの送信者を忘れた場合とリセット | `admin/emails/forgot_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ユーザー通知テンプレート | `admin/emails/user_notification_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スタートアップページ | `admin/startup/menu_item_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| カスタム管理 URL を使用 | `admin/url/use_custom` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| カスタム管理パスを使用 | `admin/url/use_custom_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 管理者アカウント共有 | `admin/security/admin_account_sharing` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パスワードリセット保護タイプ | `admin/security/password_reset_protection_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 復旧リンクの有効期限（時間） | `admin/security/password_reset_link_expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パスワードリセット要求の最大数 | `admin/security/max_number_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パスワードリセット要求の最小間隔 | `admin/security/min_time_between_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| URL への秘密鍵の追加 | `admin/security/use_form_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ログインでは大文字と小文字が区別される | `admin/security/use_case_sensitive_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 管理セッションの有効期間（秒） | `admin/security/session_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ロックアウト アカウントへのログイン エラーの最大数 | `admin/security/lockout_failures` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ロックアウト時間（分） | `admin/security/lockout_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パスワードの有効期間（日数） | `admin/security/password_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パスワードの変更 | `admin/security/password_is_forced` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| グラフを有効にする | `admin/dashboard/enable_charts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 管理者で CAPTCHA を有効にする | `admin/captcha/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| フォント | `admin/captcha/font` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Forms | `admin/captcha/forms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 表示モード | `admin/captcha/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 失敗したログイン試行回数 | `admin/captcha/failed_attempts_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CAPTCHA タイムアウト （分） | `admin/captcha/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| シンボルの数 | `admin/captcha/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CAPTCHA で使用されるシンボル | `admin/captcha/symbols` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 大文字と小文字を区別 | `admin/captcha/case_sensitive` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効なアクション | `admin/magento_logging/actions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### システムパス

これらの設定値は、管理者の **ストア**/設定/**設定**/**詳細**/**システム** で利用できます。

| 名前 | 設定パス | Commerceのみ？ |
|--------------|--------------|--------------|
| 成功したメッセージの有効期間 | `system/mysqlmq/successful_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 次の時間経過後に処理中のメッセージを再試行 | `system/mysqlmq/retry_inprogress_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 失敗したメッセージの有効期間 | `system/mysqlmq/failed_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新しいメッセージの有効期間 | `system/mysqlmq/new_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールの生成間隔 | `system/cron/index/schedule_generate_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 事前スケジュール | `system/cron/index/schedule_ahead_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 次の時間内に実行されない場合は失敗 | `system/cron/index/schedule_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 履歴クリーンアップ間隔 | `system/cron/index/history_cleanup_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 成功履歴の有効期間 | `system/cron/index/history_success_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 失敗履歴の有効期間 | `system/cron/index/history_failure_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 別のプロセスを使用 | `system/cron/index/use_separate_process` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールの生成間隔 | `system/cron/default/schedule_generate_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 事前スケジュール | `system/cron/default/schedule_ahead_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 次の時間内に実行されない場合は失敗 | `system/cron/default/schedule_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 履歴クリーンアップ間隔 | `system/cron/default/history_cleanup_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 成功履歴の有効期間 | `system/cron/default/history_success_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 失敗履歴の有効期間 | `system/cron/default/history_failure_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールの生成間隔 | `system/cron/staging/schedule_generate_every` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 事前スケジュール | `system/cron/staging/schedule_ahead_for` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 次の時間内に実行されない場合は失敗 | `system/cron/staging/schedule_lifetime` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 履歴クリーンアップ間隔 | `system/cron/staging/history_cleanup_every` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 成功履歴の有効期間 | `system/cron/staging/history_success_lifetime` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 失敗履歴の有効期間 | `system/cron/staging/history_failure_lifetime` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 別のプロセスを使用 | `system/cron/staging/use_separate_process` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| スケジュールの生成間隔 | `system/cron/catalog/event/schedule_generate_every` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 事前スケジュール | `system/cron/catalog/event/schedule_ahead_for` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 次の時間内に実行されない場合は失敗 | `system/cron/catalog/event/schedule_lifetime` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 履歴クリーンアップ間隔 | `system/cron/catalog/event/history_cleanup_every` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 成功履歴の有効期間 | `system/cron/catalog/event/history_success_lifetime` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 失敗履歴の有効期間 | `system/cron/catalog/event/history_failure_lifetime` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 別のプロセスを使用 | `system/cron/catalog/event/use_separate_process` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 別のプロセスを使用 | `system/cron/default/use_separate_process` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メール通信を無効にする | `system/smtp/disable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Return-Path を設定 | `system/smtp/set_return_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 再来訪パスのメール | `system/smtp/return_path_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| インストールされている通貨 | `system/currency/installed` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTTPS を使用したフィードの取得 | `system/adminnotification/use_https` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 更新頻度 | `system/adminnotification/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最終更新日 | `system/adminnotification/last_update` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュール バックアップを有効にする | `system/backup/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| バックアップ タイプ | `system/backup/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 開始時刻 | `system/backup/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頻度 | `system/backup/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メンテナンスモード | `system/backup/maintenance` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ログ エントリの有効期間、日数 | `system/rotation/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ログのアーカイブ頻度 | `system/rotation/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| キャッシュアプリケーション | `system/full_page_cache/caching_application` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パブリックコンテンツの TTL | `system/full_page_cache/ttl` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 猶予期間 | `system/full_page_cache/varnish/grace_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 設定を書き出し | `system/full_page_cache/varnish/export_button_version4` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ログに保存日数 | `system/bulk/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メディアストレージ | `system/media_storage_configuration/media_storage` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メディア データベースの選択 | `system/media_storage_configuration/media_database` （Commerce 2.4.3 で非推奨） | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 環境の更新時間 | `system/media_storage_configuration/configuration_update_time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ファイルの保存、日数 | `system/magento_scheduled_import_export_log/save_days` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールされたファイル履歴のクリーニングを有効にする | `system/magento_scheduled_import_export_log/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 開始時刻 | `system/magento_scheduled_import_export_log/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頻度 | `system/magento_scheduled_import_export_log/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| エラーメールテンプレート | `system/magento_scheduled_import_export_log/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### 開発者パス

これらの設定値は、管理者の **ストア**/設定/**設定**/**詳細**/**開発者** で利用できます。

| 名前 | 設定パス | Commerceのみ？ |
|--------------|--------------|--------------|
| ワークフロータイプ | `dev/front_end_development_workflow/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| シンボリックリンクを許可 | `dev/template/allow_symlink` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Html の縮小 | `dev/template/minify_html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ストアフロントのテンプレートパスヒントを有効にする | `dev/debug/template_hints_storefront` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 管理者用のテンプレートパスヒントを有効にする | `dev/debug/template_hints_admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ブロック名をヒントに追加する | `dev/debug/template_hints_blocks` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ファイルに記録 | `dev/debug/debug_logging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| syslog に記録 | `dev/syslog/syslog_logging` |  |
| ストアフロントに対して有効 | `dev/translate_inline/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 管理者に対して有効 | `dev/translate_inline/active_admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| JavaScript ファイルの結合 | `dev/js/merge_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| JavaScriptのバンドルの有効化 | `dev/js/enable_js_bundling` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| JavaScript ファイルの縮小 | `dev/js/minify_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 翻訳戦略 | `dev/js/translate_strategy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| セッションストレージに JS エラーを記録 | `dev/js/session_storage_logging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CSS ファイルの結合 | `dev/css/merge_css_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CSS ファイルの縮小 | `dev/css/minify_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 画像アダプター | `dev/image/default_adapter` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 静的ファイルへの署名 | `dev/static/sign` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 非同期インデックス作成 | `dev/grid/async_indexing` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ユーザー定義属性をキャッシュする | `dev/caching/cache_user_defined_attributes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
