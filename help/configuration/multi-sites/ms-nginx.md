---
title: Nginx を使用して複数の Web サイトを設定する
description: このチュートリアルに従って、Nginx で複数の Web サイトを設定します。
exl-id: f13926a2-182c-4ce2-b091-19c5f978f267
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '943'
ht-degree: 0%

---

# Nginx を使用して複数の Web サイトを設定する

以下を前提としています。

- 開発マシン（ラップトップ、仮想マシンなど）で作業している。

  ホストされた環境に複数の web サイトをデプロイするには、追加のタスクが必要になる場合があります。詳しくは、ホスティングプロバイダーにお問い合わせください。

  クラウドインフラストラクチャー上にAdobe Commerceをセットアップするには、追加のタスクが必要になります。 Commerceこのトピックで取り上げる作業が完了したら、_Cloud Infrastructure ガイドの [ 複数の web サイトまたはストアの設定 ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) を参照してください_。

- 1 つの仮想ホストファイルで複数のドメインを使用することも、web サイトごとに 1 つの仮想ホストを使用することもできます。仮想ホスト設定ファイルは `/etc/nginx/sites-available` にあります。
- Commerceから提供された `nginx.conf.sample` を使用する場合は、このチュートリアルで説明した変更内容のみを適用します。
- Commerce ソフトウェアが `/var/www/html/magento2` にインストールされている。
- デフォルト以外に 2 つの web サイトがあります。

   - web サイトコード `french` とストアビューコード `fr` を使用した `french.mysite.mg`
   - web サイトコード `german` とストアビューコード `de` を使用した `german.mysite.mg`
   - `mysite.mg` は、デフォルトの web サイトとデフォルトのストア表示です。

