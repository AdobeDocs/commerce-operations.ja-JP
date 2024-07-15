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

この節では、**ストア**/設定/**設定**/**顧客** の管理でオプションに使用できる変数名と設定パスを示します。

[`magento app:config:dump` コマンドは ](../cli/export-configuration.md) これらの値をソース管理にある共有構成ファイル `app/etc/config.php` に書き込みます。 任意の構成設定を上書きしたり、重要な設定を指定したりするには、[ 環境変数を使用して構成設定を上書き ](override-config-settings.md#environment-variables) を参照してください。 このトピックでは _機密の値とシステム固有の値 [ は_ 表示されません ](config-reference-sens.md)。

## ニュースレターのパス

これらの設定値は、管理者の **ストア**/設定/**設定**/**顧客**/**ニュースレター** で利用できます。

| 名前 | 設定パス | Commerceのみ？ |
|--------------|--------------|--------------|
| ゲストによる購読を許可 | `newsletter/subscription/allow_guest_subscribe` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 確認が必要 | `newsletter/subscription/confirm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 確認 E メールの送信者 | `newsletter/subscription/confirm_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 確認 E メール テンプレート | `newsletter/subscription/confirm_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 成功したメールの送信者 | `newsletter/subscription/success_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 成功の E メール テンプレート | `newsletter/subscription/success_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 購読解除メールの送信者 | `newsletter/subscription/un_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 購読解除 E メールテンプレート | `newsletter/subscription/un_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 顧客設定パス

これらの設定値は、管理者の **ストア**/設定/**設定**/**顧客**/**顧客設定** で利用できます。

| 名前 | 設定パス | Commerceのみ？ |
|--------------|--------------|--------------|
| オンライン分間隔 | `customer/online_customers/online_minutes_interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顧客アカウントの共有 | `customer/account_share/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顧客グループへの自動割り当てを有効にする | `customer/create_account/auto_group_assign` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 基づく税計算 | `customer/create_account/tax_calculation_address_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 既定のグループ | `customer/create_account/default_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効な VAT ID のグループ – 国内 | `customer/create_account/viv_domestic_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効な VAT ID のグループ – 組合内 | `customer/create_account/viv_intra_union_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 無効な VAT ID のグループ | `customer/create_account/viv_invalid_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 検証エラーグループ | `customer/create_account/viv_error_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 各トランザクションの検証 | `customer/create_account/viv_on_each_transaction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| VAT ID に基づく自動グループ変更を無効にする既定値 | `customer/create_account/viv_disable_auto_group_assign_default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ストアフロントに VAT 番号を表示 | `customer/create_account/vat_frontend_visibility` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デフォルトのようこそメール | `customer/create_account/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パスワードなしの既定のウェルカムメール | `customer/create_account/email_no_password_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E メール送信者 | `customer/create_account/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Require Emails Confirmation | `customer/create_account/confirm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 確認リンクメール | `customer/create_account/email_confirmation_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| お知らせメール | `customer/create_account/email_confirmed_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 人間にとってわかりやすい顧客 ID を生成 | `customer/create_account/generate_human_friendly_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パスワードリセット保護タイプ | `customer/password/password_reset_protection_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パスワードリセット要求の最大数 | `customer/password/max_number_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パスワードリセット要求の最小間隔 | `customer/password/min_time_between_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メールを忘れた場合のテンプレート | `customer/password/forgot_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メールテンプレートにリマインド | `customer/password/remind_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パスワードリセットテンプレート | `customer/password/reset_password_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パスワードテンプレートメールの送信者 | `customer/password/forgot_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 復旧リンクの有効期限（時間） | `customer/password/reset_link_expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ログイン / パスワードを忘れた場合のフォームのオートコンプリートを有効にする | `customer/password/autocomplete_on_storefront` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 必要な文字クラスの数 | `customer/password/required_character_classes_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ロックアウト アカウントへのログイン エラーの最大数 | `customer/password/lockout_failures` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パスワードの最小長 | `customer/password/minimum_password_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ロックアウト時間（分） | `customer/password/lockout_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 番地の行数 | `customer/address/street_lines` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| プレフィックスを表示 | `customer/address/prefix_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| プレフィックス ドロップダウンオプション | `customer/address/prefix_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ミドルネームを表示（初期） | `customer/address/middlename_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 接尾辞を表示 | `customer/address/suffix_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 接尾辞ドロップダウンオプション | `customer/address/suffix_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 生年月日を表示 | `customer/address/dob_show`<br> 現在のセキュリティとプライバシーのベストプラクティスに従って、顧客の完全な生年月日（月、日、年）と、氏名などの他の個人識別子の保存に関連して発生する可能性のある法的およびセキュリティリスクを、データの収集または処理の前に認識しておいてください。 | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 税/VAT 番号の表示 | `customer/address/taxvat_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 性別を表示 | `customer/address/gender_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ストアクレジット機能の有効化 | `customer/magento_customerbalance/is_enabled` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 顧客に店舗の与信履歴を表示 | `customer/magento_customerbalance/show_history` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 店舗クレジットの自動払戻 | `customer/magento_customerbalance/refund_automatically` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| クレジット更新メール送信者の保存 | `customer/magento_customerbalance/email_identity` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 店舗のクレジット更新の E メール テンプレート | `customer/magento_customerbalance/email_template` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| ログイン後のアカウントダッシュボードへのリダイレクト | `customer/startup/redirect_dashboard` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| テキスト | `customer/address_templates/text` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 1 行のテキスト | `customer/address_templates/oneline` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTML | `customer/address_templates/html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PDF | `customer/address_templates/pdf` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顧客セグメント機能の有効化 | `customer/magento_customersegment/is_enabled` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| ストアフロントでの CAPTCHA の有効化 | `customer/captcha/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| フォント | `customer/captcha/font` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Forms | `customer/captcha/forms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 表示モード | `customer/captcha/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 失敗したログイン試行回数 | `customer/captcha/failed_attempts_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CAPTCHA タイムアウト （分） | `customer/captcha/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| シンボルの数 | `customer/captcha/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CAPTCHA で使用されるシンボル | `customer/captcha/symbols` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 大文字と小文字を区別 | `customer/captcha/case_sensitive` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 欲しい物のリストのパス

これらの設定値は、管理者の **ストア**/設定/**設定**/**顧客**/**ウィッシュリスト** で利用できます。

| 名前 | 設定パス | Commerceのみ？ |
|--------------|--------------|--------------|
| Enabled | `wishlist/general/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 複数のウィッシュリストを有効にする | `wishlist/general/multiple_enabled` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 複数のウィッシュリストの数 | `wishlist/general/multiple_wishlist_number` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| E メール送信者 | `wishlist/email/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E メール テンプレート | `wishlist/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送信可能な最大メール数 | `wishlist/email/number_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 電子メールテキストの長さの制限 | `wishlist/email/text_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ウィッシュリストの概要を表示 | `wishlist/wishlist_link/use_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 招待のパス

これらの設定値は、管理者の **ストア**/設定/**設定**/**顧客**/**招待状** で使用できます。

| 名前 | 設定パス | Commerceのみ？ |
|--------------|--------------|--------------|
| 招待機能の有効化 | `magento_invitation/general/enabled` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| ストアフロントでの招待状の有効化 | `magento_invitation/general/enabled_on_front` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 紹介済み顧客グループ | `magento_invitation/general/registration_use_inviter_group` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 新規アカウントの登録 | `magento_invitation/general/registration_required_invitation` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 顧客が招待メールにカスタムメッセージを追加することを許可 | `magento_invitation/general/allow_customer_message` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 一度に送信できる最大招待状 | `magento_invitation/general/max_invitation_amount_per_send` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 顧客招待メールの送信者 | `magento_invitation/email/identity` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 顧客招待 E メール テンプレート | `magento_invitation/email/template` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## 報酬ポイントのパス

これらの設定値は、管理者の **ストア**/設定/**設定**/**顧客**/**報酬ポイント** で利用できます。

| 名前 | 設定パス | Commerceのみ？ |
|--------------|--------------|--------------|
| 報酬ポイント機能の有効化 | `magento_reward/general/is_enabled` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| ストアフロントでの報酬ポイント機能の有効化 | `magento_reward/general/is_enabled_on_front` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 顧客には、報酬ポイント履歴が表示される場合があります | `magento_reward/general/publish_history` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 報酬ポイントの残高償還しきい値 | `magento_reward/general/min_points_balance` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| キャップの報酬ポイントのバランス | `magento_reward/general/max_points_balance` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 報酬ポイントの有効期限（日） | `magento_reward/general/expiration_days` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 報酬ポイントの有効期限の計算 | `magento_reward/general/expiry_calculation` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 報酬ポイントを自動的に払い戻す | `magento_reward/general/refund_automatically` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 自動的に返金額から報酬ポイントを差し引く | `magento_reward/general/deduct_automatically` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| ランディングページ | `magento_reward/general/landing_page` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 購入 | `magento_reward/points/order` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 登録 | `magento_reward/points/register` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| ニュースレターの登録 | `magento_reward/points/newsletter` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 招待状を顧客に変換しています | `magento_reward/points/invitation_customer` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 顧客コンバージョン数量制限への招待 | `magento_reward/points/invitation_customer_limit` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 招待状を注文に変換しています | `magento_reward/points/invitation_order` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 注文コンバージョンの数量制限への招待 | `magento_reward/points/invitation_order_limit` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| ご注文へのご案内コンバージョン | `magento_reward/points/invitation_order_frequency` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| Review Submission | `magento_reward/points/review` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 報酬済レビューの送信数量制限 | `magento_reward/points/review_limit` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| E メール送信者 | `magento_reward/notification/email_sender` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| デフォルトで顧客を登録 | `magento_reward/notification/subscribe_by_default` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 残高更新メール | `magento_reward/notification/balance_update_template` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 報酬ポイントの有効期限警告メール | `magento_reward/notification/expiry_warning_template` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| （日間）前の有効期限の警告 | `magento_reward/notification/expiry_day_before` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## プロモーションパス

これらの設定値は、管理者の **ストア**/設定/**設定**/**顧客**/**プロモーション** で使用できます。

| 名前 | 設定パス | Commerceのみ？ |
|--------------|--------------|--------------|
| リマインダーメールを有効にする | `promo/magento_reminder/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頻度 | `promo/magento_reminder/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 間隔 | `promo/magento_reminder/interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 分（時刻） | `promo/magento_reminder/minutes` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 開始時刻 | `promo/magento_reminder/time` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 1 回の実行あたりの最大メール数 | `promo/magento_reminder/limit` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| E メール送信失敗しきい値 | `promo/magento_reminder/threshold` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| リマインダーメールの送信者 | `promo/magento_reminder/identity` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| コード長 | `promo/auto_generated_coupon_codes/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コードフォーマット | `promo/auto_generated_coupon_codes/format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コードプレフィックス | `promo/auto_generated_coupon_codes/prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コードサフィックス | `promo/auto_generated_coupon_codes/suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| X 文字ごとにダッシュ | `promo/auto_generated_coupon_codes/dash` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## ギフト レジストリのパス

これらの設定値は、管理者の **ストア**/設定/**設定**/**顧客**/**ギフトレジストリ** で使用できます。

| 名前 | 設定パス | Commerceのみ？ |
|--------------|--------------|--------------|
| ギフト レジストリを有効にする | `magento_giftregistry/general/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大登録者数 | `magento_giftregistry/general/max_registrant` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E メール テンプレート | `magento_giftregistry/owner_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E メール送信者 | `magento_giftregistry/owner_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E メール テンプレート | `magento_giftregistry/sharing_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E メール送信者 | `magento_giftregistry/sharing_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大送信数 E メールしきい値 | `magento_giftregistry/sharing_email/send_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E メール テンプレート | `magento_giftregistry/update_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E メール送信者 | `magento_giftregistry/update_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 永続的な買い物かごパス

これらの設定値は、管理者の **ストア**/設定/**設定**/**顧客**/**永続的な買い物かご** で使用できます。

| 名前 | 設定パス | Commerceのみ？ |
|--------------|--------------|--------------|
| 永続性を有効にする | `persistent/options/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 永続性の有効期間（秒） | `persistent/options/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 「Remember Me」を有効にする | `persistent/options/remember_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 「記録する」デフォルト値 | `persistent/options/remember_default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ログアウト時に永続性をクリア | `persistent/options/logout_clear` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 買い物かごを永続化 | `persistent/options/shopping_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ウィッシュリストを永続化 | `persistent/options/wishlist` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最近注文した項目を保持 | `persistent/options/recently_ordered` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 現在比較されている製品を保持 | `persistent/options/compare_current` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 比較履歴の保持 | `persistent/options/compare_history` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最近表示した製品の保持 | `persistent/options/recently_viewed` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顧客グループメンバーシップとセグメント化の保持 | `persistent/options/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
