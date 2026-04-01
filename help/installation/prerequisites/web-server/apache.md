---
title: オンプレミス デプロイメント用Apacheのインストール
description: オンプレミス Adobe Commerce デプロイメント用にApacheをインストールして設定する方法について説明します。 必要なモジュール、書き換え、および「.htaccess」設定を有効にします。
feature: Install, Configuration
badgePaas: label="オンプレミス" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce オンプレミス プロジェクトにのみ適用されます。"
exl-id: a9a394c9-389f-42ef-9029-dd22c979cfb8
source-git-commit: 352a71cb88ff38c0920201f49f1d7b889509fd61
workflow-type: tm+mt
source-wordcount: '1015'
ht-degree: 0%

---

# オンプレミス デプロイメント用のApacheのインストール {#apache}

このガイドでは、Commerce オンプレミスのデプロイメント用Apacheのインストールと、Adobe Commerceに必要なApache設定の設定について説明します。 これには、UbuntuとCentOSのApache要件とオペレーティングシステム固有の手順が共有されています。 Adobeでは、Commerce アプリケーションの機能とセキュリティの両方を保持するために、このガイドに記載されている設定手順に従うことをお勧めします。

Adobeでは、Adobe Commerce リリースの[必要システム構成](../../system-requirements.md)に記載されているApache バージョンをサポートしています。 サポートされているバージョンはリリースによって異なります。 Apacheには、サポートされているPHP設定も必要です。 関連するPHP要件については、[PHP設定](../php-settings.md)を参照してください。

環境に一致するセクションから始めます。

