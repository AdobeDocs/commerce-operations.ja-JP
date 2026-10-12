---
title: データ移行後の手順
description: '[!DNL Data Migration Tool]を使用してMagento 1からMagento 2にデータを移行した後に実行する手順について説明します。'
exl-id: 00171c41-ccea-4ebe-8958-becb9aa09973
topic: Commerce, Migration
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
source-wordcount: '84'
ht-degree: 0%
---
# データ移行後の手順

移行を完了し、新しいMagento 2 サイトを徹底的にテストしたら、次のタスクを実行します。

* Magento 1をメンテナンスモードにし、すべての管理者アクティビティを完全に停止する

* Magento 2 cron ジョブを開始

* [すべてのMagento 2 キャッシュタイプをフラッシュする](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [すべてのMagento 2 インデクサーのインデックスを再作成](../../../configuration/cli/manage-indexers.md#reindex)

* DNSおよびロードバランサーを変更して、Magento 2実稼動ハードウェアを指すようにします
