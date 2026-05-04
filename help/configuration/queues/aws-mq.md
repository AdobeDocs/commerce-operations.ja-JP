---
title: Amazon メッセージキューの設定
description: クラウド対応AMQP接続のSSLおよびTLS要件など、env.phpでAmazon MQ用のAdobe Commerce メッセージキューを設定する方法について説明します。
exl-id: 463e513f-e8d4-4450-845e-312cbf00d843
source-git-commit: 41b8d77793f1c24f08ff7e6a2d35826a62477534
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# Amazon メッセージキューの設定

Commerce 2.4.3以降、Amazon Message Queue （MQ）は、オンプレミスのメッセージキューインスタンスのクラウド対応の代替品として利用できます。

AWSでメッセージキューを作成するには、_Amazon ドキュメント_&#x200B;の[AWS MQの設定](https://docs.aws.amazon.com/amazon-mq/latest/developer-guide/amazon-mq-setting-up.html)を参照してください。

## AWS MQ用Commerceの設定

AWS MQ サービスに接続するには、`env.php` ファイルで`queue.amqp` オブジェクトを設定します。
AWS Message QueueにはSSL/TLS接続が必要です。

```php
'queue' => [
    'amqp' => [
        'host' => '[host]', //example: c-bf4kk1c5-5gcc-4b43-9b9e-8f5b54d234.mq.us-west-3.amazonaws.com
        'port' => 5671,
        'user' => 'yourusername',
        'password' => 'yourpassword',
        'virtualhost' => '/',

        // AWS fields to add
        'ssl' => 'true'
    ]
],
```

どこで：

- `host` - AMQP エンドポイントのURL。AWSのブローカー名をクリックして使用できます（「https://」と末尾のポート番号を削除）。
- `user` - AWS MQ ブローカーの作成時に入力されたユーザー名値
- `password` - AWS MQ ブローカーの作成時に入力されたパスワード値

>[!INFO]
>
>Amazon MQでは、TLS接続のみをサポートしています。 ピア検証はサポートされていません。

`env.php` ファイルを編集したら、次のコマンドを実行してセットアップを完了します。

```shell
bin/magento setup:upgrade
```

## CommerceでAWS MQ サービスを使用する方法

`async.operations.all` メッセージ キューのコンシューマーはAMQP接続を使用しています。

このコンシューマーは、AWS MQ接続を介して、`async`でプレフィックス付きの任意のトピック名をルーティングします。

例えば、`InventoryCatalog`には次の項目があります。

```text
async.V1.inventory.bulk-product-source-assign.POST
async.V1.inventory.bulk-product-source-unassign.POST
async.V1.inventory.bulk-product-source-transfer.POST
```

`InventoryCatalog`の既定の設定では、[!DNL RabbitMQ]にメッセージを公開しません。既定の動作は、同じユーザースレッドでアクションを実行することです。 メッセージを公開するように`InventoryCatalog`に指示するには、`cataloginventory/bulk_operations/async`を有効にします。 管理者から、**ストア** / 設定/**カタログ** / **インベントリ** / 管理者一括操作に移動し、`Run asynchronously`を&#x200B;**はい**&#x200B;に設定します。

## メッセージキューのテスト

Commerceから[!DNL RabbitMQ]へのメッセージ送信をテストするには：

1. AWSの[!DNL RabbitMQ] web コンソールにログインして、キューをモニターします。
1. 管理画面で、製品を作成します。
1. 在庫ソースの作成。
1. **ストア**/設定/**カタログ**/**インベントリ**/管理者一括操作/非同期で実行を有効にします。
1. **カタログ** >製品に移動します。 グリッドから、上記で作成した商品を選択し、**在庫Sourceの割り当て**&#x200B;をクリックします。
1. 「**保存して閉じる**」をクリックして、プロセスを完了します。

   これで、[!DNL RabbitMQ] web コンソールにメッセージが表示されるようになりました。

1. `async.operations.all` メッセージキューコンシューマーを開始します。

   ```shell
   bin/magento queue:consumers:start async.operations.all
   ```

これで、キューに入れられたメッセージが[!DNL RabbitMQ] web コンソールで処理されます。
管理画面の製品で在庫ソースが変更されたことを確認します。
