---
title: マスターデータベースを手動で構成する
description: 分割データベースソリューションを手動で設定する方法については、ガイダンスを参照してください。
recommendations: noCatalog
exl-id: 2c357486-4a8a-4a36-9e13-b53c83f69456
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '1373'
ht-degree: 0%

---

# マスターデータベースを手動で構成する

{{ee-only}}

{{deprecate-split-db}}

Commerce アプリケーションが既に実稼動環境にある場合や、カスタムコードまたはコンポーネントが既にインストールされている場合は、分割データベースを手動で設定する必要がある可能性があります。 続行する前に、Adobe Commerce サポートに連絡して、現在のケースでこれが必要かどうかを確認してください。

データベースを手動で分割するには、次の操作を行います。

- チェックアウトおよび注文管理システム（OMS）データベースの作成
- 次の一連の SQL スクリプトを実行します。

   - 外部キーをドロップ
   - 販売および見積データベース テーブルのバックアップ
   - テーブルをメイン データベースから販売データベースおよび見積データベースに移動する

>[!WARNING]
>
>カスタム・コードで sales および quote データベースのテーブルとの JOIN を使用する場合は、 _できません_ 分割データベースを使用します。 不明な場合は、カスタムコードまたは拡張機能の作成者に問い合わせて、そのコードで JOIN が使用されていないことを確認してください。

このトピックでは、次の命名規則を使用します。

- メインデータベース名はです。 `magento` およびそのユーザー名とパスワードは両方とも `magento`
- 引用符データベース名は `magento_quote` およびそのユーザー名とパスワードは両方とも `magento_quote`

  見積もりデータベースは、 _チェックアウト_ データベース。

- 営業データベース名はです `magento_sales` およびそのユーザー名とパスワードは両方とも `magento_sales`

  販売データベースは、OMS データベースとも呼ばれます。

>[!INFO]
>
>このガイドでは、3 つのデータベースがすべてCommerce アプリケーションと同じホスト上にあることを前提としています。 ただし、データベースの場所とデータベースの名前はユーザーが選択できます。 私たちの例が指示に従いやすくなることを願っています。

## Commerce システムのバックアップ

Adobeでは、処理中に問題が発生した場合に復元できるように、現在のデータベースとファイルシステムをバックアップすることを強くお勧めします。

**システムをバックアップするには**:

1. Commerce サーバーにとしてログインするか、に切り替えます [ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md).
1. 次のコマンドを入力します。

   ```bash
   magento setup:backup --code --media --db
   ```

1. 次の節に進みます。

## 追加のマスターデータベースを設定する

この項では、販売テーブルと見積テーブルのデータベース・インスタンスを作成する方法について説明します。

**販売および OMS 見積データベースを作成する手順は、次のとおりです**:

1. 任意のユーザーとしてデータベースサーバーにログインします。
1. 次のコマンドを入力して、MySQL コマンドプロンプトを表示します。

   ```bash
   mysql -u root -p
   ```

1. MySQL を入力 `root` プロンプトが表示されたらユーザーのパスワードを入力します。
1. 次のコマンドを表示されている順序で入力して、という名前のデータベースインスタンスを作成します。 `magento_quote` および `magento_sales` ユーザー名とパスワードが同じ場合：

   ```shell
   create database magento_quote;
   GRANT ALL ON magento_quote.* TO magento_quote@localhost IDENTIFIED BY 'magento_quote';
   ```

   ```shell
   create database magento_sales;
   GRANT ALL ON magento_sales.* TO magento_sales@localhost IDENTIFIED BY 'magento_sales';
   ```

1. Enter `exit` をクリックして、コマンドプロンプトを終了します。

1. データベースを 1 つずつ検証します。

   見積もりデータベース：

   ```bash
   mysql -u magento_quote -p
   ```

   ```shell
   exit
   ```

   ```bash
   mysql -u magento_quote -p
   ```

   ```bash
   mysql -u magento_sales -p
   ```

   ```shell
   exit
   ```

   MySQL モニターが表示された場合は、データベースが正しく作成されています。 エラーが表示された場合は、上記のコマンドを繰り返します。

