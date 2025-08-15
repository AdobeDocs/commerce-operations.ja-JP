---
title: 支払構成パス参照
description: 設定可能な支払い方法の値のリストを参照してください。
feature: Configuration, Payments
exl-id: f3e356aa-7262-4d99-9ed4-d77cbd93708c
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '4100'
ht-degree: 0%

---

# 支払構成パス参照

これらの設定値は、管理者の **ストア**/設定/**設定**/**営業**/**支払い方法** で利用できます。

[`magento app:config:dump` コマンドは ](../cli/export-configuration.md) これらの値をソース管理にある共有構成ファイル `app/etc/config.php` に書き込みます。 任意の構成設定を上書きしたり、重要な設定を指定したりするには、[ 環境変数を使用して構成設定を上書き ](override-config-settings.md#environment-variables) を参照してください。 このトピックでは _機密の値とシステム固有の値_ は [ 表示されません ](config-reference-sens.md)。

設定は、支払い方法によってさらに整理されています。

## PayPal パス

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ |
|--------------|--------------|--------------|--------------|
| このソリューションを有効にする | `payment/payflowpro/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コンテキスト内チェックアウトエクスペリエンスを有効にする | `payment/paypal_express/in_context` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal クレジットを有効にする | `payment/payflow_express_bml/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal クレジットを有効にする | `payment/paypal_express_bml/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 表示 | `payment/paypal_express_bml/homepage_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 位置 | `payment/paypal_express_bml/homepage_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| サイズ | `payment/paypal_express_bml/homepage_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 表示 | `payment/paypal_express_bml/categorypage_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 位置 | `payment/paypal_express_bml/categorypage_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| サイズ | `payment/paypal_express_bml/categorypage_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 表示 | `payment/paypal_express_bml/productpage_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 位置 | `payment/paypal_express_bml/productpage_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| サイズ | `payment/paypal_express_bml/productpage_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 表示 | `payment/paypal_express_bml/checkout_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 位置 | `payment/paypal_express_bml/checkout_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| サイズ | `payment/paypal_express_bml/checkout_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 製品詳細ページに表示 | `payment/payflow_express/visible_on_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 買い物かごに表示 | `payment/payflow_express/visible_on_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払い適用元 | `payment/payflow_express/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 適用可能な国の支払い | `payment/payflow_express/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| SSL 検証を有効にする | `payment/payflow_express/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| カート品目の転送 | `payment/payflow_express/line_items_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 注文レビューステップをスキップ | `payment/paypal_express/skip_order_review_step` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| カート品目の転送 | `payment/paypal_express/line_items_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 配送オプションの転送 | `payment/paypal_express/transfer_shipping_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ショートカット ボタンの種類 | `paypal/wpp/button_flavor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal ゲストチェックアウトの有効化 | `payment/paypal_express/solution_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顧客の請求先住所を要求 | `payment/paypal_express/require_billing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 請求契約のサインアップ | `payment/paypal_express/allow_ba_signup` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment/paypal_billing_agreement/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment/paypal_billing_agreement/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment/paypal_billing_agreement/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払いアクション | `payment/paypal_billing_agreement/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払い適用元 | `payment/paypal_billing_agreement/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 適用可能な国の支払い | `payment/paypal_billing_agreement/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| SSL 検証を有効にする | `payment/paypal_billing_agreement/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| カート品目の転送 | `payment/paypal_billing_agreement/line_items_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 請求契約で許可ウィザード | `payment/paypal_billing_agreement/allow_billing_agreement_wizard` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自動取得を有効にする | `paypal/fetch_reports/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュール | `paypal/fetch_reports/schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 時刻 | `paypal/fetch_reports/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal 製品ロゴ | `paypal/style/logo` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ページスタイル | `paypal/style/page_style` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ヘッダー画像 URL | `paypal/style/paypal_hdrimg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ヘッダーの背景色 | `paypal/style/paypal_hdrbackcolor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ヘッダーの境界線のカラー | `paypal/style/paypal_hdrbordercolor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ページの背景色 | `paypal/style/paypal_payflowcolor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| このソリューションを有効にする | `payment/paypal_express/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順 PayPal クレジット | `payment/paypal_express_bml/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment/paypal_express/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment/paypal_express/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払いアクション | `payment/paypal_express/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 製品詳細ページに表示 | `payment/paypal_express/visible_on_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 承認名誉に関する期間（日数） | `payment/paypal_express/authorization_honor_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 注文の有効期間（日数） | `payment/paypal_express/order_valid_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 子認証の数 | `payment/paypal_express/child_authorization_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 買い物かごに表示 | `payment/paypal_express/visible_on_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払い適用元 | `payment/paypal_express/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 適用可能な国の支払い | `payment/paypal_express/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| SSL 検証を有効にする | `payment/paypal_express/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールされた取得 | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal マーチャントページスタイル | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## PayPal ペイメントプロ

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ |
|--------------|--------------|--------------|--------------|
| API 認証方法 | `paypal/wpp/api_authentication` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| API がプロキシを使用 | `paypal/wpp/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールされた取得 | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールされた取得 | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Payments Pro Hosted Solution （英国）

これらのオプションは、[ 商社国 ](../reference/config-reference-sens.md#payment-sensitive-and-system-specific-paths) として英国を選択した場合にのみ使用できます。

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ |
|--------------|--------------|--------------|--------------|
| このソリューションを有効にする | `payment/hosted_pro/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment/hosted_pro/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment/hosted_pro/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払いアクション | `payment/hosted_pro/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払情報ステップに高速チェックアウトを表示する | `payment/hosted_pro/display_ec` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払い適用元 | `payment/hosted_pro/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 適用可能な国の支払い | `payment/hosted_pro/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| SSL 検証を有効にする | `payment/hosted_pro/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## PayPal Payflow Pro

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ |
|--------------|--------------|--------------|--------------|
| Vault 有効 | `payment/payflowpro_cc_vault/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment/payflowpro/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vault タイトル | `payment/payflowpro_cc_vault/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment/payflowpro/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払いアクション | `payment/payflowpro/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 許可されるクレジットカードのタイプ | `payment/payflowpro/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払い適用元 | `payment/payflowpro/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 適用可能な国の支払い | `payment/payflowpro/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| SSL 検証を有効にする | `payment/payflowpro/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CVV エントリが必要 | `payment/payflowpro/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 次の場合にトランザクションを拒否： | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| AVS Street が一致しません | `payment/payflowpro/avs_street` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| AVS Zip が一致しません | `payment/payflowpro/avs_zip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 国際 AVS 指標が一致しません | `payment/payflowpro/avs_international` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| カード セキュリティ コードが一致しません | `payment/payflowpro/avs_security_code` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ベンダー | `payment/payflowpro/vendor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| プロキシを使用 | `payment/payflowpro/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment/payflow_express/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment/payflow_express/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払いアクション | `payment/payflow_express/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールされた取得 | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal マーチャントページスタイル | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パートナー | `payment/payflow_advanced/partner` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ベンダー | `payment/payflow_advanced/vendor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| プロキシを使用 | `payment/payflow_advanced/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| このソリューションを有効にする | `payment/payflow_advanced/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment/payflow_advanced/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment/payflow_advanced/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払いアクション | `payment/payflow_advanced/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払い適用元 | `payment/payflow_advanced/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 適用可能な国の支払い | `payment/payflow_advanced/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| SSL 検証を有効にする | `payment/payflow_advanced/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CVV エントリは編集可能です | `payment/payflow_advanced/csc_editable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CVV エントリが必要 | `payment/payflow_advanced/csc_required` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メールを送信の確認 | `payment/payflow_advanced/email_confirmation` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## PayPal ペイフローリンク

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ |
|--------------|--------------|--------------|--------------|
| パートナー | `payment/payflow_link/partner` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ベンダー | `payment/payflow_link/vendor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ペイフローリンクを有効にする | `payment/payflow_link/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 高速チェックアウトを有効にする | `payment/payflow_express/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順 PayPal クレジット | `payment/payflow_express_bml/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払い適用元 | `payment/payflow_link/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 適用可能な国の支払い | `payment/payflow_link/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| SSL 検証を有効にする | `payment/payflow_link/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CVV エントリは編集可能です | `payment/payflow_link/csc_editable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CVV エントリが必要 | `payment/payflow_link/csc_required` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メールを送信の確認 | `payment/payflow_link/email_confirmation` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールされた取得 | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment/payflow_link/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment/payflow_link/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払いアクション | `payment/payflow_link/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 小計ゼロのチェックアウト パス

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ |
|--------------|--------------|--------------|--------------|
| Enabled | `payment/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| すべての品目を自動的に請求 | `payment/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 代金引換払い支払いパス

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ |
|--------------|--------------|--------------|--------------|
| Enabled | `payment/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手順 | `payment/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 銀行振込支払パス

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ |
|--------------|--------------|--------------|--------------|
| Enabled | `payment/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手順 | `payment/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 小切手または送金方法

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ |
|--------------|--------------|--------------|--------------|
| Enabled | `payment/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 小切手を支払先にする | `payment/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 発注書のパス

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ |
|--------------|--------------|--------------|--------------|
| Enabled | `payment/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 国際的な道筋

>[!INFO]
>
>使用可能なパスは、選択した [ マーチャント国 ](../reference/config-reference-sens.md#payment-sensitive-and-system-specific-paths) によって決まります。

| 名前 | 設定パス | Commerceのみ？ | 暗号化しますか？ |
|--------------|--------------|--------------|--------------|
| SFTP 資格情報 | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールされた取得 | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal マーチャントページスタイル | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| このソリューションを有効にする | `payment/wps_express/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールされた取得 | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal マーチャントページスタイル | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットカードの設定 | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 次の場合にトランザクションを拒否： | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールされた取得 | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_nz/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_nz/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_nz/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| すべての品目を自動的に請求 | `payment_nz/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_nz/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_nz/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_nz/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_nz/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_nz/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_nz/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_nz/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_nz/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手順 | `payment_nz/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_nz/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_nz/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_nz/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_nz/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_nz/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_nz/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_nz/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_nz/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手順 | `payment_nz/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_nz/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_nz/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_nz/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_nz/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_nz/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_nz/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_nz/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_nz/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 小切手を支払先にする | `payment_nz/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 小切手の送信先 | `payment_nz/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_nz/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_nz/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_nz/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_nz/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_nz/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_nz/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_nz/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_nz/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_nz/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_nz/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_nz/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_nz/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払いアクション | `payment_nz/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_nz/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_nz/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用可能な通貨 | `payment_nz/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デバッグ | `payment_nz/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットカードのタイプ | `payment_nz/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットカードの検証 | `payment_nz/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_nz/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_nz/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_nz/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_nz/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_nz/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_nz/cybersource/active` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 支払いアクション | `payment_nz/cybersource/payment_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `payment_nz/cybersource/title` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 新規注文ステータス | `payment_nz/cybersource/order_status` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| デバッグ | `payment_nz/cybersource/debug` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| クレジットカードのタイプ | `payment_nz/cybersource/cctypes` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 対象国からの支払い | `payment_nz/cybersource/allowspecific` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 特定国からの支払い | `payment_nz/cybersource/specificcountry` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 最小注文合計 | `payment_nz/cybersource/min_order_total` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 最大注文合計 | `payment_nz/cybersource/max_order_total` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 並べ替え順序 | `payment_nz/cybersource/sort_order` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| Enabled | `payment_nz/worldpay/active` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `payment_nz/worldpay/title` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 連絡先情報の編集を許可 | `payment_nz/worldpay/fix_contact` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 連絡先情報を非表示 | `payment_nz/worldpay/hide_contact` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 署名フィールド | `payment_nz/worldpay/signature_fields` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| デバッグ | `payment_nz/worldpay/debug` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| テストの支払アクション | `payment_nz/worldpay/test_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 支払いアクション | `payment_nz/worldpay/payment_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 対象国からの支払い | `payment_nz/worldpay/allowspecific` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 特定国からの支払い | `payment_nz/worldpay/specificcountry` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 注文ステータスを「Suspected Fraud for CVV」に設定 | `payment_nz/worldpay/cvv_fraud_case` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 郵便番号 AVS の注文ステータスを不正疑いに設定 | `payment_nz/worldpay/avs_fraud_case` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 並べ替え順序 | `payment_nz/worldpay/sort_order` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| Enabled | `payment_nz/eway/active` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 接続タイプ | `payment_nz/eway/connection_type` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `payment_nz/eway/title` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 支払いアクション | `payment_nz/eway/payment_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| デバッグ | `payment_nz/eway/debug` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| クレジットカードのタイプ | `payment_nz/eway/cctypes` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 対象国からの支払い | `payment_nz/eway/allowspecific` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 特定国からの支払い | `payment_nz/eway/specificcountry` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 並べ替え順序 | `payment_nz/eway/sort_order` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| スケジュールされた取得 | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal マーチャントページスタイル | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールされた取得 | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールされた取得 | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal マーチャントページスタイル | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_hk/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_hk/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_hk/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| すべての品目を自動的に請求 | `payment_hk/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_hk/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_hk/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_hk/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_hk/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_hk/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_hk/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_hk/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_hk/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手順 | `payment_hk/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_hk/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_hk/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_hk/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_hk/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_hk/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_hk/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_hk/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_hk/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手順 | `payment_hk/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_hk/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_hk/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_hk/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_hk/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_hk/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_hk/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_hk/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_hk/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_hk/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_hk/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_hk/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_hk/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_hk/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_hk/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_hk/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_hk/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_hk/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_hk/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_hk/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_hk/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払いアクション | `payment_hk/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_hk/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_hk/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用可能な通貨 | `payment_hk/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デバッグ | `payment_hk/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットカードのタイプ | `payment_hk/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットカードの検証 | `payment_hk/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_hk/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_hk/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_hk/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_hk/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_hk/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_hk/cybersource/active` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 支払いアクション | `payment_hk/cybersource/payment_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `payment_hk/cybersource/title` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 新規注文ステータス | `payment_hk/cybersource/order_status` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| デバッグ | `payment_hk/cybersource/debug` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| クレジットカードのタイプ | `payment_hk/cybersource/cctypes` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 対象国からの支払い | `payment_hk/cybersource/allowspecific` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 特定国からの支払い | `payment_hk/cybersource/specificcountry` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 最小注文合計 | `payment_hk/cybersource/min_order_total` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 最大注文合計 | `payment_hk/cybersource/max_order_total` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 並べ替え順序 | `payment_hk/cybersource/sort_order` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| Enabled | `payment_hk/worldpay/active` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `payment_hk/worldpay/title` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 連絡先情報の編集を許可 | `payment_hk/worldpay/fix_contact` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 連絡先情報を非表示 | `payment_hk/worldpay/hide_contact` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| デバッグ | `payment_hk/worldpay/debug` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| テストの支払アクション | `payment_hk/worldpay/test_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 支払いアクション | `payment_hk/worldpay/payment_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 対象国からの支払い | `payment_hk/worldpay/allowspecific` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 特定国からの支払い | `payment_hk/worldpay/specificcountry` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 注文ステータスを「Suspected Fraud for CVV」に設定 | `payment_hk/worldpay/cvv_fraud_case` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 郵便番号 AVS の注文ステータスを不正疑いに設定 | `payment_hk/worldpay/avs_fraud_case` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 並べ替え順序 | `payment_hk/worldpay/sort_order` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| Enabled | `payment_hk/eway/active` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 接続タイプ | `payment_hk/eway/connection_type` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `payment_hk/eway/title` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| サンドボックスモード | `payment_hk/eway/sandbox_flag` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 支払いアクション | `payment_hk/eway/payment_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| デバッグ | `payment_hk/eway/debug` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| クレジットカードのタイプ | `payment_hk/eway/cctypes` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 対象国からの支払い | `payment_hk/eway/allowspecific` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 特定国からの支払い | `payment_hk/eway/specificcountry` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 並べ替え順序 | `payment_hk/eway/sort_order` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| スケジュールされた取得 | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal マーチャントページスタイル | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールされた取得 | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールされた取得 | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal マーチャントページスタイル | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_es/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_es/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_es/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| すべての品目を自動的に請求 | `payment_es/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_es/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_es/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_es/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_es/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_es/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_es/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_es/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_es/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手順 | `payment_es/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_es/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_es/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_es/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_es/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_es/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_es/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_es/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_es/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手順 | `payment_es/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_es/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_es/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_es/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_es/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_es/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_es/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_es/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_es/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 小切手を支払先にする | `payment_es/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_es/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_es/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_es/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_es/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_es/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_es/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_es/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_es/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_es/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_es/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_es/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_es/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払いアクション | `payment_es/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_es/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_es/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用可能な通貨 | `payment_es/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デバッグ | `payment_es/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットカードのタイプ | `payment_es/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットカードの検証 | `payment_es/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_es/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_es/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_es/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_es/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_es/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_es/cybersource/active` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 支払いアクション | `payment_es/cybersource/payment_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `payment_es/cybersource/title` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| プロファイル ID | `payment_es/cybersource/profile_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) |
| 新規注文ステータス | `payment_es/cybersource/order_status` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| デバッグ | `payment_es/cybersource/debug` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| クレジットカードのタイプ | `payment_es/cybersource/cctypes` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 対象国からの支払い | `payment_es/cybersource/allowspecific` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 特定国からの支払い | `payment_es/cybersource/specificcountry` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 最小注文合計 | `payment_es/cybersource/min_order_total` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 最大注文合計 | `payment_es/cybersource/max_order_total` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 並べ替え順序 | `payment_es/cybersource/sort_order` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| Enabled | `payment_es/worldpay/active` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `payment_es/worldpay/title` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| インストール ID | `payment_es/worldpay/installation_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| リモート管理者インストール ID | `payment_es/worldpay/admin_installation_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 連絡先情報の編集を許可 | `payment_es/worldpay/fix_contact` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 連絡先情報を非表示 | `payment_es/worldpay/hide_contact` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 署名フィールド | `payment_es/worldpay/signature_fields` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| テストモード | `payment_es/worldpay/sandbox_flag` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| テストの支払アクション | `payment_es/worldpay/test_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 支払いアクション | `payment_es/worldpay/payment_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 対象国からの支払い | `payment_es/worldpay/allowspecific` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 特定国からの支払い | `payment_es/worldpay/specificcountry` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 注文ステータスを「Suspected Fraud for CVV」に設定 | `payment_es/worldpay/cvv_fraud_case` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 郵便番号 AVS の注文ステータスを不正疑いに設定 | `payment_es/worldpay/avs_fraud_case` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 並べ替え順序 | `payment_es/worldpay/sort_order` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| Enabled | `payment_es/eway/active` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 接続タイプ | `payment_es/eway/connection_type` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `payment_es/eway/title` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 支払いアクション | `payment_es/eway/payment_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| デバッグ | `payment_es/eway/debug` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| クレジットカードのタイプ | `payment_es/eway/cctypes` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 対象国からの支払い | `payment_es/eway/allowspecific` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 特定国からの支払い | `payment_es/eway/specificcountry` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 並べ替え順序 | `payment_es/eway/sort_order` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| スケジュールされた取得 | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal マーチャントページスタイル | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールされた取得 | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールされた取得 | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal マーチャントページスタイル | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_it/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_it/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_it/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| すべての品目を自動的に請求 | `payment_it/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_it/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_it/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_it/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_it/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_it/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_it/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_it/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_it/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手順 | `payment_it/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_it/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_it/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_it/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_it/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_it/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_it/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_it/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_it/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手順 | `payment_it/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_it/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_it/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_it/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_it/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_it/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_it/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_it/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_it/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_it/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_it/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_it/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_it/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_it/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_it/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_it/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_it/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_it/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_it/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_it/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_it/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払いアクション | `payment_it/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_it/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_it/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用可能な通貨 | `payment_it/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デバッグ | `payment_it/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットカードのタイプ | `payment_it/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットカードの検証 | `payment_it/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_it/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_it/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_it/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_it/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_it/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_it/cybersource/active` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 支払いアクション | `payment_it/cybersource/payment_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `payment_it/cybersource/title` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 新規注文ステータス | `payment_it/cybersource/order_status` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| デバッグ | `payment_it/cybersource/debug` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| クレジットカードのタイプ | `payment_it/cybersource/cctypes` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 対象国からの支払い | `payment_it/cybersource/allowspecific` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 特定国からの支払い | `payment_it/cybersource/specificcountry` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 最小注文合計 | `payment_it/cybersource/min_order_total` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 最大注文合計 | `payment_it/cybersource/max_order_total` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 並べ替え順序 | `payment_it/cybersource/sort_order` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| Enabled | `payment_it/worldpay/active` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `payment_it/worldpay/title` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 連絡先情報の編集を許可 | `payment_it/worldpay/fix_contact` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 連絡先情報を非表示 | `payment_it/worldpay/hide_contact` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 署名フィールド | `payment_it/worldpay/signature_fields` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| デバッグ | `payment_it/worldpay/debug` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| テストの支払アクション | `payment_it/worldpay/test_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 支払いアクション | `payment_it/worldpay/payment_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 対象国からの支払い | `payment_it/worldpay/allowspecific` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 特定国からの支払い | `payment_it/worldpay/specificcountry` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 注文ステータスを「Suspected Fraud for CVV」に設定 | `payment_it/worldpay/cvv_fraud_case` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 郵便番号 AVS の注文ステータスを不正疑いに設定 | `payment_it/worldpay/avs_fraud_case` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 並べ替え順序 | `payment_it/worldpay/sort_order` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| Enabled | `payment_it/eway/active` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 接続タイプ | `payment_it/eway/connection_type` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `payment_it/eway/title` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 支払いアクション | `payment_it/eway/payment_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| デバッグ | `payment_it/eway/debug` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| クレジットカードのタイプ | `payment_it/eway/cctypes` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 対象国からの支払い | `payment_it/eway/allowspecific` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 特定国からの支払い | `payment_it/eway/specificcountry` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 並べ替え順序 | `payment_it/eway/sort_order` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| スケジュールされた取得 | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal マーチャントページスタイル | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールされた取得 | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールされた取得 | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal マーチャントページスタイル | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_fr/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_fr/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_fr/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| すべての品目を自動的に請求 | `payment_fr/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_fr/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_fr/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_fr/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_fr/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_fr/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_fr/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_fr/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_fr/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手順 | `payment_fr/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_fr/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_fr/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_fr/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_fr/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_fr/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_fr/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_fr/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_fr/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手順 | `payment_fr/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_fr/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_fr/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_fr/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_fr/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_fr/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_fr/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_fr/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_fr/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_fr/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_fr/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_fr/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_fr/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_fr/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_fr/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_fr/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_fr/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_fr/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_fr/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_fr/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_fr/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払いアクション | `payment_fr/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_fr/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_fr/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用可能な通貨 | `payment_fr/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デバッグ | `payment_fr/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットカードのタイプ | `payment_fr/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットカードの検証 | `payment_fr/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_fr/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_fr/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_fr/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_fr/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_fr/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_fr/cybersource/active` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 支払いアクション | `payment_fr/cybersource/payment_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `payment_fr/cybersource/title` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 新規注文ステータス | `payment_fr/cybersource/order_status` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| デバッグ | `payment_fr/cybersource/debug` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| クレジットカードのタイプ | `payment_fr/cybersource/cctypes` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 対象国からの支払い | `payment_fr/cybersource/allowspecific` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 特定国からの支払い | `payment_fr/cybersource/specificcountry` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 最小注文合計 | `payment_fr/cybersource/min_order_total` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 最大注文合計 | `payment_fr/cybersource/max_order_total` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 並べ替え順序 | `payment_fr/cybersource/sort_order` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| Enabled | `payment_fr/worldpay/active` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `payment_fr/worldpay/title` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 連絡先情報の編集を許可 | `payment_fr/worldpay/fix_contact` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 連絡先情報を非表示 | `payment_fr/worldpay/hide_contact` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| デバッグ | `payment_fr/worldpay/debug` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| テストの支払アクション | `payment_fr/worldpay/test_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 支払いアクション | `payment_fr/worldpay/payment_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 対象国からの支払い | `payment_fr/worldpay/allowspecific` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 特定国からの支払い | `payment_fr/worldpay/specificcountry` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 注文ステータスを「Suspected Fraud for CVV」に設定 | `payment_fr/worldpay/cvv_fraud_case` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 郵便番号 AVS の注文ステータスを不正疑いに設定 | `payment_fr/worldpay/avs_fraud_case` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 並べ替え順序 | `payment_fr/worldpay/sort_order` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| Enabled | `payment_fr/eway/active` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 接続タイプ | `payment_fr/eway/connection_type` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `payment_fr/eway/title` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 支払いアクション | `payment_fr/eway/payment_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| デバッグ | `payment_fr/eway/debug` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| クレジットカードのタイプ | `payment_fr/eway/cctypes` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 対象国からの支払い | `payment_fr/eway/allowspecific` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 特定国からの支払い | `payment_fr/eway/specificcountry` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 並べ替え順序 | `payment_fr/eway/sort_order` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| スケジュールされた取得 | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal マーチャントページスタイル | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールされた取得 | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールされた取得 | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal マーチャントページスタイル | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_jp/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_jp/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_jp/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| すべての品目を自動的に請求 | `payment_jp/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_jp/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_jp/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_jp/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_jp/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_jp/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_jp/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_jp/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_jp/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手順 | `payment_jp/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_jp/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_jp/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_jp/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_jp/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_jp/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_jp/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_jp/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_jp/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手順 | `payment_jp/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_jp/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_jp/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_jp/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_jp/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_jp/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_jp/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_jp/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_jp/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_jp/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_jp/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_jp/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_jp/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_jp/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_jp/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_jp/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_jp/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_jp/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_jp/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_jp/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_jp/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払いアクション | `payment_jp/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_jp/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_jp/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用可能な通貨 | `payment_jp/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デバッグ | `payment_jp/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットカードのタイプ | `payment_jp/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットカードの検証 | `payment_jp/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_jp/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_jp/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_jp/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_jp/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_jp/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_jp/cybersource/active` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 支払いアクション | `payment_jp/cybersource/payment_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `payment_jp/cybersource/title` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| デバッグ | `payment_jp/cybersource/debug` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| クレジットカードのタイプ | `payment_jp/cybersource/cctypes` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 対象国からの支払い | `payment_jp/cybersource/allowspecific` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 特定国からの支払い | `payment_jp/cybersource/specificcountry` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 最小注文合計 | `payment_jp/cybersource/min_order_total` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 最大注文合計 | `payment_jp/cybersource/max_order_total` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 並べ替え順序 | `payment_jp/cybersource/sort_order` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| Enabled | `payment_jp/worldpay/active` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `payment_jp/worldpay/title` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 連絡先情報の編集を許可 | `payment_jp/worldpay/fix_contact` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 連絡先情報を非表示 | `payment_jp/worldpay/hide_contact` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| デバッグ | `payment_jp/worldpay/debug` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| テストの支払アクション | `payment_jp/worldpay/test_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 支払いアクション | `payment_jp/worldpay/payment_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 対象国からの支払い | `payment_jp/worldpay/allowspecific` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 特定国からの支払い | `payment_jp/worldpay/specificcountry` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 注文ステータスを「Suspected Fraud for CVV」に設定 | `payment_jp/worldpay/cvv_fraud_case` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 郵便番号 AVS の注文ステータスを不正疑いに設定 | `payment_jp/worldpay/avs_fraud_case` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 並べ替え順序 | `payment_jp/worldpay/sort_order` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| Enabled | `payment_jp/eway/active` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 接続タイプ | `payment_jp/eway/connection_type` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `payment_jp/eway/title` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 支払いアクション | `payment_jp/eway/payment_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| デバッグ | `payment_jp/eway/debug` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| クレジットカードのタイプ | `payment_jp/eway/cctypes` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 対象国からの支払い | `payment_jp/eway/allowspecific` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 特定国からの支払い | `payment_jp/eway/specificcountry` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 並べ替え順序 | `payment_jp/eway/sort_order` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| スケジュールされた取得 | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal マーチャントページスタイル | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールされた取得 | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールされた取得 | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal マーチャントページスタイル | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットカードの設定 | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 次の場合にトランザクションを拒否： | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールされた取得 | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_au/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_au/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_au/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| すべての品目を自動的に請求 | `payment_au/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_au/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_au/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_au/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_au/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_au/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_au/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_au/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_au/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手順 | `payment_au/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_au/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_au/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_au/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_au/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_au/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_au/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_au/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_au/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手順 | `payment_au/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_au/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_au/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_au/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_au/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_au/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_au/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_au/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_au/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 小切手を支払先にする | `payment_au/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 小切手の送信先 | `payment_au/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_au/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_au/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_au/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_au/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_au/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_au/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_au/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_au/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_au/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_au/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_au/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_au/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払いアクション | `payment_au/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_au/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_au/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用可能な通貨 | `payment_au/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デバッグ | `payment_au/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットカードのタイプ | `payment_au/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットカードの検証 | `payment_au/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_au/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_au/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_au/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_au/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_au/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_au/cybersource/active` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 支払いアクション | `payment_au/cybersource/payment_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `payment_au/cybersource/title` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| マーチャント ID | `payment_au/cybersource/merchant_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) |
| プロファイル ID | `payment_au/cybersource/profile_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) | ![ 暗号化 ](/help/assets/configuration/cloud-enc.png) |
| 新規注文ステータス | `payment_au/cybersource/order_status` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| デバッグ | `payment_au/cybersource/debug` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| クレジットカードのタイプ | `payment_au/cybersource/cctypes` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 対象国からの支払い | `payment_au/cybersource/allowspecific` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 特定国からの支払い | `payment_au/cybersource/specificcountry` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 最小注文合計 | `payment_au/cybersource/min_order_total` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 最大注文合計 | `payment_au/cybersource/max_order_total` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 並べ替え順序 | `payment_au/cybersource/sort_order` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| Enabled | `payment_au/worldpay/active` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `payment_au/worldpay/title` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| インストール ID | `payment_au/worldpay/installation_id` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 連絡先情報の編集を許可 | `payment_au/worldpay/fix_contact` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 連絡先情報を非表示 | `payment_au/worldpay/hide_contact` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 署名フィールド | `payment_au/worldpay/signature_fields` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| デバッグ | `payment_au/worldpay/debug` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| テストモード | `payment_au/worldpay/sandbox_flag` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| テストの支払アクション | `payment_au/worldpay/test_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 支払いアクション | `payment_au/worldpay/payment_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 対象国からの支払い | `payment_au/worldpay/allowspecific` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 特定国からの支払い | `payment_au/worldpay/specificcountry` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 注文ステータスを「Suspected Fraud for CVV」に設定 | `payment_au/worldpay/cvv_fraud_case` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 郵便番号 AVS の注文ステータスを不正疑いに設定 | `payment_au/worldpay/avs_fraud_case` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 並べ替え順序 | `payment_au/worldpay/sort_order` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| Enabled | `payment_au/eway/active` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 接続タイプ | `payment_au/eway/connection_type` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `payment_au/eway/title` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 支払いアクション | `payment_au/eway/payment_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| デバッグ | `payment_au/eway/debug` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| クレジットカードのタイプ | `payment_au/eway/cctypes` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 対象国からの支払い | `payment_au/eway/allowspecific` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 特定国からの支払い | `payment_au/eway/specificcountry` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 並べ替え順序 | `payment_au/eway/sort_order` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| スケジュールされた取得 | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal マーチャントページスタイル | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールされた取得 | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal マーチャントページスタイル | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| このソリューションを有効にする | `payment/paypal_payment_pro/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットカードの設定 | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 次の場合にトランザクションを拒否： | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールされた取得 | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットカードの設定 | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 次の場合にトランザクションを拒否： | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールされた取得 | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールされた取得 | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal マーチャントページスタイル | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_ca/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_ca/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_ca/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| すべての品目を自動的に請求 | `payment_ca/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_ca/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_ca/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_ca/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_ca/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_ca/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_ca/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_ca/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_ca/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手順 | `payment_ca/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_ca/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_ca/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_ca/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_ca/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_ca/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_ca/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_ca/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_ca/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手順 | `payment_ca/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_ca/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_ca/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_ca/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_ca/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_ca/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_ca/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_ca/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_ca/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_ca/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_ca/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_ca/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_ca/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_ca/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_ca/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_ca/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_ca/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_ca/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_ca/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_ca/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_ca/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払いアクション | `payment_ca/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_ca/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用可能な通貨 | `payment_ca/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デバッグ | `payment_ca/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットカードのタイプ | `payment_ca/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットカードの検証 | `payment_ca/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_ca/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_ca/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_ca/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_ca/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_ca/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_ca/cybersource/active` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 支払いアクション | `payment_ca/cybersource/payment_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `payment_ca/cybersource/title` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| デバッグ | `payment_ca/cybersource/debug` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| クレジットカードのタイプ | `payment_ca/cybersource/cctypes` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 対象国からの支払い | `payment_ca/cybersource/allowspecific` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 特定国からの支払い | `payment_ca/cybersource/specificcountry` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 最小注文合計 | `payment_ca/cybersource/min_order_total` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 最大注文合計 | `payment_ca/cybersource/max_order_total` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 並べ替え順序 | `payment_ca/cybersource/sort_order` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| Enabled | `payment_ca/worldpay/active` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `payment_ca/worldpay/title` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 連絡先情報の編集を許可 | `payment_ca/worldpay/fix_contact` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 連絡先情報を非表示 | `payment_ca/worldpay/hide_contact` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 署名フィールド | `payment_ca/worldpay/signature_fields` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| デバッグ | `payment_ca/worldpay/debug` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| テストの支払アクション | `payment_ca/worldpay/test_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 支払いアクション | `payment_ca/worldpay/payment_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 対象国からの支払い | `payment_ca/worldpay/allowspecific` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 特定国からの支払い | `payment_ca/worldpay/specificcountry` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 注文ステータスを「Suspected Fraud for CVV」に設定 | `payment_ca/worldpay/cvv_fraud_case` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 郵便番号 AVS の注文ステータスを不正疑いに設定 | `payment_ca/worldpay/avs_fraud_case` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 並べ替え順序 | `payment_ca/worldpay/sort_order` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| Enabled | `payment_ca/eway/active` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 接続タイプ | `payment_ca/eway/connection_type` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `payment_ca/eway/title` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 支払いアクション | `payment_ca/eway/payment_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| デバッグ | `payment_ca/eway/debug` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| クレジットカードのタイプ | `payment_ca/eway/cctypes` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 対象国からの支払い | `payment_ca/eway/allowspecific` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 特定国からの支払い | `payment_ca/eway/specificcountry` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 並べ替え順序 | `payment_ca/eway/sort_order` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| スケジュールされた取得 | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal マーチャントページスタイル | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールされた取得 | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal マーチャントページスタイル | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_other/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_other/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_other/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| すべての品目を自動的に請求 | `payment_other/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_other/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_other/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_other/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_other/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_other/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_other/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_other/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_other/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手順 | `payment_other/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_other/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_other/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_other/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_other/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_other/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_other/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_other/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_other/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手順 | `payment_other/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_other/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_other/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_other/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_other/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_other/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_other/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_other/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_other/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_other/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_other/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_other/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_other/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_other/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_other/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_other/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_other/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_other/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_other/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_other/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_other/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払いアクション | `payment_other/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_other/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用可能な通貨 | `payment_other/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デバッグ | `payment_other/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顧客に E メール通知 | `payment_other/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットカードのタイプ | `payment_other/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットカードの検証 | `payment_other/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_other/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_other/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_other/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_other/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_other/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_other/cybersource/active` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 支払いアクション | `payment_other/cybersource/payment_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `payment_other/cybersource/title` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| デバッグ | `payment_other/cybersource/debug` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| クレジットカードのタイプ | `payment_other/cybersource/cctypes` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 対象国からの支払い | `payment_other/cybersource/allowspecific` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 特定国からの支払い | `payment_other/cybersource/specificcountry` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 最小注文合計 | `payment_other/cybersource/min_order_total` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 最大注文合計 | `payment_other/cybersource/max_order_total` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 並べ替え順序 | `payment_other/cybersource/sort_order` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| Enabled | `payment_other/worldpay/active` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `payment_other/worldpay/title` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 連絡先情報の編集を許可 | `payment_other/worldpay/fix_contact` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 連絡先情報を非表示 | `payment_other/worldpay/hide_contact` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 署名フィールド | `payment_other/worldpay/signature_fields` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| デバッグ | `payment_other/worldpay/debug` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| テストの支払アクション | `payment_other/worldpay/test_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 支払いアクション | `payment_other/worldpay/payment_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 対象国からの支払い | `payment_other/worldpay/allowspecific` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 特定国からの支払い | `payment_other/worldpay/specificcountry` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 注文ステータスを「Suspected Fraud for CVV」に設定 | `payment_other/worldpay/cvv_fraud_case` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 郵便番号 AVS の注文ステータスを不正疑いに設定 | `payment_other/worldpay/avs_fraud_case` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 並べ替え順序 | `payment_other/worldpay/sort_order` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| Enabled | `payment_other/eway/active` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 接続タイプ | `payment_other/eway/connection_type` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `payment_other/eway/title` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 支払いアクション | `payment_other/eway/payment_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| デバッグ | `payment_other/eway/debug` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| クレジットカードのタイプ | `payment_other/eway/cctypes` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 対象国からの支払い | `payment_other/eway/allowspecific` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 特定国からの支払い | `payment_other/eway/specificcountry` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 並べ替え順序 | `payment_other/eway/sort_order` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| スケジュールされた取得 | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal マーチャントページスタイル | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_de/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_de/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_de/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_de/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_de/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_de/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_de/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_de/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_de/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_de/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_de/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_de/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_de/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手順 | `payment_de/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_de/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_de/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_de/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_de/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_de/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_de/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_de/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_de/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手順 | `payment_de/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_de/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_de/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_de/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_de/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_de/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_de/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| すべての品目を自動的に請求 | `payment_de/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_de/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_de/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_de/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_de/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_de/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_de/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_de/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_de/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_de/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_de/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_de/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_de/cybersource/active` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 支払いアクション | `payment_de/cybersource/payment_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `payment_de/cybersource/title` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 新規注文ステータス | `payment_de/cybersource/order_status` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| デバッグ | `payment_de/cybersource/debug` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| クレジットカードのタイプ | `payment_de/cybersource/cctypes` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 対象国からの支払い | `payment_de/cybersource/allowspecific` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 特定国からの支払い | `payment_de/cybersource/specificcountry` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 最小注文合計 | `payment_de/cybersource/min_order_total` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 最大注文合計 | `payment_de/cybersource/max_order_total` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 並べ替え順序 | `payment_de/cybersource/sort_order` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| Enabled | `payment_de/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払いアクション | `payment_de/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_de/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_de/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用可能な通貨 | `payment_de/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デバッグ | `payment_de/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットカードのタイプ | `payment_de/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットカードの検証 | `payment_de/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_de/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_de/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_de/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_de/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_de/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_de/worldpay/active` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `payment_de/worldpay/title` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 連絡先情報の編集を許可 | `payment_de/worldpay/fix_contact` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 連絡先情報を非表示 | `payment_de/worldpay/hide_contact` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 署名フィールド | `payment_de/worldpay/signature_fields` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| テストモード | `payment_de/worldpay/sandbox_flag` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| テストの支払アクション | `payment_de/worldpay/test_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 支払いアクション | `payment_de/worldpay/payment_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 対象国からの支払い | `payment_de/worldpay/allowspecific` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 特定国からの支払い | `payment_de/worldpay/specificcountry` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 注文ステータスを「Suspected Fraud for CVV」に設定 | `payment_de/worldpay/cvv_fraud_case` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 郵便番号 AVS の注文ステータスを不正疑いに設定 | `payment_de/worldpay/avs_fraud_case` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 並べ替え順序 | `payment_de/worldpay/sort_order` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| Enabled | `payment_de/eway/active` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 接続タイプ | `payment_de/eway/connection_type` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `payment_de/eway/title` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 支払いアクション | `payment_de/eway/payment_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| デバッグ | `payment_de/eway/debug` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| クレジットカードのタイプ | `payment_de/eway/cctypes` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 対象国からの支払い | `payment_de/eway/allowspecific` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 特定国からの支払い | `payment_de/eway/specificcountry` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 並べ替え順序 | `payment_de/eway/sort_order` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| スケジュールされた取得 | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal マーチャントページスタイル | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールされた取得 | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal マーチャントページスタイル | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールされた取得 | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal マーチャントページスタイル | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_gb/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_gb/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_gb/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_gb/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_gb/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 小切手を支払先にする | `payment_gb/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_gb/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_gb/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_gb/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_gb/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_gb/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_gb/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_gb/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_gb/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手順 | `payment_gb/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_gb/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_gb/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_gb/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_gb/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_gb/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_gb/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_gb/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_gb/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手順 | `payment_gb/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_gb/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_gb/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_gb/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_gb/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_gb/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_gb/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| すべての品目を自動的に請求 | `payment_gb/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_gb/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_gb/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_gb/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_gb/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_gb/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_gb/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_gb/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_gb/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_gb/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_gb/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_gb/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_gb/cybersource/active` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 支払いアクション | `payment_gb/cybersource/payment_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `payment_gb/cybersource/title` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 新規注文ステータス | `payment_gb/cybersource/order_status` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| デバッグ | `payment_gb/cybersource/debug` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| クレジットカードのタイプ | `payment_gb/cybersource/cctypes` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 対象国からの支払い | `payment_gb/cybersource/allowspecific` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 特定国からの支払い | `payment_gb/cybersource/specificcountry` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 最小注文合計 | `payment_gb/cybersource/min_order_total` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 最大注文合計 | `payment_gb/cybersource/max_order_total` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 並べ替え順序 | `payment_gb/cybersource/sort_order` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| Enabled | `payment_gb/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払いアクション | `payment_gb/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_gb/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_gb/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用可能な通貨 | `payment_gb/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デバッグ | `payment_gb/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットカードのタイプ | `payment_gb/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットカードの検証 | `payment_gb/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_gb/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_gb/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_gb/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_gb/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_gb/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_gb/worldpay/active` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `payment_gb/worldpay/title` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| トランザクションの MD5 シークレット | `payment_gb/worldpay/md5_secret` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 連絡先情報の編集を許可 | `payment_gb/worldpay/fix_contact` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 連絡先情報を非表示 | `payment_gb/worldpay/hide_contact` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 署名フィールド | `payment_gb/worldpay/signature_fields` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| デバッグ | `payment_gb/worldpay/debug` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| テストの支払アクション | `payment_gb/worldpay/test_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 支払いアクション | `payment_gb/worldpay/payment_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 対象国からの支払い | `payment_gb/worldpay/allowspecific` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 特定国からの支払い | `payment_gb/worldpay/specificcountry` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 注文ステータスを「Suspected Fraud for CVV」に設定 | `payment_gb/worldpay/cvv_fraud_case` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 郵便番号 AVS の注文ステータスを不正疑いに設定 | `payment_gb/worldpay/avs_fraud_case` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 並べ替え順序 | `payment_gb/worldpay/sort_order` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| Enabled | `payment_gb/eway/active` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 接続タイプ | `payment_gb/eway/connection_type` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `payment_gb/eway/title` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 支払いアクション | `payment_gb/eway/payment_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| デバッグ | `payment_gb/eway/debug` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| クレジットカードのタイプ | `payment_gb/eway/cctypes` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 対象国からの支払い | `payment_gb/eway/allowspecific` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 特定国からの支払い | `payment_gb/eway/specificcountry` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 並べ替え順序 | `payment_gb/eway/sort_order` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| スケジュールされた取得 | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal マーチャントページスタイル | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールされた取得 | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal マーチャントページスタイル | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットカードの設定 | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 次の場合にトランザクションを拒否： | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールされた取得 | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal マーチャントページスタイル | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal クレジットを有効にする | `payment/wps_express_bml/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールされた取得 | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal マーチャントページスタイル | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットカードの設定 | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 次の場合にトランザクションを拒否： | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールされた取得 | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal マーチャントページスタイル | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| スケジュールされた取得 | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal マーチャントページスタイル | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_us/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_us/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_us/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| すべての品目を自動的に請求 | `payment_us/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_us/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_us/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_us/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_us/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_us/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_us/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_us/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_us/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手順 | `payment_us/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_us/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_us/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_us/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_us/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_us/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_us/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_us/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_us/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手順 | `payment_us/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_us/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_us/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_us/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_us/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_us/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_us/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_us/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_us/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 小切手を支払先にする | `payment_us/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_us/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_us/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_us/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_us/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_us/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_us/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_us/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_us/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_us/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_us/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_us/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_us/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払いアクション | `payment_us/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `payment_us/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文ステータス | `payment_us/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 使用可能な通貨 | `payment_us/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デバッグ | `payment_us/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットカードのタイプ | `payment_us/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットカードの検証 | `payment_us/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 対象国からの支払い | `payment_us/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定国からの支払い | `payment_us/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文合計 | `payment_us/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大注文合計 | `payment_us/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `payment_us/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `payment_us/cybersource/active` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 支払いアクション | `payment_us/cybersource/payment_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `payment_us/cybersource/title` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 新規注文ステータス | `payment_us/cybersource/order_status` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| デバッグ | `payment_us/cybersource/debug` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| クレジットカードのタイプ | `payment_us/cybersource/cctypes` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 対象国からの支払い | `payment_us/cybersource/allowspecific` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 特定国からの支払い | `payment_us/cybersource/specificcountry` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 最小注文合計 | `payment_us/cybersource/min_order_total` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 最大注文合計 | `payment_us/cybersource/max_order_total` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 並べ替え順序 | `payment_us/cybersource/sort_order` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| Enabled | `payment_us/worldpay/active` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `payment_us/worldpay/title` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 連絡先情報の編集を許可 | `payment_us/worldpay/fix_contact` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 連絡先情報を非表示 | `payment_us/worldpay/hide_contact` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 署名フィールド | `payment_us/worldpay/signature_fields` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| デバッグ | `payment_us/worldpay/debug` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| テストの支払アクション | `payment_us/worldpay/test_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 支払いアクション | `payment_us/worldpay/payment_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 対象国からの支払い | `payment_us/worldpay/allowspecific` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 特定国からの支払い | `payment_us/worldpay/specificcountry` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 注文ステータスを「Suspected Fraud for CVV」に設定 | `payment_us/worldpay/cvv_fraud_case` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 郵便番号 AVS の注文ステータスを不正疑いに設定 | `payment_us/worldpay/avs_fraud_case` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 並べ替え順序 | `payment_us/worldpay/sort_order` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| Enabled | `payment_us/eway/active` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 接続タイプ | `payment_us/eway/connection_type` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `payment_us/eway/title` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 支払いアクション | `payment_us/eway/payment_action` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| デバッグ | `payment_us/eway/debug` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| クレジットカードのタイプ | `payment_us/eway/cctypes` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 対象国からの支払い | `payment_us/eway/allowspecific` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 特定国からの支払い | `payment_us/eway/specificcountry` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 並べ替え順序 | `payment_us/eway/sort_order` | |

{style="table-layout:auto"}