- Apacheが既にインストールされている場合は、[Apache要件の確認](#review-apache-requirements)から始めます。
- UbuntuでApacheをインストールまたはアップグレードする必要がある場合は、[Ubuntu](#installing-or-upgrading-apache-on-ubuntu)でApacheをインストールまたはアップグレードします。
- CentOSにApacheをインストールする必要がある場合は、[CentOSにApacheをインストール &#x200B;](#installing-apache-on-centos)に移動します。

## Apacheの要件の確認

Adobe Commerceをホストする任意のApache サーバーで、これらの要件を満たします。

### 必要なディレクティブの設定

サーバー設定（グローバル）または仮想ホスト設定で`AllowEncodedSlashes`を設定して、URLに問題が発生する可能性のあるエンコードされたスラッシュのデコードを避けます。 例えば、APIを介してSKUでスラッシュ付きの商品を取得する場合、スラッシュを変換する必要はありません。 次の例のブロックは完全ではなく、その他のディレクティブが必要です。

```conf
<VirtualHost *:443>
  # Allow encoded slashes
  AllowEncodedSlashes NoDecode
</VirtualHost>
```

### 書き換えと.htaccessの設定 {#apache-rewrites-and-htaccess}

このセクションを使用して、Apacheの書き換えを有効にし、[分散`.htaccess` ファイル &#x200B;](https://httpd.apache.org/docs/current/howto/htaccess.html)を設定します。 Adobe Commerceは、Apacheのディレクトリレベルの手順を提供するために、サーバーの書き換えと`.htaccess`を使用します。

>[!IMPORTANT]
>
>これらの設定を有効にしないと、通常、ストアフロントまたは管理者にスタイルが表示されなくなります。 また、`.htaccess`で定義されているAdobe Commerce セキュリティ保護をApacheが適用できないようにすることもできます。

1. Apache書き換えモジュールを有効にします。

   ```bash
   a2enmod rewrite
   ```

1. 分散`.htaccess`構成ファイルを使用するようにアプリケーションを有効にします。

   1. Ubuntuで、`/etc/apache2/sites-available/000-default.conf`を編集します。 その他のApache レイアウトまたは追加のパラメーターが必要な場合は、[Apache ドキュメント &#x200B;](https://httpd.apache.org/docs/current/mod/mod_rewrite.html)および[Apache アクセス制御ドキュメント &#x200B;](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order)を参照してください。

   1. Adobe Commerceをインストールするディレクトリの`AllowOverride` ディレクティブを追加または更新します。

   例えば、デフォルトの`docroot`にAdobe Commerceをインストールする場合は、次のブロックを`000-default.conf`に追加します。

   ```conf
   <Directory "/var/www/html">
     AllowOverride All
   </Directory>
   ```

   >[!NOTE]
   >
   >以前のバージョンのApacheからアップグレードした場合は、まず`<Directory "/var/www/html">`で既存の`<Directory "/var/www">`または`000-default.conf` ブロックを探します。 別の`docroot`にAdobe Commerceをインストールする場合は、そのパスに一致する`<Directory>` ブロックを更新します。

1. Apacheを再起動して変更を適用します。

   ```bash
   service apache2 restart
   ```

### 必要なモジュールのインストール

Adobe Commerceをインストールするには、次のApache モジュールが必要です。

- [mod_deflate.c](https://httpd.apache.org/docs/2.4/mod/mod_deflate.html)
- [mod_expires.c](https://httpd.apache.org/docs/2.4/mod/mod_expires.html)
- [mod_headers.c](https://httpd.apache.org/docs/2.4/mod/mod_headers.html)
- [mod_rewrite.c](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html)
- [mod_security.c](https://modsecurity.org)
- [mod_ssl.c](https://httpd.apache.org/docs/2.4/mod/mod_ssl.html)

## Apacheがインストールされていることを確認する

Apacheがインストールされていることを確認し、現在のバージョンを表示するには、次のように入力します。

```bash
apache2 -v
```

結果には、次のような情報が表示されます。

```text
Server version: Apache/<installed-version>
Server built: <build-date>
```

- Apacheが&#x200B;*not* インストールされている場合は、次を参照してください。
   - [UbuntuでのApacheのインストールまたはアップグレード](#installing-or-upgrading-apache-on-ubuntu)
   - [CentOSへのApacheのインストール](#installing-apache-on-centos)

## UbuntuでのApacheのインストールまたはアップグレード {#installing-or-upgrading-apache-on-ubuntu}

UbuntuでのApacheのインストールと設定は、次の3つの手順で行います。

1. ソフトウェアをインストールします。
1. 書き換えを有効にします。
1. `.htaccess` ディレクティブを指定します。

Apache サーバーの書き換えを設定する場合は、`.htaccess`で使用できるディレクティブのタイプを指定する必要があります。このディレクティブを使用して、アプリケーションは書き換えルールとセキュリティ保護を指定します。

### UbuntuでのApacheのインストール

1. まだインストールしていない場合は、Apacheをインストールします。

   ```bash
   apt-get -y install apache2
   ```

1. インストールを確認します。

   ```bash
   apache2 -v
   ```

   インストールが正常に完了したことを確認するための次の表示に類似したメッセージ：

   ```text
   Server version: Apache/<installed-version>
   Server built: <build-date>
   ```

1. 次のセクションに進みます。

   >[!NOTE]
   >
   >ApacheがデフォルトでUbuntuで提供されている場合でも、次の節を参照して設定してください。

### UbuntuでのApacheのアップグレード

Apacheが既にインストールされていて、`2.4`より前のバージョンを使用している場合は、Apache `2.4`またはデプロイしたAdobe Commerce バージョンでサポートされている最新バージョンにアップグレードします。 [必要システム構成](../../system-requirements.md)を参照してください。

1. パッケージ情報を更新：

   ```bash
   apt-get -y update
   ```

1. 必要に応じて、環境でサポートされているApache バージョンを提供するリポジトリを追加します。

1. Apacheのインストールまたはアップグレード：

   ```bash
   apt-get install -y apache2
   ```

   >[!NOTE]
   >
   >未解決の依存関係が原因で`apt-get install` コマンドが失敗した場合は、オペレーティング システム パッケージのドキュメントまたは配布サポート リソースを参照してください。

1. インストールを確認します。

   ```bash
   apache2 -v
   ```

1. インストールされているバージョンが、[必要システム構成](../../system-requirements.md)のAdobe Commerce リリースでサポートされているバージョンと一致することを確認してください。

1. Ubuntu[の`.htaccess`書き換えと](#enable-rewrites-and-htaccess-for-ubuntu)を有効にします。

### Ubuntuの書き換えと.htaccessを有効にする

1. 編集用に`/etc/apache2/sites-available/000-default.conf` ファイルを開きます：

   ```bash
   vim /etc/apache2/sites-available/000-default.conf
   ```

1. 次で始まるブロックを探します。

   ```conf
   <Directory "/var/www/html">
   ```

1. `AllowOverride`の値を`All`に変更します。

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

1. `mod_rewrite` モジュールを使用するようにApacheを設定します。

   ```bash
   cd /etc/apache2/mods-enabled
   ```

   ```bash
   ln -s ../mods-available/rewrite.load
   ```

1. Apacheを再起動して変更を適用します。

   ```bash
   service apache2 restart
   ```

>[!IMPORTANT]
>
>これらの設定を有効にしないと、通常、ストアフロントまたは管理者にスタイルが表示されなくなります。 また、`.htaccess`で定義されているAdobe Commerce セキュリティ保護をApacheが適用できないようにすることもできます。

## CentOSへのApacheのインストール {#installing-apache-on-centos}

CentOSへのApacheのインストールと設定は、次の3つの手順で行います。

1. ソフトウェアのインストール
2. 書き換えを有効にする
3. `.htaccess` ディレクティブを指定します。

Apache サーバーの書き換えを設定する場合は、`.htaccess`で使用できるディレクティブのタイプを指定する必要があります。このディレクティブを使用して、アプリケーションは書き換えルールとセキュリティ保護を指定します。

### Apacheのインストール

1. まだインストールしていない場合は、Apacheをインストールします。

   ```bash
   yum -y install httpd
   ```

1. インストールを確認します。

   ```bash
   httpd -v
   ```

   インストールが正常に完了したことを確認するための次の表示に類似したメッセージ：

   ```text
   Server version: Apache/<installed-version>
   Server built: <build-date>
   ```

1. 次のセクションに進みます。

   >[!NOTE]
   >
   >ApacheがCentOSでデフォルトで提供されている場合でも、次の節を参照して設定します。

### CentOSの書き換えと.htaccessを有効にする

1. 編集用に`/etc/httpd/conf/httpd.conf` ファイルを開きます：

   ```bash
   vim /etc/httpd/conf/httpd.conf
   ```

1. 次で始まるブロックを探します。

   ```conf
   <Directory "/var/www/html">
   ```

1. `AllowOverride`の値を`All`に変更します。

   例：

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
   >`Order`の前の値は、すべての場合で機能しない可能性があります。 詳しくは、[Apache ドキュメント &#x200B;](https://httpd.apache.org/docs/2.4/mod/mod_authz_host.html#order)を参照してください。

1. ファイルを保存し、テキストエディターを終了します。

1. Apache設定を適用するには、Apacheを再起動します。

   ```bash
   systemctl restart httpd
   ```

>[!IMPORTANT]
>
>これらの設定を有効にしないと、通常、ストアフロントまたは管理者にスタイルが表示されなくなります。 また、`.htaccess`で定義されているAdobe Commerce セキュリティ保護をApacheが適用できないようにすることもできます。

## 403 （禁止）エラーの解決

サイトにアクセスしようとしたときに403 Forbidden エラーが発生した場合は、Apache設定または仮想ホスト設定を更新して、サイトへの訪問者を有効にすることができます。

### Apacheの403 Forbidden エラーを解決する

Web サイト訪問者がサイトにアクセスできるようにするには、[要求ディレクティブ &#x200B;](https://httpd.apache.org/docs/2.4/howto/access.html)のいずれかを使用します。

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
>`Order`の前の値は、すべての場合で機能しない可能性があります。 詳しくは、[Apache ドキュメント &#x200B;](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order)を参照してください。
