---
title: 支払設定パスの参照
description: Adobe Commerce Adminの支払い設定パスとメソッド値について説明します。 PayPal、クレジットカード、支払いゲートウェイの設定オプションをご確認ください。
feature: Configuration, Payments
exl-id: f3e356aa-7262-4d99-9ed4-d77cbd93708c
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '5833'
ht-degree: 0%

---

# 支払設定パスの参照

これらの設定値は、**ストア**/設定/**構成**/**販売**/**支払い方法**&#x200B;の管理者で使用できます。

[`magento app:config:dump` コマンド ](../cli/export-configuration.md)は、これらの値をソース コントロールにある共有設定ファイル `app/etc/config.php`に書き込みます。 任意の構成設定を上書きする方法や、機密設定を設定する方法については、[環境変数を使用して構成設定を上書きする](override-config-settings.md#environment-variables)を参照してください。 このトピックでは、_Allt_&#x200B;に[機密値とシステム固有の値](config-reference-sens.md)が一覧表示されます。

設定は支払い方法によってさらに整理されています。

## PayPalのパス

| 名前 | 設定パス | Commerce版をサポートしていますか？ |
|--------------|--------------|--------------|
| このソリューションを有効にする | `payment/payflowpro/active` | すべて |
| インコンテクストなチェックアウトエクスペリエンスの実現 | `payment/paypal_express/in_context` | すべて |
| PayPal クレジットを有効にする | `payment/payflow_express_bml/active` | すべて |
| PayPal クレジットを有効にする | `payment/paypal_express_bml/active` | すべて |
| 表示 | `payment/paypal_express_bml/homepage_display` | すべて |
| 位置 | `payment/paypal_express_bml/homepage_position` | すべて |
| サイズ | `payment/paypal_express_bml/homepage_size` | すべて |
| 表示 | `payment/paypal_express_bml/categorypage_display` | すべて |
| 位置 | `payment/paypal_express_bml/categorypage_position` | すべて |
| サイズ | `payment/paypal_express_bml/categorypage_size` | すべて |
| 表示 | `payment/paypal_express_bml/productpage_display` | すべて |
| 位置 | `payment/paypal_express_bml/productpage_position` | すべて |
| サイズ | `payment/paypal_express_bml/productpage_size` | すべて |
| 表示 | `payment/paypal_express_bml/checkout_display` | すべて |
| 位置 | `payment/paypal_express_bml/checkout_position` | すべて |
| サイズ | `payment/paypal_express_bml/checkout_size` | すべて |
| 商品詳細ページに表示 | `payment/payflow_express/visible_on_product` | すべて |
| ショッピングカートに表示 | `payment/payflow_express/visible_on_cart` | すべて |
| 支払い対象： | `payment/payflow_express/allowspecific` | すべて |
| から適用される国の支払い | `payment/payflow_express/specificcountry` | すべて |
| SSL検証を有効にする | `payment/payflow_express/verify_peer` | すべて |
| カート品目の転送 | `payment/payflow_express/line_items_enabled` | すべて |
| 注文のレビュー手順をスキップ | `payment/paypal_express/skip_order_review_step` | すべて |
| カート品目の転送 | `payment/paypal_express/line_items_enabled` | すべて |
| 配送オプションの転送 | `payment/paypal_express/transfer_shipping_options` | すべて |
| ショートカットボタンの味 | `paypal/wpp/button_flavor` | すべて |
| PayPal ゲストチェックアウトを有効にする | `payment/paypal_express/solution_type` | すべて |
| お客様の請求先住所を要求 | `payment/paypal_express/require_billing_address` | すべて |
| 請求契約書の登録 | `payment/paypal_express/allow_ba_signup` | すべて |
| 有効 | `payment/paypal_billing_agreement/active` | すべて |
| タイトル | `payment/paypal_billing_agreement/title` | すべて |
| ソート順序 | `payment/paypal_billing_agreement/sort_order` | すべて |
| 支払いアクション | `payment/paypal_billing_agreement/payment_action` | すべて |
| 支払い対象： | `payment/paypal_billing_agreement/allowspecific` | すべて |
| から適用される国の支払い | `payment/paypal_billing_agreement/specificcountry` | すべて |
| SSL検証を有効にする | `payment/paypal_billing_agreement/verify_peer` | すべて |
| カート品目の転送 | `payment/paypal_billing_agreement/line_items_enabled` | すべて |
| 請求契約書で許可ウィザード | `payment/paypal_billing_agreement/allow_billing_agreement_wizard` | すべて |
| 自動取得を有効化 | `paypal/fetch_reports/active` | すべて |
| スケジュール | `paypal/fetch_reports/schedule` | すべて |
| 時間帯 | `paypal/fetch_reports/time` | すべて |
| PayPal製品ロゴ | `paypal/style/logo` | すべて |
| ページスタイル | `paypal/style/page_style` | すべて |
| ヘッダー画像URL | `paypal/style/paypal_hdrimg` | すべて |
| ヘッダーの背景色 | `paypal/style/paypal_hdrbackcolor` | すべて |
| ヘッダーの境界線の色 | `paypal/style/paypal_hdrbordercolor` | すべて |
| ページの背景色 | `paypal/style/paypal_payflowcolor` | すべて |
| このソリューションを有効にする | `payment/paypal_express/active` | すべて |
| 並べ替えPayPal クレジット | `payment/paypal_express_bml/sort_order` | すべて |
| タイトル | `payment/paypal_express/title` | すべて |
| ソート順序 | `payment/paypal_express/sort_order` | すべて |
| 支払いアクション | `payment/paypal_express/payment_action` | すべて |
| 商品詳細ページに表示 | `payment/paypal_express/visible_on_product` | すべて |
| 承認期間（日数） | `payment/paypal_express/authorization_hoAllr_period` | すべて |
| 注文有効期間（日数） | `payment/paypal_express/order_valid_period` | すべて |
| 子認証の数 | `payment/paypal_express/child_authorization_number` | すべて |
| ショッピングカートに表示 | `payment/paypal_express/visible_on_cart` | すべて |
| 子認証の数 | `payment/paypal_express/child_authorization_number` | すべて |
| 支払い対象： | `payment/paypal_express/allowspecific` | すべて |
| 子認証の数 | `payment/paypal_express/child_authorization_number` | すべて |
| から適用される国の支払い | `payment/paypal_express/specificcountry` | すべて |
| 子認証の数 | `payment/paypal_express/child_authorization_number` | すべて |
| SSL検証を有効にする | `payment/paypal_express/verify_peer` | すべて |
| 子認証の数 | `payment/paypal_express/child_authorization_number` | すべて |
| スケジュール済み取得 | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | すべて |
| PayPal加盟店ページのスタイル | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | すべて |

{style="table-layout:auto"}

## PayPal Payments Pro

| 名前 | 設定パス | Commerce版をサポートしていますか？ |
|--------------|--------------|--------------|
| API認証方法 | `paypal/wpp/api_authentication` | すべて |
| APIはプロキシを使用します | `paypal/wpp/use_proxy` | すべて |
| スケジュール済み取得 | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | すべて |
| スケジュール済み取得 | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | すべて |

{style="table-layout:auto"}

## Payments Pro Hosted Solution （英国）

これらのオプションは、英国を[ マーチャント国](../reference/config-reference-sens.md#payment-sensitive-and-system-specific-paths)として選択した場合にのみ使用できます。

| 名前 | 設定パス | Commerce版をサポートしていますか？ |
|--------------|--------------|--------------|
| このソリューションを有効にする | `payment/hosted_pro/active` | すべて |
| タイトル | `payment/hosted_pro/title` | すべて |
| ソート順序 | `payment/hosted_pro/sort_order` | すべて |
| 支払いアクション | `payment/hosted_pro/payment_action` | すべて |
| 支払い情報ステップでのExpress Checkoutの表示 | `payment/hosted_pro/display_ec` | すべて |
| 支払い対象： | `payment/hosted_pro/allowspecific` | すべて |
| から適用される国の支払い | `payment/hosted_pro/specificcountry` | すべて |
| SSL検証を有効にする | `payment/hosted_pro/verify_peer` | すべて |

{style="table-layout:auto"}

## PayPal Payflow Pro

| 名前 | 設定パス | Commerce版をサポートしていますか？ |
|--------------|--------------|--------------|
| Vault有効 | `payment/payflowpro_cc_vault/active` | すべて |
| タイトル | `payment/payflowpro/title` | すべて |
| 保管タイトル | `payment/payflowpro_cc_vault/title` | すべて |
| ソート順序 | `payment/payflowpro/sort_order` | すべて |
| 支払いアクション | `payment/payflowpro/payment_action` | すべて |
| 許可されているクレジットカードの種類 | `payment/payflowpro/cctypes` | すべて |
| 支払い対象： | `payment/payflowpro/allowspecific` | すべて |
| から適用される国の支払い | `payment/payflowpro/specificcountry` | すべて |
| SSL検証を有効にする | `payment/payflowpro/verify_peer` | すべて |
| CVV エントリの要求 | `payment/payflowpro/useccv` | すべて |
| 次の場合にトランザクションを拒否： | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | すべて |
| AVS Streetが一致しない | `payment/payflowpro/avs_street` | すべて |
| AVS ZipがAlltと一致しない | `payment/payflowpro/avs_zip` | すべて |
| 国際AVS指標はAllt一致しません | `payment/payflowpro/avs_international` | すべて |
| カードセキュリティコードが一致しない | `payment/payflowpro/avs_security_code` | すべて |
| ベンダー | `payment/payflowpro/vendor` | すべて |
| プロキシを使用 | `payment/payflowpro/use_proxy` | すべて |
| タイトル | `payment/payflow_express/title` | すべて |
| ソート順序 | `payment/payflow_express/sort_order` | すべて |
| 支払いアクション | `payment/payflow_express/payment_action` | すべて |
| スケジュール済み取得 | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | すべて |
| PayPal加盟店ページのスタイル | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | すべて |
| パートナー | `payment/payflow_advanced/partner` | すべて |
| ベンダー | `payment/payflow_advanced/vendor` | すべて |
| プロキシを使用 | `payment/payflow_advanced/use_proxy` | すべて |
| このソリューションを有効にする | `payment/payflow_advanced/active` | すべて |
| タイトル | `payment/payflow_advanced/title` | すべて |
| ソート順序 | `payment/payflow_advanced/sort_order` | すべて |
| 支払いアクション | `payment/payflow_advanced/payment_action` | すべて |
| 支払い対象： | `payment/payflow_advanced/allowspecific` | すべて |
| から適用される国の支払い | `payment/payflow_advanced/specificcountry` | すべて |
| SSL検証を有効にする | `payment/payflow_advanced/verify_peer` | すべて |
| CVV エントリは編集可能です | `payment/payflow_advanced/csc_editable` | すべて |
| CVV エントリの要求 | `payment/payflow_advanced/csc_required` | すべて |
| メール送信の確認 | `payment/payflow_advanced/email_confirmation` | すべて |

{style="table-layout:auto"}

## PayPal Payflow Link

| 名前 | 設定パス | Commerce版をサポートしていますか？ |
|--------------|--------------|--------------|
| パートナー | `payment/payflow_link/partner` | すべて |
| ベンダー | `payment/payflow_link/vendor` | すべて |
| ペイフローリンクの有効化 | `payment/payflow_link/active` | すべて |
| Express チェックアウトを有効にする | `payment/payflow_express/active` | すべて |
| 並べ替えPayPal クレジット | `payment/payflow_express_bml/sort_order` | すべて |
| 支払い対象： | `payment/payflow_link/allowspecific` | すべて |
| から適用される国の支払い | `payment/payflow_link/specificcountry` | すべて |
| SSL検証を有効にする | `payment/payflow_link/verify_peer` | すべて |
| CVV エントリは編集可能です | `payment/payflow_link/csc_editable` | すべて |
| CVV エントリの要求 | `payment/payflow_link/csc_required` | すべて |
| メール送信の確認 | `payment/payflow_link/email_confirmation` | すべて |
| スケジュール済み取得 | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | すべて |
| タイトル | `payment/payflow_link/title` | すべて |
| ソート順序 | `payment/payflow_link/sort_order` | すべて |
| 支払いアクション | `payment/payflow_link/payment_action` | すべて |

{style="table-layout:auto"}

## 小計チェックアウトパスをゼロにする

| 名前 | 設定パス | Commerce版をサポートしていますか？ |
|--------------|--------------|--------------|
| 有効 | `payment/free/active` | すべて |
| タイトル | `payment/free/title` | すべて |
| 新規注文ステータス | `payment/free/order_status` | すべて |
| すべての項目に自動請求書を発行する | `payment/free/payment_action` | すべて |
| 対象国からの支払い | `payment/free/allowspecific` | すべて |
| 特定国からの支払い | `payment/free/specificcountry` | すべて |
| ソート順序 | `payment/free/sort_order` | すべて |

{style="table-layout:auto"}

## 代金引換の支払い方法

| 名前 | 設定パス | Commerce版をサポートしていますか？ |
|--------------|--------------|--------------|
| 有効 | `payment/cashondelivery/active` | すべて |
| タイトル | `payment/cashondelivery/title` | すべて |
| 新規注文ステータス | `payment/cashondelivery/order_status` | すべて |
| 対象国からの支払い | `payment/cashondelivery/allowspecific` | すべて |
| 特定国からの支払い | `payment/cashondelivery/specificcountry` | すべて |
| 手順 | `payment/cashondelivery/instructions` | すべて |
| 最低注文合計 | `payment/cashondelivery/min_order_total` | すべて |
| 最大注文合計 | `payment/cashondelivery/max_order_total` | すべて |
| ソート順序 | `payment/cashondelivery/sort_order` | すべて |

{style="table-layout:auto"}

## 銀行振込の支払い方法

| 名前 | 設定パス | Commerce版をサポートしていますか？ |
|--------------|--------------|--------------|
| 有効 | `payment/banktransfer/active` | すべて |
| タイトル | `payment/banktransfer/title` | すべて |
| 新規注文ステータス | `payment/banktransfer/order_status` | すべて |
| 対象国からの支払い | `payment/banktransfer/allowspecific` | すべて |
| 特定国からの支払い | `payment/banktransfer/specificcountry` | すべて |
| 手順 | `payment/banktransfer/instructions` | すべて |
| 最低注文合計 | `payment/banktransfer/min_order_total` | すべて |
| 最大注文合計 | `payment/banktransfer/max_order_total` | すべて |
| ソート順序 | `payment/banktransfer/sort_order` | すべて |

{style="table-layout:auto"}

## 小切手またはマネーオーダーのパス

| 名前 | 設定パス | Commerce版をサポートしていますか？ |
|--------------|--------------|--------------|
| 有効 | `payment/checkmo/active` | すべて |
| タイトル | `payment/checkmo/title` | すべて |
| 新規注文ステータス | `payment/checkmo/order_status` | すべて |
| 対象国からの支払い | `payment/checkmo/allowspecific` | すべて |
| 特定国からの支払い | `payment/checkmo/specificcountry` | すべて |
| 小切手の支払先 | `payment/checkmo/payable_to` | すべて |
| 最低注文合計 | `payment/checkmo/min_order_total` | すべて |
| 最大注文合計 | `payment/checkmo/max_order_total` | すべて |
| ソート順序 | `payment/checkmo/sort_order` | すべて |

{style="table-layout:auto"}

## 発注パス

| 名前 | 設定パス | Commerce版をサポートしていますか？ |
|--------------|--------------|--------------|
| 有効 | `payment/purchaseorder/active` | すべて |
| タイトル | `payment/purchaseorder/title` | すべて |
| 新規注文ステータス | `payment/purchaseorder/order_status` | すべて |
| 対象国からの支払い | `payment/purchaseorder/allowspecific` | すべて |
| 特定国からの支払い | `payment/purchaseorder/specificcountry` | すべて |
| 最低注文合計 | `payment/purchaseorder/min_order_total` | すべて |
| 最大注文合計 | `payment/purchaseorder/max_order_total` | すべて |
| ソート順序 | `payment/purchaseorder/sort_order` | すべて |

{style="table-layout:auto"}

## 国際パス

>[!INFO]
>
>使用可能なパスは、[加盟店の国](../reference/config-reference-sens.md#payment-sensitive-and-system-specific-paths)の選択によって決まります。

| 名前 | 設定パス | Commerce版をサポートしていますか？ |
|--------------|--------------|--------------|
| SFTP資格情報 | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | すべて |
| スケジュール済み取得 | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | すべて |
| PayPal加盟店ページのスタイル | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | すべて |
| このソリューションを有効にする | `payment/wps_express/active` | すべて |
| スケジュール済み取得 | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | すべて |
| PayPal加盟店ページのスタイル | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | すべて |
| クレジットカード設定 | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/heading_cc` | すべて |
| 次の場合にトランザクションを拒否： | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | すべて |
| スケジュール済み取得 | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | すべて |
| 有効 | `payment_nz/free/active` | すべて |
| タイトル | `payment_nz/free/title` | すべて |
| 新規注文ステータス | `payment_nz/free/order_status` | すべて |
| すべての項目に自動請求書を発行する | `payment_nz/free/payment_action` | すべて |
| 対象国からの支払い | `payment_nz/free/allowspecific` | すべて |
| 特定国からの支払い | `payment_nz/free/specificcountry` | すべて |
| ソート順序 | `payment_nz/free/sort_order` | すべて |
| 有効 | `payment_nz/cashondelivery/active` | すべて |
| タイトル | `payment_nz/cashondelivery/title` | すべて |
| 新規注文ステータス | `payment_nz/cashondelivery/order_status` | すべて |
| 対象国からの支払い | `payment_nz/cashondelivery/allowspecific` | すべて |
| 特定国からの支払い | `payment_nz/cashondelivery/specificcountry` | すべて |
| 手順 | `payment_nz/cashondelivery/instructions` | すべて |
| 最低注文合計 | `payment_nz/cashondelivery/min_order_total` | すべて |
| 最大注文合計 | `payment_nz/cashondelivery/max_order_total` | すべて |
| ソート順序 | `payment_nz/cashondelivery/sort_order` | すべて |
| 有効 | `payment_nz/banktransfer/active` | すべて |
| タイトル | `payment_nz/banktransfer/title` | すべて |
| 新規注文ステータス | `payment_nz/banktransfer/order_status` | すべて |
| 対象国からの支払い | `payment_nz/banktransfer/allowspecific` | すべて |
| 特定国からの支払い | `payment_nz/banktransfer/specificcountry` | すべて |
| 手順 | `payment_nz/banktransfer/instructions` | すべて |
| 最低注文合計 | `payment_nz/banktransfer/min_order_total` | すべて |
| 最大注文合計 | `payment_nz/banktransfer/max_order_total` | すべて |
| ソート順序 | `payment_nz/banktransfer/sort_order` | すべて |
| 有効 | `payment_nz/checkmo/active` | すべて |
| タイトル | `payment_nz/checkmo/title` | すべて |
| 新規注文ステータス | `payment_nz/checkmo/order_status` | すべて |
| 対象国からの支払い | `payment_nz/checkmo/allowspecific` | すべて |
| 特定国からの支払い | `payment_nz/checkmo/specificcountry` | すべて |
| 小切手の支払先 | `payment_nz/checkmo/payable_to` | すべて |
| 小切手の送信先 | `payment_nz/checkmo/mailing_address` | すべて |
| 最低注文合計 | `payment_nz/checkmo/min_order_total` | すべて |
| 最大注文合計 | `payment_nz/checkmo/max_order_total` | すべて |
| ソート順序 | `payment_nz/checkmo/sort_order` | すべて |
| 有効 | `payment_nz/purchaseorder/active` | すべて |
| タイトル | `payment_nz/purchaseorder/title` | すべて |
| 新規注文ステータス | `payment_nz/purchaseorder/order_status` | すべて |
| 対象国からの支払い | `payment_nz/purchaseorder/allowspecific` | すべて |
| 特定国からの支払い | `payment_nz/purchaseorder/specificcountry` | すべて |
| 最低注文合計 | `payment_nz/purchaseorder/min_order_total` | すべて |
| 最大注文合計 | `payment_nz/purchaseorder/max_order_total` | すべて |
| ソート順序 | `payment_nz/purchaseorder/sort_order` | すべて |
| 有効 | `payment_nz/authorizenet_directpost/active` | すべて |
| 支払いアクション | `payment_nz/authorizenet_directpost/payment_action` | すべて |
| タイトル | `payment_nz/authorizenet_directpost/title` | すべて |
| 新規注文ステータス | `payment_nz/authorizenet_directpost/order_status` | すべて |
| 受け入れ可能な通貨 | `payment_nz/authorizenet_directpost/currency` | すべて |
| デバッグ | `payment_nz/authorizenet_directpost/debug` | すべて |
| クレジットカードの種類 | `payment_nz/authorizenet_directpost/cctypes` | すべて |
| クレジットカードの確認 | `payment_nz/authorizenet_directpost/useccv` | すべて |
| 対象国からの支払い | `payment_nz/authorizenet_directpost/allowspecific` | すべて |
| 特定国からの支払い | `payment_nz/authorizenet_directpost/specificcountry` | すべて |
| 最低注文合計 | `payment_nz/authorizenet_directpost/min_order_total` | すべて |
| 最大注文合計 | `payment_nz/authorizenet_directpost/max_order_total` | すべて |
| ソート順序 | `payment_nz/authorizenet_directpost/sort_order` | すべて |
| 有効 | `payment_nz/cybersource/active` | Commerce Enterpriseのみ |
| 支払いアクション | `payment_nz/cybersource/payment_action` | Commerce Enterpriseのみ |
| タイトル | `payment_nz/cybersource/title` | Commerce Enterpriseのみ |
| 新規注文ステータス | `payment_nz/cybersource/order_status` | Commerce Enterpriseのみ |
| デバッグ | `payment_nz/cybersource/debug` | Commerce Enterpriseのみ |
| クレジットカードの種類 | `payment_nz/cybersource/cctypes` | Commerce Enterpriseのみ |
| 対象国からの支払い | `payment_nz/cybersource/allowspecific` | Commerce Enterpriseのみ |
| 特定国からの支払い | `payment_nz/cybersource/specificcountry` | Commerce Enterpriseのみ |
| 最低注文合計 | `payment_nz/cybersource/min_order_total` | Commerce Enterpriseのみ |
| 最大注文合計 | `payment_nz/cybersource/max_order_total` | Commerce Enterpriseのみ |
| ソート順序 | `payment_nz/cybersource/sort_order` | Commerce Enterpriseのみ |
| 有効 | `payment_nz/worldpay/active` | Commerce Enterpriseのみ |
| タイトル | `payment_nz/worldpay/title` | Commerce Enterpriseのみ |
| 連絡先情報の編集を許可 | `payment_nz/worldpay/fix_contact` | Commerce Enterpriseのみ |
| 連絡先情報を隠す | `payment_nz/worldpay/hide_contact` | Commerce Enterpriseのみ |
| 署名フィールド | `payment_nz/worldpay/signature_fields` | Commerce Enterpriseのみ |
| デバッグ | `payment_nz/worldpay/debug` | Commerce Enterpriseのみ |
| テストの支払いアクション | `payment_nz/worldpay/test_action` | Commerce Enterpriseのみ |
| 支払いアクション | `payment_nz/worldpay/payment_action` | Commerce Enterpriseのみ |
| 対象国からの支払い | `payment_nz/worldpay/allowspecific` | Commerce Enterpriseのみ |
| 特定国からの支払い | `payment_nz/worldpay/specificcountry` | Commerce Enterpriseのみ |
| 注文ステータスを「CVVの不正行為が疑われる」に設定 | `payment_nz/worldpay/cvv_fraud_case` | Commerce Enterpriseのみ |
| 注文ステータスを「Postcode AVSの不正行為が疑われる」に設定 | `payment_nz/worldpay/avs_fraud_case` | Commerce Enterpriseのみ |
| ソート順序 | `payment_nz/worldpay/sort_order` | Commerce Enterpriseのみ |
| 有効 | `payment_nz/eway/active` | Commerce Enterpriseのみ |
| 接続タイプ | `payment_nz/eway/connection_type` | Commerce Enterpriseのみ |
| タイトル | `payment_nz/eway/title` | Commerce Enterpriseのみ |
| 支払いアクション | `payment_nz/eway/payment_action` | Commerce Enterpriseのみ |
| デバッグ | `payment_nz/eway/debug` | Commerce Enterpriseのみ |
| クレジットカードの種類 | `payment_nz/eway/cctypes` | Commerce Enterpriseのみ |
| 対象国からの支払い | `payment_nz/eway/allowspecific` | Commerce Enterpriseのみ |
| 特定国からの支払い | `payment_nz/eway/specificcountry` | Commerce Enterpriseのみ |
| ソート順序 | `payment_nz/eway/sort_order` | Commerce Enterpriseのみ |
| スケジュール済み取得 | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | すべて |
| PayPal加盟店ページのスタイル | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | すべて |
| スケジュール済み取得 | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | すべて |
| スケジュール済み取得 | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | すべて |
| PayPal加盟店ページのスタイル | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | すべて |
| 有効 | `payment_hk/free/active` | すべて |
| タイトル | `payment_hk/free/title` | すべて |
| 新規注文ステータス | `payment_hk/free/order_status` | すべて |
| すべての項目に自動請求書を発行する | `payment_hk/free/payment_action` | すべて |
| 対象国からの支払い | `payment_hk/free/allowspecific` | すべて |
| 特定国からの支払い | `payment_hk/free/specificcountry` | すべて |
| ソート順序 | `payment_hk/free/sort_order` | すべて |
| 有効 | `payment_hk/cashondelivery/active` | すべて |
| タイトル | `payment_hk/cashondelivery/title` | すべて |
| 新規注文ステータス | `payment_hk/cashondelivery/order_status` | すべて |
| 対象国からの支払い | `payment_hk/cashondelivery/allowspecific` | すべて |
| 特定国からの支払い | `payment_hk/cashondelivery/specificcountry` | すべて |
| 手順 | `payment_hk/cashondelivery/instructions` | すべて |
| 最低注文合計 | `payment_hk/cashondelivery/min_order_total` | すべて |
| 最大注文合計 | `payment_hk/cashondelivery/max_order_total` | すべて |
| ソート順序 | `payment_hk/cashondelivery/sort_order` | すべて |
| 有効 | `payment_hk/banktransfer/active` | すべて |
| タイトル | `payment_hk/banktransfer/title` | すべて |
| 新規注文ステータス | `payment_hk/banktransfer/order_status` | すべて |
| 対象国からの支払い | `payment_hk/banktransfer/allowspecific` | すべて |
| 特定国からの支払い | `payment_hk/banktransfer/specificcountry` | すべて |
| 手順 | `payment_hk/banktransfer/instructions` | すべて |
| 最低注文合計 | `payment_hk/banktransfer/min_order_total` | すべて |
| 最大注文合計 | `payment_hk/banktransfer/max_order_total` | すべて |
| ソート順序 | `payment_hk/banktransfer/sort_order` | すべて |
| 有効 | `payment_hk/checkmo/active` | すべて |
| タイトル | `payment_hk/checkmo/title` | すべて |
| 新規注文ステータス | `payment_hk/checkmo/order_status` | すべて |
| 対象国からの支払い | `payment_hk/checkmo/allowspecific` | すべて |
| 特定国からの支払い | `payment_hk/checkmo/specificcountry` | すべて |
| 最低注文合計 | `payment_hk/checkmo/min_order_total` | すべて |
| 最大注文合計 | `payment_hk/checkmo/max_order_total` | すべて |
| ソート順序 | `payment_hk/checkmo/sort_order` | すべて |
| 有効 | `payment_hk/purchaseorder/active` | すべて |
| タイトル | `payment_hk/purchaseorder/title` | すべて |
| 新規注文ステータス | `payment_hk/purchaseorder/order_status` | すべて |
| 対象国からの支払い | `payment_hk/purchaseorder/allowspecific` | すべて |
| 特定国からの支払い | `payment_hk/purchaseorder/specificcountry` | すべて |
| 最低注文合計 | `payment_hk/purchaseorder/min_order_total` | すべて |
| 最大注文合計 | `payment_hk/purchaseorder/max_order_total` | すべて |
| ソート順序 | `payment_hk/purchaseorder/sort_order` | すべて |
| 有効 | `payment_hk/authorizenet_directpost/active` | すべて |
| 支払いアクション | `payment_hk/authorizenet_directpost/payment_action` | すべて |
| タイトル | `payment_hk/authorizenet_directpost/title` | すべて |
| 新規注文ステータス | `payment_hk/authorizenet_directpost/order_status` | すべて |
| 受け入れ可能な通貨 | `payment_hk/authorizenet_directpost/currency` | すべて |
| デバッグ | `payment_hk/authorizenet_directpost/debug` | すべて |
| クレジットカードの種類 | `payment_hk/authorizenet_directpost/cctypes` | すべて |
| クレジットカードの確認 | `payment_hk/authorizenet_directpost/useccv` | すべて |
| 対象国からの支払い | `payment_hk/authorizenet_directpost/allowspecific` | すべて |
| 特定国からの支払い | `payment_hk/authorizenet_directpost/specificcountry` | すべて |
| 最低注文合計 | `payment_hk/authorizenet_directpost/min_order_total` | すべて |
| 最大注文合計 | `payment_hk/authorizenet_directpost/max_order_total` | すべて |
| ソート順序 | `payment_hk/authorizenet_directpost/sort_order` | すべて |
| 有効 | `payment_hk/cybersource/active` | Commerce Enterpriseのみ |
| 支払いアクション | `payment_hk/cybersource/payment_action` | Commerce Enterpriseのみ |
| タイトル | `payment_hk/cybersource/title` | Commerce Enterpriseのみ |
| 新規注文ステータス | `payment_hk/cybersource/order_status` | Commerce Enterpriseのみ |
| デバッグ | `payment_hk/cybersource/debug` | Commerce Enterpriseのみ |
| クレジットカードの種類 | `payment_hk/cybersource/cctypes` | Commerce Enterpriseのみ |
| 対象国からの支払い | `payment_hk/cybersource/allowspecific` | Commerce Enterpriseのみ |
| 特定国からの支払い | `payment_hk/cybersource/specificcountry` | Commerce Enterpriseのみ |
| 最低注文合計 | `payment_hk/cybersource/min_order_total` | Commerce Enterpriseのみ |
| 最大注文合計 | `payment_hk/cybersource/max_order_total` | Commerce Enterpriseのみ |
| ソート順序 | `payment_hk/cybersource/sort_order` | Commerce Enterpriseのみ |
| 有効 | `payment_hk/worldpay/active` | Commerce Enterpriseのみ |
| タイトル | `payment_hk/worldpay/title` | Commerce Enterpriseのみ |
| 連絡先情報の編集を許可 | `payment_hk/worldpay/fix_contact` | Commerce Enterpriseのみ |
| 連絡先情報を隠す | `payment_hk/worldpay/hide_contact` | Commerce Enterpriseのみ |
| デバッグ | `payment_hk/worldpay/debug` | Commerce Enterpriseのみ |
| テストの支払いアクション | `payment_hk/worldpay/test_action` | Commerce Enterpriseのみ |
| 支払いアクション | `payment_hk/worldpay/payment_action` | Commerce Enterpriseのみ |
| 対象国からの支払い | `payment_hk/worldpay/allowspecific` | Commerce Enterpriseのみ |
| 特定国からの支払い | `payment_hk/worldpay/specificcountry` | Commerce Enterpriseのみ |
| 注文ステータスを「CVVの不正行為が疑われる」に設定 | `payment_hk/worldpay/cvv_fraud_case` | Commerce Enterpriseのみ |
| 注文ステータスを「Postcode AVSの不正行為が疑われる」に設定 | `payment_hk/worldpay/avs_fraud_case` | Commerce Enterpriseのみ |
| ソート順序 | `payment_hk/worldpay/sort_order` | Commerce Enterpriseのみ |
| 有効 | `payment_hk/eway/active` | Commerce Enterpriseのみ |
| 接続タイプ | `payment_hk/eway/connection_type` | Commerce Enterpriseのみ |
| タイトル | `payment_hk/eway/title` | Commerce Enterpriseのみ |
| サンドボックスモード | `payment_hk/eway/sandbox_flag` | Commerce Enterpriseのみ |
| 支払いアクション | `payment_hk/eway/payment_action` | Commerce Enterpriseのみ |
| デバッグ | `payment_hk/eway/debug` | Commerce Enterpriseのみ |
| クレジットカードの種類 | `payment_hk/eway/cctypes` | Commerce Enterpriseのみ |
| 対象国からの支払い | `payment_hk/eway/allowspecific` | Commerce Enterpriseのみ |
| 特定国からの支払い | `payment_hk/eway/specificcountry` | Commerce Enterpriseのみ |
| ソート順序 | `payment_hk/eway/sort_order` | Commerce Enterpriseのみ |
| スケジュール済み取得 | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | すべて |
| PayPal加盟店ページのスタイル | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | すべて |
| スケジュール済み取得 | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | すべて |
| スケジュール済み取得 | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | すべて |
| PayPal加盟店ページのスタイル | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | すべて |
| 有効 | `payment_es/free/active` | すべて |
| タイトル | `payment_es/free/title` | すべて |
| 新規注文ステータス | `payment_es/free/order_status` | すべて |
| すべての項目に自動請求書を発行する | `payment_es/free/payment_action` | すべて |
| 対象国からの支払い | `payment_es/free/allowspecific` | すべて |
| 特定国からの支払い | `payment_es/free/specificcountry` | すべて |
| ソート順序 | `payment_es/free/sort_order` | すべて |
| 有効 | `payment_es/cashondelivery/active` | すべて |
| タイトル | `payment_es/cashondelivery/title` | すべて |
| 新規注文ステータス | `payment_es/cashondelivery/order_status` | すべて |
| 対象国からの支払い | `payment_es/cashondelivery/allowspecific` | すべて |
| 特定国からの支払い | `payment_es/cashondelivery/specificcountry` | すべて |
| 手順 | `payment_es/cashondelivery/instructions` | すべて |
| 最低注文合計 | `payment_es/cashondelivery/min_order_total` | すべて |
| 最大注文合計 | `payment_es/cashondelivery/max_order_total` | すべて |
| ソート順序 | `payment_es/cashondelivery/sort_order` | すべて |
| 有効 | `payment_es/banktransfer/active` | すべて |
| タイトル | `payment_es/banktransfer/title` | すべて |
| 新規注文ステータス | `payment_es/banktransfer/order_status` | すべて |
| 対象国からの支払い | `payment_es/banktransfer/allowspecific` | すべて |
| 特定国からの支払い | `payment_es/banktransfer/specificcountry` | すべて |
| 手順 | `payment_es/banktransfer/instructions` | すべて |
| 最低注文合計 | `payment_es/banktransfer/min_order_total` | すべて |
| 最大注文合計 | `payment_es/banktransfer/max_order_total` | すべて |
| ソート順序 | `payment_es/banktransfer/sort_order` | すべて |
| 有効 | `payment_es/checkmo/active` | すべて |
| タイトル | `payment_es/checkmo/title` | すべて |
| 新規注文ステータス | `payment_es/checkmo/order_status` | すべて |
| 対象国からの支払い | `payment_es/checkmo/allowspecific` | すべて |
| 特定国からの支払い | `payment_es/checkmo/specificcountry` | すべて |
| 小切手の支払先 | `payment_es/checkmo/payable_to` | すべて |
| 最低注文合計 | `payment_es/checkmo/min_order_total` | すべて |
| 最大注文合計 | `payment_es/checkmo/max_order_total` | すべて |
| ソート順序 | `payment_es/checkmo/sort_order` | すべて |
| 有効 | `payment_es/purchaseorder/active` | すべて |
| タイトル | `payment_es/purchaseorder/title` | すべて |
| 新規注文ステータス | `payment_es/purchaseorder/order_status` | すべて |
| 対象国からの支払い | `payment_es/purchaseorder/allowspecific` | すべて |
| 特定国からの支払い | `payment_es/purchaseorder/specificcountry` | すべて |
| 最低注文合計 | `payment_es/purchaseorder/min_order_total` | すべて |
| 最大注文合計 | `payment_es/purchaseorder/max_order_total` | すべて |
| ソート順序 | `payment_es/purchaseorder/sort_order` | すべて |
| 有効 | `payment_es/authorizenet_directpost/active` | すべて |
| 支払いアクション | `payment_es/authorizenet_directpost/payment_action` | すべて |
| タイトル | `payment_es/authorizenet_directpost/title` | すべて |
| 新規注文ステータス | `payment_es/authorizenet_directpost/order_status` | すべて |
| 受け入れ可能な通貨 | `payment_es/authorizenet_directpost/currency` | すべて |
| デバッグ | `payment_es/authorizenet_directpost/debug` | すべて |
| クレジットカードの種類 | `payment_es/authorizenet_directpost/cctypes` | すべて |
| クレジットカードの確認 | `payment_es/authorizenet_directpost/useccv` | すべて |
| 対象国からの支払い | `payment_es/authorizenet_directpost/allowspecific` | すべて |
| 特定国からの支払い | `payment_es/authorizenet_directpost/specificcountry` | すべて |
| 最低注文合計 | `payment_es/authorizenet_directpost/min_order_total` | すべて |
| 最大注文合計 | `payment_es/authorizenet_directpost/max_order_total` | すべて |
| ソート順序 | `payment_es/authorizenet_directpost/sort_order` | すべて |
| 有効 | `payment_es/cybersource/active` | Commerce Enterpriseのみ |
| 支払いアクション | `payment_es/cybersource/payment_action` | Commerce Enterpriseのみ |
| タイトル | `payment_es/cybersource/title` | Commerce Enterpriseのみ |
| プロファイル ID | `payment_es/cybersource/profile_id` | Commerce Enterpriseのみ\| ![暗号化](/help/assets/configuration/cloud-enc.png) |
| 新規注文ステータス | `payment_es/cybersource/order_status` | Commerce Enterpriseのみ |
| デバッグ | `payment_es/cybersource/debug` | Commerce Enterpriseのみ |
| クレジットカードの種類 | `payment_es/cybersource/cctypes` | Commerce Enterpriseのみ |
| 対象国からの支払い | `payment_es/cybersource/allowspecific` | Commerce Enterpriseのみ |
| 特定国からの支払い | `payment_es/cybersource/specificcountry` | Commerce Enterpriseのみ |
| 最低注文合計 | `payment_es/cybersource/min_order_total` | Commerce Enterpriseのみ |
| 最大注文合計 | `payment_es/cybersource/max_order_total` | Commerce Enterpriseのみ |
| ソート順序 | `payment_es/cybersource/sort_order` | Commerce Enterpriseのみ |
| 有効 | `payment_es/worldpay/active` | Commerce Enterpriseのみ |
| タイトル | `payment_es/worldpay/title` | Commerce Enterpriseのみ |
| インストール ID | `payment_es/worldpay/installation_id` | Commerce Enterpriseのみ |
| リモート管理者インストール ID | `payment_es/worldpay/admin_installation_id` | Commerce Enterpriseのみ |
| 連絡先情報の編集を許可 | `payment_es/worldpay/fix_contact` | Commerce Enterpriseのみ |
| 連絡先情報を隠す | `payment_es/worldpay/hide_contact` | Commerce Enterpriseのみ |
| 署名フィールド | `payment_es/worldpay/signature_fields` | Commerce Enterpriseのみ |
| テストモード | `payment_es/worldpay/sandbox_flag` | Commerce Enterpriseのみ |
| テストの支払いアクション | `payment_es/worldpay/test_action` | Commerce Enterpriseのみ |
| 支払いアクション | `payment_es/worldpay/payment_action` | Commerce Enterpriseのみ |
| 対象国からの支払い | `payment_es/worldpay/allowspecific` | Commerce Enterpriseのみ |
| 特定国からの支払い | `payment_es/worldpay/specificcountry` | Commerce Enterpriseのみ |
| 注文ステータスを「CVVの不正行為が疑われる」に設定 | `payment_es/worldpay/cvv_fraud_case` | Commerce Enterpriseのみ |
| 注文ステータスを「Postcode AVSの不正行為が疑われる」に設定 | `payment_es/worldpay/avs_fraud_case` | Commerce Enterpriseのみ |
| ソート順序 | `payment_es/worldpay/sort_order` | Commerce Enterpriseのみ |
| 有効 | `payment_es/eway/active` | Commerce Enterpriseのみ |
| 接続タイプ | `payment_es/eway/connection_type` | Commerce Enterpriseのみ |
| タイトル | `payment_es/eway/title` | Commerce Enterpriseのみ |
| 支払いアクション | `payment_es/eway/payment_action` | Commerce Enterpriseのみ |
| デバッグ | `payment_es/eway/debug` | Commerce Enterpriseのみ |
| クレジットカードの種類 | `payment_es/eway/cctypes` | Commerce Enterpriseのみ |
| 対象国からの支払い | `payment_es/eway/allowspecific` | Commerce Enterpriseのみ |
| 特定国からの支払い | `payment_es/eway/specificcountry` | Commerce Enterpriseのみ |
| ソート順序 | `payment_es/eway/sort_order` | Commerce Enterpriseのみ |
| スケジュール済み取得 | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | すべて |
| PayPal加盟店ページのスタイル | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | すべて |
| スケジュール済み取得 | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | すべて |
| スケジュール済み取得 | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | すべて |
| PayPal加盟店ページのスタイル | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | すべて |
| 有効 | `payment_it/free/active` | すべて |
| タイトル | `payment_it/free/title` | すべて |
| 新規注文ステータス | `payment_it/free/order_status` | すべて |
| すべての項目に自動請求書を発行する | `payment_it/free/payment_action` | すべて |
| 対象国からの支払い | `payment_it/free/allowspecific` | すべて |
| 特定国からの支払い | `payment_it/free/specificcountry` | すべて |
| ソート順序 | `payment_it/free/sort_order` | すべて |
| 有効 | `payment_it/cashondelivery/active` | すべて |
| タイトル | `payment_it/cashondelivery/title` | すべて |
| 新規注文ステータス | `payment_it/cashondelivery/order_status` | すべて |
| 対象国からの支払い | `payment_it/cashondelivery/allowspecific` | すべて |
| 特定国からの支払い | `payment_it/cashondelivery/specificcountry` | すべて |
| 手順 | `payment_it/cashondelivery/instructions` | すべて |
| 最低注文合計 | `payment_it/cashondelivery/min_order_total` | すべて |
| 最大注文合計 | `payment_it/cashondelivery/max_order_total` | すべて |
| ソート順序 | `payment_it/cashondelivery/sort_order` | すべて |
| 有効 | `payment_it/banktransfer/active` | すべて |
| タイトル | `payment_it/banktransfer/title` | すべて |
| 新規注文ステータス | `payment_it/banktransfer/order_status` | すべて |
| 対象国からの支払い | `payment_it/banktransfer/allowspecific` | すべて |
| 特定国からの支払い | `payment_it/banktransfer/specificcountry` | すべて |
| 手順 | `payment_it/banktransfer/instructions` | すべて |
| 最低注文合計 | `payment_it/banktransfer/min_order_total` | すべて |
| 最大注文合計 | `payment_it/banktransfer/max_order_total` | すべて |
| ソート順序 | `payment_it/banktransfer/sort_order` | すべて |
| 有効 | `payment_it/checkmo/active` | すべて |
| タイトル | `payment_it/checkmo/title` | すべて |
| 新規注文ステータス | `payment_it/checkmo/order_status` | すべて |
| 対象国からの支払い | `payment_it/checkmo/allowspecific` | すべて |
| 特定国からの支払い | `payment_it/checkmo/specificcountry` | すべて |
| 最低注文合計 | `payment_it/checkmo/min_order_total` | すべて |
| 最大注文合計 | `payment_it/checkmo/max_order_total` | すべて |
| ソート順序 | `payment_it/checkmo/sort_order` | すべて |
| 有効 | `payment_it/purchaseorder/active` | すべて |
| タイトル | `payment_it/purchaseorder/title` | すべて |
| 新規注文ステータス | `payment_it/purchaseorder/order_status` | すべて |
| 対象国からの支払い | `payment_it/purchaseorder/allowspecific` | すべて |
| 特定国からの支払い | `payment_it/purchaseorder/specificcountry` | すべて |
| 最低注文合計 | `payment_it/purchaseorder/min_order_total` | すべて |
| 最大注文合計 | `payment_it/purchaseorder/max_order_total` | すべて |
| ソート順序 | `payment_it/purchaseorder/sort_order` | すべて |
| 有効 | `payment_it/authorizenet_directpost/active` | すべて |
| 支払いアクション | `payment_it/authorizenet_directpost/payment_action` | すべて |
| タイトル | `payment_it/authorizenet_directpost/title` | すべて |
| 新規注文ステータス | `payment_it/authorizenet_directpost/order_status` | すべて |
| 受け入れ可能な通貨 | `payment_it/authorizenet_directpost/currency` | すべて |
| デバッグ | `payment_it/authorizenet_directpost/debug` | すべて |
| クレジットカードの種類 | `payment_it/authorizenet_directpost/cctypes` | すべて |
| クレジットカードの確認 | `payment_it/authorizenet_directpost/useccv` | すべて |
| 対象国からの支払い | `payment_it/authorizenet_directpost/allowspecific` | すべて |
| 特定国からの支払い | `payment_it/authorizenet_directpost/specificcountry` | すべて |
| 最低注文合計 | `payment_it/authorizenet_directpost/min_order_total` | すべて |
| 最大注文合計 | `payment_it/authorizenet_directpost/max_order_total` | すべて |
| ソート順序 | `payment_it/authorizenet_directpost/sort_order` | すべて |
| 有効 | `payment_it/cybersource/active` | Commerce Enterpriseのみ |
| 支払いアクション | `payment_it/cybersource/payment_action` | Commerce Enterpriseのみ |
| タイトル | `payment_it/cybersource/title` | Commerce Enterpriseのみ |
| 新規注文ステータス | `payment_it/cybersource/order_status` | Commerce Enterpriseのみ |
| デバッグ | `payment_it/cybersource/debug` | Commerce Enterpriseのみ |
| クレジットカードの種類 | `payment_it/cybersource/cctypes` | Commerce Enterpriseのみ |
| 対象国からの支払い | `payment_it/cybersource/allowspecific` | Commerce Enterpriseのみ |
| 特定国からの支払い | `payment_it/cybersource/specificcountry` | Commerce Enterpriseのみ |
| 最低注文合計 | `payment_it/cybersource/min_order_total` | Commerce Enterpriseのみ |
| 最大注文合計 | `payment_it/cybersource/max_order_total` | Commerce Enterpriseのみ |
| ソート順序 | `payment_it/cybersource/sort_order` | Commerce Enterpriseのみ |
| 有効 | `payment_it/worldpay/active` | Commerce Enterpriseのみ |
| タイトル | `payment_it/worldpay/title` | Commerce Enterpriseのみ |
| 連絡先情報の編集を許可 | `payment_it/worldpay/fix_contact` | Commerce Enterpriseのみ |
| 連絡先情報を隠す | `payment_it/worldpay/hide_contact` | Commerce Enterpriseのみ |
| 署名フィールド | `payment_it/worldpay/signature_fields` | Commerce Enterpriseのみ |
| デバッグ | `payment_it/worldpay/debug` | Commerce Enterpriseのみ |
| テストの支払いアクション | `payment_it/worldpay/test_action` | Commerce Enterpriseのみ |
| 支払いアクション | `payment_it/worldpay/payment_action` | Commerce Enterpriseのみ |
| 対象国からの支払い | `payment_it/worldpay/allowspecific` | Commerce Enterpriseのみ |
| 特定国からの支払い | `payment_it/worldpay/specificcountry` | Commerce Enterpriseのみ |
| 注文ステータスを「CVVの不正行為が疑われる」に設定 | `payment_it/worldpay/cvv_fraud_case` | Commerce Enterpriseのみ |
| 注文ステータスを「Postcode AVSの不正行為が疑われる」に設定 | `payment_it/worldpay/avs_fraud_case` | Commerce Enterpriseのみ |
| ソート順序 | `payment_it/worldpay/sort_order` | Commerce Enterpriseのみ |
| 有効 | `payment_it/eway/active` | Commerce Enterpriseのみ |
| 接続タイプ | `payment_it/eway/connection_type` | Commerce Enterpriseのみ |
| タイトル | `payment_it/eway/title` | Commerce Enterpriseのみ |
| 支払いアクション | `payment_it/eway/payment_action` | Commerce Enterpriseのみ |
| デバッグ | `payment_it/eway/debug` | Commerce Enterpriseのみ |
| クレジットカードの種類 | `payment_it/eway/cctypes` | Commerce Enterpriseのみ |
| 対象国からの支払い | `payment_it/eway/allowspecific` | Commerce Enterpriseのみ |
| 特定国からの支払い | `payment_it/eway/specificcountry` | Commerce Enterpriseのみ |
| ソート順序 | `payment_it/eway/sort_order` | Commerce Enterpriseのみ |
| スケジュール済み取得 | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | すべて |
| PayPal加盟店ページのスタイル | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | すべて |
| スケジュール済み取得 | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | すべて |
| スケジュール済み取得 | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | すべて |
| PayPal加盟店ページのスタイル | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | すべて |
| 有効 | `payment_fr/free/active` | すべて |
| タイトル | `payment_fr/free/title` | すべて |
| 新規注文ステータス | `payment_fr/free/order_status` | すべて |
| すべての項目に自動請求書を発行する | `payment_fr/free/payment_action` | すべて |
| 対象国からの支払い | `payment_fr/free/allowspecific` | すべて |
| 特定国からの支払い | `payment_fr/free/specificcountry` | すべて |
| ソート順序 | `payment_fr/free/sort_order` | すべて |
| 有効 | `payment_fr/cashondelivery/active` | すべて |
| タイトル | `payment_fr/cashondelivery/title` | すべて |
| 新規注文ステータス | `payment_fr/cashondelivery/order_status` | すべて |
| 対象国からの支払い | `payment_fr/cashondelivery/allowspecific` | すべて |
| 特定国からの支払い | `payment_fr/cashondelivery/specificcountry` | すべて |
| 手順 | `payment_fr/cashondelivery/instructions` | すべて |
| 最低注文合計 | `payment_fr/cashondelivery/min_order_total` | すべて |
| 最大注文合計 | `payment_fr/cashondelivery/max_order_total` | すべて |
| ソート順序 | `payment_fr/cashondelivery/sort_order` | すべて |
| 有効 | `payment_fr/banktransfer/active` | すべて |
| タイトル | `payment_fr/banktransfer/title` | すべて |
| 新規注文ステータス | `payment_fr/banktransfer/order_status` | すべて |
| 対象国からの支払い | `payment_fr/banktransfer/allowspecific` | すべて |
| 特定国からの支払い | `payment_fr/banktransfer/specificcountry` | すべて |
| 手順 | `payment_fr/banktransfer/instructions` | すべて |
| 最低注文合計 | `payment_fr/banktransfer/min_order_total` | すべて |
| 最大注文合計 | `payment_fr/banktransfer/max_order_total` | すべて |
| ソート順序 | `payment_fr/banktransfer/sort_order` | すべて |
| 有効 | `payment_fr/checkmo/active` | すべて |
| タイトル | `payment_fr/checkmo/title` | すべて |
| 新規注文ステータス | `payment_fr/checkmo/order_status` | すべて |
| 対象国からの支払い | `payment_fr/checkmo/allowspecific` | すべて |
| 特定国からの支払い | `payment_fr/checkmo/specificcountry` | すべて |
| 最低注文合計 | `payment_fr/checkmo/min_order_total` | すべて |
| 最大注文合計 | `payment_fr/checkmo/max_order_total` | すべて |
| ソート順序 | `payment_fr/checkmo/sort_order` | すべて |
| 有効 | `payment_fr/purchaseorder/active` | すべて |
| タイトル | `payment_fr/purchaseorder/title` | すべて |
| 新規注文ステータス | `payment_fr/purchaseorder/order_status` | すべて |
| 対象国からの支払い | `payment_fr/purchaseorder/allowspecific` | すべて |
| 特定国からの支払い | `payment_fr/purchaseorder/specificcountry` | すべて |
| 最低注文合計 | `payment_fr/purchaseorder/min_order_total` | すべて |
| 最大注文合計 | `payment_fr/purchaseorder/max_order_total` | すべて |
| ソート順序 | `payment_fr/purchaseorder/sort_order` | すべて |
| 有効 | `payment_fr/authorizenet_directpost/active` | すべて |
| 支払いアクション | `payment_fr/authorizenet_directpost/payment_action` | すべて |
| タイトル | `payment_fr/authorizenet_directpost/title` | すべて |
| 新規注文ステータス | `payment_fr/authorizenet_directpost/order_status` | すべて |
| 受け入れ可能な通貨 | `payment_fr/authorizenet_directpost/currency` | すべて |
| デバッグ | `payment_fr/authorizenet_directpost/debug` | すべて |
| クレジットカードの種類 | `payment_fr/authorizenet_directpost/cctypes` | すべて |
| クレジットカードの確認 | `payment_fr/authorizenet_directpost/useccv` | すべて |
| 対象国からの支払い | `payment_fr/authorizenet_directpost/allowspecific` | すべて |
| 特定国からの支払い | `payment_fr/authorizenet_directpost/specificcountry` | すべて |
| 最低注文合計 | `payment_fr/authorizenet_directpost/min_order_total` | すべて |
| 最大注文合計 | `payment_fr/authorizenet_directpost/max_order_total` | すべて |
| ソート順序 | `payment_fr/authorizenet_directpost/sort_order` | すべて |
| 有効 | `payment_fr/cybersource/active` | Commerce Enterpriseのみ |
| 支払いアクション | `payment_fr/cybersource/payment_action` | Commerce Enterpriseのみ |
| タイトル | `payment_fr/cybersource/title` | Commerce Enterpriseのみ |
| 新規注文ステータス | `payment_fr/cybersource/order_status` | Commerce Enterpriseのみ |
| デバッグ | `payment_fr/cybersource/debug` | Commerce Enterpriseのみ |
| クレジットカードの種類 | `payment_fr/cybersource/cctypes` | Commerce Enterpriseのみ |
| 対象国からの支払い | `payment_fr/cybersource/allowspecific` | Commerce Enterpriseのみ |
| 特定国からの支払い | `payment_fr/cybersource/specificcountry` | Commerce Enterpriseのみ |
| 最低注文合計 | `payment_fr/cybersource/min_order_total` | Commerce Enterpriseのみ |
| 最大注文合計 | `payment_fr/cybersource/max_order_total` | Commerce Enterpriseのみ |
| ソート順序 | `payment_fr/cybersource/sort_order` | Commerce Enterpriseのみ |
| 有効 | `payment_fr/worldpay/active` | Commerce Enterpriseのみ |
| タイトル | `payment_fr/worldpay/title` | Commerce Enterpriseのみ |
| 連絡先情報の編集を許可 | `payment_fr/worldpay/fix_contact` | Commerce Enterpriseのみ |
| 連絡先情報を隠す | `payment_fr/worldpay/hide_contact` | Commerce Enterpriseのみ |
| デバッグ | `payment_fr/worldpay/debug` | Commerce Enterpriseのみ |
| テストの支払いアクション | `payment_fr/worldpay/test_action` | Commerce Enterpriseのみ |
| 支払いアクション | `payment_fr/worldpay/payment_action` | Commerce Enterpriseのみ |
| 対象国からの支払い | `payment_fr/worldpay/allowspecific` | Commerce Enterpriseのみ |
| 特定国からの支払い | `payment_fr/worldpay/specificcountry` | Commerce Enterpriseのみ |
| 注文ステータスを「CVVの不正行為が疑われる」に設定 | `payment_fr/worldpay/cvv_fraud_case` | Commerce Enterpriseのみ |
| 注文ステータスを「Postcode AVSの不正行為が疑われる」に設定 | `payment_fr/worldpay/avs_fraud_case` | Commerce Enterpriseのみ |
| ソート順序 | `payment_fr/worldpay/sort_order` | Commerce Enterpriseのみ |
| 有効 | `payment_fr/eway/active` | Commerce Enterpriseのみ |
| 接続タイプ | `payment_fr/eway/connection_type` | Commerce Enterpriseのみ |
| タイトル | `payment_fr/eway/title` | Commerce Enterpriseのみ |
| 支払いアクション | `payment_fr/eway/payment_action` | Commerce Enterpriseのみ |
| デバッグ | `payment_fr/eway/debug` | Commerce Enterpriseのみ |
| クレジットカードの種類 | `payment_fr/eway/cctypes` | Commerce Enterpriseのみ |
| 対象国からの支払い | `payment_fr/eway/allowspecific` | Commerce Enterpriseのみ |
| 特定国からの支払い | `payment_fr/eway/specificcountry` | Commerce Enterpriseのみ |
| ソート順序 | `payment_fr/eway/sort_order` | Commerce Enterpriseのみ |
| スケジュール済み取得 | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | すべて |
| PayPal加盟店ページのスタイル | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | すべて |
| スケジュール済み取得 | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | すべて |
| スケジュール済み取得 | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | すべて |
| PayPal加盟店ページのスタイル | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | すべて |
| 有効 | `payment_jp/free/active` | すべて |
| タイトル | `payment_jp/free/title` | すべて |
| 新規注文ステータス | `payment_jp/free/order_status` | すべて |
| すべての項目に自動請求書を発行する | `payment_jp/free/payment_action` | すべて |
| 対象国からの支払い | `payment_jp/free/allowspecific` | すべて |
| 特定国からの支払い | `payment_jp/free/specificcountry` | すべて |
| ソート順序 | `payment_jp/free/sort_order` | すべて |
| 有効 | `payment_jp/cashondelivery/active` | すべて |
| タイトル | `payment_jp/cashondelivery/title` | すべて |
| 新規注文ステータス | `payment_jp/cashondelivery/order_status` | すべて |
| 対象国からの支払い | `payment_jp/cashondelivery/allowspecific` | すべて |
| 特定国からの支払い | `payment_jp/cashondelivery/specificcountry` | すべて |
| 手順 | `payment_jp/cashondelivery/instructions` | すべて |
| 最低注文合計 | `payment_jp/cashondelivery/min_order_total` | すべて |
| 最大注文合計 | `payment_jp/cashondelivery/max_order_total` | すべて |
| ソート順序 | `payment_jp/cashondelivery/sort_order` | すべて |
| 有効 | `payment_jp/banktransfer/active` | すべて |
| タイトル | `payment_jp/banktransfer/title` | すべて |
| 新規注文ステータス | `payment_jp/banktransfer/order_status` | すべて |
| 対象国からの支払い | `payment_jp/banktransfer/allowspecific` | すべて |
| 特定国からの支払い | `payment_jp/banktransfer/specificcountry` | すべて |
| 手順 | `payment_jp/banktransfer/instructions` | すべて |
| 最低注文合計 | `payment_jp/banktransfer/min_order_total` | すべて |
| 最大注文合計 | `payment_jp/banktransfer/max_order_total` | すべて |
| ソート順序 | `payment_jp/banktransfer/sort_order` | すべて |
| 有効 | `payment_jp/checkmo/active` | すべて |
| タイトル | `payment_jp/checkmo/title` | すべて |
| 新規注文ステータス | `payment_jp/checkmo/order_status` | すべて |
| 対象国からの支払い | `payment_jp/checkmo/allowspecific` | すべて |
| 特定国からの支払い | `payment_jp/checkmo/specificcountry` | すべて |
| 最低注文合計 | `payment_jp/checkmo/min_order_total` | すべて |
| 最大注文合計 | `payment_jp/checkmo/max_order_total` | すべて |
| ソート順序 | `payment_jp/checkmo/sort_order` | すべて |
| 有効 | `payment_jp/purchaseorder/active` | すべて |
| タイトル | `payment_jp/purchaseorder/title` | すべて |
| 新規注文ステータス | `payment_jp/purchaseorder/order_status` | すべて |
| 対象国からの支払い | `payment_jp/purchaseorder/allowspecific` | すべて |
| 特定国からの支払い | `payment_jp/purchaseorder/specificcountry` | すべて |
| 最低注文合計 | `payment_jp/purchaseorder/min_order_total` | すべて |
| 最大注文合計 | `payment_jp/purchaseorder/max_order_total` | すべて |
| ソート順序 | `payment_jp/purchaseorder/sort_order` | すべて |
| 有効 | `payment_jp/authorizenet_directpost/active` | すべて |
| 支払いアクション | `payment_jp/authorizenet_directpost/payment_action` | すべて |
| タイトル | `payment_jp/authorizenet_directpost/title` | すべて |
| 新規注文ステータス | `payment_jp/authorizenet_directpost/order_status` | すべて |
| 受け入れ可能な通貨 | `payment_jp/authorizenet_directpost/currency` | すべて |
| デバッグ | `payment_jp/authorizenet_directpost/debug` | すべて |
| クレジットカードの種類 | `payment_jp/authorizenet_directpost/cctypes` | すべて |
| クレジットカードの確認 | `payment_jp/authorizenet_directpost/useccv` | すべて |
| 対象国からの支払い | `payment_jp/authorizenet_directpost/allowspecific` | すべて |
| 特定国からの支払い | `payment_jp/authorizenet_directpost/specificcountry` | すべて |
| 最低注文合計 | `payment_jp/authorizenet_directpost/min_order_total` | すべて |
| 最大注文合計 | `payment_jp/authorizenet_directpost/max_order_total` | すべて |
| ソート順序 | `payment_jp/authorizenet_directpost/sort_order` | すべて |
| 有効 | `payment_jp/cybersource/active` | Commerce Enterpriseのみ |
| 支払いアクション | `payment_jp/cybersource/payment_action` | Commerce Enterpriseのみ |
| タイトル | `payment_jp/cybersource/title` | Commerce Enterpriseのみ |
| デバッグ | `payment_jp/cybersource/debug` | Commerce Enterpriseのみ |
| クレジットカードの種類 | `payment_jp/cybersource/cctypes` | Commerce Enterpriseのみ |
| 対象国からの支払い | `payment_jp/cybersource/allowspecific` | Commerce Enterpriseのみ |
| 特定国からの支払い | `payment_jp/cybersource/specificcountry` | Commerce Enterpriseのみ |
| 最低注文合計 | `payment_jp/cybersource/min_order_total` | Commerce Enterpriseのみ |
| 最大注文合計 | `payment_jp/cybersource/max_order_total` | Commerce Enterpriseのみ |
| ソート順序 | `payment_jp/cybersource/sort_order` | Commerce Enterpriseのみ |
| 有効 | `payment_jp/worldpay/active` | Commerce Enterpriseのみ |
| タイトル | `payment_jp/worldpay/title` | Commerce Enterpriseのみ |
| 連絡先情報の編集を許可 | `payment_jp/worldpay/fix_contact` | Commerce Enterpriseのみ |
| 連絡先情報を隠す | `payment_jp/worldpay/hide_contact` | Commerce Enterpriseのみ |
| デバッグ | `payment_jp/worldpay/debug` | Commerce Enterpriseのみ |
| テストの支払いアクション | `payment_jp/worldpay/test_action` | Commerce Enterpriseのみ |
| 支払いアクション | `payment_jp/worldpay/payment_action` | Commerce Enterpriseのみ |
| 対象国からの支払い | `payment_jp/worldpay/allowspecific` | Commerce Enterpriseのみ |
| 特定国からの支払い | `payment_jp/worldpay/specificcountry` | Commerce Enterpriseのみ |
| 注文ステータスを「CVVの不正行為が疑われる」に設定 | `payment_jp/worldpay/cvv_fraud_case` | Commerce Enterpriseのみ |
| 注文ステータスを「Postcode AVSの不正行為が疑われる」に設定 | `payment_jp/worldpay/avs_fraud_case` | Commerce Enterpriseのみ |
| ソート順序 | `payment_jp/worldpay/sort_order` | Commerce Enterpriseのみ |
| 有効 | `payment_jp/eway/active` | Commerce Enterpriseのみ |
| 接続タイプ | `payment_jp/eway/connection_type` | Commerce Enterpriseのみ |
| タイトル | `payment_jp/eway/title` | Commerce Enterpriseのみ |
| 支払いアクション | `payment_jp/eway/payment_action` | Commerce Enterpriseのみ |
| デバッグ | `payment_jp/eway/debug` | Commerce Enterpriseのみ |
| クレジットカードの種類 | `payment_jp/eway/cctypes` | Commerce Enterpriseのみ |
| 対象国からの支払い | `payment_jp/eway/allowspecific` | Commerce Enterpriseのみ |
| 特定国からの支払い | `payment_jp/eway/specificcountry` | Commerce Enterpriseのみ |
| ソート順序 | `payment_jp/eway/sort_order` | Commerce Enterpriseのみ |
| スケジュール済み取得 | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | すべて |
| PayPal加盟店ページのスタイル | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | すべて |
| スケジュール済み取得 | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | すべて |
| スケジュール済み取得 | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | すべて |
| PayPal加盟店ページのスタイル | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | すべて |
| クレジットカード設定 | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/heading_cc` | すべて |
| 次の場合にトランザクションを拒否： | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | すべて |
| スケジュール済み取得 | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | すべて |
| 有効 | `payment_au/free/active` | すべて |
| タイトル | `payment_au/free/title` | すべて |
| 新規注文ステータス | `payment_au/free/order_status` | すべて |
| すべての項目に自動請求書を発行する | `payment_au/free/payment_action` | すべて |
| 対象国からの支払い | `payment_au/free/allowspecific` | すべて |
| 特定国からの支払い | `payment_au/free/specificcountry` | すべて |
| ソート順序 | `payment_au/free/sort_order` | すべて |
| 有効 | `payment_au/cashondelivery/active` | すべて |
| タイトル | `payment_au/cashondelivery/title` | すべて |
| 新規注文ステータス | `payment_au/cashondelivery/order_status` | すべて |
| 対象国からの支払い | `payment_au/cashondelivery/allowspecific` | すべて |
| 特定国からの支払い | `payment_au/cashondelivery/specificcountry` | すべて |
| 手順 | `payment_au/cashondelivery/instructions` | すべて |
| 最低注文合計 | `payment_au/cashondelivery/min_order_total` | すべて |
| 最大注文合計 | `payment_au/cashondelivery/max_order_total` | すべて |
| ソート順序 | `payment_au/cashondelivery/sort_order` | すべて |
| 有効 | `payment_au/banktransfer/active` | すべて |
| タイトル | `payment_au/banktransfer/title` | すべて |
| 新規注文ステータス | `payment_au/banktransfer/order_status` | すべて |
| 対象国からの支払い | `payment_au/banktransfer/allowspecific` | すべて |
| 特定国からの支払い | `payment_au/banktransfer/specificcountry` | すべて |
| 手順 | `payment_au/banktransfer/instructions` | すべて |
| 最低注文合計 | `payment_au/banktransfer/min_order_total` | すべて |
| 最大注文合計 | `payment_au/banktransfer/max_order_total` | すべて |
| ソート順序 | `payment_au/banktransfer/sort_order` | すべて |
| 有効 | `payment_au/checkmo/active` | すべて |
| タイトル | `payment_au/checkmo/title` | すべて |
| 新規注文ステータス | `payment_au/checkmo/order_status` | すべて |
| 対象国からの支払い | `payment_au/checkmo/allowspecific` | すべて |
| 特定国からの支払い | `payment_au/checkmo/specificcountry` | すべて |
| 小切手の支払先 | `payment_au/checkmo/payable_to` | すべて |
| 小切手の送信先 | `payment_au/checkmo/mailing_address` | すべて |
| 最低注文合計 | `payment_au/checkmo/min_order_total` | すべて |
| 最大注文合計 | `payment_au/checkmo/max_order_total` | すべて |
| ソート順序 | `payment_au/checkmo/sort_order` | すべて |
| 有効 | `payment_au/purchaseorder/active` | すべて |
| タイトル | `payment_au/purchaseorder/title` | すべて |
| 新規注文ステータス | `payment_au/purchaseorder/order_status` | すべて |
| 対象国からの支払い | `payment_au/purchaseorder/allowspecific` | すべて |
| 特定国からの支払い | `payment_au/purchaseorder/specificcountry` | すべて |
| 最低注文合計 | `payment_au/purchaseorder/min_order_total` | すべて |
| 最大注文合計 | `payment_au/purchaseorder/max_order_total` | すべて |
| ソート順序 | `payment_au/purchaseorder/sort_order` | すべて |
| 有効 | `payment_au/authorizenet_directpost/active` | すべて |
| 支払いアクション | `payment_au/authorizenet_directpost/payment_action` | すべて |
| タイトル | `payment_au/authorizenet_directpost/title` | すべて |
| 新規注文ステータス | `payment_au/authorizenet_directpost/order_status` | すべて |
| 受け入れ可能な通貨 | `payment_au/authorizenet_directpost/currency` | すべて |
| デバッグ | `payment_au/authorizenet_directpost/debug` | すべて |
| クレジットカードの種類 | `payment_au/authorizenet_directpost/cctypes` | すべて |
| クレジットカードの確認 | `payment_au/authorizenet_directpost/useccv` | すべて |
| 対象国からの支払い | `payment_au/authorizenet_directpost/allowspecific` | すべて |
| 特定国からの支払い | `payment_au/authorizenet_directpost/specificcountry` | すべて |
| 最低注文合計 | `payment_au/authorizenet_directpost/min_order_total` | すべて |
| 最大注文合計 | `payment_au/authorizenet_directpost/max_order_total` | すべて |
| ソート順序 | `payment_au/authorizenet_directpost/sort_order` | すべて |
| 有効 | `payment_au/cybersource/active` | Commerce Enterpriseのみ |
| 支払いアクション | `payment_au/cybersource/payment_action` | Commerce Enterpriseのみ |
| タイトル | `payment_au/cybersource/title` | Commerce Enterpriseのみ |
| 加盟店ID | `payment_au/cybersource/merchant_id` | Commerce Enterpriseのみ\| ![暗号化](/help/assets/configuration/cloud-enc.png) |
| プロファイル ID | `payment_au/cybersource/profile_id` | Commerce Enterpriseのみ\| ![暗号化](/help/assets/configuration/cloud-enc.png) |
| 新規注文ステータス | `payment_au/cybersource/order_status` | Commerce Enterpriseのみ |
| デバッグ | `payment_au/cybersource/debug` | Commerce Enterpriseのみ |
| クレジットカードの種類 | `payment_au/cybersource/cctypes` | Commerce Enterpriseのみ |
| 対象国からの支払い | `payment_au/cybersource/allowspecific` | Commerce Enterpriseのみ |
| 特定国からの支払い | `payment_au/cybersource/specificcountry` | Commerce Enterpriseのみ |
| 最低注文合計 | `payment_au/cybersource/min_order_total` | Commerce Enterpriseのみ |
| 最大注文合計 | `payment_au/cybersource/max_order_total` | Commerce Enterpriseのみ |
| ソート順序 | `payment_au/cybersource/sort_order` | Commerce Enterpriseのみ |
| 有効 | `payment_au/worldpay/active` | Commerce Enterpriseのみ |
| タイトル | `payment_au/worldpay/title` | Commerce Enterpriseのみ |
| インストール ID | `payment_au/worldpay/installation_id` | Commerce Enterpriseのみ |
| 連絡先情報の編集を許可 | `payment_au/worldpay/fix_contact` | Commerce Enterpriseのみ |
| 連絡先情報を隠す | `payment_au/worldpay/hide_contact` | Commerce Enterpriseのみ |
| 署名フィールド | `payment_au/worldpay/signature_fields` | Commerce Enterpriseのみ |
| デバッグ | `payment_au/worldpay/debug` | Commerce Enterpriseのみ |
| テストモード | `payment_au/worldpay/sandbox_flag` | Commerce Enterpriseのみ |
| テストの支払いアクション | `payment_au/worldpay/test_action` | Commerce Enterpriseのみ |
| 支払いアクション | `payment_au/worldpay/payment_action` | Commerce Enterpriseのみ |
| 対象国からの支払い | `payment_au/worldpay/allowspecific` | Commerce Enterpriseのみ |
| 特定国からの支払い | `payment_au/worldpay/specificcountry` | Commerce Enterpriseのみ |
| 注文ステータスを「CVVの不正行為が疑われる」に設定 | `payment_au/worldpay/cvv_fraud_case` | Commerce Enterpriseのみ |
| 注文ステータスを「Postcode AVSの不正行為が疑われる」に設定 | `payment_au/worldpay/avs_fraud_case` | Commerce Enterpriseのみ |
| ソート順序 | `payment_au/worldpay/sort_order` | Commerce Enterpriseのみ |
| 有効 | `payment_au/eway/active` | Commerce Enterpriseのみ |
| 接続タイプ | `payment_au/eway/connection_type` | Commerce Enterpriseのみ |
| タイトル | `payment_au/eway/title` | Commerce Enterpriseのみ |
| 支払いアクション | `payment_au/eway/payment_action` | Commerce Enterpriseのみ |
| デバッグ | `payment_au/eway/debug` | Commerce Enterpriseのみ |
| クレジットカードの種類 | `payment_au/eway/cctypes` | Commerce Enterpriseのみ |
| 対象国からの支払い | `payment_au/eway/allowspecific` | Commerce Enterpriseのみ |
| 特定国からの支払い | `payment_au/eway/specificcountry` | Commerce Enterpriseのみ |
| ソート順序 | `payment_au/eway/sort_order` | Commerce Enterpriseのみ |
| スケジュール済み取得 | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | すべて |
| PayPal加盟店ページのスタイル | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | すべて |
| スケジュール済み取得 | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | すべて |
| PayPal加盟店ページのスタイル | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | すべて |
| このソリューションを有効にする | `payment/paypal_payment_pro/active` | すべて |
| クレジットカード設定 | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/heading_cc` | すべて |
| 次の場合にトランザクションを拒否： | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | すべて |
| スケジュール済み取得 | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | すべて |
| クレジットカード設定 | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/heading_cc` | すべて |
| 次の場合にトランザクションを拒否： | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | すべて |
| スケジュール済み取得 | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | すべて |
| スケジュール済み取得 | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | すべて |
| PayPal加盟店ページのスタイル | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | すべて |
| 有効 | `payment_ca/free/active` | すべて |
| タイトル | `payment_ca/free/title` | すべて |
| 新規注文ステータス | `payment_ca/free/order_status` | すべて |
| すべての項目に自動請求書を発行する | `payment_ca/free/payment_action` | すべて |
| 対象国からの支払い | `payment_ca/free/allowspecific` | すべて |
| 特定国からの支払い | `payment_ca/free/specificcountry` | すべて |
| ソート順序 | `payment_ca/free/sort_order` | すべて |
| 有効 | `payment_ca/cashondelivery/active` | すべて |
| タイトル | `payment_ca/cashondelivery/title` | すべて |
| 新規注文ステータス | `payment_ca/cashondelivery/order_status` | すべて |
| 対象国からの支払い | `payment_ca/cashondelivery/allowspecific` | すべて |
| 特定国からの支払い | `payment_ca/cashondelivery/specificcountry` | すべて |
| 手順 | `payment_ca/cashondelivery/instructions` | すべて |
| 最低注文合計 | `payment_ca/cashondelivery/min_order_total` | すべて |
| 最大注文合計 | `payment_ca/cashondelivery/max_order_total` | すべて |
| ソート順序 | `payment_ca/cashondelivery/sort_order` | すべて |
| 有効 | `payment_ca/banktransfer/active` | すべて |
| タイトル | `payment_ca/banktransfer/title` | すべて |
| 新規注文ステータス | `payment_ca/banktransfer/order_status` | すべて |
| 対象国からの支払い | `payment_ca/banktransfer/allowspecific` | すべて |
| 特定国からの支払い | `payment_ca/banktransfer/specificcountry` | すべて |
| 手順 | `payment_ca/banktransfer/instructions` | すべて |
| 最低注文合計 | `payment_ca/banktransfer/min_order_total` | すべて |
| 最大注文合計 | `payment_ca/banktransfer/max_order_total` | すべて |
| ソート順序 | `payment_ca/banktransfer/sort_order` | すべて |
| 有効 | `payment_ca/checkmo/active` | すべて |
| タイトル | `payment_ca/checkmo/title` | すべて |
| 新規注文ステータス | `payment_ca/checkmo/order_status` | すべて |
| 対象国からの支払い | `payment_ca/checkmo/allowspecific` | すべて |
| 特定国からの支払い | `payment_ca/checkmo/specificcountry` | すべて |
| 最低注文合計 | `payment_ca/checkmo/min_order_total` | すべて |
| 最大注文合計 | `payment_ca/checkmo/max_order_total` | すべて |
| ソート順序 | `payment_ca/checkmo/sort_order` | すべて |
| 有効 | `payment_ca/purchaseorder/active` | すべて |
| タイトル | `payment_ca/purchaseorder/title` | すべて |
| 新規注文ステータス | `payment_ca/purchaseorder/order_status` | すべて |
| 対象国からの支払い | `payment_ca/purchaseorder/allowspecific` | すべて |
| 特定国からの支払い | `payment_ca/purchaseorder/specificcountry` | すべて |
| 最低注文合計 | `payment_ca/purchaseorder/min_order_total` | すべて |
| 最大注文合計 | `payment_ca/purchaseorder/max_order_total` | すべて |
| ソート順序 | `payment_ca/purchaseorder/sort_order` | すべて |
| 有効 | `payment_ca/authorizenet_directpost/active` | すべて |
| 支払いアクション | `payment_ca/authorizenet_directpost/payment_action` | すべて |
| タイトル | `payment_ca/authorizenet_directpost/title` | すべて |
| 受け入れ可能な通貨 | `payment_ca/authorizenet_directpost/currency` | すべて |
| デバッグ | `payment_ca/authorizenet_directpost/debug` | すべて |
| クレジットカードの種類 | `payment_ca/authorizenet_directpost/cctypes` | すべて |
| クレジットカードの確認 | `payment_ca/authorizenet_directpost/useccv` | すべて |
| 対象国からの支払い | `payment_ca/authorizenet_directpost/allowspecific` | すべて |
| 特定国からの支払い | `payment_ca/authorizenet_directpost/specificcountry` | すべて |
| 最低注文合計 | `payment_ca/authorizenet_directpost/min_order_total` | すべて |
| 最大注文合計 | `payment_ca/authorizenet_directpost/max_order_total` | すべて |
| ソート順序 | `payment_ca/authorizenet_directpost/sort_order` | すべて |
| 有効 | `payment_ca/cybersource/active` | Commerce Enterpriseのみ |
| 支払いアクション | `payment_ca/cybersource/payment_action` | Commerce Enterpriseのみ |
| タイトル | `payment_ca/cybersource/title` | Commerce Enterpriseのみ |
| デバッグ | `payment_ca/cybersource/debug` | Commerce Enterpriseのみ |
| クレジットカードの種類 | `payment_ca/cybersource/cctypes` | Commerce Enterpriseのみ |
| 対象国からの支払い | `payment_ca/cybersource/allowspecific` | Commerce Enterpriseのみ |
| 特定国からの支払い | `payment_ca/cybersource/specificcountry` | Commerce Enterpriseのみ |
| 最低注文合計 | `payment_ca/cybersource/min_order_total` | Commerce Enterpriseのみ |
| 最大注文合計 | `payment_ca/cybersource/max_order_total` | Commerce Enterpriseのみ |
| ソート順序 | `payment_ca/cybersource/sort_order` | Commerce Enterpriseのみ |
| 有効 | `payment_ca/worldpay/active` | Commerce Enterpriseのみ |
| タイトル | `payment_ca/worldpay/title` | Commerce Enterpriseのみ |
| 連絡先情報の編集を許可 | `payment_ca/worldpay/fix_contact` | Commerce Enterpriseのみ |
| 連絡先情報を隠す | `payment_ca/worldpay/hide_contact` | Commerce Enterpriseのみ |
| 署名フィールド | `payment_ca/worldpay/signature_fields` | Commerce Enterpriseのみ |
| デバッグ | `payment_ca/worldpay/debug` | Commerce Enterpriseのみ |
| テストの支払いアクション | `payment_ca/worldpay/test_action` | Commerce Enterpriseのみ |
| 支払いアクション | `payment_ca/worldpay/payment_action` | Commerce Enterpriseのみ |
| 対象国からの支払い | `payment_ca/worldpay/allowspecific` | Commerce Enterpriseのみ |
| 特定国からの支払い | `payment_ca/worldpay/specificcountry` | Commerce Enterpriseのみ |
| 注文ステータスを「CVVの不正行為が疑われる」に設定 | `payment_ca/worldpay/cvv_fraud_case` | Commerce Enterpriseのみ |
| 注文ステータスを「Postcode AVSの不正行為が疑われる」に設定 | `payment_ca/worldpay/avs_fraud_case` | Commerce Enterpriseのみ |
| ソート順序 | `payment_ca/worldpay/sort_order` | Commerce Enterpriseのみ |
| 有効 | `payment_ca/eway/active` | Commerce Enterpriseのみ |
| 接続タイプ | `payment_ca/eway/connection_type` | Commerce Enterpriseのみ |
| タイトル | `payment_ca/eway/title` | Commerce Enterpriseのみ |
| 支払いアクション | `payment_ca/eway/payment_action` | Commerce Enterpriseのみ |
| デバッグ | `payment_ca/eway/debug` | Commerce Enterpriseのみ |
| クレジットカードの種類 | `payment_ca/eway/cctypes` | Commerce Enterpriseのみ |
| 対象国からの支払い | `payment_ca/eway/allowspecific` | Commerce Enterpriseのみ |
| 特定国からの支払い | `payment_ca/eway/specificcountry` | Commerce Enterpriseのみ |
| ソート順序 | `payment_ca/eway/sort_order` | Commerce Enterpriseのみ |
| スケジュール済み取得 | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | すべて |
| PayPal加盟店ページのスタイル | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | すべて |
| スケジュール済み取得 | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | すべて |
| PayPal加盟店ページのスタイル | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | すべて |
| 有効 | `payment_other/free/active` | すべて |
| タイトル | `payment_other/free/title` | すべて |
| 新規注文ステータス | `payment_other/free/order_status` | すべて |
| すべての項目に自動請求書を発行する | `payment_other/free/payment_action` | すべて |
| 対象国からの支払い | `payment_other/free/allowspecific` | すべて |
| 特定国からの支払い | `payment_other/free/specificcountry` | すべて |
| ソート順序 | `payment_other/free/sort_order` | すべて |
| 有効 | `payment_other/cashondelivery/active` | すべて |
| タイトル | `payment_other/cashondelivery/title` | すべて |
| 新規注文ステータス | `payment_other/cashondelivery/order_status` | すべて |
| 対象国からの支払い | `payment_other/cashondelivery/allowspecific` | すべて |
| 特定国からの支払い | `payment_other/cashondelivery/specificcountry` | すべて |
| 手順 | `payment_other/cashondelivery/instructions` | すべて |
| 最低注文合計 | `payment_other/cashondelivery/min_order_total` | すべて |
| 最大注文合計 | `payment_other/cashondelivery/max_order_total` | すべて |
| ソート順序 | `payment_other/cashondelivery/sort_order` | すべて |
| 有効 | `payment_other/banktransfer/active` | すべて |
| タイトル | `payment_other/banktransfer/title` | すべて |
| 新規注文ステータス | `payment_other/banktransfer/order_status` | すべて |
| 対象国からの支払い | `payment_other/banktransfer/allowspecific` | すべて |
| 特定国からの支払い | `payment_other/banktransfer/specificcountry` | すべて |
| 手順 | `payment_other/banktransfer/instructions` | すべて |
| 最低注文合計 | `payment_other/banktransfer/min_order_total` | すべて |
| 最大注文合計 | `payment_other/banktransfer/max_order_total` | すべて |
| ソート順序 | `payment_other/banktransfer/sort_order` | すべて |
| 有効 | `payment_other/checkmo/active` | すべて |
| タイトル | `payment_other/checkmo/title` | すべて |
| 新規注文ステータス | `payment_other/checkmo/order_status` | すべて |
| 対象国からの支払い | `payment_other/checkmo/allowspecific` | すべて |
| 特定国からの支払い | `payment_other/checkmo/specificcountry` | すべて |
| 最低注文合計 | `payment_other/checkmo/min_order_total` | すべて |
| 最大注文合計 | `payment_other/checkmo/max_order_total` | すべて |
| ソート順序 | `payment_other/checkmo/sort_order` | すべて |
| 有効 | `payment_other/purchaseorder/active` | すべて |
| タイトル | `payment_other/purchaseorder/title` | すべて |
| 新規注文ステータス | `payment_other/purchaseorder/order_status` | すべて |
| 対象国からの支払い | `payment_other/purchaseorder/allowspecific` | すべて |
| 特定国からの支払い | `payment_other/purchaseorder/specificcountry` | すべて |
| 最低注文合計 | `payment_other/purchaseorder/min_order_total` | すべて |
| 最大注文合計 | `payment_other/purchaseorder/max_order_total` | すべて |
| ソート順序 | `payment_other/purchaseorder/sort_order` | すべて |
| 有効 | `payment_other/authorizenet_directpost/active` | すべて |
| 支払いアクション | `payment_other/authorizenet_directpost/payment_action` | すべて |
| タイトル | `payment_other/authorizenet_directpost/title` | すべて |
| 受け入れ可能な通貨 | `payment_other/authorizenet_directpost/currency` | すべて |
| デバッグ | `payment_other/authorizenet_directpost/debug` | すべて |
| 電子メール顧客 | `payment_other/authorizenet_directpost/email_customer` | すべて |
| クレジットカードの種類 | `payment_other/authorizenet_directpost/cctypes` | すべて |
| クレジットカードの確認 | `payment_other/authorizenet_directpost/useccv` | すべて |
| 対象国からの支払い | `payment_other/authorizenet_directpost/allowspecific` | すべて |
| 特定国からの支払い | `payment_other/authorizenet_directpost/specificcountry` | すべて |
| 最低注文合計 | `payment_other/authorizenet_directpost/min_order_total` | すべて |
| 最大注文合計 | `payment_other/authorizenet_directpost/max_order_total` | すべて |
| ソート順序 | `payment_other/authorizenet_directpost/sort_order` | すべて |
| 有効 | `payment_other/cybersource/active` | Commerce Enterpriseのみ |
| 支払いアクション | `payment_other/cybersource/payment_action` | Commerce Enterpriseのみ |
| タイトル | `payment_other/cybersource/title` | Commerce Enterpriseのみ |
| デバッグ | `payment_other/cybersource/debug` | Commerce Enterpriseのみ |
| クレジットカードの種類 | `payment_other/cybersource/cctypes` | Commerce Enterpriseのみ |
| 対象国からの支払い | `payment_other/cybersource/allowspecific` | Commerce Enterpriseのみ |
| 特定国からの支払い | `payment_other/cybersource/specificcountry` | Commerce Enterpriseのみ |
| 最低注文合計 | `payment_other/cybersource/min_order_total` | Commerce Enterpriseのみ |
| 最大注文合計 | `payment_other/cybersource/max_order_total` | Commerce Enterpriseのみ |
| ソート順序 | `payment_other/cybersource/sort_order` | Commerce Enterpriseのみ |
| 有効 | `payment_other/worldpay/active` | Commerce Enterpriseのみ |
| タイトル | `payment_other/worldpay/title` | Commerce Enterpriseのみ |
| 連絡先情報の編集を許可 | `payment_other/worldpay/fix_contact` | Commerce Enterpriseのみ |
| 連絡先情報を隠す | `payment_other/worldpay/hide_contact` | Commerce Enterpriseのみ |
| 署名フィールド | `payment_other/worldpay/signature_fields` | Commerce Enterpriseのみ |
| デバッグ | `payment_other/worldpay/debug` | Commerce Enterpriseのみ |
| テストの支払いアクション | `payment_other/worldpay/test_action` | Commerce Enterpriseのみ |
| 支払いアクション | `payment_other/worldpay/payment_action` | Commerce Enterpriseのみ |
| 対象国からの支払い | `payment_other/worldpay/allowspecific` | Commerce Enterpriseのみ |
| 特定国からの支払い | `payment_other/worldpay/specificcountry` | Commerce Enterpriseのみ |
| 注文ステータスを「CVVの不正行為が疑われる」に設定 | `payment_other/worldpay/cvv_fraud_case` | Commerce Enterpriseのみ |
| 注文ステータスを「Postcode AVSの不正行為が疑われる」に設定 | `payment_other/worldpay/avs_fraud_case` | Commerce Enterpriseのみ |
| ソート順序 | `payment_other/worldpay/sort_order` | Commerce Enterpriseのみ |
| 有効 | `payment_other/eway/active` | Commerce Enterpriseのみ |
| 接続タイプ | `payment_other/eway/connection_type` | Commerce Enterpriseのみ |
| タイトル | `payment_other/eway/title` | Commerce Enterpriseのみ |
| 支払いアクション | `payment_other/eway/payment_action` | Commerce Enterpriseのみ |
| デバッグ | `payment_other/eway/debug` | Commerce Enterpriseのみ |
| クレジットカードの種類 | `payment_other/eway/cctypes` | Commerce Enterpriseのみ |
| 対象国からの支払い | `payment_other/eway/allowspecific` | Commerce Enterpriseのみ |
| 特定国からの支払い | `payment_other/eway/specificcountry` | Commerce Enterpriseのみ |
| ソート順序 | `payment_other/eway/sort_order` | Commerce Enterpriseのみ |
| スケジュール済み取得 | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | すべて |
| PayPal加盟店ページのスタイル | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | すべて |
| 有効 | `payment_de/checkmo/active` | すべて |
| タイトル | `payment_de/checkmo/title` | すべて |
| 新規注文ステータス | `payment_de/checkmo/order_status` | すべて |
| 対象国からの支払い | `payment_de/checkmo/allowspecific` | すべて |
| 特定国からの支払い | `payment_de/checkmo/specificcountry` | すべて |
| 最低注文合計 | `payment_de/checkmo/min_order_total` | すべて |
| 最大注文合計 | `payment_de/checkmo/max_order_total` | すべて |
| ソート順序 | `payment_de/checkmo/sort_order` | すべて |
| 有効 | `payment_de/banktransfer/active` | すべて |
| タイトル | `payment_de/banktransfer/title` | すべて |
| 新規注文ステータス | `payment_de/banktransfer/order_status` | すべて |
| 対象国からの支払い | `payment_de/banktransfer/allowspecific` | すべて |
| 特定国からの支払い | `payment_de/banktransfer/specificcountry` | すべて |
| 手順 | `payment_de/banktransfer/instructions` | すべて |
| 最低注文合計 | `payment_de/banktransfer/min_order_total` | すべて |
| 最大注文合計 | `payment_de/banktransfer/max_order_total` | すべて |
| ソート順序 | `payment_de/banktransfer/sort_order` | すべて |
| 有効 | `payment_de/cashondelivery/active` | すべて |
| タイトル | `payment_de/cashondelivery/title` | すべて |
| 新規注文ステータス | `payment_de/cashondelivery/order_status` | すべて |
| 対象国からの支払い | `payment_de/cashondelivery/allowspecific` | すべて |
| 特定国からの支払い | `payment_de/cashondelivery/specificcountry` | すべて |
| 手順 | `payment_de/cashondelivery/instructions` | すべて |
| 最低注文合計 | `payment_de/cashondelivery/min_order_total` | すべて |
| 最大注文合計 | `payment_de/cashondelivery/max_order_total` | すべて |
| ソート順序 | `payment_de/cashondelivery/sort_order` | すべて |
| 有効 | `payment_de/free/active` | すべて |
| タイトル | `payment_de/free/title` | すべて |
| 新規注文ステータス | `payment_de/free/order_status` | すべて |
| すべての項目に自動請求書を発行する | `payment_de/free/payment_action` | すべて |
| 対象国からの支払い | `payment_de/free/allowspecific` | すべて |
| 特定国からの支払い | `payment_de/free/specificcountry` | すべて |
| ソート順序 | `payment_de/free/sort_order` | すべて |
| 有効 | `payment_de/purchaseorder/active` | すべて |
| タイトル | `payment_de/purchaseorder/title` | すべて |
| 新規注文ステータス | `payment_de/purchaseorder/order_status` | すべて |
| 対象国からの支払い | `payment_de/purchaseorder/allowspecific` | すべて |
| 特定国からの支払い | `payment_de/purchaseorder/specificcountry` | すべて |
| 最低注文合計 | `payment_de/purchaseorder/min_order_total` | すべて |
| 最大注文合計 | `payment_de/purchaseorder/max_order_total` | すべて |
| ソート順序 | `payment_de/purchaseorder/sort_order` | すべて |
| 有効 | `payment_de/cybersource/active` | Commerce Enterpriseのみ |
| 支払いアクション | `payment_de/cybersource/payment_action` | Commerce Enterpriseのみ |
| タイトル | `payment_de/cybersource/title` | Commerce Enterpriseのみ |
| 新規注文ステータス | `payment_de/cybersource/order_status` | Commerce Enterpriseのみ |
| デバッグ | `payment_de/cybersource/debug` | Commerce Enterpriseのみ |
| クレジットカードの種類 | `payment_de/cybersource/cctypes` | Commerce Enterpriseのみ |
| 対象国からの支払い | `payment_de/cybersource/allowspecific` | Commerce Enterpriseのみ |
| 特定国からの支払い | `payment_de/cybersource/specificcountry` | Commerce Enterpriseのみ |
| 最低注文合計 | `payment_de/cybersource/min_order_total` | Commerce Enterpriseのみ |
| 最大注文合計 | `payment_de/cybersource/max_order_total` | Commerce Enterpriseのみ |
| ソート順序 | `payment_de/cybersource/sort_order` | Commerce Enterpriseのみ |
| 有効 | `payment_de/authorizenet_directpost/active` | すべて |
| 支払いアクション | `payment_de/authorizenet_directpost/payment_action` | すべて |
| タイトル | `payment_de/authorizenet_directpost/title` | すべて |
| 新規注文ステータス | `payment_de/authorizenet_directpost/order_status` | すべて |
| 受け入れ可能な通貨 | `payment_de/authorizenet_directpost/currency` | すべて |
| デバッグ | `payment_de/authorizenet_directpost/debug` | すべて |
| クレジットカードの種類 | `payment_de/authorizenet_directpost/cctypes` | すべて |
| クレジットカードの確認 | `payment_de/authorizenet_directpost/useccv` | すべて |
| 対象国からの支払い | `payment_de/authorizenet_directpost/allowspecific` | すべて |
| 特定国からの支払い | `payment_de/authorizenet_directpost/specificcountry` | すべて |
| 最低注文合計 | `payment_de/authorizenet_directpost/min_order_total` | すべて |
| 最大注文合計 | `payment_de/authorizenet_directpost/max_order_total` | すべて |
| ソート順序 | `payment_de/authorizenet_directpost/sort_order` | すべて |
| 有効 | `payment_de/worldpay/active` | Commerce Enterpriseのみ |
| タイトル | `payment_de/worldpay/title` | Commerce Enterpriseのみ |
| 連絡先情報の編集を許可 | `payment_de/worldpay/fix_contact` | Commerce Enterpriseのみ |
| 連絡先情報を隠す | `payment_de/worldpay/hide_contact` | Commerce Enterpriseのみ |
| 署名フィールド | `payment_de/worldpay/signature_fields` | Commerce Enterpriseのみ |
| テストモード | `payment_de/worldpay/sandbox_flag` | Commerce Enterpriseのみ |
| テストの支払いアクション | `payment_de/worldpay/test_action` | Commerce Enterpriseのみ |
| 支払いアクション | `payment_de/worldpay/payment_action` | Commerce Enterpriseのみ |
| 対象国からの支払い | `payment_de/worldpay/allowspecific` | Commerce Enterpriseのみ |
| 特定国からの支払い | `payment_de/worldpay/specificcountry` | Commerce Enterpriseのみ |
| 注文ステータスを「CVVの不正行為が疑われる」に設定 | `payment_de/worldpay/cvv_fraud_case` | Commerce Enterpriseのみ |
| 注文ステータスを「Postcode AVSの不正行為が疑われる」に設定 | `payment_de/worldpay/avs_fraud_case` | Commerce Enterpriseのみ |
| ソート順序 | `payment_de/worldpay/sort_order` | Commerce Enterpriseのみ |
| 有効 | `payment_de/eway/active` | Commerce Enterpriseのみ |
| 接続タイプ | `payment_de/eway/connection_type` | Commerce Enterpriseのみ |
| タイトル | `payment_de/eway/title` | Commerce Enterpriseのみ |
| 支払いアクション | `payment_de/eway/payment_action` | Commerce Enterpriseのみ |
| デバッグ | `payment_de/eway/debug` | Commerce Enterpriseのみ |
| クレジットカードの種類 | `payment_de/eway/cctypes` | Commerce Enterpriseのみ |
| 対象国からの支払い | `payment_de/eway/allowspecific` | Commerce Enterpriseのみ |
| 特定国からの支払い | `payment_de/eway/specificcountry` | Commerce Enterpriseのみ |
| ソート順序 | `payment_de/eway/sort_order` | Commerce Enterpriseのみ |
| スケジュール済み取得 | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | すべて |
| PayPal加盟店ページのスタイル | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | すべて |
| スケジュール済み取得 | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | すべて |
| PayPal加盟店ページのスタイル | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_frontend/paypal_pages` | すべて |
| スケジュール済み取得 | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | すべて |
| PayPal加盟店ページのスタイル | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | すべて |
| 有効 | `payment_gb/checkmo/active` | すべて |
| タイトル | `payment_gb/checkmo/title` | すべて |
| 新規注文ステータス | `payment_gb/checkmo/order_status` | すべて |
| 対象国からの支払い | `payment_gb/checkmo/allowspecific` | すべて |
| 特定国からの支払い | `payment_gb/checkmo/specificcountry` | すべて |
| 小切手の支払先 | `payment_gb/checkmo/payable_to` | すべて |
| 最低注文合計 | `payment_gb/checkmo/min_order_total` | すべて |
| 最大注文合計 | `payment_gb/checkmo/max_order_total` | すべて |
| ソート順序 | `payment_gb/checkmo/sort_order` | すべて |
| 有効 | `payment_gb/banktransfer/active` | すべて |
| タイトル | `payment_gb/banktransfer/title` | すべて |
| 新規注文ステータス | `payment_gb/banktransfer/order_status` | すべて |
| 対象国からの支払い | `payment_gb/banktransfer/allowspecific` | すべて |
| 特定国からの支払い | `payment_gb/banktransfer/specificcountry` | すべて |
| 手順 | `payment_gb/banktransfer/instructions` | すべて |
| 最低注文合計 | `payment_gb/banktransfer/min_order_total` | すべて |
| 最大注文合計 | `payment_gb/banktransfer/max_order_total` | すべて |
| ソート順序 | `payment_gb/banktransfer/sort_order` | すべて |
| 有効 | `payment_gb/cashondelivery/active` | すべて |
| タイトル | `payment_gb/cashondelivery/title` | すべて |
| 新規注文ステータス | `payment_gb/cashondelivery/order_status` | すべて |
| 対象国からの支払い | `payment_gb/cashondelivery/allowspecific` | すべて |
| 特定国からの支払い | `payment_gb/cashondelivery/specificcountry` | すべて |
| 手順 | `payment_gb/cashondelivery/instructions` | すべて |
| 最低注文合計 | `payment_gb/cashondelivery/min_order_total` | すべて |
| 最大注文合計 | `payment_gb/cashondelivery/max_order_total` | すべて |
| ソート順序 | `payment_gb/cashondelivery/sort_order` | すべて |
| 有効 | `payment_gb/free/active` | すべて |
| タイトル | `payment_gb/free/title` | すべて |
| 新規注文ステータス | `payment_gb/free/order_status` | すべて |
| すべての項目に自動請求書を発行する | `payment_gb/free/payment_action` | すべて |
| 対象国からの支払い | `payment_gb/free/allowspecific` | すべて |
| 特定国からの支払い | `payment_gb/free/specificcountry` | すべて |
| ソート順序 | `payment_gb/free/sort_order` | すべて |
| 有効 | `payment_gb/purchaseorder/active` | すべて |
| タイトル | `payment_gb/purchaseorder/title` | すべて |
| 新規注文ステータス | `payment_gb/purchaseorder/order_status` | すべて |
| 対象国からの支払い | `payment_gb/purchaseorder/allowspecific` | すべて |
| 特定国からの支払い | `payment_gb/purchaseorder/specificcountry` | すべて |
| 最低注文合計 | `payment_gb/purchaseorder/min_order_total` | すべて |
| 最大注文合計 | `payment_gb/purchaseorder/max_order_total` | すべて |
| ソート順序 | `payment_gb/purchaseorder/sort_order` | すべて |
| 有効 | `payment_gb/cybersource/active` | Commerce Enterpriseのみ |
| 支払いアクション | `payment_gb/cybersource/payment_action` | Commerce Enterpriseのみ |
| タイトル | `payment_gb/cybersource/title` | Commerce Enterpriseのみ |
| 新規注文ステータス | `payment_gb/cybersource/order_status` | Commerce Enterpriseのみ |
| デバッグ | `payment_gb/cybersource/debug` | Commerce Enterpriseのみ |
| クレジットカードの種類 | `payment_gb/cybersource/cctypes` | Commerce Enterpriseのみ |
| 対象国からの支払い | `payment_gb/cybersource/allowspecific` | Commerce Enterpriseのみ |
| 特定国からの支払い | `payment_gb/cybersource/specificcountry` | Commerce Enterpriseのみ |
| 最低注文合計 | `payment_gb/cybersource/min_order_total` | Commerce Enterpriseのみ |
| 最大注文合計 | `payment_gb/cybersource/max_order_total` | Commerce Enterpriseのみ |
| ソート順序 | `payment_gb/cybersource/sort_order` | Commerce Enterpriseのみ |
| 有効 | `payment_gb/authorizenet_directpost/active` | すべて |
| 支払いアクション | `payment_gb/authorizenet_directpost/payment_action` | すべて |
| タイトル | `payment_gb/authorizenet_directpost/title` | すべて |
| 新規注文ステータス | `payment_gb/authorizenet_directpost/order_status` | すべて |
| 受け入れ可能な通貨 | `payment_gb/authorizenet_directpost/currency` | すべて |
| デバッグ | `payment_gb/authorizenet_directpost/debug` | すべて |
| クレジットカードの種類 | `payment_gb/authorizenet_directpost/cctypes` | すべて |
| クレジットカードの確認 | `payment_gb/authorizenet_directpost/useccv` | すべて |
| 対象国からの支払い | `payment_gb/authorizenet_directpost/allowspecific` | すべて |
| 特定国からの支払い | `payment_gb/authorizenet_directpost/specificcountry` | すべて |
| 最低注文合計 | `payment_gb/authorizenet_directpost/min_order_total` | すべて |
| 最大注文合計 | `payment_gb/authorizenet_directpost/max_order_total` | すべて |
| ソート順序 | `payment_gb/authorizenet_directpost/sort_order` | すべて |
| 有効 | `payment_gb/worldpay/active` | Commerce Enterpriseのみ |
| タイトル | `payment_gb/worldpay/title` | Commerce Enterpriseのみ |
| トランザクションのMD5 シークレット | `payment_gb/worldpay/md5_secret` | Commerce Enterpriseのみ |
| 連絡先情報の編集を許可 | `payment_gb/worldpay/fix_contact` | Commerce Enterpriseのみ |
| 連絡先情報を隠す | `payment_gb/worldpay/hide_contact` | Commerce Enterpriseのみ |
| 署名フィールド | `payment_gb/worldpay/signature_fields` | Commerce Enterpriseのみ |
| デバッグ | `payment_gb/worldpay/debug` | Commerce Enterpriseのみ |
| テストの支払いアクション | `payment_gb/worldpay/test_action` | Commerce Enterpriseのみ |
| 支払いアクション | `payment_gb/worldpay/payment_action` | Commerce Enterpriseのみ |
| 対象国からの支払い | `payment_gb/worldpay/allowspecific` | Commerce Enterpriseのみ |
| 特定国からの支払い | `payment_gb/worldpay/specificcountry` | Commerce Enterpriseのみ |
| 注文ステータスを「CVVの不正行為が疑われる」に設定 | `payment_gb/worldpay/cvv_fraud_case` | Commerce Enterpriseのみ |
| 注文ステータスを「Postcode AVSの不正行為が疑われる」に設定 | `payment_gb/worldpay/avs_fraud_case` | Commerce Enterpriseのみ |
| ソート順序 | `payment_gb/worldpay/sort_order` | Commerce Enterpriseのみ |
| 有効 | `payment_gb/eway/active` | Commerce Enterpriseのみ |
| 接続タイプ | `payment_gb/eway/connection_type` | Commerce Enterpriseのみ |
| タイトル | `payment_gb/eway/title` | Commerce Enterpriseのみ |
| 支払いアクション | `payment_gb/eway/payment_action` | Commerce Enterpriseのみ |
| デバッグ | `payment_gb/eway/debug` | Commerce Enterpriseのみ |
| クレジットカードの種類 | `payment_gb/eway/cctypes` | Commerce Enterpriseのみ |
| 対象国からの支払い | `payment_gb/eway/allowspecific` | Commerce Enterpriseのみ |
| 特定国からの支払い | `payment_gb/eway/specificcountry` | Commerce Enterpriseのみ |
| ソート順序 | `payment_gb/eway/sort_order` | Commerce Enterpriseのみ |
| スケジュール済み取得 | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | すべて |
| PayPal加盟店ページのスタイル | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | すべて |
| スケジュール済み取得 | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_schedule` | すべて |
| PayPal加盟店ページのスタイル | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/frontend/paypal_pages` | すべて |
| クレジットカード設定 | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/heading_cc` | すべて |
| 次の場合にトランザクションを拒否： | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | すべて |
| スケジュール済み取得 | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | すべて |
| PayPal加盟店ページのスタイル | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_frontend/paypal_pages` | すべて |
| PayPal クレジットを有効にする | `payment/wps_express_bml/active` | すべて |
| スケジュール済み取得 | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | すべて |
| PayPal加盟店ページのスタイル | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | すべて |
| クレジットカード設定 | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/heading_cc` | すべて |
| 次の場合にトランザクションを拒否： | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | すべて |
| スケジュール済み取得 | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | すべて |
| PayPal加盟店ページのスタイル | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_frontend/paypal_pages` | すべて |
| スケジュール済み取得 | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | すべて |
| PayPal加盟店ページのスタイル | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | すべて |
| 有効 | `payment_us/free/active` | すべて |
| タイトル | `payment_us/free/title` | すべて |
| 新規注文ステータス | `payment_us/free/order_status` | すべて |
| すべての項目に自動請求書を発行する | `payment_us/free/payment_action` | すべて |
| 対象国からの支払い | `payment_us/free/allowspecific` | すべて |
| 特定国からの支払い | `payment_us/free/specificcountry` | すべて |
| ソート順序 | `payment_us/free/sort_order` | すべて |
| 有効 | `payment_us/cashondelivery/active` | すべて |
| タイトル | `payment_us/cashondelivery/title` | すべて |
| 新規注文ステータス | `payment_us/cashondelivery/order_status` | すべて |
| 対象国からの支払い | `payment_us/cashondelivery/allowspecific` | すべて |
| 特定国からの支払い | `payment_us/cashondelivery/specificcountry` | すべて |
| 手順 | `payment_us/cashondelivery/instructions` | すべて |
| 最低注文合計 | `payment_us/cashondelivery/min_order_total` | すべて |
| 最大注文合計 | `payment_us/cashondelivery/max_order_total` | すべて |
| ソート順序 | `payment_us/cashondelivery/sort_order` | すべて |
| 有効 | `payment_us/banktransfer/active` | すべて |
| タイトル | `payment_us/banktransfer/title` | すべて |
| 新規注文ステータス | `payment_us/banktransfer/order_status` | すべて |
| 対象国からの支払い | `payment_us/banktransfer/allowspecific` | すべて |
| 特定国からの支払い | `payment_us/banktransfer/specificcountry` | すべて |
| 手順 | `payment_us/banktransfer/instructions` | すべて |
| 最低注文合計 | `payment_us/banktransfer/min_order_total` | すべて |
| 最大注文合計 | `payment_us/banktransfer/max_order_total` | すべて |
| ソート順序 | `payment_us/banktransfer/sort_order` | すべて |
| 有効 | `payment_us/checkmo/active` | すべて |
| タイトル | `payment_us/checkmo/title` | すべて |
| 新規注文ステータス | `payment_us/checkmo/order_status` | すべて |
| 対象国からの支払い | `payment_us/checkmo/allowspecific` | すべて |
| 特定国からの支払い | `payment_us/checkmo/specificcountry` | すべて |
| 小切手の支払先 | `payment_us/checkmo/payable_to` | すべて |
| 最低注文合計 | `payment_us/checkmo/min_order_total` | すべて |
| 最大注文合計 | `payment_us/checkmo/max_order_total` | すべて |
| ソート順序 | `payment_us/checkmo/sort_order` | すべて |
| 有効 | `payment_us/purchaseorder/active` | すべて |
| タイトル | `payment_us/purchaseorder/title` | すべて |
| 新規注文ステータス | `payment_us/purchaseorder/order_status` | すべて |
| 対象国からの支払い | `payment_us/purchaseorder/allowspecific` | すべて |
| 特定国からの支払い | `payment_us/purchaseorder/specificcountry` | すべて |
| 最低注文合計 | `payment_us/purchaseorder/min_order_total` | すべて |
| 最大注文合計 | `payment_us/purchaseorder/max_order_total` | すべて |
| ソート順序 | `payment_us/purchaseorder/sort_order` | すべて |
| 有効 | `payment_us/authorizenet_directpost/active` | すべて |
| 支払いアクション | `payment_us/authorizenet_directpost/payment_action` | すべて |
| タイトル | `payment_us/authorizenet_directpost/title` | すべて |
| 新規注文ステータス | `payment_us/authorizenet_directpost/order_status` | すべて |
| 受け入れ可能な通貨 | `payment_us/authorizenet_directpost/currency` | すべて |
| デバッグ | `payment_us/authorizenet_directpost/debug` | すべて |
| クレジットカードの種類 | `payment_us/authorizenet_directpost/cctypes` | すべて |
| クレジットカードの確認 | `payment_us/authorizenet_directpost/useccv` | すべて |
| 対象国からの支払い | `payment_us/authorizenet_directpost/allowspecific` | すべて |
| 特定国からの支払い | `payment_us/authorizenet_directpost/specificcountry` | すべて |
| 最低注文合計 | `payment_us/authorizenet_directpost/min_order_total` | すべて |
| 最大注文合計 | `payment_us/authorizenet_directpost/max_order_total` | すべて |
| ソート順序 | `payment_us/authorizenet_directpost/sort_order` | すべて |
| 有効 | `payment_us/cybersource/active` | Commerce Enterpriseのみ |
| 支払いアクション | `payment_us/cybersource/payment_action` | Commerce Enterpriseのみ |
| タイトル | `payment_us/cybersource/title` | Commerce Enterpriseのみ |
| 新規注文ステータス | `payment_us/cybersource/order_status` | Commerce Enterpriseのみ |
| デバッグ | `payment_us/cybersource/debug` | Commerce Enterpriseのみ |
| クレジットカードの種類 | `payment_us/cybersource/cctypes` | Commerce Enterpriseのみ |
| 対象国からの支払い | `payment_us/cybersource/allowspecific` | Commerce Enterpriseのみ |
| 特定国からの支払い | `payment_us/cybersource/specificcountry` | Commerce Enterpriseのみ |
| 最低注文合計 | `payment_us/cybersource/min_order_total` | Commerce Enterpriseのみ |
| 最大注文合計 | `payment_us/cybersource/max_order_total` | Commerce Enterpriseのみ |
| ソート順序 | `payment_us/cybersource/sort_order` | Commerce Enterpriseのみ |
| 有効 | `payment_us/worldpay/active` | Commerce Enterpriseのみ |
| タイトル | `payment_us/worldpay/title` | Commerce Enterpriseのみ |
| 連絡先情報の編集を許可 | `payment_us/worldpay/fix_contact` | Commerce Enterpriseのみ |
| 連絡先情報を隠す | `payment_us/worldpay/hide_contact` | Commerce Enterpriseのみ |
| 署名フィールド | `payment_us/worldpay/signature_fields` | Commerce Enterpriseのみ |
| デバッグ | `payment_us/worldpay/debug` | Commerce Enterpriseのみ |
| テストの支払いアクション | `payment_us/worldpay/test_action` | Commerce Enterpriseのみ |
| 支払いアクション | `payment_us/worldpay/payment_action` | Commerce Enterpriseのみ |
| 対象国からの支払い | `payment_us/worldpay/allowspecific` | Commerce Enterpriseのみ |
| 特定国からの支払い | `payment_us/worldpay/specificcountry` | Commerce Enterpriseのみ |
| 注文ステータスを「CVVの不正行為が疑われる」に設定 | `payment_us/worldpay/cvv_fraud_case` | Commerce Enterpriseのみ |
| 注文ステータスを「Postcode AVSの不正行為が疑われる」に設定 | `payment_us/worldpay/avs_fraud_case` | Commerce Enterpriseのみ |
| ソート順序 | `payment_us/worldpay/sort_order` | Commerce Enterpriseのみ |
| 有効 | `payment_us/eway/active` | Commerce Enterpriseのみ |
| 接続タイプ | `payment_us/eway/connection_type` | Commerce Enterpriseのみ |
| タイトル | `payment_us/eway/title` | Commerce Enterpriseのみ |
| 支払いアクション | `payment_us/eway/payment_action` | Commerce Enterpriseのみ |
| デバッグ | `payment_us/eway/debug` | Commerce Enterpriseのみ |
| クレジットカードの種類 | `payment_us/eway/cctypes` | Commerce Enterpriseのみ |
| 対象国からの支払い | `payment_us/eway/allowspecific` | Commerce Enterpriseのみ |
| 特定国からの支払い | `payment_us/eway/specificcountry` | Commerce Enterpriseのみ |
| ソート順序 | `payment_us/eway/sort_order` | |

{style="table-layout:auto"}
