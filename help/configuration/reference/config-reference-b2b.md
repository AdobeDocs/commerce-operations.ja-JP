---
title: B2B拡張機能の設定パスのリファレンス
description: Adobe CommerceのB2B拡張機能の設定パスと値について説明します。 企業、支払い、見積もり、B2B固有の設定オプションについて説明します。
feature: Configuration, B2B, Companies, Payments, Quotes
exl-id: 3414dea1-17c9-4462-8b8a-51a6045b0bc9
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '858'
ht-degree: 0%

---

# B2B拡張機能の設定パスのリファレンス

_これは、B2B for Adobe Commerceがインストールされているインスタンスで使用できます。_

このトピックでは、Commerce Enterprise B2B Extensionの設定パスを示します。 [`magento app:config:dump` コマンド ](../cli/export-configuration.md)は、これらの値をソース コントロールにある共有設定ファイル `app/etc/config.php`に書き込みます。

>[!INFO]
>
>このリファレンスでは、Adobe CommerceのB2Bに固有の&#x200B;_のみ_&#x200B;設定パスを一覧表示します。 この拡張機能には、Adobe Commerceのすべての設定パスが含まれます。

これらの設定パスについては、次を参照してください。

- [支払い設定パス](config-reference-payment.md)
- [機密性の高いシステム固有の設定パスの参照](config-reference-sens.md)

