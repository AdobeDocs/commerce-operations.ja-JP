---
title: リモート MySQL データベース接続を設定する
description: 次の手順に従って、Adobe CommerceとMagento Open Sourceのオンプレミスインストールでリモートデータベース接続を設定します。
source-git-commit: 61638d373408d9a7c3c3a935eee61927acfac7a6
workflow-type: tm+mt
source-wordcount: '746'
ht-degree: 0%

---


# リモート MySQL データベース接続を設定する

同じマシン上でデータベース・サーバと Web サーバを実行する代わりに、別のサーバ上でデータベースをホストする場合があります。

Adobeは、別のマシン上の MySQL サーバーに接続する方法を提供しました。 Adobe CommerceおよびMagento Open Source2.4.3 以降では、コードを変更せずにAmazon Web Services(AWS)Aurora データベースを使用するようにアプリケーションを設定することもできます。

Aurora は、AWSでホストされる、高パフォーマンスで完全に準拠した MySQL サーバです。

## AWS Aurora データベースへの接続

Aurora をデータベースとして使用すると、デフォルトのデータベースコネクタを使用して、通常のAdobe CommerceおよびMagento Open Source設定でデータベースを指定するのと同じくらい簡単に行えます。

実行時 `bin/magento setup:install`の場合は、 `db-` フィールド：

```bash
bin/magento setup:install ... --db-host='database-aurora.us-east-1.rds.amazonaws.com' --db-name='magento2' --db-user='username' --db-password='password' ...
```

この `db-host` の値は Aurora URL で、 `https://` および末尾 `:portnumber`  削除済み。

## リモートデータベース接続の設定

>[!NOTE]
>
>これは、経験豊富なネットワーク管理者またはデータベース管理者のみが使用する必要がある高度なトピックです。 必ず `root` ファイルシステムにアクセスでき、MySQL に `root`.

### 前提条件

開始する前に、以下をおこなう必要があります。

* [MySQL サーバーのインストール](mysql.md) をデータベースサーバーに設定します。
* [データベースインスタンスの作成](mysql.md#configuring-the-database-instance) をデータベースサーバーに設定します。
* MySQL クライアントをAdobe CommerceまたはMagento Open SourceWeb ノードにインストールします。 詳しくは、 MySQL のドキュメントを参照してください。

### 高可用性

Web サーバーまたはデータベースサーバーがクラスター化されている場合、リモートデータベース接続を構成するには、次のガイドラインを使用します。

* Web サーバーノードごとに接続を設定する必要があります。
* 通常は、データベース・ロード・バランサへのデータベース接続を設定します。ただし、データベースのクラスタリングは複雑な場合があり、設定は自由です。 Adobeでは、データベースのクラスタリングに関する具体的な推奨事項はありません。

   詳しくは、 [MySQL ドキュメント](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html).

### 接続の問題の解決

どちらかのホストに接続する際に問題が発生した場合は、最初に他のホストに ping を送信して、そのホストに到達可能であることを確認します。 ファイアウォールと SELinux の規則を変更する（SELinux を使用する場合）ことで、あるホストから別のホストへの接続を許可する必要が生じる場合があります。

## リモート接続を作成

リモート接続を作成するには：

1. データベースサーバー上で、 `root` 権限を設定し、MySQL 設定ファイルを開きます。

   これを探すには、次のコマンドを入力します。

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
   >Ubuntu 16 では、通常、パスは `/etc/mysql/mysql.conf.d/mysqld.cnf`.

1. 設定ファイルで `bind-address`.

   存在する場合は、値を次のように変更します。

   存在しない場合は、 `[mysqld]` 」セクションに入力します。

   ```conf
   bind-address = <ip address of your web node>
   ```

   詳しくは、 [MySQL ドキュメント](https://dev.mysql.com/doc/refman/5.6/en/server-options.html)（特に、クラスター化された Web サーバーがある場合）

1. 変更を設定ファイルに保存し、テキストエディターを終了します。
1. MySQL サービスを再起動します。

   * CentOS: `service mysqld restart`

   * Ubuntu: `service mysql restart`
   >[!NOTE]
   >
   >MySQL が起動しない場合は、syslog で問題の原因を調べます。 次を使用して問題を解決： [MySQL ドキュメント](https://dev.mysql.com/doc/refman/5.6/en/server-options.html#option_mysqld_bind-address) その他の権威あるソース

## データベース・ユーザーへのアクセス権の付与

Web ノードがデータベース・サーバに接続できるようにするには、リモート・サーバ上のデータベースに対する Web ノード・データベース・ユーザーのアクセス権を付与する必要があります。

この例では、 `root` リモート・ホスト上のデータベースへのフル・アクセス権を持つデータベース・ユーザー。

データベース・ユーザーにアクセス権を付与する手順は、次のとおりです。

1. データベースサーバーにログインします。
1. MySQL データベースに `root` ユーザー。
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
   >Web サーバーがクラスター化されている場合は、すべての Web サーバーで同じコマンドを入力します。 すべての Web サーバーで同じユーザー名を使用する必要があります。

## データベースアクセスの検証

Web ノードホストで、次のコマンドを入力して接続が機能することを確認します。

```bash
mysql -u <local database username> -h <database server ip address> -p
```

MySQL モニターが次のように表示される場合、データベースはAdobe CommerceまたはMagento Open Sourceの準備ができています。

```terminal
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 213 Server version: 5.6.26 MySQL Community Server (GPL)

Copyright (c) 2000, 2015, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its affiliates. Other names may be trademarks of their respective owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
```

Web サーバーがクラスター化されている場合は、各 Web サーバーホストでコマンドを入力します。

## Adobe CommerceまたはMagento Open Source

Adobe CommerceまたはMagento Open Sourceをインストールする場合は、次の情報を指定する必要があります。

* ベース [URL](https://glossary.magento.com/url) ( 別名 *ストアアドレス*) は、 *web ノード*
* データベースホストは *リモートデータベースサーバ* IP アドレス（データベース・サーバがクラスタ化されている場合はロード・バランサ）
* データベースのユーザー名： *ローカル web ノード* アクセス権を付与したデータベースユーザー
* データベースのパスワードは、ローカル Web ノードのユーザーのパスワードです
* データベース名は、リモートサーバー上のデータベースの名前です
