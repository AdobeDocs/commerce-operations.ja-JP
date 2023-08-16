---
title: 分割データベースを元に戻す
description: 非推奨の分割データベース実装から単一のデータベース実装に戻します。
feature: Configuration, Storage
exl-id: 2ece24e0-1f85-445a-8e22-fb10611403ff
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# 分割データベースから元に戻す

{{ee-only}}

を実装しているAdobe Commerceのお客様向け [データベースを分割](multi-master.md)以下のトピックでは、単一のデータベースを元に戻す（または元のデータベースに戻す）方法について説明します。 現在 Split Database を使用しているAdobe Commerceの商人に対しては、2.4.2 以降へのアップグレードを計画し、これらの手順を確認することをお勧めします。 [お知らせ](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) 分割データベースの廃止予定について説明します。

分割データベースから単一のデータベースに戻すには、 `magento_quote` および `magento_sales` データベースを読み込む前に `magento_main` データベース。

この例では、3 つのデータベースすべてにログインします。同じホスト (`magento2-mysql`) を「root」ユーザーとして追加します。 これらの値は、データベースに適した値に置き換える必要があります。

1. のバックアップを作成します。 `magento_quote` データベース：

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_quote > ./quote.sql
   ```

1. のバックアップを作成します。 `magento_sales` データベース：

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_sales > ./sales.sql
   ```

1. を読み込む `magento_quote` データベースを `magento_main` データベース：

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./quote.sql
   ```

1. を読み込む `magento_sales` データベースを `magento_main` データベース：

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./sales.sql
   ```

1. 次をドロップ： `magento_sales` データベース：

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_sales;"
   ```

1. 次をドロップ： `magento_quote` データベース：

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_quote;"
   ```

1. 次のデプロイメント設定を削除： `checkout` および `sales` （内） `connections` および `resources` セクション `env.php` ファイル。
1. 外部キーを復元：

   ```bash
   bin/magento setup:upgrade
   ```

## 作業内容を確認する

単一のデータベースの実装が正しく動作していることを確認するには、次のタスクを実行し、データが `magento_main` データベーステーブルを [phpMyAdmin](../../installation/prerequisites/optional-software.md#phpmyadmin):

1. 外部キーが復元されたことを確認します。 例えば、 `QUOTE_STORE_ID_STORE_STORE_ID` キー `quote` データベーステーブル。
1. 顧客がストアフロントから注文を行えることを確認します。
1. 分割データベースを単一のデータベースに戻す前に作成された注文が、管理者で使用できることを確認します。
