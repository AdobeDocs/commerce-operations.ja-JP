---
title: お客様の個人情報に関するリファレンス（バージョン 2.x）
description: Adobe CommerceおよびMagento Open Source2.x の、顧客の個人情報に対するデータフロー図およびデータベースエンティティのマッピングについて説明します。
source-git-commit: 0640b59cc529123911537475bbfc179c917ac258
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---


# お客様の個人情報に関するリファレンス（バージョン 2.x）

>[!NOTE]
>
>これは、Adobe CommerceやMagento Open Sourceの販売店や開発者がプライバシー規制への準拠に備えるのに役立つ、一連のトピックの 1 つです。 御社のビジネスが法的義務を遵守する必要があるかどうか、また、その方法を決定するには、弁護士に相談してください。

次のようなプライバシー規制への準拠プログラムを開発する際には、参照用に、次のデータフロー図とデータベースエンティティマッピングを使用します。

- [GDPR](gdpr.md)
- [CCPA](ccpa.md)

## データフロー図

データフロー図には、顧客および管理者がストアフロントおよび管理者から入力および取得できるデータのタイプが示されます。

### フロントエンドデータエントリポイント

ユーザは、顧客、住所、支払い情報を入力して、アカウントの登録時、チェックアウト時などに、同様のイベントを行うことができます。

![フロントエンドデータエントリポイント](../../assets/security-compliance/frontend-data-entry-points.svg)

### フロントエンドデータアクセスポイント

Adobe CommerceおよびMagento Open Sourceは、顧客がログインして複数の異なるページを表示したり、チェックアウトしたりすると、顧客情報を読み込みます。

![フロントエンドデータアクセスポイント](../../assets/security-compliance/frontend-data-access-points.svg)

### バックエンドのデータエントリポイント

マーチャントは、顧客または注文を管理者から作成する際に、顧客情報、住所データ、支払いデータを入力できます。

![バックエンドのデータエントリポイント](../../assets/security-compliance/backend-data-entry-points.svg)

### バックエンドデータアクセスポイント

Adobe CommerceとMagento Open Sourceは、マーチャントが複数の種類のグリッドを表示し、グリッドをクリックして詳細情報を表示し、その他の様々なタスクを実行する際に顧客情報をロードします。

![バックエンドデータアクセスポイント](../../assets/security-compliance/backend-data-access-points.svg)

## データベースエンティティ

Adobe CommerceとMagento Open Sourceは主に、顧客固有の情報を顧客、住所、注文、見積、支払いの各テーブルに保存します。 その他のテーブルには、顧客 ID への参照が含まれています。

### 顧客データ

Adobe CommerceとMagento Open Sourceは、次の顧客属性を格納するように設定できます。

- 生年月日
- 電子メール
- 名
- 性別
- 姓
- ミドルネーム/イニシャル
- 名前のプレフィックス
- 名前サフィックス

>[!NOTE]
>
>現在のセキュリティおよびプライバシーのベストプラクティスに従い、顧客の生年月日（月、日、年）のストレージに関連する法的リスクとセキュリティリスクの可能性、およびその他の個人 ID（氏名など）を把握してから、データを収集または処理してください。

#### `customer_entity` および「customer_entity」参照

