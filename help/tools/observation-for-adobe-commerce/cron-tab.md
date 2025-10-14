---
title: ' [!DNL Cron]  タブ'
description: ' [!DNL Cron]  の  [!DNL Observation for Adobe Commerce] タブについて説明します。'
exl-id: 66f5ffd6-4118-4534-b2d6-09c7a30e5e13
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# 「[!DNL Cron]」タブ

このタブでは、問題とその原因をすばやく特定 [!DNL cron] ます。

## [!UICONTROL Cron transaction duration in seconds]

![Cron トランザクション期間（秒単位） &#x200B;](../../assets/tools/observation-for-adobe-commerce/cron-tab-1.jpg)

**[!UICONTROL Cron transaction duration in seconds]** フレームには、トランザクション期間 [!DNL crons] 秒単位で表示されます。 実行時間が長いトランザクションが表示されます。 APM を詳しく調べると、トランザクション/操作で実行されているクエリの詳細が表示されます。

## [!UICONTROL MySQL Non-Sleeping Threads by Node]

![&#x200B; ノード別 MySQL Non Sleeping Threads](../../assets/tools/observation-for-adobe-commerce/cron-tab-2.jpg)

**[!UICONTROL MySQL Non-Sleeping Threads by Node]** のフレームには、選択した期間、ノード別の MySQL の非スリーピングスレッドが表示されます。

## [!UICONTROL SQL Trace count by path]

![&#x200B; パス別の SQL トレース数 &#x200B;](../../assets/tools/observation-for-adobe-commerce/cron-tab-3.jpg)

**[!UICONTROL SQL Trace count by path]** フレームは、パス別に MySQL トレースのカウントを調べます。これにより、選択した期間にわたって SQL ステートメントをトレースできます。

## [!UICONTROL Cron database call]

![Cron データベース呼び出 &#x200B;](../../assets/tools/observation-for-adobe-commerce/cron-tab-4.jpg)

**[!UICONTROL Cron database call]** フレームは、選択した期間におけるデータベースへの呼び出し [!DNL crons] 数を調べます。

## [!UICONTROL Cron schedule table locks]

![Cron スケジュール・テーブルのロック &#x200B;](../../assets/tools/observation-for-adobe-commerce/cron-tab-5.jpg)

**[!UICONTROL Cron schedule table locks]** 枠は、選択した期間 [!DNL cron] スケジュール・テーブルのロックを確認します。

## [!UICONTROL Cron schedule clean cron fired]

![Cron スケジュール・テーブルのロック &#x200B;](../../assets/tools/observation-for-adobe-commerce/cron-tab-6.jpg)

**[!UICONTROL Cron schedule clean cron fired]** フレームは、選択した期間にクリーンアップされた [!DNL crons] の数を調べます。 このフレームにデータが表示されない場合は、[!DNL crons] が正しく実行されていないことが原因である可能性があります。 [!DNL cron] ジョブ スケジュールがクリーンアップされない場合、[!DNL crons] は最適に実行されず、実行に時間がかかる場合があります。

## [!UICONTROL Cron schedule clean records details table]

![Cron スケジュールのクリーンレコードの詳細テーブル &#x200B;](../../assets/tools/observation-for-adobe-commerce/cron-tab-7.jpg)

**[!UICONTROL Cron schedule clean records details table]** テーブルには、選択した期間に `cron_schedule` テーブルからレコードを削除するジョブの詳細が表示されます。

## [!UICONTROL cron_schedule table updates]

![cron_schedule テーブルの更新 &#x200B;](../../assets/tools/observation-for-adobe-commerce/cron-tab-8.jpg)

**[!UICONTROL cron_schedule table updates]** フレームは、選択した期間におけるスケジュール済みテーブル [!DNL cron] 更新数を調べます。 このテーブルの削除や更新のアクティビティが多い場合、[!DNL crons] に問題がある可能性があります。 また、このテーブルは実行時および完了時に更新で [!DNL crons] ます。したがって、このテーブルでアクティビティが実行されておらず、[!DNL crons] が設定されている場合、[!DNL crons] に問題がある可能性があります。

## [!UICONTROL Datastore Operations Tables]

![&#x200B; データストア操作テーブル &#x200B;](../../assets/tools/observation-for-adobe-commerce/cron-tab-9.jpg)

**[!UICONTROL Datastore Operations Tables]** では、選択した期間の `SELECT`、`DELETE`、`UPDATE` などのデータベーステーブル操作を確認します。 このフレームは、最も高い操作頻度を持つデータベース・テーブルを示します。
