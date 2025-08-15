---
title: 販売構成パス リファレンス
description: 販売設定値のリストを参照してください。
feature: Configuration, Checkout, Gift, Shipping/Delivery, Taxes
exl-id: 7981f78a-5e5f-422c-9bff-54022e1fb9f3
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '1473'
ht-degree: 0%

---

# 販売構成パス リファレンス

このセクションでは、**ストア**/設定/**設定**/**セールス** の管理でオプションに使用できる変数名と設定パスを示します。

[`magento app:config:dump` コマンドは ](../cli/export-configuration.md) これらの値をソース管理にある共有構成ファイル `app/etc/config.php` に書き込みます。 任意の構成設定を上書きしたり、重要な設定を指定したりするには、[ 環境変数を使用して構成設定を上書き ](override-config-settings.md#environment-variables) を参照してください。 このトピックでは _機密の値とシステム固有の値_ は [ 表示されません ](config-reference-sens.md)。

## 販売パス

これらの設定値は、管理者の **Stores**/設定/**Configuration**/**Sales**/**Sales** で使用できます。

| 名前 | 設定パス | Commerceのみ？ |
|--------------|--------------|--------------|
| 顧客 IP を非表示 | `sales/general/hide_customer_ip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 小計 | `sales/totals_sort/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 割引 | `sales/totals_sort/discount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送料 | `sales/totals_sort/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 税 | `sales/totals_sort/tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 固定製品税 | `sales/totals_sort/weee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 総計 | `sales/totals_sort/grand_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ギフトカード | `sales/totals_sort/giftcardaccount` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 店舗クレジット | `sales/totals_sort/customerbalance` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 並べ替えを許可 | `sales/reorder/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PDFの印刷出力（200 x 50）のロゴ | `sales/identity/logo` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTML印刷レイアウト表示のロゴ | `sales/identity/logo_html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| アドレス | `sales/identity/address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enable （有効） | `sales/minimum_order/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小量 | `sales/minimum_order/amount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 金額に税を含める | `sales/minimum_order/tax_including` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 説明メッセージ | `sales/minimum_order/description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| カートに表示するエラー | `sales/minimum_order/error_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 複数アドレスのチェックアウトで各住所を個別に検証する | `sales/minimum_order/multi_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 複数アドレスの説明メッセージ | `sales/minimum_order/multi_address_description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 買い物かごに表示する複数アドレスエラー | `sales/minimum_order/multi_address_error_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 集計データの使用 | `sales/dashboard/use_aggregated_data` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 保留中の支払い注文の有効期間（分） | `sales/orders/delete_pending_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 注文レベルでのギフト メッセージを許可 | `sales/gift_options/allow_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 注文品目のギフト メッセージを許可 | `sales/gift_options/allow_items` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 注文レベルでギフトの折り返しを許可する | `sales/gift_options/wrapping_allow_order` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 注文品目のギフト ラッピングを許可する | `sales/gift_options/wrapping_allow_items` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| ギフト受領書を許可 | `sales/gift_options/allow_gift_receipt` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 印刷されたカードを許可 | `sales/gift_options/allow_printed_card` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 印刷されたカードの既定の価格 | `sales/gift_options/printed_card_price` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| マップを有効にする | `sales/msrp/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 実際の価格を表示 | `sales/msrp/display_price_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 既定のポップアップ テキスト メッセージ | `sales/msrp/explanation_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デフォルトの「このことについて」テキストメッセージ | `sales/msrp/explanation_message_whats_this` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ストアフロントのマイアカウントで SKU による並べ替えを有効にする | `sales/product_sku/my_account_enable` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| Enabled | `sales/instant_purchase/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ボタンのテキスト | `sales/instant_purchase/button_text` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顧客グループ | `sales/product_sku/allowed_groups` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| アーカイブを有効にする | `sales/magento_salesarchive/active` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 購入済み注文のアーカイブ | `sales/magento_salesarchive/age` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 注文ステータスをアーカイブ済み | `sales/magento_salesarchive/order_statuses` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| ストアフロントでの RMA の有効化 | `sales/magento_rma/enabled` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 製品レベルで RMA を有効にする | `sales/magento_rma/enabled_on_product` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| ストアアドレスを使用 | `sales/magento_rma/use_store_address` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## 販売 E メールのパス

これらの設定値は、管理者の **Stores**/設定/**Configuration**/**Sales**/**Sales Emails** で使用できます。

| 名前 | 設定パス | Commerceのみ？ |
|--------------|--------------|--------------|
| 非同期送信 | `sales_email/general/async_sending` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `sales_email/order/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文確認メールの送信者 | `sales_email/order/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新規注文確認テンプレート | `sales_email/order/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ゲスト用の新しい注文確認テンプレート | `sales_email/order/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 注文メールのコピー方法を送信 | `sales_email/order/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `sales_email/order_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 注文コメントのメール送信者 | `sales_email/order_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 注文コメントのメールテンプレート | `sales_email/order_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ゲスト用注文コメント E メール テンプレート | `sales_email/order_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 注文コメントのメール送信のコピー方法 | `sales_email/order_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `sales_email/invoice/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 請求書 E メール送信者 | `sales_email/invoice/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 請求書 E メール テンプレート | `sales_email/invoice/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ゲストの請求書 E メール テンプレート | `sales_email/invoice/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 請求書 E メールのコピー方法 | `sales_email/invoice/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `sales_email/invoice_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 請求書コメント E メール送信者 | `sales_email/invoice_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 請求書コメント E メール テンプレート | `sales_email/invoice_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ゲスト宛請求書コメント E メール テンプレート | `sales_email/invoice_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 請求書コメントの E メール・コピー方法 | `sales_email/invoice_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `sales_email/shipment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 出荷電子メールの送信者 | `sales_email/shipment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 出荷 E メール テンプレート | `sales_email/shipment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ゲスト用出荷 E メール テンプレート | `sales_email/shipment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 出荷電子メールのコピー方法の送信 | `sales_email/shipment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `sales_email/shipment_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 出荷コメント E メール送信者 | `sales_email/shipment_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 出荷コメント E メール テンプレート | `sales_email/shipment_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ゲスト用出荷コメント E メール テンプレート | `sales_email/shipment_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 出荷コメントの E メール・コピー方法の送信 | `sales_email/shipment_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `sales_email/creditmemo/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジット メモ E メール送信者 | `sales_email/creditmemo/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットメモのメールテンプレート | `sales_email/creditmemo/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ゲスト用クレジット メモ E メール テンプレート | `sales_email/creditmemo/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジット・メモの E メール・コピー方法の送信 | `sales_email/creditmemo/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `sales_email/creditmemo_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジット メモ コメント メール送信者 | `sales_email/creditmemo_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジット メモ コメント E メール テンプレート | `sales_email/creditmemo_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ゲスト用クレジット メモ コメント E メール テンプレート | `sales_email/creditmemo_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジット・メモ注釈の送信 E メール・コピー方法 | `sales_email/creditmemo_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `sales_email/magento_rma/enabled` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| RMA メール送信者 | `sales_email/magento_rma/identity` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| RMA メールテンプレート | `sales_email/magento_rma/template` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| ゲスト用 RMA メールテンプレート | `sales_email/magento_rma/guest_template` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| RMA メールコピーの送信方法 | `sales_email/magento_rma/copy_method` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| Enabled | `sales_email/magento_rma_auth/enabled` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| RMA 認証メール送信者 | `sales_email/magento_rma_auth/identity` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| RMA 認証メールテンプレート | `sales_email/magento_rma_auth/template` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| ゲスト用 RMA 認証メールテンプレート | `sales_email/magento_rma_auth/guest_template` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| RMA 認証メールのコピー方法を送信 | `sales_email/magento_rma_auth/copy_method` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| Enabled | `sales_email/magento_rma_comment/enabled` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| RMA コメントメール送信者 | `sales_email/magento_rma_comment/identity` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| RMA コメントメールテンプレート | `sales_email/magento_rma_comment/template` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| ゲスト用 RMA コメントメールテンプレート | `sales_email/magento_rma_comment/guest_template` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| RMA メールコピーの送信方法 | `sales_email/magento_rma_comment/copy_method` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| Enabled | `sales_email/magento_rma_customer_comment/enabled` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| RMA コメントメール送信者 | `sales_email/magento_rma_customer_comment/identity` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| RMA コメントの E メール受信者 | `sales_email/magento_rma_customer_comment/recipient` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| RMA コメントメールテンプレート | `sales_email/magento_rma_customer_comment/template` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| RMA メールコピーの送信方法 | `sales_email/magento_rma_customer_comment/copy_method` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| ヘッダーに注文 ID を表示 | `sales_pdf/invoice/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ヘッダーに注文 ID を表示 | `sales_pdf/shipment/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ヘッダーに注文 ID を表示 | `sales_pdf/creditmemo/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 税パス

これらの設定値は、管理者の **Stores**/設定/**Configuration**/**Sales**/**Tax** で使用できます。

| 名前 | 設定パス | Commerceのみ？ |
|--------------|--------------|--------------|
| 配送用の税クラス | `tax/classes/shipping_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ギフト オプションの税クラス | `tax/classes/wrapping_tax_class` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 商品の既定の税クラス | `tax/classes/default_product_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顧客の既定の税クラス | `tax/classes/default_customer_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ～に基づく税額算定方法 | `tax/calculation/algorithm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 基づく税計算 | `tax/calculation/based_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| カタログ価格 | `tax/calculation/price_includes_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送料 | `tax/calculation/shipping_includes_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顧客税の適用 | `tax/calculation/apply_after_discount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 価格割引を適用 | `tax/calculation/discount_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 税金を適用する | `tax/calculation/apply_tax_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 国境を越えた貿易を可能にする | `tax/calculation/cross_border_trade_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デフォルトの国 | `tax/defaults/country` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デフォルトの状態 | `tax/defaults/region` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 既定の Post コード | `tax/defaults/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 製品価格をカタログに表示 | `tax/display/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 配送料を表示 | `tax/display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 価格を表示 | `tax/cart_display/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 小計を表示 | `tax/cart_display/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 配送料を表示 | `tax/cart_display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ギフト包装価格の表示 | `tax/cart_display/gift_wrapping` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 印刷されたカード価格を表示する | `tax/cart_display/printed_card` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 注文合計に税を含める | `tax/cart_display/grandtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 全税概要の表示 | `tax/cart_display/full_summary` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 税の小計ゼロを表示 | `tax/cart_display/zero_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 価格を表示 | `tax/sales_display/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 小計を表示 | `tax/sales_display/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 配送料を表示 | `tax/sales_display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ギフト包装価格の表示 | `tax/sales_display/gift_wrapping` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 印刷されたカード価格を表示する | `tax/sales_display/printed_card` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 注文合計に税を含める | `tax/sales_display/grandtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 全税概要の表示 | `tax/sales_display/full_summary` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 税の小計ゼロを表示 | `tax/sales_display/zero_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| FPT を有効にする | `tax/weee/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 製品リストに価格を表示 | `tax/weee/display_list` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 製品ビューページに価格を表示 | `tax/weee/display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 販売モジュールに価格を表示 | `tax/weee/display_sales` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 価格を E メールで表示 | `tax/weee/display_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| FPT への税の適用 | `tax/weee/apply_vat` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 小計に FPT を含める | `tax/weee/include_in_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## チェックアウトパス

これらの設定値は、管理者の **ストア**/設定/**設定**/**営業**/**チェックアウト** で利用できます。

| 名前 | 設定パス | Commerceのみ？ |
|--------------|--------------|--------------|
| Onepage チェックアウトの有効化 | `checkout/options/onepage_checkout_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ゲストのチェックアウトを許可 | `checkout/options/guest_checkout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 請求先住所を表示 | `checkout/options/display_billing_address_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 利用条件を有効にする | `checkout/options/enable_agreements` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 見積もりの有効期間（日数） | `checkout/cart/delete_quote_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 買い物かごへの製品リダイレクトを追加した後 | `checkout/cart/redirect_to_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| グループ化された製品画像 | `checkout/cart/grouped_product_image` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 設定可能な製品画像 | `checkout/cart/configurable_product_image` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 見積もりの有効期間（分）のプレビュー | `checkout/cart/preview_quota_lifetime` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 買い物かごの概要を表示 | `checkout/cart_link/use_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 買い物かごサイドバーを表示 | `checkout/sidebar/display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最近追加された項目の最大表示数 | `checkout/sidebar/count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払いに失敗したメールの送信者 | `checkout/payment_failed/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払いに失敗した電子メール受信者 | `checkout/payment_failed/receiver` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払いに失敗したテンプレート | `checkout/payment_failed/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払いに失敗した電子メールのコピー方法の送信 | `checkout/payment_failed/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 出荷設定のパス

これらの設定値は、管理者の **Stores**/設定/**Configuration**/**Sales**/**Shipping Settings** で使用できます。

| 名前 | 設定パス | Commerceのみ？ |
|--------------|--------------|--------------|
| カスタム配送ポリシーの適用 | `shipping/shipping_policy/enable_shipping_policy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 配送ポリシー | `shipping/shipping_policy/shipping_policy_content` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 複数出荷設定のパス

これらの設定値は、管理者の **ストア**/設定/**設定**/**営業**/**複数出荷設定** で利用できます。

| 名前 | 設定パス | Commerceのみ？ |
|--------------|--------------|--------------|
| 複数のアドレスへの配送を許可 | `multishipping/options/checkout_multiple` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 複数の住所への配送で許可される最大数量 | `multishipping/options/checkout_multiple_maximum_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 配信方法のパス

これらの設定値は、管理者の **ストア**/設定/**設定**/**営業**/**配信方法** で使用できます。

| 名前 | 設定パス | Commerceのみ？ |
|--------------|--------------|--------------|
| Enabled | `carriers/flatrate/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `carriers/flatrate/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メソッド名 | `carriers/flatrate/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイプ | `carriers/flatrate/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 価格 | `carriers/flatrate/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手数料の計算 | `carriers/flatrate/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手数料 | `carriers/flatrate/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 表示されたエラーメッセージ | `carriers/flatrate/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 適用可能な国に出荷 | `carriers/flatrate/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定の国に出荷 | `carriers/flatrate/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 該当しない場合はメソッドを表示 | `carriers/flatrate/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `carriers/flatrate/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `carriers/freeshipping/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `carriers/freeshipping/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メソッド名 | `carriers/freeshipping/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文金額 | `carriers/freeshipping/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 表示されたエラーメッセージ | `carriers/freeshipping/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 適用可能な国に出荷 | `carriers/freeshipping/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定の国に出荷 | `carriers/freeshipping/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 該当しない場合はメソッドを表示 | `carriers/freeshipping/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `carriers/freeshipping/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enabled | `carriers/tablerate/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `carriers/tablerate/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メソッド名 | `carriers/tablerate/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 条件 | `carriers/tablerate/condition_name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 価格計算に仮想製品を含める | `carriers/tablerate/include_virtual_price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Export | `carriers/tablerate/export` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| インポート | `carriers/tablerate/import` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手数料の計算 | `carriers/tablerate/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手数料 | `carriers/tablerate/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 表示されたエラーメッセージ | `carriers/tablerate/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 適用可能な国に出荷 | `carriers/tablerate/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定の国に出荷 | `carriers/tablerate/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 該当しない場合はメソッドを表示 | `carriers/tablerate/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `carriers/tablerate/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| チェックアウトを有効 | `carriers/ups/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| RMA に対して有効 | `carriers/ups/active_rma` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| UPS タイプ | `carriers/ups/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| モード | `carriers/ups/mode_xml` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 出荷の起源 | `carriers/ups/origin_shipment` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ゲートウェイ URL | `carriers/ups/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `carriers/ups/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 交渉レートを有効にする | `carriers/ups/negotiated_active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パッケージリクエストタイプ | `carriers/ups/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コンテナ | `carriers/ups/container` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 重み単位 | `carriers/ups/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 宛先のタイプ | `carriers/ups/dest_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大パッケージ重量（サポートされている最大出荷重量については、配送業者にお問い合わせください） | `carriers/ups/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ピックアップ方法 | `carriers/ups/pickup` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小パッケージ重量（サポートされている最小出荷重量については、配送業者にお問い合わせください） | `carriers/ups/min_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手数料の計算 | `carriers/ups/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 適用された処理 | `carriers/ups/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手数料 | `carriers/ups/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 許可されるメソッド | `carriers/ups/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自由方法 | `carriers/ups/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送料無料しきい値を有効にする | `carriers/ups/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送料無料の金額のしきい値 | `carriers/ups/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 表示されたエラーメッセージ | `carriers/ups/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 適用可能な国に出荷 | `carriers/ups/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定の国に出荷 | `carriers/ups/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 該当しない場合はメソッドを表示 | `carriers/ups/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `carriers/ups/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| チェックアウトを有効 | `carriers/usps/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| RMA に対して有効 | `carriers/usps/active_rma` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| モード | `carriers/usps/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パッケージリクエストタイプ | `carriers/usps/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コンテナ | `carriers/usps/container` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| サイズ | `carriers/usps/size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 長さ | `carriers/usps/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 幅 | `carriers/usps/width` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 高さ | `carriers/usps/height` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 周囲 | `carriers/usps/girth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 機械加工できる | `carriers/usps/machinable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大パッケージ重量（サポートされている最大出荷重量については、配送業者にお問い合わせください） | `carriers/usps/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手数料の計算 | `carriers/usps/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 適用された処理 | `carriers/usps/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手数料 | `carriers/usps/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 許可されるメソッド | `carriers/usps/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自由方法 | `carriers/usps/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送料無料しきい値を有効にする | `carriers/usps/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送料無料の金額のしきい値 | `carriers/usps/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 表示されたエラーメッセージ | `carriers/usps/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 適用可能な国に出荷 | `carriers/usps/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定の国に出荷 | `carriers/usps/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デバッグ | `carriers/usps/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 該当しない場合はメソッドを表示 | `carriers/usps/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `carriers/usps/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| チェックアウトを有効 | `carriers/fedex/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| RMA に対して有効 | `carriers/fedex/active_rma` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `carriers/fedex/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Web サービス URL （実稼動） | `carriers/fedex/production_webservices_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Web サービス URL （サンドボックス） | `carriers/fedex/sandbox_webservices_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パッケージリクエストタイプ | `carriers/fedex/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 包装 | `carriers/fedex/packaging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ドロップオフ | `carriers/fedex/dropoff` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 重み単位 | `carriers/fedex/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大パッケージ重量（サポートされている最大出荷重量については、配送業者にお問い合わせください） | `carriers/fedex/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手数料の計算 | `carriers/fedex/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 適用された処理 | `carriers/fedex/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手数料 | `carriers/fedex/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 宅配便 | `carriers/fedex/residence_delivery` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 許可されるメソッド | `carriers/fedex/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ハブ ID | `carriers/fedex/smartpost_hubid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自由方法 | `carriers/fedex/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送料無料しきい値を有効にする | `carriers/fedex/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送料無料の金額のしきい値 | `carriers/fedex/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 表示されたエラーメッセージ | `carriers/fedex/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 適用可能な国に出荷 | `carriers/fedex/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定の国に出荷 | `carriers/fedex/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デバッグ | `carriers/fedex/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 該当しない場合はメソッドを表示 | `carriers/fedex/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `carriers/fedex/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| チェックアウトを有効 | `carriers/dhl/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| RMA に対して有効 | `carriers/dhl/active_rma` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `carriers/dhl/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コンテンツタイプ | `carriers/dhl/content_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手数料の計算 | `carriers/dhl/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 適用された処理 | `carriers/dhl/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手数料 | `carriers/dhl/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| オーダーの重み付けの除算 | `carriers/dhl/divide_order_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 重み単位 | `carriers/dhl/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| サイズ | `carriers/dhl/size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 高さ | `carriers/dhl/height` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Depth | `carriers/dhl/depth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 幅 | `carriers/dhl/width` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 許可されるメソッド | `carriers/dhl/doc_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 許可されるメソッド | `carriers/dhl/nondoc_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 準備時間 | `carriers/dhl/ready_time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 表示されたエラーメッセージ | `carriers/dhl/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自由方法 | `carriers/dhl/free_method_doc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自由方法 | `carriers/dhl/free_method_nondoc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送料無料しきい値を有効にする | `carriers/dhl/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送料無料の金額のしきい値 | `carriers/dhl/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 適用可能な国に出荷 | `carriers/dhl/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定の国に出荷 | `carriers/dhl/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 該当しない場合はメソッドを表示 | `carriers/dhl/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順序 | `carriers/dhl/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Google API のパス

これらの設定値は、管理者の **Stores**/設定/**Configuration**/**Sales**/6}Google API **で利用できます。**