任意の構成設定を上書きする方法や、機密設定を設定する方法については、[環境変数を使用して構成設定を上書きする](override-config-settings.md#environment-variables)を参照してください。

## 一般カテゴリ

このセクションでは、管理者の&#x200B;**[!UICONTROL Stores]**/設定/**[!UICONTROL Configuration]**/**[!UICONTROL General]**&#x200B;のオプションで使用できる変数名と設定パスを示します。

### B2B機能のパス

これらの設定値は、**[!UICONTROL Stores]**/設定/**[!UICONTROL Configuration]**/**[!UICONTROL General]**/**[!UICONTROL B2B Features]**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | 暗号化？ | システム固有ですか？ | 繊細な？ |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| 会社を有効にする | `btob/website_configuration/company_active` | | | |
| 共有カタログを有効にする | `btob/website_configuration/sharedcatalog_active` | | | |
| B2B見積の有効化 | `btob/website_configuration/negotiablequote_active` | | | |
| クイックオーダーを有効にする | `btob/website_configuration/quickorder_active` | | | |
| 要求リストの有効化 | `btob/website_configuration/requisition_list_active` | | | |
| 適用される支払い方法 | `btob/default_b2b_payment_methods/applicable_payment_methods` | | | |
| お支払い方法 | `btob/default_b2b_payment_methods/available_payment_methods` | | | |

{style="table-layout:auto"}

## 顧客カテゴリ

このセクションでは、管理者の&#x200B;**[!UICONTROL Stores]**/設定/**[!UICONTROL Configuration]**/**[!UICONTROL Customers]**&#x200B;のオプションで使用できる変数名と設定パスを一覧表示します。

### 会社の設定パス

これらの設定値は、**[!UICONTROL Stores]**/設定/**[!UICONTROL Configuration]**/**[!UICONTROL Customers]**/**[!UICONTROL Company Configuration]**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | 暗号化？ | システム固有ですか？ | 繊細な？ |
|--------------|--------------|--------------|--------------|--------------|
| ストアフロントから会社登録を許可 | `company/general/allow_company_registration` | | | |
| 会社登録のメール受信者 | `company/email/company_registration` | | | ![機密性](/help/assets/configuration/cloud-sens.png) |
| 会社登録メールのコピーの送信先 | `company/email/company_registration_copy` | | | ![機密性](/help/assets/configuration/cloud-sens.png) |
| メール送信方法のコピー方法 | `company/email/company_copy_method` | | | |
| デフォルトの会社登録メール | `company/email/company_notify_admin_template` | | | |
| 顧客関連のメール | `company/email/heading_customer` | | | |
| デフォルトの営業担当者が割り当てたメール | `company/email/customer_sales_representative_template` | | | |
| デフォルトの顧客メールへの会社の割り当て | `company/email/customer_company_customer_assign_template` | | | |
| デフォルトの会社割り当て管理者メール | `company/email/customer_assign_super_user_template` | | | |
| 既定の会社管理者の非アクティブなメール | `company/email/customer_inactivate_super_user_template` | | | |
| 既定の会社管理者がメンバーの電子メールに変更されました | `company/email/customer_remove_super_user_template` | | | |
| 既定の顧客ステータスのアクティブな電子メール | `company/email/customer_account_activated_template` | | | |
| デフォルトの顧客ステータスの非アクティブな電子メール | `company/email/customer_account_locked_template` | | | |
| 会社ステータスの変更 | `company/email/heading_company_status` | | | |
| 会社ステータス変更メール受信者 | `company/email/company_status_change` | | | |
| 会社ステータスの送信電子メールのコピーの変更先 | `company/email/company_status_change_copy` | | | ![機密性](/help/assets/configuration/cloud-sens.png) |
| メール送信方法のコピー方法 | `company/email/company_status_copy_method` | | | |
| デフォルトの会社ステータスをアクティブな1つのメールに変更 | `company/email/company_status_pending_approval_to_active_template` | | | |
| デフォルトの会社ステータスをアクティブな2つのメールに変更 | `company/email/company_status_rejected_blocked_to_active_template` | | | |
| デフォルトの会社ステータスが「拒否された電子メール」に変更されました | `company/email/company_status_rejected_template` | | | |
| デフォルトの会社ステータスが「ブロック済みメール」に変更されました | `company/email/company_status_blocked_template` | | | |
| デフォルトの会社ステータスが「承認待ち」電子メールに変更されました | `company/email/company_status_pending_approval_template` | | | |
| 会社クレジット | `company/email/heading_company_credit` | | | |
| 会社のクレジット変更メール送信者 | `company/email/company_credit_change` |  | | ![機密性](/help/assets/configuration/cloud-sens.png) |
| 会社のクレジット変更メールのコピーの送信先 | `company/email/company_credit_change_copy` | | | |
| メール送信方法のコピー方法 | `company/email/company_credit_copy_method` | | | |
| 割り当てられた電子メールテンプレート | `company/email/credit_allocated_email_template` | | | |
| 更新された電子メールテンプレート | `company/email/credit_updated_email_template` | | | |
| 払い戻し済みメールテンプレート | `company/email/credit_reimbursed_email_template` | | | |
| 返金済みメールテンプレート | `company/email/credit_refunded_email_template` | | | |
| 元に戻された電子メールテンプレート | `company/email/credit_reverted_email_template` | | | |

{style="table-layout:auto"}

### 購買依頼リストのパス

これらの設定値は、**ストア**/設定/**設定**/**顧客**/**要求リスト**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | 暗号化？ | システム固有ですか？ | 繊細な？ |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| 要求リストの数 | `requisitionlist/general/number_requisition_lists` | | | |

{style="table-layout:auto"}

## 販売カテゴリ

このセクションでは、管理者の&#x200B;**ストア**/設定/**構成**/**セールス**&#x200B;のオプションで使用できる変数名と構成パスをリストします。

### セールスメールのパス

これらの設定値は、**Stores** / 設定/**Configuration** / **Sales** / **Sales Email**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | 暗号化？ | システム固有ですか？ | 繊細な？ |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| 有効 | `sales_email/quote/enabled` | | | |
| 更新された見積テンプレート（購入者に対して） | `sales_email/quote/updated_buyer_template` | | | |
| 拒否された見積テンプレート（購入者に対して） | `sales_email/quote/declined_buyer_template` | | | |
| 新しい見積もりテンプレート（販売者へ） | `sales_email/quote/new_seller_template` | | | |
| 更新された見積テンプレート （販売者に） | `sales_email/quote/updated_seller_template` | | | |
| 見積もり有効期限（48時間以内） | `sales_email/quote/expire_two_days_template` | | | |
| 見積もり有効期限（24時間以内） | `sales_email/quote/expire_one_day_template` | | | |
| 有効期限のリセット | `sales_email/quote/expire_reset_template` | | | |
| 見積もり電子メール コピーの送信先 | `sales_email/quote/copy_to` | | | ![機密性](/help/assets/configuration/cloud-sens.png) |
| 見積メール送信方法 | `sales_email/quote/copy_method` | | | |

{style="table-layout:auto"}

### 引用符のパス

これらの設定値は、**ストア**/設定/**設定**/**セールス**/**見積**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | 暗号化？ | システム固有ですか？ | 繊細な？ |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| 最低金額 | `quote/general/minimum_amount` | | | |
| 最小金額メッセージ | `quote/general/minimum_amount_message` | | | |
| デフォルトの有効期限 | `quote/general/default_expiration_period` | | | |
| アップロード用のファイル形式 | `quote/attached_files/file_formats` | | | |
| 最大ファイルサイズ | `quote/attached_files/maximum_file_size` | | | |
| 最低金額 | `quote/general/minimum_amount` | | | |
| 最小金額メッセージ | `quote/general/minimum_amount_message` | | | |
| デフォルトの有効期限 | `quote/general/default_expiration_period` | | | |
| アップロード用のファイル形式 | `quote/attached_files/file_formats` | | | |
| 最大ファイルサイズ | `quote/attached_files/maximum_file_size` | | | |

{style="table-layout:auto"}

## 支払方法のパス

これらの設定値は、**ストア**/設定/**構成**/**販売**/**支払い方法**&#x200B;の管理者で使用できます。

>[!INFO]
>
>利用可能なパスは、加盟店の国の選択によって決まります。

| 名前 | 設定パス | 暗号化？ | システム固有ですか？ | 繊細な？ |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| 有効 | `payment/au/companycredit/active` | | | |
| タイトル | `payment/au/companycredit/title` | | | |
| 新規注文ステータス | `payment/au/companycredit/order_status` | | | |
| 対象国からの支払い | `payment/au/companycredit/allowspecific` | | | |
| 特定国からの支払い | `payment/au/companycredit/specificcountry` | | | |
| 最低注文合計 | `payment/au/companycredit/min_order_total` | | | |
| 最大注文合計 | `payment/au/companycredit/max_order_total` | | | |
| ソート順序 | `payment/au/companycredit/sort_order` | | | |
| 有効 | `payment/es/companycredit/active` | | | |
| タイトル | `payment/es/companycredit/title` | | | |
| 新規注文ステータス | `payment/es/companycredit/order_status` | | | |
| 対象国からの支払い | `payment/es/companycredit/allowspecific` | | | |
| 特定国からの支払い | `payment/es/companycredit/specificcountry` | | | |
| 最低注文合計 | `payment/es/companycredit/min_order_total` | | | |
| 最大注文合計 | `payment/es/companycredit/max_order_total` | | | |
| ソート順序 | `payment/es/companycredit/sort_order` | | | |
| 有効 | `payment/companycredit/active` | | | |
| タイトル | `payment/companycredit/title` | | | |
| 新規注文ステータス | `payment/companycredit/order_status` | | | |
| 対象国からの支払い | `payment/companycredit/allowspecific` | | | |
| 特定国からの支払い | `payment/companycredit/specificcountry` | | | |
| 最低注文合計 | `payment/companycredit/min_order_total` | | | |
| 最大注文合計 | `payment/companycredit/max_order_total` | | | |
| ソート順序 | `payment/companycredit/sort_order` | | | |
| 有効 | `payment/nz/companycredit/active` | | | |
| タイトル | `payment/nz/companycredit/title` | | | |
| 新規注文ステータス | `payment/nz/companycredit/order_status` | | | |
| 対象国からの支払い | `payment/nz/companycredit/allowspecific` | | | |
| 特定国からの支払い | `payment/nz/companycredit/specificcountry` | | | |
| 最低注文合計 | `payment/nz/companycredit/min_order_total` | | | |
| 最大注文合計 | `payment/nz/companycredit/max_order_total` | | | |
| ソート順序 | `payment/nz/companycredit/sort_order` | | | |
| 有効 | `payment/us/companycredit/active` | | | |
| タイトル | `payment/us/companycredit/title` | | | |
| 新規注文ステータス | `payment/us/companycredit/order_status` | | | |
| 対象国からの支払い | `payment/us/companycredit/allowspecific` | | | |
| 特定国からの支払い | `payment/us/companycredit/specificcountry` | | | |
| 最低注文合計 | `payment/us/companycredit/min_order_total` | | | |
| 最大注文合計 | `payment/us/companycredit/max_order_total` | | | |
| ソート順序 | `payment/us/companycredit/sort_order` | | | |
| 有効 | `payment/gb/companycredit/active` | | | |
| タイトル | `payment/gb/companycredit/title` | | | |
| 新規注文ステータス | `payment/gb/companycredit/order_status` | | | |
| 対象国からの支払い | `payment/gb/companycredit/allowspecific` | | | |
| 特定国からの支払い | `payment/gb/companycredit/specificcountry` | | | |
| 最低注文合計 | `payment/gb/companycredit/min_order_total` | | | |
| 最大注文合計 | `payment/gb/companycredit/max_order_total` | | | |
| ソート順序 | `payment/gb/companycredit/sort_order` | | | |
| 有効 | `payment/de/companycredit/active` | | | |
| タイトル | `payment/de/companycredit/title` | | | |
| 新規注文ステータス | `payment/de/companycredit/order_status` | | | |
| 対象国からの支払い | `payment/de/companycredit/allowspecific` | | | |
| 特定国からの支払い | `payment/de/companycredit/specificcountry` | | | |
| 最低注文合計 | `payment/de/companycredit/min_order_total` | | | |
| 最大注文合計 | `payment/de/companycredit/max_order_total` | | | |
| ソート順序 | `payment/de/companycredit/sort_order` | | | |
| 有効 | `payment/other/companycredit/active` | | | |
| タイトル | `payment/other/companycredit/title` | | | |
| 新規注文ステータス | `payment/other/companycredit/order_status` | | | |
| 対象国からの支払い | `payment/other/companycredit/allowspecific` | | | |
| 特定国からの支払い | `payment/other/companycredit/specificcountry` | | | |
| 最低注文合計 | `payment/other/companycredit/min_order_total` | | | |
| 最大注文合計 | `payment/other/companycredit/max_order_total` | | | |
| ソート順序 | `payment/other/companycredit/sort_order` | | | |
| 有効 | `payment/ca/companycredit/active` | | | |
| タイトル | `payment/ca/companycredit/title` | | | |
| 新規注文ステータス | `payment/ca/companycredit/order_status` | | | |
| 対象国からの支払い | `payment/ca/companycredit/allowspecific` | | | |
| 特定国からの支払い | `payment/ca/companycredit/specificcountry` | | | |
| 最低注文合計 | `payment/ca/companycredit/min_order_total` | | | |
| 最大注文合計 | `payment/ca/companycredit/max_order_total` | | | |
| ソート順序 | `payment/ca/companycredit/sort_order` | | | |
| 有効 | `payment/hk/companycredit/active` | | | |
| タイトル | `payment/hk/companycredit/title` | | | |
| 新規注文ステータス | `payment/hk/companycredit/order_status` | | | |
| 対象国からの支払い | `payment/hk/companycredit/allowspecific` | | | |
| 特定国からの支払い | `payment/hk/companycredit/specificcountry` | | | |
| 最低注文合計 | `payment/hk/companycredit/min_order_total` | | | |
| 最大注文合計 | `payment/hk/companycredit/max_order_total` | | | |
| ソート順序 | `payment/hk/companycredit/sort_order` | | | |
| 有効 | `payment/jp/companycredit/active` | | | |
| タイトル | `payment/jp/companycredit/title` | | | |
| 新規注文ステータス | `payment/jp/companycredit/order_status` | | | |
| 対象国からの支払い | `payment/jp/companycredit/allowspecific` | | | |
| 特定国からの支払い | `payment/jp/companycredit/specificcountry` | | | |
| 最低注文合計 | `payment/jp/companycredit/min_order_total` | | | |
| 最大注文合計 | `payment/jp/companycredit/max_order_total` | | | |
| ソート順序 | `payment/jp/companycredit/sort_order` | | | |
| 有効 | `payment/fr/companycredit/active` | | | |
| タイトル | `payment/fr/companycredit/title` | | | |
| 新規注文ステータス | `payment/fr/companycredit/order_status` | | | |
| 対象国からの支払い | `payment/fr/companycredit/allowspecific` | | | |
| 特定国からの支払い | `payment/fr/companycredit/specificcountry` | | | |
| 最低注文合計 | `payment/fr/companycredit/min_order_total` | | | |
| 最大注文合計 | `payment/fr/companycredit/max_order_total` | | | |
| ソート順序 | `payment/fr/companycredit/sort_order` | | | |
| 有効 | `payment/it/companycredit/active` | | | |
| タイトル | `payment/it/companycredit/title` | | | |
| 新規注文ステータス | `payment/it/companycredit/order_status` | | | |
| 対象国からの支払い | `payment/it/companycredit/allowspecific` | | | |
| 特定国からの支払い | `payment/it/companycredit/specificcountry` | | | |
| 最低注文合計 | `payment/it/companycredit/min_order_total` | | | |
| 最大注文合計 | `payment/it/companycredit/max_order_total` | | | |
| ソート順序 | `payment/it/companycredit/sort_order` | | | |

{style="table-layout:auto"}
