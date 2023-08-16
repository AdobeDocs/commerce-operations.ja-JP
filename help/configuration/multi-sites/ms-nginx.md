---
title: Nginx で複数の Web サイトを設定する
description: Nginx で複数の Web サイトを設定するには、このチュートリアルに従います。
exl-id: f13926a2-182c-4ce2-b091-19c5f978f267
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '959'
ht-degree: 0%

---

# Nginx で複数の Web サイトを設定する

我々は、以下を想定する。

- 開発マシン（ノート PC、仮想マシンなど）で作業している。

  ホスト環境で複数の Web サイトをデプロイする場合は、追加のタスクが必要になる場合があります。詳しくは、ホスティングプロバイダーにお問い合わせください。

  クラウドインフラストラクチャ上にAdobe Commerceを設定するには、追加のタスクが必要です。 このトピックで説明したタスクを完了した後、 [複数の Web サイトまたはストアを設定する](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) （内） _Commerce on Cloud Infrastructure ガイド_.

- 複数のドメインを 1 つの仮想ホストファイルで受け入れるか、Web サイトごとに 1 つの仮想ホストを使用します。仮想ホストの設定ファイルは、 `/etc/nginx/sites-available`.
- 次を使用します。 `nginx.conf.sample` Commerce で提供され、このチュートリアルで説明する変更のみが含まれます。
- Commerce ソフトウェアは、 `/var/www/html/magento2`.
- デフォルト以外の 2 つの Web サイトがあります。

   - `french.mysite.mg` Web サイトコード `french` およびビューコードをストア `fr`
   - `german.mysite.mg` Web サイトコード `german` およびビューコードをストア `de`
   - `mysite.mg` はデフォルトの Web サイトおよびデフォルトのストア表示です。

