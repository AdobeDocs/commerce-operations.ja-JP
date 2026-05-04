---
title: メッセージキューコンシューマーを開始
description: Adobe Commerce非同期処理のメッセージキューコンシューマーを開始する方法を説明します。 消費者の管理とB2B機能の設定についてご紹介します。
exl-id: fd6edb24-8ebe-4b67-8a03-6cc759b60fa8
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# メッセージキューコンシューマーを開始

{{file-system-owner}}

Inventory managementの一括処理やRESTの一括処理、非同期エンドポイントなどの非同期処理を有効にするには、[ メッセージキューコンシューマー](../queues/consumers.md)を開始する必要があります。 B2B機能を有効にするには、複数の消費者を開始する必要があります。 カスタムコンシューマーを開始する必要がある場合もあります。

すべての消費者のリストを表示するには：

```shell
bin/magento queue:consumers:list
```

メッセージキューコンシューマーを開始するには：

```shell
bin/magento queue:consumers:start [--max-messages=<value>] [--batch-size=<value>] [--single-thread] [--area-code=<value>] [--multi-process=<value>] <consumer_name>
```

使用可能なすべてのメッセージを消費した後、コマンドは終了します。 手動またはcron ジョブを使用して、コマンドを再度実行できます。 `magento queue:consumers:start` コマンドの複数のインスタンスを実行して、大規模なメッセージキューを処理することもできます。 例えば、コマンドに`&`を追加してバックグラウンドで実行し、プロンプトに戻ってコマンドの実行を続行できます。

```shell
bin/magento queue:consumers:start <consumer_name> &
```

コマンドオプション、パラメーター、値について詳しくは、_コマンドラインツールのリファレンス_&#x200B;のCommerce セクションの[`queue:consumers:start`](../../tools/reference/commerce-on-premises.md#queueconsumersstart)を参照してください。

>[!INFO]
>
>`--multi-process` オプションは`queue:consumers:start` コマンドに存在しますが、並行プロセスでコンシューマーを実行するには、`/app/etc/env.php`で[`multiple_processes`](../queues/manage-message-queues.md#configuration) オプションを設定します。 それ以外の場合、`queue:consumers:start`が`--multi-process` オプションで呼び出された場合は、1つのスレッドでのみ機能します。
