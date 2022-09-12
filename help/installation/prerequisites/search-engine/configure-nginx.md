---
title: 検索エンジン用に Nginx を設定する
description: Nginx Web サーバーを使用して検索エンジンを構成し、Adobe CommerceとMagento Open Sourceのオンプレミスインストールを行うには、次の手順に従います。
source-git-commit: a0f2c6480edcda5540ca83835580d18f401de72f
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 0%

---


# 検索エンジン用に Nginx を設定する

{{$include /help/_includes/web-server-communication.md}}

## プロキシの設定

>[!NOTE]
>
>2.4.4 で OpenSearch のサポートが追加されました。OpenSearch は互換性のあるElasticsearchの分岐です。 Elasticsearch7 を設定するすべての手順は、OpenSearch に適用されます。 詳しくは、 [Elasticsearchを OpenSearch に移行](../../../upgrade/prepare/opensearch-migration.md) を参照してください。

この節では、nginx を *安全でない* プロキシを使用して、Adobe CommerceまたはMagento Open Sourceがこのサーバーで実行している検索エンジンを使用できるようにします。 この節では、HTTP 基本認証の設定については説明しません。これについては、 [nginx との安全な通信](#secure-communication-with-nginx).

>[!NOTE]
>
>この例でプロキシが保護されていないのは、設定と検証がより簡単になるからです。 必要に応じて、このプロキシで TLS を使用できます。これをおこなうには、プロキシ情報をセキュリティで保護されたサーバーブロック設定に追加する必要があります。

### グローバル設定で追加の設定ファイルを指定する

グローバルな `/etc/nginx/nginx.conf` には次の行が含まれ、以降の節で説明するその他の設定ファイルが読み込まれます。

```conf
include /etc/nginx/conf.d/*.conf;
```

### プロキシとしての nginx の設定

このセクションでは、 [nginx](https://glossary.magento.com/nginx) サーバー。

1. テキストエディターを使用したファイルの作成 `/etc/nginx/conf.d/magento_es_auth.conf` を次の内容で指定します。

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

   例えば、プロキシでポート 8080 を使用する場合は、次のようになります。

   ```bash
   curl -i http://localhost:8080/_cluster/health
   ```

   成功を示す次の表示に類似したメッセージ：

   ```terminal
   HTTP/1.1 200 OK
   Date: Tue, 23 Feb 2019 20:38:03 GMT
   Content-Type: application/json; charset=UTF-8
   Content-Length: 389
   Connection: keep-alive
   
   {"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
   ```

## nginx との安全な通信

このセクションでは、 [HTTP 基本認証](https://nginx.org/en/docs/http/ngx_http_auth_basic_module.html) セキュリティで保護されたプロキシを使用します。 TLS と HTTP Basic 認証を併用すると、Elasticsearch、Adobe Commerce、Magento Open Sourceサーバーとの通信が傍受されるのを防ぐことができます。

Nginx は HTTP Basic 認証をネイティブにサポートしているので、例えば、HTTP Basic 認証をオーバーにすることをお勧めします。 [ダイジェスト認証](https://www.nginx.com/resources/wiki/modules/auth_digest/)：実稼動環境ではお勧めしません。

その他のリソース：

* [Ubuntu 14.04(Digital Ocean) で Nginx を使用したパスワード認証の設定方法](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-nginx-on-ubuntu-14-04)
* [Nginx を使用した基本的な HTTP 認証 (HowtoForge)](https://www.howtoforge.com/basic-http-authentication-with-nginx)
* [Elasticsearch用の Nginx 設定の例](https://gist.github.com/karmi/b0a9b4c111ed3023a52d)

詳しくは、次の節を参照してください。

* [パスワードの作成](#create-a-password)
* [nginx へのアクセスの設定](#set-up-access-to-nginx)
* [検索エンジンの制限付きコンテキストの設定](#set-up-a-restricted-context-for-the-search-engine)
* [通信が安全であることを確認します。](#secure-communication-with-nginx)

### パスワードの作成

Apache `htpasswd` Elasticsearchまたは OpenSearch ( `magento_elasticsearch` （この例では）。

パスワードを作成するには：

1. 次のコマンドを入力して、 `htpasswd` は既にインストールされています：

   ```bash
   which htpasswd
   ```

   パスが表示される場合は、そのパスがインストールされます。コマンドが出力を返さない場合、 `htpasswd` がインストールされていません。

1. 必要に応じて、をインストールします。 `htpasswd`:

   * Ubuntu: `apt-get -y install apache2-utils`
   * CentOS: `yum -y install httpd-tools`

1. の作成 `/etc/nginx/passwd` パスワードを保存するディレクトリ：

   ```bash
   mkdir -p /etc/nginx/passwd
   ```

   ```bash
   htpasswd -c /etc/nginx/passwd/.<filename> <username>
   ```

   >[!WARNING]
   >
   >セキュリティ上の理由から、 `<filename>` 隠すべきだつまり、ピリオドで始める必要があります。

1. *（オプション）。* 別のユーザーをパスワードファイルに追加するには、 `-c` （作成）オプション：

   ```bash
   htpasswd /etc/nginx/passwd/.<filename> <username>
   ```

1. のコンテンツを検証します。 `/etc/nginx/passwd` が正しい。

### nginx へのアクセスの設定

このセクションでは、nginx サーバにアクセスできるユーザーを指定する方法について説明します。

>[!WARNING]
>
>次に、 *安全でない* プロキシを使用します。 セキュアプロキシを使用するには、次のコンテンツ（リスンポートを除く）をセキュアサーバーブロックに追加します。

テキストエディターを使用して、次のいずれかを変更します。 `/etc/nginx/conf.d/magento_es_auth.conf` （セキュリティで保護されていない）、または以下の内容を含むセキュリティで保護されたサーバーブロック。

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
>前の例に示した検索エンジンのリスンポートは、例です。 セキュリティ上の理由から、デフォルト以外のリッスンポートを使用することをお勧めします。

### 検索エンジンの制限付きコンテキストの設定

このセクションでは、検索エンジンサーバーにアクセスできるユーザーを指定する方法について説明します。

1. 次のコマンドを入力して、認証設定を保存するディレクトリを作成します。

   ```bash
   mkdir /etc/nginx/auth/
   ```

1. テキストエディターを使用したファイルの作成 `/etc/nginx/auth/magento_elasticsearch.conf` を次の内容で指定します。

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

1. セキュアプロキシを設定した場合は、 `/etc/nginx/conf.d/magento_es_auth.conf`.
1. nginx を再起動し、次のセクションに進みます。

   ```bash
   service nginx restart
   ```

#### 検証

{{$include /help/_includes/verify-secure-communication.md}}
