---
title: B2B 拡張機能の設定パスのリファレンス
description: B2B 関連の設定値のリストを参照してください。
feature: Configuration, B2B, Companies, Payments, Quotes
exl-id: 3414dea1-17c9-4462-8b8a-51a6045b0bc9
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 0%

---

# B2B 拡張機能の設定パスのリファレンス

_これは、Adobe Commerce用 B2B がインストールされたインスタンスで使用できます。_

このトピックでは、Commerce Enterprise B2B Extension の設定パスを示します。 この [`magento app:config:dump` コマンド](../cli/export-configuration.md) これらの値を共有構成ファイルに書き込みます。 `app/etc/config.php`（ソース管理にする必要があります）。

>[!INFO]
>
>この参照リスト _のみ_ Adobe Commerceの B2B に固有の設定パス。 この拡張機能には、Adobe Commerceのすべての設定パスが含まれます。

これらの設定パスについては、以下を参照してください。

- [支払構成パス](config-reference-payment.md)
- [機密およびシステム固有の設定パスのリファレンス](config-reference-sens.md)

必要に応じて設定を上書きしたり、重要な設定を指定するには、を参照してください。 [環境変数を使用して設定を上書きする](override-config-settings.md#environment-variables).

## 一般カテゴリ

この節では、の管理でオプションに使用できる変数名と設定パスを示します。 **[!UICONTROL Stores]** > 設定 > **[!UICONTROL Configuration]** > **[!UICONTROL General]**.

### B2B 機能のパス

これらの設定値は、の管理者で使用できます。 **[!UICONTROL Stores]** > 設定 > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.

| 名前 | 設定パス | 暗号化しますか？ | システム固有？ | 機密？ |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| 会社を有効にする | `btob/website_configuration/company_active` | | | |
| Enable Shared Catalog | `btob/website_configuration/sharedcatalog_active` | | | |
| B2B 見積の有効化 | `btob/website_configuration/negotiablequote_active` | | | |
| クイックオーダーを有効にする | `btob/website_configuration/quickorder_active` | | | |
| 購買依頼リストの有効化 | `btob/website_configuration/requisition_list_active` | | | |
| 適用可能な支払い方法 | `btob/default_b2b_payment_methods/applicable_payment_methods` | | | |
| 支払い方法 | `btob/default_b2b_payment_methods/available_payment_methods` | | | |

{style="table-layout:auto"}

## 顧客カテゴリ

この節では、の管理画面でオプションに使用できる変数名と設定パスを示します。 **[!UICONTROL Stores]** > 設定 > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]**.

### 会社の設定パス

これらの設定値は、の管理者で使用できます。 **[!UICONTROL Stores]** > 設定 > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Company Configuration]**.

