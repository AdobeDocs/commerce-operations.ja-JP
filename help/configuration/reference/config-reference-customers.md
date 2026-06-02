---
title: 顧客設定パス リファレンス
description: Adobe Commerceの管理者設定で、お客様の設定パスと値について説明します。 ニュースレター、アカウント管理、カスタマーサービスの各オプションをご確認ください。
feature: Configuration, Customers
exl-id: a0571423-6fbd-4cfc-9797-a13c0c24bb53
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '945'
ht-degree: 0%

---

# 顧客設定パス リファレンス

このセクションでは、管理者の&#x200B;**ストア**/設定/**構成**/**顧客**&#x200B;のオプションで使用できる変数名と構成パスを一覧表示します。

[`magento app:config:dump` コマンド &#x200B;](../cli/export-configuration.md)は、これらの値をソース コントロールにある共有設定ファイル `app/etc/config.php`に書き込みます。 任意の構成設定を上書きする方法や、機密設定を設定する方法については、[環境変数を使用して構成設定を上書きする](override-config-settings.md#environment-variables)を参照してください。 このトピックでは、_not_&#x200B;に[機密値とシステム固有の値](config-reference-sens.md)が一覧表示されています。

## ニュースレター・パス

これらの設定値は、**ストア**/設定/**設定**/**顧客**/**ニュースレター**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerceだけ？ |
|--------------|--------------|--------------|
| ゲストのサブスクリプションを許可 | `newsletter/subscription/allow_guest_subscribe` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 確認の必要性 | `newsletter/subscription/confirm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 確認メール送信者 | `newsletter/subscription/confirm_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 確認メールテンプレート | `newsletter/subscription/confirm_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 成功メール送信者 | `newsletter/subscription/success_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| サクセスメールテンプレート | `newsletter/subscription/success_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 購読解除メール送信者 | `newsletter/subscription/un_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 購読解除メールテンプレート | `newsletter/subscription/un_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 顧客設定パス

これらの設定値は、**Stores**/設定/**Configuration**/**Customers**/**Customer Configuration**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerceだけ？ |
|--------------|--------------|--------------|
| オンライン分間隔 | `customer/online_customers/online_minutes_interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顧客アカウントの共有 | `customer/account_share/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顧客グループへの自動割り当てを有効にする | `customer/create_account/auto_group_assign` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 次に基づく税計算 | `customer/create_account/tax_calculation_address_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デフォルトグループ | `customer/create_account/default_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効なVAT IDのグループ – 国内 | `customer/create_account/viv_domestic_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効なVAT IDのグループ - Intra-Union | `customer/create_account/viv_intra_union_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 無効なVAT IDのグループ | `customer/create_account/viv_invalid_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 検証エラーグループ | `customer/create_account/viv_error_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 各トランザクションを検証 | `customer/create_account/viv_on_each_transaction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| VAT IDに基づく自動グループ変更を無効にするデフォルト値 | `customer/create_account/viv_disable_auto_group_assign_default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ストアフロントにVAT番号を表示 | `customer/create_account/vat_frontend_visibility` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デフォルトのウェルカムメール | `customer/create_account/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パスワードのないデフォルトのウェルカムメール | `customer/create_account/email_no_password_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メール送信者 | `customer/create_account/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メール確認を要求 | `customer/create_account/confirm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 確認リンクのメール | `customer/create_account/email_confirmation_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ウェルカムメール | `customer/create_account/email_confirmed_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 人に適した顧客IDの生成 | `customer/create_account/generate_human_friendly_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パスワードリセット保護タイプ | `customer/password/password_reset_protection_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パスワードリセット要求の最大数 | `customer/password/max_number_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パスワードのリセット要求の間の最小時間 | `customer/password/min_time_between_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メールテンプレートを忘れた場合 | `customer/password/forgot_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| リマインドメールテンプレート | `customer/password/remind_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パスワードテンプレートのリセット | `customer/password/reset_password_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パスワードテンプレートのメール送信者 | `customer/password/forgot_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 回復リンクの有効期限（時間） | `customer/password/reset_link_expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ログイン時/パスワードを忘れた場合にオートコンプリートを有効にする | `customer/password/autocomplete_on_storefront` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 必要な文字クラスの数 | `customer/password/required_character_classes_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ロックアウトアカウントへの最大ログイン失敗 | `customer/password/lockout_failures` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パスワードの最小長 | `customer/password/minimum_password_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ロックアウト時間（分） | `customer/password/lockout_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 住所の行数 | `customer/address/street_lines` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 接頭辞を表示 | `customer/address/prefix_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 接頭辞ドロップダウンオプション | `customer/address/prefix_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ミドルネームを表示（初期） | `customer/address/middlename_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 接尾辞を表示 | `customer/address/suffix_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 接尾辞ドロップダウンオプション | `customer/address/suffix_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 生年月日を表示 | `customer/address/dob_show`<br>現在のセキュリティとプライバシーのベストプラクティスに従って、データを収集または処理する前に、お客様の生年月日（月、日、年）およびその他の個人識別子（氏名など）を保存することに関連する潜在的な法的およびセキュリティ上のリスクを必ず認識してください。 | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 消費税/VAT番号を表示 | `customer/address/taxvat_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 性別を表示 | `customer/address/gender_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ストアクレジット機能の有効化 | `customer/magento_customerbalance/is_enabled` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| ストアのクレジット履歴を顧客に表示 | `customer/magento_customerbalance/show_history` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| ストアのクレジットを自動的に返金 | `customer/magento_customerbalance/refund_automatically` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| Store Credit Update Email Sender | `customer/magento_customerbalance/email_identity` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| ストアクレジット更新メールテンプレート | `customer/magento_customerbalance/email_template` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| ログイン後、お客様をアカウントダッシュボードにリダイレクト | `customer/startup/redirect_dashboard` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| テキスト | `customer/address_templates/text` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| テキスト 1行 | `customer/address_templates/oneline` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTML | `customer/address_templates/html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PDF | `customer/address_templates/pdf` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顧客セグメント機能の有効化 | `customer/magento_customersegment/is_enabled` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| ストアフロントでCAPTCHAを有効にする | `customer/captcha/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| フォント | `customer/captcha/font` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Forms | `customer/captcha/forms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 表示モード | `customer/captcha/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ログインに失敗した試行回数 | `customer/captcha/failed_attempts_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CAPTCHA タイムアウト（分） | `customer/captcha/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| シンボル数 | `customer/captcha/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CAPTCHAで使用される記号 | `customer/captcha/symbols` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 大文字と小文字を区別 | `customer/captcha/case_sensitive` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## ウィッシュリストのパス

これらの設定値は、**ストア**/設定/**設定**/**顧客**/**ウィッシュリスト**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerceだけ？ |
|--------------|--------------|--------------|
| 有効 | `wishlist/general/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 複数のウィッシュリストを有効にする | `wishlist/general/multiple_enabled` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 複数のウィッシュリストの数 | `wishlist/general/multiple_wishlist_number` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| メール送信者 | `wishlist/email/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メールテンプレート | `wishlist/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送信可能な最大電子メール数 | `wishlist/email/number_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 電子メールテキストの長さの制限 | `wishlist/email/text_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ウィッシュリストの概要の表示 | `wishlist/wishlist_link/use_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 招待パス

これらの設定値は、**ストア**/設定/**設定**/**顧客**/**招待**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerceだけ？ |
|--------------|--------------|--------------|
| 招待状の機能を有効にする | `magento_invitation/general/enabled` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| ストアフロントで招待を有効にする | `magento_invitation/general/enabled_on_front` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| リファラー顧客グループ | `magento_invitation/general/registration_use_inviter_group` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 新規口座登録 | `magento_invitation/general/registration_required_invitation` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 顧客が招待メールにカスタムメッセージを追加することを許可 | `magento_invitation/general/allow_customer_message` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 1回に送信できる招待の最大数 | `magento_invitation/general/max_invitation_amount_per_send` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 顧客の招待メール送信者 | `magento_invitation/email/identity` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 顧客招待状メールテンプレート | `magento_invitation/email/template` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## ポイントのパスへの報酬

これらの設定値は、**ストア**/設定/**設定**/**顧客**/**報酬ポイント**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerceだけ？ |
|--------------|--------------|--------------|
| 報酬ポイント機能を有効にする | `magento_reward/general/is_enabled` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| ストアフロントで報酬ポイント機能を有効にする | `magento_reward/general/is_enabled_on_front` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 顧客に報酬ポイントの履歴が表示される場合がある | `magento_reward/general/publish_history` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 報酬ポイント残高の引き換えしきい値 | `magento_reward/general/min_points_balance` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 報酬ポイントの残高を上限 | `magento_reward/general/max_points_balance` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 報酬ポイントの有効期限（日数） | `magento_reward/general/expiration_days` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 報酬ポイントの有効期限の計算 | `magento_reward/general/expiry_calculation` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 報酬ポイントを自動的に返金 | `magento_reward/general/refund_automatically` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 返金金額から報酬ポイントを自動的に差し引く | `magento_reward/general/deduct_automatically` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| ランディングページ | `magento_reward/general/landing_page` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 購入 | `magento_reward/points/order` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 登録 | `magento_reward/points/register` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| ニュースレター登録 | `magento_reward/points/newsletter` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 招待状をお客様に変換する | `magento_reward/points/invitation_customer` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 顧客コンバージョンへの招待数の制限 | `magento_reward/points/invitation_customer_limit` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 招待を注文に変換 | `magento_reward/points/invitation_order` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 注文への招待状コンバージョン数の制限 | `magento_reward/points/invitation_order_limit` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 注文特典への招待状の変換 | `magento_reward/points/invitation_order_frequency` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 送信をレビュー | `magento_reward/points/review` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| リワード付きレビューの送信数量制限 | `magento_reward/points/review_limit` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| メール送信者 | `magento_reward/notification/email_sender` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| デフォルトで顧客を購読 | `magento_reward/notification/subscribe_by_default` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 残高の更新メール | `magento_reward/notification/balance_update_template` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 報酬ポイントの有効期限に関する警告メール | `magento_reward/notification/expiry_warning_template` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 有効期限の警告（日） | `magento_reward/notification/expiry_day_before` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## プロモーションパス

これらの設定値は、**ストア**/設定/**設定**/**顧客**/**プロモーション**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerceだけ？ |
|--------------|--------------|--------------|
| リマインダーメールを有効にする | `promo/magento_reminder/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 頻度 | `promo/magento_reminder/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 間隔 | `promo/magento_reminder/interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minute of the Hour | `promo/magento_reminder/minutes` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 開始時間 | `promo/magento_reminder/time` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 1回の実行あたりの最大メール数 | `promo/magento_reminder/limit` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| メール送信の失敗しきい値 | `promo/magento_reminder/threshold` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| リマインダーメール送信者 | `promo/magento_reminder/identity` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| コード長 | `promo/auto_generated_coupon_codes/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コード形式 | `promo/auto_generated_coupon_codes/format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コード接頭辞 | `promo/auto_generated_coupon_codes/prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コードサフィックス | `promo/auto_generated_coupon_codes/suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ダッシュのX文字ごと | `promo/auto_generated_coupon_codes/dash` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## ギフトレジストリパス

これらの設定値は、**Stores**/設定/**Configuration**/**Customers**/**Gift Registry**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerceだけ？ |
|--------------|--------------|--------------|
| ギフトレジストリを有効にする | `magento_giftregistry/general/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大登録者数 | `magento_giftregistry/general/max_registrant` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メールテンプレート | `magento_giftregistry/owner_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メール送信者 | `magento_giftregistry/owner_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メールテンプレート | `magento_giftregistry/sharing_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メール送信者 | `magento_giftregistry/sharing_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メールの送信数のしきい値の最大値 | `magento_giftregistry/sharing_email/send_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メールテンプレート | `magento_giftregistry/update_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メール送信者 | `magento_giftregistry/update_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 永続的なショッピングカートのパス

これらの設定値は、**ストア**/設定/**設定**/**顧客**/**永続的なショッピングカート**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerceだけ？ |
|--------------|--------------|--------------|
| 永続性を有効にする | `persistent/options/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 永続性の有効期間（秒） | `persistent/options/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 「自分を記憶」を有効にする | `persistent/options/remember_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| &quot;Remember Me&quot; デフォルト値 | `persistent/options/remember_default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ログアウト時の永続性のクリア | `persistent/options/logout_clear` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 買い物かごを保持 | `persistent/options/shopping_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ウィッシュリストを保持 | `persistent/options/wishlist` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最近注文した項目を保持する | `persistent/options/recently_ordered` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 現在の比較製品を保持する | `persistent/options/compare_current` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 比較履歴を保持 | `persistent/options/compare_history` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最近閲覧した商品を保持する | `persistent/options/recently_viewed` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顧客グループのメンバーシップとセグメンテーションの保持 | `persistent/options/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
