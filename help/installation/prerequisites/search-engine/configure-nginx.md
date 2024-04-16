---
title: 検索エンジン用の Nginx の設定
description: Adobe Commerceのオンプレミスインストール用に Nginx web サーバーで検索エンジンを設定するには、次の手順に従います。
feature: Install, Search
exl-id: 8d2f8695-e30a-4acc-bba3-d122212b0a53
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 0%

---

# 検索エンジン用の Nginx の設定

{{$include /help/_includes/web-server-communication.md}}

## プロキシの設定

>[!NOTE]
>
>OpenSearch のサポートは 2.4.4 で追加されました。OpenSearch は、互換性のあるElasticsearchのフォークです。 参照： [Elasticsearchを OpenSearch に移行する](../../../upgrade/prepare/opensearch-migration.md) を参照してください。

このセクションでは、nginx を *安全でない* Adobe Commerceがこのサーバーで実行中の検索エンジンを使用できるように、プロキシを設定します。 この項では、HTTP 基本認証の設定については説明しません。詳細は、を参照してください。 [nginx との安全な通信](#secure-communication-with-nginx).

>[!NOTE]
>
>この例ではプロキシが保護されていない理由は、設定と検証が容易だからです。 必要に応じて、このプロキシで TLS を使用できます。そのためには、プロキシ情報を安全なサーバーブロック設定に必ず追加してください。

### グローバル設定で追加の設定ファイルを指定します

グローバルな `/etc/nginx/nginx.conf` には次の行が含まれるので、以下の節で説明するその他の設定ファイルが読み込まれます。

```conf
include /etc/nginx/conf.d/*.conf;
```

### プロキシとしての nginx の設定

このセクションでは、nginx サーバにアクセスできるユーザを指定する方法について説明します。

1. テキストエディターを使用したファイルの作成 `/etc/nginx/conf.d/magento_es_auth.conf` 次の内容を含みます。

   ```conf
   server {
      listen 8080;
      location /_cluster/health {
         proxy_pass http://localhost:9200/_cluster/health;
      }
   }
   ```

1. nginx を再起動します。

   ```bash
   service nginx restart
   ```

1. 次のコマンドを入力して、プロキシが機能することを確認します。

   ```bash
   curl -i http://localhost:<proxy port>/_cluster/health
   ```

   例えば、プロキシでポート 8080 が使用されている場合は、次のようになります。

   ```bash
   curl -i http://localhost:8080/_cluster/health
   ```

   次のようなメッセージが成功を示して表示されます。

   ```terminal
   HTTP/1.1 200 OK
   Date: Tue, 23 Feb 2019 20:38:03 GMT
   Content-Type: application/json; charset=UTF-8
   Content-Length: 389
   Connection: keep-alive
   
   {"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
   ```

## nginx との安全な通信

この節では、の設定方法について説明します [HTTP 基本認証](https://nginx.org/en/docs/http/ngx_http_auth_basic_module.html) 安全なプロキシを使用します。 TLS と HTTP 基本認証を一緒に使用すると、Elasticsearchや OpenSearch、またはアプリケーションサーバーとの通信がインターセプトされるのを防ぐことができます。

Nginx は HTTP 基本認証をネイティブでサポートしているので、例えば次のような上書きを推奨します。 [ダイジェスト認証](https://www.nginx.com/resources/wiki/modules/auth_digest/)（実稼動環境では推奨されません）。

追加のリソース：

* [Ubuntu 14.04 （Digital Ocean）で Nginx を使用してパスワード認証を設定する方法](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-nginx-on-ubuntu-14-04)
* [Nginx を使った基本的な HTTP 認証（HowtoForge）](https://www.howtoforge.com/basic-http-authentication-with-nginx)
* [Elasticsearchのための Nginx 設定の例](https://gist.github.com/karmi/b0a9b4c111ed3023a52d)

詳しくは、次の節を参照してください。

* [パスワードの作成](#create-a-password)
* [nginx へのアクセスの設定](#set-up-access-to-nginx)
* [検索エンジンの制限付きコンテキストの設定](#set-up-a-restricted-context-for-the-search-engine)
* [通信がセキュリティで保護されていることを確認](#secure-communication-with-nginx)

### パスワードの作成

Apache を使用することをお勧めします `htpasswd` Elasticsearchまたは OpenSearch （という名前）にアクセスできるユーザーのパスワードをエンコードするコマンド `magento_elasticsearch` この例では）。

パスワードを作成するには：

1. 次のコマンドを入力して、 `htpasswd` はすでにインストールされています：

   ```bash
   which htpasswd
   ```

   パスが表示される場合は、インストールされます。コマンドが出力を返さない場合は、 `htpasswd` はインストールされていません。

1. 必要に応じて、 `htpasswd`:

   * Ubuntu: `apt-get -y install apache2-utils`
   * CentOS: `yum -y install httpd-tools`

1. を作成 `/etc/nginx/passwd` パスワードを保存するディレクトリ：

   ```bash
   mkdir -p /etc/nginx/passwd
   ```

   ```bash
   htpasswd -c /etc/nginx/passwd/.<filename> <username>
   ```

   >[!WARNING]
   >
   >セキュリティ上の理由から、 `<filename>` 非表示にする必要があります。つまり、ピリオドで始まる必要があります。

1. *（オプション）。* 別のユーザーをパスワードファイルに追加するには、同じコマンドを `-c` （作成）オプション：

   ```bash
   htpasswd /etc/nginx/passwd/.<filename> <username>
   ```

1. 内容を確認する `/etc/nginx/passwd` は正しいです。

### nginx へのアクセスの設定

このセクションでは、nginx サーバにアクセスできるユーザを指定する方法について説明します。

>[!WARNING]
>
>次に示す例はです。 *安全でない* プロキシ。 安全なプロキシを使用するには、次の内容（リッスンポートを除く）を安全なサーバーブロックに追加します。

テキストエディターを使用して、次のいずれかを変更します `/etc/nginx/conf.d/magento_es_auth.conf` （保護されていない）または次の内容を含む保護されたサーバーブロック：

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
>上記の例で示した検索エンジンのリッスンポートは、例にすぎません。 セキュリティ上の理由から、デフォルト以外のリッスンポートを使用することをお勧めします。

### 検索エンジンの制限付きコンテキストの設定

このセクションでは、検索エンジン サーバーにアクセスできるユーザーを指定する方法について説明します。

1. 次のコマンドを入力して、認証設定を格納するディレクトリを作成します。

   ```bash
   mkdir /etc/nginx/auth/
   ```

1. テキストエディターを使用したファイルの作成 `/etc/nginx/auth/magento_elasticsearch.conf` 次の内容を含みます。

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

1. 安全なプロキシを設定する場合は、次を削除します `/etc/nginx/conf.d/magento_es_auth.conf`.
1. nginx を再起動し、次のセクションに進みます。

   ```bash
   service nginx restart
   ```

#### 検証

{{$include /help/_includes/verify-secure-communication.md}}
