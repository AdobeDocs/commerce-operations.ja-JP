---
title: 検索エンジン用のApacheの設定
description: Adobe Commerceのオンプレミスインストール用にApache web サーバーを使用して検索エンジンを設定するには、次の手順に従います。
feature: Install, Search
exl-id: b35c95a7-0c00-48e5-b37d-7c9e17feebec
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 0%

---

# 検索エンジン用のApacheの設定

{{$include /help/_includes/web-server-communication.md}}

## プロキシの設定

>[!NOTE]
>
>OpenSearchのサポートは2.4.4で追加されました。 OpenSearchはElasticsearchの互換性のあるフォークです。 詳しくは、[ElasticsearchをOpenSearchに移行](../../../upgrade/prepare/opensearch-migration.md)を参照してください。

この節では、Adobe Commerceがこのサーバーで実行されている検索エンジンを使用できるように、*unsecure* プロキシとしてApacheを設定する方法について説明します。 この節では、HTTP Basic認証の設定については説明しません。詳しくは、[Apacheとの通信の保護](#secure-communication-with-apache)を参照してください。

>[!NOTE]
>
>この例でプロキシが保護されていない理由は、設定と検証が簡単だからです。 このプロキシでTLSを使用できます。 これを行う場合は、プロキシ情報をセキュアな仮想ホスト設定に追加してください。

### Apache 2.4のプロキシの設定

この節では、仮想ホストを使用してプロキシを設定する方法について説明します。

1. 次のように`mod_proxy`を有効にします。

   ```shell
   a2enmod proxy_http
   ```

1. テキストエディターを使用して`/etc/apache2/sites-available/000-default.conf`を開く
1. ファイルの上部に次のディレクティブを追加します。

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

1. Apacheを再起動します。

   ```shell
   service apache2 restart
   ```

1. 次のコマンドを入力して、プロキシが機能することを確認します。

   ```shell
   curl -i http://localhost:<proxy port>/_cluster/health
   ```

   例えば、Elasticsearchを使用しており、プロキシでポート 8080を使用している場合は次のようになります。

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

## Apacheとの安全な通信

この節では、[HTTP Basic](https://datatracker.ietf.org/doc/html/rfc2617)認証とApacheを使用してApacheと検索エンジン間の通信を保護する方法について説明します。 その他のオプションについては、次のいずれかのリソースを参照してください。

* [Apache 2.4認証と認証のチュートリアル](https://httpd.apache.org/docs/2.4/howto/auth.html)

次のいずれかのセクションを参照してください。

* [パスワードファイルの作成](#create-a-password)
* [セキュアな仮想ホストの設定](#secure-communication-with-apache)

### パスワードの作成

セキュリティ上の理由から、Web サーバーのdocroot以外の場所にパスワードファイルを配置できます。 この例では、パスワードファイルを新しいディレクトリに保存する方法を示します。

#### 必要に応じてhtpasswdをインストールします

まず、次のようにApache `htpasswd` ユーティリティがインストールされているかどうかを確認します。

1. 次のコマンドを入力して、`htpasswd`が既にインストールされているかどうかを確認します。

   ```shell
   which htpasswd
   ```

   パスが表示された場合はインストールされます。コマンドが出力を返さない場合は、`htpasswd`はインストールされません。

1. 必要に応じて、`htpasswd`をインストールします。

   * Ubuntu: `apt-get -y install apache2-utils`
   * CentOS: `yum -y install httpd-tools`

#### パスワードファイルの作成

`root`権限を持つユーザーとして次のコマンドを入力します。

```shell
mkdir -p /usr/local/apache/password
```

```shell
htpasswd -c /usr/local/apache/password/.<password file name> <username>
```

どこで

* `<username>`は次の値を指定できます。

   * cronの設定：web サーバーユーザーまたは別のユーザー。

  この例では、web サーバーユーザーを使用していますが、ユーザーの選択はユーザーによって異なります。

   * Elasticsearchの設定：この例では、ユーザー名は`magento_elasticsearch`です

* `<password file name>`は非表示ファイル（`.`で始まる）である必要があり、ユーザーの名前を反映する必要があります。 詳しくは、この節の後の例を参照してください。

画面の指示に従って、ユーザーのパスワードを作成します。

#### 例

**例1: cron**
cronの認証は1人のユーザーに対してのみ設定する必要があります。この例では、web サーバーユーザーを使用します。 Web サーバーユーザーのパスワードファイルを作成するには、次のコマンドを入力します。

```shell
mkdir -p /usr/local/apache/password
```

```shell
htpasswd -c /usr/local/apache/password/.htpasswd apache
```

**例2: Elasticsearch**
nginxへのアクセス権を持つユーザーとElasticsearchへのアクセス権を持つユーザーの2人の認証を設定する必要があります。 これらのユーザーのパスワードファイルを作成するには、次のコマンドを入力します。

```shell
mkdir -p /usr/local/apache/password
```

```shell
htpasswd -c /usr/local/apache/password/.htpasswd_elasticsearch magento_elasticsearch
```

#### 追加ユーザーの追加

パスワードファイルに別のユーザーを追加するには、`root`権限を持つユーザーとして次のコマンドを入力します。

```shell
htpasswd /usr/local/apache/password/.htpasswd <username>
```

### Apacheとの安全な通信

この節では、[HTTP Basic認証](https://httpd.apache.org/docs/2.2/howto/auth.html)を設定する方法について説明します。 TLS認証とHTTP Basic認証を一緒に使用すると、ElasticsearchやOpenSearch、またはアプリケーションサーバーとの通信を誰もが傍受できなくなります。

この節では、Apache サーバーにアクセスできるユーザーを指定する方法について説明します。

1. テキストエディターを使用して、セキュアな仮想ホストに次のコンテンツを追加します。

   * Apache 2.4: `/etc/apache2/sites-available/default-ssl.conf`を編集

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

1. 前のディレクティブをセキュアな仮想ホストに追加した場合は、`Listen 8080`と前にセキュアでない仮想ホストに追加した`<VirtualHost *:8080>` ディレクティブを削除します。

1. 変更を保存し、テキストエディターを終了して、Apacheを再起動します。

   * CentOS: `service httpd restart`
   * Ubuntu: `service apache2 restart`

#### 検証

{{$include /help/_includes/verify-secure-communication.md}}

<!-- Last updated from includes: 2024-07-18 15:50:54 -->
