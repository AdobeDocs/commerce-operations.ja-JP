---
title: アップグレードのメンテナンスモードオプション
description: アップグレードの実行中に、Adobe Commerce ストアフロントで顧客に表示されるカスタムメンテナンスモードページを作成します。
exl-id: 77e6d82d-5cc6-4d14-8b5c-1d2108f27b29
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# アップグレードのメンテナンスモードオプション

ここでは、Magento アプリケーションのアップグレード中にユーザーに表示するカスタムメンテナンスページを作成する方法について説明します。 カスタムページの作成はオプションですが、アップグレードの一環としてサイトにアクセスできるため、お勧めします。

ユーザーをリダイレクトするカスタムページを作成すると、サイトへのアクセスが禁止され、サイトがメンテナンス中であることをユーザーに通知できます。

>[!NOTE]
>
>このセクションのタスクは、`root`権限を持つユーザーとして実行する必要があります。 開発者用モードでは、カスタムメンテナンスページを設定できません。

## カスタムメンテナンスページの作成

メンテナンスページを作成してリダイレクトするには、まず次の名前のメンテナンスページを作成します。

- Apache: `<web server docroot>/maintenance.html`
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

## Apacheのカスタムメンテナンスページ

この節では、カスタムメンテナンスページを作成する方法と、そのページにトラフィックをリダイレクトする方法について説明します。

この節の例では、メンテナンスページを設定する方法の1つとして、次のファイルを変更する方法を示します。

- Apache 2.4: `/etc/apache2/sites-available/000-default.conf`
- Apache 2.2: `/etc/apache2/sites-available/default` （Ubuntu）、`/etc/httpd/conf/httpd.conf` （CentOS）

トラフィックをカスタムメンテナンスページにリダイレクトするには：

1. Apache設定を更新して、次の操作を行います。

   - すべてのトラフィックをメンテナンスページにリダイレクトする
   - 管理者がMagento ソフトウェアをアップグレードできるように、特定のIPを許可リストに加えるします。

   次の使用例は、192.0.2.110を許可リストに加えるしています。

   Apache設定ファイルの最後に次の項目を追加します。

   ```text
   RewriteEngine On
   RewriteCond %{REMOTE_ADDR} !^192\.0\.2\.110
   RewriteCond %{DOCUMENT_ROOT}/maintenance.html -f
   RewriteCond %{DOCUMENT_ROOT}/maintenance.enable -f
   RewriteCond %{SCRIPT_FILENAME} !maintenance.html
   RewriteRule ^.*$ /maintenance.html [R=503,L]
   ErrorDocument 503 /maintenance.html
   Header Set Cache-Control "max-age=0, no-store"
   ```

1. Apacheを再起動します。

   - CentOS: `service httpd restart`
   - Ubuntu: `service apache2 restart`

1. 次のコマンドを入力します。

   ```shell
   touch <web server docroot>/maintenance.enable
   ```

1. [ システムをアップグレード ](../implementation/perform-upgrade.md)。
1. サイトを検証し、正しく機能することを確認する。
1. アップグレードが完了したら、`maintenance.enable`を削除します。

## nginxのカスタムメンテナンスページ

この節では、カスタムメンテナンスページを作成する方法と、そのページにトラフィックをリダイレクトする方法について説明します。

トラフィックをカスタムメンテナンスページにリダイレクトするには：

1. テキストエディターを使用して、サーバーブロックを含むnginx設定ファイルを開きます。
1. 以下をサーバーブロックに追加します（`server`は明確にするためにのみ表示されます。2番目のサーバーブロックを追加しないでください）。

   次のは、Magentoが`/var/www/html/magento2`にインストールされているシステム上のIP アドレス 192.0.2.110と192.0.2.115を許可リストに加えるします。

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

   ```shell
   touch <magento_root>/maintenance.enable
   ```

1. nginx設定をリロードします。

   ```shell
   service nginx reload
   ```

1. [ システムをアップグレード ](../implementation/perform-upgrade.md)。
1. サイトを検証し、正しく機能することを確認する。
1. アップグレードが完了したら、`maintenance.enable`を削除または名前変更します
1. nginx設定をリロードします。

   ```shell
   service nginx reload
   ```
