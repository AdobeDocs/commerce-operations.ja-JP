---
title: メッセージブローカー
description: 以下の手順に従って、Adobe CommerceとMagento Open Sourceのオンプレミスインストールに必要なメッセージブローカーソフトウェア（RabbitMQ など）をインストールし、設定します。
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 0%

---


# メッセージブローカー

Adobe Commerceは RabbitMQ オープンソースメッセージブローカーを使用します。 高い可用性と拡張性を備え、ポータブルなメッセージングシステムを提供します。

メッセージキューは、メッセージの送信者と受信者が互いに連絡を取らない非同期通信メカニズムを提供する。 また、メッセージキューと同時に通信する必要もありません。 送信者がメッセージをキューに入れると、受信者がメッセージを受け取るまで保存されます。

メッセージキューシステムは、Adobe CommerceまたはMagento Open Sourceをインストールする前に確立する必要があります。 基本的なシーケンスは次のとおりです。

1. RabbitMQ およびその他の前提条件をインストールします。
1. RabbitMQ をAdobe CommerceまたはMagento Open Sourceに接続します。

>[!NOTE]
>
>MySQL または RabbitMQ を使用してメッセージキューを処理できます。 メッセージキューシステムの設定について詳しくは、 [メッセージキュー：概要](https://developer.adobe.com/commerce/php/development/components/message-queues/). Adobe Commerceで Bulk API を使用している場合、メッセージキューのシステム設定では、デフォルトで RabbitMQ をメッセージブローカーとして使用します。 詳しくは、 [メッセージキューコンシューマーを開始](../../configuration/cli/start-message-queues.md) を参照してください。

## Ubuntu に RabbitMQ をインストール

Ubuntu 16 に RabbitMQ をインストールするには、次のコマンドを入力します。

```bash
sudo apt install -y rabbitmq-server
```

このコマンドは、必要な Erlang パッケージもインストールします。

古いバージョンの Ubuntu がある場合、RabbitMQ は、Web サイトからパッケージをインストールすることをお勧めします。

1. .deb パッケージのダウンロード先 [rabbitmq-server](https://www.rabbitmq.com/download.html).
1. パッケージのインストール先 `dpkg`.

参照： [Debian/Ubuntu へのインストール](https://www.rabbitmq.com/install-debian.html) を参照してください。

## CentOS での RabbitMQ のインストール

### Erlang のインストール

RabbitMQ は Erlang プログラミング言語を使用して記述されました。RabbitMQ と同じシステムにインストールする必要があります。

詳しくは、 [手動インストール](https://www.erlang-solutions.com/downloads/) を参照してください。

詳しくは、 [RabbitMQ/Erlang バージョンマトリックス](https://www.rabbitmq.com/which-erlang.html) をクリックして、正しいバージョンをインストールします。

### RabbitMQ のインストール

RabbitMQ サーバーは CentOS に含まれていますが、バージョンは古いことが多いです。 RabbitMQ では、Web サイトからパッケージをインストールすることをお勧めします。

サポートされている最新バージョンを取得するには、 RabbitMQ のインストールページを参照してください。 Adobe CommerceおよびMagento Open Source2.3 および 2.4 では、RabbitMQ 3.8.x がサポートされています。

参照： [RPM ベースの Linux へのインストール](https://www.rabbitmq.com/install-rpm.html) を参照してください。

## RabbitMQ の設定

RabbitMQ の設定と管理については、公式の RabbitMQ ドキュメントを参照してください。 次の項目に注意してください。

* 環境変数
* ポートアクセス
* デフォルトのユーザーアカウント
* ブローカーの起動と停止
* システム制限

## RabbitMQ と共にインストールし、接続します。

Adobe CommerceまたはMagento Open Source _後_ RabbitMQ をインストールする場合は、インストール中に次のコマンドラインパラメーターを追加します。

```bash
--amqp-host="<hostname>" --amqp-port="5672" --amqp-user="<user_name>" --amqp-password="<password>" --amqp-virtualhost="/"
```

ここで、

| パラメータ | 説明 |
|--- |--- |
| `--amqp-host` | RabbitMQ がインストールされているホスト名。 |
| `--amqp-port` | RabbitMQ への接続に使用するポート。 デフォルトはです。 `5672`. |
| `--amqp-user` | RabbitMQ に接続するためのユーザー名。 デフォルトのユーザーを使用しない `guest`. |
| `--amqp-password` | RabbitMQ に接続するためのパスワード。 デフォルトのパスワードを使用しない `guest`. |
| `--amqp-virtualhost` | RabbitMQ に接続するための仮想ホスト。 デフォルトはです。 `/`. |
| `--amqp-ssl` | RabbitMQ に接続するかどうかを示します。 デフォルトはです。 `false`. 値を true に設定した場合、詳しくは SSL の設定を参照してください。 |

## RabbitMQ を接続

既にAdobe CommerceまたはMagento Open Sourceがインストールされていて、RabbitMQ に接続する場合は、 `queue` セクション `<install_directory>/app/etc/env.php` ファイルの内容が次のようになります。

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

RabbitMQ の設定値は、 `bin/magento setup:config:set` コマンド：

```bash
bin/magento setup:config:set --amqp-host="rabbitmq.example.com" --amqp-port="11213" --amqp-user="magento" --amqp-password="magento" --amqp-virtualhost="/"
```

コマンドの実行後、または `<install_directory>/app/etc/env.php` AMQP 構成値を持つファイル、実行 `bin/magento setup:upgrade` をクリックして、RabbitMQ で必要なキューと交換を作成します。

## SSL の設定

SSL のサポートを設定するには、 `ssl` および `ssl_options` パラメーター `<install_directory>/app/etc/env.php` ファイルで次のように表示されます。

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

Adobe Commerceと RabbitMQ を接続したら、メッセージキューコンシューマーを開始する必要があります。 詳しくは、 [メッセージキューの設定](../../configuration/cli/start-message-queues.md) 」を参照してください。
