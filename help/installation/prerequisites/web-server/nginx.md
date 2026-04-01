---
title: オンプレミス デプロイメント用のNginxのインストール
description: オンプレミス Adobe Commerceのデプロイメント用にNginx web サーバーをインストールおよび設定する方法について説明します。 PHP-FPMと仮想ホストを設定します。
feature: Install, Configuration
badgePaas: label="オンプレミス" type="Informative" url="https://experienceleague.adobe.com/ja/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce オンプレミス プロジェクトにのみ適用されます。"
exl-id: 041ddb9d-868e-4021-9388-1c9ea11bfd8f
source-git-commit: 352a71cb88ff38c0920201f49f1d7b889509fd61
workflow-type: tm+mt
source-wordcount: '1430'
ht-degree: 0%

---

# オンプレミスのデプロイメント用にNginxをインストールする {#nginx}

このガイドでは、Adobe Commerce オンプレミスのデプロイメント用にNginxをインストールし、Commerceに必要なNginx設定を設定する方法について説明します。 これには、UbuntuおよびCentOSのオペレーティングシステム固有の手順と、PHP-FPMの設定に関するガイダンスが含まれます。 Adobeでは、Commerce アプリケーションの機能とセキュリティの両方を保持するために、このガイドに記載されている設定手順に従うことをお勧めします。

Adobeは、お使いのAdobe Commerce リリースの[必要システム構成](../../system-requirements.md)に記載されているNginx バージョンをサポートしています。 サポートされているバージョンはリリースによって異なります。 Nginxでは、サポートされているPHP-FPM設定も必要です。 関連するPHP要件については、[PHP](../php-settings.md)を参照してください。

## Ubuntuへのインストール

このセクションでは、Nginx、PHP、MySQLを使用してUbuntuにAdobe Commerceをインストールする方法を説明します。

### Nginxのインストール

```bash
sudo apt -y install nginx
```

