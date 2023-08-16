---
title: メッセージブローカー
description: 次の手順に従って、必要な Message Broker ソフトウェア ( [!DNL RabbitMQ]) を使用して、Adobe CommerceとMagento Open Sourceのオンプレミスでのインストールを行います。
exl-id: ae6200d6-540f-46b3-92ba-7df7f6bb6fae
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# メッセージブローカー

Adobe Commerceは [!DNL RabbitMQ] オープンソースのメッセージブローカー。 高い可用性と拡張性を備え、ポータブルなメッセージングシステムを提供します。

メッセージキューは、メッセージの送信者と受信者が互いに連絡を取らない非同期通信メカニズムを提供する。 また、メッセージキューと同時に通信する必要もありません。 送信者がメッセージをキューに入れると、受信者がメッセージを受け取るまで保存されます。

メッセージキューシステムは、Adobe CommerceまたはMagento Open Sourceをインストールする前に確立する必要があります。 基本的なシーケンスは次のとおりです。

1. インストール [!DNL RabbitMQ] およびその前提条件
1. 接続 [!DNL RabbitMQ] Adobe CommerceまたはMagento Open Sourceに

>[!NOTE]
>
>MySQL または [!DNL RabbitMQ] メッセージキューの処理用。 メッセージキューシステムの設定について詳しくは、 [メッセージキュー：概要](https://developer.adobe.com/commerce/php/development/components/message-queues/). Adobe Commerceで Bulk API を使用している場合、メッセージキューのシステム設定はデフォルトで [!DNL RabbitMQ] メッセージブローカーとして。 詳しくは、 [メッセージキューコンシューマーを開始](../../configuration/cli/start-message-queues.md) を参照してください。

## インストール [!DNL RabbitMQ] Ubuntu で

をインストールするには [!DNL RabbitMQ] Ubuntu 16 で、次のコマンドを入力します。

```bash
sudo apt install -y rabbitmq-server
```

このコマンドは、必要な Erlang パッケージもインストールします。

古いバージョンの Ubuntu がある場合、 [!DNL RabbitMQ] では、Web サイトからパッケージをインストールすることをお勧めします。

1. .deb パッケージのダウンロード先 [rabbitmq-server](https://www.rabbitmq.com/download.html).
1. パッケージのインストール先 `dpkg`.

参照： [Debian/Ubuntu へのインストール](https://www.rabbitmq.com/install-debian.html) を参照してください。

## インストール [!DNL RabbitMQ] CentOS で

### Erlang のインストール

[!DNL RabbitMQ] は Erlang プログラミング言語を使用して書かれていましたが、この言語はと同じシステムにインストールする必要があります。 [!DNL RabbitMQ].

詳しくは、 [手動インストール](https://www.erlang-solutions.com/downloads/) を参照してください。

詳しくは、 [[!DNL RabbitMQ]/Erlang バージョンのマトリックス](https://www.rabbitmq.com/which-erlang.html) をクリックして、正しいバージョンをインストールします。

### インストール [!DNL RabbitMQ]

The [!DNL RabbitMQ] サーバーは CentOS に含まれていますが、多くの場合、古いバージョンです。 [!DNL RabbitMQ] では、Web サイトからパッケージをインストールすることをお勧めします。

詳しくは、 [!DNL RabbitMQ] サポートされている最新バージョンを取得するには、インストールページを使用します。 Adobe CommerceとMagento Open Source2.3 および 2.4 のサポート [!DNL RabbitMQ] 3.8.x.

参照： [RPM ベースの Linux へのインストール](https://www.rabbitmq.com/install-rpm.html) を参照してください。

## 設定 [!DNL RabbitMQ]

公式のレビュー [!DNL RabbitMQ] 設定および管理に関するドキュメント [!DNL RabbitMQ]. 次の項目に注意してください。

* 環境変数
* ポートアクセス
* デフォルトのユーザーアカウント
* ブローカーの起動と停止
* システムの制限

## 次を使用してインストール [!DNL RabbitMQ] と接続します。

Adobe CommerceまたはMagento Open Source _次より後_ インストール [!DNL RabbitMQ]をクリックし、インストール時に次のコマンドラインパラメーターを追加します。

```bash
--amqp-host="<hostname>" --amqp-port="5672" --amqp-user="<user_name>" --amqp-password="<password>" --amqp-virtualhost="/"
```

次の場合：

| パラメーター | 説明 |
|--- |--- |
| `--amqp-host` | ホスト名： [!DNL RabbitMQ] がインストールされている。 |
| `--amqp-port` | 接続に使用するポート [!DNL RabbitMQ]. デフォルトはです。 `5672`. |
| `--amqp-user` | 接続先のユーザー名 [!DNL RabbitMQ]. デフォルトのユーザーを使用しない `guest`. |
| `--amqp-password` | 接続用のパスワード [!DNL RabbitMQ]. デフォルトのパスワードを使用しない `guest`. |
| `--amqp-virtualhost` | 接続する仮想ホスト [!DNL RabbitMQ]. デフォルトはです。 `/`. |
| `--amqp-ssl` | 接続するかどうかを示します [!DNL RabbitMQ]. デフォルトはです。 `false`. 値を true に設定した場合、詳しくは SSL の設定を参照してください。 |

## 接続 [!DNL RabbitMQ]

既にAdobe CommerceまたはMagento Open Sourceがインストールされていて、接続先となる場合 [!DNL RabbitMQ]、を追加します。 `queue` セクション内 `<install_directory>/app/etc/env.php` ファイルの内容が次のようになります。

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

また、 [!DNL RabbitMQ] 設定値を `bin/magento setup:config:set` コマンド：

```bash
bin/magento setup:config:set --amqp-host="rabbitmq.example.com" --amqp-port="11213" --amqp-user="magento" --amqp-password="magento" --amqp-virtualhost="/"
```

コマンドの実行後、または `<install_directory>/app/etc/env.php` AMQP 構成値を持つファイル、実行 `bin/magento setup:upgrade` 変更を適用し、必要なキューと交換を [!DNL RabbitMQ].

## SSL の設定

SSL のサポートを設定するには、 `ssl` および `ssl_options` パラメーターを `<install_directory>/app/etc/env.php` ファイルで次のように表示されます。

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

## メッセージキューのコンシューマーを開始

Adobe Commerceと [!DNL RabbitMQ]メッセージキューのコンシューマーを開始する必要があります。 詳しくは、 [メッセージキューの設定](../../configuration/cli/start-message-queues.md) 」を参照してください。
