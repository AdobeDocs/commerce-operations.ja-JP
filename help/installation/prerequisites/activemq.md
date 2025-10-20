---
title: メッセージ ブローカ （ActiveMQ Artemis）
description: 次の手順に従って、Adobe Commerceのオンプレミスインストール用に Apache ActiveMQ Artemis Message Broker をインストールして設定します。
source-git-commit: 46816b42ea30cb6c5f5ce59752cc00c38d221610
workflow-type: tm+mt
source-wordcount: '902'
ht-degree: 0%

---

# メッセージ ブローカ （ActiveMQ Artemis）

Adobe Commerceは、Simple Text Oriented Messaging Protocol （STOMP）を介した ActiveMQ Artemis オープンソースメッセージブローカーもサポートしています。 信頼性と拡張性に優れたメッセージングシステムを提供し、STOMP ベースの統合に柔軟性を提供します。


>[!NOTE]
>
>ActiveMQ Artemis は、Adobe Commerce 2.4.6 以降のバージョンで導入されました。 クラウドインフラストラクチャプロジェクトのAdobe CommerceCommerceへの ActiveMQ Artemis のインストールについて詳しくは、[Cloud Guide の &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/activemqsee)ActiveMQ サービスの設定 *を参照してください*

メッセージキューは、メッセージの送信者と受信者が互いに接触しない非同期通信メカニズムを提供します。 また、メッセージキューと同時に通信する必要もありません。 送信者がメッセージをキューに入れると、受信者が受信するまで保存されます。

Adobe Commerceをインストールする前に、メッセージキューシステムを確立する必要があります。 基本的なシーケンスは次のとおりです。

1. Apache ActiveMQ Artemis および必要な前提条件をインストールします。
1. ActiveMQ をAdobe Commerceに接続します。

