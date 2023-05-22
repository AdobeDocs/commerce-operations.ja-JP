---
title: 顧客設定パスのリファレンス
description: 顧客の設定値のリストを参照してください。
feature: Configuration, Customers
exl-id: a0571423-6fbd-4cfc-9797-a13c0c24bb53
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '883'
ht-degree: 0%

---

# 顧客設定パスのリファレンス

この節では、以下の管理で使用できる変数名と設定パスを示します。 **ストア** /設定/ **設定** > **顧客**.

この [`magento app:config:dump` command](../cli/export-configuration.md) は、これらの値を共有設定ファイルに書き込みます。 `app/etc/config.php`（ソース管理下に置く必要があります） オプションで設定を上書きしたり、機密設定を設定したりするには、 [環境変数を使用して設定を上書きする](override-config-settings.md#environment-variables). このトピックでは、 _not_ リスト [機密性の高いシステム固有の値](config-reference-sens.md).

## ニュースレターのパス

これらの設定値は、 **ストア** /設定/ **設定** > **顧客** > **ニュースレター**.

| 名前 | 設定パス | コマースのみ？ |
|--------------|--------------|--------------|
| ゲスト購読を許可 | `newsletter/subscription/allow_guest_subscribe` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 確認が必要 | `newsletter/subscription/confirm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 確認メール送信者 | `newsletter/subscription/confirm_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 確認メールテンプレート | `newsletter/subscription/confirm_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 成功したメール送信者 | `newsletter/subscription/success_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 成功メールテンプレート | `newsletter/subscription/success_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 配信停止メール送信者 | `newsletter/subscription/un_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メールテンプレートの購読解除 | `newsletter/subscription/un_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 顧客設定パス

これらの設定値は、 **ストア** /設定/ **設定** > **顧客** > **顧客設定**.

| 名前 | 設定パス | コマースのみ？ |
|--------------|--------------|--------------|
| オンラインの分間隔 | `customer/online_customers/online_minutes_interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顧客アカウントの共有 | `customer/account_share/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顧客グループへの自動割り当ての有効化 | `customer/create_account/auto_group_assign` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 次に基づく税の計算 | `customer/create_account/tax_calculation_address_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デフォルトのグループ | `customer/create_account/default_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効な VAT ID のグループ — 国内 | `customer/create_account/viv_domestic_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効な VAT ID のグループ — EU 内 | `customer/create_account/viv_intra_union_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 無効な VAT ID のグループ | `customer/create_account/viv_invalid_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 検証エラーグループ | `customer/create_account/viv_error_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 各トランザクションでの検証 | `customer/create_account/viv_on_each_transaction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| VAT ID に基づく自動グループ変更の無効化のデフォルト値 | `customer/create_account/viv_disable_auto_group_assign_default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ストアフロントに VAT 番号を表示 | `customer/create_account/vat_frontend_visibility` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デフォルトのお知らせメール | `customer/create_account/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パスワードなしのデフォルトのお知らせメール | `customer/create_account/email_no_password_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メール送信者 | `customer/create_account/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メールの確認が必要 | `customer/create_account/confirm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 確認リンクメール | `customer/create_account/email_confirmation_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| お知らせメール | `customer/create_account/email_confirmed_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 人間にやさしい顧客 ID の生成 | `customer/create_account/generate_human_friendly_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パスワードリセット保護の種類 | `customer/password/password_reset_protection_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パスワードリセット要求の最大数 | `customer/password/max_number_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パスワードリセット要求の最小間隔 | `customer/password/min_time_between_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メールテンプレートを忘れた場合 | `customer/password/forgot_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メールテンプレートを通知 | `customer/password/remind_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パスワードテンプレートのリセット | `customer/password/reset_password_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パスワードテンプレートメール送信者 | `customer/password/forgot_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 回復リンクの有効期限（時間） | `customer/password/reset_link_expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ログイン/パスワードを忘れた場合のオートコンプリートを有効にする | `customer/password/autocomplete_on_storefront` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 必要な文字クラスの数 | `customer/password/required_character_classes_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ロックアウトアカウントに対する最大ログイン失敗数 | `customer/password/lockout_failures` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パスワードの最小長 | `customer/password/minimum_password_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ロックアウト時間（分） | `customer/password/lockout_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 番地内の行数 | `customer/address/street_lines` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| プレフィックスを表示 | `customer/address/prefix_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| プレフィックスドロップダウンオプション | `customer/address/prefix_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ミドルネームを表示（初期） | `customer/address/middlename_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| サフィックスを表示 | `customer/address/suffix_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| サフィックスドロップダウンオプション | `customer/address/suffix_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 生年月日を表示 | `customer/address/dob_show`<br>現在のセキュリティおよびプライバシーのベストプラクティスに従い、顧客の生年月日（月、日、年）のストレージに関連する法的リスクとセキュリティリスクの可能性、およびその他の個人 ID（氏名など）を把握してから、データを収集または処理してください。 | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 税/VAT 番号の表示 | `customer/address/taxvat_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 性別を表示 | `customer/address/gender_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 店舗クレジット機能の有効化 | `customer/magento_customerbalance/is_enabled` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 顧客に対する店舗クレジット履歴の表示 | `customer/magento_customerbalance/show_history` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 店舗クレジットの自動返金 | `customer/magento_customerbalance/refund_automatically` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| ストアクレジット更新メール送信者 | `customer/magento_customerbalance/email_identity` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| クレジット更新メールテンプレートを保存 | `customer/magento_customerbalance/email_template` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| ログイン後に顧客をアカウントダッシュボードにリダイレクト | `customer/startup/redirect_dashboard` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| テキスト | `customer/address_templates/text` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| テキスト 1 行 | `customer/address_templates/oneline` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTML | `customer/address_templates/html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PDF | `customer/address_templates/pdf` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顧客セグメント機能の有効化 | `customer/magento_customersegment/is_enabled` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| ストアフロントでの CAPTCHA の有効化 | `customer/captcha/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| フォント | `customer/captcha/font` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Forms | `customer/captcha/forms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 表示モード | `customer/captcha/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ログイン失敗の回数 | `customer/captcha/failed_attempts_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CAPTCHA タイムアウト（分） | `customer/captcha/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| シンボル数 | `customer/captcha/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CAPTCHA で使用されるシンボル | `customer/captcha/symbols` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 大文字と小文字を区別 | `customer/captcha/case_sensitive` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## ウィッシュリストのパス

これらの設定値は、 **ストア** /設定/ **設定** > **顧客** > **ウィッシュリスト**.

| 名前 | 設定パス | コマースのみ？ |
|--------------|--------------|--------------|
| 有効 | `wishlist/general/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 複数のウィッシュリストの有効化 | `wishlist/general/multiple_enabled` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 複数のウィッシュリストの数 | `wishlist/general/multiple_wishlist_number` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| メール送信者 | `wishlist/email/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メールテンプレート | `wishlist/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送信可能な最大メール数 | `wishlist/email/number_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メールテキストの長さ制限 | `wishlist/email/text_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ウィッシュリストの概要を表示 | `wishlist/wishlist_link/use_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 招待パス

これらの設定値は、 **ストア** /設定/ **設定** > **顧客** > **招待**.

| 名前 | 設定パス | コマースのみ？ |
|--------------|--------------|--------------|
| 招待機能の有効化 | `magento_invitation/general/enabled` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| ストアフロントでの招待を有効にする | `magento_invitation/general/enabled_on_front` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 参照元の顧客グループ | `magento_invitation/general/registration_use_inviter_group` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 新規アカウントの登録 | `magento_invitation/general/registration_required_invitation` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 顧客による招待メールへのカスタムメッセージの追加を許可 | `magento_invitation/general/allow_customer_message` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 一度に送信できる最大招待数 | `magento_invitation/general/max_invitation_amount_per_send` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 顧客招待メール送信者 | `magento_invitation/email/identity` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 顧客招待メールテンプレート | `magento_invitation/email/template` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## ポイントパスの報奨

これらの設定値は、 **ストア** /設定/ **設定** > **顧客** > **報酬ポイント**.

| 名前 | 設定パス | コマースのみ？ |
|--------------|--------------|--------------|
| 報酬ポイント機能の有効化 | `magento_reward/general/is_enabled` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| ストアフロントの報酬ポイント機能を有効にする | `magento_reward/general/is_enabled_on_front` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| お客様が報酬ポイント履歴を確認できる | `magento_reward/general/publish_history` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 報酬ポイント残高引き換えしきい値 | `magento_reward/general/min_points_balance` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 最大報酬ポイントの残高 | `magento_reward/general/max_points_balance` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 有効期限が切れる報酬ポイント（日数） | `magento_reward/general/expiration_days` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 報酬ポイントの有効期限の計算 | `magento_reward/general/expiry_calculation` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 報酬ポイントを自動的に返金 | `magento_reward/general/refund_automatically` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 返金額から報酬ポイントを自動的に差し引く | `magento_reward/general/deduct_automatically` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| ランディングページ | `magento_reward/general/landing_page` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 購入 | `magento_reward/points/order` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 登録 | `magento_reward/points/register` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| ニュースレターのサインアップ | `magento_reward/points/newsletter` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| お客様への招待の変換 | `magento_reward/points/invitation_customer` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 顧客コンバージョン数量制限への招待 | `magento_reward/points/invitation_customer_limit` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 招待を注文に変換中 | `magento_reward/points/invitation_order` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 受注換算数量制限への招待 | `magento_reward/points/invitation_order_limit` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 注文報酬への招待状の変換 | `magento_reward/points/invitation_order_frequency` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| レビューの送信 | `magento_reward/points/review` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 報酬レビュー発行数量制限 | `magento_reward/points/review_limit` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| メール送信者 | `magento_reward/notification/email_sender` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| デフォルトで顧客を購読 | `magento_reward/notification/subscribe_by_default` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 残高更新メール | `magento_reward/notification/balance_update_template` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 報酬ポイントの有効期限警告メール | `magento_reward/notification/expiry_warning_template` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| （日）前の有効期限警告 | `magento_reward/notification/expiry_day_before` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## プロモーションパス

これらの設定値は、 **ストア** /設定/ **設定** > **顧客** > **プロモーション**.

| 名前 | 設定パス | コマースのみ？ |
|--------------|--------------|--------------|
| リマインダーメールの有効化 | `promo/magento_reminder/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頻度 | `promo/magento_reminder/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 間隔 | `promo/magento_reminder/interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 時間の分 | `promo/magento_reminder/minutes` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 開始時間 | `promo/magento_reminder/time` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 1 回の実行あたりの最大メール数 | `promo/magento_reminder/limit` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| メール送信失敗しきい値 | `promo/magento_reminder/threshold` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| リマインダーメール送信者 | `promo/magento_reminder/identity` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| コードの長さ | `promo/auto_generated_coupon_codes/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コード形式 | `promo/auto_generated_coupon_codes/format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コードプレフィックス | `promo/auto_generated_coupon_codes/prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コードサフィックス | `promo/auto_generated_coupon_codes/suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| X 文字ごとにダッシュ | `promo/auto_generated_coupon_codes/dash` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## ギフトレジストリパス

これらの設定値は、 **ストア** /設定/ **設定** > **顧客** > **ギフトレジストリ**.

| 名前 | 設定パス | コマースのみ？ |
|--------------|--------------|--------------|
| ギフトレジストリの有効化 | `magento_giftregistry/general/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大登録者数 | `magento_giftregistry/general/max_registrant` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メールテンプレート | `magento_giftregistry/owner_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メール送信者 | `magento_giftregistry/owner_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メールテンプレート | `magento_giftregistry/sharing_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メール送信者 | `magento_giftregistry/sharing_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大送信メール数しきい値 | `magento_giftregistry/sharing_email/send_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メールテンプレート | `magento_giftregistry/update_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メール送信者 | `magento_giftregistry/update_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 永続的な買い物かごパス

これらの設定値は、 **ストア** /設定/ **設定** > **顧客** > **永続的な買い物かご**.

| 名前 | 設定パス | コマースのみ？ |
|--------------|--------------|--------------|
| 永続化を有効にする | `persistent/options/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 永続化の有効期間（秒） | `persistent/options/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 「このアカウントを記憶する」を有効にする | `persistent/options/remember_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 「このアカウントを記憶する」のデフォルト値 | `persistent/options/remember_default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ログアウト時に永続性をクリア | `persistent/options/logout_clear` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 買い物かごを保持 | `persistent/options/shopping_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ウィッシュリストを保持 | `persistent/options/wishlist` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最近注文した項目を保持 | `persistent/options/recently_ordered` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 現在比較されている製品を保持 | `persistent/options/compare_current` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 比較履歴を保持 | `persistent/options/compare_history` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最近表示した製品を保持 | `persistent/options/recently_viewed` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顧客グループのメンバーシップとセグメント化を保持 | `persistent/options/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
