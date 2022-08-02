---
title: B2B 拡張機能の設定パスの参照
description: B2B 関連の設定値の一覧を参照してください。
source-git-commit: ee2e446edf79efcd7cbbd67248f8e7ece06bfefd
workflow-type: tm+mt
source-wordcount: '859'
ht-degree: 0%

---


# B2B 拡張機能の設定パスの参照

_これは、Adobe Commerce用 B2B がインストールされているインスタンスで使用できます。_

このトピックでは、Commerce Enterprise B2B 拡張機能の設定パスを示します。 この [`magento app:config:dump` command](../cli/export-configuration.md) は、これらの値を共有設定ファイルに書き込みます。 `app/etc/config.php`（ソース管理下に置く必要があります）

>[!INFO]
>
>このリファレンスリスト _のみ_ Adobe Commerceの B2B に固有の設定パス。 この拡張機能には、Adobe Commerceのすべての設定パスが含まれます。

これらの設定パスについては、次を参照してください。

- [支払い設定パス](config-reference-payment.md)
- [機密性の高いシステム固有の設定パスの参照](config-reference-sens.md)

オプションで設定を上書きしたり、機密設定を設定したりするには、 [環境変数を使用して設定を上書きする](override-config-settings.md#environment-variables).

## 一般カテゴリ

この節では、以下の管理で使用できる変数名と設定パスを示します。 **[!UICONTROL Stores]** /設定/ **[!UICONTROL Configuration]** > **[!UICONTROL General]**.

### B2B 機能パス

これらの設定値は、 **[!UICONTROL Stores]** /設定/ **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.

| 名前 | 設定パス | 暗号化？ | システム固有？ | 敏感？ |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| 会社を有効にする | `btob/website_configuration/company_active` |  |  |  |
| 共有カタログを有効にする | `btob/website_configuration/sharedcatalog_active` |  |  |  |
| B2B 見積もりの有効化 | `btob/website_configuration/negotiablequote_active` |  |  |  |
| クイックオーダーを有効にする | `btob/website_configuration/quickorder_active` |  |  |  |
| 購買依頼リストの有効化 | `btob/website_configuration/requisition_list_active` |  |  |  |
| 該当する支払い方法 | `btob/default_b2b_payment_methods/applicable_payment_methods` |  |  |  |
| 支払い方法 | `btob/default_b2b_payment_methods/available_payment_methods` |  |  |  |

{style=&quot;table-layout:auto&quot;}

## 顧客カテゴリ

この節では、以下の管理で使用できる変数名と設定パスを示します。 **[!UICONTROL Stores]** /設定/ **[!UICONTROL Configuration]** > **[!UICONTROL Customers]**.

### 会社の設定パス

これらの設定値は、 **[!UICONTROL Stores]** /設定/ **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Company Configuration]**.

| 名前 | 設定パス | 暗号化？ | システム固有？ | 敏感？ |
|--------------|--------------|--------------|--------------|--------------|
| ストアフロントからの会社登録を許可 | `company/general/allow_company_registration` |  |  |  |
| 会社登録メールの受信者 | `company/email/company_registration` |  |  | ![機密](/help/assets/configuration/cloud-sens.png) |
| 会社登録メールコピーの送信先 | `company/email/company_registration_copy` |  |  | ![機密](/help/assets/configuration/cloud-sens.png) |
| Send Email Copy メソッド | `company/email/company_copy_method` |  |  |  |
| デフォルトの会社登録メール | `company/email/company_notify_admin_template` |  |  |  |
| 顧客関連メール | `company/email/heading_customer` |  |  |  |
| デフォルトのセールス担当者割り当てメール | `company/email/customer_sales_representative_template` |  |  |  |
| 顧客メールに会社をデフォルトで割り当て | `company/email/customer_company_customer_assign_template` |  |  |  |
| デフォルトの会社管理者メールの割り当て | `company/email/customer_assign_super_user_template` |  |  |  |
| デフォルトの会社管理非アクティブメール | `company/email/customer_inactivate_super_user_template` |  |  |  |
| デフォルトの会社管理者がメンバーメールに変更されました | `company/email/customer_remove_super_user_template` |  |  |  |
| デフォルトの顧客ステータスアクティブメール | `company/email/customer_account_activated_template` |  |  |  |
| デフォルトの顧客ステータス非アクティブメール | `company/email/customer_account_locked_template` |  |  |  |
| 会社ステータスの変更 | `company/email/heading_company_status` |  |  |  |
| 会社ステータス変更メールの受信者 | `company/email/company_status_change` |  |  |  |
| 会社ステータス変更メールコピーの送信先 | `company/email/company_status_change_copy` |  |  | ![機密](/help/assets/configuration/cloud-sens.png) |
| Send Email Copy メソッド | `company/email/company_status_copy_method` |  |  |  |
| デフォルトの会社ステータスがアクティブな 1 件のメールに変更されました | `company/email/company_status_pending_approval_to_active_template` |  |  |  |
| デフォルトの会社ステータスがアクティブな 2 件のメールに変更されました | `company/email/company_status_rejected_blocked_to_active_template` |  |  |  |
| デフォルトの会社ステータスの変更が却下されたメールに変更されました | `company/email/company_status_rejected_template` |  |  |  |
| デフォルトの会社ステータスがブロック済みメールに変更されました | `company/email/company_status_blocked_template` |  |  |  |
| デフォルトの会社ステータスが承認待ちメールに変更されました | `company/email/company_status_pending_approval_template` |  |  |  |
| 会社クレジット | `company/email/heading_company_credit` |  |  |  |
| 会社のクレジット変更メール送信者 | `company/email/company_credit_change` |  |  | ![機密](/help/assets/configuration/cloud-sens.png) |
| 会社クレジット変更メールコピーの送信先 | `company/email/company_credit_change_copy` |  |  |  |
| Send Email Copy メソッド | `company/email/company_credit_copy_method` |  |  |  |
| 割り当て済みメールテンプレート | `company/email/credit_allocated_email_template` |  |  |  |
| 更新されたメールテンプレート | `company/email/credit_updated_email_template` |  |  |  |
| 返金済みメールテンプレート | `company/email/credit_reimbursed_email_template` |  |  |  |
| 返金済みメールテンプレート | `company/email/credit_refunded_email_template` |  |  |  |
| 元に戻されたメールテンプレート | `company/email/credit_reverted_email_template` |  |  |  |

