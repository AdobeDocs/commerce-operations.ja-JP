---
title: メッセージキューの管理
description: Adobe Commerceのコマンドラインからメッセージキューを管理する方法について説明します。
exl-id: 619e5df1-39cb-49b6-b636-618b12682d32
source-git-commit: 7610a5843b526a765dd35188722b7be8e6051049
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# メッセージキューの管理

cron ジョブまたは外部プロセスマネージャーを使用して、コマンドラインからメッセージキューを管理し、消費者がメッセージを取得していることを確認できます。 これは、RabbitMQ （AMQP）、Apache ActiveMQ Artemis （STOMP）、MySQL アダプタなど、サポートされているすべてのメッセージブローカーに適用されます。

## プロセス管理

Cron ジョブは、消費者を再起動するためのデフォルトのメカニズムです。 `cron`によって開始されたプロセスは、指定された数のメッセージを消費してから終了します。 `cron`を再実行すると、コンシューマーが再起動します。

次の例は、実行中のコンシューマーの`crontab`設定を示しています。

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
>メッセージキューを確認する頻度は、ビジネスロジックと利用可能なシステムリソースによって異なります。 一般的に、カタログの更新など、リソースを集約するプロセスよりも、新規顧客を確認し、ウェルカムメールをより頻繁に送信する必要があります。 ビジネスニーズに応じて`cron`のスケジュールを定義する必要があります。
>
>この設定は、管理者ストア / 設定/設定/詳細/システム/Cron グループの設定オプション（コンシューマー）で行うことができます。
>
>Commerceでの`cron`の使用について詳しくは、[cron](../cli/configure-cron-jobs.md)の設定と実行を参照してください。

[ スーパーバイザー](https://supervisord.readthedocs.io/en/latest/)などのプロセスマネージャーを使用して、プロセスのステータスを監視することもできます。 マネージャーはコマンドラインを使用して、必要に応じてプロセスを再起動できます。

## 設定

### デフォルトでの動作

- Cron ジョブ `consumers_runner`が有効です
- Cron ジョブ `consumers_runner`は、定義済みのすべてのコンシューマーを実行します
- 各コンシューマーは、メッセージ 10000処理してから終了します

>[!INFO]
>
>Adobe Commerce ストアがCloud Platform上でホストされている場合は、[`CRON_CONSUMERS_RUNNER`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=ja#cron_consumers_runner)を使用して`consumers_runner` cron ジョブを設定します。

### 特定の設定

`/app/etc/env.php` ファイルを編集して、cron ジョブ `consumers_runner`を設定します。

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

- `cron_run` - `consumers_runner` cron ジョブを有効または無効にするブール値（デフォルト = `true`）。
- `max_messages` – 各コンシューマーが終了前に処理する必要があるメッセージの最大数（デフォルト = `10000`）。 お勧めしませんが、0を使用して、消費者が終了するのを防ぐことができます。 消費者がメッセージキューからメッセージを処理する方法を設定するには、[`consumers_wait_for_messages`](../reference/config-reference-envphp.md#consumerswaitformessages)を参照してください。
- `consumers` – 実行するコンシューマーを指定する文字列の配列。 空の配列は&#x200B;*all*&#x200B;個の消費者を実行します。
- `multiple_processes` - プロセス数で実行するコンシューマーを指定するキーと値のペアの配列。 Commerce 2.4.4以降でサポートされています。

  >[!INFO]
  >
  >MySQLが操作するキューで複数のコンシューマーを実行することはお勧めしません。 AMQP （RabbitMQ）またはSTOMP （ActiveMQ Artemis）への切り替えについて詳しくは、[MySQLから外部ブローカーへのメッセージキューの変更](https://developer.adobe.com/commerce/php/development/components/message-queues/#change-message-queue-from-mysql-to-external-brokers)を参照してください。

  >[!INFO]
  >
  >Adobe Commerce ストアがCloud Platform上でホストされている場合は、[`CONSUMERS_WAIT_FOR_MAX_MESSAGES`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=ja#consumers_wait_for_max_messages)を使用して、消費者がメッセージキューからメッセージを処理する方法を設定します。

  >[!NOTE]
  >
  >ActiveMQ Artemis （STOMP）は、Adobe Commerce 2.4.5以降で導入されました。

[開始メッセージキューコンシューマー](../cli/start-message-queues.md)を参照してください。
