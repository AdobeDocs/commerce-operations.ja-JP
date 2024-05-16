---
title: Cron ジョブ
description: cron グループと、カスタム cron ジョブの作成について説明します。
exl-id: a9d83af7-9979-4653-adc9-30ffeb13a5ce
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# Cron ジョブ

これらのトピックでは、カスタム cron ジョブと、オプションでカスタム cron グループを設定する方法について説明します。 Commerce拡張機能で、スケジュールされたタスクを定期的に実行する必要がある場合は、次のトピックを使用して cron を設定できます _ジョブ_ （スケジュールされたタスク）と、オプションで cron _グループ_&#x200B;同時にカスタムタスクを実行します。

Commerceが提供する cron グループを使用する場合、カスタム cron グループを定義する必要はありません。ただし、cron ジョブを別のスケジュールで実行したり、すべてを一緒に実行したりする場合は、cron グループを定義する必要があります

Commerce アプリケーションは次の cron グループを提供します。

- `default`（ほとんどの cron ジョブを含む）
- `index`、更新 [インデクサー](../cli/manage-indexers.md)
- `consumers`。メッセージキューを実行します [消費者](../cli/start-message-queues.md)
- これらのトピックは、Adobe Commerceでのみ使用できます
   - `staging`。が実行されます [ステージング関連](https://docs.magento.com/user-guide/cms/content-staging.html) タスク
   - `catalog_event`:target ルールと買い物かごルールのタスクを実行します
