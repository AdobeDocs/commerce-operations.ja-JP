---
title: セキュリティを向上させるために docroot を変更する
description: Adobe CommerceまたはMagento Open Sourceのオンプレミスのファイルシステムへの不正なブラウザーベースのアクセスを防ぎます。
feature: Install, Security
exl-id: aabe148d-00c8-4011-a629-aa5abfa6c682
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 0%

---

# セキュリティを向上させるために docroot を変更する

Apache web サーバーを使用した標準インストールでは、Adobe Commerceはデフォルトの web ルートにインストールされます。 `/var/www/html/magento2`.

この `magento2/` ディレクトリには、次の内容が含まれます。

- `pub/`
- `setup/`
- `var/`

アプリケーションの提供元 `/var/www/html/magento2/pub`. ブラウザーからアクセスできるので、残りのファイルシステムは脆弱です。
webroot をに設定 `pub/` ディレクトリは、サイト訪問者がブラウザーからファイルシステムの機密性の高い領域にアクセスするのを防ぎます。

このトピックでは、既存のインスタンス上の Apache docroot を変更して、からファイルを提供する方法について説明します `pub/` ディレクトリの方が安全です。

## nginx に関するメモ

を使用している場合 [nginx](../prerequisites/web-server/nginx.md) および [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) インストールディレクトリに含まれているファイルは、おそらく次の場所からファイルを提供しています。 `pub/` ディレクトリ。

サイトを定義するサーバーブロックで使用する場合、 `nginx.conf.sample` の設定は、からのファイルを提供するようにサーバーの docroot 設定を上書きします。 `pub/` ディレクトリ。 例えば、次の設定の最後の行を参照してください。

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
- Adobe CommerceまたはMagento Open Source（2.4 以降）

>[!NOTE]
>
>こちらを参照してください [前提条件](../prerequisites/overview.md) および [インストールガイド](../overview.md) を参照してください。

## 1. サーバー設定を編集する

仮想ホストファイルの名前と場所は、実行している Apache のバージョンによって異なります。 この例は、Apache v2.4 上の仮想ホストファイルの名前と場所を示しています。

1. アプリケーションサーバーにログインします。
1. 仮想ホストファイルを編集します。

   ```bash
   vim /etc/apache2/sites-available/000-default.conf
   ```

1. パスをに追加します `pub/` ディレクトリ `DocumentRoot` ディレクティブ：

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

サーバーのホスト名または IP アドレスにディレクトリ名を追加して、アプリケーションのインストール時にベース URL を作成した場合（例：） `http://192.168.33.10/magento2`）、削除する必要があります。

>[!NOTE]
>
>置換 `192.168.33.10` サーバーのホスト名を使用します。

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

次のノードをに追加します `env.php` ファイル。

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

を参照してください。 [env.php リファレンス](../../configuration/reference/config-reference-envphp.md) を参照してください。

## 4. スイッチモード

[アプリケーションモード](../../configuration/bootstrap/application-modes.md)。これには以下が含まれます `production` および `developer`は、セキュリティを向上させ、開発を容易にするために設計されています。 名前が示すように、に切り替える必要があります。 `developer` アプリケーションを拡張またはカスタマイズする際のモードで、に切り替える `production` ライブ環境で実行している場合はモードになります。

モードの切り替えは、サーバー設定が正しく動作していることを確認するための重要な手順です。 CLI ツールを使用してモードを切り替えることができます。

1. インストールディレクトリに移動します。
1. 切り替え先 `production` モード。

   ```bash
   bin/magento deploy:mode:set production
   ```

   ```bash
   bin/magento cache:flush
   ```

1. ブラウザーを更新し、ストアフロントが正しく表示されていることを確認します。
1. 切り替え先 `developer` モード。

   ```bash
   bin/magento deploy:mode:set developer
   ```

   ```bash
   bin/magento cache:flush
   ```

1. ブラウザーを更新し、ストアフロントが正しく表示されていることを確認します。

## 5. ストアフロントを確認する

Web ブラウザーでストアフロントに移動して、すべてが機能していることを確認します。

1. Web ブラウザーを開き、アドレスバーにサーバーのホスト名または IP アドレスを入力します。 例： `http://192.168.33.10`.

   次の図は、ストアフロントページのサンプルを示しています。 次のように表示される場合、インストールは成功です。

   ![インストールが正常に完了したことを確認するストアフロント](../../assets/installation/install-success_store.png)

   を参照してください。 [トラブルシューティング セクション](https://support.magento.com/hc/en-us/articles/360032994352) ページに「404 （見つかりません）」と表示される場合や、画像、CSS、JS などの他のアセットの読み込みに失敗する場合。

1. ブラウザーからアプリケーションディレクトリにアクセスしてみてください。 サーバーのホスト名または IP アドレスにディレクトリ名をアドレスバーに追加します。

   404 または「アクセスが拒否されました」というメッセージが表示された場合、ファイルシステムへのアクセスが正常に制限されました。

   ![アクセス拒否](../../assets/installation/access-denied.png)