[&#x200B; ソースからNginxをビルドすることもできます](https://www.armanism.com/blog/install-nginx-on-ubuntu)。

次のセクションを完了してアプリケーションをインストールしたら、サンプル設定ファイルを使用して[Nginx](#configure-nginx)を設定します。 この推奨設定では、Commerce アプリケーションの機能とセキュリティの両方が保持されます。

### PHP-FPMのインストールと設定

Adobe Commerceを適切に機能させるには、複数の[PHP拡張機能](../php-settings.md)が必要です。 これらの拡張機能に加えて、Nginxを使用している場合は、`php-fpm`拡張機能もインストールして設定する必要があります。

`php-fpm`をインストールして設定するには：

1. Adobe Commerce リリースでサポートされているPHP バージョンの`php-fpm`および`php-cli` パッケージをインストールします。 Ubuntuでは、パッケージ名は通常、次のパターンに従います。

   ```bash
   apt-get -y install php<php-version>-fpm php<php-version>-cli
   ```

   >[!NOTE]
   >
   >`<php-version>`を、インストール中のAdobe Commerce リリースの[必要システム構成](../../system-requirements.md)に記載されているサポート対象のPHP マイナーバージョンに置き換えます。 次の手順では、ファイルパス、サービス名、ソケットパスで同じ値を使用します。

1. エディターで`php.ini` ファイルを開きます。

   ```bash
   vim /etc/php/<php-version>/fpm/php.ini
   ```

   ```bash
   vim /etc/php/<php-version>/cli/php.ini
   ```

1. 次の行に一致するように両方のファイルを編集します。

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Adobeでは、Adobe Commerceをテストする際に、メモリ制限を2 GBに設定することをお勧めします。 詳しくは、[必要なPHP設定](../php-settings.md)を参照してください。

1. エディターを保存して終了します。

1. `php-fpm` サービスを再起動します。

   ```bash
   systemctl restart php<php-version>-fpm
   ```

### MySQLのインストールと設定

詳しくは、[MySQL](../database/mysql.md)を参照してください。

### Adobe Commerceのインストール

Adobe Commerceは、次のような方法でダウンロードできます。

* [Composer メタパッケージを入手](../../composer.md)

* [Git リポジトリのクローンを作成](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository)

この例では、コマンドラインを使用したComposer ベースのインストールを示します。

1. [&#x200B; ファイルシステムの所有者](../file-system/overview.md)として、アプリケーションサーバーにログインします。

1. Web サーバーのdocroot ディレクトリまたは仮想ホストのdocrootとして設定したディレクトリに変更します。 この例では、Ubuntuのデフォルト `/var/www/html`を使用しています。

   ```bash
   cd /var/www/html
   ```

1. Composerをグローバルにインストールします。 Adobe Commerceをインストールする前に、Composerで依存関係を更新する必要があります。

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. Adobe Commerce メタパッケージを使用してComposer プロジェクトを作成します。

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   プロンプトが表示されたら、[認証キー](../authentication-keys.md)を入力します。 _公開鍵_&#x200B;はユーザー名、秘密鍵&#x200B;_はパスワードです。_

1. アプリケーションをインストールする前に、web サーバーグループの読み取り/書き込み権限を設定します。 これは、コマンドラインがファイルシステムにファイルを書き込めるようにするために必要です。

   ```bash
   cd /var/www/html/<magento install directory>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```bash
   chown -R :www-data . # Ubuntu
   ```

   ```bash
   chmod u+x bin/magento
   ```

1. [&#x200B; コマンドライン &#x200B;](../../advanced.md)からインストールします。 この例では、インストールディレクトリの名前が`magento2ee`で、データベースホストが同じマシン （`localhost`）上にあることが前提としています。

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=<db-name> \
   --db-user=<db-user> \
   --db-password=<db-password> \
   --backend-frontname=<backend-uri> \
   --admin-firstname=<admin-first-name> \
   --admin-lastname=<admin-last-name> \
   --admin-email=<admin-email> \
   --admin-user=<admin-user> \
   --admin-password=<admin-password> \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1 \
   --search-engine=<search-engine-value> \
   --<search-engine-host-parameter>=search-host.example.com \
   --<search-engine-port-parameter>=9200
   ```

   >[!NOTE]
   >
   >インストール中のAdobe Commerce リリースで必要な`--search-engine`値と一致するホスト/ポートオプションを使用します。 2.4.6より前のバージョンの場合は、`elasticsearch7`をElasticsearch 7またはOpenSearchの`--elasticsearch-*` オプションと共に使用します。 バージョン 2.4.6以降では、そのリリースでサポートされている検索エンジンの値と対応するCLI オプションを使用します。

1. 開発者モードに切り替える：

   ```bash
   cd /var/www/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### Nginxの設定

Adobeでは、Commerce アプリケーションの機能とセキュリティの両方を維持するために、インストールディレクトリに用意されている`nginx.conf.sample`設定ファイルとNginx仮想ホスト設定を使用してNginxを設定することをお勧めします。

>[!IMPORTANT]
>
>`nginx.conf.sample` ファイルは、必要なアプリケーションのルーティングとセキュリティ強化ルールを提供します。 例えば、サーバーにアップロードされる有害なスクリプトの実行を制限します。 このファイルを使用しない場合やルールを変更しない場合は、カスタム nginx設定に同等のセキュリティ制御を実装する責任があります。

これらの手順では、`/etc/nginx/sites-available`などのNginx仮想ホストのUbuntuのデフォルトの場所と、`/var/www/html`などのUbuntuのデフォルトのdocrootを使用していることを前提としています。 これらの場所は、環境に合わせて変更できます。

1. サイトの新しい仮想ホストを作成します。

   ```bash
   vim /etc/nginx/sites-available/magento
   ```

1. 次の設定を追加します。

   ```conf
   upstream fastcgi_backend {
     server  unix:/run/php/php<php-version>-fpm.sock;
   }
   
   server {
   
     listen 80;
     server_name www.magento-dev.com;
     set $MAGE_ROOT /var/www/html/magento2;
     include /var/www/html/magento2/nginx.conf.sample;
   }
   ```

   >[!NOTE]
   >
   >`include` ディレクティブは、インストールディレクトリのサンプル nginx設定ファイルを指している必要があります。

1. `www.magento-dev.com`をドメイン名に置き換えます。 これは、Adobe Commerceのインストール時に指定したベース URLと一致する必要があります。

1. エディターを保存して終了します。

1. 新しく作成した仮想ホストをアクティブ化するには、`/etc/nginx/sites-enabled` ディレクトリにシンボリックリンクを作成します。

   ```bash
   ln -s /etc/nginx/sites-available/magento /etc/nginx/sites-enabled
   ```

1. 構文が正しいことを確認します。

   ```bash
   nginx -t
   ```

1. Nginxを再起動します。

   ```bash
   systemctl restart nginx
   ```

### インストールの確認

インストールを確認するには、web ブラウザーを開き、サイトのベース URLに移動します。 詳細については、[&#x200B; インストールの確認](../../next-steps/verify.md)を参照してください。

## CentOS 7へのインストール

このセクションでは、Nginx、PHP、MySQLを使用してCentOS 7にAdobe Commerceをインストールする方法を説明します。

### Nginxのインストール

```bash
yum -y install epel-release
```

```bash
yum -y install nginx
```

インストールが完了したら、nginxを起動し、起動時に起動するように設定します。

```bash
systemctl start nginx
```

```bash
systemctl enable nginx
```

以下のセクションを完了してアプリケーションをインストールしたら、サンプル設定ファイルを使用してNginxを設定します。

### PHP-FPMのインストールと設定

Adobe Commerceを適切に機能させるには、いくつかの[PHP](../php-settings.md)拡張機能が必要です。 これらの拡張機能に加えて、Nginxを使用している場合は、`php-fpm`拡張機能もインストールして設定する必要があります。

1. `php-fpm`をインストール：

   ```bash
   yum -y install <php-fpm-package>
   ```

1. エディターで`/etc/php.ini` ファイルを開きます。

   >[!NOTE]
   >
   >インストール中のAdobe Commerce リリースでサポートされているPHP バージョンの`php-fpm`を提供するパッケージをインストールします。 パッケージ名は、リポジトリとオペレーティングシステムによって異なります。 [必要システム構成](../../system-requirements.md)を参照してください。

1. `cgi.fix_pathinfo`行のコメントを解除し、値を`0`に変更します。

1. 次の行に一致するようにファイルを編集します。

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Adobeでは、Adobe Commerceをテストする際に、メモリ制限を2 GBに設定することをお勧めします。 詳しくは、[必要なPHP設定](../php-settings.md)を参照してください。

1. セッションパスディレクトリのコメントを解除し、パスを設定します。

   ```conf
   session.save_path = "/var/lib/php/session"
   ```

1. エディターを保存して終了します。

1. エディターで`/etc/php-fpm.d/www.conf`を開きます。

1. 次の行に一致するようにファイルを編集します。

   ```conf
   user = nginx
   group = nginx
   listen = /run/php-fpm/php-fpm.sock
   listen.owner = nginx
   listen.group = nginx
   listen.mode = 0660
   ```

1. 環境行のコメントを解除：

   ```conf
   env[HOSTNAME] = $HOSTNAME
   env[PATH] = /usr/local/bin:/usr/bin:/bin
   env[TMP] = /tmp
   env[TMPDIR] = /tmp
   env[TEMP] = /tmp
   ```

1. エディターを保存して終了します。

1. PHP セッション パスのディレクトリを作成し、所有者を`nginx` ユーザーとグループに変更します。

   ```bash
   mkdir -p /var/lib/php/session/
   ```

   ```bash
   chown -R nginx:nginx /var/lib/php/
   ```

1. PHP-FPM ソケットのディレクトリを作成し、所有者を`nginx` ユーザーとグループに変更します。

   ```bash
   mkdir -p /run/php-fpm/
   ```

   ```bash
   chown -R nginx:nginx /run/php-fpm/
   ```

1. `php-fpm` サービスを開始し、起動時に開始するように設定します。

   ```bash
   systemctl start php-fpm
   ```

   ```bash
   systemctl enable php-fpm
   ```

1. `php-fpm` サービスが実行されていることを確認します。

   ```bash
   netstat -pl | grep php-fpm.sock
   ```

### MySQLのインストールと設定

詳しくは、[MySQL](../database/mysql.md)を参照してください。

### Adobe Commerceのインストール

Adobe Commerceは、次のような方法でダウンロードできます。

* [Composer メタパッケージを入手](../../composer.md)

* [Git リポジトリのクローンを作成](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository)

この例では、コマンドラインを使用したComposer ベースのインストールを示します。

1. [&#x200B; ファイルシステムの所有者](../file-system/overview.md)として、アプリケーションサーバーにログインします。

1. Web サーバーのdocroot ディレクトリまたは仮想ホストのdocrootとして設定したディレクトリに変更します。 この例では、CentOSのデフォルト `/usr/share/nginx/html`を使用します。

   ```bash
   cd /usr/share/nginx/html
   ```

1. Composerをグローバルにインストールします。 Adobe Commerceをインストールする前に、Composerで依存関係を更新する必要があります。

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. Adobe Commerce メタパッケージを使用してComposer プロジェクトを作成します。

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   プロンプトが表示されたら、[認証キー](../authentication-keys.md)を入力します。 _公開鍵_&#x200B;はユーザー名、秘密鍵&#x200B;_はパスワードです。_

1. アプリケーションをインストールする前に、web サーバーグループの読み取り/書き込み権限を設定します。 これは、コマンドラインがファイルシステムにファイルを書き込めるようにするために必要です。

   ```bash
   cd /usr/share/nginx/html/<magento install directory>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```bash
   chown -R :nginx . # CentOS
   ```

   ```bash
   chmod u+x bin/magento
   ```

1. [&#x200B; コマンドライン &#x200B;](../../advanced.md)からインストールします。 この例では、インストールディレクトリの名前が`magento2ee`で、データベースホストが同じマシン （`localhost`）上にあることが前提としています。

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=<db-name> \
   --db-user=<db-user> \
   --db-password=<db-password> \
   --backend-frontname=<backend-uri> \
   --admin-firstname=<admin-first-name> \
   --admin-lastname=<admin-last-name> \
   --admin-email=<admin-email> \
   --admin-user=<admin-user> \
   --admin-password=<admin-password> \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1
   ```

1. 開発者モードに切り替える：

   ```bash
   cd /usr/share/nginx/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### Nginxの設定

インストールディレクトリの`nginx.conf.sample` ファイルとNginx仮想ホスト設定を使用してNginxを設定することをお勧めします。

>[!IMPORTANT]
>
>`nginx.conf.sample` ファイルは、必要なアプリケーションのルーティングとセキュリティ強化ルールを提供します。 例えば、サーバーにアップロードされる有害なスクリプトの実行を制限します。 このファイルを使用しない場合やルールを変更しない場合は、カスタム nginx設定に同等のセキュリティ制御を実装する責任があります。

これらの手順では、`/etc/nginx/conf.d`などのNginx仮想ホストのCentOSのデフォルトの場所と、`/usr/share/nginx/html`などのデフォルトのdocrootを使用していることを前提としています。 これらの場所は、環境に合わせて変更できます。

1. サイトの新しい仮想ホストを作成します。

   ```bash
   vim /etc/nginx/conf.d/magento.conf
   ```

1. 次の設定を追加します。

   ```conf
   upstream fastcgi_backend {
     server  unix:/run/php-fpm/php-fpm.sock;
   }
   
   server {
   
     listen 80;
     server_name www.magento-dev.com;
     set $MAGE_ROOT /usr/share/nginx/html/magento2;
     include /usr/share/nginx/html/magento2/nginx.conf.sample;
   }
   ```

   >[!NOTE]
   >
   >`include` ディレクティブは、インストールディレクトリのサンプル nginx設定ファイルを指している必要があります。

1. `www.magento-dev.com`をドメイン名に置き換えます。

1. エディターを保存して終了します。

1. 構文が正しいことを確認します。

   ```bash
   nginx -t
   ```

1. Nginxを再起動します。

   ```bash
   systemctl restart nginx
   ```

### SELinuxとfirewalldの設定

CentOS 7では、SELinuxがデフォルトで有効になっています。 次のコマンドを使用して、実行中であることを確認します。

```bash
sestatus
```

SELinuxとfirewalldを設定するには：

1. SELinux管理ツールをインストールします。

   ```bash
   yum -y install policycoreutils-python
   ```

1. 次のコマンドを実行して、インストールディレクトリのセキュリティコンテキストを変更します。

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/app/etc(/.*)?'
   ```

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/var(/.*)?'
   ```

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/pub/media(/.*)?'
   ```

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/pub/static(/.*)?'
   ```

   ```bash
   restorecon -Rv '/usr/share/nginx/html/magento2/'
   ```

1. firewalld パッケージをインストールします。

   ```bash
   yum -y install firewalld
   ```

1. ファイアウォールサービスを起動し、起動時に起動するように設定します。

   ```bash
   systemctl start firewalld
   ```

   ```bash
   systemctl enable firewalld
   ```

1. 次のコマンドを実行して、HTTPおよびHTTPSのポートを開き、web ブラウザーからベース URLにアクセスできるようにします。

   ```bash
   firewall-cmd --permanent --add-service=http
   ```

   ```bash
   firewall-cmd --permanent --add-service=https
   ```

   ```bash
   firewall-cmd --reload
   ```

### インストールの確認

インストールを確認するには、web ブラウザーを開き、サイトのベース URLに移動します。 詳細については、[&#x200B; インストールの確認](../../next-steps/verify.md)を参照してください。