{style=&quot;table-layout:auto&quot;}

### 購買依頼リストのパス

これらの設定値は、 **ストア** /設定/ **設定** > **顧客** > **購買依頼リスト**.

| 名前 | 設定パス | 暗号化？ | システム固有？ | 敏感？ |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| 購買依頼リストの数 | `requisitionlist/general/number_requisition_lists` |  |  |  |

{style=&quot;table-layout:auto&quot;}

## 販売カテゴリ

この節では、以下の管理で使用できる変数名と設定パスを示します。 **ストア** /設定/ **設定** > **セールス**.

### セールスメールのパス

これらの設定値は、 **ストア** /設定/ **設定** > **セールス** > **セールスメール**.

| 名前 | 設定パス | 暗号化？ | システム固有？ | 敏感？ |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| 有効 | `sales_email/quote/enabled` |  |  |  |
| （購入者に対する）更新済みの見積テンプレート | `sales_email/quote/updated_buyer_template` |  |  |  |
| 拒否された見積もりテンプレート（購入者へ） | `sales_email/quote/declined_buyer_template` |  |  |  |
| 新規見積もりテンプレート（販売者へ） | `sales_email/quote/new_seller_template` |  |  |  |
| 更新された見積もりテンプレート（販売者へ） | `sales_email/quote/updated_seller_template` |  |  |  |
| 見積もりの有効期限（48 時間） | `sales_email/quote/expire_two_days_template` |  |  |  |
| 見積もりの有効期限（24 時間） | `sales_email/quote/expire_one_day_template` |  |  |  |
| 有効期限のリセット | `sales_email/quote/expire_reset_template` |  |  |  |
| 見積もりメールのコピーの送信先 | `sales_email/quote/copy_to` |  |  | ![機密](/help/assets/configuration/cloud-sens.png) |
| 見積もりのメールコピー方法の送信 | `sales_email/quote/copy_method` |  |  |  |

{style=&quot;table-layout:auto&quot;}

### パスを引用符で囲む

これらの設定値は、 **ストア** /設定/ **設定** > **セールス** > **引用符**.

| 名前 | 設定パス | 暗号化？ | システム固有？ | 敏感？ |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| 最小金額 | `quote/general/minimum_amount` |  |  |  |
| 最小金額メッセージ | `quote/general/minimum_amount_message` |  |  |  |
| デフォルトの有効期限 | `quote/general/default_expiration_period` |  |  |  |
| アップロード用のファイル形式 | `quote/attached_files/file_formats` |  |  |  |
| 最大ファイルサイズ | `quote/attached_files/maximum_file_size` |  |  |  |
| 最小金額 | `quote/general/minimum_amount` |  |  |  |
| 最小金額メッセージ | `quote/general/minimum_amount_message` |  |  |  |
| デフォルトの有効期限 | `quote/general/default_expiration_period` |  |  |  |
| アップロード用のファイル形式 | `quote/attached_files/file_formats` |  |  |  |
| 最大ファイルサイズ | `quote/attached_files/maximum_file_size` |  |  |  |

