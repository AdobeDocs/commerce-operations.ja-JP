---
title: Cron ジョブ
description: cron グループと、Adobe Commerceでカスタム cron ジョブを作成する方法を説明します。 スケジュールされたタスクの設定と cron グループ設定の確認
exl-id: a9d83af7-9979-4653-adc9-30ffeb13a5ce
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---

# Cron ジョブ

これらのトピックでは、カスタム cron ジョブと、オプションでカスタム cron グループを設定する方法について説明します。 Commerce拡張機能で、スケジュールされたタスクを定期的に実行する必要がある場合は、これらのトピックを使用して、カスタムタスクを同時に実行する cron _ジョブ_ （スケジュールされたタスク）とオプションで cron _グループ_ を設定できます。

Commerceが提供する cron グループを使用する場合、カスタム cron グループを定義する必要はありません。ただし、cron ジョブを別のスケジュールで実行したり、すべてを一緒に実行したりする場合は、cron グループを定義する必要があります

Commerce アプリケーションは次の cron グループを提供します。

- ほとんどの cron ジョブを含む `default`
- `index` インデクサー [&#x200B; を更新する &#x200B;](../cli/manage-indexers.md)
- メッセージキュー `consumers` コンシューマー [&#x200B; を実行する &#x200B;](../cli/start-message-queues.md)
- これらのトピックは、Adobe Commerceでのみ使用できます
   - `staging` ステージング関連 [&#x200B; タスクを実行する &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/staging/content-staging)
   - ターゲットと買い物かごルールのタスクを実行する `catalog_event`
