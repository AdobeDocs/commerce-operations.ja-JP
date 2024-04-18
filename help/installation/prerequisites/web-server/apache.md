---
title: Apache
description: 次の手順に従って、Apache web サーバーをインストールし、Adobe Commerceのオンプレミスインストール用に設定します。
exl-id: a9a394c9-389f-42ef-9029-dd22c979cfb8
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---

# Apache

Adobe Commerceは Apache 2.4.x をサポートしています。

## Apache 必須ディレクティブ

1. を設定 `AllowEncodedSlashes` サーバー設定（グローバル）または仮想ホスト設定でを使用して、URL の問題の原因となる可能性のあるエンコードされたスラッシュのデコードを回避します。 例えば、API を使用して SKU にスラッシュが含まれる製品を取得する場合は、スラッシュを変換しないでください。 サンプルブロックが完全ではなく、他のディレクティブが必要な場合。

   ```conf
   <VirtualHost *:443>
     # Allow encoded slashes
     AllowEncodedSlashes NoDecode
   </VirtualHost>
   ```

## Apache の書き換えとアクセス

このトピックでは、Apache 2.4 の書き換えを有効にする方法と、の設定を指定する方法について説明します [分散構成ファイル、 `.htaccess`](https://httpd.apache.org/docs/current/howto/htaccess.html).

Adobe Commerceは、サーバーの書き換えを使用します。 `.htaccess` Apache にディレクトリレベルの手順を提供する。 次の手順は、このトピックの他のすべての節にも含まれています。

このセクションを使用して、Apache 2.4 の書き換えを有効にし、 [分散構成ファイル、 `.htaccess`](https://httpd.apache.org/docs/current/howto/htaccess.html)

Adobe Commerceは、サーバーの書き換えを使用します。 `.htaccess` Apache にディレクトリレベルの手順を提供する。

>[!NOTE]
>
>これらの設定を有効にしないと、通常、ストアフロントや管理者にスタイルが表示されません。

1. Apache 書き換えモジュールを有効にします。

   ```bash
   a2enmod rewrite
   ```

1. アプリケーションで分散されたを使用できるようにするには `.htaccess` 設定ファイルについては、のガイドラインを参照してください [Apache 2.4 ドキュメント](https://httpd.apache.org/docs/current/mod/mod_rewrite.html).

   >[!TIP]
   >
   >Apache 2.4 では、サーバーのデフォルトのサイト設定ファイルはです。 `/etc/apache2/sites-available/000-default.conf`.

   例えば、次のコードをに追加できます `000-default.conf`:

   ```terminal
   <Directory "/var/www/html">
       AllowOverride All
   </Directory>
   ```

   >[!NOTE]
   >
   >追加のパラメーターが必要になる場合があります。 詳しくは、 [Apache 2.4 ドキュメント](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).

1. Apache 設定を変更した場合は、Apache を再起動します。

   ```bash
   service apache2 restart
   ```

   >[!NOTE]
   >
   >- 以前の Apache バージョンからアップグレードした場合は、まずを探します `<Directory "/var/www/html">` または `<Directory "/var/www">` 。対象： `000-default.conf`.
   >- の値を変更する必要があります `AllowOverride` Adobe Commerce ソフトウェアをインストールするディレクトリのディレクティブで指定します。 例えば、web サーバーの docroot にをインストールするには、次のディレクティブを編集します `<Directory /var/www>`.

>[!NOTE]
>
>これらの設定を有効にしないと、通常、ストアフロントや管理者にスタイルが表示されません。

## Apache 必須モジュール

Adobe Commerceでは、次の Apache モジュールをインストールする必要があります。

- [mod_deflate.c](https://httpd.apache.org/docs/2.4/mod/mod_deflate.html)
- [mod_expires.c](https://httpd.apache.org/docs/2.4/mod/mod_expires.html)
- [mod_headers.c](https://httpd.apache.org/docs/2.4/mod/mod_headers.html)
- [mod_rewrite.c](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html)
- [mod_security.c](https://modsecurity.org)
- [mod_ssl.c](https://httpd.apache.org/docs/2.4/mod/mod_ssl.html)

## Apache のバージョンを確認する

現在実行中の Apache のバージョンを確認するには、次のように入力します。

```bash
apache2 -v
```

結果は次のように表示されます。

```terminal
Server version: Apache/2.4.04 (Ubuntu)
Server built: Jul 22 2020 14:35:32
```

- Apache が *ではない* インストール済み。以下を参照してください。
   - [Ubuntu での Apache のインストールまたはアップグレード](#installing-apache-on-ubuntu)
   - [CentOS への Apache のインストール](#installing-apache-on-centos)

## Ubuntu での Apache のインストールまたはアップグレード

次の節では、Apache のインストールまたはアップグレード方法について説明します。

- Apache のインストール
- Ubuntu 上の Apache 2.4 にアップグレードして、PHP 7.4 を使用します。

### Ubuntu への Apache のインストール

デフォルトバージョンの Apache をインストールするには：

1. Apache のインストール

   ```bash
   apt-get -y install apache2
   ```

1. インストールを確認します。

   ```bash
   apache2 -v
   ```

   結果は次のように表示されます。

   ```terminal
   Server version: Apache/2.4.18 (Ubuntu)
   Server built: 2020-04-15T18:00:57
   ```

1. Enable （有効） [書き換えと `.htaccess`](#apache-rewrites-and-htaccess).

### Ubuntu 上の Apache のアップグレード

Apache 2.4 にアップグレードするには：

1. を追加 `ppa:ondrej` apache 2.4 が含まれているリポジトリ：

   ```bash
   apt-get -y update
   ```

   ```bash
   apt-add-repository ppa:ondrej/apache2
   ```

   ```bash
   apt-get -y update
   ```

1. Apache 2.4 をインストールします。

   ```bash
   apt-get install -y apache2
   ```

   >[!NOTE]
   >
   >依存関係が満たされていないために「apt-get install」コマンドが失敗した場合は、次のようなリソースを参照してください。 [https://askubuntu.com/](https://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa).

1. インストールを確認します。

   ```bash
   apache2 -v
   ```

   次のようなメッセージが表示されます。

   ```terminal
   Server version: Apache/2.4.10 (Ubuntu)
   Server built: Jul 22 2020 22:46:25
   ```

1. Enable （有効） [書き換えと `.htaccess`](#apache-rewrites-and-htaccess).

## CentOS への Apache のインストール

Adobe Commerceを使用するには、Apache サーバーの書き換えが必要です。 で使用できるディレクティブのタイプも指定する必要があります `.htaccess`を使用します。アプリケーションでは、この値を使用して書き換えルールを指定します。

Apache のインストールと設定は、基本的に、ソフトウェアのインストール、書き換えの有効化、指定の 3 つの手順で行います `.htaccess` ディレクティブ。

### Apache のインストール

1. Apache 2.4 をまだインストールしていない場合は、インストールします。

   ```bash
   yum -y install httpd
   ```

1. インストールを確認します。

   ```bash
   httpd -v
   ```

   次のようなメッセージが表示され、インストールが成功したことを確認します。

   ```terminal
   Server version: Apache/2.4.40 (Unix)
   Server built: Oct 16 2020 14:48:21
   ```

1. 次の節に進みます。

   >[!NOTE]
   >
   >CentOS で Apache 2.4 がデフォルトで提供されている場合でも、設定するには次の節を参照してください。

### CentOS の書き換えと.htaccess の有効化

1. 開く `/etc/httpd/conf/httpd.conf` 編集用ファイル：

   ```bash
   vim /etc/httpd/conf/httpd.conf`
   ```

1. 次で始まるブロックを見つけます。

   ```conf
   <Directory "/var/www/html">
   ```

1. の値を変更します `AllowOverride` 対象： `All`.

   以下に例を挙げます。

   ```conf
   <Directory "/var/www/">
     Options Indexes FollowSymLinks MultiViews
     AllowOverride All
     Order allow,deny
     Allow from all
   </Directory>
   ```

   >[!NOTE]
   >
   >上記のの値 `Order` すべての場合に機能するとは限りません。 詳しくは、Apache のドキュメント（[2.4](https://httpd.apache.org/docs/2.4/mod/mod_authz_host.html#order)）に設定します。

1. ファイルを保存し、テキストエディターを終了します。

1. Apache 設定を適用するには、Apache を再起動します。

   ```bash
   service apache2 restart
   ```

>[!NOTE]
>
>これらの設定を有効にしないと、通常、ストアフロントや管理者にスタイルが表示されません。

### Ubuntu の書き換えと.htaccess を有効にする

1. 開く `/etc/apache2/sites-available/default` 編集用ファイル：

   ```bash
   vim /etc/apache2/sites-available/default
   ```

1. 次で始まるブロックを見つけます。

   `<Directory "/var/www/html">`

1. の値を変更します `AllowOverride` 対象： `All`.

   例：

   ```conf
   <Directory "/var/www/html">
     Options Indexes FollowSymLinks MultiViews
     AllowOverride All
     Order allow,deny
     Allow from all
   </Directory>
   ```

1. ファイルを保存し、テキストエディターを終了します。

1. を使用するように Apache を設定する `mod_rewrite` モジュール：

   ```bash
   cd /etc/apache2/mods-enabled
   ```

   ```bash
   ln -s ../mods-available/rewrite.load
   ```

1. Apache を再起動して、変更を適用します。

   ```bash
   service apache2 restart
   ```

## 403 （禁止）エラーの解決

サイトへのアクセス中に 403 Forbidden エラーが発生した場合は、Apache 設定または仮想ホスト設定を更新して、サイトへの訪問者を有効にできます。

### Apache 2.4 の 403 Forbidden エラーの解決

Web サイトの訪問者がサイトにアクセスできるようにするには、次のいずれかを使用します [ディレクティブを必要とする](https://httpd.apache.org/docs/2.4/howto/access.html).

例：

```conf
<Directory "/var/www/">
  Options Indexes FollowSymLinks MultiViews
  AllowOverride All
  Order allow,deny
  Require all granted
</Directory>
```

>[!NOTE]
>
>上記のの値 `Order` すべての場合に機能するとは限りません。 詳しくは、 [Apache ドキュメント](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).
