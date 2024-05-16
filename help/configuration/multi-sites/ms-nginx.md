---
title: Nginx を使用して複数の Web サイトを設定する
description: このチュートリアルに従って、Nginx で複数の Web サイトを設定します。
exl-id: f13926a2-182c-4ce2-b091-19c5f978f267
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '943'
ht-degree: 0%

---

# Nginx を使用して複数の Web サイトを設定する

以下を前提としています。

- 開発マシン（ラップトップ、仮想マシンなど）で作業している。

  ホストされた環境に複数の web サイトをデプロイするには、追加のタスクが必要になる場合があります。詳しくは、ホスティングプロバイダーにお問い合わせください。

  クラウドインフラストラクチャー上にAdobe Commerceをセットアップするには、追加のタスクが必要になります。 このトピックで説明するタスクを完了したら、次を参照してください [複数の web サイトまたはストアを設定](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) が含まれる _クラウドインフラストラクチャー上のCommerce ガイド_.

- 1 つの仮想ホストファイルで複数のドメインを使用することも、web サイトごとに 1 つの仮想ホストを使用することもできます。仮想ホスト設定ファイルは、次の場所に配置されます。 `/etc/nginx/sites-available`.
- を使用します `nginx.conf.sample` Commerceによって、このチュートリアルで説明した変更のみが提供されます。
- Commerce ソフトウェアのインストール先 `/var/www/html/magento2`.
- デフォルト以外に 2 つの web サイトがあります。

   - `french.mysite.mg` （web サイトコードを使用） `french` およびストア表示コード `fr`
   - `german.mysite.mg` （web サイトコードを使用） `german` およびストア表示コード `de`
   - `mysite.mg` は、デフォルトの web サイトとデフォルトのストア表示です。

