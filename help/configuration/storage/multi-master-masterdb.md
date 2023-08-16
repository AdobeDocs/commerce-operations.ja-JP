---
title: マスターデータベースを自動的に構成する
description: 分割データベースソリューションの自動設定に関するガイダンスを参照してください。
recommendations: noCatalog
exl-id: a27ad097-de60-4cdd-81f9-eb1ae84587e4
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 1%

---

# マスターデータベースを自動的に構成する

{{ee-only}}

{{deprecate-split-db}}

このトピックでは、次の方法でデータベース分割ソリューションの使用を開始する方法について説明します。

1. 1 つのマスターデータベース（名前は）を使用したAdobe Commerceのインストール `magento`)
1. チェックアウトおよび OMS 用の 2 つの追加のマスター・データベースの作成 ( 名前： `magento_quote` および `magento_sales`)
1. チェックアウトおよび販売データベースを使用するためのAdobe Commerceの設定

>[!INFO]
>
>このガイドでは、3 つのデータベースがすべて Commerce アプリケーションと同じホスト上にあり、これらのデータベースの名前がとなっていることを前提としています `magento`, `magento_quote`、および `magento_sales`. ただし、データベースの場所と名前の選択はユーザー次第です。 私たちの例が、指示を従いやすくしてくれることを願っています。

## Adobe Commerceソフトウェアのインストール

Adobe Commerceソフトウェアをインストールした後は、いつでも分割データベースを有効にすることができます。つまり、既にチェックアウトおよび注文データを持つAdobe Commerceシステムに分割データベースを追加できます。 Adobe Commerce README または [インストールガイド](../../installation/overview.md) をクリックし、1 つのマスターデータベースを使用してAdobe Commerceソフトウェアをインストールします。

## 追加のマスターデータベースを設定する

次の手順に従って、チェックアウトおよび OMS マスター・データベースを作成します。

1. 任意のユーザーとしてデータベースサーバーにログインします。
1. 次のコマンドを入力して、MySQL コマンドプロンプトに移動します。

   ```bash
   mysql -u root -p
   ```

1. MySQL を入力 `root` ユーザーのパスワードを求められた場合。
1. 次のコマンドを、示された順序で入力して、という名前のデータベースインスタンスを作成します。 `magento_quote` および `magento_sales` 同じユーザー名とパスワードを使用：

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

1. 入力 `exit` をクリックして、コマンドプロンプトを終了します。

1. データベースを 1 つずつ検証します。

   チェックアウトデータベース：

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

   MySQL モニタが表示される場合は、データベースが正しく作成されています。 エラーが表示される場合は、前述のコマンドを繰り返します。

## マスターデータベースを使用するように Commerce を構成する

合計 3 つのマスターデータベースを設定した後、コマンドラインを使用して、それらを使用するように Commerce を設定します。 （このコマンドは、データベース接続を設定し、マスターデータベース間でテーブルを分配します）。

### 最初の手順

詳しくは、 [コマンドの実行](../cli/config-cli.md#running-commands) ログインして CLI コマンドを実行します。

### チェックアウトデータベースを設定する

コマンドの構文：

```bash
bin/magento setup:db-schema:split-quote --host="<checkout db host or ip>" --dbname="<name>" --username="<checkout db username>" --password="<password>"
```

以下に例を挙げます。

```bash
bin/magento setup:db-schema:split-quote --host="localhost" --dbname="magento_quote" --username="magento_quote" --password="magento_quote"
```

次のメッセージが表示され、設定が正常に完了したことを確認します。

```terminal
Migration has been finished successfully!
```

### OMS データベースを構成する

コマンドの構文：

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

次のメッセージが表示され、設定が正常に完了したことを確認します。

```terminal
Migration has been finished successfully!
```
