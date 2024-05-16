---
title: この [!DNL Cron] タブ
description: について説明します [!DNL Cron] タブ / [!DNL Observation for Adobe Commerce].
exl-id: 66f5ffd6-4118-4534-b2d6-09c7a30e5e13
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# この [!DNL Cron] タブ

このタブでは、の問題と原因をすばやく特定します [!DNL cron] 問題。

## [!UICONTROL Cron transaction duration in seconds]

![Cron トランザクション期間（秒）](../../assets/tools/observation-for-adobe-commerce/cron-tab-1.jpg)

この **[!UICONTROL Cron transaction duration in seconds]** フレーム表示 [!DNL crons] トランザクション期間（秒）。 実行時間が長いトランザクションが表示されます。 APM を詳しく調べると、トランザクション/操作で実行されているクエリの詳細が表示されます。

## [!UICONTROL MySQL Non-Sleeping Threads by Node]

![ノード別 MySQL ノンスリープThreads](../../assets/tools/observation-for-adobe-commerce/cron-tab-2.jpg)

この **[!UICONTROL MySQL Non-Sleeping Threads by Node]** フレームには、選択した期間、ノード別の MySQL の非スリーピングスレッドが表示されます。

## [!UICONTROL SQL Trace count by path]

![パス別の SQL トレース数](../../assets/tools/observation-for-adobe-commerce/cron-tab-3.jpg)

この **[!UICONTROL SQL Trace count by path]** フレームは、パス別に MySQL トレースのカウントを調べます。これにより、選択した期間にわたって SQL ステートメントをトレースできます。

## [!UICONTROL Cron database call]

![Cron データベース呼出し](../../assets/tools/observation-for-adobe-commerce/cron-tab-4.jpg)

この **[!UICONTROL Cron database call]** フレームは、次の数を調べます。 [!DNL crons] 選択した期間におけるデータベースへの呼び出し。

## [!UICONTROL Cron schedule table locks]

![Cron スケジュール・テーブル・ロック](../../assets/tools/observation-for-adobe-commerce/cron-tab-5.jpg)

この **[!UICONTROL Cron schedule table locks]** フレームは次を参照 [!DNL cron] 選択した期間、集計表がロックされます。

## [!UICONTROL Cron schedule clean cron fired]

![Cron スケジュール・テーブル・ロック](../../assets/tools/observation-for-adobe-commerce/cron-tab-6.jpg)

この **[!UICONTROL Cron schedule clean cron fired]** フレームは、次の数を調べます。 [!DNL crons] 選択した期間にクリーンアップしました。 このフレームにデータが表示されない場合は、に問題がある可能性があります。 [!DNL crons] 正常に実行しています。 次の場合 [!DNL cron] ジョブ スケジュールはクリーンアップされません。 [!DNL crons] は最適に実行されず、実行に時間がかかる場合があります。

## [!UICONTROL Cron schedule clean records details table]

![Cron スケジュールのクリーンレコードの詳細テーブル](../../assets/tools/observation-for-adobe-commerce/cron-tab-7.jpg)

この **[!UICONTROL Cron schedule clean records details table]** 表は、からレコードをクリーンアップするジョブの詳細を示しています `cron_schedule` 選択した期間のテーブル。

## [!UICONTROL cron_schedule table updates]

![cron_schedule テーブルの更新](../../assets/tools/observation-for-adobe-commerce/cron-tab-8.jpg)

この **[!UICONTROL cron_schedule table updates]** フレームは、次の数を調べます。 [!DNL cron] スケジュールされたテーブルは、選択した期間で更新されます。 このテーブルの削除や更新のアクティビティが多い場合、に問題がある可能性があります。 [!DNL crons]. また、 [!DNL crons] 実行および完了したら、このテーブルを更新します。これにより、このテーブルでアクティビティが発生せず、 [!DNL crons] が設定されています。に問題がある可能性があります。 [!DNL crons].

## [!UICONTROL Datastore Operations Tables]

![データストア操作テーブル](../../assets/tools/observation-for-adobe-commerce/cron-tab-9.jpg)

この **[!UICONTROL Datastore Operations Tables]** 次のようなデータベーステーブル操作を確認します `SELECT`, `DELETE`、および `UPDATE` 選択した期間。 このフレームは、最も高い操作頻度を持つデータベース・テーブルを示します。
