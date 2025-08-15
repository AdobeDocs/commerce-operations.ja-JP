---
title: Apache
description: 次の手順に従って、Apache web サーバーをインストールし、Adobe Commerceのオンプレミスインストール用に設定します。
exl-id: a9a394c9-389f-42ef-9029-dd22c979cfb8
source-git-commit: f8c5d714a4e96d0508f745d1b7617696c8cc94a7
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---

# Apache

Adobe Commerceは Apache 2.4.x をサポートしています。

## Apache 必須ディレクティブ

1. URL の問題を引き起こす可能性のあるエンコードされたスラッシュのデコードを回避するために、サーバー設定（グローバル）または仮想ホスト設定で `AllowEncodedSlashes` を設定します。 例えば、API を使用して SKU にスラッシュが含まれる製品を取得する場合は、スラッシュを変換しないでください。 サンプルブロックが完全ではなく、他のディレクティブが必要な場合。

   ```conf
   <VirtualHost *:443>
     # Allow encoded slashes
     AllowEncodedSlashes NoDecode
   </VirtualHost>
   ```

## Apache の書き換えとアクセス

このトピックでは、Apache 2.4 の書き換えを有効にする方法と、[ 分散設定ファイル `.htaccess`](https://github.com/magento/magento2/blob/2.4-develop/.htaccess.sample) の設定を指定する方法について説明します。

Adobe Commerceは、サーバーの書き換えと `.htaccess` き換えを使用して、Apache にディレクトリレベルの手順を提供します。 次の手順は、このトピックの他のすべての節にも含まれています。

このセクションを使用して、Apache 2.4 の書き換えを有効にし、[ 分散設定ファイル、`.htaccess`](https://httpd.apache.org/docs/current/howto/htaccess.html) の設定を指定します

Adobe Commerceは、サーバーの書き換えと `.htaccess` き換えを使用して、Apache にディレクトリレベルの手順を提供します。

>[!NOTE]
>
>これらの設定を有効にしないと、通常、ストアフロントや管理者にスタイルが表示されません。

1. Apache 書き換えモジュールを有効にします。

   ```bash
   a2enmod rewrite
   ```

1. アプリケーションで分散 `.htaccess` 設定ファイルを使用できるようにするには、[Apache 2.4 ドキュメント ](https://httpd.apache.org/docs/current/mod/mod_rewrite.html) のガイドラインを参照してください。

   >[!TIP]
   >
   >Apache 2.4 では、サーバーのデフォルトのサイト設定ファイルは `/etc/apache2/sites-available/000-default.conf` です。

   例えば、次のコードを `000-default.conf` の末尾に追加できます。

   ```
   <Directory "/var/www/html">
       AllowOverride All
   </Directory>
   ```

   >[!NOTE]
   >
   >追加のパラメーターが必要になる場合があります。 詳しくは、[Apache 2.4 ドキュメント ](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order) を参照してください。

1. Apache 設定を変更した場合は、Apache を再起動します。

   ```bash
   service apache2 restart
   ```

   >[!NOTE]
   >
   >- 以前の Apache バージョンからアップグレードした場合は、まず `<Directory "/var/www/html">` で `<Directory "/var/www">` または `000-default.conf` を探します。
   >- Adobe Commerce ソフトウェアをインストールするディレクトリのディレクティブで `AllowOverride` の値を変更する必要があります。 例えば、web サーバーの docroot にをインストールするには、`<Directory /var/www>` でディレクティブを編集します。

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

```
Server version: Apache/2.4.04 (Ubuntu)
Server built: Jul 22 2020 14:35:32
```

- Apache がインストールされて *ない* 場合は、以下を参照してください。
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

   ```
   Server version: Apache/2.4.18 (Ubuntu)
   Server built: 2020-04-15T18:00:57
   ```

1. [rewrites and `.htaccess`](#apache-rewrites-and-htaccess) を有効にします。

### Ubuntu 上の Apache のアップグレード

Apache 2.4 にアップグレードするには：

1. Apache 2.4 が含まれている `ppa:ondrej` リポジトリを追加します。

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
   >依存関係が満たされていないために「apt-get install」コマンドが失敗した場合は、[https://askubuntu.com/](https://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa) などのリソースを参照してください。

1. インストールを確認します。

   ```bash
   apache2 -v
   ```

   次のようなメッセージが表示されます。

   ```
   Server version: Apache/2.4.10 (Ubuntu)
   Server built: Jul 22 2020 22:46:25
   ```

1. [rewrites and `.htaccess`](#apache-rewrites-and-htaccess) を有効にします。

## CentOS への Apache のインストール

Adobe Commerceを使用するには、Apache サーバーの書き換えが必要です。 また、`.htaccess` で使用できるディレクティブのタイプも指定する必要があります。アプリケーションでは、このタイプを使用して書き換えルールを指定します。

Apache のインストールと設定は、基本的に、ソフトウェアのインストール、書き換えの有効化、`.htaccess` ディレクティブの指定の 3 つの手順で行います。

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

   ```
   Server version: Apache/2.4.40 (Unix)
   Server built: Oct 16 2020 14:48:21
   ```

1. 次の節に進みます。

   >[!NOTE]
   >
   >CentOS で Apache 2.4 がデフォルトで提供されている場合でも、設定するには次の節を参照してください。

### CentOS の書き換えと.htaccess の有効化

1. ファイル `/etc/httpd/conf/httpd.conf` 開いて編集します。

   ```bash
   vim /etc/httpd/conf/httpd.conf`
   ```

1. 次で始まるブロックを見つけます。

   ```conf
   <Directory "/var/www/html">
   ```

1. `AllowOverride` の値を `All` に変更します。

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
   >上記の `Order` の値は、すべての場合で機能するとは限りません。 詳しくは、Apache ドキュメント（[2.4](https://httpd.apache.org/docs/2.4/mod/mod_authz_host.html#order)）を参照してください。

1. ファイルを保存し、テキストエディターを終了します。

1. Apache 設定を適用するには、Apache を再起動します。

   ```bash
   service apache2 restart
   ```

>[!NOTE]
>
>これらの設定を有効にしないと、通常、ストアフロントや管理者にスタイルが表示されません。

### Ubuntu の書き換えと.htaccess を有効にする

1. ファイル `/etc/apache2/sites-available/default` 開いて編集します。

   ```bash
   vim /etc/apache2/sites-available/default
   ```

1. 次で始まるブロックを見つけます。

   `<Directory "/var/www/html">`

1. `AllowOverride` の値を `All` に変更します。

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

1. `mod_rewrite` モジュールを使用するように Apache を設定します。

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

Web サイトの訪問者がサイトにアクセスできるようにするには、[Require ディレクティブ ](https://httpd.apache.org/docs/2.4/howto/access.html) のいずれかを使用します。

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
>上記の `Order` の値は、すべての場合で機能するとは限りません。 詳しくは、[Apache ドキュメント ](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order) を参照してください。
