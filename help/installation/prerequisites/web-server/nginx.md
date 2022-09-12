---
title: Nginx
description: Nginx Web サーバーをインストールして、Adobe CommerceとMagento Open Sourceのオンプレミスインストール用に設定するには、次の手順に従います。
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '1180'
ht-degree: 0%

---


# Nginx

Adobe Commerceは nginx 1.18 ( または [最新のメインラインバージョン](https://nginx.org/en/linux_packages.html#mainline)) をクリックします。 最新バージョンの `php-fpm`.

インストール手順は、使用しているオペレーティングシステムによって異なります。 詳しくは、 [PHP](../php-settings.md) 」を参照してください。

## Ubuntu

次の節では、Ubuntu に nginx、PHP、MySQL を使用してAdobe CommerceとMagento Open Source2.x をインストールする方法について説明します。

### nginx のインストール

```bash
sudo apt -y install nginx
```

また、 [ソースから nginx を構築](https://www.armanism.com/blog/install-nginx-on-ubuntu)

以下の節でアプリケーションのインストールを完了した後、サンプルの設定ファイルを使用して [nginx の設定](#configure-nginx).

### php-fpm のインストールと設定

Adobe CommerceとMagento Open Sourceには複数の [PHP 拡張機能](../php-settings.md) 正しく機能しない。 これらの拡張機能に加えて、 `php-fpm` 拡張機能を使用します（nginx を使用している場合）。

をインストールして設定するには、以下を実行します。 `php-fpm`:

1. インストール `php-fpm` および `php-cli`:

   ```bash
   apt-get -y install php7.2-fpm php7.2-cli
   ```

   >[!NOTE]
   >
   >このコマンドは、PHP 7.2.X の利用可能な最新バージョンをインストールします。詳しくは、 [システム要件](../../system-requirements.md) サポートされる PHP バージョンの場合。

1. を開きます。 `php.ini` エディター内のファイル：

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
   >Adobe CommerceとMagento Open Sourceをテストする際は、メモリ制限を 2 G に設定することをお勧めします。 参照： [必要な PHP 設定](../php-settings.md) を参照してください。

1. エディターを保存して終了します。

1. を再起動します。 `php-fpm` サービス：

   ```bash
   systemctl restart php7.2-fpm
   ```

### MySQL のインストールと設定

参照： [MySQL](../database/mysql.md) を参照してください。

### インストールと設定

Adobe CommerceとMagento Open Sourceをダウンロードするには、次のような方法があります。

* [Composer のメタパッケージの取得](../../composer.md)

* [Git リポジトリのクローン](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

この例では、コマンドラインを使用した Composer ベースのインストールを示します。

1. を [ファイルシステム所有者](../file-system/overview.md)、アプリケーションサーバーにログインします。

1. Web サーバーの docroot ディレクトリ、または仮想ホストの docroot として設定したディレクトリに変更します。 この例では、Ubuntu デフォルトを使用しています。 `/var/www/html`.

   ```bash
   cd /var/www/html
   ```

1. Composer をグローバルにインストールします。 Adobe CommerceまたはMagento Open Sourceをインストールする前に、依存関係を更新するには、Composer が必要です。

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. Magento Open SourceまたはAdobe Commerceのメタパッケージを使用して Composer プロジェクトを作成します。

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   プロンプトが表示されたら、 [認証キー](../authentication-keys.md). お使いの _公開鍵_ はユーザー名です。あなたの _秘密鍵_ はパスワードです。

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

1. からインストールする [コマンドライン](../../advanced.md). この例では、インストールディレクトリの名前がとなっていることを前提としています。 `magento2ee`、 `db-host` は同じマシン (`localhost`)、および `db-name`, `db-user`、および `db-password` すべて `magento`:

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

### nginx の設定

nginx を設定するには、 `nginx.conf.sample` インストールディレクトリと nginx 仮想ホストに指定された設定ファイル。

これらの手順は、nginx 仮想ホストに Ubuntu デフォルトの場所を使用していることを前提としています ( 例： `/etc/nginx/sites-available`) と Ubuntu のデフォルトドキュメントルート ( 例： `/var/www/html`) で指定できますが、環境に合わせてこれらの場所を変更できます。

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

1. 置換 `www.magento-dev.com` をドメイン名に置き換えます。 Adobe CommerceまたはMagento Open Sourceのインストール時に指定したベース URL と一致させる必要があります。

1. エディターを保存して終了します。

1. 新しく作成した仮想ホストへの symlink を `/etc/nginx/sites-enabled` ディレクトリ：

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

Web ブラウザーを開き、サイトのベース URL( ) に移動します。 [インストールの確認](../../next-steps/verify.md).

## CentOS 7

以下の節では、CentOS 7 に nginx、PHP、MySQL を使用してAdobe CommerceとMagento Open Source2.x をインストールする方法について説明します。

### nginx のインストール

```bash
yum -y install epel-release
```

```bash
yum -y install nginx
```

インストールが完了したら、nginx を起動し、起動時に起動するように設定します。

```bash
systemctl start nginx
```

```bash
systemctl enable nginx
```

以下の節で説明する手順を完了し、アプリケーションをインストールした後、サンプルの設定ファイルを使用して nginx を設定します。

### php-fpm のインストールと設定

Adobe CommerceとMagento Open Sourceには複数の [PHP](../php-settings.md) 拡張機能が適切に機能しない問題を修正しました。 これらの拡張機能に加えて、 `php-fpm` 拡張機能を使用します（ nginx を使用している場合）。

1. インストール `php-fpm`:

   ```bash
   yum -y install php70w-fpm
   ```

1. を開きます。 `/etc/php.ini` ファイルを編集します。

1. コメントを解除 `cgi.fix_pathinfo` 行を開き、値を `0`.

1. 次の行に一致するようにファイルを編集します。

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Adobe CommerceまたはMagento Open Sourceをテストする際は、メモリ制限を 2 G に設定することをお勧めします。 参照： [必要な PHP 設定](../php-settings.md) を参照してください。

1. セッションパスディレクトリのコメントを解除し、パスを設定します。

   ```conf
   session.save_path = "/var/lib/php/session"
   ```

1. エディターを保存して終了します。

1. 開く `/etc/php-fpm.d/www.conf` 」と入力します。

1. 次の行に一致するようにファイルを編集します。

   ```conf
   user = nginx
   group = nginx
   listen = /run/php-fpm/php-fpm.sock
   listen.owner = nginx
   listen.group = nginx
   listen.mode = 0660
   ```

1. 環境行のコメントを解除します。

   ```conf
   env[HOSTNAME] = $HOSTNAME
   env[PATH] = /usr/local/bin:/usr/bin:/bin
   env[TMP] = /tmp
   env[TMPDIR] = /tmp
   env[TEMP] = /tmp
   ```

1. エディターを保存して終了します。

1. PHP セッションパスのディレクトリを作成し、所有者を `apache` ユーザーとグループ：

   ```bash
   mkdir -p /var/lib/php/session/
   ```

   ```bash
   chown -R apache:apache /var/lib/php/
   ```

1. PHP セッションパスのディレクトリを作成し、所有者を `apache` ユーザーとグループ：

   ```bash
   mkdir -p /run/php-fpm/
   ```

   ```bash
   chown -R apache:apache /run/php-fpm/
   ```

1. を開始します。 `php-fpm` 起動時にサービスを実行して設定を行う：

   ```bash
   systemctl start php-fpm
   ```

   ```bash
   systemctl enable php-fpm
   ```

1. を確認します。 `php-fpm` サービスは実行中です：

   ```bash
   netstat -pl | grep php-fpm.sock
   ```

### MySQL のインストールと設定

参照： [MySQL](..//database/mysql.md) を参照してください。

### インストールと設定

Adobe CommerceとMagento Open Sourceをダウンロードするには、次のような方法があります。

* [Composer のメタパッケージの取得](../../composer.md)

* [Git リポジトリのクローン](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

この例では、コマンドラインを使用した Composer ベースのインストールを示します。

1. を [ファイルシステム所有者](../file-system/overview.md)、アプリケーションサーバーにログインします。

1. Web サーバーの docroot ディレクトリ、または仮想ホストの docroot として設定したディレクトリに変更します。 この例では、Ubuntu デフォルトを使用しています。 `/var/www/html`.

   ```bash
   cd /var/www/html
   ```

1. Composer をグローバルにインストールします。 Adobe CommerceまたはMagento Open Sourceをインストールする前に、依存関係を更新するには、Composer が必要です。

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. Magento Open SourceまたはAdobe Commerceのメタパッケージを使用して Composer プロジェクトを作成します。

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   プロンプトが表示されたら、 [認証キー](../authentication-keys.md). お使いの _公開鍵_ はユーザー名です。あなたの _秘密鍵_ はパスワードです。

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

1. からインストールする [コマンドライン](../../advanced.md). この例では、インストールディレクトリの名前がとなっていることを前提としています。 `magento2ee`、 `db-host` は同じマシン (`localhost`)、および `db-name`, `db-user`、および `db-password` すべて `magento`:

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

### nginx の設定

nginx を設定するには、 `nginx.conf.sample` インストールディレクトリと nginx 仮想ホストに指定された設定ファイル。

これらの手順は、CentOS のデフォルトの場所を nginx 仮想ホスト ( 例えば、 `/etc/nginx/conf.d`) とデフォルトのドキュメントルート ( 例： `/usr/share/nginx/html`) で指定できますが、環境に合わせてこれらの場所を変更できます。

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

1. 置換 `www.magento-dev.com` をドメイン名に置き換えます。

1. エディターを保存して終了します。

1. 構文が正しいことを確認します。

   ```bash
   nginx -t
   ```

1. nginx を再起動します。

   ```bash
   systemctl restart nginx
   ```

### SELinux および Firewalld の設定

SELinux は、CentOS 7 でデフォルトで有効になっています。 次のコマンドを使用して、実行中かどうかを確認します。

```bash
sestatus
```

SELinux と Firewalld を設定するには：

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

1. Firewalld パッケージをインストールします。

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

1. 次のコマンドを実行して、HTTP および HTTPS 用のポートを開き、Web ブラウザーからベース URL にアクセスできるようにします。

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

Web ブラウザーを開き、サイトのベース URL( ) に移動します。 [インストールの確認](../../next-steps/verify.md).
