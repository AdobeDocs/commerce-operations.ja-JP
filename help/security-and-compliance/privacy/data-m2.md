---
title: 顧客の個人情報の参照（バージョン 2.x）
description: Adobe Commerce 2.x におけるお客様の個人情報に関するデータフロー図とデータベースエンティティマッピングについて説明します。
exl-id: f08f4f93-a7b6-4c43-bc07-f159822dc528
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 0%

---

# 顧客の個人情報の参照（バージョン 2.x）

>[!NOTE]
>
>これは、Adobe Commerceのマーチャントやデベロッパーがプライバシー規制への準拠に備えるのに役立つ、一連のトピックの 1 つです。 自社のビジネスが法的義務に準拠する必要があるかどうか、またどのように準拠すべきかを判断するには、法務担当者に相談してください。

プライバシー規制に関するコンプライアンスプログラムを開発する際の参考として、次のデータフロー図とデータベースエンティティのマッピングを使用します。例えば、次のようなものがあります。

- [GDPR](gdpr.md)
- [CCPA](ccpa.md)

## データフロー図

データフロー図は、顧客および管理者がストアフロントおよび管理者から入力および取得できるデータのタイプを示しています。

### フロントエンドデータのエントリポイント

ユーザーは、アカウントの登録時、チェックアウト時などのイベントに、顧客、住所、支払い情報を入力できます。

![ フロントエンドデータエントリポイント ](../../assets/security-compliance/frontend-data-entry-points.svg)

### フロントエンド データ アクセス ポイント

Adobe Commerceは、ユーザーがログインして複数の異なるページを表示した場合、またはチェックアウトした場合に、ユーザー情報を読み込みます。

![ フロントエンドデータアクセスポイント ](../../assets/security-compliance/frontend-data-access-points.svg)

### バックエンドデータのエントリポイント

マーチャントは、管理者から顧客または注文を作成する際に、顧客情報、住所データおよび支払いデータを入力できます。

![ バックエンドデータエントリポイント ](../../assets/security-compliance/backend-data-entry-points.svg)

### バックエンドのデータアクセスポイント

Adobe Commerceは、マーチャントが複数のタイプのグリッドを表示したり、グリッドをクリックして詳細情報を表示したり、その他の様々なタスクを実行したりすると、顧客情報を読み込みます。

![ バックエンドのデータアクセスポイント ](../../assets/security-compliance/backend-data-access-points.svg)

## データベースエンティティ

Adobe Commerceは主に、お客様固有の情報を、お客様、住所、注文、見積もり、支払いの各テーブルに格納します。 その他のテーブルには、顧客 ID への参照が含まれます。

### 顧客データ

Adobe Commerceは、次の顧客属性を格納するように設定できます。

- 生年月日
- 電子メール
- 名前（名）
- 性別
- 名前（姓）
- ミドルネーム/イニシャル
- 名前のプレフィックス
- 名前サフィックス

>[!NOTE]
>
>現在のセキュリティとプライバシーのベストプラクティスに従って、顧客の完全な生年月日（月、日、年）と、フルネームなどのその他の個人識別子の保存に関連して発生する可能性のある法的およびセキュリティリスクを認識してから、そのようなデータを収集または処理してください。

#### `customer_entity` および「customer_entity」参照

顧客情報は、`customer_entity` テーブルの次のカラムに格納されます。

| 列 | データタイプ |
| ------------ | ------------ |
| `email` | varchar （255） |
| `prefix` | varchar （40） |
| `firstname` | varchar （255） |
| `middlename` | varchar （255） |
| `lastname` | varchar （255） |
| `suffix` | varchar （40） |
| `dob` | 日付 |
| `gender` | smallint （5） |

次の表は、`customer_entity` を参照し、カスタム顧客属性を含めることができます。

| テーブル | 列 | データタイプ |
| -------------------------- | ------- | ------------- |
| `customer_entity_datetime` | `value` | datetime |
| `customer_entity_decimal` | `value` | decimal （12,4） |
| `customer_entity_int` | `value` | int （11） |
| `customer_entity_text` | `value` | text |
| `customer_entity_varchar` | `value` | varchar （255） |

#### `customer_grid_flat` テーブル

顧客情報は、`customer_grid_flat` テーブルの次のカラムに格納されます。

| 列 | データタイプ |
| -------------------- | ------------ |
| `name` | text |
| `email` | varchar （255） |
| `dob` | 日付 |
| `gender` | int （11） |
| `shipping_full` | text |
| `billing_full` | text |
| `billing_firstname` | varchar （255） |
| `billing_lastname` | varchar （255） |
| `billing_telephone` | varchar （255） |
| `billing_postcode` | varchar （255） |
| `billing_country_id` | varchar （255） |
| `billing_region` | varchar （255） |
| `billing_city` | varchar （255） |
| `billing_fax` | varchar （255） |
| `billing_vat_id` | varchar （255） |
| `billing_company` | varchar （255） |

### アドレスデータ

Adobe Commerceには、次の顧客属性が格納されます。

- 市区町村
- 会社
- 国
- ファックス
- 名前（名）
- 名前（姓）
- ミドルネーム/イニシャル
- 名前のプレフィックス
- 名前サフィックス
- 電話番号
- 都道府県
- 都道府県 ID
- 番地
- VAT 番号
- 郵便番号

#### `customer_address_entity` と `customer_address_entity` の参照

顧客情報は、`customer_address_entity` テーブルの次のカラムに格納されます。

