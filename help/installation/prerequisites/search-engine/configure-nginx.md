---
title: 検索エンジン用にNginxを設定する
description: 次の手順に従って、Adobe Commerceのオンプレミスインストール用にNginx web サーバーを使用して検索エンジンを設定します。
feature: Install, Search
exl-id: 8d2f8695-e30a-4acc-bba3-d122212b0a53
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%

---

# 検索エンジン用にNginxを設定する

{{$include /help/_includes/web-server-communication.md}}

## プロキシの設定

>[!NOTE]
>
>OpenSearchのサポートは2.4.4で追加されました。 OpenSearchはElasticsearchの互換性のあるフォークです。 詳しくは、[ElasticsearchをOpenSearchに移行](../../../upgrade/prepare/opensearch-migration.md)を参照してください。

この節では、Adobe Commerceがこのサーバーで実行されている検索エンジンを使用できるように、*unsecure* プロキシとしてnginxを設定する方法について説明します。 この節では、HTTP Basic認証の設定については説明しません。これは、[nginxとの通信の保護](#secure-communication-with-nginx)で説明しています。

>[!NOTE]
>
>この例でプロキシが保護されていない理由は、設定と検証が簡単だからです。 必要に応じて、このプロキシでTLSを使用できます。これを行うには、プロキシ情報をセキュアサーバーブロック設定に追加します。

### グローバル設定で追加の設定ファイルを指定します

グローバル `/etc/nginx/nginx.conf`に次の行が含まれていることを確認して、次の節で説明する他の設定ファイルを読み込みます。

```conf
include /etc/nginx/conf.d/*.conf;
```

### nginxをプロキシとして設定する

この節では、nginx サーバーにアクセスできるユーザーを指定する方法について説明します。

1. テキストエディターを使用して、次の内容を含むファイル `/etc/nginx/conf.d/magento_es_auth.conf`を作成します。

   ```conf
   server {
      listen 8080;
      location /_cluster/health {
         proxy_pass http://localhost:9200/_cluster/health;
      }
   }
   ```

1. nginxを再起動します。

   ```shell
   service nginx restart
   ```

1. 次のコマンドを入力して、プロキシが機能することを確認します。

   ```shell
   curl -i http://localhost:<proxy port>/_cluster/health
   ```

   例えば、プロキシでポート 8080を使用している場合は、次のようになります。

   ```shell
   curl -i http://localhost:8080/_cluster/health
   ```

   成功を示す次の表示と同様のメッセージ：

   ```text
   HTTP/1.1 200 OK
   Date: Tue, 23 Feb 2019 20:38:03 GMT
   Content-Type: application/json; charset=UTF-8
   Content-Length: 389
   Connection: keep-alive
   
   {"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
   ```

## nginxとの安全なコミュニケーション

この節では、セキュアプロキシで[HTTP Basic認証](https://nginx.org/en/docs/http/ngx_http_auth_basic_module.html)を設定する方法について説明します。 TLS認証とHTTP Basic認証を一緒に使用すると、ElasticsearchやOpenSearch、またはアプリケーションサーバーとの通信を誰もが傍受できなくなります。

nginxはHTTP Basic認証をネイティブにサポートしているので、実稼動環境では推奨されていない[ ダイジェスト認証](https://www.nginx.com/resources/wiki/modules/auth_digest/)などの方法で認証することをお勧めします。

関連トピックス：

* [Ubuntu 14.04 （Digital Ocean）でNginxでパスワード認証を設定する方法](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-nginx-on-ubuntu-14-04)
* [Nginxによる基本的なHTTP認証（HowtoForge）](https://www.howtoforge.com/basic-http-authentication-with-nginx)
* [ElasticsearchのNginx設定の例](https://gist.github.com/karmi/b0a9b4c111ed3023a52d)

詳しくは、次の節を参照してください。

* [パスワードの作成](#create-a-password)
* [nginxへのアクセスを設定する](#set-up-access-to-nginx)
* [検索エンジンの制限付きコンテキストの設定](#set-up-a-restricted-context-for-the-search-engine)
* [通信が安全であることを確認します](#secure-communication-with-nginx)

### パスワードの作成

ElasticsearchまたはOpenSearchへのアクセス権を持つユーザー（この例では`magento_elasticsearch`という名前）のパスワードをエンコードするには、Apache `htpasswd` コマンドを使用することをお勧めします。

パスワードを作成するには：

1. 次のコマンドを入力して、`htpasswd`が既にインストールされているかどうかを確認します。

   ```shell
   which htpasswd
   ```

   パスが表示された場合はインストールされます。コマンドが出力を返さない場合は、`htpasswd`はインストールされません。

1. 必要に応じて、`htpasswd`をインストールします。

   * Ubuntu: `apt-get -y install apache2-utils`
   * CentOS: `yum -y install httpd-tools`

1. パスワードを保存する`/etc/nginx/passwd` ディレクトリを作成します。

   ```shell
   mkdir -p /etc/nginx/passwd
   ```

   ```shell
   htpasswd -c /etc/nginx/passwd/.<filename> <username>
   ```

   >[!WARNING]
   >
   >セキュリティ上の理由から、`<filename>`は非表示にする必要があります。つまり、期間で始める必要があります。

1. *（オプション）。* パスワードファイルに別のユーザーを追加するには、`-c` （作成）オプションを使用せずに同じコマンドを入力します。

   ```shell
   htpasswd /etc/nginx/passwd/.<filename> <username>
   ```

1. `/etc/nginx/passwd`の内容が正しいことを確認してください。

### nginxへのアクセスを設定する

この節では、nginx サーバーにアクセスできるユーザーを指定する方法について説明します。

>[!WARNING]
>
>この例は、*安全でない* プロキシを示しています。 セキュアプロキシを使用するには、セキュアサーバーブロックに次のコンテンツ（リッスポートを除く）を追加します。

テキストエディターを使用して、次の内容で`/etc/nginx/conf.d/magento_es_auth.conf` （安全でない）または安全なサーバーブロックを変更します。

```conf
server {
  listen 8080;
  server_name 127.0.0.1;

  location / {
   limit_except HEAD {
      auth_basic "Restricted";
      auth_basic_user_file  /etc/nginx/passwd/.htpasswd_magento_elasticsearch;
   }
   proxy_pass http://127.0.0.1:9200;
   proxy_redirect off;
   proxy_set_header Host $host;
   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
  }

  location /_aliases {
   auth_basic "Restricted";
   auth_basic_user_file  /etc/nginx/passwd/.htpasswd_magento_elasticsearch;
   proxy_pass http://127.0.0.1:9200;
   proxy_redirect off;
   proxy_set_header Host $host;
   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
  }

  include /etc/nginx/auth/*.conf;
}
```

>[!NOTE]
>
>前述の例で示した検索エンジンのリッスン ポートは、例としてのみ使用できます。 セキュリティ上の理由から、デフォルト以外のリッスン ポートを使用することをお勧めします。

### 検索エンジンの制限付きコンテキストの設定

この節では、検索エンジンサーバーにアクセスできるユーザーを指定する方法について説明します。

1. 次のコマンドを入力して、認証設定を保存するディレクトリを作成します。

   ```shell
   mkdir /etc/nginx/auth/
   ```

1. テキストエディターを使用して、次の内容を含むファイル `/etc/nginx/auth/magento_elasticsearch.conf`を作成します。

   ```conf
   location /elasticsearch {
   auth_basic "Restricted - elasticsearch";
   auth_basic_user_file /etc/nginx/passwd/.htpasswd_magento_elasticsearch;
   
   proxy_pass http://127.0.0.1:9200;
   proxy_redirect off;
   proxy_set_header Host $host;
   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
   }
   ```

1. 安全なプロキシを設定している場合は、`/etc/nginx/conf.d/magento_es_auth.conf`を削除します。
1. nginxを再起動し、次のセクションに進みます。

   ```shell
   service nginx restart
   ```

#### 検証

{{$include /help/_includes/verify-secure-communication.md}}

<!-- Last updated from includes: 2024-07-18 15:50:54 -->
