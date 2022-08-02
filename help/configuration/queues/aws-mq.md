---
title: Amazon Message Queue の設定
description: AWS MQ サービスを使用するように Commerce を設定する方法を説明します。
source-git-commit: ee2e446edf79efcd7cbbd67248f8e7ece06bfefd
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---


# Amazon Message Queue の設定

Commerce 2.4.3 以降、Amazon Message Queue(MQ) は、オンプレミスのメッセージキューインスタンスに対するクラウド対応の代替機能として使用できます。

AWSでメッセージキューを作成するには、 [Amazon MQ の設定](https://docs.aws.amazon.com/amazon-mq/latest/developer-guide/amazon-mq-setting-up.html) 内 _AWSドキュメント_.

## Commerce for AWS MQ の設定

AWS MQ サービスに接続するには、 `queue.amqp` オブジェクトを `env.php` ファイル。
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

- `host`- AMQP エンドポイントの URL。AWSでブローカー名 (「https://」を削除し、末尾のポート番号を削除 ) をクリックすると使用できます。
- `user`— AWS MQ ブローカーの作成時に入力したユーザー名の値
- `password`— AWS MQ ブローカーの作成時に入力したパスワード値

>[!INFO]
>
>Amazon MQ は、TLS 接続のみをサポートします。 ピアの検証はサポートされていません。

編集後 `env.php` ファイルを開き、次のコマンドを実行して設定を完了します。

```bash
bin/magento setup:upgrade
```

## Commerce がAWS MQ サービスを使用する方法

この `async.operations.all` メッセージキューコンシューマーは、AMQP 接続を使用します。

このコンシューマーは、 `async` AWS MQ 接続を介して

例： `InventoryCatalog` 以下があります。

```text
async.V1.inventory.bulk-product-source-assign.POST
async.V1.inventory.bulk-product-source-unassign.POST
async.V1.inventory.bulk-product-source-transfer.POST
```

のデフォルト設定 `InventoryCatalog` は RabbitMQ にメッセージを公開しません。デフォルトの動作では、同じユーザースレッドでアクションを実行します。 次の情報を `InventoryCatalog` メッセージを公開するには、有効にします。 `cataloginventory/bulk_operations/async`. 管理者から、に移動します。 **ストア** /設定 > **カタログ** > **在庫** /管理者の一括操作とセット  `Run asynchronously`から **はい**.

## メッセージキューのテスト

Commerce から RabbitMQ に送信されるメッセージをテストするには：

1. キューを監視するには、AWSの RabbitMQ Web コンソールにログインします。
1. 管理者で、製品を作成します。
1. 在庫ソースを作成します。
1. 有効にする **ストア** /設定 > **カタログ** > **在庫** /管理者の一括操作/非同期で実行。
1. に移動します。 **カタログ** /製品。 グリッドから、上で作成した製品を選択し、 **在庫ソースの割り当て**.
1. クリック **保存して閉じる** をクリックしてプロセスを完了します。

   これで、RabbitMQ Web コンソールにメッセージが表示されます。

1. を開始します。 `async.operations.all` メッセージキューコンシューマー。

   ```bash
   bin/magento queue:consumers:start async.operations.all
   ```

これで、キューに格納されたメッセージが RabbitMQ Web コンソールで処理されるのがわかります。
管理で、製品の在庫ソースが変更されたことを確認します。