| 列 | データタイプ |
| ------------ | ------------ |
| `city` | varchar （255） |
| `company` | varchar （255） |
| `country_id` | varchar （255） |
| `fax` | varchar （255） |
| `firstname` | varchar （255） |
| `lastname` | varchar （255） |
| `middlename` | varchar （255） |
| `postcode` | varchar （255） |
| `region` | varchar （255） |
| `region_id` | int （10） |
| `street` | text |
| `suffix` | varchar （40） |
| `telephone` | varchar （255） |
| `vat_id` | varchar （255） |

次の表は、`customer_address_entity` を参照し、カスタム顧客属性を含めることができます。

| テーブル | 列 | データタイプ |
| ---------------------------------- | ------- | ------------- |
| `customer_address_entity_datetime` | `value` | datetime |
| `customer_address_entity_decimal` | `value` | decimal （12,4） |
| `customer_address_entity_int` | `value` | int （11） |
| `customer_address_entity_text` | `value` | text |
| `customer_address_entity_varchar` | `value` | varchar （255） |

### 注文データ

`sales_order` および関連するテーブルには、顧客名、請求先および配送先住所、関連するデータが含まれています。

#### `sales_order` テーブル

顧客情報は、`sales_order` テーブルの次のカラムに格納されます。

| 列 | データタイプ |
| --------------------- | ------------ |
| `customer_dob` | datetime |
| `customer_email` | varchar （128） |
| `customer_firstname` | varchar （128） |
| `customer_gender` | int （11） |
| `customer_group_id` | int （11） |
| `customer_id` | int （10） |
| `customer_lastname` | varchar （128） |
| `customer_middlename` | varchar （128） |
| `customer_prefix` | varchar （32） |
| `customer_suffix` | varchar （32） |
| `customer_taxvat` | varchar （32） |
| `quote_address_id` | int （11） |
| `remote_ip` | varchar （32） |
| `x_forwarded_for` | varchar （32） |

#### `sales_order_address` テーブル

`sales_order_address` テーブルには、顧客の住所が格納されます。

| 列 | データタイプ |
| --------------------- | ------------ |
| `customer_address_id` | int （11） |
| `quote_address_id` | int （11） |
| `region_id` | int （11） |
| `customer_id` | int （11） |
| `fax` | varchar （255） |
| `region` | varchar （255） |
| `postcode` | varchar （255） |
| `lastname` | varchar （255） |
| `street` | varchar （255） |
| `city` | varchar （255） |
| `email` | varchar （255） |
| `telephone` | varchar （255） |
| `country_id` | varchar （2） |
| `firstname` | varchar （255） |
| `suffix` | varchar （255） |
| `company` | varchar （255） |

#### `sales_order_grid` テーブル

顧客情報は、`sales_order_grid` テーブルの次のカラムに格納されます。

| 列 | データタイプ |
| ---------------------- | ------------ |
| `customer_id` | int （10） |
| `shipping_name` | varchar （255） |
| `billing_name` | varchar （255） |
| `billing_address` | varchar （255） |
| `shipping_address` | varchar （255） |
| `shipping_information` | varchar （255） |
| `customer_email` | varchar （255） |
| `customer_name` | varchar （255） |

### 見積データ

見積もりには、顧客の名前、メールアドレス、住所、および関連情報が含まれています。

#### `quote` テーブル

顧客情報は、`quote` テーブルの次のカラムに格納されます。

| 列 | データタイプ |
| --------------------- | ------------ |
| `customer_id` | int （10） |
| `customer_email` | varchar （255） |
| `customer_prefix` | varchar （40） |
| `customer_firstname` | varchar （255） |
| `customer_middlename` | varchar （40） |
| `customer_lastname` | varchar （255） |
| `customer_dob` | datetime |
| `remote_ip` | varchar （32） |
| `customer_taxvat` | varchar （255） |
| `customer_gender` | varchar （255） |

#### `quote_address` テーブル

顧客情報は、`quote_address` テーブルの次のカラムに格納されます。

| 列 | データタイプ |
| ------------- | ------------ |
| `customer_id` | int （10） |
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
| `region_id` | int （10） |
| `postcode` | varchar （20） |
| `country_id` | varchar （30） |
| `telephone` | varchar （255） |
| `fax` | varchar （255） |

### 支払いデータ

`sales_order_payment` テーブルは、クレジットカード情報およびその他のトランザクション情報を含む。

| 列 | データタイプ |
| ------------------------ | ------------ |
| `cc_exp_month` | varchar （12） |
| `echeck_bank_name` | varchar （128） |
| `cc_last_4` | varchar （100） |
| `cc_owner` | varchar （128） |
| `po_number` | varchar （32） |
| `cc_exp_year` | varchar （4） |
| `echeck_routing_number` | varchar （32） |
| `cc_debug_response_body` | varchar （32） |
| `echeck_account_name` | varchar （32） |
| `cc_number_enc` | varchar （128） |
| `additional_information` | text |

### 招待データ

Adobe Commerceは、顧客が個人の営業やイベントへの招待状を送信できるように設定できます。

#### `magento_invitation` テーブル

`magento_invitation` テーブルには、顧客 ID、メールおよびリファラル ID が含まれます。

| 列 | データタイプ |
| ------------- | ------------ |
| `customer_id` | int （10） |
| `email` | varchar （255） |
| `referral_id` | int （10） |

#### `magento_invitation_track` テーブル

`magento_invitation_track` の表には、顧客情報も含まれています。

| 列 | データタイプ |
| ------------- | --------- |
| `inviter_id` | int （10） |
| `referral_id` | int （10） |

### 顧客を参照するその他のテーブル

次のテーブルには、`customer_id` の列が含まれています。

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
