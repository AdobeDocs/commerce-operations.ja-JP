---
title: Cron ジョブ
description: cron グループと、カスタム cron ジョブの作成について説明します。
exl-id: a9d83af7-9979-4653-adc9-30ffeb13a5ce
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# Cron ジョブ

このトピックでは、カスタム cron ジョブの設定方法と、オプションでカスタム cron グループの設定方法について説明します。 Commerce 拡張機能で定期的に実行するスケジュールされたタスクが必要な場合は、次のトピックを使用して cron を設定できます _ジョブ_ （スケジュール済みタスク）と（オプションで cron） _グループ_：カスタムタスクを同時に実行します。

コマースで提供される Cron グループを使用する場合、カスタム Cron グループを定義する必要はありません。ただし、Cron ジョブを別のスケジュールで実行したい場合や、すべてを一緒に実行したい場合は、Cron グループを定義する必要があります

Commerce アプリケーションは、次の CRON グループを提供します。

- `default`：ほとんどの cron ジョブを含みます。
- `index`を更新します。 [インデクサー](../cli/manage-indexers.md)
- `consumers`（メッセージキューを実行） [消費者](../cli/start-message-queues.md)
- これらのトピックは、Adobe Commerceでのみ使用できます
   - `staging`（実行） [ステージング関連](https://docs.magento.com/user-guide/cms/content-staging.html) タスク
   - `catalog_event`：ターゲットと買い物かごのルールのタスクを実行します。
