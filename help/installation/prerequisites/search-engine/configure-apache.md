---
title: 検索エンジン用に Apache を設定する
description: Adobe Commerceのオンプレミスインストール用に Apache web サーバーで検索エンジンを設定するには、次の手順に従います。
feature: Install, Search
exl-id: b35c95a7-0c00-48e5-b37d-7c9e17feebec
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 0%

---

# 検索エンジン用に Apache を設定する

{{$include /help/_includes/web-server-communication.md}}

## プロキシの設定

>[!NOTE]
>
>OpenSearch のサポートは 2.4.4 で追加されました。OpenSearch は、互換性のあるElasticsearchのフォークです。 参照： [Elasticsearchを OpenSearch に移行する](../../../upgrade/prepare/opensearch-migration.md) を参照してください。

この節では、Apache をとして設定する方法について説明します *安全でない* Adobe Commerceがこのサーバーで実行中の検索エンジンを使用できるように、プロキシを設定します。 この項では、HTTP 基本認証の設定については説明しません。詳細は、を参照してください。 [Apache との安全な通信](#secure-communication-with-apache).

>[!NOTE]
>
>この例ではプロキシが保護されていない理由は、設定と検証が容易だからです。 このプロキシでは TLS を使用できます。 これを行う場合は、必ずプロキシ情報を安全な仮想ホスト設定に追加してください。

### Apache 2.4 用のプロキシの設定

この節では、仮想ホストを使用してプロキシを設定する方法について説明します。

1. Enable （有効） `mod_proxy` 次のように設定します。

   ```bash
   a2enmod proxy_http
   ```

1. テキストエディターを使用して開く `/etc/apache2/sites-available/000-default.conf`
1. ファイルの先頭に次のディレクティブを追加します。

   ```conf
   Listen 8080
   ```

1. ファイルの下部に次を追加します。

   ```conf
   <VirtualHost *:8080>
       ProxyPass "/" "http://localhost:9200/"
       ProxyPassReverse "/" "http://localhost:9200/"
   </VirtualHost>
   ```

1. Apache を再起動します。

   ```bash
   service apache2 restart
   ```

1. 次のコマンドを入力して、プロキシが機能することを確認します。

   ```bash
   curl -i http://localhost:<proxy port>/_cluster/health
   ```

   例えば、プロキシを使用していて、Elasticsearchがポート 8080 を使用している場合、次のようになります。

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

## Apache との安全な通信

ここでは、を使用して、Apache と検索エンジン間の通信を保護する方法について説明します [HTTP ベーシック](https://datatracker.ietf.org/doc/html/rfc2617) apache での認証。 その他のオプションについては、次のいずれかのリソースを参照してください。

* [Apache 2.4 認証および承認に関するチュートリアル](https://httpd.apache.org/docs/2.4/howto/auth.html)

以下のセクションの 1 つを参照してください。

* [パスワードファイルの作成](#create-a-password)
* [セキュアな仮想ホストの設定](#secure-communication-with-apache)

### パスワードの作成

セキュリティ上の理由から、web サーバーの docroot を除く任意の場所にパスワードファイルを配置できます。 この例では、パスワードファイルを新しいディレクトリに保存する方法を示します。

#### 必要に応じて htpasswd をインストールします。

まず、Apache があるかどうかを確認します `htpasswd` ユーティリティは次のようにインストールされます。

1. 次のコマンドを入力して、 `htpasswd` はすでにインストールされています：

   ```bash
   which htpasswd
   ```

   パスが表示される場合は、インストールされます。コマンドが出力を返さない場合は、 `htpasswd` はインストールされていません。

1. 必要に応じて、 `htpasswd`:

   * Ubuntu: `apt-get -y install apache2-utils`
   * CentOS: `yum -y install httpd-tools`

#### パスワードファイルの作成

を使用して、ユーザーとして次のコマンドを入力します `root` 権限：

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.<password file name> <username>
```

ここで、

* `<username>` 次になることができます。

   * Cron の設定：web サーバーユーザーまたは別のユーザー。

  この例では web サーバーユーザーを使用しますが、ユーザーの選択はユーザー次第です。

   * Elasticsearchの設定：ユーザーの名前 `magento_elasticsearch` この例では、

* `<password file name>` は非表示のファイルである必要があります（で始まります） `.`）に設定し、ユーザー名を反映させる必要があります。 詳しくは、この節の後半の例を参照してください。

画面の指示に従って、ユーザーのパスワードを作成します。

#### 例

**例 1:cron**
cron 用に 1 人のユーザーの認証のみを設定する必要があります。この例では、web サーバーユーザーを使用します。 Web サーバーユーザーのパスワードファイルを作成するには、次のコマンドを入力します。

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.htpasswd apache
```

**例 2:Elasticsearch**
2 人のユーザーに対してElasticsearchを設定する必要があります。1 人は nginx にアクセスでき、もう 1 人は認証にアクセスできます。 これらのユーザーのパスワードファイルを作成するには、次のコマンドを入力します。

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.htpasswd_elasticsearch magento_elasticsearch
```

#### ユーザーを追加

パスワードファイルに別のユーザーを追加するには、ユーザーとして次のコマンドを入力します。 `root` 権限：

```bash
htpasswd /usr/local/apache/password/.htpasswd <username>
```

### Apache との安全な通信

この節では、の設定方法について説明します [HTTP 基本認証](https://httpd.apache.org/docs/2.2/howto/auth.html). TLS と HTTP 基本認証を一緒に使用すると、Elasticsearchや OpenSearch、またはアプリケーションサーバーとの通信がインターセプトされるのを防ぐことができます。

ここでは、Apache サーバーにアクセスできるユーザーを指定する方法について説明します。

1. テキストエディターを使用して、次の内容を安全な仮想ホストに追加します。

   * Apache 2.4：編集 `/etc/apache2/sites-available/default-ssl.conf`

   ```conf
   <Proxy *>
       Order deny,allow
       Allow from all
   
       AuthType Basic
       AuthName "Elasticsearch Server" # or OpenSearch Server
       AuthBasicProvider file
       AuthUserFile /usr/local/apache/password/.htpasswd_elasticsearch
       Require valid-user
   
     # This allows OPTIONS-requests without authorization
     <LimitExcept OPTIONS>
           Require valid-user
     </LimitExcept>
   </Proxy>
   ```

1. 上記のを安全な仮想ホストに追加した場合は、 `Listen 8080` および `<VirtualHost *:8080>` 安全でない仮想ホストに以前に追加したディレクティブ。

1. 変更を保存し、テキストエディターを終了して、Apache を再起動します。

   * CentOS: `service httpd restart`
   * Ubuntu: `service apache2 restart`

#### 検証

{{$include /help/_includes/verify-secure-communication.md}}
