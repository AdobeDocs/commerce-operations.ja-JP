---
title: アップグレードのメンテナンスモードオプション
description: 'アップグレードの実行中にAdobe CommerceまたはMagento Open Sourceストアフロントに表示されるカスタムメンテナンスモードページを作成します。 '
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---


# アップグレードのメンテナンスモードオプション

このトピックでは、Magento・アプリケーションのアップグレード中にユーザーに表示するカスタム・メンテナンス・ページを作成する方法について説明します。 カスタムページの作成は任意ですが、アップグレード時にサイトにアクセスできるので、お勧めします。

ユーザーをリダイレクトするカスタムページを作成すると、サイトへのアクセスが妨げられ、そのサイトがメンテナンス中であることをユーザーに通知します。

>[!NOTE]
>
>この節のタスクは、 `root` 権限。 開発者モードの間は、カスタムメンテナンスページを設定できません。

## カスタムメンテナンスページの作成

メンテナンスページを作成してそのページにリダイレクトするには、まず次の名前のメンテナンスページを作成します。

- Apache: `<web server docroot>/maintenance.html`
- nginx: `<magento_root>/maintenance.html`

次のコンテンツを追加します。

```html
<!DOCTYPE html>
<html>
<head>
<title>Temporarily Offline</title>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<style>
h1
{ font-size: 50px; }

body
{ text-align:center; font: 20px Helvetica, sans-serif; color: #333; }

</style>
</head>
<body>

# Temporarily offline

<p>We're down for a short time to perform maintenance on our site to give you the best possible experience. Check back soon!</p>
</body>
</html>
```

## Apache のカスタムメンテナンスページ

この節では、カスタムメンテナンスページの作成方法と、そのページにトラフィックをリダイレクトする方法について説明します。

この節の例では、次のファイルを変更する方法を示します。これは、メンテナンスページを設定する 1 つの方法です。

- Apache 2.4: `/etc/apache2/sites-available/000-default.conf`
- Apache 2.2: `/etc/apache2/sites-available/default` （ウブントゥ） `/etc/httpd/conf/httpd.conf` (CentOS)

トラフィックをカスタムメンテナンスページにリダイレクトするには：

1. Apache 設定を更新して、次の操作をおこないます。

   - すべてのトラフィックをメンテナンスページにリダイレクトします
   - 特定の IP をし許可リストて、管理者がMagento・ソフトウェアをアップグレードできるようにします。

   次の例の許可リストは 192.0.2.110 です。

   Apache 設定ファイルの末尾に次の内容を追加します。

   ```terminal
   RewriteEngine On
   RewriteCond %{REMOTE_ADDR} !^192\.0\.2\.110
   RewriteCond %{DOCUMENT_ROOT}/maintenance.html -f
   RewriteCond %{DOCUMENT_ROOT}/maintenance.enable -f
   RewriteCond %{SCRIPT_FILENAME} !maintenance.html
   RewriteRule ^.*$ /maintenance.html [R=503,L]
   ErrorDocument 503 /maintenance.html
   Header Set Cache-Control "max-age=0, no-store"
   ```

1. Apache を再起動します。

   - CentOS: `service httpd restart`
   - Ubuntu: `service apache2 restart`

1. 次のコマンドを入力します。

   ```bash
   touch <web server docroot>/maintenance.enable
   ```

1. [システムのアップグレード](../implementation/perform-upgrade.md).
1. サイトをテストして、正しく機能することを確認します。
1. アップグレードが完了したら、 `maintenance.enable`.

## nginx のカスタムメンテナンスページ

この節では、カスタムメンテナンスページの作成方法と、そのページにトラフィックをリダイレクトする方法について説明します。

トラフィックをカスタムメンテナンスページにリダイレクトするには：

1. テキストエディターを使用して [nginx](https://glossary.magento.com/nginx) サーバーブロックを含む設定ファイル。
1. 次の内容をサーバーブロック (`server` は、明確にするためにのみ表示されます。2 つ目のサーバーブロックを追加しないでください )。

   次の許可リストでは、Magentoがにインストールされているシステムの IP アドレス 192.0.2.110 と 192.0.2.115 を設定します。 `/var/www/html/magento2`:

   ```conf
   server {
        listen 80;
        set $MAGE_ROOT /var/www/html/magento2;
   
        set $maintenance off;
   
        if (-f $MAGE_ROOT/maintenance.enable) {
            set $maintenance on;
        }
   
        if ($remote_addr ~ (192.0.2.110|192.0.2.115)) {
            set $maintenance off;
        }
   
        if ($maintenance = on) {
            return 503;
        }
   
        location /maintenance {
        }
   
        error_page 503 @maintenance;
   
        location @maintenance {
        root $MAGE_ROOT;
        rewrite ^(.*)$ /maintenance.html break;
    }
   
        include /var/www/html/magento2/nginx.conf;
   }
   ```

1. 次のコマンドを入力します。

   ```bash
   touch <magento_root>/maintenance.enable
   ```

1. nginx 設定を再読み込みします。

   ```bash
   service nginx reload
   ```

1. [システムのアップグレード](../implementation/perform-upgrade.md).
1. サイトをテストして、正しく機能することを確認します。
1. アップグレードが完了したら、削除または名前の変更を行います `maintenance.enable`
1. nginx 設定を再読み込みします。

   ```bash
   service nginx reload
   ```
