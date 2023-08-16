---
title: データ移行後の手順
description: を使用した後に実行する手順を説明します。 [!DNL Data Migration Tool] データをMagento1 からMagento2 に移行する場合。
exl-id: 00171c41-ccea-4ebe-8958-becb9aa09973
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '74'
ht-degree: 0%

---

# データ移行後の手順

移行を完了し、新しいMagento2 サイトを十分にテストした後、次のタスクを実行します。

* Magento1 をメンテナンスモードにし、すべての管理アクティビティを恒久的に停止します

* Magento2 cron ジョブを開始

* [すべてのMagento2 キャッシュタイプをフラッシュ](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [すべてのMagento2 のインデクサーを再インデックス化](../../../configuration/cli/manage-indexers.md#reindex)

* DNS およびロードバランサーを、Magento2 の本番ハードウェアを指すように変更します。
