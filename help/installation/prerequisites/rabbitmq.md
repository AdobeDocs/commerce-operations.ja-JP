---
title: メッセージブローカー（RabbitMQ）
description: 次の手順に従って、Adobe Commerceのオンプレミスインストールに必要な Message Broker ソフトウェア（ [!DNL RabbitMQ] など）をインストールして設定します。
exl-id: ae6200d6-540f-46b3-92ba-7df7f6bb6fae
source-git-commit: 73faaa2a3b9ce773e9a381d103735403966f568b
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---

# メッセージブローカー（RabbitMQ）

Adobe Commerceは、[!DNL RabbitMQ] のオープンソースの Message Broker を使用します。 信頼性が高く、可用性が高く、スケーラブルで、ポータブルなメッセージングシステムを提供します。

メッセージキューは、メッセージの送信者と受信者が互いに接触しない非同期通信メカニズムを提供します。 また、メッセージキューと同時に通信する必要もありません。 送信者がメッセージをキューに入れると、受信者が受信するまで保存されます。

Adobe Commerceをインストールする前に、メッセージキューシステムを確立する必要があります。 基本的なシーケンスは次のとおりです。

1. [!DNL RabbitMQ] およびその前提条件をインストールします。
1. [!DNL RabbitMQ] をAdobe Commerceに接続します。

>[!NOTE]
>
>メッセージキューの処理には、MySQL または [!DNL RabbitMQ] を使用できます。 メッセージキューシステムの設定について詳しくは、[&#x200B; メッセージキューの概要 &#x200B;](https://developer.adobe.com/commerce/php/development/components/message-queues/) を参照してください。 Adobe Commerceで Bulk API を使用している場合、メッセージキューのシステム設定はデフォルトで [!DNL RabbitMQ] をメッセージブローカーとして使用します。 詳しくは、[&#x200B; メッセージキューコンシューマーの開始 &#x200B;](../../configuration/cli/start-message-queues.md) を参照してください。

## Ubuntu への [!DNL RabbitMQ] のインストール

Ubuntu 16 に [!DNL RabbitMQ] をインストールするには、次のコマンドを入力します。

```bash
sudo apt install -y rabbitmq-server
```

このコマンドは、必要な Erlang パッケージもインストールします。

古いバージョンの Ubuntu をお使いの場合は、Web サイトからパッケージをインストールすることをお [!DNL RabbitMQ] めします。

1. [rabbitmq-server](https://www.rabbitmq.com/download.html) から.deb パッケージをダウンロードします。
1. `dpkg` を含むパッケージをインストールします。

詳しくは、[Debian/Ubuntu へのインストール &#x200B;](https://www.rabbitmq.com/install-debian.html) を参照してください。

## CentOS への [!DNL RabbitMQ] のインストール

### Erlang のインストール

[!DNL RabbitMQ] は、Erlang プログラミング言語を使用して記述されています。この言語は、[!DNL RabbitMQ] と同じシステムにインストールする必要があります。

詳しくは、[&#x200B; 手動インストール &#x200B;](https://www.erlang-solutions.com/downloads/) を参照してください。

正しいバージョンをインストールするには [[!DNL RabbitMQ]](https://www.rabbitmq.com/which-erlang.html)/Erlang のバージョンマトリックスを参照してください。

### [!DNL RabbitMQ] のインストール

[!DNL RabbitMQ] サーバーは CentOS に含まれていますが、多くの場合、バージョンは古いです。 [!DNL RabbitMQ] では、Web サイトからパッケージをインストールすることをお勧めします。

サポートされている最新のバージョンを取得するには、[!DNL RabbitMQ] のインストール ページを参照してください。 Adobe Commerce 2.3 および 2.4 は、[!DNL RabbitMQ] 3.8.x をサポートしています。

詳しくは、[RPM ベースの Linux へのインストール &#x200B;](https://www.rabbitmq.com/install-rpm.html) を参照してください。

## [!DNL RabbitMQ] の設定

公式の [!DNL RabbitMQ] ドキュメントを参照して、[!DNL RabbitMQ] の設定と管理を行います。 次の項目に注意してください。

* 環境変数
* ポートアクセス
* デフォルトのユーザーアカウント
* ブローカーの起動と停止
* システム制限

## [!DNL RabbitMQ] を使用したインストールと接続

Adobe Commerce _after_ をインストールする場合は、インストール時に次のコマンドラインパラメーターを追加 [!DNL RabbitMQ] ます。

```bash
--amqp-host="<hostname>" --amqp-port="5672" --amqp-user="<user_name>" --amqp-password="<password>" --amqp-virtualhost="/"
```

ここで、

| パラメーター | 説明 |
|--- |--- |
| `--amqp-host` | [!DNL RabbitMQ] がインストールされているホスト名。 |
| `--amqp-port` | [!DNL RabbitMQ] への接続に使用するポート。 デフォルトは `5672` です。 |
| `--amqp-user` | [!DNL RabbitMQ] に接続するためのユーザー名。 デフォルトのユーザー `guest` は使用しないでください。 |
| `--amqp-password` | [!DNL RabbitMQ] に接続するためのパスワード デフォルトのパスワード `guest` は使用しないでください。 |
| `--amqp-virtualhost` | [!DNL RabbitMQ] に接続するための仮想ホスト。 デフォルトは `/` です。 |
| `--amqp-ssl` | [!DNL RabbitMQ] に接続するかどうかを示します。 デフォルトは `false` です。 値を true に設定した場合、詳しくは、SSL の設定を参照してください。 |

## Connect [!DNL RabbitMQ]

既にAdobe Commerceをインストールしていて、それを [!DNL RabbitMQ] に接続する場合は、`queue` ファイルに次のような `<install_directory>/app/etc/env.php` セクションを追加します。

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

[!DNL RabbitMQ] のコマンドを使用 `bin/magento setup:config:set` て、設定値を設定することもできます。

```bash
bin/magento setup:config:set --amqp-host="rabbitmq.example.com" --amqp-port="11213" --amqp-user="magento" --amqp-password="magento" --amqp-virtualhost="/"
```

コマンドを実行するか、AMQP 設定値で `<install_directory>/app/etc/env.php` ファイルを更新した後、`bin/magento setup:upgrade` を実行して変更を適用し、必要なキューと交換を [!DNL RabbitMQ] で作成します。

## SSL を設定

SSL のサポートを設定するには、`ssl` ファイルの `ssl_options` パラメーターと `<install_directory>/app/etc/env.php` パラメーターを次のように編集します。

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

## メッセージキューコンシューマーの開始

Adobe Commerceと [!DNL RabbitMQ] を接続したら、メッセージキューコンシューマーを起動する必要があります。 詳しくは、[&#x200B; メッセージキューの設定 &#x200B;](../../configuration/cli/start-message-queues.md) を参照してください。
