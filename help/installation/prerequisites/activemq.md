---
title: メッセージブローカー（ActiveMQ Artemis）
description: Adobe Commerceのオンプレミス インストール用にApache ActiveMQ Artemis Message Brokerをインストールして設定するには、次の手順に従います。
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '936'
ht-degree: 0%

---

# メッセージブローカー（ActiveMQ Artemis）

Adobe Commerceは、Simple Text Oriented Messaging Protocol （STOMP）を通じて、ActiveMQ Artemis オープンソースのメッセージブローカーもサポートしています。 信頼性の高いスケーラブルなメッセージングシステムを提供し、STOMP ベースの統合に柔軟に対応できます。


>[!NOTE]
>
>ActiveMQ Artemisは、Adobe Commerce 2.4.5以降で導入されました。 クラウドインフラストラクチャプロジェクトにAdobe CommerceにActiveMQ Artemisをインストールする方法について詳しくは、「*Commerce on Cloud Guide*」の「[ActiveMQ サービスの設定](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/configure/service/activemq)」を参照してください。

メッセージキューは、メッセージの送信者と受信者が互いに接触しない非同期通信メカニズムを提供します。 また、メッセージキューと同時に通信する必要もありません。 送信者がメッセージをキューに入れると、受信者が受信するまで保存されます。

Adobe Commerceをインストールする前に、メッセージキューシステムを確立する必要があります。 基本的なシーケンスは次のとおりです。

1. Apache ActiveMQ Artemisと任意の前提条件をインストールします。
1. ActiveMQをAdobe Commerceに接続します。

