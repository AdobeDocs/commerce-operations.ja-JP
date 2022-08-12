---
title: 「 [!UICONTROL Cron] タブ"
description: 詳しくは、 [!UICONTROL Cron] タブ [!DNL Observation for Adobe Commerce].
source-git-commit: 3c1e50b3bff1bd2b2760e2e763173275161b0044
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# この [!UICONTROL Cron] タブ

このタブでは、cron の問題の問題と原因をすばやく特定します。

## [!UICONTROL Cron transaction duration in seconds]

![Cron トランザクションの時間（秒）](../../assets/tools/observation-for-adobe-commerce/cron-tab-1.jpg)

この **[!UICONTROL Cron transaction duration in seconds]** frame は、crons トランザクションの期間を秒単位で表示します。 これは、長いランタイムを持つトランザクションを表示します。 APM を詳しく調べると、トランザクション/操作が実行されている可能性のあるクエリの詳細が表示されます。

## [!UICONTROL MySql Non-Sleeping Threads by Node]

![ノード別の MySql 非スリープスレッド](../../assets/tools/observation-for-adobe-commerce/cron-tab-2.jpg)

この **[!UICONTROL MySql Non-Sleeping Threads by Node]** frame は、選択した期間の MySql 非スリープスレッドをノード別に表示します。

## [!UICONTROL SQL Trace count by path]

![パス別の SQL トレース数](../../assets/tools/observation-for-adobe-commerce/cron-tab-3.jpg)

この **[!UICONTROL SQL Trace count by path]** frame は、パス別に MySql トレース数を調べます。これは、選択した期間にわたって SQL 文をトレースするのに役立ちます。

## [!UICONTROL Cron database call]

![Cron データベース呼び出し](../../assets/tools/observation-for-adobe-commerce/cron-tab-4.jpg)

この **[!UICONTROL Cron database call]** frame は、選択した期間にデータベースに対して呼び出された cron の数を調べます。

## [!UICONTROL Cron schedule table locks]

![Cron スケジュールテーブルのロック](../../assets/tools/observation-for-adobe-commerce/cron-tab-5.jpg)

この **[!UICONTROL Cron schedule table locks]** frame は、選択した期間にわたる cron スケジュールテーブルのロックを調べます。

## [!UICONTROL Cron schedule clean cron fired]

![Cron スケジュールテーブルのロック](../../assets/tools/observation-for-adobe-commerce/cron-tab-6.jpg)

この **[!UICONTROL Cron schedule clean cron fired]** frame は、選択した期間にクリーンアップされた cron の数を調べます。 このフレームにデータが表示されない場合は、Cron が正しく実行されていることに問題がある可能性があります。 cron ジョブスケジュールが消去されない場合、cron は最適に実行されず、実行に時間がかかる場合があります。

## [!UICONTROL Cron schedule clean records details table]

![Cron スケジュールのレコードのクリーン詳細テーブル](../../assets/tools/observation-for-adobe-commerce/cron-tab-7.jpg)

この **[!UICONTROL Cron schedule clean records details table]** テーブルには、レコードをクリーンアップするジョブの詳細が表示されます `cron_schedule` 選択した期間のテーブル。

## [!UICONTROL cron_schedule table updates]

![cron_schedule テーブルの更新](../../assets/tools/observation-for-adobe-commerce/cron-tab-8.jpg)

この **[!UICONTROL cron_schedule table updates]** frame は、選択した期間における cron 予定テーブルの更新数を調べます。 このテーブルの削除または更新でのアクティビティが高い場合は、cron の問題を示している可能性があります。 また、cron は、実行および完了時にこのテーブルを更新します。そのため、このテーブルにアクティビティがなく、cron が設定されている場合は、cron に問題がある可能性があります。

## [!UICONTROL Datastore Operations Tables]

![データストア操作テーブル](../../assets/tools/observation-for-adobe-commerce/cron-tab-9.jpg)

この **[!UICONTROL Datastore Operations Tables]** データベーステーブルの操作を参照します。以下が含まれます。 `SELECT`, `DELETE`、および `UPDATE` 選択した期間をまたいで。 このフレームは、操作頻度が最も高いデータベーステーブルを表示します。
