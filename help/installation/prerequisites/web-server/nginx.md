---
title: Nginx
description: 次の手順に従って、Adobe Commerceのオンプレミスインストール用に Nginx web サーバーをインストールして設定します。
exl-id: 041ddb9d-868e-4021-9388-1c9ea11bfd8f
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '1134'
ht-degree: 0%

---

# Nginx

Adobe Commerceは、nginx 1.x （または [最新のメインラインバージョン](https://nginx.org/en/linux_packages.html#mainline)）に設定します。 の最新バージョンもインストールする必要があります `php-fpm`.

インストール手順は、使用しているオペレーティングシステムによって異なります。 参照： [PHP](../php-settings.md) を参照してください。

## Ubuntu

次の節では、nginx、PHP、MySQL を使用して、Ubuntu にAdobe Commerce 2.x をインストールする方法について説明します。

### nginx のインストール

```bash
sudo apt -y install nginx
```

以下の手順でも可能です [ソースから nginx をビルド](https://www.armanism.com/blog/install-nginx-on-ubuntu)

以下の節を完了し、アプリケーションをインストールしたら、サンプルの設定ファイルを使用して以下を行います [nginx の設定](#configure-nginx).

### php-fpm のインストールと設定

Adobe Commerceには複数のが必要です [PHP 拡張機能](../php-settings.md) 正しく機能する。 これらの拡張機能に加えて、 `php-fpm` 拡張（nginx を使用している場合）

をインストールして設定するには `php-fpm`:

1. インストール `php-fpm` および `php-cli`:

   ```bash
   apt-get -y install php7.2-fpm php7.2-cli
   ```

   >[!NOTE]
   >
   >このコマンドは、利用可能な最新バージョンの PHP 7.2.X をインストールします。参照： [必要システム構成](../../system-requirements.md) （サポートされている PHP バージョン用）

1. を開きます `php.ini` エディター内のファイル：

   ```bash
   vim /etc/php/7.2/fpm/php.ini
   ```

   ```bash
   vim /etc/php/7.2/cli/php.ini
   ```

1. 次の行に一致するように両方のファイルを編集します。

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Adobe Commerceをテストする際は、メモリ制限を 2 G に設定することをお勧めします。 こちらを参照してください [必要な PHP 設定](../php-settings.md) を参照してください。

1. 保存して、エディターを終了します。

1. を再起動します `php-fpm` サービス：

   ```bash
   systemctl restart php7.2-fpm
   ```

### MySQL のインストールと設定

こちらを参照してください [MySQL](../database/mysql.md) を参照してください。

### インストールと設定

Adobe Commerceをダウンロードするには、次のようないくつかの方法があります。

* [Composer メタパッケージの取得](../../composer.md)

* [Git リポジトリのクローン](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

この例は、コマンドラインを使用した Composer ベースのインストールを示しています。

1. として [ファイルシステム所有者](../file-system/overview.md)アプリケーションサーバーにログインします。

1. Web サーバーの docroot ディレクトリまたは仮想ホストの docroot として設定したディレクトリに移動します。 この例では、Ubuntu のデフォルトを使用しています `/var/www/html`.

   ```bash
   cd /var/www/html
   ```

1. Composer をグローバルにインストール Adobe CommerceまたはMagento Open Sourceをインストールする前に、依存関係を更新するために Composer が必要です。

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. Magento Open SourceまたはAdobe Commerce メタパッケージを使用して Composer プロジェクトを作成します。

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   プロンプトが表示されたら、 [認証キー](../authentication-keys.md). あなたの _公開鍵_ はユーザー名、は _秘密鍵_ はパスワードです。

1. アプリケーションをインストールする前に、Web サーバーグループの読み取り/書き込み権限を設定します。 これは、コマンドラインがファイルをファイルシステムに書き込めるようにするために必要です。

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

1. からをインストール [コマンドライン](../../advanced.md). この例では、インストールディレクトリの名前がであることを前提としています `magento2ee`, `db-host` が同じマシン上にある（`localhost`）に設定し、 `db-name`, `db-user`、および `db-password` が全て `magento`:

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=magento \
   --db-user=magento \
   --db-password=magento \
   --backend-frontname=admin \
   --admin-firstname=admin \
   --admin-lastname=admin \
   --admin-email=admin@admin.com \
   --admin-user=admin \
   --admin-password=admin123 \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1 \
   --search-engine=elasticsearch7 \
   --elasticsearch-host=es-host.example.com \
   --elasticsearch-port=9200
   ```

1. 開発者モードに切り替えます。

   ```bash
   cd /var/www/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### Nginx の設定

を使用して nginx を設定することをお勧めします。 `nginx.conf.sample` インストールディレクトリおよび nginx 仮想ホストで提供される設定ファイル。

これらの手順は、nginx 仮想ホストに Ubuntu のデフォルトの場所（たとえば、 `/etc/nginx/sites-available`）を選択し、Ubuntu のデフォルトのドキュメントルート（例： `/var/www/html`ただし、環境に合わせてこれらの場所を変更することはできます。

1. サイトの新しい仮想ホストを作成します。

   ```bash
   vim /etc/nginx/sites-available/magento
   ```

1. 次の設定を追加します。

   ```conf
   upstream fastcgi_backend {
     server  unix:/run/php/php7.2-fpm.sock;
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
   >この `include` ディレクティブは、インストールディレクトリ内のサンプル nginx 設定ファイルを指す必要があります。

1. 置換 `www.magento-dev.com` とドメイン名を使用します。 これは、Adobe CommerceまたはMagento Open Sourceをインストールするときに指定したベース URL と一致する必要があります。

1. 保存して、エディターを終了します。

1. で新しく作成した仮想ホストへのシンボリックリンクを作成して、そのホストをアクティベートします。 `/etc/nginx/sites-enabled` ディレクトリ：

   ```bash
   ln -s /etc/nginx/sites-available/magento /etc/nginx/sites-enabled
   ```

1. 構文が正しいことを確認します。

   ```bash
   nginx -t
   ```

1. nginx を再起動します。

   ```bash
   systemctl restart nginx
   ```

### インストールの確認

Web ブラウザーを開き、サイトのベース URL に移動して、次の操作を行います [インストールの確認](../../next-steps/verify.md).

## CentOS 7

次の節では、nginx、PHP、および MySQL を使用して、CentOS 7 にAdobe Commerce 2.x をインストールする方法について説明します。

### nginx のインストール

```bash
yum -y install epel-release
```

```bash
yum -y install nginx
```

インストールが完了したら、nginx を起動し、ブート時に起動するように設定します。

```bash
systemctl start nginx
```

```bash
systemctl enable nginx
```

以下のセクションを完了し、アプリケーションをインストールしたら、サンプルの設定ファイルを使用して nginx を設定します。

### php-fpm のインストールと設定

Adobe Commerceには複数のが必要です [PHP](../php-settings.md) 正しく機能するための拡張機能。 これらの拡張機能に加えて、 `php-fpm` nginx を使用している場合は拡張機能です。

1. インストール `php-fpm`:

   ```bash
   yum -y install php70w-fpm
   ```

1. を開きます `/etc/php.ini` エディター内のファイル。

1. のコメントを解除 `cgi.fix_pathinfo` を行い、値をに変更します `0`.

1. 次の行に一致するようにファイルを編集します。

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Adobe CommerceまたはMagento Open Sourceをテストする場合は、メモリ制限を 2 G に設定することをお勧めします。 こちらを参照してください [必要な PHP 設定](../php-settings.md) を参照してください。

1. セッションパスディレクトリのコメントを解除し、パスを設定します。

   ```conf
   session.save_path = "/var/lib/php/session"
   ```

1. 保存して、エディターを終了します。

1. 開く `/etc/php-fpm.d/www.conf` エディターで。

1. 次の行に一致するようにファイルを編集します。

   ```conf
   user = nginx
   group = nginx
   listen = /run/php-fpm/php-fpm.sock
   listen.owner = nginx
   listen.group = nginx
   listen.mode = 0660
   ```

1. 環境の行をコメント解除します。

   ```conf
   env[HOSTNAME] = $HOSTNAME
   env[PATH] = /usr/local/bin:/usr/bin:/bin
   env[TMP] = /tmp
   env[TMPDIR] = /tmp
   env[TEMP] = /tmp
   ```

1. 保存して、エディターを終了します。

1. PHP セッションパスのディレクトリを作成し、所有者をに変更します。 `apache` ユーザーとグループ：

   ```bash
   mkdir -p /var/lib/php/session/
   ```

   ```bash
   chown -R apache:apache /var/lib/php/
   ```

1. PHP セッションパスのディレクトリを作成し、所有者をに変更します。 `apache` ユーザーとグループ：

   ```bash
   mkdir -p /run/php-fpm/
   ```

   ```bash
   chown -R apache:apache /run/php-fpm/
   ```

1. を開始する `php-fpm` サービスを提供し、起動時に開始するように設定します。

   ```bash
   systemctl start php-fpm
   ```

   ```bash
   systemctl enable php-fpm
   ```

1. を確認します `php-fpm` サービス実行中：

   ```bash
   netstat -pl | grep php-fpm.sock
   ```

### MySQL のインストールと設定

こちらを参照してください [MySQL](..//database/mysql.md) を参照してください。

### インストールと設定

Adobe Commerceをダウンロードするには、次のようないくつかの方法があります。

* [Composer メタパッケージの取得](../../composer.md)

* [Git リポジトリのクローン](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

この例は、コマンドラインを使用した Composer ベースのインストールを示しています。

1. として [ファイルシステム所有者](../file-system/overview.md)アプリケーションサーバーにログインします。

1. Web サーバーの docroot ディレクトリまたは仮想ホストの docroot として設定したディレクトリに移動します。 この例では、Ubuntu のデフォルトを使用しています `/var/www/html`.

   ```bash
   cd /var/www/html
   ```

1. Composer をグローバルにインストール Adobe CommerceまたはMagento Open Sourceをインストールする前に、依存関係を更新するために Composer が必要です。

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. Magento Open SourceまたはAdobe Commerce メタパッケージを使用して Composer プロジェクトを作成します。

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   プロンプトが表示されたら、 [認証キー](../authentication-keys.md). あなたの _公開鍵_ はユーザー名、は _秘密鍵_ はパスワードです。

1. アプリケーションをインストールする前に、Web サーバーグループの読み取り/書き込み権限を設定します。 これは、コマンドラインがファイルをファイルシステムに書き込めるようにするために必要です。

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

1. からをインストール [コマンドライン](../../advanced.md). この例では、インストールディレクトリの名前がであることを前提としています `magento2ee`, `db-host` が同じマシン上にある（`localhost`）に設定し、 `db-name`, `db-user`、および `db-password` が全て `magento`:

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=magento \
   --db-user=magento \
   --db-password=magento \
   --backend-frontname=admin \
   --admin-firstname=admin \
   --admin-lastname=admin \
   --admin-email=admin@admin.com \
   --admin-user=admin \
   --admin-password=admin123 \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1
   ```

1. 開発者モードに切り替えます。

   ```bash
   cd /var/www/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### Nginx の設定

を使用して nginx を設定することをお勧めします。 `nginx.conf.sample` インストールディレクトリおよび nginx 仮想ホストで提供される設定ファイル。

これらの手順は、nginx 仮想ホストのデフォルトの CentOS の場所（例： `/etc/nginx/conf.d`）を選択し、デフォルトの docroot （例： `/usr/share/nginx/html`ただし、環境に合わせてこれらの場所を変更することはできます。

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
   >この `include` ディレクティブは、インストールディレクトリ内のサンプル nginx 設定ファイルを指す必要があります。

1. 置換 `www.magento-dev.com` とドメイン名を使用します。

1. 保存して、エディターを終了します。

1. 構文が正しいことを確認します。

   ```bash
   nginx -t
   ```

1. nginx を再起動します。

   ```bash
   systemctl restart nginx
   ```

### SELinux と Firewalld の設定

CentOS 7 では、SELinux がデフォルトで有効になっています。 次のコマンドを使用して、実行中かどうかを確認します。

```bash
sestatus
```

SELinux と firewalld を設定するには：

1. SELinux 管理ツールをインストールします。

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

1. firewalld パッケージのインストール：

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

1. 次のコマンドを実行して HTTP および HTTPS のポートを開くと、web ブラウザーからベース URL にアクセスできます。

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

Web ブラウザーを開き、サイトのベース URL に移動して、次の操作を行います [インストールの確認](../../next-steps/verify.md).