| 名前 | 設定パス | Commerceのみ？ |
|--------------|--------------|--------------|
| Enable （有効） | `google/analytics/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| アカウントタイプ | `google/analytics/type` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| コンテンツ実験の有効化 | `google/analytics/experiments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| カタログページのリストプロパティ | `google/analytics/catalog_page_list_value` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| クロスセル ブロックのリストプロパティ | `google/analytics/crosssell_block_list_value` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| アップセル ブロックのリスト プロパティ | `google/analytics/upsell_block_list_value` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 関連製品ブロックのリストプロパティ | `google/analytics/related_block_list_value` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| 検索結果ページのリストプロパティ | `google/analytics/search_page_list_value` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| プロモーションフィールド「ラベル」の「内部プロモーション」。 | `google/analytics/promotions_list_value` | ![Commerceのみ ](/help/assets/configuration/cloud-ee.png) |
| Enable （有効） | `google/adwords/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コンバージョン ID | `google/adwords/conversion_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コンバージョン言語 | `google/adwords/conversion_language` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 変換形式 | `google/adwords/conversion_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 変換カラー | `google/adwords/conversion_color` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コンバージョンラベル | `google/adwords/conversion_label` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コンバージョン値タイプ | `google/adwords/conversion_value_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コンバージョン値 | `google/adwords/conversion_value` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## ギフト カードのパス

