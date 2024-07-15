---
title: セキュリティを向上させるために docroot を変更する
description: Adobe Commerce オンプレミスのファイルシステムへの不正なブラウザーベースのアクセスを防ぐ。
feature: Install, Security
exl-id: aabe148d-00c8-4011-a629-aa5abfa6c682
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 0%

---

# セキュリティを向上させるために docroot を変更する

Apache web サーバーを使用した標準インストールでは、Adobe Commerceはデフォルトの web ルート `/var/www/html/magento2` にインストールされます。

`magento2/` ディレクトリには、次の内容が含まれます。

- `pub/`
- `setup/`
- `var/`

アプリケーションは `/var/www/html/magento2/pub` から提供されます。 ブラウザーからアクセスできるので、残りのファイルシステムは脆弱です。
webroot を `pub/` ディレクトリに設定すると、サイト訪問者がブラウザーからファイルシステムの機密性の高い領域にアクセスできなくなります。

このトピックでは、既存のインスタンス上の Apache docroot を変更して、より安全な `pub/` ディレクトリからファイルを提供する方法について説明します。

## nginx に関するメモ

[nginx](../prerequisites/web-server/nginx.md) と、インストールディレクトリに含まれる [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) ファイルを使用している場合は、おそらく `pub/` ディレクトリのファイルを既に提供しています。

サイトを定義するサーバーブロックで使用する場合、`nginx.conf.sample` の設定は、サーバーの docroot 設定を上書きして、`pub/` ディレクトリからファイルを提供します。 例えば、次の設定の最後の行を参照してください。

```conf
# /etc/nginx/sites-available/magento

upstream fastcgi_backend {
   server  unix:/run/php/php7.4-fpm.sock;
}

server {

         listen 80;
         server_name 192.168.33.10;
         set $MAGE_ROOT /var/www/html/magento2ce;
         include /var/www/html/magento2ce/nginx.conf.sample;
}
```

## 始める前に

このチュートリアルを完了するには、LAMP スタック上で動作しているインストールにアクセスする必要があります。

- Linux
- Apache （2.4 以降）
- MySQL （5.7 以降）
- PHP （7.4）
- Elasticsearch（7.x）または OpenSearch （1.2）
- Adobe Commerce（2.4 以降）

>[!NOTE]
>
>詳しくは、[ 前提条件 ](../prerequisites/overview.md) および [ インストールガイド ](../overview.md) を参照してください。

## 1. サーバー設定を編集する

仮想ホストファイルの名前と場所は、実行している Apache のバージョンによって異なります。 この例は、Apache v2.4 上の仮想ホストファイルの名前と場所を示しています。

1. アプリケーションサーバーにログインします。
1. 仮想ホストファイルを編集します。

   ```bash
   vim /etc/apache2/sites-available/000-default.conf
   ```

1. `DocumentRoot` ディレクティブへの `pub/` ディレクトリへのパスを追加します。

   ```conf
   <VirtualHost *:80>
   
            ServerAdmin webmaster@localhost
            DocumentRoot /var/www/html/magento2ce/pub
   
            ErrorLog ${APACHE_LOG_DIR}/error.log
            CustomLog ${APACHE_LOG_DIR}/access.log combined
   
            <Directory "/var/www/html">
                        AllowOverride all
            </Directory>
    </VirtualHost>
   ```

1. Apache を再起動します。

   ```bash
   systemctl restart apache2
   ```

## 2. ベース URL を更新する

サーバーのホスト名または IP アドレスにディレクトリ名を追加して、アプリケーションのインストール時にベース URL を作成した場合は（例：`http://192.168.33.10/magento2`）、削除する必要があります。

>[!NOTE]
>
>`192.168.33.10` をサーバーのホスト名に置き換えます。

1. データベースにログインします。

   ```bash
   mysql -u <user> -p
   ```

1. アプリケーションのインストール時に作成したデータベースを指定します。

   ```shell
   use <database-name>
   ```

1. ベース URL を更新します。

   ```shell
   UPDATE core_config_data SET value='http://192.168.33.10' WHERE path='web/unsecure/base_url';
   ```

## 3. env.php ファイルを更新する

`env.php` ファイルに次のノードを追加します。

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

詳しくは、[env.php リファレンス ](../../configuration/reference/config-reference-envphp.md) を参照してください。

## 4. スイッチモード

`production` と `developer` を含む [ アプリケーションモード ](../../configuration/bootstrap/application-modes.md) は、セキュリティを向上させ、開発を容易にするために設計されています。 名前が示すように、アプリケーションを拡張またはカスタマイズする場合は `developer` モードに切り替え、実稼働環境で実行する場合は `production` モードに切り替える必要があります。

モードの切り替えは、サーバー設定が正しく動作していることを確認するための重要な手順です。 CLI ツールを使用してモードを切り替えることができます。

1. インストールディレクトリに移動します。
1. `production` モードに切り替えます。

   ```bash
   bin/magento deploy:mode:set production
   ```

   ```bash
   bin/magento cache:flush
   ```

1. ブラウザーを更新し、ストアフロントが正しく表示されていることを確認します。
1. `developer` モードに切り替えます。

   ```bash
   bin/magento deploy:mode:set developer
   ```

   ```bash
   bin/magento cache:flush
   ```

1. ブラウザーを更新し、ストアフロントが正しく表示されていることを確認します。

## 5. ストアフロントを確認する

Web ブラウザーでストアフロントに移動して、すべてが機能していることを確認します。

1. Web ブラウザーを開き、アドレスバーにサーバーのホスト名または IP アドレスを入力します。 例：`http://192.168.33.10`。

   次の図は、ストアフロントページのサンプルを示しています。 次のように表示される場合、インストールは成功です。

   ![ インストールが成功したことを確認するストアフロント ](../../assets/installation/install-success_store.png)

   ページに 404 （見つかりません）が表示される場合や、画像、CSS、JS など他のアセットの読み込みに失敗する場合は、[ トラブルシューティングの節 ](https://support.magento.com/hc/en-us/articles/360032994352) を参照してください。

1. ブラウザーからアプリケーションディレクトリにアクセスしてみてください。 サーバーのホスト名または IP アドレスにディレクトリ名をアドレスバーに追加します。

   404 または「アクセスが拒否されました」というメッセージが表示された場合、ファイルシステムへのアクセスが正常に制限されました。

   ![ アクセスが拒否されました ](../../assets/installation/access-denied.png)
