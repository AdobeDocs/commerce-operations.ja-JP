---
title: Nginxで複数のweb サイトを設定する
description: このチュートリアルに従って、Nginxで複数のweb サイトを設定します。
exl-id: f13926a2-182c-4ce2-b091-19c5f978f267
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '972'
ht-degree: 0%

---

# Nginxで複数のweb サイトを設定する

私たちは、次のことを想定しています。

- 開発用マシン（ラップトップ、仮想マシンなど）で作業している。

  ホスト環境に複数のweb サイトをデプロイするには、追加のタスクが必要になる場合があります。詳しくは、ホスティングプロバイダーを確認してください。

  クラウドインフラストラクチャでAdobe Commerceを設定するには、追加のタスクが必要です。 このトピックで説明したタスクを完了したら、_Commerce on Cloud Infrastructure ガイド_&#x200B;の「[複数のweb サイトまたはストアを設定する](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html)」を参照してください。

- 1つの仮想ホストファイルで複数のドメインを受け入れるか、web サイトごとに1つの仮想ホストを使用します。仮想ホスト設定ファイルは`/etc/nginx/sites-available`にあります。
- Commerceが提供する`nginx.conf.sample`を、このチュートリアルで説明した変更のみを使用します。
- Commerce ソフトウェアが`/var/www/html/magento2`にインストールされています。
- デフォルト以外に2つのWeb サイトがあります。

   - `french.mysite.mg` （web サイト コード `french`およびストアビューコード `fr`）
   - `german.mysite.mg` （web サイト コード `german`およびストアビューコード `de`）
   - `mysite.mg`は既定のweb サイトと既定のストアビューです

