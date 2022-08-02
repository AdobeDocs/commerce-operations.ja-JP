---
title: メッセージキューコンシューマーを開始
description: メッセージキューコンシューマーを開始する方法を説明します。
source-git-commit: 02f02393878d04b4a0fcdae256ac1ac5dd13b7f6
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---


# メッセージキューコンシューマーを開始

{{file-system-owner}}

Inventory managementの一括アクションや REST の一括および非同期エンドポイントなどの非同期操作を有効にするには、メッセージキューコンシューマーを開始する必要があります。 B2B 機能を有効にするには、複数のコンシューマーを開始する必要があります。 また、サードパーティモジュールでは、カスタムコンシューマーを開始する必要が生じる場合があります。

すべてのコンシューマーのリストを表示するには：

```bash
bin/magento queue:consumers:list
```

メッセージ・キュー・コンシューマを開始するには、次の手順に従います。

```bash
bin/magento queue:consumers:start [--max-messages=<value>] [--batch-size=<value>] [--single-thread] [--area-code=<value>] [--multi-process=<value>] <consumer_name>
```

使用可能なすべてのメッセージを消費すると、コマンドは終了します。 コマンドは、手動で、または cron ジョブで再度実行できます。 また、 `magento queue:consumers:start` 大きなメッセージキューを処理するコマンド 例えば、 `&` バックグラウンドで実行するコマンドに戻り、プロンプトに戻って、コマンドの実行を続けます。

```bash
bin/magento queue:consumers:start <consumer_name> &
```

詳しくは、 [キュー:consumers:開始](https://devdocs.magento.com/guides/v2.4/reference/cli/magento-commerce.html#queueconsumersstart) ( _コマンドラインツールリファレンス_ コマンドのオプション、パラメータ、値の詳細については、を参照してください。

>[!INFO]
>
>この `--multi-process` オプションが `queue:consumers:start` コマンドを使用しますが、並列プロセスでコンシューマーを実行するには、 [`multiple_processes`](../queues/manage-message-queues.md#configuration) オプション `/app/etc/env.php`. それ以外の場合は、 `queue:consumers:start` が `--multi-process` オプションを指定した場合、単一のスレッドでのみ機能します。
