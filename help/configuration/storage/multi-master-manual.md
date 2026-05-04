---
title: マスターデータベースの手動設定
description: スプリットデータベースソリューションの手動での設定に関するガイダンスを参照してください。
recommendations: noCatalog
exl-id: 2c357486-4a8a-4a36-9e13-b53c83f69456
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '1391'
ht-degree: 0%

---

# マスターデータベースの手動設定

{{ee-only}}

{{deprecate-split-db}}

Commerce アプリケーションが既に実稼動環境にある場合や、カスタムコードまたはコンポーネントを既にインストールしている場合は、スプリットデータベースを手動で設定する必要がある場合があります。 続行する前に、Adobe Commerce サポートにお問い合わせいただき、この操作が必要かどうかを確認してください。

データベースを手動で分割するには、次の操作が必要です。

- チェックアウトおよび注文管理システム（OMS）データベースの作成
- 次のような一連のSQL スクリプトを実行します。

   - 外部キーをドロップ
   - セールスおよび見積データベース テーブルのバックアップ
   - テーブルをメイン データベースからセールス データベースおよび見積データベースに移動する

>[!WARNING]
>
>任意のカスタムコードがSALESおよびQuote データベースのテーブルとJOINを使用している場合、_では_&#x200B;分割データベースを使用できません。 不明な場合は、カスタムコードまたは拡張機能の作成者に連絡して、コードがJOINを使用していないことを確認してください。

このトピックでは、次の命名規則を使用します。

- メインデータベース名は`magento`で、ユーザー名とパスワードはどちらも`magento`です
- 見積データベース名は`magento_quote`で、ユーザー名とパスワードは両方とも`magento_quote`です

  見積もりデータベースは、_チェックアウト_ データベースとも呼ばれます。

- 営業データベース名は`magento_sales`で、ユーザー名とパスワードはどちらも`magento_sales`です

  セールスデータベースは、OMS データベースとも呼ばれます。

>[!INFO]
>
>このガイドでは、3つのデータベースがすべてCommerce アプリケーションと同じホスト上にあることを前提としています。 ただし、データベースの場所と名前を指定する場所は、ユーザーが選択します。 私たちの例が指示を従いやすくすることを願っています。

## Commerce システムのバックアップ

Adobeでは、プロセス中に問題が発生した場合に復元できるように、現在のデータベースとファイルシステムをバックアップすることを強くお勧めします。

**システムをバックアップするには**:

1. [ ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md)としてCommerce サーバーにログインするか、切り替えます。
1. 次のコマンドを入力します。

   ```shell
   magento setup:backup --code --media --db
   ```

1. 次のセクションに進みます。

## 追加のマスターデータベースの設定

この節では、セールスと見積もりテーブルのデータベースインスタンスを作成する方法について説明します。

**セールスおよびOMS見積データベースを作成するには**:

1. 任意のユーザーとしてデータベース・サーバにログインします。
1. 次のコマンドを入力して、MySQL コマンドプロンプトにアクセスします。

   ```shell
   mysql -u root -p
   ```

1. プロンプトが表示されたら、MySQL `root` ユーザーのパスワードを入力します。
1. 同じユーザー名とパスワードを使用して`magento_quote`と`magento_sales`という名前のデータベース インスタンスを作成するには、次のコマンドを順に入力します。

   ```shell
   create database magento_quote;
   GRANT ALL ON magento_quote.* TO magento_quote@localhost IDENTIFIED BY 'magento_quote';
   ```

   ```shell
   create database magento_sales;
   GRANT ALL ON magento_sales.* TO magento_sales@localhost IDENTIFIED BY 'magento_sales';
   ```

1. コマンド プロンプトを終了するには、`exit`と入力します。

1. データベースを1つずつ確認します。

   見積もりデータベース：

   ```shell
   mysql -u magento_quote -p
   ```

   ```shell
   exit
   ```

   ```shell
   mysql -u magento_quote -p
   ```

   ```shell
   mysql -u magento_sales -p
   ```

   ```shell
   exit
   ```

   MySQL モニターが表示される場合は、データベースを適切に作成しました。 エラーが表示された場合は、上記のコマンドを繰り返します。

1. 次のセクションに進みます。

## セールスデータベースの設定

この節では、引用符データベーステーブルを変更し、それらのテーブルからデータをバックアップするSQL スクリプトを作成および実行する方法について説明します。

セールスデータベースのテーブル名は次で始まります。

