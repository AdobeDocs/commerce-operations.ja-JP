---
title: メッセージキューコンシューマーの開始
description: メッセージキューコンシューマーを開始する方法を説明します。
exl-id: fd6edb24-8ebe-4b67-8a03-6cc759b60fa8
source-git-commit: c9e7a8926c7003d34a62d2defb62c09d58919ddd
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# メッセージキューコンシューマーの開始

{{file-system-owner}}

を開始する必要があります [メッセージキューコンシューマー](../queues/consumers.md) Inventory management一括アクション、REST 一括エンドポイントおよび非同期エンドポイントなどの非同期操作を有効にする。 B2B 機能を有効にするには、複数のコンシューマーを開始する必要があります。 また、サードパーティモジュールでは、カスタムコンシューマーを開始する必要が生じる場合があります。

すべてのコンシューマのリストを表示する手順は、次のとおりです。

```bash
bin/magento queue:consumers:list
```

メッセージキューコンシューマーを開始するには：

```bash
bin/magento queue:consumers:start [--max-messages=<value>] [--batch-size=<value>] [--single-thread] [--area-code=<value>] [--multi-process=<value>] <consumer_name>
```

使用可能なすべてのメッセージを使用した後、コマンドは終了します。 手動で、または cron ジョブを使用して、もう一度コマンドを実行できます。 の複数のインスタンスを実行することもできます `magento queue:consumers:start` 大きなメッセージキューを処理するコマンド。 例えば、 `&` コマンドをバックグラウンドで実行するには、プロンプトに戻り、次のコマンドを実行し続けます。

```bash
bin/magento queue:consumers:start <consumer_name> &
```

参照： [`queue:consumers:start`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento-commerce.html#queueconsumersstart) のCommerce セクション内 _コマンドラインツールリファレンス_ コマンドオプション、パラメーター、値について詳しくは、「」を参照してください。

>[!INFO]
>
>この `--multi-process` オプションがに存在する `queue:consumers:start` コマンドを使用しますが、並列プロセスでコンシューマーを実行するには、 [`multiple_processes`](../queues/manage-message-queues.md#configuration) オプション： `/app/etc/env.php`. そうでない場合、 `queue:consumers:start` は、以下で呼び出されます。 `--multi-process` オプションは、単一のスレッドでのみ機能します。
