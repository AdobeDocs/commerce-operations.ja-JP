---
title: メッセージブローカー（RabbitMQ）
description: Adobe Commerceのオンプレミス インストールに必要なメッセージブローカーソフトウェア（ [!DNL RabbitMQ]など）をインストールして設定するには、次の手順に従います。
exl-id: ae6200d6-540f-46b3-92ba-7df7f6bb6fae
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 0%

---

# メッセージブローカー（RabbitMQ）

Adobe Commerceは、[!DNL RabbitMQ] オープンソースのメッセージブローカーを使用しています。 信頼性、高可用性、拡張性、ポータブルなメッセージングシステムを提供します。

メッセージキューは、メッセージの送信者と受信者が互いに接触しない非同期通信メカニズムを提供します。 また、メッセージキューと同時に通信する必要もありません。 送信者がメッセージをキューに入れると、受信者が受信するまで保存されます。

Adobe Commerceをインストールする前に、メッセージキューシステムを確立する必要があります。 基本的なシーケンスは次のとおりです。

1. [!DNL RabbitMQ]と前提条件をインストールします。
1. [!DNL RabbitMQ]をAdobe Commerceに接続します。

>[!NOTE]
>
>メッセージキュー処理には、MySQLまたは[!DNL RabbitMQ]を使用できます。 メッセージキューシステムの設定について詳しくは、[&#x200B; メッセージキューの概要](https://developer.adobe.com/commerce/php/development/components/message-queues/)を参照してください。 Adobe CommerceでBulk APIを使用している場合、メッセージキューシステム設定は、デフォルトで[!DNL RabbitMQ]をメッセージブローカーとして使用します。 詳しくは、[&#x200B; メッセージキューコンシューマー](../../configuration/cli/start-message-queues.md)の開始を参照してください。

## Ubuntuに[!DNL RabbitMQ]をインストール

Ubuntu 16に[!DNL RabbitMQ]をインストールするには、次のコマンドを入力します。

```shell
sudo apt install -y rabbitmq-server
```

このコマンドは、必要なErlang パッケージもインストールします。

古いバージョンのUbuntuをお持ちの場合、[!DNL RabbitMQ]はWeb サイトからパッケージをインストールすることをお勧めします。

1. [rabbitmq-server](https://www.rabbitmq.com/download.html)から.deb パッケージをダウンロードします。
1. `dpkg`のパッケージをインストールします。

詳しくは、[Debian/Ubuntuへのインストール &#x200B;](https://www.rabbitmq.com/install-debian.html)を参照してください。

## CentOSに[!DNL RabbitMQ]をインストール

### Erlangのインストール

[!DNL RabbitMQ]はErlang プログラミング言語を使用して作成されました。これは[!DNL RabbitMQ]と同じシステムにインストールする必要があります。

詳しくは、[手動インストール &#x200B;](https://www.erlang-solutions.com/downloads/)を参照してください。

正しいバージョンをインストールするには、[[!DNL RabbitMQ]/Erlang バージョン マトリックス &#x200B;](https://www.rabbitmq.com/which-erlang.html)を参照してください。

### [!DNL RabbitMQ]をインストール

[!DNL RabbitMQ] サーバーはCentOSに含まれていますが、多くの場合、バージョンが古くなっています。 [!DNL RabbitMQ]様は、web サイトからパッケージをインストールすることをお勧めします。

サポートされている最新バージョンを取得するには、[!DNL RabbitMQ] インストールページを参照してください。 Adobe Commerce 2.3および2.4では、[!DNL RabbitMQ] 3.8.xがサポートされています。

詳しくは、[RPM ベースのLinux](https://www.rabbitmq.com/install-rpm.html)へのインストールを参照してください。

## [!DNL RabbitMQ]の設定

[!DNL RabbitMQ]の設定と管理については、[!DNL RabbitMQ]の公式ドキュメントを参照してください。 次の項目に注意してください。

* 環境変数
* ポートアクセス
* デフォルトユーザーアカウント
* ブローカーの開始と停止
* システム制限

## [!DNL RabbitMQ]でインストールして接続

[!DNL RabbitMQ]をインストールした&#x200B;_後にAdobe Commerce_&#x200B;をインストールする場合は、インストール中に次のコマンドラインパラメーターを追加します。

```shell
--amqp-host="<hostname>" --amqp-port="5672" --amqp-user="<user_name>" --amqp-password="<password>" --amqp-virtualhost="/"
```

どこで：

| パラメーター | 説明 |
|--- |--- |
| `--amqp-host` | [!DNL RabbitMQ]がインストールされているホスト名。 |
| `--amqp-port` | [!DNL RabbitMQ]への接続に使用するポート。 デフォルトは`5672`です。 |
| `--amqp-user` | [!DNL RabbitMQ]に接続するためのユーザー名。 既定のユーザー`guest`は使用しないでください。 |
| `--amqp-password` | [!DNL RabbitMQ]に接続するためのパスワード。 既定のパスワード `guest`は使用しないでください。 |
| `--amqp-virtualhost` | [!DNL RabbitMQ]に接続するための仮想ホスト。 デフォルトは`/`です。 |
| `--amqp-ssl` | [!DNL RabbitMQ]に接続するかどうかを示します。 デフォルトは`false`です。 値をtrueに設定する場合は、SSLの設定を参照してください。 |

## [!DNL RabbitMQ]を接続

既にAdobe Commerceがインストールされていて、[!DNL RabbitMQ]に接続する場合は、`<install_directory>/app/etc/env.php` ファイルに`queue` セクションを追加して、次のようになります。

```php
'queue' =>
  array (
    'amqp' =>
    array (
      'host' => 'rabbitmq.example.com',
      'port' => '11213',
      'user' => 'magento',
      'password' => 'magento',
      'virtualhost' => '/'
     ),
  ),
```

`bin/magento setup:config:set` コマンドを使用して[!DNL RabbitMQ]の設定値を設定することもできます。

```shell
bin/magento setup:config:set --amqp-host="rabbitmq.example.com" --amqp-port="11213" --amqp-user="magento" --amqp-password="magento" --amqp-virtualhost="/"
```

コマンドを実行するか、AMQP設定値を含む`<install_directory>/app/etc/env.php` ファイルを更新した後、`bin/magento setup:upgrade`を実行して変更を適用し、必要なキューと交換を[!DNL RabbitMQ]に作成します。

## SSLの設定

SSLのサポートを設定するには、`<install_directory>/app/etc/env.php` ファイルの`ssl`および`ssl_options` パラメーターを編集して、次のようになります。

```php
'queue' =>
  array (
    'amqp' =>
    array (
      'host' => 'rabbitmq.example.com',
      'port' => '11213',
      'user' => 'magento',
      'password' => 'magento',
      'virtualhost' => '/',
      'ssl' => 'true',
      'ssl_options' => [
            'cafile' =>  '/etc/pki/tls/certs/DigiCertCA.crt',
            'certfile' => '/path/to/magento/app/etc/ssl/test-rabbit.crt',
            'keyfile' => '/path/to/magento/app/etc/ssl/test-rabbit.key'
       ],
     ),
  ),
```

## メッセージキューコンシューマーを開始

Adobe Commerceと[!DNL RabbitMQ]を接続したら、メッセージキューコンシューマーを開始する必要があります。 詳しくは、[&#x200B; メッセージキューの設定](../../configuration/cli/start-message-queues.md)を参照してください。