>[!TIP]
>
>これらの値を見つける方法については、[Web サイトの作成](ms-admin.md#step-2-create-websites)および[ ストアビューの作成](ms-admin.md#step-4-create-store-views)を参照してください。

以下は、nginxを使用して複数のweb サイトを設定するためのロードマップです。

1. [管理画面でweb サイト、ストア、ストアビューを設定](ms-admin.md)。
1. [Nginx バーチャルホスト ](#step-2-create-nginx-virtual-hosts)を作成して、多数のWeb サイトまたは1つのNginx バーチャルホストをCommerce web サイトごとにマッピングします（以下の手順を参照）。
1. Magentoが提供する`nginx.conf.sample`を使用して、[MAGE変数](ms-overview.md) `$MAGE_RUN_TYPE`および`$MAGE_RUN_CODE`の値をnginxに渡します（以下で説明する手順）。

   - `$MAGE_RUN_TYPE`は`store`または`website`のいずれかです：

      - `website`を使用して、ストアフロントにweb サイトを読み込みます。
      - `store`を使用して、ストアフロントの任意のストアビューを読み込みます。

   - `$MAGE_RUN_CODE`は、`$MAGE_RUN_TYPE`に対応する一意のweb サイトまたはストアビューコードです。

1. Commerce管理者のBase URL設定を更新します。

## 手順1：管理画面でweb サイト、ストアビュー、ストアビューを作成する

[管理者](ms-admin.md)で複数のweb サイト、ストア、ストアビューを設定するを参照してください。

## 手順2:nginx仮想ホストの作成

このステップでは、ストアフロントにweb サイトを読み込む方法について説明します。 Web サイトまたはストアビューのいずれかを使用できます。ストアビューを使用する場合は、それに応じてパラメーター値を調整する必要があります。 このセクションのタスクは、`sudo`権限を持つユーザーとして完了する必要があります。

1つの[nginx仮想ホストファイル ](#step-2-create-nginx-virtual-hosts)のみを使用することで、nginx設定をシンプルかつクリーンに保つことができます。 複数の仮想ホストファイルを使用すると、各ストアをカスタマイズできます（例えば、`french.mysite.mg`のカスタム場所を使用する）。

**1つの仮想ホストを作成するには** （簡略化）:

この設定は、[nginx設定](../../installation/prerequisites/web-server/nginx.md)に拡張されます。

1. テキストエディターを開き、次の内容を`/etc/nginx/sites-available/magento`という名前の新しいファイルに追加します。

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

1. ファイルに変更を保存し、テキストエディターを終了します。
1. サーバー設定を確認します。

   ```shell
   nginx -t
   ```

1. 成功すると、次のメッセージが表示されます。

   ```yaml
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   エラーが表示される場合は、仮想ホスト設定ファイルの構文を確認します。

1. `/etc/nginx/sites-enabled` ディレクトリにシンボリックリンクを作成します。

   ```shell
   cd /etc/nginx/sites-enabled
   ```

   ```shell
   ln -s /etc/nginx/sites-available/magento magento
   ```

マップディレクティブについて詳しくは、マップディレクティブ ](http://nginx.org/en/docs/http/ngx_http_map_module.html#map)の[nginx ドキュメントを参照してください。


**複数の仮想ホストを作成するには**:

1. テキストエディターを開き、次の内容を`/etc/nginx/sites-available/french.mysite.mg`という名前の新しいファイルに追加します。

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

1. 同じディレクトリに次の内容を持つ`german.mysite.mg`という名前の別のファイルを作成します。

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

1. ファイルに変更を保存し、テキストエディターを終了します。
1. サーバー設定を確認します。

   ```shell
   nginx -t
   ```

1. 成功すると、次のメッセージが表示されます。

   ```yaml
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   エラーが表示される場合は、仮想ホスト設定ファイルの構文を確認します。

1. `/etc/nginx/sites-enabled` ディレクトリにシンボリックリンクを作成します。

   ```shell
   cd /etc/nginx/sites-enabled
   ```

   ```shell
   ln -s /etc/nginx/sites-available/french.mysite.mg french.mysite.mg
   ```

   ```shell
   ln -s /etc/nginx/sites-available/german.mysite.mg german.mysite.mg
   ```

## 手順3:nginx.conf.sampleの変更

>[!TIP]
>
>`nginx.conf.sample` ファイルは編集しないでください。新しいリリースのたびに更新されるコア Commerce ファイルです。 代わりに、`nginx.conf.sample` ファイルをコピーし、名前を変更してから、コピーしたファイルを編集します。

**メインアプリケーションのPHP エントリポイントを編集するには**:

`nginx.conf.sample` ファイルを変更するには、**の手順を実行します。

1. テキストエディターを開き、`nginx.conf.sample` ファイル、`<magento2_installation_directory>/nginx.conf.sample`を確認します。 次のセクションを探します。

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

1. include ステートメントの前に、次の2行で`nginx.conf.sample` ファイルを更新します。

   ```conf
   fastcgi_param MAGE_RUN_TYPE $MAGE_RUN_TYPE;
   fastcgi_param MAGE_RUN_CODE $MAGE_RUN_CODE;
   ```

メインアプリケーションの更新されたPHP エントリポイントの例は次のようになります。

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

## 手順4：基本URL設定の更新

Commerce管理者の`french`および`german` Web サイトのベース URLを更新する必要があります。

### フランス語Web サイトのベース URLを更新

1. Commerce管理者にログインし、**Stores** > **Settings** > **Configuration** > **General** > **Web**&#x200B;に移動します。
1. _構成範囲_&#x200B;を`french` web サイトに変更します。
1. **Base URL** セクションを展開し、**Base URL**&#x200B;と&#x200B;**Base Link URL**&#x200B;の値を`http://french.magento24.com/`に更新します。
1. **Base URL （Secure）** セクションを展開し、**Secure Base URL**&#x200B;と&#x200B;**Secure Base Link URL**&#x200B;の値を`https://french.magento24.com/`に更新します。
1. 「**設定を保存**」をクリックし、設定の変更を保存します。

### ドイツ語Web サイトのベース URLを更新

1. Commerce管理者にログインし、**Stores** > **Settings** > **Configuration** > **General** > **Web**&#x200B;に移動します。
1. _構成範囲_&#x200B;を`german` web サイトに変更します。
1. **Base URL** セクションを展開し、**Base URL**&#x200B;と&#x200B;**Base Link URL**&#x200B;の値を`http://german.magento24.com/`に更新します。
1. **Base URL （Secure）** セクションを展開し、**Secure Base URL**&#x200B;と&#x200B;**Secure Base Link URL**&#x200B;の値を`https://german.magento24.com/`に更新します。
1. 「**設定を保存**」をクリックし、設定の変更を保存します。

### キャッシュのクリーニング

次のコマンドを実行して、`config`および`full_page` キャッシュをクリーンアップします。

```shell
bin/magento cache:clean config full_page
```

## サイトの確認

ストアのURLにDNSを設定していない限り、`hosts` ファイルのホストに静的ルートを追加する必要があります。

1. オペレーティング システム `hosts` ファイルを探します。
1. 静的ルートを次の形式で追加します。

   ```conf
   <ip-address> french.mysite.mg
   <ip-address> german.mysite.mg
   ```

1. ブラウザーで次のいずれかのURLに移動します。

   ```http
   http://mysite.mg/admin
   http://french.mysite.mg/frenchstoreview
   http://german.mysite.mg/germanstoreview
   ```

>[!INFO]
>
>- ホスト環境に複数のweb サイトをデプロイするには、追加のタスクが必要になる場合があります。詳しくは、ホスティングプロバイダーを確認してください。
>- クラウドインフラストラクチャ上にAdobe Commerceを設定するには、追加のタスクが必要です。_クラウドインフラストラクチャ上のCommerce ガイド_&#x200B;の[複数のクラウドウェブサイトまたはストアの設定](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html)を参照してください。

### トラブルシューティング

- フランス語とドイツ語のサイトで404が返され、管理者が読み込まれる場合は、[手順6: ストア コードをベース URLに追加](ms-admin.md#step-6-add-the-store-code-to-the-base-url)してください。
- すべてのURLが404を返す場合は、必ずweb サーバーを再起動してください。
- 管理者が正しく機能しない場合は、仮想ホストを適切に設定してください。