| 名前 | 設定パス | 暗号化しますか？ | システム固有？ | 機密？ |
|--------------|--------------|--------------|--------------|--------------|
| ストアフロントからの会社登録を許可 | `company/general/allow_company_registration` | | | |
| 会社登録の電子メール受信者 | `company/email/company_registration` | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 会社登録の電子メール コピーの送信先 | `company/email/company_registration_copy` | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| Send Email Copy メソッド | `company/email/company_copy_method` | | | |
| 既定の会社登録 E メール | `company/email/company_notify_admin_template` | | | |
| 顧客関連のメール | `company/email/heading_customer` | | | |
| 既定の営業担当者割り当て電子メール | `company/email/customer_sales_representative_template` | | | |
| デフォルトの会社を顧客メールに割り当て | `company/email/customer_company_customer_assign_template` | | | |
| デフォルトの会社管理者メールアドレスの割り当て | `company/email/customer_assign_super_user_template` | | | |
| 既定の会社管理者の非アクティブな電子メール | `company/email/customer_inactivate_super_user_template` | | | |
| デフォルトの会社管理者がメンバーメールに変更されました | `company/email/customer_remove_super_user_template` | | | |
| 既定の顧客ステータスアクティブ電子メール | `company/email/customer_account_activated_template` | | | |
| 既定の顧客ステータス非アクティブ電子メール | `company/email/customer_account_locked_template` | | | |
| 会社ステータスの変更 | `company/email/heading_company_status` | | | |
| 会社ステータス変更のメール受信者 | `company/email/company_status_change` | | | |
| 会社の状態変更の E メール コピーの送信先 | `company/email/company_status_change_copy` | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| Send Email Copy メソッド | `company/email/company_status_copy_method` | | | |
| デフォルトの会社ステータスがアクティブ 1 件のメールに変更されました | `company/email/company_status_pending_approval_to_active_template` | | | |
| デフォルトの会社ステータスがアクティブ 2 のメールに変更される | `company/email/company_status_rejected_blocked_to_active_template` | | | |
| 拒否メールに対するデフォルトの会社ステータスの変更 | `company/email/company_status_rejected_template` | | | |
| ブロックされたメールに対するデフォルトの会社ステータス変更 | `company/email/company_status_blocked_template` | | | |
| デフォルトの会社ステータスが承認保留中の E メールに変更される | `company/email/company_status_pending_approval_template` | | | |
| 会社クレジット | `company/email/heading_company_credit` | | | |
| 会社のクレジット変更メールの送信者 | `company/email/company_credit_change` |  | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 会社のクレジット変更メールのコピーの送信先 | `company/email/company_credit_change_copy` | | | |
| Send Email Copy メソッド | `company/email/company_credit_copy_method` | | | |
| 割り当て済みメールテンプレート | `company/email/credit_allocated_email_template` | | | |
| 更新されたメールテンプレート | `company/email/credit_updated_email_template` | | | |
| 返済済みメールテンプレート | `company/email/credit_reimbursed_email_template` | | | |
| 払い戻し済みメールテンプレート | `company/email/credit_refunded_email_template` | | | |
| 戻された電子メールテンプレート | `company/email/credit_reverted_email_template` | | | |

{style="table-layout:auto"}

### 購買依頼リスト・パス

これらの設定値は、の管理者で使用できます。 **ストア** > 設定 > **設定** > **顧客** > **購買依頼リスト**.

| 名前 | 設定パス | 暗号化しますか？ | システム固有？ | 機密？ |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| 購買依頼リスト数 | `requisitionlist/general/number_requisition_lists` | | | |

{style="table-layout:auto"}

## 販売カテゴリ

この節では、の管理画面でオプションに使用できる変数名と設定パスを示します。 **ストア** > 設定 > **設定** > **売上**.

### 販売 E メールのパス

これらの設定値は、の管理者で使用できます。 **ストア** > 設定 > **設定** > **売上** > **販売メール**.

| 名前 | 設定パス | 暗号化しますか？ | システム固有？ | 機密？ |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Enabled | `sales_email/quote/enabled` | | | |
| 更新された見積テンプレート （購買担当へ） | `sales_email/quote/updated_buyer_template` | | | |
| 拒否された見積テンプレート （購買担当に対して） | `sales_email/quote/declined_buyer_template` | | | |
| 新しい見積もりテンプレート （販売者宛） | `sales_email/quote/new_seller_template` | | | |
| 更新された見積テンプレート （販売者へ） | `sales_email/quote/updated_seller_template` | | | |
| 見積もりの有効期限（48 時間） | `sales_email/quote/expire_two_days_template` | | | |
| 見積もりの有効期限（24 時間） | `sales_email/quote/expire_one_day_template` | | | |
| 有効期限のリセット | `sales_email/quote/expire_reset_template` | | | |
| 見積 E メール コピーの送信先 | `sales_email/quote/copy_to` | | | ![機密](/help/assets/configuration/cloud-sens.png) |
| 見積書 E メール コピーの送信方法 | `sales_email/quote/copy_method` | | | |

{style="table-layout:auto"}

### 引用符パス

これらの設定値は、の管理者で使用できます。 **ストア** > 設定 > **設定** > **売上** > **見積もり**.

| 名前 | 設定パス | 暗号化しますか？ | システム固有？ | 機密？ |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| 最小量 | `quote/general/minimum_amount` | | | |
| 最小量のメッセージ | `quote/general/minimum_amount_message` | | | |
| デフォルトの有効期限 | `quote/general/default_expiration_period` | | | |
| アップロードするファイル形式 | `quote/attached_files/file_formats` | | | |
| 最大ファイルサイズ | `quote/attached_files/maximum_file_size` | | | |
| 最小量 | `quote/general/minimum_amount` | | | |
| 最小量のメッセージ | `quote/general/minimum_amount_message` | | | |
| デフォルトの有効期限 | `quote/general/default_expiration_period` | | | |
| アップロードするファイル形式 | `quote/attached_files/file_formats` | | | |
| 最大ファイルサイズ | `quote/attached_files/maximum_file_size` | | | |

