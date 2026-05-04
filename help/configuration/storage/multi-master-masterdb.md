---
title: マスターデータベースの自動設定
description: 分割データベースソリューションの自動設定に関するガイダンスを参照してください。
recommendations: noCatalog
exl-id: a27ad097-de60-4cdd-81f9-eb1ae84587e4
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 1%

---

# マスターデータベースの自動設定

{{ee-only}}

{{deprecate-split-db}}

このトピックでは、次の方法でスプリットデータベースソリューションを開始する方法について説明します。

1. 1つのマスターデータベース （`magento`という名前）にAdobe Commerceをインストールしています
1. チェックアウトおよびOMS用に2つの追加のマスターデータベースを作成しています（`magento_quote`および`magento_sales`）
1. チェックアウトデータベースとセールスデータベースを使用するためのAdobe Commerceの設定

>[!INFO]
>
>このガイドでは、3つのデータベースがすべてCommerce アプリケーションと同じホスト上にあり、名前が`magento`、`magento_quote`、`magento_sales`であると仮定しています。 ただし、データベースの場所と名前を指定する場所は、ユーザーが選択します。 私たちの例が指示を従いやすくすることを願っています。

## Adobe Commerce ソフトウェアのインストール

Adobe Commerce ソフトウェアをインストールした後は、いつでも分割データベースを有効にできます。つまり、チェックアウトおよび注文データを既に持つAdobe Commerce システムに分割データベースを追加できます。 Adobe Commerce READMEまたは[ インストールガイド ](../../installation/overview.md)の手順に従って、1つのマスターデータベースを使用してAdobe Commerce ソフトウェアをインストールします。

## 追加のマスターデータベースの設定

次のように、チェックアウトとOMS マスターデータベースを作成します。

1. 任意のユーザーとしてデータベース・サーバにログインします。
1. 次のコマンドを入力して、MySQL コマンドプロンプトにアクセスします。

   ```shell
   mysql -u root -p
   ```

1. プロンプトが表示されたら、MySQL `root` ユーザーのパスワードを入力します。
1. 同じユーザー名とパスワードを使用して`magento_quote`と`magento_sales`という名前のデータベース インスタンスを作成するには、次のコマンドを順に入力します。

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

1. コマンド プロンプトを終了するには、`exit`と入力します。

1. データベースを1つずつ確認します。

   チェックアウトデータベース：

   ```shell
   mysql -u magento_quote -p
   ```

   ```shell
   exit
   ```

   注文管理システムデータベース：

   ```shell
   mysql -u magento_sales -p
   ```

   ```shell
   exit
   ```

   MySQL モニターが表示される場合は、データベースを適切に作成しました。 エラーが表示された場合は、上記のコマンドを繰り返します。

## マスターデータベースを使用するようにCommerceを設定する

合計3つのマスターデータベースを設定した後、コマンドラインを使用してCommerceを設定し、それらを使用します。 （このコマンドは、データベース接続を設定し、マスターデータベース間でテーブルを配布します）。

### 最初のステップ

ログインしてCLI コマンドを実行するには、[ コマンドの実行](../cli/config-cli.md#running-commands)を参照してください。

### チェックアウトデータベースの設定

コマンドの構文：

```shell
bin/magento setup:db-schema:split-quote --host="<checkout db host or ip>" --dbname="<name>" --username="<checkout db username>" --password="<password>"
```

以下に例を挙げます。

```shell
bin/magento setup:db-schema:split-quote --host="localhost" --dbname="magento_quote" --username="magento_quote" --password="magento_quote"
```

設定が正常に完了したことを確認するには、次のメッセージが表示されます。

```text
Migration has been finished successfully!
```

### OMS データベースの設定

コマンドの構文：

```shell
bin/magento setup:db-schema:split-sales --host="<checkout db host or ip>" --dbname="<name>" --username="<checkout db username>" --password="<password>"
```

以下に例を挙げます。

```shell
bin/magento setup:db-schema:split-sales --host="localhost" --dbname="magento_sales" --username="magento_sales" --password="magento_sales"
```

```shell
bin/magento setup:upgrade
```

設定が正常に完了したことを確認するには、次のメッセージが表示されます。

```text
Migration has been finished successfully!
```
