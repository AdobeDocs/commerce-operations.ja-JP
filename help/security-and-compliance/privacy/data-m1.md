---
title: お客様の個人情報に関するリファレンス（バージョン 1.x）
description: Magento1.x での、顧客の個人情報に対するデータフローとデータベースエンティティのマッピングについて説明します。
exl-id: 8b01418d-8ca1-48fc-9577-a324ed3109d1
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '606'
ht-degree: 0%

---

# お客様の個人情報に関するリファレンス（バージョン 1.x）

>[!NOTE]
>
>これは、Adobe CommerceやMagento Open Sourceの販売店や開発者がプライバシー規制への準拠に備えるのに役立つ、一連のトピックの 1 つです。 御社のビジネスが法的義務を遵守する必要があるかどうか、また、その方法を決定するには、弁護士に相談してください。

次のようなプライバシー規制への準拠プログラムを開発する際には、次のデータフロー図およびデータベースエンティティマッピングを参照用に使用します。

- [GDPR](gdpr.md)
- [CCPA](ccpa.md)

## データフロー図

データフロー図には、顧客および管理者がストアフロントと管理で入力および取得できるデータのタイプが示されています。

### フロントエンドデータエントリポイント

ユーザは、顧客、住所、支払い情報を入力して、アカウントの登録時、チェックアウト時などに、同様のイベントを行うことができます。

![フロントエンドデータエントリポイント](../../assets/security-compliance/frontend-data-entry-points.svg)

### フロントエンドデータアクセスポイント

Commerce は、顧客がログインして複数の異なるページを表示したりチェックアウトしたりすると、顧客情報を読み込みます。

![フロントエンドデータアクセスポイント](../../assets/security-compliance/frontend-data-access-points.svg)

### バックエンドのデータエントリポイント

マーチャントは、顧客、住所、支払い情報を管理者から入力して、顧客や注文を作成できます。

![バックエンドのデータエントリポイント](../../assets/security-compliance/backend-data-entry-points.svg)

### バックエンドデータアクセスポイント

Commerce は、マーチャントが複数の種類のグリッドを表示し、グリッドをクリックして詳細情報を表示し、その他の様々なタスクを実行すると、顧客情報を読み込みます。

![バックエンドデータアクセスポイント](../../assets/security-compliance/backend-data-access-points.svg)

## データベースエンティティ

Magento1 は、顧客、販売、その他のデータベーステーブルに顧客情報を格納します。

### 顧客データ

Magento1 は、顧客情報を `customer_entity` および `customer_address_entity` テーブル。 これらのテーブルには、カスタム顧客属性を含むことができる複数の参照テーブルがあります。

#### `customer_entity` および参照テーブル

