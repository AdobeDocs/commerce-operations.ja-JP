---
title: アップグレードのメンテナンスモードオプション
description: アップグレードを実行する際に、Adobe Commerce ストアフロントで顧客に表示されるカスタムメンテナンスモードページを作成します。
exl-id: 77e6d82d-5cc6-4d14-8b5c-1d2108f27b29
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# アップグレードのメンテナンスモードオプション

このトピックでは、Magentoアプリケーションのアップグレード中にユーザーに表示するカスタムメンテナンスページを作成する方法について説明します。 カスタムページの作成はオプションですが、アップグレードの一環としてサイトにアクセスできるので、推奨されます。

ユーザーをリダイレクトするカスタムページを作成すると、サイトへのアクセスができなくなり、サイトがメンテナンス中であることもユーザーに通知されます。

>[!NOTE]
>
>この節で説明するタスクは、`root` 権限を持つユーザーとして実行する必要があります。 開発者モードでは、カスタムメンテナンスページを設定できません。

## カスタムメンテナンスページの作成

メンテナンスページを作成し、そのページにリダイレクトするには、まず、次の名前のメンテナンスページを作成します。

- Apache:`<web server docroot>/maintenance.html`
- nginx: `<magento_root>/maintenance.html`

次の内容を追加します。

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

この節では、カスタムメンテナンスページを作成する方法と、そのページにトラフィックをリダイレクトする方法について説明します。

この節の例では、メンテナンスページを設定する 1 つの方法である次のファイルの変更方法を示します。

- Apache 2.4: `/etc/apache2/sites-available/000-default.conf`
- Apache 2.2:`/etc/apache2/sites-available/default` （Ubuntu）、`/etc/httpd/conf/httpd.conf` （CentOS）

カスタムメンテナンスページにトラフィックをリダイレクトするには：

1. 以下を行うように Apache 設定を更新します。

   - すべてのトラフィックをメンテナンスページにリダイレクト
   - 管理者がMagentoソフトウェアをアップグレードできるように、特定の IP を許可リストに加えるします。

   次の例は 192.0.2.110 を許可リストに加えるします。

   Apache 設定ファイルの末尾に次のコードを追加します。

   ```
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

1. [ システムをアップグレードします ](../implementation/perform-upgrade.md)。
1. サイトをテストし、正しく機能することを確認します。
1. アップグレードが完了したら、`maintenance.enable` を削除します。

## nginx のカスタムメンテナンスページ

この節では、カスタムメンテナンスページを作成する方法と、そのページにトラフィックをリダイレクトする方法について説明します。

カスタムメンテナンスページにトラフィックをリダイレクトするには：

1. テキストエディターを使用して、サーバーブロックを含む nginx 設定ファイルを開きます。
1. サーバーブロックに次の内容を追加します（`server` の内容が明確になるように表示されています。2 つ目のサーバーブロックは追加しないでください）。

   次の許可リストは、Magentoが `/var/www/html/magento2` にインストールされているシステムの IP アドレス 192.0.2.110 と 192.0.2.115 です。

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

1. nginx 設定をリロードします。

   ```bash
   service nginx reload
   ```

1. [ システムをアップグレードします ](../implementation/perform-upgrade.md)。
1. サイトをテストし、正しく機能することを確認します。
1. アップグレードが完了したら、`maintenance.enable` を削除するか、名前を変更します。
1. nginx 設定をリロードします。

   ```bash
   service nginx reload
   ```