>[!TIP]
>
>これらの値の見つけ方のヘルプについては、[Web サイトの作成 ](ms-admin.md#step-2-create-websites) および [ ストアビューの作成 ](ms-admin.md#step-4-create-store-views) を参照してください。

次に、nginx で複数の web サイトを設定するためのロードマップを示します。

1. 管理画面で [web サイト、ストア、ストア表示を設定 ](ms-admin.md) します。
1. [Nginx virtual host](#step-2-create-nginx-virtual-hosts)）を作成して、Commerceの web サイトごとに多数の web サイトまたは 1 つの Nginx virtual host をマッピングします（以下の手順を参照）。
1. Magentoが提供する `nginx.conf.sample` を使用して、[MAGE 変数 ](ms-overview.md) `$MAGE_RUN_TYPE` と `$MAGE_RUN_CODE` の値を nginx に渡します（以下に説明する手順）。

   - `$MAGE_RUN_TYPE` は、`store` または `website` のいずれかです。

      - `website` を使用して、web サイトをストアフロントに読み込みます。
      - `store` を使用して、ストアフロントに任意のストア表示を読み込みます。

   - `$MAGE_RUN_CODE` は、`$MAGE_RUN_TYPE` に対応する一意の web サイトまたはストア表示コードです。

1. Commerce管理者でベース URL 設定を更新します。

## 手順 1：管理での web サイト、ストア、ストアビューの作成

詳しくは [ 管理での複数の web サイト、ストア、ストア表示の設定 ](ms-admin.md) を参照してください。

## 手順 2:nginx 仮想ホストの作成

この手順では、ストアフロントで web サイトを読み込む方法について説明します。 Web サイトまたはストアビューを使用できます。ストアビューを使用する場合は、パラメーター値を適宜調整する必要があります。 このセクションのタスクは、`sudo` 権限を持つユーザーとして完了する必要があります。

1 つの [nginx 仮想ホストファイル ](#step-2-create-nginx-virtual-hosts) を使用するだけで、nginx 設定をシンプルでクリーンに保つことができます。 複数の仮想ホストファイルを使用すると、各ストアをカスタマイズできます（例えば、`french.mysite.mg` のストアにカスタムの場所を使用する場合）。

**1 つの仮想ホストを作成する場合** （シンプル）:

この設定は、[nginx 設定 ](../../installation/prerequisites/web-server/nginx.md) をさらに拡張したものです。

1. テキストエディターを開き、次の内容を `/etc/nginx/sites-available/magento` という名前の新しいファイルに追加します。

   ```conf
   map $http_host $MAGE_RUN_CODE {
       default '';
       french.mysite.mg french;
       german.mysite.mg german;
   }
   
   server {
       listen 80;
       server_name mysite.mg french.mysite.mg german.mysite.mg;
       set $MAGE_ROOT /var/www/html/magento2;
       set $MAGE_MODE developer;
       set $MAGE_RUN_TYPE website; #or set $MAGE_RUN_TYPE store;
       include /var/www/html/magento2/nginx.conf;
   }
   ```

1. ファイルへの変更を保存し、テキストエディターを終了します。
1. サーバー設定を確認します。

   ```bash
   nginx -t
   ```

1. 成功すると、次のメッセージが表示されます。

   ```
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   エラーが表示された場合は、仮想ホスト設定ファイルの構文を確認してください。

1. `/etc/nginx/sites-enabled` ディレクトリにシンボリックリンクを作成します。

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/magento magento
   ```

map ディレクティブの詳細については、[map ディレクティブに関する nginx ドキュメント ](http://nginx.org/en/docs/http/ngx_http_map_module.html#map) を参照してください。


**複数の仮想ホストを作成するには**:

1. テキストエディターを開き、次の内容を `/etc/nginx/sites-available/french.mysite.mg` という名前の新しいファイルに追加します。

   ```conf
   server {
       listen 80;
       server_name french.mysite.mg;
       set $MAGE_ROOT /var/www/html/magento2;
       set $MAGE_MODE developer;
       set $MAGE_RUN_TYPE website; #or set $MAGE_RUN_TYPE store;
       set $MAGE_RUN_CODE french;
       include /var/www/html/magento2/nginx.conf;
   }
   ```

1. 同じディレクトリ内に、`german.mysite.mg` という名前の別のファイルを、次の内容で作成します。

   ```conf
   server {
       listen 80;
       server_name german.mysite.mg;
       set $MAGE_ROOT /var/www/html/magento2;
       set $MAGE_MODE developer;
       set $MAGE_RUN_TYPE website; #or set $MAGE_RUN_TYPE store;
       set $MAGE_RUN_CODE german;
       include /var/www/html/magento2/nginx.conf;
   }
   ```

1. ファイルへの変更を保存し、テキストエディターを終了します。
1. サーバー設定を確認します。

   ```bash
   nginx -t
   ```

1. 成功すると、次のメッセージが表示されます。

   ```
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   エラーが表示された場合は、仮想ホスト設定ファイルの構文を確認してください。

1. `/etc/nginx/sites-enabled` ディレクトリにシンボリックリンクを作成します。

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/french.mysite.mg french.mysite.mg
   ```

   ```bash
   ln -s /etc/nginx/sites-available/german.mysite.mg german.mysite.mg
   ```

## 手順 3:nginx.conf.sample の変更

>[!TIP]
>
>`nginx.conf.sample` ファイルは編集しないでください。コアのCommerce ファイルであり、新しいリリースごとに更新される可能性があります。 代わりに、`nginx.conf.sample` ファイルをコピーし、名前を変更してから、コピーしたファイルを編集します。

**メインアプリケーションの PHP エントリポイントを編集するには、** の手順を実行します。

`nginx.conf.sample` ファイルを変更するには、**の手順を実行します。

1. テキストエディターを開き、`nginx.conf.sample` ファイル `<magento2_installation_directory>/nginx.conf.sample` を確認します。 次のセクションを探します。

   ```conf
   # PHP entry point for main application
   location ~ (index|get|static|report|404|503|health_check)\.php$ {
       try_files $uri =404;
       fastcgi_pass   fastcgi_backend;
       fastcgi_buffers 1024 4k;
   
       fastcgi_param  PHP_FLAG  "session.auto_start=off \n suhosin.session.cryptua=off";
       fastcgi_param  PHP_VALUE "memory_limit=1G \n max_execution_time=18000";
       fastcgi_read_timeout 600s;
       fastcgi_connect_timeout 600s;
   
       fastcgi_index  index.php;
       fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
       include        fastcgi_params;
   }
   ```

1. include ステートメントの前に次の 2 行を指定して、`nginx.conf.sample` ファイルを更新します。

   ```conf
   fastcgi_param MAGE_RUN_TYPE $MAGE_RUN_TYPE;
   fastcgi_param MAGE_RUN_CODE $MAGE_RUN_CODE;
   ```

メインアプリケーションの更新済み PHP エントリポイントの例を次に示します。

```conf
# PHP entry point for main application

location ~ (index|get|static|report|404|503|health_check)\.php$ {
    try_files $uri =404;
    fastcgi_pass   fastcgi_backend;
    fastcgi_buffers 1024 4k;

    fastcgi_param  PHP_FLAG  "session.auto_start=off \n suhosin.session.cryptua=off";
    fastcgi_param  PHP_VALUE "memory_limit=1G \n max_execution_time=18000";
    fastcgi_read_timeout 600s;
    fastcgi_connect_timeout 600s;

    fastcgi_index  index.php;
    fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
    # START - Multisite customization
    fastcgi_param MAGE_RUN_TYPE $MAGE_RUN_TYPE;
    fastcgi_param MAGE_RUN_CODE $MAGE_RUN_CODE;
    # END - Multisite customization
    include        fastcgi_params;
}
```

## 手順 4：ベース URL 設定の更新

Commerce管理で `french` と `german` の Web サイトのベース URL を更新する必要があります。

### フランス語の Web サイトのベース URL を更新

1. Commerce管理者にログインし、**ストア**/**設定**/**設定**/**一般**/**Web** に移動します。
1. _設定範囲_ を `french` の web サイトに変更します。
1. 「**ベース URL**」セクションを展開し、「**ベース URL**」および「**ベースリンク URL**」の値を `http://french.magento24.com/` に更新します。
1. 「**ベース URL （セキュア）**」セクションを展開し、「**セキュアベース URL**」および「**セキュアベースリンク URL**」の値を `https://french.magento24.com/` に更新します。
1. 「**設定を保存**」をクリックして、設定の変更を保存します。

### ドイツ語の Web サイトのベース URL を更新

1. Commerce管理者にログインし、**ストア**/**設定**/**設定**/**一般**/**Web** に移動します。
1. _設定範囲_ を `german` の web サイトに変更します。
1. 「**ベース URL**」セクションを展開し、「**ベース URL**」および「**ベースリンク URL**」の値を `http://german.magento24.com/` に更新します。
1. 「**ベース URL （セキュア）**」セクションを展開し、「**セキュアベース URL**」および「**セキュアベースリンク URL**」の値を `https://german.magento24.com/` に更新します。
1. 「**設定を保存**」をクリックして、設定の変更を保存します。

### キャッシュのクリーンアップ

次のコマンドを実行して、`config` および `full_page` キャッシュをクリーンアップします。

```bash
bin/magento cache:clean config full_page
```

## サイトの検証

ストアの URL に対して DNS を設定していない限り、`hosts` ファイルのホストへの静的ルートを追加する必要があります。

1. オペレーティングシステムの `hosts` ファイルを見つけます。
1. 次の形式で静的ルートを追加します。

   ```conf
   <ip-address> french.mysite.mg
   <ip-address> german.mysite.mg
   ```

1. ブラウザーで次の URL のいずれかに移動します。

   ```http
   http://mysite.mg/admin
   http://french.mysite.mg/frenchstoreview
   http://german.mysite.mg/germanstoreview
   ```

>[!INFO]
>
>- ホストされた環境に複数の web サイトをデプロイするには、追加のタスクが必要になる場合があります。詳しくは、ホスティングプロバイダーにお問い合わせください。
>- クラウドインフラストラクチャー上にAdobe Commerceを設定するには、さらに作業が必要です。[2&rbrace; クラウドインフラストラクチャー上のCommerceガイド ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) 複数のクラウド Web サイトまたはストアの設定 _を参照してください。_

### トラブルシューティング

- フランス語およびドイツ語のサイトが 404 を返すが、管理者が読み込む場合は、[ 手順 6：ベース URL にストアコードを追加する ](ms-admin.md#step-6-add-the-store-code-to-the-base-url) を完了していることを確認します。
- すべての URL が 404 を返す場合は、web サーバーを再起動していることを確認します。
- 管理者が正しく機能しない場合は、仮想ホストを正しく設定していることを確認してください。
