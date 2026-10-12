---
title: Cron ジョブ
description: Adobe Commerceでcron グループとカスタム cron ジョブを作成する方法について説明します。 スケジュールされたタスクの設定とcron グループの設定を確認します。
exl-id: a9d83af7-9979-4653-adc9-30ffeb13a5ce
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
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
source-wordcount: '179'
ht-degree: 0%
---
# Cron ジョブ

これらのトピックでは、カスタム cron ジョブとオプションでカスタム cron グループを設定する方法について説明します。 Commerce拡張機能でスケジュールされたタスクを定期的に実行する必要がある場合は、これらのトピックを使用して、cron _ジョブ_ （スケジュールされたタスク）と、必要に応じてcron _グループ_&#x200B;を設定し、同時にカスタムタスクを実行できます。

Commerceが提供するcron グループを使用する場合、カスタム cron グループを定義する必要はありません。ただし、cron ジョブを別のスケジュールで実行する場合や、すべてのジョブを一緒に実行する場合は、cron グループを定義する必要があります

Commerce アプリケーションには、次のcron グループが用意されています。

- `default`。ほとんどのcron ジョブが含まれています
- `index`が[&#x200B; インデクサー](../cli/manage-indexers.md)を更新します
- メッセージ キュー[consumers](../cli/start-message-queues.md)を実行する`consumers`
- これらのトピックは、Adobe Commerceでのみ使用できます
  - `staging`。[&#x200B; ステージング関連](https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/staging/content-staging) タスクを実行します
  - ターゲットと買い物かごのルールのタスクを実行する`catalog_event`
