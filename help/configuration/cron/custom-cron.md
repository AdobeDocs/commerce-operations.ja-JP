---
title: Cron ジョブ
description: cron グループと、カスタム cron ジョブの作成について説明します。
exl-id: a9d83af7-9979-4653-adc9-30ffeb13a5ce
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# Cron ジョブ

これらのトピックでは、カスタム cron ジョブと、オプションでカスタム cron グループを設定する方法について説明します。 Commerce拡張機能で、スケジュールされたタスクを定期的に実行する必要がある場合は、これらのトピックを使用して、カスタムタスクを同時に実行する cron _ジョブ_ （スケジュールされたタスク）とオプションで cron _グループ_ を設定できます。

Commerceが提供する cron グループを使用する場合、カスタム cron グループを定義する必要はありません。ただし、cron ジョブを別のスケジュールで実行したり、すべてを一緒に実行したりする場合は、cron グループを定義する必要があります

Commerce アプリケーションは次の cron グループを提供します。

- ほとんどの cron ジョブを含む `default`
- [ インデクサー ](../cli/manage-indexers.md) を更新する `index`
- メッセージキュー [ コンシューマー ](../cli/start-message-queues.md) を実行する `consumers`
- これらのトピックは、Adobe Commerceでのみ使用できます
   - [ ステージング関連 ](https://experienceleague.adobe.com/ja/docs/commerce-admin/content-design/staging/content-staging) タスクを実行する `staging`
   - ターゲットと買い物かごルールのタスクを実行する `catalog_event`
