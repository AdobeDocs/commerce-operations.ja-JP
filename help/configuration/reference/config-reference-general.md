---
title: 一般設定パスのリファレンス
description: Adobe Commerceの一般的および高度な設定パスと値について説明します。 システム、セキュリティ、管理設定オプションの詳細。
feature: Configuration, Observability, Roles/Permissions, System
exl-id: 3c557746-5182-4929-aebf-5b6fe76f0d8f
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '971'
ht-degree: 0%

---

# 一般および詳細設定パスのリファレンス

このトピックでは、一般的な設定パスと高度な設定パスおよび&#x200B;_not_ [機密値とシステム固有の値](config-reference-sens.md)をリストします。 [`magento app:config:dump` コマンド &#x200B;](../cli/export-configuration.md)は、これらの値をソース コントロールにある共有設定ファイル `app/etc/config.php`に書き込みます。

任意の構成設定を上書きする方法や、機密設定を設定する方法については、[環境変数を使用して構成設定を上書きする](override-config-settings.md#environment-variables)を参照してください。

## 一般カテゴリ

このセクションでは、管理者の&#x200B;**ストア**/設定/**構成**/**一般**&#x200B;のオプションで使用できる変数名と構成パスを示します。

### 一般パス

これらの設定値は、**ストア**/設定/**構成**/一般/**一般**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerceだけ？ | 繊細な？ |
|--------------|--------------|--------------|--------------|
| デフォルトの国 | `general/country/default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![機密性](/help/assets/configuration/cloud-sens.png) |
| 国を許可 | `general/country/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![機密性](/help/assets/configuration/cloud-sens.png) |
| 郵便番号はオプションです | `general/country/optional_zip_countries` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![機密性](/help/assets/configuration/cloud-sens.png) |
| 欧州連合諸国 | `general/country/eu_countries` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![機密性](/help/assets/configuration/cloud-sens.png) |
| 上位の配信先 | `general/country/destinations` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| の状態は必須です | `general/region/state_required` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| 「国」オプションの場合、「州」を選択できます | `general/region/display_all` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| タイムゾーン | `general/locale/timezone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| ロケール | `general/locale/code` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| 重み単位 | `general/locale/weight_unit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| 週の初日 | `general/locale/firstday` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| 週末の日数 | `general/locale/weekend` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| アクセス制限 | `general/restriction/is_active` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) | |
| 制限モード | `general/restriction/mode` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) | |
| スタートアップページ | `general/restriction/http_redirect` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) | |
| ランディングページ | `general/restriction/cms_page` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) | |
| HTTP レスポンス | `general/restriction/http_status` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) | |
| ストア名 | `general/store_information/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| 電話番号を保存 | `general/store_information/phone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| 営業時間の保存 | `general/store_information/hours` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| 国 | `general/store_information/country_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| 地域/州 | `general/store_information/region_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| 郵便番号 | `general/store_information/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| 市区町村 | `general/store_information/city` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| 住所 | `general/store_information/street_line1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| 住所2行目 | `general/store_information/street_line2` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| VAT番号 | `general/store_information/merchant_vat_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| シングルストアモードを有効にする | `general/single_store_mode/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |

{style="table-layout:auto"}

### web パス

これらの設定値は、**Stores**/設定/**Configuration**/**General**/**Web**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerceだけ？ |
|--------------|--------------|--------------|
| Urlにストアコードを追加 | `web/url/use_store` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ベース URLに自動リダイレクト | `web/url/redirect_to_base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Web サーバーの書き換えを使用 | `web/seo/use_rewrites` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ストアフロントで安全なURLを使用する | `web/secure/use_in_frontend` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 管理画面でセキュア URLを使用する | `web/secure/use_in_adminhtml` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTTP Strict Transport Security （HSTS）の有効化 | `web/secure/enable_hsts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 安全でない要求をアップグレード | `web/secure/enable_upgrade_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| オフローダーヘッダー | `web/secure/offloader_header` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CMS ホームページ | `web/default/cms_home_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CMSのルートページ | `web/default/cms_no_route` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CMSのCookieに関するページ | `web/default/cms_no_cookies` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CMS ページのパンくずリストを表示 | `web/default/show_cms_breadcrumbs` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cookieの有効期間 | `web/cookie/cookie_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTTPのみを使用 | `web/cookie/cookie_httponly` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cookie制限モード | `web/cookie/cookie_restriction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| REMOTE_ADDRの検証 | `web/session/use_remote_addr` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTTP_VIAの検証 | `web/session/use_http_via` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTTP_X_FORWARDED_FORの検証 | `web/session/use_http_x_forwarded_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTTP_USER_AGENTの検証 | `web/session/use_http_user_agent` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ストアフロントでSIDを使用する | `web/session/use_frontend_sid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cookieが無効になっている場合は、CMS ページにリダイレクトします | `web/browser_capabilities/cookies` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| JavaScriptが無効の場合の通知を表示 | `web/browser_capabilities/javascript` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ローカルストレージが無効になっている場合の通知を表示 | `web/browser_capabilities/local_storage` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### 通貨設定パス

これらの設定値は、**ストア**/設定/**設定**/**一般**/**通貨セットアップ**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerceだけ？ |
|--------------|--------------|--------------|
| 基本通貨 | `currency/options/base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 既定の表示通貨 | `currency/options/default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 許可されている通貨 | `currency/options/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Yahoo Finance Exchange | `TBD` | |
| Fixer.io | `TBD` | |
| Webservicex | `TBD` | |
| 接続タイムアウト （秒） | `currency/yahoofinance/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 接続タイムアウト （秒） | `currency/fixerio/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 接続タイムアウト （秒） | `currency/webservicex/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効 | `currency/import/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| サービス | `currency/import/service` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 開始時間 | `currency/import/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頻度 | `currency/import/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メール受信者のエラー | `currency/import/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メール送信者のエラー | `currency/import/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メールテンプレートのエラー | `currency/import/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### 連絡先のパス

これらの設定値は、**ストア**/設定/**設定**/**一般**/**連絡先**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerceだけ？ |
|--------------|--------------|--------------|
| お問い合わせを有効にする | `contact/contact/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メール送信先 | `contact/email/recipient_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メール送信者 | `contact/email/sender_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メールテンプレート | `contact/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### レポートパス

これらの設定値は、**ストア**/設定/**設定**/**一般**/**レポート**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerceだけ？ |
|--------------|--------------|--------------|
| 年初 | `reports/dashboard/ytd_start` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 今月の開始 | `reports/dashboard/mtd_start` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### コンテンツ管理のパス

これらの設定値は、**Stores**/設定/**Configuration**/**General**/**Content Management**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerceだけ？ |
|--------------|--------------|--------------|
| WYSIWYG エディターを有効にする | `cms/wysiwyg/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| カタログ用WYSIWYGでのメディアコンテンツの静的URLの使用 | `cms/wysiwyg/use_static_urls_in_catalog` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 階層機能の有効化 | `cms/hierarchy/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 階層メタデータを有効にする | `cms/hierarchy/metadata_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 階層メニューのデフォルトレイアウト | `cms/hierarchy/menu_layout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### New Relicのレポートパス

これらの設定値は、**Stores**/Settings > **Configuration** > **General** > **New Relic Reporting**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerceだけ？ |
|--------------|--------------|--------------|
| New Relic統合の有効化 | `newrelicreporting/general/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Relic アプリケーション名 | `newrelicreporting/general/app_name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cronを有効にする | `newrelicreporting/cron/enable_cron` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 高度なカテゴリ

このセクションでは、管理者の&#x200B;**ストア**/設定/**構成**/**詳細**&#x200B;のオプションで使用できる変数名と構成パスを示します。

### 管理者パス

これらの設定値は、**Stores** / 設定/**Configuration** / **Advanced** / **Admin**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerceだけ？ |
|--------------|--------------|--------------|
| パスワードのメールテンプレートを忘れた | `admin/emails/forgot_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メール送信者を忘れた場合とリセットした場合 | `admin/emails/forgot_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ユーザー通知テンプレート | `admin/emails/user_notification_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スタートアップページ | `admin/startup/menu_item_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| カスタム管理者URLの使用 | `admin/url/use_custom` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| カスタム管理パスの使用 | `admin/url/use_custom_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 管理者アカウント共有 | `admin/security/admin_account_sharing` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パスワードリセット保護タイプ | `admin/security/password_reset_protection_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 回復リンクの有効期限（時間） | `admin/security/password_reset_link_expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パスワードリセット要求の最大数 | `admin/security/max_number_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パスワードのリセット要求の間の最小時間 | `admin/security/min_time_between_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 秘密鍵をURLに追加 | `admin/security/use_form_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ログインでは大文字と小文字が区別されます | `admin/security/use_case_sensitive_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 管理者セッションの有効期間（秒） | `admin/security/session_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ロックアウトアカウントへの最大ログイン失敗 | `admin/security/lockout_failures` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ロックアウト時間（分） | `admin/security/lockout_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パスワードの有効期間（日数） | `admin/security/password_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パスワードの変更 | `admin/security/password_is_forced` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| グラフを有効にする | `admin/dashboard/enable_charts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 管理画面でCAPTCHAを有効にする | `admin/captcha/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| フォント | `admin/captcha/font` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Forms | `admin/captcha/forms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 表示モード | `admin/captcha/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ログインに失敗した試行回数 | `admin/captcha/failed_attempts_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CAPTCHA タイムアウト（分） | `admin/captcha/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| シンボル数 | `admin/captcha/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CAPTCHAで使用される記号 | `admin/captcha/symbols` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 大文字と小文字を区別 | `admin/captcha/case_sensitive` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効なアクション | `admin/magento_logging/actions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### システムパス

これらの設定値は、**Stores**/設定/**Configuration**/**Advanced**/**System**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerceだけ？ |
|--------------|--------------|--------------|
| 成功したメッセージの有効期間 | `system/mysqlmq/successful_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 処理中のメッセージを後で再試行 | `system/mysqlmq/retry_inprogress_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 失敗したメッセージの有効期間 | `system/mysqlmq/failed_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新しいメッセージの有効期間 | `system/mysqlmq/new_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュール毎回生成 | `system/cron/index/schedule_generate_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 今後のスケジュール | `system/cron/index/schedule_ahead_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 次の内で実行されない場合は欠落しています | `system/cron/index/schedule_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 履歴のクリーンアップ間隔 | `system/cron/index/history_cleanup_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 成功履歴の有効期間 | `system/cron/index/history_success_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| エラー履歴の有効期間 | `system/cron/index/history_failure_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 個別のプロセスを使用 | `system/cron/index/use_separate_process` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュール毎回生成 | `system/cron/default/schedule_generate_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 今後のスケジュール | `system/cron/default/schedule_ahead_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 次の内で実行されない場合は欠落しています | `system/cron/default/schedule_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 履歴のクリーンアップ間隔 | `system/cron/default/history_cleanup_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 成功履歴の有効期間 | `system/cron/default/history_success_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| エラー履歴の有効期間 | `system/cron/default/history_failure_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュール毎回生成 | `system/cron/staging/schedule_generate_every` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 今後のスケジュール | `system/cron/staging/schedule_ahead_for` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 次の内で実行されない場合は欠落しています | `system/cron/staging/schedule_lifetime` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 履歴のクリーンアップ間隔 | `system/cron/staging/history_cleanup_every` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 成功履歴の有効期間 | `system/cron/staging/history_success_lifetime` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| エラー履歴の有効期間 | `system/cron/staging/history_failure_lifetime` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 個別のプロセスを使用 | `system/cron/staging/use_separate_process` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| スケジュール毎回生成 | `system/cron/catalog/event/schedule_generate_every` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 今後のスケジュール | `system/cron/catalog/event/schedule_ahead_for` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 次の内で実行されない場合は欠落しています | `system/cron/catalog/event/schedule_lifetime` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 履歴のクリーンアップ間隔 | `system/cron/catalog/event/history_cleanup_every` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 成功履歴の有効期間 | `system/cron/catalog/event/history_success_lifetime` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| エラー履歴の有効期間 | `system/cron/catalog/event/history_failure_lifetime` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 個別のプロセスを使用 | `system/cron/catalog/event/use_separate_process` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 個別のプロセスを使用 | `system/cron/default/use_separate_process` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 電子メール通信を無効にする | `system/smtp/disable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Return-Pathを設定 | `system/smtp/set_return_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Return-Path Email | `system/smtp/return_path_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| インストール済み通貨 | `system/currency/installed` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTTPSを使用してフィードを取得 | `system/adminnotification/use_https` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 更新頻度 | `system/adminnotification/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最終更新日 | `system/adminnotification/last_update` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールされたバックアップを有効にする | `system/backup/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| バックアップタイプ | `system/backup/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 開始時間 | `system/backup/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頻度 | `system/backup/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メンテナンスモード | `system/backup/maintenance` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ログ記録の有効期間、日数 | `system/rotation/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ログ アーカイブ頻度 | `system/rotation/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| アプリケーションをキャッシュ | `system/full_page_cache/caching_application` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 公開コンテンツのTTL | `system/full_page_cache/ttl` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 猶予期間 | `system/full_page_cache/varnish/grace_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 設定の書き出し | `system/full_page_cache/varnish/export_button_version4` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ログに保存された日数 | `system/bulk/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メディアストレージ | `system/media_storage_configuration/media_storage` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メディア データベースを選択 | `system/media_storage_configuration/media_database` （Commerce 2.4.3では非推奨） | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 環境の更新時間 | `system/media_storage_configuration/configuration_update_time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ファイル、日数を保存 | `system/magento_scheduled_import_export_log/save_days` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールされたファイル履歴のクリーニングを有効にする | `system/magento_scheduled_import_export_log/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 開始時間 | `system/magento_scheduled_import_export_log/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頻度 | `system/magento_scheduled_import_export_log/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メールテンプレートのエラー | `system/magento_scheduled_import_export_log/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### 開発者用パス

これらの設定値は、**ストア**/設定/**設定**/**詳細**/**開発者**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerceだけ？ |
|--------------|--------------|--------------|
| ワークフロータイプ | `dev/front_end_development_workflow/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| シンボリックリンクを許可 | `dev/template/allow_symlink` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Htmlを縮小 | `dev/template/minify_html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ストアフロントのテンプレートパスヒントを有効にする | `dev/debug/template_hints_storefront` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 管理者のテンプレートパスヒントを有効にする | `dev/debug/template_hints_admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ブロック名をヒントに追加 | `dev/debug/template_hints_blocks` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ファイルにログイン | `dev/debug/debug_logging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| syslogにログイン | `dev/syslog/syslog_logging` |  |
| ストアフロントで有効 | `dev/translate_inline/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 管理者に対して有効 | `dev/translate_inline/active_admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| JavaScript ファイルの結合 | `dev/js/merge_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| JavaScript バンドルを有効にする | `dev/js/enable_js_bundling` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| JavaScriptファイルを縮小 | `dev/js/minify_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 翻訳戦略 | `dev/js/translate_strategy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| セッションストレージへのJS エラーのログ記録 | `dev/js/session_storage_logging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CSS ファイルを結合 | `dev/css/merge_css_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CSS ファイルを縮小 | `dev/css/minify_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 画像アダプタ | `dev/image/default_adapter` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 静的ファイルに署名 | `dev/static/sign` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 非同期インデックス作成 | `dev/grid/async_indexing` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ユーザー定義属性のキャッシュ | `dev/caching/cache_user_defined_attributes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
