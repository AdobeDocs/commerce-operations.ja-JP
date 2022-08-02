---
title: Cron ジョブ
description: cron グループと、カスタム cron ジョブの作成について説明します。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---


# Cron ジョブ

このトピックでは、カスタム cron ジョブの設定方法と、オプションでカスタム cron グループの設定方法について説明します。 Commerce 拡張機能で定期的に実行するスケジュールされたタスクが必要な場合は、次のトピックを使用して cron を設定できます _ジョブ_ （スケジュール済みタスク）と（オプションで cron） _グループ_：カスタムタスクを同時に実行します。

コマースで提供される Cron グループを使用する場合、カスタム Cron グループを定義する必要はありません。ただし、cron ジョブを別のスケジュールで実行する場合や、すべてを同時に実行する場合は、cron グループを定義する必要があります

Commerce アプリケーションは、次の cron グループを提供します。

- `default`：ほとんどの cron ジョブを含みます。
- `index`を更新します。 [indexers](../cli/manage-indexers.md)
- `consumers`（メッセージキューを実行） [消費者](../cli/start-message-queues.md)
- これらのトピックは、Adobe Commerceでのみ利用できます
   - `staging`：実行 [ステージング関連](https://docs.magento.com/user-guide/cms/content-staging.html) タスク
   - `catalog_event`：ターゲットと買い物かごのルールのタスクを実行します。