{style="table-layout:auto"}

## 支払方法のパス

これらの設定値は、の管理者で使用できます。 **ストア** > 設定 > **設定** > **売上** > **支払い方法**.

>[!INFO]
>
>使用可能なパスは、商人の国の選択によって決定されます。

| 名前 | 設定パス | 暗号化しますか？ | システム固有？ | 機密？ |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Enabled | `payment/au/companycredit/active` | | | |
| タイトル | `payment/au/companycredit/title` | | | |
| 新規注文ステータス | `payment/au/companycredit/order_status` | | | |
| 対象国からの支払い | `payment/au/companycredit/allowspecific` | | | |
| 特定国からの支払い | `payment/au/companycredit/specificcountry` | | | |
| 最小注文合計 | `payment/au/companycredit/min_order_total` | | | |
| 最大注文合計 | `payment/au/companycredit/max_order_total` | | | |
| 並べ替え順序 | `payment/au/companycredit/sort_order` | | | |
| Enabled | `payment/es/companycredit/active` | | | |
| タイトル | `payment/es/companycredit/title` | | | |
| 新規注文ステータス | `payment/es/companycredit/order_status` | | | |
| 対象国からの支払い | `payment/es/companycredit/allowspecific` | | | |
| 特定国からの支払い | `payment/es/companycredit/specificcountry` | | | |
| 最小注文合計 | `payment/es/companycredit/min_order_total` | | | |
| 最大注文合計 | `payment/es/companycredit/max_order_total` | | | |
| 並べ替え順序 | `payment/es/companycredit/sort_order` | | | |
| Enabled | `payment/companycredit/active` | | | |
| タイトル | `payment/companycredit/title` | | | |
| 新規注文ステータス | `payment/companycredit/order_status` | | | |
| 対象国からの支払い | `payment/companycredit/allowspecific` | | | |
| 特定国からの支払い | `payment/companycredit/specificcountry` | | | |
| 最小注文合計 | `payment/companycredit/min_order_total` | | | |
| 最大注文合計 | `payment/companycredit/max_order_total` | | | |
| 並べ替え順序 | `payment/companycredit/sort_order` | | | |
| Enabled | `payment/nz/companycredit/active` | | | |
| タイトル | `payment/nz/companycredit/title` | | | |
| 新規注文ステータス | `payment/nz/companycredit/order_status` | | | |
| 対象国からの支払い | `payment/nz/companycredit/allowspecific` | | | |
| 特定国からの支払い | `payment/nz/companycredit/specificcountry` | | | |
| 最小注文合計 | `payment/nz/companycredit/min_order_total` | | | |
| 最大注文合計 | `payment/nz/companycredit/max_order_total` | | | |
| 並べ替え順序 | `payment/nz/companycredit/sort_order` | | | |
| Enabled | `payment/us/companycredit/active` | | | |
| タイトル | `payment/us/companycredit/title` | | | |
| 新規注文ステータス | `payment/us/companycredit/order_status` | | | |
| 対象国からの支払い | `payment/us/companycredit/allowspecific` | | | |
| 特定国からの支払い | `payment/us/companycredit/specificcountry` | | | |
| 最小注文合計 | `payment/us/companycredit/min_order_total` | | | |
| 最大注文合計 | `payment/us/companycredit/max_order_total` | | | |
| 並べ替え順序 | `payment/us/companycredit/sort_order` | | | |
| Enabled | `payment/gb/companycredit/active` | | | |
| タイトル | `payment/gb/companycredit/title` | | | |
| 新規注文ステータス | `payment/gb/companycredit/order_status` | | | |
| 対象国からの支払い | `payment/gb/companycredit/allowspecific` | | | |
| 特定国からの支払い | `payment/gb/companycredit/specificcountry` | | | |
| 最小注文合計 | `payment/gb/companycredit/min_order_total` | | | |
| 最大注文合計 | `payment/gb/companycredit/max_order_total` | | | |
| 並べ替え順序 | `payment/gb/companycredit/sort_order` | | | |
| Enabled | `payment/de/companycredit/active` | | | |
| タイトル | `payment/de/companycredit/title` | | | |
| 新規注文ステータス | `payment/de/companycredit/order_status` | | | |
| 対象国からの支払い | `payment/de/companycredit/allowspecific` | | | |
| 特定国からの支払い | `payment/de/companycredit/specificcountry` | | | |
| 最小注文合計 | `payment/de/companycredit/min_order_total` | | | |
| 最大注文合計 | `payment/de/companycredit/max_order_total` | | | |
| 並べ替え順序 | `payment/de/companycredit/sort_order` | | | |
| Enabled | `payment/other/companycredit/active` | | | |
| タイトル | `payment/other/companycredit/title` | | | |
| 新規注文ステータス | `payment/other/companycredit/order_status` | | | |
| 対象国からの支払い | `payment/other/companycredit/allowspecific` | | | |
| 特定国からの支払い | `payment/other/companycredit/specificcountry` | | | |
| 最小注文合計 | `payment/other/companycredit/min_order_total` | | | |
| 最大注文合計 | `payment/other/companycredit/max_order_total` | | | |
| 並べ替え順序 | `payment/other/companycredit/sort_order` | | | |
| Enabled | `payment/ca/companycredit/active` | | | |
| タイトル | `payment/ca/companycredit/title` | | | |
| 新規注文ステータス | `payment/ca/companycredit/order_status` | | | |
| 対象国からの支払い | `payment/ca/companycredit/allowspecific` | | | |
| 特定国からの支払い | `payment/ca/companycredit/specificcountry` | | | |
| 最小注文合計 | `payment/ca/companycredit/min_order_total` | | | |
| 最大注文合計 | `payment/ca/companycredit/max_order_total` | | | |
| 並べ替え順序 | `payment/ca/companycredit/sort_order` | | | |
| Enabled | `payment/hk/companycredit/active` | | | |
| タイトル | `payment/hk/companycredit/title` | | | |
| 新規注文ステータス | `payment/hk/companycredit/order_status` | | | |
| 対象国からの支払い | `payment/hk/companycredit/allowspecific` | | | |
| 特定国からの支払い | `payment/hk/companycredit/specificcountry` | | | |
| 最小注文合計 | `payment/hk/companycredit/min_order_total` | | | |
| 最大注文合計 | `payment/hk/companycredit/max_order_total` | | | |
| 並べ替え順序 | `payment/hk/companycredit/sort_order` | | | |
| Enabled | `payment/jp/companycredit/active` | | | |
| タイトル | `payment/jp/companycredit/title` | | | |
| 新規注文ステータス | `payment/jp/companycredit/order_status` | | | |
| 対象国からの支払い | `payment/jp/companycredit/allowspecific` | | | |
| 特定国からの支払い | `payment/jp/companycredit/specificcountry` | | | |
| 最小注文合計 | `payment/jp/companycredit/min_order_total` | | | |
| 最大注文合計 | `payment/jp/companycredit/max_order_total` | | | |
| 並べ替え順序 | `payment/jp/companycredit/sort_order` | | | |
| Enabled | `payment/fr/companycredit/active` | | | |
| タイトル | `payment/fr/companycredit/title` | | | |
| 新規注文ステータス | `payment/fr/companycredit/order_status` | | | |
| 対象国からの支払い | `payment/fr/companycredit/allowspecific` | | | |
| 特定国からの支払い | `payment/fr/companycredit/specificcountry` | | | |
| 最小注文合計 | `payment/fr/companycredit/min_order_total` | | | |
| 最大注文合計 | `payment/fr/companycredit/max_order_total` | | | |
| 並べ替え順序 | `payment/fr/companycredit/sort_order` | | | |
| Enabled | `payment/it/companycredit/active` | | | |
| タイトル | `payment/it/companycredit/title` | | | |
| 新規注文ステータス | `payment/it/companycredit/order_status` | | | |
| 対象国からの支払い | `payment/it/companycredit/allowspecific` | | | |
| 特定国からの支払い | `payment/it/companycredit/specificcountry` | | | |
| 最小注文合計 | `payment/it/companycredit/min_order_total` | | | |
| 最大注文合計 | `payment/it/companycredit/max_order_total` | | | |
| 並べ替え順序 | `payment/it/companycredit/sort_order` | | | |

{style="table-layout:auto"}
