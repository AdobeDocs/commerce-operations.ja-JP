---
title: データ移行後の手順
description: 「 [!DNL Data Migration Tool] 」を使用してMagento 1からMagento 2にデータを移行した後に実行する手順について説明します。
exl-id: 00171c41-ccea-4ebe-8958-becb9aa09973
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 0%

---

# データ移行後の手順

移行を完了し、新しいMagento 2 サイトを徹底的にテストしたら、次のタスクを実行します。

* Magento 1をメンテナンスモードにし、すべての管理者アクティビティを完全に停止する

* Magento 2 cron ジョブを開始

* [すべてのMagento 2のキャッシュタイプをフラッシュする](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [すべてのMagento 2 インデクサーのインデックスを再作成](../../../configuration/cli/manage-indexers.md#reindex)

* DNSおよびロードバランサーをMagento 2実稼動ハードウェアを指すように変更する