>[!TIP]
>
>こちらを参照してください [Web サイトの作成](ms-admin.md#step-2-create-websites) および [ストア表示の作成](ms-admin.md#step-4-create-store-views) これらの値の検索に関するヘルプ。

次に、nginx で複数の web サイトを設定するためのロードマップを示します。

1. [Web サイト、ストア、ストアビューの設定](ms-admin.md) admin.
1. を作成 [Nginx 仮想ホスト](#step-2-create-nginx-virtual-hosts)）を使用して、Commerceの web サイトごとに多数の web サイトまたは 1 つの Nginx Virtual Host をマッピングします（以下に説明する手順）。
1. の値を渡します [MAGE 変数](ms-overview.md) `$MAGE_RUN_TYPE` および `$MAGE_RUN_CODE` Magentoを使用して nginx に送信 `nginx.conf.sample` （手順は以下で説明します）。

   - `$MAGE_RUN_TYPE` 次のいずれかになります `store` または `website`:

      - 使用方法 `website` で web サイトをストアフロントに読み込みます。
      - 使用方法 `store` をクリックして、ストアフロントの任意のストア表示を読み込みます。

   - `$MAGE_RUN_CODE` は、に対応する一意の web サイトまたはストア表示コードです `$MAGE_RUN_TYPE`.

1. Commerce管理者でベース URL 設定を更新します。

## 手順 1：管理での web サイト、ストア、ストアビューの作成

参照： [管理での複数の web サイト、ストア、ストア表示の設定](ms-admin.md).

## 手順 2:nginx 仮想ホストの作成

この手順では、ストアフロントで web サイトを読み込む方法について説明します。 Web サイトまたはストアビューを使用できます。ストアビューを使用する場合は、パラメーター値を適宜調整する必要があります。 以下を持つユーザーとして、この節で説明するタスクを完了する必要があります。 `sudo` 権限。

1 つだけを使用 [nginx 仮想ホスト ファイル](#step-2-create-nginx-virtual-hosts)を使用すれば、nginx の設定をシンプルかつクリーンに保つことができます。 複数の仮想ホストファイルを使用すると、各ストアをカスタマイズして（に対してカスタムの場所を使用する） `french.mysite.mg` 例えば）に保存します。

**1 つの仮想ホストを作成するには** （シンプル）:

この設定は、次の場合に拡張されます [nginx 設定](../../installation/prerequisites/web-server/nginx.md).

1. テキストエディターを開き、次の内容をという名前の新しいファイルに追加します。 `/etc/nginx/sites-available/magento`:

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

   ```terminal
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   エラーが表示された場合は、仮想ホスト設定ファイルの構文を確認してください。

1. にシンボリックリンクを作成 `/etc/nginx/sites-enabled` ディレクトリ：

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/magento magento
   ```

map ディレクティブの詳細については、を参照してください [map ディレクティブに関する nginx ドキュメント](http://nginx.org/en/docs/http/ngx_http_map_module.html#map).


**複数の仮想ホストを作成するには**:

1. テキストエディターを開き、次の内容をという名前の新しいファイルに追加します。 `/etc/nginx/sites-available/french.mysite.mg`:

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

1. という名前の別のファイルを作成します。 `german.mysite.mg` 同じディレクトリに以下の内容を格納します。

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

   ```terminal
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   エラーが表示された場合は、仮想ホスト設定ファイルの構文を確認してください。

1. にシンボリックリンクを作成する `/etc/nginx/sites-enabled` ディレクトリ：

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
>を編集しないでください `nginx.conf.sample` ファイル。新しいリリースごとに更新される可能性のあるコア Commerce ファイルです。 代わりに、をコピーします `nginx.conf.sample` ファイル名を変更し、コピーしたファイルを編集します。

**メインアプリケーションの PHP エントリポイントを編集する**:

を変更するには `nginx.conf.sample` ファイル**:

1. テキストエディターを開き、 `nginx.conf.sample` ファイル、`<magento2_installation_directory>/nginx.conf.sample`. 次のセクションを探します。

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

1. を更新 `nginx.conf.sample` ファイルの include ステートメントの前に次の 2 行を追加します。

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

のベース URL を更新する必要があります `french` および `german` Commerce管理画面の web サイト。

### フランス語の Web サイトのベース URL を更新

1. Commerce管理者にログインし、に移動します。 **ストア** > **設定** > **設定** > **一般** > **Web**.
1. 変更： _設定スコープ_ に `french` web サイト。
1. を展開 **ベース URL** 「」セクションを選択して「」を更新 **ベース URL** および **ベースリンク URL** value to `http://french.magento24.com/`.
1. を展開 **ベース URL （セキュア）** 「」セクションを選択して「」を更新 **セキュアなベース URL** および **セキュアベースリンク URL** value to `https://french.magento24.com/`.
1. クリック **設定を保存** 設定変更を保存します。

### ドイツ語の Web サイトのベース URL を更新

1. Commerce管理者にログインし、に移動します。 **ストア** > **設定** > **設定** > **一般** > **Web**.
1. 変更： _設定スコープ_ に `german` web サイト。
1. を展開 **ベース URL** 「」セクションを選択して「」を更新 **ベース URL** および **ベースリンク URL** value to `http://german.magento24.com/`.
1. を展開 **ベース URL （セキュア）** 「」セクションを選択して「」を更新 **セキュアなベース URL** および **セキュアベースリンク URL** value to `https://german.magento24.com/`.
1. クリック **設定を保存** 設定変更を保存します。

### キャッシュのクリーンアップ

次のコマンドを実行して、 `config` および `full_page` キャッシュ。

```bash
bin/magento cache:clean config full_page
```

## サイトの検証

ストアの URL に対して DNS を設定していない限り、のホストへの静的ルートを追加する必要があります `hosts` ファイル：

1. オペレーティングシステムの場所 `hosts` ファイル。
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
>- クラウドインフラストラクチャにAdobe Commerceを設定するには、さらに作業が必要です。詳しくは、以下を参照してください [複数のクラウド web サイトまたはストアを設定する](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) が含まれる _クラウドインフラストラクチャー上のCommerce ガイド_.

### トラブルシューティング

- フランス語およびドイツ語のサイトが 404 を返したが、管理者が読み込まれる場合は、完了していることを確認します [手順 6：ベース URL へのストアコードの追加](ms-admin.md#step-6-add-the-store-code-to-the-base-url).
- すべての URL が 404 を返す場合は、web サーバーを再起動していることを確認します。
- 管理者が正しく機能しない場合は、仮想ホストを正しく設定していることを確認してください。
