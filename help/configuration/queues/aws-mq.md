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

AWSでメッセージキューを作成するには、を参照してください。 [Amazon MQ のセットアップ](https://docs.aws.amazon.com/amazon-mq/latest/developer-guide/amazon-mq-setting-up.html) が含まれる _AWS ドキュメント_.

## Commerce for AWS MQ の設定

AWS MQ サービスに接続するには、以下を設定します。 `queue.amqp` 内のオブジェクト `env.php` ファイル。
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

- `host`—AMQP エンドポイントの URL。AWSでブローカー名をクリックすると使用できます（「https://」と末尾のポート番号を削除します）。
- `user`— AWS MQ ブローカを作成するときに入力されたユーザ名の値
- `password`—AWS MQ ブローカの作成時に入力されたパスワード値

>[!INFO]
>
>Amazon MQ は、TLS 接続のみをサポートしています。 ピアの検証はサポートされていません。

の編集後 `env.php` ファイルで、次のコマンドを実行してセットアップを完了します。

```bash
bin/magento setup:upgrade
```

## CommerceでのAWS MQ サービスの使用方法

この `async.operations.all` メッセージ キューコンシューマーは AMQP 接続を使用します。

このコンシューマーは、プレフィックスが付いたすべてのトピック名をルーティングします `async` AWS MQ 接続を介して。

例： `InventoryCatalog` 次のものがあります。

```text
async.V1.inventory.bulk-product-source-assign.POST
async.V1.inventory.bulk-product-source-unassign.POST
async.V1.inventory.bulk-product-source-transfer.POST
```

のデフォルト設定 `InventoryCatalog` メッセージをに公開しない [!DNL RabbitMQ]デフォルトの動作は、同じユーザスレッドでアクションを実行することです。 話す `InventoryCatalog` メッセージを公開するには、を有効にします `cataloginventory/bulk_operations/async`. 管理者から、に移動します。 **ストア** > 設定 > **カタログ** > **在庫** /管理者の一括操作と設定  `Run asynchronously`対象： **はい**.

## メッセージキューのテスト

Commerceからへのメッセージ送信をテストするには [!DNL RabbitMQ]:

1. にログインします [!DNL RabbitMQ] キューを監視するAWSの web コンソール。
1. 管理者で、製品を作成します。
1. 在庫ソースの作成。
1. Enable （有効） **ストア** > 設定 > **カタログ** > **在庫** /管理者の一括操作/非同期実行。
1. に移動 **カタログ** > 製品。 グリッドから、上で作成した製品を選択し、をクリックします **在庫ソースの割り当て**.
1. クリック **保存して閉じる** をクリックしてプロセスを完了します。

   メッセージがに表示されます。 [!DNL RabbitMQ] web コンソール。

1. を開始する `async.operations.all` メッセージキューコンシューマー。

   ```bash
   bin/magento queue:consumers:start async.operations.all
   ```

キュー内のメッセージが、 [!DNL RabbitMQ] web コンソール。
管理画面で、製品の在庫ソースが変更されていることを確認します。
