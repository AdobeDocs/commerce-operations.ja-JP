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

を実装したAdobe Commerceのお客様向け [データベースの分割](multi-master.md)次のトピックでは、単一のデータベースに戻す方法または単一のデータベースに戻す方法について説明します。 現在、分割データベースを使用しているAdobe Commerce マーチャントは、2.4.2 以降にアップグレードする予定で、これらの手順および以下の手順を確認することをお勧めします [お知らせ](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) 分割データベースの廃止が計画されていること。

分割されたデータベースから単一のデータベースに戻すには、次のバックアップを作成する必要があります `magento_quote` および `magento_sales` 単一データベースに読み込む前のデータベース `magento_main` データベース。

この例では、同じホストにインストールされている 3 つのデータベースすべてにログインします（`magento2-mysql`）を「root」ユーザーとして設定します。 これらの値を、データベースに適した値に置き換える必要があります。

1. のバックアップを作成 `magento_quote` データベース：

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_quote > ./quote.sql
   ```

1. のバックアップを作成 `magento_sales` データベース：

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_sales > ./sales.sql
   ```

1. を読み込みます `magento_quote` データベースをに `magento_main` データベース：

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./quote.sql
   ```

1. を読み込みます `magento_sales` データベースをに `magento_main` データベース：

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./sales.sql
   ```

1. をドロップ `magento_sales` データベース：

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_sales;"
   ```

1. をドロップ `magento_quote` データベース：

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_quote;"
   ```

1. のデプロイメント設定を削除します `checkout` および `sales` が含まれる `connections` および `resources` のセクション `env.php` ファイル。
1. 外部キーを復元：

   ```bash
   bin/magento setup:upgrade
   ```

## 作業内容の検証

単一のデータベース実装が正しく動作していることを確認するには、次のタスクを実行し、データがに追加されていることを確認します `magento_main` のようなデータベースツールを使用したデータベーステーブル [phpMyAdmin](../../installation/prerequisites/optional-software.md#phpmyadmin):

1. 外部キーが復元されたことを確認します。 例： `QUOTE_STORE_ID_STORE_STORE_ID` 内のキー `quote` データベーステーブル。
1. 顧客がストアフロントから注文できることを確認します。
1. 分割されたデータベースを単一のデータベースに戻す前に作成された注文が、管理者で使用できることを確認します。