>[!NOTE]
>
>メッセージキュー処理には、MySQL、ActiveMQ、または[!DNL RabbitMQ]を使用できます。 メッセージキューシステムの設定について詳しくは、[&#x200B; メッセージキューの概要](https://developer.adobe.com/commerce/php/development/components/message-queues/)を参照してください。 Adobe CommerceでBulk APIを使用している場合、メッセージキューシステム設定は、デフォルトで[!DNL RabbitMQ]をメッセージブローカーとして使用します。 詳しくは、[&#x200B; メッセージキューコンシューマー](../../configuration/cli/start-message-queues.md)の開始を参照してください。

>[!TIP]
>
>インストールする前に、常に[Apache ActiveMQ Artemis ダウンロードページ &#x200B;](https://activemq.apache.org/components/artemis/download/)で最新の安定バージョンを確認してください。 このドキュメントの例では、2025年9月の最新の安定リリースであるバージョン 2.42.0を使用しています。


## Apache ActiveMQ Artemisのインストール

ActiveMQ Artemisは、Docker （開発に推奨）または手動インストール（実稼動に推奨）のいずれかを使用してインストールできます。

### オプション 1: Dockerのインストール（開発に推奨）

#### 前提条件

Dockerがシステムにインストールされ、実行されていることを確認します。

>[!TIP]
>
>公式のActiveMQ Artemis Docker イメージについて詳しくは、[Apache ActiveMQ Artemis Docker Hub ページ &#x200B;](https://hub.docker.com/r/apache/activemq-artemis)を参照してください。

#### インストール手順

1. 公式のDocker イメージを使用してActiveMQ Artemisを実行します。

   ```shell
   # Run with default configuration
   docker run --detach \
     --name artemis \
     --publish 8161:8161 \
     --publish 61613:61613 \
     --publish 5672:5672 \
     apache/activemq-artemis:2.42.0
   ```

1. カスタム資格情報を使用して実行：

   ```shell
   # Run with custom username/password
   docker run --detach \
     --name artemis \
     --publish 8161:8161 \
     --publish 61613:61613 \
     --publish 5672:5672 \
     --env ARTEMIS_USER=magento \
     --env ARTEMIS_PASSWORD=magento \
     apache/activemq-artemis:2.42.0
   ```

#### Docker管理コマンド

```shell
# Check container status
docker ps | grep artemis

# View logs
docker logs artemis

# Stop the container
docker stop artemis

# Start the container
docker start artemis

# Remove the container
docker rm artemis
```

#### サービスへのアクセス

Docker コンテナが実行されたら、次にアクセスできます。

- **Web コンソール**: http://localhost:8161/console （デフォルトの資格情報：artemis/artemis）
- **STOMP port**: localhost:61613 （Adobe Commerce接続用）

>[!NOTE]
>
>開発とテストにはDockerのインストールをお勧めします。 本番環境では、適切なセキュリティ設定を行った手動インストールの使用を検討してください。

### オプション 2:Ubuntu/CentOSでの手動インストール

#### 前提条件

Java 17以降がインストールされていることを確認します（ActiveMQ Artemis 2.42.0以降で必要）。

### インストール手順

1. [Apache ActiveMQ Artemis web サイト &#x200B;](https://activemq.apache.org/components/artemis/download/)から最新バージョンをダウンロードしてインストールします。 2025年9月現在、最新の安定バージョンは2.42.0です。

   ```shell
   sudo mkdir -p /opt/artemis
   cd /opt/artemis
   sudo curl -O https://downloads.apache.org/activemq/activemq-artemis/2.42.0/apache-artemis-2.42.0-bin.tar.gz
   sudo tar -xzf apache-artemis-2.42.0-bin.tar.gz --strip-components=1
   sudo rm apache-artemis-2.42.0-bin.tar.gz
   ```

1. `artemis` ユーザーを作成し、所有権を設定します。

   ```shell
   # Create artemis user and set ownership
   sudo useradd -r -s /bin/false artemis 2>/dev/null || true
   sudo chown -R artemis:artemis /opt/artemis
   ```

1. ブローカーインスタンスを作成します。

   ```shell
   sudo /opt/artemis/bin/artemis create /var/lib/artemis-instance --user artemis --password artemis --allow-anonymous
   sudo chown -R artemis:artemis /var/lib/artemis-instance
   ```

1. ブローカーを起動します。

   ```shell
   # Start in foreground (for testing)
   sudo /var/lib/artemis-instance/bin/artemis run
   
   # Start as background service
   sudo /var/lib/artemis-instance/bin/artemis-service start
   
   # Stop the broker
   sudo /var/lib/artemis-instance/bin/artemis-service stop
   
   # Restart the broker
   sudo /var/lib/artemis-instance/bin/artemis-service restart
   
   # Force stop the broker
   sudo /var/lib/artemis-instance/bin/artemis-service force-stop
   
   # Check broker status
   sudo /var/lib/artemis-instance/bin/artemis-service status
   ```

## ActiveMQ Artemisの設定

ブローカーの設定と管理については、ActiveMQ Artemisの公式ドキュメントを参照してください。 次の項目に注意してください。

- 環境変数
- ポートアクセス（STOMP プロトコル）
- デフォルトのユーザーアカウントと資格情報
- ブローカーの開始と停止
- システム制限とリソース調整

### 主要な設定ファイル

- `/var/lib/artemis-instance/etc/broker.xml` - メイン ブローカーの設定
- `/var/lib/artemis-instance/etc/artemis-users.properties` - ユーザー認証
- `/var/lib/artemis-instance/etc/artemis-roles.properties` - ユーザーロール
- `/var/lib/artemis-instance/etc/bootstrap.xml` - Bootstrap設定

### STOMP プロトコルの有効化

`/var/lib/artemis-instance/etc/broker.xml`を確認して、STOMP アクセプターが設定されていることを確認します。

```xml
<acceptors>
   <acceptor name="artemis">tcp://0.0.0.0:61616?tcpSendBufferSize=1048576;tcpReceiveBufferSize=1048576;amqpMinLargeMessageSize=102400;protocols=CORE,AMQP,STOMP,HORNETQ,MQTT,OPENWIRE;useEpoll=true;amqpCredits=1000;amqpLowCredits=300;amqpDuplicateDetection=true</acceptor>
   <acceptor name="stomp">tcp://0.0.0.0:61613?protocols=STOMP</acceptor>
   <acceptor name="stomp-ssl">tcp://0.0.0.0:61617?protocols=STOMP;sslEnabled=true;keyStorePath=/path/to/keystore.jks;keyStorePassword=password</acceptor>
</acceptors>
```

STOMPでSSLを有効にするには、`stomp-ssl`受信者を明示的に追加する必要があります。

## ActiveMQ Artemisでインストールし、接続する

ActiveMQ Artemisをインストールした&#x200B;_後にAdobe Commerce_&#x200B;をインストールする場合は、インストール時に次のコマンドラインパラメーターを追加します。

```shell
--stomp-host="<hostname>" --stomp-port="61613" --stomp-user="<user_name>" --stomp-password="<password>"
```

どこで：

| パラメーター | 説明 |
|--- |--- |
| `--stomp-host` | ActiveMQがインストールされているホスト名。 |
| `--stomp-port` | ActiveMQへの接続に使用するポート。 デフォルトは`61613`です。 |
| `--stomp-user` | ActiveMQに接続するためのユーザー名。 既定のユーザー`artemis`は使用しないでください。 |
| `--stomp-password` | ActiveMQに接続するためのパスワード。 既定のパスワード `artemis`は使用しないでください。 |
| `--stomp-ssl` | ActiveMQに接続するかどうかを示します。 デフォルトは`false`です。 値をtrueに設定する場合は、SSLの設定を参照してください。 |

## ActiveMQ Artemisの接続

`<install_directory>/app/etc/env.php` ファイルにRabbitMQ （AMQP）設定を含むAdobe Commerce インスタンスが既にあり、それをActiveMQに接続する場合は、次のように`queue` セクションをSTOMPに置き換えます。

```php
'queue' =>
  array (
    'stomp' =>
    array (
      'host' => 'activemq.example.com',
      'port' => '61613',  // SSL STOMP port (default 61617, non-SSL is 61613)
      'user' => 'magento',
      'password' => 'magento',
      // Performance tuning options
      'heartbeat_send' => 10000,     // 10 seconds // Optional
      'heartbeat_receive' => 10000,  // 10 seconds // Optional
      'read_timeout' => 250000       // 250ms // Optional
     ),
  ),
```

また、`bin/magento setup:config:set` コマンドを使用してActiveMQ設定値を設定することもできます（`app/etc/env.php` ファイルにAMQP設定が存在する場合は削除します）。

```shell
bin/magento setup:config:set --stomp-host="activemq.example.com" --stomp-port="61613" --stomp-user="magento" --stomp-password="magento"
```

コマンドを実行するか、STOMP設定値を含む`<install_directory>/app/etc/env.php` ファイルを更新した後、`bin/magento setup:upgrade`を実行して変更を適用し、ActiveMQに必要なキューを作成します。

## SSLの設定

SSLのサポートを設定するには、`<install_directory>/app/etc/env.php` ファイルの`ssl`および`ssl_options` パラメーターを編集して、次のようになります。

```php
'queue' =>
  array (
    'stomp' =>
    array (
      'host' => 'activemq.example.com',
      'port' => '61617',  // SSL STOMP port (default 61617, non-SSL is 61613)
      'user' => 'magento',
      'password' => 'magento',
      'ssl' => 'true',
      'ssl_options' => [
            'cafile' => '/etc/pki/tls/certs/DigiCertCA.crt',
            'local_cert' => '/path/to/magento/app/etc/ssl/test-activemq.crt', // Optional: Client certificate for mutual SSL
            'local_pk' => '/path/to/magento/app/etc/ssl/test-activemq.key', // Optional: Client private key for mutual SSL
            'passphrase' => 'client_key_password', // Optional: Passphrase for client private key
            'verify_peer' => true,
            'verify_peer_name' => true,
            'allow_self_signed' => false
       ],
      // Performance tuning options
      'heartbeat_send' => 10000,     // 10 seconds // Optional
      'heartbeat_receive' => 10000,  // 10 seconds // Optional
      'read_timeout' => 250000       // 250ms // Optional
     ),
  ),
```

### SSL設定オプション

| オプション | 説明 | Default |
|--- |--- |--- |
| `verify_peer` | ブローカーのSSL証明書を確認する | `true` |
| `verify_peer_name` | ブローカーのホスト名が証明書と一致することを確認します | `true` |
| `allow_self_signed` | 自己署名証明書を許可 | `false` |
| `cafile` | ブローカー検証用のCA証明書ファイルへのパス | SSLの場合は必須 |
| `certfile` | クライアント証明書ファイルへのパス（相互SSL用） | オプション |
| `keyfile` | クライアント秘密鍵ファイルへのパス（相互SSL用） | オプション |
| `passphrase` | クライアント秘密鍵のパスフレーズ | オプション |

### 開発SSL設定

開発環境では、緩和されたSSL設定を使用できます。

```php
'ssl_options' => [
    'verify_peer' => false,
    'verify_peer_name' => false,
    'allow_self_signed' => true
]
```

## パフォーマンス調整

ActiveMQ Artemisには、パフォーマンス調整オプションがいくつか用意されています。

```php
'queue' =>
  array (
    'stomp' =>
    array (
      'host' => 'activemq.example.com',
      'port' => '61613',
      'user' => 'artemis',
      'password' => 'artemis',
      // Performance options
      'heartbeat_send' => 10000,      // Send heartbeat every 10 seconds
      'heartbeat_receive' => 10000,   // Expect heartbeat every 10 seconds
      'read_timeout' => 250000,       // 250ms read timeout
     ),
  ),
```

## 追跡と管理

### Web コンソール

ActiveMQ Artemisは、次の場所からアクセスできるweb ベースの管理コンソールを提供します。
- URL: `http://localhost:8161/console`
- 既定の資格情報：`artemis/artemis`

## トラブルシューティング

### 一般的な問題

1. **接続が拒否されました**: ActiveMQ Artemisが実行されており、STOMP アクセプターが設定されていることを確認してください。
1. **認証に失敗しました**: ブローカー設定と`env.php` ファイルの両方でユーザー名とパスワードを確認してください。
1. **SSL ハンドシェイクが失敗しました**: SSL証明書と設定を確認してください。




### STOMP接続の確認

telnetを使用してSTOMP接続をテストします。

```shell
telnet localhost 61613
```

接続が確立されます。 STOMP コマンドを使用してテストするには、次の手順に従います。

```shell
# Test basic STOMP connection
echo -e "CONNECT\nhost:localhost\n\n\x00" | telnet localhost 61613
```

予想される出力では、接続が確立され、STOMP プロトコル応答が表示されます。

## メッセージキューコンシューマーを開始

Adobe CommerceとActiveMQ Artemisを接続したら、メッセージキューコンシューマーを開始する必要があります。 詳しくは、[&#x200B; メッセージキューの設定](../../configuration/cli/start-message-queues.md)を参照してください。

