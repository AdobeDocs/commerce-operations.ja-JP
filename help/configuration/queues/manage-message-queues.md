---
title: メッセージキューの管理
description: Adobe Commerceのコマンドラインからメッセージキューを管理する方法について説明します。
exl-id: 619e5df1-39cb-49b6-b636-618b12682d32
source-git-commit: 8dce1f1e961ec02d7783a7423a51a7d4567dce79
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# メッセージキューの管理

Cron ジョブまたは外部プロセスマネージャーを使用して、コマンドラインからメッセージキューを管理し、コンシューマーがメッセージを確実に取得できるようにします。

## プロセス管理

Cron ジョブは、コンシューマーを再起動するデフォルトのメカニズムです。 によって開始されたプロセス `cron` 指定された数のメッセージを使用してから終了します。 再実行 `cron` コンシューマーを再起動します。

次の例は、 `crontab` コンシューマーを実行するための設定：

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
>メッセージキューの確認頻度は、ビジネスロジックと使用可能なシステムリソースによって異なります。 一般的に、カタログの更新など、リソースを集中的に消費するプロセスよりも頻繁に、新しい顧客を確認し、ようこそメールを送信します。 以下を定義する必要があります。 `cron` は、ビジネスニーズに応じてスケジュールを設定します。
>
>これは、グループ : コンシューマーの管理ストア /設定/設定/詳細/ システム / Cron 設定オプションで設定できます。
>
>参照： [Cron の設定と実行](../cli/configure-cron-jobs.md) の使用の詳細情報 `cron` （Commerceを使用）。

次のようなプロセスマネージャーを使用することもできます [監督者](https://supervisord.readthedocs.io/en/latest/) プロセスのステータスを監視します。 マネージャーは、コマンドラインを使用して、必要に応じてプロセスを再起動できます。

## 設定

### デフォルトの動作

- Cron ジョブ `consumers_runner` 有効
- Cron ジョブ `consumers_runner` 定義されたすべてのコンシューマーを実行
- 各コンシューマーは 10000 メッセージを処理してから終了します

>[!INFO]
>
>Adobe Commerce ストアがクラウドプラットフォームでホストされている場合は、 [`CRON_CONSUMERS_RUNNER`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#cron_consumers_runner) を設定します `consumers_runner` cron ジョブ。

### 特定の設定

を編集する `/app/etc/env.php` cron ジョブを設定するためのファイル `consumers_runner`.

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

- `cron_run` - パラメーターの有効/無効を切り替えるブール値 `consumers_runner` cron ジョブ（デフォルト = `true`）に設定します。
- `max_messages`  – 各消費者が終了するまでに処理する必要があるメッセージの最大数（デフォルト = `10000`）に設定します。 推奨はしませんが、0 を使用して消費者が終了するのを防ぐことができます。 参照： [`consumers_wait_for_messages`](../reference/config-reference-envphp.md#consumerswaitformessages) コンシューマーがメッセージキューからのメッセージを処理する方法を設定します。
- `consumers`  – 実行するコンシューマを指定する文字列の配列。 空の配列が実行される *all* 消費者。
- `multiple_processes` - プロセス数で実行するコンシューマーを指定するキーと値のペアの配列。 Commerce 2.4.4 以降でサポートされます。

  >[!INFO]
  >
  >MySQL 操作キューで複数のコンシューマーを実行することはお勧めしません。 参照： [メッセージキューを MySQL から AMQP に変更](https://developer.adobe.com/commerce/php/development/components/message-queues/#change-message-queue-from-mysql-to-amqp) を参照してください。

  >[!INFO]
  >
  >Adobe Commerce ストアがクラウドプラットフォームでホストされている場合は、 [`CONSUMERS_WAIT_FOR_MAX_MESSAGES`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#consumers_wait_for_max_messages) コンシューマーがメッセージキューからのメッセージを処理する方法を設定します。

参照： [メッセージキューコンシューマーの開始](../cli/start-message-queues.md).
