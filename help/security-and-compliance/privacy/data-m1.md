---
title: 顧客の個人情報の参照（バージョン 1.x）
description: Magento 1.x におけるお客様の個人情報のデータフローとデータベースエンティティマッピングについて説明します。
exl-id: 8b01418d-8ca1-48fc-9577-a324ed3109d1
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 0%

---

# 顧客の個人情報の参照（バージョン 1.x）

>[!NOTE]
>
>これは、Adobe Commerceのマーチャントやデベロッパーがプライバシー規制への準拠に備えるのに役立つ、一連のトピックの 1 つです。 自社のビジネスが法的義務に準拠する必要があるかどうか、またどのように準拠すべきかを判断するには、法務担当者に相談してください。

プライバシー規制に関するコンプライアンスプログラムを開発する際の参考として、次のデータフロー図とデータベースエンティティのマッピングを使用します。例えば、次のようなものがあります。

- [GDPR](gdpr.md)
- [CCPA](ccpa.md)

## データフロー図

データフロー図は、顧客および管理者がストアフロントおよび管理者に入力して取得できるデータのタイプを示しています。

### フロントエンドデータのエントリポイント

ユーザーは、アカウントの登録時、チェックアウト時などのイベントに、顧客、住所、支払い情報を入力できます。

![フロントエンドデータのエントリポイント](../../assets/security-compliance/frontend-data-entry-points.svg)

### フロントエンド データ アクセス ポイント

Commerceは、ユーザーがログインして複数の異なるページを表示したり、チェックアウトしたりする際に、ユーザー情報を読み込みます。

![フロントエンド データ アクセス ポイント](../../assets/security-compliance/frontend-data-access-points.svg)

### バックエンドデータのエントリポイント

マーチャントは、管理者から顧客、住所、支払い情報を入力して、顧客または注文を作成できます。

![バックエンドデータのエントリポイント](../../assets/security-compliance/backend-data-entry-points.svg)

### バックエンドのデータアクセスポイント

Commerceは、マーチャントが複数のタイプのグリッドを表示したり、グリッドをクリックして詳細情報を表示したり、その他の様々なタスクを実行したりすると、顧客情報を読み込みます。

![バックエンドのデータアクセスポイント](../../assets/security-compliance/backend-data-access-points.svg)

## データベースエンティティ

Magento1 は、顧客の情報を customer、sales およびその他のデータベーステーブルに格納します。

### 顧客データ

Magento1 は、 `customer_entity` および `customer_address_entity` テーブル。 これらのテーブルにはどちらも、カスタム顧客属性を含めることができる参照テーブルがいくつかあります。

#### `customer_entity` および参照テーブル

次の列 `customer_entity`テーブルには、顧客情報が格納されます。

| 列 | データタイプ |
| --- | --- |
| `email` | varchar （255） |

これらのテーブルは、 `customer_entity` また、カスタム顧客属性を含めることができます。

| テーブル | 列 | データタイプ |
| --- | --- | --- |
| `customer_entity_datetime` | `value` | datetime |
| `customer_entity_decimal` | `value` | decimal （12,4） |
| `customer_entity_int` | `value` | int （11） |
| `customer_entity_text` | `value` | text |
| `customer_entity_varchar` | `value` | varchar （255） |

#### `customer_address_entity` および参照テーブル

以下のテーブルのリファレンス `customer_address_entity` また、カスタム顧客属性を含めることができます。

| テーブル | 列 | データタイプ |
| --- | --- | --- |
| `customer_address_entity_datetime` | `value` | datetime |
| `customer_address_entity_decimal` | `value` | decimal （12,4） |
| `customer_address_entity_int` | `value` | int （11） |
| `customer_address_entity_text` | `value` | text |
| `customer_address_entity_varchar` | `value` | varchar （255） |

### 注文データ

この `sales_flat_order` および関連するテーブルには、顧客の名前、請求先と配送先住所、および関連する情報が含まれています。

#### `sales_flat_order` テーブル

次の列 `sales_order` テーブルには、顧客情報が格納されます。

| 列 | データタイプ |
| --- | --- |
| `customer_id` | int （10） |
| `customer_email` | varchar （128） |
| `customer_firstname` | varchar （128） |
| `customer_gender` | int （11） |
| `customer_lastname` | varchar （128） |
| `customer_middlename` | varchar （128） |
| `customer_prefix` | varchar （32） |
| `customer_suffix` | varchar （32） |
| `customer_taxvat` | varchar （32） |
| `remote_ip` | varchar （32） |

#### `sales_flat_order_address` テーブル

この `sales_flat_order_address` テーブルには、顧客の住所が含まれます。

| 列 | データタイプ |
| --- | --- |
| `customer_id` | int （10） |
| `fax` | varchar （255） |
| `region` | varchar （255） |
| `postcode` | varchar （255） |
| `lastname` | varchar （255） |
| `street` | varchar （255） |
| `city` | varchar （255） |
| `email` | varchar （255） |
| `telephone` | varchar （255） |
| `firstname` | varchar （255） |
| `prefix` | varchar （255） |
| `suffix` | varchar （255） |
| `middlename` | varchar （255） |
| `company` | varchar （255） |
| `vat_id` | text |

#### `sales_flat_order_grid` テーブル

次の列 `sales_flat_order_grid` テーブルには、顧客情報が格納されます。

| 列 | データタイプ |
| --- | --- |
| `customer_id` | int （10） |
| `shipping_name` | varchar （255） |
| `billing_name` | varchar （255） |

#### `sales_flat_order_payment` テーブル

次の列 `sales_flat_order_payment` テーブルには、顧客情報が格納されます。

