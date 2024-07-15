---
title: 分割データベースを元に戻す
description: 非推奨（廃止予定）の分割データベース実装から単一のデータベース実装に戻す。
feature: Configuration, Storage
exl-id: 2ece24e0-1f85-445a-8e22-fb10611403ff
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---

# 分割データベースから復帰する

{{ee-only}}

[Split Database](multi-master.md) を実装しているAdobe Commerceのお客様の場合、次のトピックでは、1 つのデータベースに戻す方法または 1 つのデータベースに戻す方法について説明します。 現在 Split Database を使用しているAdobe Commerce マーチャントは、2.4.2 以降にアップグレードする予定です。これらの手順のほか、予定されている Split Database の廃止に関する [ お知らせ ](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) も確認することをお勧めします。

分割データベースから単一データベースに戻すには、`magento_quote` および `magento_sales` データベースのバックアップを作成してから、それらを単一の `magento_main` データベースにロードします。

この例では、「root」ユーザーと同じホスト（`magento2-mysql`）にインストールされている 3 つのデータベースすべてにログインします。 これらの値を、データベースに適した値に置き換える必要があります。

1. `magento_quote` データベースのバックアップを作成します。

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_quote > ./quote.sql
   ```

1. `magento_sales` データベースのバックアップを作成します。

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_sales > ./sales.sql
   ```

1. `magento_quote` データベースを `magento_main` データベースに読み込みます。

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./quote.sql
   ```

1. `magento_sales` データベースを `magento_main` データベースに読み込みます。

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./sales.sql
   ```

1. `magento_sales` データベースをドロップします。

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_sales;"
   ```

1. `magento_quote` データベースをドロップします。

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_quote;"
   ```

1. `env.php` ファイルの `connections` セクションおよび `resources` セクションで、`checkout` および `sales` のデプロイメント設定を削除します。
1. 外部キーを復元：

   ```bash
   bin/magento setup:upgrade
   ```

## 作業内容の検証

単一データベースの実装が正常に動作していることを確認するには、次のタスクを実行し、[phpMyAdmin](../../installation/prerequisites/optional-software.md#phpmyadmin) などのデータベースツールを使用して `magento_main` のデータベーステーブルにデータが追加されていることを確認します。

1. 外部キーが復元されたことを確認します。 例えば、`quote` データベーステーブルの `QUOTE_STORE_ID_STORE_STORE_ID` キーなどです。
1. 顧客がストアフロントから注文できることを確認します。
1. 分割されたデータベースを単一のデータベースに戻す前に作成された注文が、管理者で使用できることを確認します。