1. 次の節に進みます。

## 販売データベースの設定

この項では、引用符データベース・テーブルを変更し、それらのテーブルのデータをバックアップする SQL スクリプトを作成および実行する方法について説明します。

Sales データベースのテーブル名は次で始まります：

- `salesrule_`
- `sales_`
- `magento_sales_`
- この `magento_customercustomattributes_sales_flat_order` テーブルにも影響があります

>[!INFO]
>
>このセクションには、特定のデータベーステーブル名を持つスクリプトが含まれています。 カスタマイズを実行した場合、またはアクションを実行する前にテーブルの完全なリストを確認する場合は、を参照してください [参照スクリプト](#reference-scripts).

詳しくは、以下を参照してください。

- [Sales データベースの SQL スクリプトの作成](#create-sales-database-sql-scripts)
- [販売データのバックアップ](#back-up-sales-data)

### Sales データベースの SQL スクリプトの作成

Commerce サーバーにログインしたユーザーがアクセスできる場所に、次の SQL スクリプトを作成します。 例えば、次のようにログインまたはコマンドを実行した場合 `root`で作成します。でスクリプトを作成できます `/root/sql-scripts` ディレクトリ。

#### 外部キーの削除

このスクリプトは、sales データベースから sales 以外のテーブルを参照する外部キーを削除します。

次のスクリプトを作成し、のような名前を付けます。 `1_foreign-sales.sql`. 置換 `<your main DB name>` 使用するデータベースの名前。

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

### 販売データベースの設定

上記のスクリプトを実行します。

1. MySQL データベースにとしてログインします。 `root` または管理ユーザー：

   ```bash
   mysql -u root -p
   ```

1. 時刻 `mysql>` プロンプトが表示されたら、次のようにスクリプトを実行します。

   ```shell
   source <path>/<script>.sql
   ```

   以下に例を挙げます。

   ```shell
   source /root/sql-scripts/1_foreign-sales.sql
   ```

1. スクリプトの実行後、と入力します `exit`.

### 販売データのバックアップ

この項では、メインのCommerceデータベースから sales テーブルをバックアップして、別の sales データベースにリストアできるようにする方法について説明します。

現在ステータスが `mysql>` プロンプト，enter `exit` コマンド シェルに戻ります。

次を実行します `mysqldump` コマンド シェルからコマンドを 1 つずつ実行します。 それぞれに、以下を置き換えます。

- `<your database root username>` とデータベースルートユーザーの名前
- `<your database root user password>` （ユーザーのパスワードを使用）
- `<your main Commerce DB name>` （Commerce データベースの名前を使用）
- `<path>` 書き込み可能なファイルシステムパス

#### スクリプト 1

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> sales_bestsellers_aggregated_daily sales_bestsellers_aggregated_monthly sales_bestsellers_aggregated_yearly sales_creditmemo sales_creditmemo_comment sales_creditmemo_grid sales_creditmemo_item sales_invoice sales_invoice_comment sales_invoice_grid sales_invoice_item sales_invoiced_aggregated sales_invoiced_aggregated_order sales_order sales_order_address sales_order_aggregated_created sales_order_aggregated_updated sales_order_grid sales_order_item sales_order_payment sales_order_status sales_order_status_history sales_order_status_label sales_order_status_state sales_order_tax sales_order_tax_item sales_payment_transaction sales_refunded_aggregated sales_refunded_aggregated_order sales_sequence_meta sales_sequence_profile sales_shipment sales_shipment_comment sales_shipment_grid sales_shipment_item sales_shipment_track sales_shipping_aggregated sales_shipping_aggregated_order > /<path>/sales.sql
```

#### スクリプト 2

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_sales_creditmemo_grid_archive magento_sales_invoice_grid_archive magento_sales_order_grid_archive magento_sales_shipment_grid_archive > /<path>/salesarchive.sql
```

#### スクリプト 3

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_customercustomattributes_sales_flat_order magento_customercustomattributes_sales_flat_order_address > /<path>/customercustomattributes.sql
```

#### スクリプト 4

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> sequence_creditmemo_0 sequence_creditmemo_1 sequence_invoice_0 sequence_invoice_1 sequence_order_0 sequence_order_1 sequence_rma_item_0 sequence_rma_item_1 sequence_shipment_0 sequence_shipment_1 > /<path>/sequence.sql
```

### 販売データの復元

このスクリプトは、見積データベースの売上データを復元します。

#### NDB 要件

を使用する場合 [ネットワークデータベース（NDB）](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html) クラスター：

1. ダンプファイル内のテーブルを InnoDb から NDB タイプに変換します。

   ```bash
   sed -ei 's/InnoDb/NDB/' <file name>.sql
   ```

1. NDB テーブルは FULLTEXT をサポートしていないので、FULLTEXT キーを含む行をダンプから削除します。

#### データを復元

次のコマンドを実行します。

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/sales.sql
```

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/sequence.sql
```

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/salesarchive.sql
```

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/customercustomattributes.sql
```

ここで、

- `<your sales DB name>` と sales データベースの名前を指定します。

  このトピックでは、サンプル・データベース名はです。 `magento_sales`.

- `<root username>` （MySQL ルートユーザー名を使用）
- `<root user password>` （ユーザーのパスワードを使用）
- 前の手順で作成したバックアップ ファイルの場所を確認します（例： `/var/sales.sql`）

## 見積もりデータベースの設定

この項では、外部キーを sales データベース・テーブルから削除し、テーブルを sales データベースに移動するために必要なタスクについて説明します。

>[!INFO]
>
>このセクションには、特定のデータベーステーブル名を持つスクリプトが含まれています。 カスタマイズを実行した場合、またはアクションを実行する前にテーブルの完全なリストを確認する場合は、を参照してください [参照スクリプト](#reference-scripts).

引用符データベース テーブル名の先頭にを付ける `quote`. この `magento_customercustomattributes_sales_flat_quote` および `magento_customercustomattributes_sales_flat_quote_address` テーブルにも影響します

### 見積もりテーブルからの外部キーの削除

このスクリプトは、非引用符テーブルを参照する外部キーを引用符テーブルから削除します。 置換 `<your main Commerce DB name>` とCommerce データベースの名前を指定します。

次のスクリプトを作成し、のような名前を付けます。 `2_foreign-key-quote.sql`:

```sql
use <your main DB name>;
ALTER TABLE quote DROP FOREIGN KEY QUOTE_STORE_ID_STORE_STORE_ID;
ALTER TABLE quote_item DROP FOREIGN KEY QUOTE_ITEM_PRODUCT_ID_CATALOG_PRODUCT_ENTITY_ENTITY_ID;
ALTER TABLE quote_item DROP FOREIGN KEY QUOTE_ITEM_STORE_ID_STORE_STORE_ID;
```

次のようにスクリプトを実行します。

1. MySQL データベースに root または管理ユーザーとしてログインします。

   ```bash
   mysql -u root -p
   ```

1. 時刻 `mysql >` プロンプトが表示されたら、次のようにスクリプトを実行します。
   `source <path>/<script>.sql`

   以下に例を挙げます。

   ```shell
   source /root/sql-scripts/2_foreign-key-quote.sql
   ```

1. スクリプトの実行後、次のように入力します `exit`.

### 見積もりテーブルのバックアップ

このセクションでは、メイン・データベースから見積テーブルをバックアップして、見積データベースにリストアする方法について説明します。

コマンドプロンプトから次のコマンドを実行します。

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_customercustomattributes_sales_flat_quote magento_customercustomattributes_sales_flat_quote_address quote quote_address quote_address_item quote_item quote_item_option quote_payment quote_shipping_rate quote_id_mask > /<path>/quote.sql;
```

### NDB 要件

を使用する場合 [ネットワークデータベース（NDB）](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html) クラスター：

1. ダンプファイル内のテーブルを InnoDb から NDB タイプに変換します。

   ```bash
   sed -ei 's/InnoDb/NDB/' <file name>.sql
   ```

1. NDB テーブルは FULLTEXT をサポートしていないので、FULLTEXT キーを含む行をダンプから削除します。

### 見積もりデータベースにテーブルを復元する

```bash
mysql -u root -p magento_quote < /<path>/quote.sql
```

## データベースから売上テーブルと見積テーブルを削除します

このスクリプトは、Commerce データベースのテーブルを sales および quote にします。 置換 `<your main DB name>` とCommerce データベースの名前を指定します。

次のスクリプトを作成し、のような名前を付けます。 `3_drop-tables.sql`:

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

1. MySQL データベースに root または管理ユーザーとしてログインします。

   ```bash
   mysql -u root -p
   ```

1. 時刻 `mysql>` プロンプトが表示されたら、次のようにスクリプトを実行します。

   ```shell
   source <path>/<script>.sql
   ```

   以下に例を挙げます。

   ```shell
   source /root/sql-scripts/3_drop-tables.sql
   ```

1. スクリプトの実行後、次のように入力します `exit`.

## デプロイメント設定の更新

データベースを手動で分割する最後の手順は、Commerceのデプロイメント設定に接続とリソースの情報を追加することです。 `env.php`.

デプロイメント設定を更新するには：

1. Commerce サーバーにとしてログインするか、に切り替えます [ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md).
1. デプロイメント設定をバックアップします。

   ```bash
   cp <magento_root>/app/etc/env.php <magento_root>/app/etc/env.php.orig
   ```

1. 開く `<magento_root>/app/etc/env.php` テキストエディターで、以下の節で説明するガイドラインを使用して更新します。

### データベース接続の更新

で始まるブロックを見つけます `'default'` （以下 `'connection'`）に設定して、 `'checkout'` および `'sales'` セクション。 サンプル値をサイトに適した値に置き換えます。

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

で始まるブロックを見つけます `'resource'` 追加： `'checkout'` および `'sales'` セクションについて次に示します。

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

この節では、影響を受けるテーブルの完全なリストを印刷するスクリプトを実行します。それらのテーブルに対してアクションを実行する必要はありません。 これらを使用して、データベースを手動で分割する前に、どのテーブルが影響を受けるかを確認できます。これは、データベーススキーマをカスタマイズする拡張機能を使用する場合に役立ちます。

これらのスクリプトを使用するには：

1. このセクションの各スクリプトの内容を使用して SQL スクリプトを作成します。
1. 各スクリプトで、 `<your main DB name>` とCommerce データベースの名前を指定します。

   このトピックでは、サンプル・データベース名はです。 `magento`.

1. から各スクリプトを実行します `mysql>` プロンプトの形式 `source <script name>`
1. 出力を確認します。
1. 各スクリプトの結果を、パイプ文字（`|`）に設定します。
1. から各スクリプトを実行します `mysql>` プロンプトの形式 `source <script name>`.

   この 2 番目のスクリプトを実行すると、メインのCommerce データベースでアクションが実行されます。

### 外部キーの削除（販売テーブル）

このスクリプトは、sales データベースから sales 以外のテーブルを参照する外部キーを削除します。

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

### 外部キーの削除（引用符テーブル）

このスクリプトは、非引用符テーブルを参照する外部キーを引用符テーブルから削除します。

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

### 販売テーブルの削除

このスクリプトは、Commerce データベースから sales テーブルを削除します。

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

### 直接見積もりテーブル

で始まるすべてのテーブルをドロップ `quote_`.