>[!TIP]
>
>参照： [Web サイトの作成](ms-admin.md#step-2-create-websites) および [ストア表示の作成](ms-admin.md#step-4-create-store-views) を参照してください。

nginx を使用した複数の Web サイトのセットアップロードマップを次に示します。

1. [Web サイト、ストア、ストアの表示を設定する](ms-admin.md) 」と入力します。
1. の作成 [Nginx 仮想ホスト](#step-2-create-nginx-virtual-hosts)) を使用して、多くの Web サイトまたは 1 つの Nginx 仮想ホストを Commerce Web サイトごとにマッピングします（以下の手順で詳しく説明します）。
1. の値を渡す [画像変数](ms-overview.md) `$MAGE_RUN_TYPE` および `$MAGE_RUN_CODE` Magento提供の `nginx.conf.sample` （以下で説明する手順）。

   - `$MAGE_RUN_TYPE` 次のいずれかを指定できます。 `store` または `website`:

      - 用途 `website` をクリックして、ストアフロントに web サイトを読み込みます。
      - 用途 `store` ストアのビューをストアフロントに読み込みます。

   - `$MAGE_RUN_CODE` は、 `$MAGE_RUN_TYPE`.

1. コマース管理でベース URL 設定を更新します。

## 手順 1:Web サイト、ストアを作成し、管理者にビューを保存する

詳しくは、 [複数の Web サイト、ストア、管理者での表示の設定](ms-admin.md).

## 手順 2:nginx 仮想ホストを作成する

この手順では、ストアフロントに Web サイトを読み込む方法について説明します。 Web サイトまたはストア表示を使用できます。ストア表示を使用する場合は、それに応じてパラメーター値を調整する必要があります。 この節のタスクは、 `sudo` 権限。

1 つだけを使用して [nginx 仮想ホストファイル](#step-2-create-nginx-virtual-hosts)を使用すると、nginx の設定をシンプルでクリーンな状態に保つことができます。 複数の仮想ホストファイルを使用すると、各ストアをカスタマイズできます ( `french.mysite.mg` 例えば )。

**1 つの仮想ホストを作成するには** （簡略化）:

この設定は、 [nginx 設定](../../installation/prerequisites/web-server/nginx.md).

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

1. 変更をファイルに保存し、テキストエディターを終了します。
1. サーバー設定を確認します。

   ```bash
   nginx -t
   ```

1. 成功すると、次のメッセージが表示されます。

   ```terminal
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   エラーが表示される場合は、仮想ホスト構成ファイルの構文を確認します。

1. でシンボリックリンクを作成します。 `/etc/nginx/sites-enabled` ディレクトリ：

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/magento magento
   ```

map ディレクティブの詳細については、 [map ディレクティブに関する nginx ドキュメント](http://nginx.org/en/docs/http/ngx_http_map_module.html#map).


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

1. という名前の別のファイルを作成します。 `german.mysite.mg` は、次の内容を含む同じディレクトリ内にあります。

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

1. 変更をファイルに保存し、テキストエディターを終了します。
1. サーバー設定を確認します。

   ```bash
   nginx -t
   ```

1. 成功すると、次のメッセージが表示されます。

   ```terminal
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   エラーが表示される場合は、仮想ホスト構成ファイルの構文を確認します。

1. シンボリックリンクを `/etc/nginx/sites-enabled` ディレクトリ：

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/french.mysite.mg french.mysite.mg
   ```

   ```bash
   ln -s /etc/nginx/sites-available/german.mysite.mg german.mysite.mg
   ```

## 手順 3: nginx.conf.sample を変更する

>[!TIP]
>
>次を編集しない： `nginx.conf.sample` ファイル。新しいリリースのたびに更新される可能性のあるコア Commerce ファイルです。 代わりに、 `nginx.conf.sample` ファイルの名前を変更し、コピーしたファイルを編集します。

**メインアプリケーションの PHP エントリポイントを編集するには**:

次の手順で `nginx.conf.sample` file**:

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

1. を更新します。 `nginx.conf.sample` ファイルの前に以下の 2 行を記述します。

   ```conf
   fastcgi_param MAGE_RUN_TYPE $MAGE_RUN_TYPE;
   fastcgi_param MAGE_RUN_CODE $MAGE_RUN_CODE;
   ```

更新された PHP エントリポイントの例を次に示します。

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

のベース URL を更新する必要があります。 `french` そして `german` Web サイトをコマース管理者に表示します。

### フランス語の Web サイトのベース URL を更新

1. コマース管理者にログインし、に移動します。 **ストア** > **設定** > **設定** > **一般** > **Web**.
1. 次を変更： _設定範囲_ から `french` web サイト。
1. 展開 **ベース URL** セクションを開き、 **ベース URL** および **ベースリンク URL** 値 `http://french.magento24.com/`.
1. 展開 **ベース URL （セキュア）** セクションを開き、 **セキュアベース URL** および **セキュアベースリンク URL** 値 `https://french.magento24.com/`.
1. クリック **設定を保存** 設定の変更を保存します。

### ドイツ語の Web サイトのベース URL を更新

1. コマース管理者にログインし、に移動します。 **ストア** > **設定** > **設定** > **一般** > **Web**.
1. 次を変更： _設定範囲_ から `german` web サイト。
1. 展開 **ベース URL** セクションを開き、 **ベース URL** および **ベースリンク URL** 値 `http://german.magento24.com/`.
1. 展開 **ベース URL （セキュア）** セクションを開き、 **セキュアベース URL** および **セキュアベースリンク URL** 値 `https://german.magento24.com/`.
1. クリック **設定を保存** 設定の変更を保存します。

### キャッシュのクリーンアップ

次のコマンドを実行して、 `config` および `full_page` キャッシュ。

```bash
bin/magento cache:clean config full_page
```

## サイトの検証

ストアの URL に対して DNS が設定されていない限り、 `hosts` ファイル：

1. オペレーティングシステムを見つける `hosts` ファイル。
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
>- ホスト環境で複数の Web サイトをデプロイする場合は、追加のタスクが必要になる場合があります。詳しくは、ホスティングプロバイダーにお問い合わせください。
>- クラウドインフラストラクチャ上にAdobe Commerceを設定するには、追加のタスクが必要です。詳しくは、 [複数のクラウド Web サイトまたはストアを設定する](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) （内） _Commerce on Cloud Infrastructure ガイド_.

### トラブルシューティング

- フランス語およびドイツ語のサイトが 404 秒を返すが、管理者が読み込まれる場合は、必ず [手順 6：ベース URL にストアコードを追加する](ms-admin.md#step-6-add-the-store-code-to-the-base-url).
- すべての URL が 404 秒を返す場合は、Web サーバーを再起動したことを確認してください。
- 管理者が正しく機能しない場合は、仮想ホストを正しく設定していることを確認してください。
