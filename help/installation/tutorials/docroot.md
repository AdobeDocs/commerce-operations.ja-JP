---
title: セキュリティを向上させるために docroot を変更
description: Adobe CommerceやMagento Open Sourceオンプレミスのファイルシステムへの不正なブラウザベースのアクセスを防ぎます。
feature: Install, Security
exl-id: aabe148d-00c8-4011-a629-aa5abfa6c682
source-git-commit: 32dd5005422b98923ce1bdf6c3fb3f55c2ec15bd
workflow-type: tm+mt
source-wordcount: '586'
ht-degree: 0%

---

# セキュリティを向上させるために docroot を変更

Apache Web サーバーを使用した標準インストールでは、Adobe CommerceとMagento Open Sourceはデフォルトの Web ルートにインストールされます。 `/var/www/html/magento2`.

The `magento2/` ディレクトリには次の情報が含まれます。

- `pub/`
- `setup/`
- `var/`

アプリケーションの提供元： `/var/www/html/magento2/pub`. ファイルシステムの残りの部分は、ブラウザからアクセスできるため、脆弱です。
Web ルートを `pub/` ディレクトリを使用すると、サイト訪問者はブラウザーからファイルシステムの機密領域にアクセスできなくなります。

このトピックでは、既存のインスタンス上の Apache docroot を、 `pub/` ディレクトリに格納されます。これはより安全です。

## nginx に関する注意

を使用している場合、 [nginx](../prerequisites/web-server/nginx.md) そして [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) インストールディレクトリに含まれるファイルは、おそらく既に `pub/` ディレクトリ。

サイトを定義するサーバーブロックで使用する場合、 `nginx.conf.sample` 設定は、サーバーの docroot 設定よりも優先され、 `pub/` ディレクトリ。 例えば、次の設定の最後の行を参照します。

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

このチュートリアルを完了するには、LAMP スタック上で動作する作業用インストールにアクセスする必要があります。

- Linux
- Apache（2.4 以降）
- MySQL （5.7 以降）
- PHP (7.4)
- Elasticsearch(7.x) または OpenSearch (1.2)
- Adobe CommerceまたはMagento Open Source（2.4 以降）

>[!NOTE]
>
>参照： [前提条件](../prerequisites/overview.md) そして [インストールガイド](../overview.md) を参照してください。

## 1.サーバー設定を編集します

仮想ホストファイルの名前と場所は、実行している Apache のバージョンに応じて異なります。 この例は、Apache v2.4 上の仮想ホストファイルの名前と場所を示しています。

1. アプリケーションサーバーにログインします。
1. 仮想ホストファイルを編集します。

   ```bash
   vim /etc/apache2/sites-available/000-default.conf
   ```

1. パスを `pub/` ディレクトリの `DocumentRoot` ディレクティブ：

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

## 2.ベース URL を更新する

アプリケーションのインストール時に、サーバーのホスト名または IP アドレスにディレクトリ名を追加してベース URL を作成した場合 ( 例： `http://192.168.33.10/magento2`) を削除する必要があります。

>[!NOTE]
>
>置換 `192.168.33.10` をサーバーのホスト名に設定します。

1. データベースにログインします。

   ```bash
   mysql -u <user> -p
   ```

1. アプリケーションのインストール時に作成したデータベースを指定します。

   ```shell
   use <database-name>
   ```

1. ベース URL の更新：

   ```shell
   UPDATE core_config_data SET value='http://192.168.33.10' WHERE path='web/unsecure/base_url';
   ```

## 3. env.php ファイルを更新する

次のノードを `env.php` ファイル。

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

詳しくは、 [env.php リファレンス](../../configuration/reference/config-reference-envphp.md) を参照してください。

## 4.スイッチモード

[アプリケーションモード](../../configuration/bootstrap/application-modes.md)を含む `production` および `developer`は、セキュリティを強化し、開発を容易にするように設計されています。 名前が示すように、 `developer` モード：アプリケーションを拡張またはカスタマイズする際に使用し、 `production` モードを使用して、ライブ環境で実行しているとき。

モードの切り替えは、サーバー設定が正しく動作していることを確認するための重要な手順です。 CLI ツールを使用して、モードを切り替えることができます。

1. インストールディレクトリに移動します。
1. 切り替え先 `production` モード。

   ```bash
   bin/magento deploy:mode:set production
   ```

   ```bash
   bin/magento cache:flush
   ```

1. ブラウザーを更新し、ストアフロントが正しく表示されることを確認します。
1. 切り替え先 `developer` モード。

   ```bash
   bin/magento deploy:mode:set developer
   ```

   ```bash
   bin/magento cache:flush
   ```

1. ブラウザーを更新し、ストアフロントが正しく表示されることを確認します。

## 5.ストアフロントを確認します。

Web ブラウザーのストアフロントに移動して、すべてが機能していることを確認します。

1. Web ブラウザーを開き、アドレスバーにサーバーのホスト名または IP アドレスを入力します。 例： `http://192.168.33.10`.

   次の図は、ストアフロントページのサンプルを示しています。 次のように表示される場合は、インストールは成功しています。

   ![インストールが成功したことを確認するストアフロント](../../assets/installation/install-success_store.png)

   詳しくは、 [トラブルシューティング節](https://support.magento.com/hc/en-us/articles/360032994352) ページに 404（見つかりません）が表示されるか、画像、CSS、JS などの他のアセットの読み込みに失敗する場合。

1. ブラウザーからアプリケーションディレクトリにアクセスしてみてください。 アドレスバーで、サーバーのホスト名または IP アドレスにディレクトリ名を追加します。

   404 または「アクセスが拒否されました」というメッセージが表示された場合は、ファイルシステムへのアクセスが正常に制限されています。

   ![アクセス拒否](../../assets/installation/access-denied.png)