{style=&quot;table-layout:auto&quot;}

## 支払い方法のパス

これらの設定値は、 **ストア** /設定/ **設定** > **セールス** > **支払い方法**.

>[!INFO]
>
>使用可能なパスは、マーチャントの国を選択して決定します。

| 名前 | 設定パス | 暗号化？ | システム固有？ | 敏感？ |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| 有効 | `payment/au/companycredit/active` |  |  |  |
| タイトル | `payment/au/companycredit/title` |  |  |  |
| 新しい注文ステータス | `payment/au/companycredit/order_status` |  |  |  |
| 該当国からの支払 | `payment/au/companycredit/allowspecific` |  |  |  |
| 特定の国からの支払い | `payment/au/companycredit/specificcountry` |  |  |  |
| 最小注文合計 | `payment/au/companycredit/min_order_total` |  |  |  |
| 最大注文合計 | `payment/au/companycredit/max_order_total` |  |  |  |
| 並べ替え順 | `payment/au/companycredit/sort_order` |  |  |  |
| 有効 | `payment/es/companycredit/active` |  |  |  |
| タイトル | `payment/es/companycredit/title` |  |  |  |
| 新しい注文ステータス | `payment/es/companycredit/order_status` |  |  |  |
| 該当国からの支払 | `payment/es/companycredit/allowspecific` |  |  |  |
| 特定の国からの支払い | `payment/es/companycredit/specificcountry` |  |  |  |
| 最小注文合計 | `payment/es/companycredit/min_order_total` |  |  |  |
| 最大注文合計 | `payment/es/companycredit/max_order_total` |  |  |  |
| 並べ替え順 | `payment/es/companycredit/sort_order` |  |  |  |
| 有効 | `payment/companycredit/active` |  |  |  |
| タイトル | `payment/companycredit/title` |  |  |  |
| 新しい注文ステータス | `payment/companycredit/order_status` |  |  |  |
| 該当国からの支払 | `payment/companycredit/allowspecific` |  |  |  |
| 特定の国からの支払い | `payment/companycredit/specificcountry` |  |  |  |
| 最小注文合計 | `payment/companycredit/min_order_total` |  |  |  |
| 最大注文合計 | `payment/companycredit/max_order_total` |  |  |  |
| 並べ替え順 | `payment/companycredit/sort_order` |  |  |  |
| 有効 | `payment/nz/companycredit/active` |  |  |  |
| タイトル | `payment/nz/companycredit/title` |  |  |  |
| 新しい注文ステータス | `payment/nz/companycredit/order_status` |  |  |  |
| 該当国からの支払 | `payment/nz/companycredit/allowspecific` |  |  |  |
| 特定の国からの支払い | `payment/nz/companycredit/specificcountry` |  |  |  |
| 最小注文合計 | `payment/nz/companycredit/min_order_total` |  |  |  |
| 最大注文合計 | `payment/nz/companycredit/max_order_total` |  |  |  |
| 並べ替え順 | `payment/nz/companycredit/sort_order` |  |  |  |
| 有効 | `payment/us/companycredit/active` |  |  |  |
| タイトル | `payment/us/companycredit/title` |  |  |  |
| 新しい注文ステータス | `payment/us/companycredit/order_status` |  |  |  |
| 該当国からの支払 | `payment/us/companycredit/allowspecific` |  |  |  |
| 特定の国からの支払い | `payment/us/companycredit/specificcountry` |  |  |  |
| 最小注文合計 | `payment/us/companycredit/min_order_total` |  |  |  |
| 最大注文合計 | `payment/us/companycredit/max_order_total` |  |  |  |
| 並べ替え順 | `payment/us/companycredit/sort_order` |  |  |  |
| 有効 | `payment/gb/companycredit/active` |  |  |  |
| タイトル | `payment/gb/companycredit/title` |  |  |  |
| 新しい注文ステータス | `payment/gb/companycredit/order_status` |  |  |  |
| 該当国からの支払 | `payment/gb/companycredit/allowspecific` |  |  |  |
| 特定の国からの支払い | `payment/gb/companycredit/specificcountry` |  |  |  |
| 最小注文合計 | `payment/gb/companycredit/min_order_total` |  |  |  |
| 最大注文合計 | `payment/gb/companycredit/max_order_total` |  |  |  |
| 並べ替え順 | `payment/gb/companycredit/sort_order` |  |  |  |
| 有効 | `payment/de/companycredit/active` |  |  |  |
| タイトル | `payment/de/companycredit/title` |  |  |  |
| 新しい注文ステータス | `payment/de/companycredit/order_status` |  |  |  |
| 該当国からの支払 | `payment/de/companycredit/allowspecific` |  |  |  |
| 特定の国からの支払い | `payment/de/companycredit/specificcountry` |  |  |  |
| 最小注文合計 | `payment/de/companycredit/min_order_total` |  |  |  |
| 最大注文合計 | `payment/de/companycredit/max_order_total` |  |  |  |
| 並べ替え順 | `payment/de/companycredit/sort_order` |  |  |  |
| 有効 | `payment/other/companycredit/active` |  |  |  |
| タイトル | `payment/other/companycredit/title` |  |  |  |
| 新しい注文ステータス | `payment/other/companycredit/order_status` |  |  |  |
| 該当国からの支払 | `payment/other/companycredit/allowspecific` |  |  |  |
| 特定の国からの支払い | `payment/other/companycredit/specificcountry` |  |  |  |
| 最小注文合計 | `payment/other/companycredit/min_order_total` |  |  |  |
| 最大注文合計 | `payment/other/companycredit/max_order_total` |  |  |  |
| 並べ替え順 | `payment/other/companycredit/sort_order` |  |  |  |
| 有効 | `payment/ca/companycredit/active` |  |  |  |
| タイトル | `payment/ca/companycredit/title` |  |  |  |
| 新しい注文ステータス | `payment/ca/companycredit/order_status` |  |  |  |
| 該当国からの支払 | `payment/ca/companycredit/allowspecific` |  |  |  |
| 特定の国からの支払い | `payment/ca/companycredit/specificcountry` |  |  |  |
| 最小注文合計 | `payment/ca/companycredit/min_order_total` |  |  |  |
| 最大注文合計 | `payment/ca/companycredit/max_order_total` |  |  |  |
| 並べ替え順 | `payment/ca/companycredit/sort_order` |  |  |  |
| 有効 | `payment/hk/companycredit/active` |  |  |  |
| タイトル | `payment/hk/companycredit/title` |  |  |  |
| 新しい注文ステータス | `payment/hk/companycredit/order_status` |  |  |  |
| 該当国からの支払 | `payment/hk/companycredit/allowspecific` |  |  |  |
| 特定の国からの支払い | `payment/hk/companycredit/specificcountry` |  |  |  |
| 最小注文合計 | `payment/hk/companycredit/min_order_total` |  |  |  |
| 最大注文合計 | `payment/hk/companycredit/max_order_total` |  |  |  |
| 並べ替え順 | `payment/hk/companycredit/sort_order` |  |  |  |
| 有効 | `payment/jp/companycredit/active` |  |  |  |
| タイトル | `payment/jp/companycredit/title` |  |  |  |
| 新しい注文ステータス | `payment/jp/companycredit/order_status` |  |  |  |
| 該当国からの支払 | `payment/jp/companycredit/allowspecific` |  |  |  |
| 特定の国からの支払い | `payment/jp/companycredit/specificcountry` |  |  |  |
| 最小注文合計 | `payment/jp/companycredit/min_order_total` |  |  |  |
| 最大注文合計 | `payment/jp/companycredit/max_order_total` |  |  |  |
| 並べ替え順 | `payment/jp/companycredit/sort_order` |  |  |  |
| 有効 | `payment/fr/companycredit/active` |  |  |  |
| タイトル | `payment/fr/companycredit/title` |  |  |  |
| 新しい注文ステータス | `payment/fr/companycredit/order_status` |  |  |  |
| 該当国からの支払 | `payment/fr/companycredit/allowspecific` |  |  |  |
| 特定の国からの支払い | `payment/fr/companycredit/specificcountry` |  |  |  |
| 最小注文合計 | `payment/fr/companycredit/min_order_total` |  |  |  |
| 最大注文合計 | `payment/fr/companycredit/max_order_total` |  |  |  |
| 並べ替え順 | `payment/fr/companycredit/sort_order` |  |  |  |
| 有効 | `payment/it/companycredit/active` |  |  |  |
| タイトル | `payment/it/companycredit/title` |  |  |  |
| 新しい注文ステータス | `payment/it/companycredit/order_status` |  |  |  |
| 該当国からの支払 | `payment/it/companycredit/allowspecific` |  |  |  |
| 特定の国からの支払い | `payment/it/companycredit/specificcountry` |  |  |  |
| 最小注文合計 | `payment/it/companycredit/min_order_total` |  |  |  |
| 最大注文合計 | `payment/it/companycredit/max_order_total` |  |  |  |
| 並べ替え順 | `payment/it/companycredit/sort_order` |  |  |  |

{style=&quot;table-layout:auto&quot;}