| 列 | データタイプ |
| --- | --- |
| `cc_exp_month` | varchar （255） |
| `cc_ss_start_year` | varchar （255） |
| `echeck_bank_name` | varchar （128） |
| `echeck_type` | varchar （255） |
| `cc_ss_start_month` | varchar （255） |
| `cc_owner` | varchar （255） |
| `cc_exp_year` | varchar （255） |
| `echeck_routing_number` | varchar （255） |
| `echeck_account_name` | varchar （255） |

### 見積データ

見積もりには、顧客の名前、メールアドレス、住所、および関連情報が含まれています。

#### `sales_flat_quote` テーブル

次の列 `sales_flat_quote` テーブルには、顧客情報が格納されます。

| 列 | データタイプ |
| --- | --- |
| `customer_id` | int （10） |
| `customer_tax_class_id` | int （10） |
| `customer_group_id` | int （10） |
| `customer_email` | varchar （255） |
| `customer_prefix` | varchar （40） |
| `customer_firstname` | varchar （255） |
| `customer_middlename` | varchar （40） |
| `customer_lastname` | varchar （255） |
| `customer_suffix` | varchar （40） |
| `customer_dob` | datetime |
| `customer_note` | varchar （255） |
| `remote_ip` | varchar （255） |
| `customer_gender` | varchar （255） |

#### `sales_flat_quote_address` テーブル

次の列 `sales_flat_quote_address` テーブルには、顧客情報が格納されます。

| 列 | データタイプ |
| --- | --- |
| `email` | varchar （255） |
| `prefix` | varchar （40） |
| `firstname` | varchar （255） |
| `middlename` | varchar （40） |
| `lastname` | varchar （255） |
| `suffix` | varchar （40） |
| `company` | varchar （255） |
| `street` | varchar （255） |
| `city` | varchar （255） |
| `region` | varchar （255） |
| `postcode` | varchar （255） |
| `fax` | varchar （255） |

#### `sales_flat_quote_payment` テーブル

この `sales_flat_quote_payment` 表には、クレジット・カード情報およびその他の取引情報が含まれます。

| 列 | データタイプ |
| --- | --- |
| `cc_last_4` | varchar （255） |
| `cc_owner` | varchar （255） |
| `cc_exp_month` | smallint （5） |
| `cc_exp_year` | smallint （5） |
| `cc_ss_owner` | varchar （255） |
| `cc_ss_start_month` | smallint （5） |
| `cc_ss_start_year` | smallint （5） |

### データのアーカイブ

次の表と列には、顧客情報が含まれています。

| テーブル | 列 | データタイプ |
| --- | --- | --- |
| `enterprise_sales_creditmemo_grid_archive` | `billing_name` | varchar （255） |
| `enterprise_sales_invoice_grid_archive` | `billing_name` | varchar （255） |
| `enterprise_sales_order_grid_archive` | `billing_name` | varchar （255） |
| `enterprise_sales_order_grid_archive` | `customer_id` | int （10） |
| `enterprise_sales_order_grid_archive` | `shipping_name` | varchar （255） |
| `enterprise_sales_shipment_grid_archive` | `shipping_name` | varchar （255） |

### 販売データ

次の表と列には、顧客情報が含まれています。

| テーブル | 列 | データタイプ |
| --- | --- | --- |
| `sales_flat_creditmemo_grid` | `billing_name` | varchar （255） |
| `sales_flat_invoice_grid` | `billing_name` | varchar （255） |

### RMA データ

次の RMA 表および列には、顧客情報が含まれています。

| テーブル | 列 | データタイプ |
| --- | --- | --- |
| `enterprise_rma` | `customer_custom_email` | varchar （255） |
| `enterprise_rma_grid` | `customer_id` | int （10） |
| `enterprise_rma_grid` | `customer_name` | varchar （255） |

### その他データ

次の表と列には、顧客情報が含まれています。

| テーブル | 列 | データタイプ |
| --- | --- | --- |
| `core_email_queue_recipients` | `recipient_email` | varchar （128） |
| `core_email_queue_recipients` | `recipient_name` | varchar （255） |
| `customer_flowpassword` | `email` | varchar （255） |
| `customer_flowpassword` | `ip` | varchar （50） |
| `enterprise_giftregistry_person` | `email` | varchar （150） |
| `enterprise_giftregistry_person` | `firstname` | varchar （100） |
| `enterprise_giftregistry_person` | `lastname` | varchar （100） |
| `enterprise_giftregistry_person` | `middlename` | text |
| `enterprise_invitation` | `customer_id` | int （10） |
| `enterprise_invitation` | `email` | varchar （255） |
| `enterprise_invitation` | `referral_id` | int （10） |
| `enterprise_reminder_rule_coupon` | `customer_id` | int （10） |
| `enterprise_reminder_rule_coupon` | `emails_failed` | smallint （5） |
| `enterprise_scheduled_operations` | `email_receiver` | varchar （150） |
| `enterprise_scheduled_operations` | `email_sender` | varchar （150） |
| `gift_message` | `customer_id` | int （10） |
| `gift_message` | `recipient` | varchar （255） |
| `gift_message` | `sender` | varchar （255） |
| `newsletter_subscriber` | `customer_id` | int （10） |
| `newsletter_subscriber` | `subscriber_email` | varchar （150） |
| `persistent_session` | `customer_id` | int （10） |
| `persistent_session` | `info` | text |
| `poll_vote` | `customer_id` | int （10） |
| `poll_vote` | `ip_address` | varbinary （16） |
| `rating_option_vote` | `customer_id` | int （10） |
| `rating_option_vote` | `remote_ip` | varchar （50） |
| `rating_option_vote` | `remote_ip_long` | varbinary （516） |
| `send_friend_log` | `ip` | varbinary （16） |

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
