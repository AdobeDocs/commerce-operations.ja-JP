---
title: 自動的にマスタ データベースを構成する
description: 分割データベースソリューションの自動設定に関するガイダンスを参照してください。
recommendations: noCatalog
exl-id: a27ad097-de60-4cdd-81f9-eb1ae84587e4
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 1%

---

# 自動的にマスタ データベースを構成する

{{ee-only}}

{{deprecate-split-db}}

このトピックでは、次の方法で分割データベース・ソリューションを開始する方法について説明します。

1. （という名前の） 1 つのマスターデータベースを持つAdobe Commerceのインストール `magento`）
1. チェックアウトと OMS 用の 2 つの追加マスターデータベースの作成（という名前） `magento_quote` および `magento_sales`）
1. チェックアウトおよび販売データベースを使用するためのAdobe Commerceの設定

>[!INFO]
>
>このガイドでは、3 つのデータベースがすべてCommerce アプリケーションと同じホスト上にあり、名前が付けられていることを前提としています `magento`, `magento_quote`、および `magento_sales`. ただし、データベースの場所とデータベースの名前はユーザーが選択できます。 私たちの例が指示に従いやすくなることを願っています。

## Adobe Commerce ソフトウェアのインストール

分割データベースは、Adobe Commerce ソフトウェアのインストール後、いつでも有効にすることができます。つまり、既にチェックアウトと注文のデータがあるAdobe Commerce システムに分割データベースを追加できます。 Adobe Commerceの README の手順を参照するか、 [インストールガイド](../../installation/overview.md) 単一のマスターデータベースを用いてAdobe Commerceソフトウェアをインストールする。

## 追加のマスターデータベースを設定する

チェックアウトおよび OMS マスターデータベースを次のように作成します。

1. 任意のユーザーとしてデータベースサーバーにログインします。
1. 次のコマンドを入力して、MySQL コマンドプロンプトを表示します。

   ```bash
   mysql -u root -p
   ```

1. MySQL を入力 `root` プロンプトが表示されたらユーザーのパスワードを入力します。
1. 次のコマンドを表示されている順序で入力して、という名前のデータベースインスタンスを作成します。 `magento_quote` および `magento_sales` ユーザー名とパスワードが同じ場合：

   ```shell
   create database magento_quote;
   ```

   ```shell
   GRANT ALL ON magento_quote.* TO magento_quote@localhost IDENTIFIED BY 'magento_quote';
   ```

   ```shell
   create database magento_sales;
   ```

   ```shell
   GRANT ALL ON magento_sales.* TO magento_sales@localhost IDENTIFIED BY 'magento_sales';
   ```

1. Enter `exit` をクリックして、コマンドプロンプトを終了します。

1. データベースを 1 つずつ検証します。

   データベースのチェックアウト：

   ```bash
   mysql -u magento_quote -p
   ```

   ```shell
   exit
   ```

   受注管理システム・データベース：

   ```bash
   mysql -u magento_sales -p
   ```

   ```shell
   exit
   ```

   MySQL モニターが表示された場合は、データベースが正しく作成されています。 エラーが表示された場合は、上記のコマンドを繰り返します。

## マスターデータベースを使用するようにCommerceを設定する

合計 3 つのマスターデータベースを設定した後、コマンドラインを使用して、Commerceでそれらを使用するように設定します。 （このコマンドは、データベース接続を設定し、マスターデータベース間でテーブルを配布します）。

### 最初の手順

参照： [コマンドの実行](../cli/config-cli.md#running-commands) にログインし、CLI コマンドを実行します。

### チェックアウトデータベースの設定

コマンド構文：

```bash
bin/magento setup:db-schema:split-quote --host="<checkout db host or ip>" --dbname="<name>" --username="<checkout db username>" --password="<password>"
```

以下に例を挙げます。

```bash
bin/magento setup:db-schema:split-quote --host="localhost" --dbname="magento_quote" --username="magento_quote" --password="magento_quote"
```

セットアップが正常に完了したことを確認する次のメッセージが表示されます。

```terminal
Migration has been finished successfully!
```

### OMS データベースの構成

コマンド構文：

```bash
bin/magento setup:db-schema:split-sales --host="<checkout db host or ip>" --dbname="<name>" --username="<checkout db username>" --password="<password>"
```

以下に例を挙げます。

```bash
bin/magento setup:db-schema:split-sales --host="localhost" --dbname="magento_sales" --username="magento_sales" --password="magento_sales"
```

```bash
bin/magento setup:upgrade
```

セットアップが正常に完了したことを確認する次のメッセージが表示されます。

```terminal
Migration has been finished successfully!
```