これらの設定値は、管理者の **ストア**/設定/**設定**/**セールス**/**ギフトカード** で使用できます。

| 名前 | 設定パス | Commerceのみ？ |
|--------------|--------------|--------------|
| ギフト カード通知メールの送信者 | `giftcard/email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ギフトカード通知メールテンプレート | `giftcard/email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 引換可能 | `giftcard/general/is_redeemable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効期間（日数） | `giftcard/general/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ギフト メッセージを許可 | `giftcard/general/allow_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ギフト メッセージの最大長 | `giftcard/general/message_max_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 注文品目がの場合にギフト カード アカウントを生成 | `giftcard/general/order_item_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ギフト カードの E メール送信者 | `giftcard/giftcardaccount_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ギフト カード テンプレート | `giftcard/giftcardaccount_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コード長 | `giftcard/giftcardaccount_general/code_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コードフォーマット | `giftcard/giftcardaccount_general/code_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コードプレフィックス | `giftcard/giftcardaccount_general/code_prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コードサフィックス | `giftcard/giftcardaccount_general/code_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| X 文字ごとにダッシュ | `giftcard/giftcardaccount_general/code_split` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新しいプールサイズ | `giftcard/giftcardaccount_general/pool_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 低コード プールしきい値 | `giftcard/giftcardaccount_general/pool_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