次の列 ( `customer_entity`表には、顧客情報が含まれます。

| 列 | データタイプ |
| --- | --- |
| `email` | varchar(255) |

以下の表は、を参照しています。 `customer_entity` には、カスタム顧客属性を含めることができます。

| テーブル | 列 | データタイプ |
| --- | --- | --- |
| `customer_entity_datetime` | `value` | 日時 |
| `customer_entity_decimal` | `value` | decimal(12,4) |
| `customer_entity_int` | `value` | int(11) |
| `customer_entity_text` | `value` | テキスト |
| `customer_entity_varchar` | `value` | varchar(255) |

#### `customer_address_entity` および参照テーブル

以下の表のリファレンス `customer_address_entity` には、カスタム顧客属性を含めることができます。

| テーブル | 列 | データタイプ |
| --- | --- | --- |
| `customer_address_entity_datetime` | `value` | 日時 |
| `customer_address_entity_decimal` | `value` | decimal(12,4) |
| `customer_address_entity_int` | `value` | int(11) |
| `customer_address_entity_text` | `value` | テキスト |
| `customer_address_entity_varchar` | `value` | varchar(255) |

### 注文データ

The `sales_flat_order` および関連するテーブルには、顧客の名前、請求先住所、配送先住所、および関連情報が含まれます。

#### `sales_flat_order` 表

次の列 ( `sales_order` 表には、顧客情報が含まれます。

| 列 | データタイプ |
| --- | --- |
| `customer_id` | int(10) |
| `customer_email` | varchar(128) |
| `customer_firstname` | varchar(128) |
| `customer_gender` | int(11) |
| `customer_lastname` | varchar(128) |
| `customer_middlename` | varchar(128) |
| `customer_prefix` | varchar(32) |
| `customer_suffix` | varchar(32) |
| `customer_taxvat` | varchar(32) |
| `remote_ip` | varchar(32) |

#### `sales_flat_order_address` 表

The `sales_flat_order_address` テーブルには、顧客の住所が含まれます。

| 列 | データタイプ |
| --- | --- |
| `customer_id` | int(10) |
| `fax` | varchar(255) |
| `region` | varchar(255) |
| `postcode` | varchar(255) |
| `lastname` | varchar(255) |
| `street` | varchar(255) |
| `city` | varchar(255) |
| `email` | varchar(255) |
| `telephone` | varchar(255) |
| `firstname` | varchar(255) |
| `prefix` | varchar(255) |
| `suffix` | varchar(255) |
| `middlename` | varchar(255) |
| `company` | varchar(255) |
| `vat_id` | テキスト |

#### `sales_flat_order_grid` 表

次の列 ( `sales_flat_order_grid` 表には、顧客情報が含まれます。

| 列 | データタイプ |
| --- | --- |
| `customer_id` | int(10) |
| `shipping_name` | varchar(255) |
| `billing_name` | varchar(255) |

#### `sales_flat_order_payment` 表

次の列 ( `sales_flat_order_payment` 表には、顧客情報が含まれます。

| 列 | データタイプ |
| --- | --- |
| `cc_exp_month` | varchar(255) |
| `cc_ss_start_year` | varchar(255) |
| `echeck_bank_name` | varchar(128) |
| `echeck_type` | varchar(255) |
| `cc_ss_start_month` | varchar(255) |
| `cc_owner` | varchar(255) |
| `cc_exp_year` | varchar(255) |
| `echeck_routing_number` | varchar(255) |
| `echeck_account_name` | varchar(255) |

### 見積もりデータ

引用符には、お客様の名前、電子メール、住所、関連情報が含まれます。

#### `sales_flat_quote` 表

次の列 ( `sales_flat_quote` 表には、顧客情報が含まれます。

| 列 | データタイプ |
| --- | --- |
| `customer_id` | int(10) |
| `customer_tax_class_id` | int(10) |
| `customer_group_id` | int(10) |
| `customer_email` | varchar(255) |
| `customer_prefix` | varchar(40) |
| `customer_firstname` | varchar(255) |
| `customer_middlename` | varchar(40) |
| `customer_lastname` | varchar(255) |
| `customer_suffix` | varchar(40) |
| `customer_dob` | 日時 |
| `customer_note` | varchar(255) |
| `remote_ip` | varchar(255) |
| `customer_gender` | varchar(255) |

#### `sales_flat_quote_address` 表

次の列 ( `sales_flat_quote_address` 表には、顧客情報が含まれます。

| 列 | データタイプ |
| --- | --- |
| `email` | varchar(255) |
| `prefix` | varchar(40) |
| `firstname` | varchar(255) |
| `middlename` | varchar(40) |
| `lastname` | varchar(255) |
| `suffix` | varchar(40) |
| `company` | varchar(255) |
| `street` | varchar(255) |
| `city` | varchar(255) |
| `region` | varchar(255) |
| `postcode` | varchar(255) |
| `fax` | varchar(255) |

#### `sales_flat_quote_payment` 表

The `sales_flat_quote_payment` 表には、クレジットカード情報やその他のトランザクション情報が含まれます。

| 列 | データタイプ |
| --- | --- |
| `cc_last_4` | varchar(255) |
| `cc_owner` | varchar(255) |
| `cc_exp_month` | smallint(5) |
| `cc_exp_year` | smallint(5) |
| `cc_ss_owner` | varchar(255) |
| `cc_ss_start_month` | smallint(5) |
| `cc_ss_start_year` | smallint(5) |

### データをアーカイブ

次のテーブルと列には、顧客情報が含まれます。

| テーブル | 列 | データタイプ |
| --- | --- | --- |
| `enterprise_sales_creditmemo_grid_archive` | `billing_name` | varchar(255) |
| `enterprise_sales_invoice_grid_archive` | `billing_name` | varchar(255) |
| `enterprise_sales_order_grid_archive` | `billing_name` | varchar(255) |
| `enterprise_sales_order_grid_archive` | `customer_id` | int(10) |
| `enterprise_sales_order_grid_archive` | `shipping_name` | varchar(255) |
| `enterprise_sales_shipment_grid_archive` | `shipping_name` | varchar(255) |

### 販売データ

次のテーブルと列には、顧客情報が含まれます。

| テーブル | 列 | データタイプ |
| --- | --- | --- |
| `sales_flat_creditmemo_grid` | `billing_name` | varchar(255) |
| `sales_flat_invoice_grid` | `billing_name` | varchar(255) |

### RMA データ

次の RMA 表および列には、顧客情報が含まれます。

| テーブル | 列 | データタイプ |
| --- | --- | --- |
| `enterprise_rma` | `customer_custom_email` | varchar(255) |
| `enterprise_rma_grid` | `customer_id` | int(10) |
| `enterprise_rma_grid` | `customer_name` | varchar(255) |

### その他のデータ

次のテーブルと列には、顧客情報が含まれます。

| テーブル | 列 | データタイプ |
| --- | --- | --- |
| `core_email_queue_recipients` | `recipient_email` | varchar(128) |
| `core_email_queue_recipients` | `recipient_name` | varchar(255) |
| `customer_flowpassword` | `email` | varchar(255) |
| `customer_flowpassword` | `ip` | varchar(50) |
| `enterprise_giftregistry_person` | `email` | varchar(150) |
| `enterprise_giftregistry_person` | `firstname` | varchar(100) |
| `enterprise_giftregistry_person` | `lastname` | varchar(100) |
| `enterprise_giftregistry_person` | `middlename` | テキスト |
| `enterprise_invitation` | `customer_id` | int(10) |
| `enterprise_invitation` | `email` | varchar(255) |
| `enterprise_invitation` | `referral_id` | int(10) |
| `enterprise_reminder_rule_coupon` | `customer_id` | int(10) |
| `enterprise_reminder_rule_coupon` | `emails_failed` | smallint(5) |
| `enterprise_scheduled_operations` | `email_receiver` | varchar(150) |
| `enterprise_scheduled_operations` | `email_sender` | varchar(150) |
| `gift_message` | `customer_id` | int(10) |
| `gift_message` | `recipient` | varchar(255) |
| `gift_message` | `sender` | varchar(255) |
| `newsletter_subscriber` | `customer_id` | int(10) |
| `newsletter_subscriber` | `subscriber_email` | varchar(150) |
| `persistent_session` | `customer_id` | int(10) |
| `persistent_session` | `info` | テキスト |
| `poll_vote` | `customer_id` | int(10) |
| `poll_vote` | `ip_address` | varbinary(16) |
| `rating_option_vote` | `customer_id` | int(10) |
| `rating_option_vote` | `remote_ip` | varchar(50) |
| `rating_option_vote` | `remote_ip_long` | varbinary(516) |
| `send_friend_log` | `ip` | varbinary(16) |

顧客を参照するその他のテーブル：

- `catalog_compare_item`
- `downloadable_link_purchased`
- `enterprise_customerbalance`
- `enterprise_customersegment_customer`
- `enterprise_giftregistry_entity`
- `enterprise_reminder_rule_log`
- `enterprise_reward`
- `log_customer`
- `log_visitor_online`
- `oauth_token`
- `product_alert_price`
- `product_alert_stock`
- `report_compared_product_index`
- `report_viewed_product_index`
- `review_detail`
- `sales_billing_agreement`
- `sales_flat_shipment`
- `sales_recurring_profile`
- `salesrule_coupon_usage`
- `salesrule_customer`
- `tag`
- `tag_relation`
- `wishlist`