次の列 ( `customer_entity` 表には、顧客情報が含まれます。

| 列 | データタイプ |
| ------------ | ------------ |
| `email` | varchar(255) |
| `prefix` | varchar(40) |
| `firstname` | varchar(255) |
| `middlename` | varchar(255) |
| `lastname` | varchar(255) |
| `suffix` | varchar(40) |
| `dob` | 日付 |
| `gender` | smallint(5) |

以下の表は、 `customer_entity` には、カスタム顧客属性を含めることができます。

| テーブル | 列 | データタイプ |
| -------------------------- | ------- | ------------- |
| `customer_entity_datetime` | `value` | 日時 |
| `customer_entity_decimal` | `value` | decimal(12,4) |
| `customer_entity_int` | `value` | int(11) |
| `customer_entity_text` | `value` | テキスト |
| `customer_entity_varchar` | `value` | varchar(255) |

#### `customer_grid_flat` 表

次の列 ( `customer_grid_flat` 表には、顧客情報が含まれます。

| 列 | データタイプ |
| -------------------- | ------------ |
| `name` | テキスト |
| `email` | varchar(255) |
| `dob` | 日付 |
| `gender` | int(11) |
| `shipping_full` | テキスト |
| `billing_full` | テキスト |
| `billing_firstname` | varchar(255) |
| `billing_lastname` | varchar(255) |
| `billing_telephone` | varchar(255) |
| `billing_postcode` | varchar(255) |
| `billing_country_id` | varchar(255) |
| `billing_region` | varchar(255) |
| `billing_city` | varchar(255) |
| `billing_fax` | varchar(255) |
| `billing_vat_id` | varchar(255) |
| `billing_company` | varchar(255) |

### 住所データ

Adobe CommerceとMagento Open Sourceは、次の顧客属性を保存します。

- 市区町村
- 会社
- 国
- FAX
- 名
- 姓
- ミドルネーム/イニシャル
- 名前のプレフィックス
- 名前サフィックス
- 電話番号
- 都道府県
- 都道府県 ID
- 住所
- VAT 番号
- 郵便番号

#### `customer_address_entity` および `customer_address_entity` 参照

次の列 ( `customer_address_entity` 表には、顧客情報が含まれます。

| 列 | データタイプ |
| ------------ | ------------ |
| `city` | varchar(255) |
| `company` | varchar(255) |
| `country_id` | varchar(255) |
| `fax` | varchar(255) |
| `firstname` | varchar(255) |
| `lastname` | varchar(255) |
| `middlename` | varchar(255) |
| `postcode` | varchar(255) |
| `region` | varchar(255) |
| `region_id` | int(10) |
| `street` | テキスト |
| `suffix` | varchar(40) |
| `telephone` | varchar(255) |
| `vat_id` | varchar(255) |

以下の表は、 `customer_address_entity` には、カスタム顧客属性を含めることができます。

| テーブル | 列 | データタイプ |
| ---------------------------------- | ------- | ------------- |
| `customer_address_entity_datetime` | `value` | 日時 |
| `customer_address_entity_decimal` | `value` | decimal(12,4) |
| `customer_address_entity_int` | `value` | int(11) |
| `customer_address_entity_text` | `value` | テキスト |
| `customer_address_entity_varchar` | `value` | varchar(255) |

### 注文データ

この `sales_order` および関連するテーブルには、顧客名、請求先住所、配送先住所、および関連するデータが含まれます。

#### `sales_order` 表

次の列 ( `sales_order` 表には、顧客情報が含まれます。

| 列 | データタイプ |
| --------------------- | ------------ |
| `customer_dob` | 日時 |
| `customer_email` | varchar(128) |
| `customer_firstname` | varchar(128) |
| `customer_gender` | int(11) |
| `customer_group_id` | int(11) |
| `customer_id` | int(10) |
| `customer_lastname` | varchar(128) |
| `customer_middlename` | varchar(128) |
| `customer_prefix` | varchar(32) |
| `customer_suffix` | varchar(32) |
| `customer_taxvat` | varchar(32) |
| `quote_address_id` | int(11) |
| `remote_ip` | varchar(32) |
| `x_forwarded_for` | varchar(32) |

#### `sales_order_address` 表

この `sales_order_address` テーブルには、顧客の住所が含まれます。

| 列 | データタイプ |
| --------------------- | ------------ |
| `customer_address_id` | int(11) |
| `quote_address_id` | int(11) |
| `region_id` | int(11) |
| `customer_id` | int(11) |
| `fax` | varchar(255) |
| `region` | varchar(255) |
| `postcode` | varchar(255) |
| `lastname` | varchar(255) |
| `street` | varchar(255) |
| `city` | varchar(255) |
| `email` | varchar(255) |
| `telephone` | varchar(255) |
| `country_id` | varchar(2) |
| `firstname` | varchar(255) |
| `suffix` | varchar(255) |
| `company` | varchar(255) |

#### `sales_order_grid` 表

次の列 ( `sales_order_grid` 表には、顧客情報が含まれます。

| 列 | データタイプ |
| ---------------------- | ------------ |
| `customer_id` | int(10) |
| `shipping_name` | varchar(255) |
| `billing_name` | varchar(255) |
| `billing_address` | varchar(255) |
| `shipping_address` | varchar(255) |
| `shipping_information` | varchar(255) |
| `customer_email` | varchar(255) |
| `customer_name` | varchar(255) |

### 見積もりデータ

引用符には、お客様の名前、電子メール、住所、関連情報が含まれます。

#### `quote` 表

次の列 ( `quote` 表には、顧客情報が含まれます。

| 列 | データタイプ |
| --------------------- | ------------ |
| `customer_id` | int(10) |
| `customer_email` | varchar(255) |
| `customer_prefix` | varchar(40) |
| `customer_firstname` | varchar(255) |
| `customer_middlename` | varchar(40) |
| `customer_lastname` | varchar(255) |
| `customer_dob` | 日時 |
| `remote_ip` | varchar(32) |
| `customer_taxvat` | varchar(255) |
| `customer_gender` | varchar(255) |

#### `quote_address` 表

次の列 ( `quote_address` 表には、顧客情報が含まれます。

| 列 | データタイプ |
| ------------- | ------------ |
| `customer_id` | int(10) |
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
| `region_id` | int(10) |
| `postcode` | varchar(20) |
| `country_id` | varchar(30) |
| `telephone` | varchar(255) |
| `fax` | varchar(255) |

### 支払いデータ

この `sales_order_payment` 表には、クレジットカード情報やその他のトランザクション情報が含まれます。

| 列 | データタイプ |
| ------------------------ | ------------ |
| `cc_exp_month` | varchar(12) |
| `echeck_bank_name` | varchar(128) |
| `cc_last_4` | varchar(100) |
| `cc_owner` | varchar(128) |
| `po_number` | varchar(32) |
| `cc_exp_year` | varchar(4) |
| `echeck_routing_number` | varchar(32) |
| `cc_debug_response_body` | varchar(32) |
| `echeck_account_name` | varchar(32) |
| `cc_number_enc` | varchar(128) |
| `additional_information` | テキスト |

### 招待データ

Adobe CommerceとMagento Open Sourceは、お客様がプライベートセールスやイベントに招待を送信できるように設定できます。

#### `magento_invitation` 表

この `magento_invitation` テーブルには、顧客 ID、電子メールおよび紹介 ID が含まれます。

| 列 | データタイプ |
| ------------- | ------------ |
| `customer_id` | int(10) |
| `email` | varchar(255) |
| `referral_id` | int(10) |

#### `magento_invitation_track` 表

この `magento_invitation_track` 「 」テーブルには、顧客情報も含まれます。

| 列 | データタイプ |
| ------------- | --------- |
| `inviter_id` | int(10) |
| `referral_id` | int(10) |

### 顧客を参照するその他のテーブル

次の表に、 `customer_id` 列：

- `catalog_compare_item`
- `catalog_product_frontend_action`
- `downloadable_link_purchased`
- `magento_customerbalance`
- `magento_customersegment_customer`
- `magento_reward`
- `magento_rma`
- `oauth_token`
- `paypal_billing_agreement`
- `persistent_session`
- `product_alert_price`
- `product_stock_alert`
- `report_compared_product_index`
- `report_viewed_product_index`
- `review_detail`
- `salesrule_coupon_usage`
- `salesrule_customer`
- `wishlist`
