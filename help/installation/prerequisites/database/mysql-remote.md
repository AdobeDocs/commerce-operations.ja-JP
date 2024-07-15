---
title: リモート MySQL データベース接続の設定
description: Adobe Commerceのオンプレミスインストール用にリモートデータベース接続を設定するには、次の手順に従います。
exl-id: 5fe304bd-ff38-4066-a1fd-8937575e4de4
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 0%

---

# リモート MySQL データベース接続の設定

データベース・サーバと Web サーバを同じマシン上で実行する代わりに、別のサーバでデータベースをホストする場合があります。

Adobeでは、別のマシン上の MySQL サーバーに接続する手段を提供しています。 Adobe Commerce 2.4.3 では、コードを変更せずにAmazon Web Services（AWS） Aurora データベースを使用するようにアプリケーションを設定することもできます。

Aurora は、AWS上でホストされる、高性能で完全に準拠した MySQL サーバーです。

## AWS Aurora データベースへの接続

Aurora をデータベースとして使用することは、デフォルトのデータベースコネクタを使用して、通常のAdobe Commerce設定でデータベースを指定するのと同じくらい簡単です。

`bin/magento setup:install` を実行する際は、`db-` のフィールドに Aurora 情報を使用します。

```bash
bin/magento setup:install ... --db-host='database-aurora.us-east-1.rds.amazonaws.com' --db-name='magento2' --db-user='username' --db-password='password' ...
```

`db-host` の値は、`https://` と末尾の `:portnumber` が削除された Aurora URL です。

## リモート・データベース接続の設定

>[!NOTE]
>
>これは、経験豊富なネットワーク管理者またはデータベース管理者のみが使用する高度なトピックです。 ファイルシステムに対する `root` アクセス権を持ち、`root` として MySQL にログインできる必要があります。

### 前提条件

開始する前に、次の操作を行う必要があります。

* データベースサーバーに [MySQL サーバーをインストール ](mysql.md) します。
* データベースサーバーで [ データベースインスタンスを作成 ](mysql.md#configuring-the-database-instance) します。
* Adobe Commerce web ノードに MySQL クライアントをインストールします。 詳しくは、MySQL のドキュメントを参照してください。

### 高可用性

Web サーバーまたはデータベースサーバーがクラスター化されている場合は、次のガイドラインを使用してリモートデータベース接続を設定します。

* Web サーバーノードごとに接続を設定する必要があります。
* 通常は、データベース・ロード・バランサへのデータベース接続を構成します。ただし、データベース・クラスタリングは複雑になる場合があり、構成はユーザー次第です。 Adobeでは、データベースクラスタリングに関して具体的な推奨事項を提供していません。

  詳しくは、[MySQL のドキュメント ](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html) を参照してください。

### 接続の問題の解決

いずれかのホストへの接続で問題が発生した場合は、最初に他のホストに ping を送信して、そのホストに到達可能であることを確認します。 ファイアウォールと SELinux ルールを変更して、あるホストから別のホストへの接続を許可する必要がある場合があります（SELinux を使用する場合）。

## リモート接続の作成

リモート接続を作成するには：

1. データベースサーバーで、`root` 権限を持つユーザーとして、MySQL 設定ファイルを開きます。

   このディレクトリを探すには、次のコマンドを入力します。

   ```bash
   mysql --help
   ```

   場所は次のように表示されます。

   ```terminal
   Default options are read from the following files in the given order:
   /etc/my.cnf /etc/mysql/my.cnf /usr/etc/my.cnf ~/.my.cnf
   ```

   >[!NOTE]
   >
   >Ubuntu 16 では通常、パスは `/etc/mysql/mysql.conf.d/mysqld.cnf` です。

1. 設定ファイルで `bind-address` を検索します。

   存在する場合は、次のように値を変更します。

   存在しない場合は、`[mysqld]` セクションに追加します。

   ```conf
   bind-address = <ip address of your web node>
   ```

   特にクラスター化された web サーバーがある場合は、[MySQL ドキュメント ](https://dev.mysql.com/doc/refman/5.6/en/server-options.html) を参照してください。

1. 設定ファイルに対する変更を保存し、テキストエディターを終了します。
1. MySQL サービスを再起動します。

   * CentOS: `service mysqld restart`

   * Ubuntu: `service mysql restart`

   >[!NOTE]
   >
   >MySQL の起動に失敗した場合は、syslog で問題の原因を調べます。 [MySQL ドキュメント ](https://dev.mysql.com/doc/refman/5.6/en/server-options.html#option_mysqld_bind-address) またはその他の信頼できるソースを使用して、問題を解決します。

## データベースユーザーへのアクセス権の付与

Web ノードがデータベースサーバーに接続できるようにするには、web ノードのデータベースユーザーにリモートサーバー上のデータベースへのアクセス権を付与する必要があります。

この例では、`root` データベース・ユーザーにリモート・ホスト上のデータベースへのフル・アクセス権を付与します。

データベース・ユーザーにアクセス権を付与するには、次の手順に従います。

1. データベースサーバーにログインします。
1. `root` ユーザーとして MySQL データベースに接続します。
1. 次のコマンドを入力します。

   ```shell
   GRANT ALL ON <local database name>.* TO <remote web node username>@<remote web node server ip address> IDENTIFIED BY '<database user password>';
   ```

   以下に例を挙げます。

   ```shell
   GRANT ALL ON magento_remote.* TO dbuser@192.0.2.50 IDENTIFIED BY 'dbuserpassword';
   ```

   >[!NOTE]
   >
   >Web サーバーがクラスター化されている場合は、すべての web サーバーに同じコマンドを入力します。 すべての Web サーバーに同じユーザー名を使用する必要があります。

## データベースアクセスの検証

Web ノードホストで、次のコマンドを入力して接続が機能していることを確認します。

```bash
mysql -u <local database username> -h <database server ip address> -p
```

MySQL モニターに次のように表示される場合、データベースはAdobe Commerceに対応しています。

```terminal
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 213 Server version: 5.6.26 MySQL Community Server (GPL)

Copyright (c) 2000, 2015, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its affiliates. Other names may be trademarks of their respective owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
```

Web サーバーがクラスター化されている場合は、各 web サーバーホストでコマンドを入力します。

## Adobe Commerceのインストール

Adobe Commerceをインストールする際は、次の情報を指定する必要があります。

* ベース URL （「ストアアドレス *とも呼ばれます）は* web ノード *のホスト名または IP アドレスを指定しま*。
* データベースホストは *リモートデータベースサーバー* IP アドレス（または、データベースサーバーがクラスター化されている場合はロードバランサー）です。
* Database username は、アクセス権を付与した *ローカル web ノード* データベースユーザーです
* データベースパスワードは、ローカル web ノードユーザーのパスワードです。
* Database name は、リモート・サーバ上のデータベースの名前です
