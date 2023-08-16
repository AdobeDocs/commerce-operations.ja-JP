---
title: The [!DNL Cron] タブ
description: 詳しくは、 [!DNL Cron] タブ [!DNL Observation for Adobe Commerce].
exl-id: 66f5ffd6-4118-4534-b2d6-09c7a30e5e13
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# The [!DNL Cron] タブ

このタブでは、 [!DNL cron] 問題。

## [!UICONTROL Cron transaction duration in seconds]

![Cron トランザクションの時間（秒）](../../assets/tools/observation-for-adobe-commerce/cron-tab-1.jpg)

The **[!UICONTROL Cron transaction duration in seconds]** フレーム表示 [!DNL crons] トランザクションの期間（秒）。 これは、長いランタイムを持つトランザクションを表示します。 APM を詳しく調べると、トランザクション/操作が実行されている可能性のあるクエリの詳細が表示されます。

## [!UICONTROL MySQL Non-Sleeping Threads by Node]

![ノード別の MySQL 非スリープスレッド](../../assets/tools/observation-for-adobe-commerce/cron-tab-2.jpg)

The **[!UICONTROL MySQL Non-Sleeping Threads by Node]** frame は、選択した期間の MySQL 非スリープスレッドをノード別に表示します。

## [!UICONTROL SQL Trace count by path]

![パス別の SQL トレース数](../../assets/tools/observation-for-adobe-commerce/cron-tab-3.jpg)

The **[!UICONTROL SQL Trace count by path]** frame は、パス別に MySQL トレース数を調べます。これは、選択した期間にわたって SQL 文をトレースするのに役立ちます。

## [!UICONTROL Cron database call]

![Cron データベース呼び出し](../../assets/tools/observation-for-adobe-commerce/cron-tab-4.jpg)

The **[!UICONTROL Cron database call]** フレームは、 [!DNL crons] 選択した期間にわたるデータベースへの呼び出し。

## [!UICONTROL Cron schedule table locks]

![Cron スケジュールテーブルのロック](../../assets/tools/observation-for-adobe-commerce/cron-tab-5.jpg)

The **[!UICONTROL Cron schedule table locks]** フレームが見る [!DNL cron] スケジュールテーブルは、選択した期間でロックされます。

## [!UICONTROL Cron schedule clean cron fired]

![Cron スケジュールテーブルのロック](../../assets/tools/observation-for-adobe-commerce/cron-tab-6.jpg)

The **[!UICONTROL Cron schedule clean cron fired]** フレームは、 [!DNL crons] 選択した期間でクリーンアップされました。 このフレームにデータが表示されない場合は、 [!DNL crons] が正しく実行されている。 次の場合、 [!DNL cron] ジョブスケジュールはクリーンアップされません。 [!DNL crons] が最適に実行されず、実行に時間がかかる場合があります。

## [!UICONTROL Cron schedule clean records details table]

![Cron スケジュールのレコードのクリーン詳細テーブル](../../assets/tools/observation-for-adobe-commerce/cron-tab-7.jpg)

The **[!UICONTROL Cron schedule clean records details table]** テーブルには、レコードをクリーンアップするジョブの詳細が表示されます `cron_schedule` 選択した期間のテーブル。

## [!UICONTROL cron_schedule table updates]

![cron_schedule テーブルの更新](../../assets/tools/observation-for-adobe-commerce/cron-tab-8.jpg)

The **[!UICONTROL cron_schedule table updates]** フレームは、 [!DNL cron] スケジュール済みテーブルが、選択した期間に更新されます。 このテーブルの削除または更新での高いアクティビティは、 [!DNL crons]. また、 [!DNL crons] 実行および完了時にこのテーブルを更新します。このテーブルにアクティビティがなく、アクティビティがなく、 [!DNL crons] 設定済みの場合は、 [!DNL crons].

## [!UICONTROL Datastore Operations Tables]

![データストア操作テーブル](../../assets/tools/observation-for-adobe-commerce/cron-tab-9.jpg)

The **[!UICONTROL Datastore Operations Tables]** データベーステーブルの操作を参照します。次の操作が含まれます。 `SELECT`, `DELETE`、および `UPDATE` 選択した期間をまたいで。 このフレームは、操作頻度が最も高いデータベーステーブルを表示します。
