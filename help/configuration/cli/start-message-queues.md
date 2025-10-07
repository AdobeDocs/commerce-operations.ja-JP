---
title: メッセージキューコンシューマーの開始
description: Adobe Commerceの非同期操作用にメッセージキューコンシューマーを開始する方法について説明します。 消費者管理と B2B 機能のセットアップについて説明します。
exl-id: fd6edb24-8ebe-4b67-8a03-6cc759b60fa8
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# メッセージキューコンシューマーの開始

{{file-system-owner}}

Inventory management一括アクション、REST 一括エンドポイントおよび非同期エンドポイントなどの非同期操作を有効にするには、[&#x200B; メッセージキューコンシューマー &#x200B;](../queues/consumers.md) を起動する必要があります。 B2B 機能を有効にするには、複数のコンシューマーを開始する必要があります。 また、サードパーティモジュールでは、カスタムコンシューマーを開始する必要が生じる場合があります。

すべてのコンシューマのリストを表示する手順は、次のとおりです。

```bash
bin/magento queue:consumers:list
```

メッセージキューコンシューマーを開始するには：

```bash
bin/magento queue:consumers:start [--max-messages=<value>] [--batch-size=<value>] [--single-thread] [--area-code=<value>] [--multi-process=<value>] <consumer_name>
```

使用可能なすべてのメッセージを使用した後、コマンドは終了します。 手動で、または cron ジョブを使用して、もう一度コマンドを実行できます。 `magento queue:consumers:start` コマンドの複数のインスタンスを実行して、大きなメッセージキューを処理することもできます。 例えば、コマンドに `&` を追加して、バックグラウンドで実行し、プロンプトに戻り、次のコマンドを実行し続けることができます。

```bash
bin/magento queue:consumers:start <consumer_name> &
```

コマンドのオプション、パラメーター、値について詳しくは、[`queue:consumers:start`](../../tools/reference/commerce-on-premises.md#queueconsumersstart) コマンドラインツールリファレンス _のCommerceの節の_ を参照してください。

>[!INFO]
>
>`--multi-process` コマンドには `queue:consumers:start` オプションがありますが、並列プロセスでコンシューマーを実行するには、[`multiple_processes`](../queues/manage-message-queues.md#configuration) で `/app/etc/env.php` オプションを設定します。 それ以外の場合、`queue:consumers:start` オプションを指定して `--multi-process` を呼び出すと、単一のスレッドでのみ動作します。
