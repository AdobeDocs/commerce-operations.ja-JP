---
title: セールス構成パスの参照
description: 販売構成値の一覧を参照してください。
feature: Configuration, Checkout, Gift, Shipping/Delivery, Taxes
exl-id: 7981f78a-5e5f-422c-9bff-54022e1fb9f3
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '1473'
ht-degree: 0%

---

# セールス構成パスの参照

この節では、以下の管理で使用できる変数名と設定パスを示します。 **ストア** /設定/ **設定** > **セールス**.

The [`magento app:config:dump` command](../cli/export-configuration.md) は、これらの値を共有設定ファイルに書き込みます。 `app/etc/config.php`（ソース管理下に置く必要があります） オプションで設定を上書きしたり、機密設定を設定したりするには、 [環境変数を使用して設定を上書きする](override-config-settings.md#environment-variables). このトピックでは、 _not_ リスト [機密性の高いシステム固有の値](config-reference-sens.md).

## 販売パス

これらの設定値は、 **ストア** /設定/ **設定** > **セールス** > **セールス**.

| 名前 | 設定パス | コマースのみ？ |
|--------------|--------------|--------------|
| 顧客 IP を非表示 | `sales/general/hide_customer_ip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 小計 | `sales/totals_sort/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 割引 | `sales/totals_sort/discount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送料 | `sales/totals_sort/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 税 | `sales/totals_sort/tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 固定製品税 | `sales/totals_sort/weee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 総計 | `sales/totals_sort/grand_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ギフトカード | `sales/totals_sort/giftcardaccount` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 店舗クレジット | `sales/totals_sort/customerbalance` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 並べ替えを許可 | `sales/reorder/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PDF印刷アウト用ロゴ (200 x 50) | `sales/identity/logo` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTML印刷表示のロゴ | `sales/identity/logo_html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 住所 | `sales/identity/address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効にする | `sales/minimum_order/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小金額 | `sales/minimum_order/amount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 税額を含む | `sales/minimum_order/tax_including` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 説明メッセージ | `sales/minimum_order/description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 買い物かごに表示するエラー | `sales/minimum_order/error_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 複数アドレスのチェックアウトで各アドレスを個別に検証 | `sales/minimum_order/multi_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 複数アドレスの説明メッセージ | `sales/minimum_order/multi_address_description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 買い物かごに表示する複数アドレスエラー | `sales/minimum_order/multi_address_error_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 集計データを使用 | `sales/dashboard/use_aggregated_data` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払保留中の注文の有効期間（分） | `sales/orders/delete_pending_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 注文レベルでのギフトメッセージを許可 | `sales/gift_options/allow_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 注文項目のギフトメッセージを許可 | `sales/gift_options/allow_items` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 注文レベルでギフト用ラッピングを許可 | `sales/gift_options/wrapping_allow_order` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 注文アイテムのギフト用ラッピングを許可 | `sales/gift_options/wrapping_allow_items` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| ギフトレシートを許可 | `sales/gift_options/allow_gift_receipt` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 印刷済みカードを許可 | `sales/gift_options/allow_printed_card` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 印刷済みカードのデフォルト価格 | `sales/gift_options/printed_card_price` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| MAP を有効にする | `sales/msrp/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 実際の価格を表示 | `sales/msrp/display_price_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デフォルトのポップアップテキストメッセージ | `sales/msrp/explanation_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デフォルトの「What&#39;s This」テキストメッセージ | `sales/msrp/explanation_message_whats_this` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Storefront のマイアカウントで SKU ごとの並べ替えを有効にする | `sales/product_sku/my_account_enable` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 有効 | `sales/instant_purchase/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ボタンのテキスト | `sales/instant_purchase/button_text` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顧客グループ | `sales/product_sku/allowed_groups` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| アーカイブを有効にする | `sales/magento_salesarchive/active` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 購入した注文をアーカイブ | `sales/magento_salesarchive/age` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| アーカイブする注文ステータス | `sales/magento_salesarchive/order_statuses` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| Storefront で RMA を有効にする | `sales/magento_rma/enabled` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 製品レベルでの RMA の有効化 | `sales/magento_rma/enabled_on_product` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| ストアの住所を使用 | `sales/magento_rma/use_store_address` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## セールスメールのパス

これらの設定値は、 **ストア** /設定/ **設定** > **セールス** > **セールスメール**.

| 名前 | 設定パス | コマースのみ？ |
|--------------|--------------|--------------|
| 非同期送信 | `sales_email/general/async_sending` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効 | `sales_email/order/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新しい注文確認メール送信者 | `sales_email/order/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新しい注文確認テンプレート | `sales_email/order/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ゲスト用の新しい注文確認テンプレート | `sales_email/order/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Send Order Email Copy メソッド | `sales_email/order/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効 | `sales_email/order_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 注文コメントメール送信者 | `sales_email/order_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 注文コメントメールテンプレート | `sales_email/order_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ゲスト用のコメントメールテンプレートを注文 | `sales_email/order_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 注文コメントメールコピーメソッドの送信 | `sales_email/order_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効 | `sales_email/invoice/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 請求書メール送信者 | `sales_email/invoice/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 請求書メールテンプレート | `sales_email/invoice/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ゲスト用の請求書メールテンプレート | `sales_email/invoice/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 請求書メールコピー方法の送信 | `sales_email/invoice/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効 | `sales_email/invoice_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 請求書コメントメール送信者 | `sales_email/invoice_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 請求書コメントメールテンプレート | `sales_email/invoice_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ゲスト用の請求書コメントメールテンプレート | `sales_email/invoice_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 請求書コメントの送信メールのコピー方法 | `sales_email/invoice_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効 | `sales_email/shipment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 出荷メール送信者 | `sales_email/shipment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 出荷メールテンプレート | `sales_email/shipment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ゲスト用の出荷メールテンプレート | `sales_email/shipment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 発送メールのコピー方法の送信 | `sales_email/shipment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効 | `sales_email/shipment_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 出荷コメントメール送信者 | `sales_email/shipment_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 出荷コメントメールテンプレート | `sales_email/shipment_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ゲスト用の出荷コメントメールテンプレート | `sales_email/shipment_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 出荷コメントのメールコピー方法の送信 | `sales_email/shipment_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効 | `sales_email/creditmemo/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットメモメール送信者 | `sales_email/creditmemo/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットメモ電子メールテンプレート | `sales_email/creditmemo/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ゲスト用クレジットメモメールテンプレート | `sales_email/creditmemo/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジット・メモの電子メール・コピー・メソッドの送信 | `sales_email/creditmemo/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効 | `sales_email/creditmemo_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットメモコメントメール送信者 | `sales_email/creditmemo_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジットメモコメントの電子メールテンプレート | `sales_email/creditmemo_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ゲスト用クレジットメモコメントメールテンプレート | `sales_email/creditmemo_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クレジット・メモ注釈の送信電子メール・コピー・メソッド | `sales_email/creditmemo_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効 | `sales_email/magento_rma/enabled` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| RMA E メール送信者 | `sales_email/magento_rma/identity` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| RMA 電子メールテンプレート | `sales_email/magento_rma/template` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| ゲスト用の RMA 電子メールテンプレート | `sales_email/magento_rma/guest_template` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| RMA E メール・コピー・メソッドの送信 | `sales_email/magento_rma/copy_method` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 有効 | `sales_email/magento_rma_auth/enabled` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| RMA 承認 E メール送信者 | `sales_email/magento_rma_auth/identity` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| RMA 承認電子メールテンプレート | `sales_email/magento_rma_auth/template` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| ゲスト用の RMA 承認メールテンプレート | `sales_email/magento_rma_auth/guest_template` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| RMA 認証 E メール・コピー・メソッドの送信 | `sales_email/magento_rma_auth/copy_method` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 有効 | `sales_email/magento_rma_comment/enabled` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| RMA コメント E メール送信者 | `sales_email/magento_rma_comment/identity` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| RMA コメント電子メールテンプレート | `sales_email/magento_rma_comment/template` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| ゲスト用 RMA コメント電子メールテンプレート | `sales_email/magento_rma_comment/guest_template` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| RMA E メール・コピー・メソッドの送信 | `sales_email/magento_rma_comment/copy_method` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 有効 | `sales_email/magento_rma_customer_comment/enabled` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| RMA コメント E メール送信者 | `sales_email/magento_rma_customer_comment/identity` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| RMA コメントの電子メール受信者 | `sales_email/magento_rma_customer_comment/recipient` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| RMA コメント電子メールテンプレート | `sales_email/magento_rma_customer_comment/template` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| RMA E メール・コピー・メソッドの送信 | `sales_email/magento_rma_customer_comment/copy_method` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| ヘッダーに注文 ID を表示 | `sales_pdf/invoice/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ヘッダーに注文 ID を表示 | `sales_pdf/shipment/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ヘッダーに注文 ID を表示 | `sales_pdf/creditmemo/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 税パス

これらの設定値は、 **ストア** /設定/ **設定** > **セールス** > **税**.

| 名前 | 設定パス | コマースのみ？ |
|--------------|--------------|--------------|
| 輸送用税区分 | `tax/classes/shipping_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 贈与オプションの税区分 | `tax/classes/wrapping_tax_class` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 製品のデフォルト税区分 | `tax/classes/default_product_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顧客のデフォルト税区分 | `tax/classes/default_customer_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 次に基づく税金計算方法 | `tax/calculation/algorithm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 次に基づく税の計算 | `tax/calculation/based_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| カタログ価格 | `tax/calculation/price_includes_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送料 | `tax/calculation/shipping_includes_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 顧客税の適用 | `tax/calculation/apply_after_discount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 価格に対する割引の適用 | `tax/calculation/discount_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 税金を適用する | `tax/calculation/apply_tax_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 国境を越えた貿易を有効にする | `tax/calculation/cross_border_trade_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デフォルトの国 | `tax/defaults/country` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デフォルトの状態 | `tax/defaults/region` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デフォルトの Post コード | `tax/defaults/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| カタログに商品価格を表示 | `tax/display/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送料の表示 | `tax/display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 価格を表示 | `tax/cart_display/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 小計を表示 | `tax/cart_display/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送料の表示 | `tax/cart_display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ギフト用ラッピング価格を表示 | `tax/cart_display/gift_wrapping` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 印刷されたカードの価格を表示 | `tax/cart_display/printed_card` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 税を注文合計に含める | `tax/cart_display/grandtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 全税金要約の表示 | `tax/cart_display/full_summary` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ゼロ税金小計の表示 | `tax/cart_display/zero_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 価格を表示 | `tax/sales_display/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 小計を表示 | `tax/sales_display/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送料の表示 | `tax/sales_display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ギフト用ラッピング価格を表示 | `tax/sales_display/gift_wrapping` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 印刷されたカードの価格を表示 | `tax/sales_display/printed_card` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 税を注文合計に含める | `tax/sales_display/grandtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 全税金要約の表示 | `tax/sales_display/full_summary` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ゼロ税金小計の表示 | `tax/sales_display/zero_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| FPT を有効にする | `tax/weee/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 製品リストに価格を表示 | `tax/weee/display_list` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 製品表示ページに価格を表示 | `tax/weee/display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 販売モジュールの価格を表示 | `tax/weee/display_sales` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メールでの価格の表示 | `tax/weee/display_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 税金を FPT に適用 | `tax/weee/apply_vat` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| FPT を小計に含める | `tax/weee/include_in_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## チェックアウトパス

これらの設定値は、 **ストア** /設定/ **設定** > **セールス** > **チェックアウト**.

| 名前 | 設定パス | コマースのみ？ |
|--------------|--------------|--------------|
| オンページチェックアウトの有効化 | `checkout/options/onepage_checkout_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ゲストによるチェックアウトを許可 | `checkout/options/guest_checkout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 請求先住所を次の日に表示： | `checkout/options/display_billing_address_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 利用条件を有効にする | `checkout/options/enable_agreements` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 見積もりの有効期間（日数） | `checkout/cart/delete_quote_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 買い物かごへの製品リダイレクトの追加後 | `checkout/cart/redirect_to_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| グループ化された製品画像 | `checkout/cart/grouped_product_image` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 設定可能な製品イメージ | `checkout/cart/configurable_product_image` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 見積もりの有効期間（分）をプレビュー | `checkout/cart/preview_quota_lifetime` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 買い物かごの概要を表示 | `checkout/cart_link/use_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 買い物かごのサイドバーを表示 | `checkout/sidebar/display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最近追加された項目の最大表示数 | `checkout/sidebar/count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払いに失敗したメール送信者 | `checkout/payment_failed/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払い失敗メール受信者 | `checkout/payment_failed/receiver` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払い失敗テンプレート | `checkout/payment_failed/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 支払い失敗メールコピー方法の送信 | `checkout/payment_failed/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 配送設定のパス

これらの設定値は、 **ストア** /設定/ **設定** > **セールス** > **発送設定**.

| 名前 | 設定パス | コマースのみ？ |
|--------------|--------------|--------------|
| カスタム発送ポリシーの適用 | `shipping/shipping_policy/enable_shipping_policy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 発送ポリシー | `shipping/shipping_policy/shipping_policy_content` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 複数配送設定のパス

これらの設定値は、 **ストア** /設定/ **設定** > **セールス** > **複数配送設定**.

| 名前 | 設定パス | コマースのみ？ |
|--------------|--------------|--------------|
| 複数の住所への発送を許可 | `multishipping/options/checkout_multiple` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 複数の住所への出荷に許可される最大数量 | `multishipping/options/checkout_multiple_maximum_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## 配信メソッドのパス

これらの設定値は、 **ストア** /設定/ **設定** > **セールス** > **配信方法**.

| 名前 | 設定パス | コマースのみ？ |
|--------------|--------------|--------------|
| 有効 | `carriers/flatrate/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `carriers/flatrate/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メソッド名 | `carriers/flatrate/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイプ | `carriers/flatrate/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 価格 | `carriers/flatrate/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 処理費の計算 | `carriers/flatrate/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手数料 | `carriers/flatrate/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 表示されたエラーメッセージ | `carriers/flatrate/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 該当国への出荷 | `carriers/flatrate/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定の国に出荷 | `carriers/flatrate/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 該当しない場合はメソッドを表示 | `carriers/flatrate/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順 | `carriers/flatrate/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効 | `carriers/freeshipping/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `carriers/freeshipping/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メソッド名 | `carriers/freeshipping/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小注文額 | `carriers/freeshipping/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 表示されたエラーメッセージ | `carriers/freeshipping/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 該当国への出荷 | `carriers/freeshipping/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定の国に出荷 | `carriers/freeshipping/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 該当しない場合はメソッドを表示 | `carriers/freeshipping/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順 | `carriers/freeshipping/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効 | `carriers/tablerate/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `carriers/tablerate/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| メソッド名 | `carriers/tablerate/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 条件 | `carriers/tablerate/condition_name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 価格計算に仮想製品を含める | `carriers/tablerate/include_virtual_price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 書き出し | `carriers/tablerate/export` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| インポート | `carriers/tablerate/import` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 処理費の計算 | `carriers/tablerate/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手数料 | `carriers/tablerate/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 表示されたエラーメッセージ | `carriers/tablerate/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 該当国への出荷 | `carriers/tablerate/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定の国に出荷 | `carriers/tablerate/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 該当しない場合はメソッドを表示 | `carriers/tablerate/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順 | `carriers/tablerate/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| チェックアウトに対して有効 | `carriers/ups/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| RMA に対して有効 | `carriers/ups/active_rma` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| UPS タイプ | `carriers/ups/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| モード | `carriers/ups/mode_xml` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 出荷元 | `carriers/ups/origin_shipment` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ゲートウェイ URL | `carriers/ups/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| タイトル | `carriers/ups/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ネゴシエートされたレートを有効にする | `carriers/ups/negotiated_active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パッケージのリクエストタイプ | `carriers/ups/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コンテナ | `carriers/ups/container` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 重み付け単位 | `carriers/ups/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 宛先のタイプ | `carriers/ups/dest_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大パッケージ重み（サポートされる最大配送量については、配送業者にお問い合わせください） | `carriers/ups/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ピックアップ方法 | `carriers/ups/pickup` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最小パッケージ重み（サポートされる最小出荷重みについては、配送業者にお問い合わせください） | `carriers/ups/min_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 処理費の計算 | `carriers/ups/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 適用された処理 | `carriers/ups/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手数料 | `carriers/ups/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 許可されるメソッド | `carriers/ups/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自由方式 | `carriers/ups/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送料無料しきい値の有効化 | `carriers/ups/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送料の無料しきい値 | `carriers/ups/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 表示されたエラーメッセージ | `carriers/ups/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 該当国への出荷 | `carriers/ups/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定の国に出荷 | `carriers/ups/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 該当しない場合はメソッドを表示 | `carriers/ups/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順 | `carriers/ups/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| チェックアウトに対して有効 | `carriers/usps/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| RMA に対して有効 | `carriers/usps/active_rma` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| モード | `carriers/usps/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パッケージのリクエストタイプ | `carriers/usps/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コンテナ | `carriers/usps/container` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| サイズ | `carriers/usps/size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 長さ | `carriers/usps/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 幅 | `carriers/usps/width` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 高さ | `carriers/usps/height` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ガース | `carriers/usps/girth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 被削可能 | `carriers/usps/machinable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大パッケージ重み（サポートされる最大配送量については、配送業者にお問い合わせください） | `carriers/usps/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 処理費の計算 | `carriers/usps/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 適用された処理 | `carriers/usps/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手数料 | `carriers/usps/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 許可されるメソッド | `carriers/usps/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自由方式 | `carriers/usps/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送料無料しきい値の有効化 | `carriers/usps/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送料の無料しきい値 | `carriers/usps/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 表示されたエラーメッセージ | `carriers/usps/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 該当国への出荷 | `carriers/usps/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定の国に出荷 | `carriers/usps/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デバッグ | `carriers/usps/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 該当しない場合はメソッドを表示 | `carriers/usps/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順 | `carriers/usps/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| チェックアウトに対して有効 | `carriers/fedex/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| RMA に対して有効 | `carriers/fedex/active_rma` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `carriers/fedex/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Web サービス URL （実稼動） | `carriers/fedex/production_webservices_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Web サービス URL （サンドボックス） | `carriers/fedex/sandbox_webservices_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パッケージのリクエストタイプ | `carriers/fedex/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| パッケージ | `carriers/fedex/packaging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ドロップオフ | `carriers/fedex/dropoff` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 重み付け単位 | `carriers/fedex/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 最大パッケージ重み（サポートされる最大配送量については、配送業者にお問い合わせください） | `carriers/fedex/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 処理費の計算 | `carriers/fedex/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 適用された処理 | `carriers/fedex/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手数料 | `carriers/fedex/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 住宅配送 | `carriers/fedex/residence_delivery` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 許可されるメソッド | `carriers/fedex/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ハブ ID | `carriers/fedex/smartpost_hubid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自由方式 | `carriers/fedex/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送料無料しきい値の有効化 | `carriers/fedex/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送料の無料しきい値 | `carriers/fedex/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 表示されたエラーメッセージ | `carriers/fedex/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 該当国への出荷 | `carriers/fedex/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定の国に出荷 | `carriers/fedex/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| デバッグ | `carriers/fedex/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 該当しない場合はメソッドを表示 | `carriers/fedex/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順 | `carriers/fedex/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| チェックアウトに対して有効 | `carriers/dhl/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| RMA に対して有効 | `carriers/dhl/active_rma` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| タイトル | `carriers/dhl/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コンテンツタイプ | `carriers/dhl/content_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 処理費の計算 | `carriers/dhl/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 適用された処理 | `carriers/dhl/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 手数料 | `carriers/dhl/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 重み付けを除算 | `carriers/dhl/divide_order_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 重み付け単位 | `carriers/dhl/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| サイズ | `carriers/dhl/size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 高さ | `carriers/dhl/height` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 深さ | `carriers/dhl/depth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 幅 | `carriers/dhl/width` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 許可されるメソッド | `carriers/dhl/doc_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 許可されるメソッド | `carriers/dhl/nondoc_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 準備完了時間 | `carriers/dhl/ready_time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 表示されたエラーメッセージ | `carriers/dhl/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自由方式 | `carriers/dhl/free_method_doc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 自由方式 | `carriers/dhl/free_method_nondoc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送料無料しきい値の有効化 | `carriers/dhl/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 送料の無料しきい値 | `carriers/dhl/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 該当国への出荷 | `carriers/dhl/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 特定の国に出荷 | `carriers/dhl/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 該当しない場合はメソッドを表示 | `carriers/dhl/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 並べ替え順 | `carriers/dhl/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Google API パス

これらの設定値は、 **ストア** /設定/ **設定** > **セールス** > **Google API**.

| 名前 | 設定パス | コマースのみ？ |
|--------------|--------------|--------------|
| 有効にする | `google/analytics/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| アカウントタイプ | `google/analytics/type` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| Content Experiment を有効にする | `google/analytics/experiments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| カタログページのリストプロパティ | `google/analytics/catalog_page_list_value` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| クロス販売ブロックのリストプロパティ | `google/analytics/crosssell_block_list_value` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| アップセルブロックのリストプロパティ | `google/analytics/upsell_block_list_value` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 関連製品ブロックのリストプロパティ | `google/analytics/related_block_list_value` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 検索結果ページのリストプロパティ | `google/analytics/search_page_list_value` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 「内部プロモーション」（プロモーションフィールド「ラベル」）。 | `google/analytics/promotions_list_value` | ![コマースのみ](/help/assets/configuration/cloud-ee.png) |
| 有効にする | `google/adwords/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コンバージョン ID | `google/adwords/conversion_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コンバージョン言語 | `google/adwords/conversion_language` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 変換形式 | `google/adwords/conversion_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 変換カラー | `google/adwords/conversion_color` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コンバージョンラベル | `google/adwords/conversion_label` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コンバージョン値のタイプ | `google/adwords/conversion_value_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コンバージョン値 | `google/adwords/conversion_value` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## ギフトカードのパス

これらの設定値は、 **ストア** /設定/ **設定** > **セールス** > **ギフトカード**.

| 名前 | 設定パス | コマースのみ？ |
|--------------|--------------|--------------|
| ギフトカード通知メール送信者 | `giftcard/email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ギフトカード通知メールテンプレート | `giftcard/email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 取り消し可能 | `giftcard/general/is_redeemable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 全期間（日数） | `giftcard/general/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ギフトメッセージを許可 | `giftcard/general/allow_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ギフトメッセージの最大長 | `giftcard/general/message_max_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 注文項目が次の場合にギフトカードアカウントを生成 | `giftcard/general/order_item_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ギフトカードの E メール送信者 | `giftcard/giftcardaccount_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ギフトカードテンプレート | `giftcard/giftcardaccount_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コードの長さ | `giftcard/giftcardaccount_general/code_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コード形式 | `giftcard/giftcardaccount_general/code_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コードプレフィックス | `giftcard/giftcardaccount_general/code_prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| コードサフィックス | `giftcard/giftcardaccount_general/code_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| X 文字ごとにダッシュ | `giftcard/giftcardaccount_general/code_split` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 新しいプールサイズ | `giftcard/giftcardaccount_general/pool_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 低コードプールしきい値 | `giftcard/giftcardaccount_general/pool_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
