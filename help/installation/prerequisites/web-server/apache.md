---
title: Apache
description: Adobe CommerceとMagento Open Sourceのオンプレミスインストールに Apache Web サーバーをインストールして設定するには、次の手順に従います。
exl-id: a9a394c9-389f-42ef-9029-dd22c979cfb8
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '844'
ht-degree: 0%

---

# Apache

Adobe Commerceは Apache 2.4.x をサポートしています。

## Apache で必要なディレクティブ

1. 設定 `AllowEncodedSlashes` （グローバルに）、または仮想ホスト設定で、URL の問題を引き起こす可能性のあるエンコードされたスラッシュのデコードを避けるために、を設定します。 例えば、API を使用して SKU にスラッシュが付いた製品を取得する場合、その変換結果は望ましくありません。 サンプルブロックが完成せず、他のディレクティブが必要です。

   ```conf
   <VirtualHost *:443>
     # Allow encoded slashes
     AllowEncodedSlashes NoDecode
   </VirtualHost>
   ```

## Apache による書き換えと htaccess

このトピックでは、Apache 2.4 の書き換えを有効にする方法と、 [分散設定ファイル `.htaccess`](https://httpd.apache.org/docs/current/howto/htaccess.html).

Adobe CommerceとMagento Open Sourceは、サーバーの書き換えと `.htaccess` Apache にディレクトリレベルの手順を提供する場合。 このトピックの他のすべての節にも、次の手順が含まれています。

Apache 2.4 の書き換えを有効にし、 [分散設定ファイル `.htaccess`](https://httpd.apache.org/docs/current/howto/htaccess.html)

Adobe CommerceとMagento Open Sourceは、サーバーの書き換えと `.htaccess` Apache にディレクトリレベルの手順を提供する場合。

>[!NOTE]
>
>これらの設定を有効にしないと、通常、ストアフロントや管理者にスタイルが表示されません。

1. Apache Rewrite モジュールを有効にします。

   ```bash
   a2enmod rewrite
   ```

1. アプリケーションで配布済みの `.htaccess` 設定ファイル ( [Apache 2.4 ドキュメント](https://httpd.apache.org/docs/current/mod/mod_rewrite.html).

   >[!TIP]
   >
   >Apache 2.4 では、サーバーのデフォルトのサイト設定ファイルは次のようになります。 `/etc/apache2/sites-available/000-default.conf`.

   例えば、次のコードを `000-default.conf`:

   ```terminal
   <Directory "/var/www/html">
       AllowOverride All
   </Directory>
   ```

   >[!NOTE]
   >
   >場合によっては、追加のパラメーターが必要になることがあります。 詳しくは、 [Apache 2.4 ドキュメント](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).

1. Apache の設定を変更した場合は、Apache を再起動します。

   ```bash
   service apache2 restart
   ```

   >[!NOTE]
   >
   >- 以前の Apache バージョンからアップグレードした場合は、まずを探してください。 `<Directory "/var/www/html">` または `<Directory "/var/www">` in `000-default.conf`.
   >- 次の値を変更する必要があります： `AllowOverride` を、Adobe CommerceまたはMagento Open Source・ソフトウェアのインストール先のディレクトリのディレクティブに追加します。 例えば、Web サーバーのドキュメントルートにをインストールするには、でディレクティブを編集します。 `<Directory /var/www>`.

>[!NOTE]
>
>これらの設定を有効にしないと、通常、ストアフロントや管理者にスタイルが表示されません。

## Apache が必要なモジュール

Adobe CommerceおよびMagento Open Sourceでは、以下の Apache モジュールをインストールする必要があります。

- [mod_deflate.c](https://httpd.apache.org/docs/2.4/mod/mod_deflate.html)
- [mod_expires.c](https://httpd.apache.org/docs/2.4/mod/mod_expires.html)
- [mod_headers.c](https://httpd.apache.org/docs/2.4/mod/mod_headers.html)
- [mod_rewrite.c](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html)
- [mod_security.c](https://modsecurity.org)
- [mod_ssl.c](https://httpd.apache.org/docs/2.4/mod/mod_ssl.html)

## Apache のバージョンを確認します。

現在実行中の Apache のバージョンを確認するには、次のように入力します。

```bash
apache2 -v
```

結果は次のように表示されます。

```terminal
Server version: Apache/2.4.04 (Ubuntu)
Server built: Jul 22 2020 14:35:32
```

- Apache が *not* インストール済み：
   - [Ubuntu での Apache のインストールまたはアップグレード](#installing-apache-on-ubuntu)
   - [CentOS への Apache のインストール](#installing-apache-on-centos)

## Ubuntu での Apache のインストールまたはアップグレード

以下の節では、Apache のインストールまたはアップグレード方法について説明します。

- Apache のインストール
- PHP 7.4 を使用するには、Ubuntu 上の Apache 2.4 にアップグレードします。

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

1. 有効にする [書き換えと `.htaccess`](#apache-rewrites-and-htaccess).

### Ubuntu での Apache のアップグレード

Apache 2.4 にアップグレードするには：

1. 次を追加： `ppa:ondrej` リポジトリ (Apache 2.4):

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
   >&#39;apt-get install&#39;コマンドが未満の依存関係で失敗した場合は、次のようなリソースを参照してください。 [https://askubuntu.com/](https://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa).

1. インストールを確認します。

   ```bash
   apache2 -v
   ```

   次のようなメッセージが表示されます。

   ```terminal
   Server version: Apache/2.4.10 (Ubuntu)
   Server built: Jul 22 2020 22:46:25
   ```

1. 有効にする [書き換えと `.htaccess`](#apache-rewrites-and-htaccess).

## CentOS への Apache のインストール

Adobe CommerceとMagento Open Sourceでは、Apache でサーバーの書き換えを使用する必要があります。 また、で使用できるディレクティブのタイプも指定する必要があります。 `.htaccess`：アプリケーションが書き換えルールを指定する際に使用するものです。

Apache のインストールと設定は、基本的に、ソフトウェアのインストール、書き換えの有効化、指定の 3 つの手順で構成されます。 `.htaccess` ディレクティブ。

### Apache のインストール

1. Apache 2.4 をまだインストールしていない場合は、インストールします。

   ```bash
   yum -y install httpd
   ```

1. インストールを確認します。

   ```bash
   httpd -v
   ```

   インストールが成功したことを確認する次の表示に類似したメッセージ：

   ```terminal
   Server version: Apache/2.4.40 (Unix)
   Server built: Oct 16 2020 14:48:21
   ```

1. 次の節に進みます。

   >[!NOTE]
   >
   >CentOS で Apache 2.4 がデフォルトで提供されている場合でも、次の節を参照して設定してください。

### CentOS の書き換えと.htaccess の有効化

1. 開く `/etc/httpd/conf/httpd.conf` 編集用のファイル：

   ```bash
   vim /etc/httpd/conf/httpd.conf`
   ```

1. 次の語句で始まるブロックを見つけます。

   ```conf
   <Directory "/var/www/html">
   ```

1. の値を変更 `AllowOverride` から `All`.

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
   >以前の `Order` どの場合でも機能しない場合があります。 詳しくは、Apache のドキュメント ([2.4](https://httpd.apache.org/docs/2.4/mod/mod_authz_host.html#order)) をクリックします。

1. ファイルを保存し、テキストエディターを終了します。

1. Apache 設定を適用するには、Apache を再起動します。

   ```bash
   service apache2 restart
   ```

>[!NOTE]
>
>これらの設定を有効にしないと、通常、ストアフロントや管理者にスタイルが表示されません。

### Ubuntu の書き換えと.htaccess を有効にする

1. 開く `/etc/apache2/sites-available/default` 編集用のファイル：

   ```bash
   vim /etc/apache2/sites-available/default
   ```

1. 次の語句で始まるブロックを見つけます。

   `<Directory "/var/www/html">`

1. の値を変更 `AllowOverride` から `All`.

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

1. を使用するように Apache を設定 `mod_rewrite` モジュール：

   ```bash
   cd /etc/apache2/mods-enabled
   ```

   ```bash
   ln -s ../mods-available/rewrite.load
   ```

1. Apache を再起動して変更を適用します。

   ```bash
   service apache2 restart
   ```

## 403（禁止）エラーの解決

サイトにアクセスしようとしたときに 403 Forbidden エラーが発生した場合は、Apache 設定または仮想ホスト設定を更新して、サイトへの訪問者を有効にすることができます。

### Apache 2.4 の 403 Forbidden エラーの解決

Web サイトの訪問者がサイトにアクセスできるようにするには、 [Require ディレクティブ](https://httpd.apache.org/docs/2.4/howto/access.html).

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
>以前の `Order` どの場合でも機能しない場合があります。 詳しくは、 [Apache ドキュメント](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).
