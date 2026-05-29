---
title: 営業設定パスのリファレンス
description: Adobe Commerceのセールス設定パスと変数名について説明します。 チェックアウト、配送、税金に関する管理者設定をご覧ください。
feature: Configuration, Checkout, Gift, Shipping/Delivery, Taxes
exl-id: 7981f78a-5e5f-422c-9bff-54022e1fb9f3
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '1546'
ht-degree: 0%

---

# 営業設定パスのリファレンス

このセクションでは、管理者の&#x200B;**ストア**/設定/**構成**/**セールス**&#x200B;のオプションで使用できる変数名と構成パスをリストします。

[`magento app:config:dump` コマンド ](../cli/export-configuration.md)は、これらの値をソース コントロールにある共有設定ファイル `app/etc/config.php`に書き込みます。 任意の構成設定を上書きする方法や、機密設定を設定する方法については、[環境変数を使用して構成設定を上書きする](override-config-settings.md#environment-variables)を参照してください。 このトピックでは、_not_&#x200B;に[機密値とシステム固有の値](config-reference-sens.md)が一覧表示されています。

## セールスパス

これらの設定値は、**Stores**/設定/**Configuration**/**Sales**/**Sales**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerceだけ？ |
|--------------|--------------|--------------|
| 顧客IPの非表示 | `sales/general/hide_customer_ip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 小計 | `sales/totals_sort/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 割引 | `sales/totals_sort/discount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 発送 | `sales/totals_sort/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 税 | `sales/totals_sort/tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 固定製品税 | `sales/totals_sort/weee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 総計 | `sales/totals_sort/grand_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ギフトカード | `sales/totals_sort/giftcardaccount` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| ストアクレジット | `sales/totals_sort/customerbalance` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 再注文を許可 | `sales/reorder/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PDF プリントアウトのロゴ （200 x 50） | `sales/identity/logo` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTMLプリントビューのロゴ | `sales/identity/logo_html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| アドレス | `sales/identity/address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効にする | `sales/minimum_order/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最低金額 | `sales/minimum_order/amount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 金額に税金を含める | `sales/minimum_order/tax_including` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 説明メッセージ | `sales/minimum_order/description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ショッピングカートに表示するエラー | `sales/minimum_order/error_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| マルチアドレスチェックアウトで各アドレスを個別に検証する | `sales/minimum_order/multi_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 複数アドレスの説明メッセージ | `sales/minimum_order/multi_address_description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 買い物かごに表示するマルチアドレスエラー | `sales/minimum_order/multi_address_error_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 集約されたデータの使用 | `sales/dashboard/use_aggregated_data` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 保留中の支払い注文の有効期間（分） | `sales/orders/delete_pending_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 注文レベルでのギフトメッセージの許可 | `sales/gift_options/allow_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 注文項目のギフトメッセージを許可 | `sales/gift_options/allow_items` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 注文レベルでのギフトの折り返しを許可 | `sales/gift_options/wrapping_allow_order` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 注文商品のギフト包装を許可する | `sales/gift_options/wrapping_allow_items` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| ギフト領収書を許可 | `sales/gift_options/allow_gift_receipt` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 印刷カードを許可 | `sales/gift_options/allow_printed_card` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 印刷されたカードのデフォルト価格 | `sales/gift_options/printed_card_price` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| マップを有効にする | `sales/msrp/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 実際の価格を表示 | `sales/msrp/display_price_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デフォルトのポップアップテキストメッセージ | `sales/msrp/explanation_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デフォルトの「What&#39;s This」テキストメッセージ | `sales/msrp/explanation_message_whats_this` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ストアフロントのマイアカウントでSKUによる注文を有効にする | `sales/product_sku/my_account_enable` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 有効 | `sales/instant_purchase/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ボタンテキスト | `sales/instant_purchase/button_text` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顧客グループ | `sales/product_sku/allowed_groups` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| アーカイブを有効にする | `sales/magento_salesarchive/active` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 購入した注文をアーカイブ | `sales/magento_salesarchive/age` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| アーカイブする注文ステータス | `sales/magento_salesarchive/order_statuses` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| ストアフロントでRMAを有効にする | `sales/magento_rma/enabled` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 製品レベルでのRMAの有効化 | `sales/magento_rma/enabled_on_product` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| ストアアドレスを使用 | `sales/magento_rma/use_store_address` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## セールスメールのパス

これらの設定値は、**Stores** / 設定/**Configuration** / **Sales** / **Sales Email**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerceだけ？ |
|--------------|--------------|--------------|
| 非同期送信 | `sales_email/general/async_sending` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効 | `sales_email/order/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文確認メール送信者 | `sales_email/order/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文確認テンプレート | `sales_email/order/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ゲスト用の新規注文確認テンプレート | `sales_email/order/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送信注文の電子メールのコピー方法 | `sales_email/order/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効 | `sales_email/order_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 注文コメント メール送信者 | `sales_email/order_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 注文コメント電子メールテンプレート | `sales_email/order_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ゲスト用の注文コメント電子メールテンプレート | `sales_email/order_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 注文コメントの電子メールのコピー方法の送信 | `sales_email/order_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効 | `sales_email/invoice/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 請求書メール送信者 | `sales_email/invoice/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 請求書の電子メールテンプレート | `sales_email/invoice/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ゲスト用の請求書メールテンプレート | `sales_email/invoice/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 請求書メールのコピー方法の送信 | `sales_email/invoice/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効 | `sales_email/invoice_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 請求書コメント メール送信者 | `sales_email/invoice_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 請求書コメント電子メールテンプレート | `sales_email/invoice_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ゲスト用の請求書コメント電子メールテンプレート | `sales_email/invoice_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 請求書コメントの電子メールのコピー方法の送信 | `sales_email/invoice_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効 | `sales_email/shipment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 発送メール送信者 | `sales_email/shipment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 発送メール テンプレート | `sales_email/shipment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ゲスト用の配送メールテンプレート | `sales_email/shipment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送信メールのコピー方法 | `sales_email/shipment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効 | `sales_email/shipment_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 出荷コメント電子メール送信者 | `sales_email/shipment_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 出荷コメント電子メールテンプレート | `sales_email/shipment_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ゲスト用の出荷コメント電子メールテンプレート | `sales_email/shipment_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送信コメントの電子メールのコピー方法 | `sales_email/shipment_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効 | `sales_email/creditmemo/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットメモ電子メール送信者 | `sales_email/creditmemo/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットメモ電子メールテンプレート | `sales_email/creditmemo/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ゲスト用クレジットメモ電子メールテンプレート | `sales_email/creditmemo/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットメモ電子メールのコピー方法の送信 | `sales_email/creditmemo/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効 | `sales_email/creditmemo_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットメモのコメント電子メール送信者 | `sales_email/creditmemo_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットメモのコメント電子メールテンプレート | `sales_email/creditmemo_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ゲストのクレジットメモのコメント電子メールテンプレート | `sales_email/creditmemo_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットメモのコメントの電子メールのコピー方法の送信 | `sales_email/creditmemo_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効 | `sales_email/magento_rma/enabled` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| RMA メール送信者 | `sales_email/magento_rma/identity` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| RMA メールテンプレート | `sales_email/magento_rma/template` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| ゲスト用RMA メールテンプレート | `sales_email/magento_rma/guest_template` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| RMA電子メールのコピー方法の送信 | `sales_email/magento_rma/copy_method` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 有効 | `sales_email/magento_rma_auth/enabled` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| RMA認証メール送信者 | `sales_email/magento_rma_auth/identity` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| RMA認証のメールテンプレート | `sales_email/magento_rma_auth/template` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| ゲスト用RMA認証メールテンプレート | `sales_email/magento_rma_auth/guest_template` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| RMA承認電子メールコピー方法の送信 | `sales_email/magento_rma_auth/copy_method` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 有効 | `sales_email/magento_rma_comment/enabled` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| RMA コメント メール送信者 | `sales_email/magento_rma_comment/identity` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| RMA コメント電子メールテンプレート | `sales_email/magento_rma_comment/template` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| ゲスト用RMA コメント電子メールテンプレート | `sales_email/magento_rma_comment/guest_template` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| RMA電子メールのコピー方法の送信 | `sales_email/magento_rma_comment/copy_method` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 有効 | `sales_email/magento_rma_customer_comment/enabled` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| RMA コメント メール送信者 | `sales_email/magento_rma_customer_comment/identity` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| RMA コメント メール受信者 | `sales_email/magento_rma_customer_comment/recipient` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| RMA コメント電子メールテンプレート | `sales_email/magento_rma_customer_comment/template` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| RMA電子メールのコピー方法の送信 | `sales_email/magento_rma_customer_comment/copy_method` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| ヘッダーに注文IDを表示 | `sales_pdf/invoice/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ヘッダーに注文IDを表示 | `sales_pdf/shipment/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ヘッダーに注文IDを表示 | `sales_pdf/creditmemo/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 税パス

これらの設定値は、**Stores**/設定/**Configuration**/**Sales**/**Tax**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerceだけ？ |
|--------------|--------------|--------------|
| 送料の税区分 | `tax/classes/shipping_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ギフトオプションの税区分 | `tax/classes/wrapping_tax_class` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 製品の既定の税区分 | `tax/classes/default_product_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顧客のデフォルト税区分 | `tax/classes/default_customer_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 次に基づく税計算方法 | `tax/calculation/algorithm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 次に基づく税計算 | `tax/calculation/based_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| カタログ価格 | `tax/calculation/price_includes_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送料 | `tax/calculation/shipping_includes_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顧客税の適用 | `tax/calculation/apply_after_discount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 価格に割引を適用する | `tax/calculation/discount_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 消費税を適用 | `tax/calculation/apply_tax_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 国境を越えた貿易を可能にする | `tax/calculation/cross_border_trade_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デフォルトの国 | `tax/defaults/country` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Default State | `tax/defaults/region` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 既定の郵便番号 | `tax/defaults/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 商品の価格をカタログで表示する | `tax/display/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送料の表示 | `tax/display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 表示価格 | `tax/cart_display/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 小計を表示 | `tax/cart_display/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 配送金額の表示 | `tax/cart_display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ギフトのラッピング価格の表示 | `tax/cart_display/gift_wrapping` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 印刷カードの価格の表示 | `tax/cart_display/printed_card` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 注文の合計に税金を含める | `tax/cart_display/grandtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 税金の全要約の表示 | `tax/cart_display/full_summary` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 税小計ゼロを表示 | `tax/cart_display/zero_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 表示価格 | `tax/sales_display/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 小計を表示 | `tax/sales_display/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 配送金額の表示 | `tax/sales_display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ギフトのラッピング価格の表示 | `tax/sales_display/gift_wrapping` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 印刷カードの価格の表示 | `tax/sales_display/printed_card` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 注文の合計に税金を含める | `tax/sales_display/grandtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 税金の全要約の表示 | `tax/sales_display/full_summary` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 税小計ゼロを表示 | `tax/sales_display/zero_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| FPTを有効にする | `tax/weee/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 商品リストに価格を表示する | `tax/weee/display_list` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 商品ビューページに価格を表示する | `tax/weee/display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 販売モジュールでの価格の表示 | `tax/weee/display_sales` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メールでの価格の表示 | `tax/weee/display_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| FPTに税金を適用 | `tax/weee/apply_vat` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 小計にFPTを含める | `tax/weee/include_in_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## チェックアウトパス

これらの設定値は、**ストア**/設定/**設定**/**セールス**/**チェックアウト**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerceだけ？ |
|--------------|--------------|--------------|
| ワンページチェックアウトを有効にする | `checkout/options/onepage_checkout_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ゲストチェックアウトを許可 | `checkout/options/guest_checkout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 請求先住所の表示日 | `checkout/options/display_billing_address_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 利用条件を有効にする | `checkout/options/enable_agreements` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 見積もり有効期間（日数） | `checkout/cart/delete_quote_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ショッピングカートに商品リダイレクトを追加した後 | `checkout/cart/redirect_to_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| グループ化された製品画像 | `checkout/cart/grouped_product_image` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コンフィグ可能な商品画像 | `checkout/cart/configurable_product_image` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 見積もりの有効期間のプレビュー（分） | `checkout/cart/preview_quota_lifetime` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| カートの概要を表示 | `checkout/cart_link/use_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ショッピングカートのサイドバーを表示 | `checkout/sidebar/display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最近追加した項目の最大表示 | `checkout/sidebar/count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払いが失敗したメール送信者 | `checkout/payment_failed/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払失敗メール受信者 | `checkout/payment_failed/receiver` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払いに失敗したテンプレート | `checkout/payment_failed/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払い失敗した電子メールのコピー方法の送信 | `checkout/payment_failed/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 出荷設定のパス

これらの設定値は、**ストア**/設定/**設定**/**セールス**/**出荷設定**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerceだけ？ |
|--------------|--------------|--------------|
| カスタム配送ポリシーの適用 | `shipping/shipping_policy/enable_shipping_policy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 配送ポリシー | `shipping/shipping_policy/shipping_policy_content` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 複数発送設定のパス

これらの設定値は、**Stores**/設定/**Configuration**/**Sales**/**Multishipping Settings**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerceだけ？ |
|--------------|--------------|--------------|
| 複数の住所への配送を許可 | `multishipping/options/checkout_multiple` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 複数の住所への配送に使用できる最大数量 | `multishipping/options/checkout_multiple_maximum_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 配信方法のパス

これらの設定値は、**ストア**/設定/**設定**/**セールス**/**配信方法**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerceだけ？ |
|--------------|--------------|--------------|
| 有効 | `carriers/flatrate/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `carriers/flatrate/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メソッド名 | `carriers/flatrate/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイプ | `carriers/flatrate/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 価格 | `carriers/flatrate/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 処理手数料の計算 | `carriers/flatrate/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手数料の処理 | `carriers/flatrate/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 表示されるエラーメッセージ | `carriers/flatrate/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 適用国への配送 | `carriers/flatrate/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定の国への配送 | `carriers/flatrate/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 該当しない場合はメソッドを表示 | `carriers/flatrate/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ソート順序 | `carriers/flatrate/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効 | `carriers/freeshipping/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `carriers/freeshipping/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メソッド名 | `carriers/freeshipping/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最低注文金額 | `carriers/freeshipping/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 表示されるエラーメッセージ | `carriers/freeshipping/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 適用国への配送 | `carriers/freeshipping/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定の国への配送 | `carriers/freeshipping/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 該当しない場合はメソッドを表示 | `carriers/freeshipping/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ソート順序 | `carriers/freeshipping/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効 | `carriers/tablerate/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `carriers/tablerate/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メソッド名 | `carriers/tablerate/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 状況 | `carriers/tablerate/condition_name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 価格計算にバーチャル商品を含める | `carriers/tablerate/include_virtual_price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 書き出し | `carriers/tablerate/export` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| インポート | `carriers/tablerate/import` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 処理手数料の計算 | `carriers/tablerate/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手数料の処理 | `carriers/tablerate/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 表示されるエラーメッセージ | `carriers/tablerate/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 適用国への配送 | `carriers/tablerate/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定の国への配送 | `carriers/tablerate/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 該当しない場合はメソッドを表示 | `carriers/tablerate/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ソート順序 | `carriers/tablerate/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| チェックアウト可能 | `carriers/ups/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| RMAに対して有効 | `carriers/ups/active_rma` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| UPS タイプ | `carriers/ups/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| モード | `carriers/ups/mode_xml` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 出荷の起源 | `carriers/ups/origin_shipment` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ゲートウェイ URL | `carriers/ups/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `carriers/ups/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 交渉済みレートの有効化 | `carriers/ups/negotiated_active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Packages リクエストタイプ | `carriers/ups/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コンテナ | `carriers/ups/container` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 重み単位 | `carriers/ups/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 宛先タイプ | `carriers/ups/dest_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大パッケージ重量（サポートされている最大の配送重量については、配送業者にお問い合わせください） | `carriers/ups/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 受け取り方法 | `carriers/ups/pickup` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小パッケージ重量（サポートされる最小の配送重量については、配送業者にお問い合わせください） | `carriers/ups/min_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 処理手数料の計算 | `carriers/ups/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 処理が適用されました | `carriers/ups/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手数料の処理 | `carriers/ups/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 許可されるメソッド | `carriers/ups/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 無料メソッド | `carriers/ups/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送料無料のしきい値を有効にする | `carriers/ups/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送料無料のしきい値 | `carriers/ups/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 表示されるエラーメッセージ | `carriers/ups/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 適用国への配送 | `carriers/ups/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定の国への配送 | `carriers/ups/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 該当しない場合はメソッドを表示 | `carriers/ups/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ソート順序 | `carriers/ups/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| チェックアウト可能 | `carriers/usps/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| RMAに対して有効 | `carriers/usps/active_rma` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| モード | `carriers/usps/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Packages リクエストタイプ | `carriers/usps/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コンテナ | `carriers/usps/container` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| サイズ | `carriers/usps/size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 長さ | `carriers/usps/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 幅 | `carriers/usps/width` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 高さ | `carriers/usps/height` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Girth | `carriers/usps/girth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 機械加工可能 | `carriers/usps/machinable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大パッケージ重量（サポートされている最大の配送重量については、配送業者にお問い合わせください） | `carriers/usps/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 処理手数料の計算 | `carriers/usps/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 処理が適用されました | `carriers/usps/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手数料の処理 | `carriers/usps/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 許可されるメソッド | `carriers/usps/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 無料メソッド | `carriers/usps/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送料無料のしきい値を有効にする | `carriers/usps/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送料無料のしきい値 | `carriers/usps/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 表示されるエラーメッセージ | `carriers/usps/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 適用国への配送 | `carriers/usps/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定の国への配送 | `carriers/usps/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デバッグ | `carriers/usps/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 該当しない場合はメソッドを表示 | `carriers/usps/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ソート順序 | `carriers/usps/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| チェックアウト可能 | `carriers/fedex/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| RMAに対して有効 | `carriers/fedex/active_rma` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `carriers/fedex/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Web サービス URL （実稼動環境） | `carriers/fedex/production_webservices_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Web サービス URL （サンドボックス） | `carriers/fedex/sandbox_webservices_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Packages リクエストタイプ | `carriers/fedex/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 包装 | `carriers/fedex/packaging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ドロップオフ | `carriers/fedex/dropoff` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 重み単位 | `carriers/fedex/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大パッケージ重量（サポートされている最大の配送重量については、配送業者にお問い合わせください） | `carriers/fedex/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 処理手数料の計算 | `carriers/fedex/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 処理が適用されました | `carriers/fedex/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手数料の処理 | `carriers/fedex/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 居住者向け配送 | `carriers/fedex/residence_delivery` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 許可されるメソッド | `carriers/fedex/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ハブ ID | `carriers/fedex/smartpost_hubid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 無料メソッド | `carriers/fedex/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送料無料のしきい値を有効にする | `carriers/fedex/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送料無料のしきい値 | `carriers/fedex/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 表示されるエラーメッセージ | `carriers/fedex/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 適用国への配送 | `carriers/fedex/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定の国への配送 | `carriers/fedex/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デバッグ | `carriers/fedex/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 該当しない場合はメソッドを表示 | `carriers/fedex/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ソート順序 | `carriers/fedex/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| チェックアウト可能 | `carriers/dhl/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| RMAに対して有効 | `carriers/dhl/active_rma` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `carriers/dhl/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コンテンツタイプ | `carriers/dhl/content_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 処理手数料の計算 | `carriers/dhl/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 処理が適用されました | `carriers/dhl/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手数料の処理 | `carriers/dhl/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| オーダーの重みを分割 | `carriers/dhl/divide_order_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 重み単位 | `carriers/dhl/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| サイズ | `carriers/dhl/size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 高さ | `carriers/dhl/height` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Depth | `carriers/dhl/depth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 幅 | `carriers/dhl/width` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 許可されるメソッド | `carriers/dhl/doc_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 許可されるメソッド | `carriers/dhl/nondoc_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 準備完了 | `carriers/dhl/ready_time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 表示されるエラーメッセージ | `carriers/dhl/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 無料メソッド | `carriers/dhl/free_method_doc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 無料メソッド | `carriers/dhl/free_method_nondoc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送料無料のしきい値を有効にする | `carriers/dhl/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送料無料のしきい値 | `carriers/dhl/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 適用国への配送 | `carriers/dhl/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定の国への配送 | `carriers/dhl/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 該当しない場合はメソッドを表示 | `carriers/dhl/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ソート順序 | `carriers/dhl/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Google API パス

これらの設定値は、**Stores**/Settings > **Configuration** > **Sales** > **Google API**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerceだけ？ |
|--------------|--------------|--------------|
| 有効にする | `google/analytics/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| アカウントタイプ | `google/analytics/type` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| コンテンツ実験の有効化 | `google/analytics/experiments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| カタログページのリストプロパティ | `google/analytics/catalog_page_list_value` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| クロスセルブロックのリストプロパティ | `google/analytics/crosssell_block_list_value` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| アップセルブロックのリストプロパティ | `google/analytics/upsell_block_list_value` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 関連製品ブロックのリストプロパティ | `google/analytics/related_block_list_value` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 検索結果ページのリストプロパティ | `google/analytics/search_page_list_value` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| プロモーションフィールド「ラベル」の「内部プロモーション」。 | `google/analytics/promotions_list_value` | ![Commerceのみ](/help/assets/configuration/cloud-ee.png) |
| 有効にする | `google/adwords/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コンバージョン ID | `google/adwords/conversion_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コンバージョン言語 | `google/adwords/conversion_language` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コンバージョン形式 | `google/adwords/conversion_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コンバージョンカラー | `google/adwords/conversion_color` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コンバージョンラベル | `google/adwords/conversion_label` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コンバージョン値タイプ | `google/adwords/conversion_value_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コンバージョン値 | `google/adwords/conversion_value` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## ギフトカードのパス

これらの設定値は、**ストア**/設定/**設定**/**セールス**/**ギフトカード**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerceだけ？ |
|--------------|--------------|--------------|
| ギフトカード通知メール送信者 | `giftcard/email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ギフトカード通知メールテンプレート | `giftcard/email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 償還可能 | `giftcard/general/is_redeemable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 生涯（日数） | `giftcard/general/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ギフトメッセージを許可 | `giftcard/general/allow_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ギフトメッセージの最大長 | `giftcard/general/message_max_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 注文項目が次の場合にギフトカードアカウントを生成 | `giftcard/general/order_item_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ギフトカードのメール送信者 | `giftcard/giftcardaccount_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ギフトカードテンプレート | `giftcard/giftcardaccount_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コード長 | `giftcard/giftcardaccount_general/code_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コード形式 | `giftcard/giftcardaccount_general/code_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コード接頭辞 | `giftcard/giftcardaccount_general/code_prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コードサフィックス | `giftcard/giftcardaccount_general/code_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ダッシュのX文字ごと | `giftcard/giftcardaccount_general/code_split` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新しいプールサイズ | `giftcard/giftcardaccount_general/pool_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 低コード プールしきい値 | `giftcard/giftcardaccount_general/pool_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
