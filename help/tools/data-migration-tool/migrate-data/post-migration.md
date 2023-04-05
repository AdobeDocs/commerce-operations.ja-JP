---
title: データ移行後の手順
description: を使用した後に実行する手順を説明します。 [!DNL Data Migration Tool] データをMagento1 からMagento2 に移行する場合
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
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
