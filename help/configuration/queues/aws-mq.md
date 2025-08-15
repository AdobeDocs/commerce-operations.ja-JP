---
title: Amazon Message Queue の設定
description: AWS MQ サービスを使用するようにCommerceを設定する方法について説明します。
exl-id: 463e513f-e8d4-4450-845e-312cbf00d843
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# Amazon Message Queue の設定

Commerce 2.4.3 以降、オンプレミスのメッセージキューインスタンスの代わりに、Amazon Message Queue （MQ）をクラウド対応として使用できるようになりました。

AWSでメッセージキューを作成するには、[AWS ドキュメントの ](https://docs.aws.amazon.com/amazon-mq/latest/developer-guide/amazon-mq-setting-up.html)Amazon MQ の設定 _を参照してください_。

## Commerce for AWS MQ の設定

AWS MQ サービスに接続するには、`queue.amqp` ファイルで `env.php` オブジェクトを設定します。
AWS Message Queue には SSL/TLS 接続が必要です。

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

ここで、

- `host` - AMQP エンドポイントの URL。AWSでブローカ名をクリックすると使用可能になります（「https://」と末尾のポート番号を削除します）
- `user` - AWS MQ ブローカの作成時に入力されたユーザ名の値
- `password` - AWS MQ ブローカーの作成時に入力されたパスワード値

>[!INFO]
>
>Amazon MQ は、TLS 接続のみをサポートしています。 ピアの検証はサポートされていません。

`env.php` ファイルを編集した後、次のコマンドを実行してセットアップを完了します。

```bash
bin/magento setup:upgrade
```

## CommerceでのAWS MQ サービスの使用方法

`async.operations.all` メッセージ キューコンシューマーは、AMQP 接続を使用します。

このコンシューマーは、プレフィックスが `async` の任意のトピック名をAWS MQ 接続を介してルーティングします。

例えば、`InventoryCatalog` には次のものがあります。

```text
async.V1.inventory.bulk-product-source-assign.POST
async.V1.inventory.bulk-product-source-unassign.POST
async.V1.inventory.bulk-product-source-transfer.POST
```

`InventoryCatalog` のデフォルトの設定では、メッセージは [!DNL RabbitMQ] に公開されません。デフォルトの動作では、同じユーザースレッドでアクションを実行します。 メッセージを公開するように `InventoryCatalog` に指示するには、`cataloginventory/bulk_operations/async` を有効にします。 管理者で、**ストア**/設定/**カタログ**/**在庫**/管理者の一括操作に移動し、「`Run asynchronously`**はい**」に設定します。

## メッセージキューのテスト

Commerceから [!DNL RabbitMQ] へのメッセージ送信をテストするには：

1. キューを監視するには、AWSで [!DNL RabbitMQ] web コンソールにログインします。
1. 管理者で、製品を作成します。
1. 在庫ソースの作成。
1. **ストア**/設定/**カタログ**/**在庫**/管理者の一括操作/非同期で実行を有効にします。
1. **カタログ**/製品に移動します。 グリッドから、上記で作成した商品を選択し、「**在庫の割り当てSource**」をクリックします。
1. 「**保存して閉じる**」をクリックして、プロセスを完了します。

   これで、メッセージが [!DNL RabbitMQ] web コンソールに表示されます。

1. `async.operations.all` メッセージキューコンシューマーを起動します。

   ```bash
   bin/magento queue:consumers:start async.operations.all
   ```

これで、キューに入れられたメッセージが [!DNL RabbitMQ] web コンソールで処理されたことを確認できます。
管理画面で、製品の在庫ソースが変更されていることを確認します。
