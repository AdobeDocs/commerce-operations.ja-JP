---
title: リモート MySQL データベース接続の設定
description: Adobe Commerceのオンプレミス インストール用にリモート データベース接続を設定するには、次の手順に従います。
exl-id: 5fe304bd-ff38-4066-a1fd-8937575e4de4
source-git-commit: 319f3232d1ba5f5ed7cdd10ce85b9d7ffbeec89a
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 0%

---

# リモート MySQL データベース接続の設定

同じマシン上でデータベースサーバーとweb サーバーを実行する代わりに、別のサーバーでデータベースをホストしたい場合があります。

Adobeは、別のマシン上のMySQL サーバーに接続する方法を提供しました。 Adobe Commerce 2.4.3以降では、コードを変更せずにAmazon Web Services（AWS） Aurora データベースを使用するようにアプリケーションを設定することもできます。

Auroraは、AWS上でホストされる高性能で完全に準拠したMySQL サーバーです。

## AWS Aurora データベースへの接続

Auroraをデータベースとして使用することは、デフォルトのデータベースコネクタを使用して、通常のAdobe Commerce セットアップ設定でデータベースを指定するのと同じくらい簡単です。

`bin/magento setup:install`を実行する場合は、`db-` フィールドでAurora情報を使用します。

```shell
bin/magento setup:install ... --db-host='database-aurora.us-east-1.rds.amazonaws.com' --db-name='magento2' --db-user='username' --db-password='password' ...
```

`db-host`の値は、`https://`と末尾の`:portnumber`が削除されたAurora URLです。

## リモート・データベース接続の設定

>[!NOTE]
>
>これは、経験豊富なネットワーク管理者またはデータベース管理者のみが使用できる高度なトピックです。 ファイルシステムに`root` アクセスできる必要があり、MySQLに`root`としてログインできる必要があります。

### 前提条件

始める前に、次のことをおこなう必要があります。

* [&#x200B; データベース サーバーにMySQL サーバー](mysql.md)をインストールします。
* [&#x200B; データベースサーバー上にデータベースインスタンス &#x200B;](mysql.md#configuring-the-database-instance)を作成します。
* MySQL クライアントをAdobe Commerce web ノードにインストールします。 詳しくは、MySQLのドキュメントを参照してください。

### 高い可用性

Web サーバーまたはデータベースサーバーがクラスター化されている場合は、次のガイドラインを使用してリモートデータベース接続を設定します。

* Web サーバーノードごとに接続を設定する必要があります。
* 通常、データベース ロード バランサーに対するデータベース接続を設定しますが、データベース クラスタリングは複雑になる可能性があり、設定は自分で行います。 Adobeでは、データベースクラスタリングに関する具体的な推奨事項は示されていません。

  詳しくは、[MySQL ドキュメント &#x200B;](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html)を参照してください。

### 接続の問題の解決

いずれかのホストへの接続に問題がある場合は、まず他のホストにping送信して、そのホストに到達できることを確認します。 ファイアウォールとSELinux ルールを変更して、あるホストから別のホストへの接続を許可する必要がある場合があります（SELinuxを使用している場合）。

## リモート接続の作成

リモート接続を作成するには：

1. データベースサーバーで、`root`権限を持つユーザーとして、MySQL設定ファイルを開きます。

   検索するには、次のコマンドを入力します。

   ```shell
   mysql --help
   ```

   場所は次のように表示されます。

   ```text
   Default options are read from the following files in the given order:
   /etc/my.cnf /etc/mysql/my.cnf /usr/etc/my.cnf ~/.my.cnf
   ```

   >[!NOTE]
   >
   >Ubuntu 16では、パスは通常`/etc/mysql/mysql.conf.d/mysqld.cnf`です。

1. `bind-address`の設定ファイルを検索します。

   存在する場合は、次のように値を変更します。

   存在しない場合は、`[mysqld]` セクションに追加します。

   ```conf
   bind-address = <ip address of your web node>
   ```

   特にクラスター化されたWeb サーバーがある場合は、[MySQL ドキュメント &#x200B;](https://dev.mysql.com/doc/refman/5.6/en/server-options.html)を参照してください。

1. 設定ファイルに変更を保存し、テキストエディターを終了します。
1. MySQL サービスを再起動します。

   * CentOS: `service mysqld restart`

   * Ubuntu: `service mysql restart`

   >[!NOTE]
   >
   >MySQLが起動しない場合は、syslogで問題の原因を探します。 [MySQL ドキュメント &#x200B;](https://dev.mysql.com/doc/refman/5.6/en/server-options.html#option_mysqld_bind-address)またはその他の信頼できるソースを使用して、問題を解決します。

## データベースユーザーへのアクセス権の付与

Web ノードでデータベースサーバーへの接続を有効にするには、Web ノードデータベースユーザーにリモートサーバー上のデータベースへのアクセス権を付与する必要があります。

次の使用例は、`root` データベース ユーザーにリモート ホスト上のデータベースへの完全なアクセス権を付与します。

データベースユーザーにアクセス権を付与するには：

1. データベースサーバーにログインします。
1. MySQL データベースに`root` ユーザーとして接続します。
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
   >Web サーバーがクラスター化されている場合は、すべてのweb サーバーで同じコマンドを入力します。 Web サーバーごとに同じユーザー名を使用する必要があります。

## データベースアクセスの確認

Web ノードホストで、次のコマンドを入力して、接続が機能することを確認します。

```shell
mysql -u <local database username> -h <database server ip address> -p
```

MySQL モニターが次のように表示された場合、データベースはAdobe Commerceの準備が整っています。

```text
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 213 Server version: 5.6.26 MySQL Community Server (GPL)

Copyright (c) 2000, 2015, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its affiliates. Other names may be trademarks of their respective owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
```

Web サーバーがクラスター化されている場合は、各Web サーバーホストでコマンドを入力します。

## Adobe Commerceのインストール

Adobe Commerceをインストールする場合は、次の項目を指定する必要があります。

* ベース URL （*ストアアドレス*&#x200B;とも呼ばれます）は、*web ノード*&#x200B;のホスト名またはIP アドレスを指定します
* データベース ホストは&#x200B;*リモート データベース サーバー*&#x200B;のIP アドレス（データベース サーバーがクラスター化されている場合はロード バランサー）です
* データベース ユーザー名は、アクセス権を付与した&#x200B;*ローカル web ノード*&#x200B;のデータベース ユーザーです
* データベースのパスワードは、ローカル web ノードユーザーのパスワードです
* データベース名は、リモートサーバー上のデータベースの名前です
