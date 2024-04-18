---
title: メッセージブローカー
description: 次の手順に従って、必要なメッセージブローカーソフトウェア（など）をインストールして設定します [!DNL RabbitMQ]）を選択します（Adobe Commerceのオンプレミスインストールの場合）。
exl-id: ae6200d6-540f-46b3-92ba-7df7f6bb6fae
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---

# メッセージブローカー

Adobe Commerceはを使用します [!DNL RabbitMQ] オープンソースのメッセージブローカ。 信頼性が高く、可用性が高く、スケーラブルで、ポータブルなメッセージングシステムを提供します。

メッセージキューは、メッセージの送信者と受信者が互いに接触しない非同期通信メカニズムを提供します。 また、メッセージキューと同時に通信する必要もありません。 送信者がメッセージをキューに入れると、受信者が受信するまで保存されます。

Adobe Commerceをインストールする前に、メッセージキューシステムを確立する必要があります。 基本的なシーケンスは次のとおりです。

1. インストール [!DNL RabbitMQ] およびその前提条件。
1. 接続 [!DNL RabbitMQ] をAdobe Commerceに送信します。

>[!NOTE]
>
>MySQL を使用するか、 [!DNL RabbitMQ] メッセージキューの処理用。 メッセージキューシステムの設定については、を参照してください。 [メッセージキューの概要](https://developer.adobe.com/commerce/php/development/components/message-queues/). Adobe Commerceで Bulk API を使用する場合、メッセージキューのシステム設定はデフォルトで次を使用します [!DNL RabbitMQ] メッセージブローカーとして。 参照： [メッセージキューコンシューマーの開始](../../configuration/cli/start-message-queues.md) を参照してください。

## インストール [!DNL RabbitMQ] Ubuntu の場合

をインストールするには [!DNL RabbitMQ] ubuntu 16 で、次のコマンドを入力します。

```bash
sudo apt install -y rabbitmq-server
```

このコマンドは、必要な Erlang パッケージもインストールします。

古いバージョンの Ubuntu がある場合は、 [!DNL RabbitMQ] では、Web サイトからパッケージをインストールすることをお勧めします。

1. .deb パッケージを [rabbitmq-server](https://www.rabbitmq.com/download.html).
1. を含むパッケージのインストール `dpkg`.

こちらを参照してください [Debian/Ubuntu へのインストール](https://www.rabbitmq.com/install-debian.html) を参照してください。

## インストール [!DNL RabbitMQ] （CentOS 上）

### Erlang のインストール

[!DNL RabbitMQ] は Erlang プログラミング言語で記述されており、と同じシステムにインストールする必要があります [!DNL RabbitMQ].

参照： [手動インストール](https://www.erlang-solutions.com/downloads/) を参照してください。

を参照してください。 [[!DNL RabbitMQ]/Erlang バージョン マトリックス](https://www.rabbitmq.com/which-erlang.html) 正しいバージョンをインストールします。

### インストール [!DNL RabbitMQ]

この [!DNL RabbitMQ] サーバーは CentOS に含まれていますが、バージョンは多くの場合、古いです。 [!DNL RabbitMQ] では、Web サイトからパッケージをインストールすることをお勧めします。

を参照してください。 [!DNL RabbitMQ] ページをインストールして、サポートされている最新バージョンを入手します。 Adobe Commerce 2.3 および 2.4 のサポート [!DNL RabbitMQ] 3.8.x

こちらを参照してください [RPM ベースの Linux へのインストール](https://www.rabbitmq.com/install-rpm.html) を参照してください。

## 設定 [!DNL RabbitMQ]

職員を再調査する [!DNL RabbitMQ] 設定および管理するドキュメント [!DNL RabbitMQ]. 次の項目に注意してください。

* 環境変数
* ポートアクセス
* デフォルトのユーザーアカウント
* ブローカーの起動と停止
* システム制限

## でのインストール [!DNL RabbitMQ] と接続

Adobe Commerceのインストール方法 _後_ をインストールします [!DNL RabbitMQ]をインストールする際に、次のコマンドラインパラメーターを追加します。

```bash
--amqp-host="<hostname>" --amqp-port="5672" --amqp-user="<user_name>" --amqp-password="<password>" --amqp-virtualhost="/"
```

ここで、

| パラメーター | 説明 |
|--- |--- |
| `--amqp-host` | ホスト名 [!DNL RabbitMQ] がインストールされました。 |
| `--amqp-port` | への接続に使用するポート [!DNL RabbitMQ]. デフォルトはです `5672`. |
| `--amqp-user` | に接続するためのユーザー名 [!DNL RabbitMQ]. デフォルトユーザーを使用しない `guest`. |
| `--amqp-password` | に接続するためのパスワード [!DNL RabbitMQ]. デフォルトのパスワードを使用しない `guest`. |
| `--amqp-virtualhost` | 接続先の仮想ホスト [!DNL RabbitMQ]. デフォルトはです `/`. |
| `--amqp-ssl` | 接続先を示します [!DNL RabbitMQ]. デフォルトはです `false`. 値を true に設定した場合、詳しくは、SSL の設定を参照してください。 |

## 接続 [!DNL RabbitMQ]

既にAdobe Commerceをインストールしていて、次への接続を希望する場合： [!DNL RabbitMQ]、を追加します `queue` セクション： `<install_directory>/app/etc/env.php` 次のようにファイルを指定します。

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

以下を設定することもできます [!DNL RabbitMQ] を使用した設定値 `bin/magento setup:config:set` コマンド：

```bash
bin/magento setup:config:set --amqp-host="rabbitmq.example.com" --amqp-port="11213" --amqp-user="magento" --amqp-password="magento" --amqp-virtualhost="/"
```

コマンドの実行後または `<install_directory>/app/etc/env.php` amqp 設定値を含むファイル、実行 `bin/magento setup:upgrade` で変更を適用し、必要なキューと交換を作成します。 [!DNL RabbitMQ].

## SSL を設定

SSL のサポートを設定するには、 `ssl` および `ssl_options` のパラメーター `<install_directory>/app/etc/env.php` 次のようになるようにファイルします。

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

Adobe Commerceに接続し、 [!DNL RabbitMQ]の場合は、メッセージキューコンシューマーを起動する必要があります。 参照： [メッセージキューの設定](../../configuration/cli/start-message-queues.md) を参照してください。
