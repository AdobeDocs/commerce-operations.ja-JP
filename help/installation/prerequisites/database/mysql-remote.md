---
title: リモート MySQL データベース接続の設定
description: Adobe Commerceのオンプレミスインストール用にリモートデータベース接続を設定するには、次の手順に従います。
exl-id: 5fe304bd-ff38-4066-a1fd-8937575e4de4
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 0%

---

# リモート MySQL データベース接続の設定

データベース・サーバと Web サーバを同じマシン上で実行する代わりに、別のサーバでデータベースをホストする場合があります。

Adobeでは、別のマシン上の MySQL サーバーに接続する手段を提供しています。 Adobe Commerce 2.4.3 では、コードを変更せずにAmazon Web Services（AWS） Aurora データベースを使用するようにアプリケーションを設定することもできます。

Aurora は、AWS上でホストされる、高性能で完全に準拠した MySQL サーバーです。

## AWS Aurora データベースへの接続

Aurora をデータベースとして使用することは、デフォルトのデータベースコネクタを使用して、通常のAdobe Commerce設定でデータベースを指定するのと同じくらい簡単です。

実行中 `bin/magento setup:install`で、Aurora 情報を使用します `db-` フィールド :

```bash
bin/magento setup:install ... --db-host='database-aurora.us-east-1.rds.amazonaws.com' --db-name='magento2' --db-user='username' --db-password='password' ...
```

この `db-host` 値は、を含む Aurora URL です。 `https://` および末尾 `:portnumber`  を削除しました。

## リモート・データベース接続の設定

>[!NOTE]
>
>これは、経験豊富なネットワーク管理者またはデータベース管理者のみが使用する高度なトピックです。 以下が必要です `root` ファイルシステムにアクセスし、次のように MySQL にログインできる必要があります `root`.

### 前提条件

開始する前に、次の操作を行う必要があります。

* [MySQL サーバーのインストール](mysql.md) データベースサーバー上。
* [データベースインスタンスの作成](mysql.md#configuring-the-database-instance) データベースサーバー上。
* Adobe CommerceまたはMagento Open Source web ノードに MySQL クライアントをインストールします。 詳しくは、MySQL のドキュメントを参照してください。

### 高可用性

Web サーバーまたはデータベースサーバーがクラスター化されている場合は、次のガイドラインを使用してリモートデータベース接続を設定します。

* Web サーバーノードごとに接続を設定する必要があります。
* 通常は、データベース・ロード・バランサへのデータベース接続を構成します。ただし、データベース・クラスタリングは複雑になる場合があり、構成はユーザー次第です。 Adobeでは、データベースクラスタリングに関して具体的な推奨事項を提供していません。

  詳しくは、を参照してください [MySQL ドキュメント](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html).

### 接続の問題の解決

いずれかのホストへの接続で問題が発生した場合は、最初に他のホストに ping を送信して、そのホストに到達可能であることを確認します。 ファイアウォールと SELinux ルールを変更して、あるホストから別のホストへの接続を許可する必要がある場合があります（SELinux を使用する場合）。

## リモート接続の作成

リモート接続を作成するには：

1. データベースサーバーで、を持つユーザーとして `root` 権限を設定するには、MySQL 設定ファイルを開きます。

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
   >Ubuntu 16 では、通常はパスは `/etc/mysql/mysql.conf.d/mysqld.cnf`.

1. 設定ファイルで次を検索： `bind-address`.

   存在する場合は、次のように値を変更します。

   存在しない場合は、に追加します `[mysqld]` セクション。

   ```conf
   bind-address = <ip address of your web node>
   ```

   参照： [MySQL ドキュメント](https://dev.mysql.com/doc/refman/5.6/en/server-options.html)特に、クラスター化された web サーバーがある場合。

1. 設定ファイルに対する変更を保存し、テキストエディターを終了します。
1. MySQL サービスを再起動します。

   * CentOS: `service mysqld restart`

   * Ubuntu: `service mysql restart`

   >[!NOTE]
   >
   >MySQL の起動に失敗した場合は、syslog で問題の原因を調べます。 を使用して問題を解決する [MySQL ドキュメント](https://dev.mysql.com/doc/refman/5.6/en/server-options.html#option_mysqld_bind-address) または別の信頼できる情報源。

## データベースユーザーへのアクセス権の付与

Web ノードがデータベースサーバーに接続できるようにするには、web ノードのデータベースユーザーにリモートサーバー上のデータベースへのアクセス権を付与する必要があります。

この例では、次の権限が付与されます `root` データベースユーザー：リモートホスト上のデータベースへのフルアクセス。

データベース・ユーザーにアクセス権を付与するには、次の手順に従います。

1. データベースサーバーにログインします。
1. MySQL データベースにとして接続します `root` ユーザー。
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

MySQL モニターに次のように表示される場合、データベースはAdobe CommerceまたはMagento Open Sourceの準備が整っています。

```terminal
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 213 Server version: 5.6.26 MySQL Community Server (GPL)

Copyright (c) 2000, 2015, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its affiliates. Other names may be trademarks of their respective owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
```

Web サーバーがクラスター化されている場合は、各 web サーバーホストでコマンドを入力します。

## Adobe CommerceまたはMagento Open Sourceのインストール

Adobe CommerceまたはMagento Open Sourceをインストールする際は、次の情報を指定する必要があります。

* ベース URL （別名） *ストアアドレス*）は、ホスト名または IP アドレスを指定します *web ノード*
* データベースホストはです *リモート・データベース・サーバ* IP アドレス （または、データベースサーバーがクラスター化されている場合はロードバランサー）
* データベースのユーザー名は *ローカル web ノード* アクセス権を付与したデータベースユーザー
* データベースパスワードは、ローカル web ノードユーザーのパスワードです。
* Database name は、リモート・サーバ上のデータベースの名前です
