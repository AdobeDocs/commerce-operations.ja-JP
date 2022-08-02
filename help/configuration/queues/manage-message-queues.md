---
title: メッセージキューの管理
description: Adobe Commerceのコマンドラインからメッセージキューを管理する方法を説明します。
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---


# メッセージキューの管理

CRON ジョブや外部プロセスマネージャーを使用して、コマンドラインからメッセージキューを管理し、コンシューマーがメッセージを確実に取得できるようにします。

## プロセス管理

Cron ジョブは、コンシューマーを再起動するデフォルトのメカニズムです。 プロセスの開始者 `cron` 指定された数のメッセージを消費してから終了します。 再実行中 `cron` コンシューマーを再起動します。

次の例は、 `crontab` 実行するコンシューマーの設定：

> /app/code/Magento/MessageQueue/etc/crontab.xml

```xml
...
<job name="consumers_runner" instance="Magento\MessageQueue\Model\Cron\ConsumersRunner" method="run">
    <schedule>* * * * *</schedule>
</job>
...
```

>[!INFO]
>
>メッセージキューの確認頻度は、ビジネスロジックと使用可能なシステムリソースに応じて異なります。 一般に、新規顧客を確認し、カタログの更新など、リソースを集中的に消費するプロセスよりも頻繁にお知らせメールを送信する必要があります。 次を定義する必要があります。 `cron` は、ビジネスニーズに応じてスケジュールを設定します。
>
>この設定は、グループの管理ストア/設定/設定/詳細/システム/ Cron 設定オプションでおこなえます。消費者
>
>詳しくは、 [cron の設定と実行](../cli/configure-cron-jobs.md) を使用する方法の詳細 `cron` コマースを使用します。

また、 [スーパーバイザー](http://supervisord.org/index.html) プロセスのステータスを監視する。 マネージャーは、必要に応じて、コマンドラインを使用してプロセスを再起動できます。

## 設定

### デフォルトの動作

- Cron ジョブ `consumers_runner` 有効
- Cron ジョブ `consumers_runner` すべての定義済みコンシューマーを実行
- 各コンシューマーは10000件のメッセージを処理してから終了します

>[!INFO]
>
>Adobe Commerceストアがクラウドプラットフォームでホストされている場合、 [`CRON_CONSUMERS_RUNNER`](https://devdocs.magento.com/cloud/env/variables-deploy.html#cron_consumers_runner) を設定するには、以下を実行します。 `consumers_runner` cron ジョブ。

### 特定の設定

を編集します。 `/app/etc/env.php` cron ジョブを設定するファイル `consumers_runner`.

```php
...
    'cron_consumers_runner' => [
        'cron_run' => false,
        'max_messages' => 20000,
        'consumers' => [
            'consumer1',
            'consumer2',
        ],
        'multiple_processes' => [
            'consumer1' => 4
        ]
    ],
...
```

- `cron_run` - `consumers_runner` cron ジョブ ( デフォルト= `true`) をクリックします。
- `max_messages`  — 各コンシューマーが処理する必要があるメッセージの最大数（デフォルトは=） `10000`) をクリックします。 お勧めしませんが、0 を使用して、消費者が終了するのを防ぐことができます。 詳しくは、 [`consumers_wait_for_messages`](../reference/config-reference-envphp.md#consumerswaitformessages) コンシューマーがメッセージキューからのメッセージを処理する方法を設定する場合。
- `consumers`  — 実行するコンシューマーを指定する文字列の配列。 空の配列が実行されます *すべて* 消費者
- `multiple_processes`  — 実行するコンシューマーをプロセス数で指定するキーと値のペアの配列。

   >[!INFO]
   >
   >MySQL 操作のキューで複数のコンシューマーを実行することはお勧めしません。 詳しくは、 [メッセージキューを MySQL から AMQP に変更](https://developer.adobe.com/commerce/php/development/components/message-queues/#change-message-queue-from-mysql-to-amqp) を参照してください。

   >[!INFO]
   >
   >Adobe Commerceストアがクラウドプラットフォームでホストされている場合、 [`CONSUMERS_WAIT_FOR_MAX_MESSAGES`](https://devdocs.magento.com/cloud/env/variables-deploy.html#consumers_wait_for_max_messages) コンシューマーがメッセージキューからのメッセージを処理する方法を設定する場合。

詳しくは、 [メッセージキューコンシューマーを開始](../cli/start-message-queues.md).
