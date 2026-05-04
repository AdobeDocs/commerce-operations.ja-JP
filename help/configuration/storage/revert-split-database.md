---
title: 分割データベースを元に戻す
description: 非推奨の分割データベース実装から単一のデータベース実装に戻します。
feature: Configuration, Storage
exl-id: 2ece24e0-1f85-445a-8e22-fb10611403ff
source-git-commit: f9a135fc63574ccbecd3f564a87fc5c4ac03f009
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 0%

---

# 分割データベースから復帰

{{ee-only}}

[Split Database](multi-master.md)を実装したAdobe Commerceのお客様の場合、次のトピックでは、1つのデータベースに戻したり、戻したりする方法について説明します。 現在Split Databaseを使用しており、2.4.2以降にアップグレードする予定のAdobe Commerce販売者には、これらの手順を確認することをお勧めします。

分割データベースから単一データベースに戻すには、`magento_quote`および`magento_sales` データベースのバックアップを作成してから、単一の`magento_main` データベースに読み込む必要があります。

この例では、3つのデータベースすべてにログインします。これらのデータベースは、「root」ユーザーと同じホスト（`magento2-mysql`）にインストールされます。 これらの値は、データベースに適した値に置き換える必要があります。

1. `magento_quote` データベースのバックアップを作成します。

   ```shell
   mysqldump -h "magento2-mysql" -u root -p magento_quote > ./quote.sql
   ```

1. `magento_sales` データベースのバックアップを作成します。

   ```shell
   mysqldump -h "magento2-mysql" -u root -p magento_sales > ./sales.sql
   ```

1. `magento_quote` データベースを`magento_main` データベースに読み込みます。

   ```shell
   mysql -h "magento2-mysql" -u root -p magento_main < ./quote.sql
   ```

1. `magento_sales` データベースを`magento_main` データベースに読み込みます。

   ```shell
   mysql -h "magento2-mysql" -u root -p magento_main < ./sales.sql
   ```

1. `magento_sales` データベースをドロップします。

   ```shell
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_sales;"
   ```

1. `magento_quote` データベースをドロップします。

   ```shell
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_quote;"
   ```

1. `env.php` ファイルの`connections`および`resources` セクションの`checkout`および`sales`のデプロイメント設定を削除します。
1. 外部キーの復元：

   ```shell
   bin/magento setup:upgrade
   ```

## 作品の確認

単一のデータベース実装が正しく機能していることを確認するには、次のタスクを実行し、[phpMyAdmin](../../installation/prerequisites/optional-software.md#phpmyadmin)などのデータベースツールを使用して、データが`magento_main` データベーステーブルに追加されていることを確認します。

1. 外部キーが復元されたことを確認します。 例えば、`quote` データベーステーブルの`QUOTE_STORE_ID_STORE_STORE_ID` キー。
1. 顧客がストアフロントから注文できることを確認します。
1. 分割データベースを単一のデータベースに戻す前に作成された注文が、管理者で使用可能であることを確認します。