>[!NOTE]
>
>メッセージキューの処理には、MySQL、ActiveMQ、または [!DNL RabbitMQ] を使用できます。 メッセージキューシステムの設定について詳しくは、[&#x200B; メッセージキューの概要 &#x200B;](https://developer.adobe.com/commerce/php/development/components/message-queues/) を参照してください。 Adobe Commerceで Bulk API を使用している場合、メッセージキューのシステム設定はデフォルトで [!DNL RabbitMQ] をメッセージブローカーとして使用します。 詳しくは、[&#x200B; メッセージキューコンシューマーの開始 &#x200B;](../../configuration/cli/start-message-queues.md) を参照してください。

>[!TIP]
>
>インストール前に、常に [Apache ActiveMQ Artemis ダウンロードページ &#x200B;](https://activemq.apache.org/components/artemis/download/) で最新の安定したバージョンを確認してください。 このドキュメントの例では、2025 年 9 月現在の最新の安定リリースであるバージョン 2.42.0 を使用しています。


## Apache ActiveMQ Artemis のインストール

ActiveMQ Artemis は、Docker （開発用に推奨）または手動インストール（実稼動用に推奨）を使用してインストールできます。

### オプション 1:Docker のインストール（開発用に推奨）

#### 前提条件

Docker がシステムにインストールされ、実行されていることを確認します。

>[!TIP]
>
>公式の ActiveMQ Artemis Docker イメージについて詳しくは、[Apache ActiveMQ Artemis Docker Hub ページ &#x200B;](https://hub.docker.com/r/apache/activemq-artemis) を参照してください。

#### インストール手順

1. 公式 Docker イメージを使用して ActiveMQ Artemis を実行します。

   ```bash
   # Run with default configuration
   docker run --detach \
     --name artemis \
     --publish 8161:8161 \
     --publish 61613:61613 \
     --publish 5672:5672 \
     apache/activemq-artemis:2.42.0
   ```

1. カスタム資格情報を使用して実行：

   ```bash
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

#### Docker 管理コマンド

```bash
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

Docker コンテナが実行されると、次の場所にアクセスできます。

- **Web コンソール**:http://localhost:8161/console （デフォルトの資格情報：artemis/artemis）
- **STOMP ポート**:localhost:61613 （Adobe Commerce接続用）

>[!NOTE]
>
>開発およびテストには、Docker をインストールすることをお勧めします。 実稼動環境の場合は、適切なセキュリティ設定を使用して手動インストールを行うことを検討してください。

### オプション 2:Ubuntu/CentOS での手動インストール

#### 前提条件

Java 17 以降がインストールされていることを確認します（ActiveMQ Artemis 2.42.0 以降で必要）。

### インストール手順

1. [Apache ActiveMQ Artemis web サイト &#x200B;](https://activemq.apache.org/components/artemis/download/) から最新バージョンをダウンロードしてインストールします。 2025 年 9 月現在、最新の安定バージョンは 2.42.0 です。

   ```bash
   sudo mkdir -p /opt/artemis
   cd /opt/artemis
   sudo curl -O https://downloads.apache.org/activemq/activemq-artemis/2.42.0/apache-artemis-2.42.0-bin.tar.gz
   sudo tar -xzf apache-artemis-2.42.0-bin.tar.gz --strip-components=1
   sudo rm apache-artemis-2.42.0-bin.tar.gz
   ```

1. `artemis` ユーザーを作成し、所有権を設定します。

   ```bash
   # Create artemis user and set ownership
   sudo useradd -r -s /bin/false artemis 2>/dev/null || true
   sudo chown -R artemis:artemis /opt/artemis
   ```

1. ブローカーインスタンスを作成します。

   ```bash
   sudo /opt/artemis/bin/artemis create /var/lib/artemis-instance --user artemis --password artemis --allow-anonymous
   sudo chown -R artemis:artemis /var/lib/artemis-instance
   ```

1. ブローカーを起動します。

   ```bash
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

## ActiveMQ Artemis の設定

公式の ActiveMQ Artemis ドキュメントを参照して、ブローカーを設定および管理します。 次の項目に注意してください。

- 環境変数
- ポートアクセス（STOMP プロトコル）
- デフォルトのユーザーアカウントと資格情報
- ブローカーの起動と停止
- システムの制限とリソースの調整

### 主要な設定ファイル

- `/var/lib/artemis-instance/etc/broker.xml` - メインブローカー設定
- `/var/lib/artemis-instance/etc/artemis-users.properties` - ユーザー認証
- `/var/lib/artemis-instance/etc/artemis-roles.properties` - ユーザーの役割
- `/var/lib/artemis-instance/etc/bootstrap.xml` - Bootstrapの設定

### STOMP プロトコルを有効にする

`/var/lib/artemis-instance/etc/broker.xml` をチェックして、STOMP アクセプターが設定されていることを確認します。

```xml
<acceptors>
   <acceptor name="artemis">tcp://0.0.0.0:61616?tcpSendBufferSize=1048576;tcpReceiveBufferSize=1048576;amqpMinLargeMessageSize=102400;protocols=CORE,AMQP,STOMP,HORNETQ,MQTT,OPENWIRE;useEpoll=true;amqpCredits=1000;amqpLowCredits=300;amqpDuplicateDetection=true</acceptor>
   <acceptor name="stomp">tcp://0.0.0.0:61613?protocols=STOMP</acceptor>
   <acceptor name="stomp-ssl">tcp://0.0.0.0:61617?protocols=STOMP;sslEnabled=true;keyStorePath=/path/to/keystore.jks;keyStorePassword=password</acceptor>
</acceptors>
```

STOMP で SSL を有効にするには、`stomp-ssl` アクセプターを明示的に追加する必要があります。

## ActiveMQ Artemis を使用してインストールし、接続します。

Adobe Commerce _after_ をインストールして ActiveMQ Artemis をインストールする場合は、インストール時に次のコマンドラインパラメーターを追加します。

```bash
--stomp-host="<hostname>" --stomp-port="61613" --stomp-user="<user_name>" --stomp-password="<password>"
```

ここで、

| パラメーター | 説明 |
|--- |--- |
| `--stomp-host` | ActiveMQ がインストールされているホスト名。 |
| `--stomp-port` | ActiveMQ への接続に使用するポート。 デフォルトは `61613` です。 |
| `--stomp-user` | ActiveMQ に接続するためのユーザー名。 デフォルトのユーザー `artemis` は使用しないでください。 |
| `--stomp-password` | ActiveMQ に接続するためのパスワード。 デフォルトのパスワード `artemis` は使用しないでください。 |
| `--stomp-ssl` | ActiveMQ に接続するかどうかを示します。 デフォルトは `false` です。 値を true に設定した場合、詳しくは、SSL の設定を参照してください。 |

## ActiveMQ Artemis の接続

`<install_directory>/app/etc/env.php` ファイルに RabbitMQ （AMQP）設定のAdobe Commerce インスタンスが既にあり、それを ActiveMQ に接続する場合は、`queue` のセクションを STOMP に置き換えて、次のようになります。

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

`bin/magento setup:config:set` コマンドを使用して ActiveMQ 設定値を設定することもできます（`app/etc/env.php` ファイルに AMQP 設定が存在する場合は、その設定を削除します）。

```bash
bin/magento setup:config:set --stomp-host="activemq.example.com" --stomp-port="61613" --stomp-user="magento" --stomp-password="magento"
```

コマンドを実行するか、STOMP 設定値で `<install_directory>/app/etc/env.php` ファイルを更新した後、`bin/magento setup:upgrade` を実行して変更を適用し、ActiveMQ で必要なキューを作成します。

## SSL を設定

SSL のサポートを設定するには、`ssl` ファイルの `ssl_options` パラメーターと `<install_directory>/app/etc/env.php` パラメーターを次のように編集します。

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

### SSL 設定オプション

| オプション | 説明 | デフォルト |
|--- |--- |--- |
| `verify_peer` | ブローカーの SSL 証明書の検証 | `true` |
| `verify_peer_name` | ブローカーのホスト名が証明書と一致することを確認します | `true` |
| `allow_self_signed` | 自己署名証明書を許可する | `false` |
| `cafile` | ブローカー検証用の CA 証明書ファイルへのパス | SSL に必須 |
| `certfile` | クライアント証明書ファイルのパス （相互 SSL の場合） | オプション |
| `keyfile` | クライアント秘密鍵ファイルのパス（相互 SSL 用） | オプション |
| `passphrase` | クライアント秘密鍵のパスフレーズ | オプション |

### 開発 SSL 設定

開発環境の場合、リラックスした SSL 設定を使用できます。

```php
'ssl_options' => [
    'verify_peer' => false,
    'verify_peer_name' => false,
    'allow_self_signed' => true
]
```

## パフォーマンスチューニング

ActiveMQ Artemis には、パフォーマンス調整オプションがいくつか用意されています。

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

## 監視と管理

### Web コンソール

ActiveMQ Artemis は、次の場所からアクセス可能な web ベースの管理コンソールを提供します。
- URL: `http://localhost:8161/console`
- 既定の資格情報：`artemis/artemis`

## トラブルシューティング

### よくある問題

1. **接続が拒否されました**: ActiveMQ Artemis が実行中で、STOMP アクセプターが構成されていることを確認してください。
1. **認証に失敗しました**: ブローカー構成と `env.php` ファイルの両方のユーザー名/パスワードを確認してください。
1. **SSL ハンドシェイクに失敗しました**: SSL 証明書と設定を検証します。




### STOMP 接続の検証

telnet を使用して STOMP 接続をテストします。

```bash
telnet localhost 61613
```

接続が確立されているのが確認できます。 STOMP コマンドを使用してテストするには、次の手順に従います。

```bash
# Test basic STOMP connection
echo -e "CONNECT\nhost:localhost\n\n\x00" | telnet localhost 61613
```

期待される出力では、接続が確立され、STOMP プロトコル応答が示されます。

## メッセージキューコンシューマーの開始

Adobe Commerceと ActiveMQ Artemis を接続したら、メッセージキューコンシューマーを起動する必要があります。 詳しくは、[&#x200B; メッセージキューの設定 &#x200B;](../../configuration/cli/start-message-queues.md) を参照してください。

