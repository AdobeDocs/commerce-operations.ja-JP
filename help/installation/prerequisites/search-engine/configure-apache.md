---
title: 検索エンジン用に Apache を設定
description: Apache Web サーバーと共に検索エンジンを設定し、Adobe CommerceとMagento Open Sourceのオンプレミスインストールを行うには、次の手順に従います。
source-git-commit: d3cfd97450164d38fd340b538099739601573d64
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 0%

---


# 検索エンジン用に Apache を設定

{{$include /help/_includes/web-server-communication.md}}

## プロキシの設定

>[!NOTE]
>
>2.4.4 で OpenSearch のサポートが追加されました。OpenSearch は互換性のあるElasticsearchの分岐です。 詳しくは、 [Elasticsearchを OpenSearch に移行](../../../upgrade/prepare/opensearch-migration.md) を参照してください。

この節では、Apache を *安全でない* プロキシを使用して、Adobe Commerceがこのサーバーで実行されている検索エンジンを使用できるようにします。 この節では、HTTP 基本認証の設定については説明しません。これについては、 [Apache との安全な通信](#secure-communication-with-apache).

>[!NOTE]
>
>この例でプロキシが保護されていないのは、設定と検証がより簡単になるからです。 このプロキシで TLS を使用できます。 これをおこなう場合は、プロキシ情報をセキュリティで保護された仮想ホスト設定に追加する必要があります。

### Apache 2.4 のプロキシの設定

このセクションでは、仮想ホストを使用してプロキシを設定する方法について説明します。

1. 有効にする `mod_proxy` 次のように指定します。

   ```bash
   a2enmod proxy_http
   ```

1. テキストエディターを使用してを開きます。 `/etc/apache2/sites-available/000-default.conf`
1. ファイルの先頭に次のディレクティブを追加します。

   ```conf
   Listen 8080
   ```

1. ファイルの下部に以下を追加します。

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

   例えば、Elasticsearchを使用し、プロキシでポート 8080 を使用する場合は、次のようになります。

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

## Apache との安全な通信

この節では、を使用して Apache と検索エンジン間の通信を保護する方法について説明します。 [HTTP Basic](https://datatracker.ietf.org/doc/html/rfc2617) 認証を Apache でおこないます。 その他のオプションについては、次のリソースのいずれかを参照してください。

* [Apache 2.4 の認証と承認に関するチュートリアル](https://httpd.apache.org/docs/2.4/howto/auth.html)

次のセクションのいずれかを参照してください。

* [パスワードファイルの作成](#create-a-password)
* [セキュアな仮想ホストを設定する](#secure-communication-with-apache)

### パスワードの作成

セキュリティ上の理由から、Web サーバーの docroot 以外の場所でも、パスワードファイルを見つけることができます。 この例では、パスワードファイルを新しいディレクトリに保存する方法を示します。

#### 必要に応じて htpasswd をインストールします。

まず、Apache を使用しているかどうかを確認します。 `htpasswd` ユーティリティは、次のようにインストールされます。

1. 次のコマンドを入力して、 `htpasswd` は既にインストールされています：

   ```bash
   which htpasswd
   ```

   パスが表示される場合は、そのパスがインストールされます。コマンドが出力を返さない場合、 `htpasswd` がインストールされていません。

1. 必要に応じて、をインストールします。 `htpasswd`:

   * Ubuntu: `apt-get -y install apache2-utils`
   * CentOS: `yum -y install httpd-tools`

#### パスワードファイルの作成

を使用して、次のコマンドをユーザーとして入力します。 `root` 権限：

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.<password file name> <username>
```

ここで、

* `<username>` は次のいずれかになります。

   * cron の設定：web サーバーユーザーまたは別のユーザー。

   この例では、Web サーバーユーザーを使用しますが、ユーザーの選択はユーザー次第です。

   * Elasticsearch:ユーザーの名前は `magento_elasticsearch` この例では


* `<password file name>` は、非表示のファイル ( `.`) およびには、ユーザーの名前が反映されている必要があります。 詳しくは、この節の後の例を参照してください。

画面の指示に従って、ユーザーのパスワードを作成します。

#### 例

**例 1:cron**
cron の認証は 1 人のユーザーに対してのみ設定する必要があります。この例では、web サーバーユーザーを使用します。 Web サーバーユーザーのパスワードファイルを作成するには、次のコマンドを入力します。

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.htpasswd apache
```

**例 2:Elasticsearch**
次の 2 人のユーザーに対して認証を設定する必要があります。1 つは nginx へのアクセス権を持ち、もう 1 つはElasticsearchへのアクセス権を持ちます。 これらのユーザーのパスワードファイルを作成するには、次のコマンドを入力します。

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.htpasswd_elasticsearch magento_elasticsearch
```

#### ユーザーの追加

別のユーザーをパスワードファイルに追加するには、次のコマンドを `root` 権限：

```bash
htpasswd /usr/local/apache/password/.htpasswd <username>
```

### Apache との安全な通信

このセクションでは、 [HTTP 基本認証](https://httpd.apache.org/docs/2.2/howto/auth.html). TLS と HTTP Basic 認証を併用すると、Elasticsearch、OpenSearch、またはお使いのアプリケーションサーバーとの通信が傍受されるのを防ぐことができます。

この節では、Apache サーバーにアクセスできるユーザーを指定する方法について説明します。

1. テキストエディターを使用して、セキュリティで保護された仮想ホストに次のコンテンツを追加します。

   * Apache 2.4:編集 `/etc/apache2/sites-available/default-ssl.conf`

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

1. セキュリティで保護された仮想ホストに前述のを追加した場合は、を削除します。 `Listen 8080` そして `<VirtualHost *:8080>` セキュリティで保護されていない仮想ホストに前に追加したディレクティブ。

1. 変更を保存し、テキストエディターを終了して、Apache を再起動します。

   * CentOS: `service httpd restart`
   * Ubuntu: `service apache2 restart`

#### 検証

{{$include /help/_includes/verify-secure-communication.md}}
