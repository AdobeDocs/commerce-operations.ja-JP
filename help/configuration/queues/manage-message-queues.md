---
title: メッセージキューの管理
description: Adobe Commerceのコマンドラインからメッセージキューを管理する方法について説明します。
exl-id: 619e5df1-39cb-49b6-b636-618b12682d32
source-git-commit: 47525e8d8379061b254bfa90ab46e27a1ee2f524
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# メッセージキューの管理

Cron ジョブまたは外部プロセスマネージャーを使用して、コマンドラインからメッセージキューを管理し、コンシューマーがメッセージを確実に取得できるようにします。 これは、RabbitMQ （AMQP）、Apache ActiveMQ Artemis （STOMP）、MySQL アダプターなど、サポートされるすべてのメッセージブローカーに適用されます。

## プロセス管理

Cron ジョブは、コンシューマーを再起動するデフォルトのメカニズムです。 `cron` によって開始されたプロセスは、指定された数のメッセージを使用してから終了します。 `cron` を再実行すると、コンシューマーが再起動します。

次の例は、コンシューマーを実行するための `crontab` の設定を示しています。

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
>メッセージキューの確認頻度は、ビジネスロジックと使用可能なシステムリソースによって異なります。 一般的に、カタログの更新など、リソースを集中的に消費するプロセスよりも頻繁に、新しい顧客を確認し、ようこそメールを送信します。 ビジネスニーズに応じて、`cron` のスケジュールを定義する必要があります。
>
>これは、グループ : コンシューマーの管理ストア /設定/設定/詳細/ システム / Cron 設定オプションで設定できます。
>
>Commerceでの [&#x200B; の使用について詳しくは、](../cli/configure-cron-jobs.md)Cron の設定と実行 `cron` を参照してください。

[Supervisor](https://supervisord.readthedocs.io/en/latest/) などのプロセスマネージャーを使用して、プロセスのステータスを監視することもできます。 マネージャーは、コマンドラインを使用して、必要に応じてプロセスを再起動できます。

## 設定

### デフォルトの動作

- Cron ジョブ `consumers_runner` が有効化されています
- Cron ジョブ `consumers_runner` 定義されたすべてのコンシューマーを実行
- 各コンシューマーは 10000 メッセージを処理してから終了します

>[!INFO]
>
>Adobe Commerce ストアがクラウドプラットフォーム上にホストされている場合は、[`CRON_CONSUMERS_RUNNER`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=ja#cron_consumers_runner) を使用して `consumers_runner` cron ジョブを設定します。

### 特定の設定

`/app/etc/env.php` ファイルを編集して、cron ジョブ `consumers_runner` を設定します。

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

- `cron_run` - `consumers_runner` cron ジョブを有効または無効にするブール値（デフォルトは `true`）。
- `max_messages` – 各消費者が終了するまでに処理する必要があるメッセージの最大数（デフォルト = `10000`）。 推奨はしませんが、0 を使用して消費者が終了するのを防ぐことができます。 コンシューマーがメッセージキューからのメッセージを処理する方法を設定する [`consumers_wait_for_messages`](../reference/config-reference-envphp.md#consumerswaitformessages) 法を参照してください。
- `consumers` – 実行するコンシューマーを指定する文字列の配列。 空の配列が *all* コンシューマーを実行します。
- `multiple_processes` - プロセス数で実行するコンシューマーを指定するキーと値のペアの配列。 Commerce 2.4.4 以降でサポートされます。

  >[!INFO]
  >
  >MySQL 操作キューで複数のコンシューマーを実行することはお勧めしません。 AMQP （RabbitMQ）または STOMP （ActiveMQ Artemis）への切り替えについて詳しくは、[MySQL から外部ブローカーへのメッセージキューの変更 &#x200B;](https://developer.adobe.com/commerce/php/development/components/message-queues/#change-message-queue-from-mysql-to-external-brokers) を参照してください。

  >[!INFO]
  >
  >Adobe Commerce ストアがクラウドプラットフォーム上にホストされている場合は、[`CONSUMERS_WAIT_FOR_MAX_MESSAGES`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=ja#consumers_wait_for_max_messages) を使用して、コンシューマーがメッセージキューからのメッセージを処理する方法を設定します。

  >[!NOTE]
  >
  >ActiveMQ Artemis （STOMP）は、Adobe Commerce 2.4.6 以降のバージョンで導入されました。

[&#x200B; メッセージキューコンシューマーの開始 &#x200B;](../cli/start-message-queues.md) を参照してください。