- `salesrule_`
- `sales_`
- `magento_sales_`
- `magento_customercustomattributes_sales_flat_order` テーブルにも影響があります

>[!INFO]
>
>このセクションには、特定のデータベーステーブル名を持つスクリプトが含まれます。 カスタマイズを実行した場合、またはアクションを実行する前にテーブルの完全なリストを表示する場合は、[参照スクリプト ](#reference-scripts)を参照してください。

詳細は、次を参照してください。

- [セールスデータベース SQL スクリプトの作成](#create-sales-database-sql-scripts)
- [販売データのバックアップ](#back-up-sales-data)

### セールスデータベース SQL スクリプトの作成

次のSQL スクリプトは、Commerce サーバーにログインするユーザーがアクセスできる場所に作成します。 例えば、コマンドを`root`としてログインまたは実行する場合、`/root/sql-scripts` ディレクトリにスクリプトを作成できます。

#### 外部キーの削除

このスクリプトは、セールスデータベースからセールス以外のテーブルを参照する外部キーを削除します。

次のスクリプトを作成し、`1_foreign-sales.sql`のような名前を付けます。 `<your main DB name>`をデータベースの名前に置き換えます。

```sql
use <your main DB name>;
ALTER TABLE salesrule_coupon_aggregated_order DROP FOREIGN KEY SALESRULE_COUPON_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_coupon_aggregated DROP FOREIGN KEY SALESRULE_COUPON_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_coupon_aggregated_updated DROP FOREIGN KEY SALESRULE_COUPON_AGGREGATED_UPDATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_coupon_usage DROP FOREIGN KEY SALESRULE_COUPON_USAGE_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE salesrule_customer_group DROP FOREIGN KEY SALESRULE_CSTR_GROUP_CSTR_GROUP_ID_CSTR_GROUP_CSTR_GROUP_ID;
ALTER TABLE salesrule_customer DROP FOREIGN KEY SALESRULE_CUSTOMER_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE salesrule_label DROP FOREIGN KEY SALESRULE_LABEL_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_product_attribute DROP FOREIGN KEY SALESRULE_PRD_ATTR_ATTR_ID_EAV_ATTR_ATTR_ID;
ALTER TABLE salesrule_product_attribute DROP FOREIGN KEY SALESRULE_PRD_ATTR_CSTR_GROUP_ID_CSTR_GROUP_CSTR_GROUP_ID;
ALTER TABLE salesrule_product_attribute DROP FOREIGN KEY SALESRULE_PRODUCT_ATTRIBUTE_WEBSITE_ID_STORE_WEBSITE_WEBSITE_ID;
ALTER TABLE salesrule_website DROP FOREIGN KEY SALESRULE_WEBSITE_WEBSITE_ID_STORE_WEBSITE_WEBSITE_ID;
ALTER TABLE sales_bestsellers_aggregated_daily DROP FOREIGN KEY SALES_BESTSELLERS_AGGRED_DAILY_PRD_ID_CAT_PRD_ENTT_ENTT_ID;
ALTER TABLE sales_bestsellers_aggregated_monthly DROP FOREIGN KEY SALES_BESTSELLERS_AGGRED_MONTHLY_PRD_ID_CAT_PRD_ENTT_ENTT_ID;
ALTER TABLE sales_bestsellers_aggregated_yearly DROP FOREIGN KEY SALES_BESTSELLERS_AGGRED_YEARLY_PRD_ID_CAT_PRD_ENTT_ENTT_ID;
ALTER TABLE sales_bestsellers_aggregated_daily DROP FOREIGN KEY SALES_BESTSELLERS_AGGREGATED_DAILY_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_bestsellers_aggregated_monthly DROP FOREIGN KEY SALES_BESTSELLERS_AGGREGATED_MONTHLY_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_bestsellers_aggregated_yearly DROP FOREIGN KEY SALES_BESTSELLERS_AGGREGATED_YEARLY_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_creditmemo_grid DROP FOREIGN KEY SALES_CREDITMEMO_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_creditmemo DROP FOREIGN KEY SALES_CREDITMEMO_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoiced_aggregated_order DROP FOREIGN KEY SALES_INVOICED_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoiced_aggregated DROP FOREIGN KEY SALES_INVOICED_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoice_grid DROP FOREIGN KEY SALES_INVOICE_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoice DROP FOREIGN KEY SALES_INVOICE_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_aggregated_created DROP FOREIGN KEY SALES_ORDER_AGGREGATED_CREATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_aggregated_updated DROP FOREIGN KEY SALES_ORDER_AGGREGATED_UPDATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order DROP FOREIGN KEY SALES_ORDER_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE sales_order_grid DROP FOREIGN KEY SALES_ORDER_GRID_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE sales_order_grid DROP FOREIGN KEY SALES_ORDER_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_item DROP FOREIGN KEY SALES_ORDER_ITEM_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_status_label DROP FOREIGN KEY SALES_ORDER_STATUS_LABEL_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order DROP FOREIGN KEY SALES_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_refunded_aggregated_order DROP FOREIGN KEY SALES_REFUNDED_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_refunded_aggregated DROP FOREIGN KEY SALES_REFUNDED_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipment_grid DROP FOREIGN KEY SALES_SHIPMENT_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipment DROP FOREIGN KEY SALES_SHIPMENT_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipping_aggregated_order DROP FOREIGN KEY SALES_SHIPPING_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipping_aggregated DROP FOREIGN KEY SALES_SHIPPING_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_creditmemo_grid_archive DROP FOREIGN KEY MAGENTO_SALES_CREDITMEMO_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_invoice_grid_archive DROP FOREIGN KEY MAGENTO_SALES_INVOICE_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_order_grid_archive DROP FOREIGN KEY MAGENTO_SALES_ORDER_GRID_ARCHIVE_CSTR_ID_CSTR_ENTT_ENTT_ID;
ALTER TABLE magento_sales_order_grid_archive DROP FOREIGN KEY MAGENTO_SALES_ORDER_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_shipment_grid_archive DROP FOREIGN KEY MAGENTO_SALES_SHIPMENT_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE downloadable_link_purchased_item DROP FOREIGN KEY DL_LNK_PURCHASED_ITEM_ORDER_ITEM_ID_SALES_ORDER_ITEM_ITEM_ID;
ALTER TABLE downloadable_link_purchased DROP FOREIGN KEY DOWNLOADABLE_LINK_PURCHASED_ORDER_ID_SALES_ORDER_ENTITY_ID;
ALTER TABLE paypal_billing_agreement_order DROP FOREIGN KEY PAYPAL_BILLING_AGREEMENT_ORDER_ORDER_ID_SALES_ORDER_ENTITY_ID;
```

### セールスデータベースの設定

前のスクリプトを実行します。

1. MySQL データベースに`root`または管理ユーザーとしてログインします。

   ```shell
   mysql -u root -p
   ```

1. `mysql>` プロンプトで、次のようにスクリプトを実行します。

   ```shell
   source <path>/<script>.sql
   ```

   以下に例を挙げます。

   ```shell
   source /root/sql-scripts/1_foreign-sales.sql
   ```

1. スクリプトの実行後、`exit`と入力します。

### 販売データのバックアップ

この節では、メインのCommerce データベースからセールステーブルをバックアップし、セールスデータベースに復元する方法について説明します。

現在`mysql>` プロンプトを使用している場合は、`exit`と入力してコマンドシェルに戻ります。

コマンドシェルから次の`mysqldump` コマンドを1つずつ実行します。 それぞれの場合は、次のように置き換えます。

- `<your database root username>`をデータベース ルート ユーザーの名前に置き換えます
- `<your database root user password>`とユーザーのパスワード
- `<your main Commerce DB name>`をCommerce データベースの名前に置き換えます
- 書き込み可能なファイル システム パスを持つ`<path>`

#### スクリプト 1

```shell
mysqldump -u <your database root username> -p <your main Commerce DB name> sales_bestsellers_aggregated_daily sales_bestsellers_aggregated_monthly sales_bestsellers_aggregated_yearly sales_creditmemo sales_creditmemo_comment sales_creditmemo_grid sales_creditmemo_item sales_invoice sales_invoice_comment sales_invoice_grid sales_invoice_item sales_invoiced_aggregated sales_invoiced_aggregated_order sales_order sales_order_address sales_order_aggregated_created sales_order_aggregated_updated sales_order_grid sales_order_item sales_order_payment sales_order_status sales_order_status_history sales_order_status_label sales_order_status_state sales_order_tax sales_order_tax_item sales_payment_transaction sales_refunded_aggregated sales_refunded_aggregated_order sales_sequence_meta sales_sequence_profile sales_shipment sales_shipment_comment sales_shipment_grid sales_shipment_item sales_shipment_track sales_shipping_aggregated sales_shipping_aggregated_order > /<path>/sales.sql
```

#### スクリプト 2

```shell
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_sales_creditmemo_grid_archive magento_sales_invoice_grid_archive magento_sales_order_grid_archive magento_sales_shipment_grid_archive > /<path>/salesarchive.sql
```

#### スクリプト 3

```shell
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_customercustomattributes_sales_flat_order magento_customercustomattributes_sales_flat_order_address > /<path>/customercustomattributes.sql
```

#### スクリプト 4

```shell
mysqldump -u <your database root username> -p <your main Commerce DB name> sequence_creditmemo_0 sequence_creditmemo_1 sequence_invoice_0 sequence_invoice_1 sequence_order_0 sequence_order_1 sequence_rma_item_0 sequence_rma_item_1 sequence_shipment_0 sequence_shipment_1 > /<path>/sequence.sql
```

### 販売データの復元

このスクリプトは、見積データベースの販売データを復元します。

#### NDB要件

[Network Database （NDB） ](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html) クラスターを使用している場合：

1. InnoDbからダンプファイルのNDB タイプにテーブルを変換する：

   ```shell
   sed -ei 's/InnoDb/NDB/' <file name>.sql
   ```

1. NDB テーブルではFULLTEXTがサポートされていないため、FULLTEXT キーを持つ行をダンプから削除します。

#### データの復元

次のコマンドを実行します。

```shell
mysql -u <root username> -p <your sales DB name> < /<path>/sales.sql
```

```shell
mysql -u <root username> -p <your sales DB name> < /<path>/sequence.sql
```

```shell
mysql -u <root username> -p <your sales DB name> < /<path>/salesarchive.sql
```

```shell
mysql -u <root username> -p <your sales DB name> < /<path>/customercustomattributes.sql
```

どこで

- `<your sales DB name>`をセールスデータベースの名前に置き換えます。

  このトピックでは、サンプル データベース名は`magento_sales`です。

- `<root username>`をMySQL ルートのユーザー名で指定します
- `<root user password>`とユーザーのパスワード
- 前に作成したバックアップ ファイルの場所を確認します（例：`/var/sales.sql`）

## 見積データベースの設定

この節では、セールスデータベースのテーブルから外部キーを削除し、テーブルをセールスデータベースに移動するために必要なタスクについて説明します。

>[!INFO]
>
>このセクションには、特定のデータベーステーブル名を持つスクリプトが含まれます。 カスタマイズを実行した場合、またはアクションを実行する前にテーブルの完全なリストを表示する場合は、[参照スクリプト ](#reference-scripts)を参照してください。

見積データベース テーブル名は`quote`で始まります。 `magento_customercustomattributes_sales_flat_quote`および`magento_customercustomattributes_sales_flat_quote_address` テーブルも影響を受けます

### 引用符テーブルから外部キーをドロップする

このスクリプトは、引用符で囲まれたテーブル以外のテーブルを参照する外部キーを引用符で囲まれたテーブルから削除します。 `<your main Commerce DB name>`をCommerce データベースの名前に置き換えます。

次のスクリプトを作成し、`2_foreign-key-quote.sql`のような名前を付けます。

```sql
use <your main DB name>;
ALTER TABLE quote DROP FOREIGN KEY QUOTE_STORE_ID_STORE_STORE_ID;
ALTER TABLE quote_item DROP FOREIGN KEY QUOTE_ITEM_PRODUCT_ID_CATALOG_PRODUCT_ENTITY_ENTITY_ID;
ALTER TABLE quote_item DROP FOREIGN KEY QUOTE_ITEM_STORE_ID_STORE_STORE_ID;
```

次のようにスクリプトを実行します。

1. MySQL データベースにroot ユーザーまたは管理ユーザーとしてログインします。

   ```shell
   mysql -u root -p
   ```

1. `mysql >` プロンプトで、次のようにスクリプトを実行します。
   `source <path>/<script>.sql`

   以下に例を挙げます。

   ```shell
   source /root/sql-scripts/2_foreign-key-quote.sql
   ```

1. スクリプトが実行されたら、`exit`と入力します。

### 見積もりテーブルのバックアップ

この節では、メイン・データベースから見積テーブルをバックアップし、見積データベースに復元する方法について説明します。

コマンドプロンプトから次のコマンドを実行します。

```shell
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_customercustomattributes_sales_flat_quote magento_customercustomattributes_sales_flat_quote_address quote quote_address quote_address_item quote_item quote_item_option quote_payment quote_shipping_rate quote_id_mask > /<path>/quote.sql;
```

### NDB要件

[Network Database （NDB） ](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html) クラスターを使用している場合：

1. InnoDbからダンプファイルのNDB タイプにテーブルを変換する：

   ```shell
   sed -ei 's/InnoDb/NDB/' <file name>.sql
   ```

1. NDB テーブルではFULLTEXTがサポートされていないため、FULLTEXT キーを持つ行をダンプから削除します。

### テーブルを見積データベースに復元する

```shell
mysql -u root -p magento_quote < /<path>/quote.sql
```

## データベースから売上表と見積もり表を削除します

このスクリプトは、Commerce データベースのセールスと見積もりテーブルを示します。 `<your main DB name>`をCommerce データベースの名前に置き換えます。

次のスクリプトを作成し、`3_drop-tables.sql`のような名前を付けます。

```sql
use <your main DB name>;
SET foreign_key_checks = 0;
DROP TABLE magento_customercustomattributes_sales_flat_quote;
DROP TABLE magento_customercustomattributes_sales_flat_quote_address;
DROP TABLE quote;
DROP TABLE quote_address;
DROP TABLE quote_address_item;
DROP TABLE quote_item;
DROP TABLE quote_item_option;
DROP TABLE quote_payment;
DROP TABLE quote_shipping_rate;
DROP TABLE quote_id_mask;
DROP TABLE sales_bestsellers_aggregated_daily;
DROP TABLE sales_bestsellers_aggregated_monthly;
DROP TABLE sales_bestsellers_aggregated_yearly;
DROP TABLE sales_creditmemo;
DROP TABLE sales_creditmemo_comment;
DROP TABLE sales_creditmemo_grid;
DROP TABLE sales_creditmemo_item;
DROP TABLE sales_invoice;
DROP TABLE sales_invoice_comment;
DROP TABLE sales_invoice_grid;
DROP TABLE sales_invoice_item;
DROP TABLE sales_invoiced_aggregated;
DROP TABLE sales_invoiced_aggregated_order;
DROP TABLE sales_order;
DROP TABLE sales_order_address;
DROP TABLE sales_order_aggregated_created;
DROP TABLE sales_order_aggregated_updated;
DROP TABLE sales_order_grid;
DROP TABLE sales_order_item;
DROP TABLE sales_order_payment;
DROP TABLE sales_order_status;
DROP TABLE sales_order_status_history;
DROP TABLE sales_order_status_label;
DROP TABLE sales_order_status_state;
DROP TABLE sales_order_tax;
DROP TABLE sales_order_tax_item;
DROP TABLE sales_payment_transaction;
DROP TABLE sales_refunded_aggregated;
DROP TABLE sales_refunded_aggregated_order;
DROP TABLE sales_sequence_meta;
DROP TABLE sales_sequence_profile;
DROP TABLE sales_shipment;
DROP TABLE sales_shipment_comment;
DROP TABLE sales_shipment_grid;
DROP TABLE sales_shipment_item;
DROP TABLE sales_shipment_track;
DROP TABLE sales_shipping_aggregated;
DROP TABLE sales_shipping_aggregated_order;
DROP TABLE magento_sales_creditmemo_grid_archive;
DROP TABLE magento_sales_invoice_grid_archive;
DROP TABLE magento_sales_order_grid_archive;
DROP TABLE magento_sales_shipment_grid_archive;
DROP TABLE magento_customercustomattributes_sales_flat_order;
DROP TABLE magento_customercustomattributes_sales_flat_order_address;
DROP TABLE sequence_creditmemo_0;
DROP TABLE sequence_creditmemo_1;
DROP TABLE sequence_invoice_0;
DROP TABLE sequence_invoice_1;
DROP TABLE sequence_order_0;
DROP TABLE sequence_order_1;
DROP TABLE sequence_rma_item_0;
DROP TABLE sequence_rma_item_1;
DROP TABLE sequence_shipment_0;
DROP TABLE sequence_shipment_1;
SET foreign_key_checks = 1;
```

次のようにスクリプトを実行します。

1. MySQL データベースにroot ユーザーまたは管理ユーザーとしてログインします。

   ```shell
   mysql -u root -p
   ```

1. `mysql>` プロンプトで、次のようにスクリプトを実行します。

   ```shell
   source <path>/<script>.sql
   ```

   以下に例を挙げます。

   ```shell
   source /root/sql-scripts/3_drop-tables.sql
   ```

1. スクリプトが実行されたら、`exit`と入力します。

## デプロイメント設定の更新

データベースを手動で分割する最後の手順は、Commerceのデプロイメント設定`env.php`に接続とリソース情報を追加することです。

デプロイメント設定を更新するには：

1. [ ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md)としてCommerce サーバーにログインするか、切り替えます。
1. デプロイメント設定をバックアップします。

   ```shell
   cp <magento_root>/app/etc/env.php <magento_root>/app/etc/env.php.orig
   ```

1. `<magento_root>/app/etc/env.php`をテキストエディターで開き、次の節で説明するガイドラインを使用して更新します。

### データベース接続の更新

`'default'`で始まるブロック（`'connection'`の下）を見つけ、`'checkout'`および`'sales'`個のセクションを追加します。 サンプル値をサイトに適した値に置き換えます。

```php
 'default' =>
      array (
'host' => 'localhost',
'dbname' => 'magento',
'username' => 'magento',
'password' => 'magento',
'model' => 'mysql4',
'engine' => 'innodb',
'initStatements' => 'SET NAMES utf8;',
'active' => '1',
      ),
      'checkout' =>
      array (
'host' => 'localhost',
'dbname' => 'magento_quote',
'username' => 'magento_quote',
'password' => 'magento_quote',
'model' => 'mysql4',
'engine' => 'innodb',
'initStatements' => 'SET NAMES utf8;',
'active' => '1',
      ),
      'sales' =>
      array (
'host' => 'localhost',
'dbname' => 'magento_sales',
'username' => 'magento_sales',
'password' => 'magento_sales',
'model' => 'mysql4',
'engine' => 'innodb',
'initStatements' => 'SET NAMES utf8;',
'active' => '1',
      ),
    ),
```

### リソースの更新

`'resource'`で始まるブロックを見つけ、次のように`'checkout'`および`'sales'` セクションを追加します。

```php
'resource' =>
  array (
    'default_setup' =>
    array (
      'connection' => 'default',
    ),
    'checkout' =>
    array (
      'connection' => 'checkout',
    ),
    'sales' =>
    array (
      'connection' => 'sales',
    ),
```

## 参照スクリプト

この節では、影響を受けるテーブルの完全なリストを印刷するスクリプトを提供します。 データベースを手動で分割する前に、それらを使用して影響を受けるテーブルを確認できます。これは、データベーススキーマをカスタマイズする拡張機能を使用する場合に便利です。

これらのスクリプトを使用するには：

1. この節の各スクリプトの内容を含むSQL スクリプトを作成します。
1. 各スクリプトで、`<your main DB name>`をCommerce データベースの名前に置き換えます。

   このトピックでは、サンプル データベース名は`magento`です。

1. `mysql>` プロンプトから各スクリプトを`source <script name>`として実行します
1. 出力の検証：
1. 各スクリプトの結果を別のSQL スクリプトにコピーし、パイプ文字（`|`）を削除します。
1. `mysql>` プロンプトから各スクリプトを`source <script name>`として実行します。

   この2つ目のスクリプトを実行すると、メインのCommerce データベースでアクションが実行されます。

### 外部キー（販売テーブル）の削除

このスクリプトは、セールスデータベースからセールス以外のテーブルを参照する外部キーを削除します。

```sql
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like  '<your main DB name>/|sales_%' escape '|'
    and ref_name not like  '<your main DB name>/|sales_%' escape '|'
union all
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like  '<your main DB name>/|magento_sales|_%' escape '|'
    and ref_name not like  '<your main DB name>/|sales|_%' escape '|'
;
```

### 外部キー（引用テーブル）の削除

このスクリプトは、引用符で囲まれたテーブル以外のテーブルを参照する外部キーを引用符で囲まれたテーブルから削除します。

```sql
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like '<your main DB name>/%'
    and ref_name like '<your main DB name>/sales\_%'
union all
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like '<your main DB name>/%'
    and ref_name like '<your main DB name>/magento_sales\_%'
union all
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like '<your main DB name>/%'
    and ref_name like '<your main DB name>/magento_customercustomattributes\_%'
;
```

### 販売テーブルのドロップ

このスクリプトは、Commerce データベースからセールステーブルを削除します。

```sql
use <your main DB name>;
select ' SET foreign_key_checks = 0;' as querytext
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'sales/_%' escape '/'
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'magento_sales/_%' escape '/'
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'magento_customercustomattributes_sales_flat_order%' escape '/'
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'sequence/_%' escape '/'
union all
select 'SET foreign_key_checks = 1;';
```

### 引用テーブルをドロップ

`quote_`で始まるすべてのテーブルをドロップします。
