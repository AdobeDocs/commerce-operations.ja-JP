---
title: 「[!DNL Cron]」タブ
description: '[!DNL Observation for Adobe Commerce]の「[!DNL Cron]」タブについて説明します。'
exl-id: 66f5ffd6-4118-4534-b2d6-09c7a30e5e13
feature: Configuration, Observability
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 4239b8a6-e74f-567d-a7a5-b98b9ead0ea4
    internal-label: Observability
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%
---
# 「[!DNL Cron]」タブ

このタブは、[!DNL cron]個の問題の問題と原因を迅速に特定する試みです。

## [!UICONTROL Cron transaction duration in seconds]

![Cron トランザクション時間（秒） ](../../assets/tools/observation-for-adobe-commerce/cron-tab-1.jpg)

**[!UICONTROL Cron transaction duration in seconds]** フレームには、[!DNL crons] トランザクション期間が秒単位で表示されます。 これにより、実行時間が長いトランザクションが表示されます。 APMの詳細では、トランザクション/オペレーションが実行している可能性のあるクエリの詳細が表示されます。

## [!UICONTROL MySQL Non-Sleeping Threads by Node]

![ ノード別のMySQL Non Sleeping Threads](../../assets/tools/observation-for-adobe-commerce/cron-tab-2.jpg)

**[!UICONTROL MySQL Non-Sleeping Threads by Node]** フレームには、選択した時間枠のノード別のMySQL非スリープスレッドが表示されます。

## [!UICONTROL SQL Trace count by path]

パス別![SQL トレース数](../../assets/tools/observation-for-adobe-commerce/cron-tab-3.jpg)

**[!UICONTROL SQL Trace count by path]** フレームは、MySQL トレース数をパス別に表示します。これは、選択した期間にわたってSQL ステートメントをトレースするのに役立ちます。

## [!UICONTROL Cron database call]

![Cron データベース呼び出し](../../assets/tools/observation-for-adobe-commerce/cron-tab-4.jpg)

**[!UICONTROL Cron database call]** フレームは、選択した期間におけるデータベースへの[!DNL crons]呼び出し回数を調べます。

## [!UICONTROL Cron schedule table locks]

![Cron スケジュール テーブルのロック ](../../assets/tools/observation-for-adobe-commerce/cron-tab-5.jpg)

**[!UICONTROL Cron schedule table locks]** フレームは、選択した時間枠で[!DNL cron]個のスケジュール テーブルのロックを確認します。

## [!UICONTROL Cron schedule clean cron fired]

![Cron スケジュール テーブルのロック ](../../assets/tools/observation-for-adobe-commerce/cron-tab-6.jpg)

**[!UICONTROL Cron schedule clean cron fired]** フレームは、選択した時間枠でクリーンアップされた[!DNL crons]の数を調べます。 このフレームにデータが表示されない場合は、[!DNL crons]が正しく実行されていないという問題を示している可能性があります。 [!DNL cron] ジョブ スケジュールがクリーニングされない場合、[!DNL crons]は最適に実行されず、実行に時間がかかる可能性があります。

## [!UICONTROL Cron schedule clean records details table]

![Cron スケジュールのクリーン レコードの詳細テーブル ](../../assets/tools/observation-for-adobe-commerce/cron-tab-7.jpg)

**[!UICONTROL Cron schedule clean records details table]** テーブルには、選択した期間にわたって`cron_schedule` テーブルからレコードをクリーニングするジョブの詳細が表示されます。

## [!UICONTROL cron_schedule table updates]

![cron_schedule テーブルの更新](../../assets/tools/observation-for-adobe-commerce/cron-tab-8.jpg)

**[!UICONTROL cron_schedule table updates]** フレームは、選択した期間における[!DNL cron]件のスケジュールされたテーブル更新の数を調べます。 このテーブルの削除または更新に関するアクティビティが多い場合は、[!DNL crons]に関する問題を示している可能性があります。 また、[!DNL crons]は、実行および完了時にこのテーブルを更新するので、このテーブルにアクティビティがなく、[!DNL crons]が設定されている場合、[!DNL crons]に問題が発生する可能性があります。

## [!UICONTROL Datastore Operations Tables]

![ データストア操作テーブル ](../../assets/tools/observation-for-adobe-commerce/cron-tab-9.jpg)

**[!UICONTROL Datastore Operations Tables]**&#x200B;は、選択した期間の`SELECT`、`DELETE`および`UPDATE`を含むデータベース テーブル操作を確認します。 このフレームは、データベースのテーブルに対して最も高い操作頻度を示しています。
