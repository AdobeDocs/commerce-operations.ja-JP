---
title: Postとデータの移行手順
description: を使用してMagento 1 からMagento 2 にデータを移行した後に  [!DNL Data Migration Tool]  るべき手順を説明します。
exl-id: 00171c41-ccea-4ebe-8958-becb9aa09973
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 0%

---

# Postとデータの移行手順

移行を完了し、新しいMagento2 サイトを十分にテストしたら、次の作業を実行します。

* Magento 1 をメンテナンスモードにして、すべての管理者アクティビティを完全に停止する

* Magento 2 cron ジョブの開始

* [すべてのMagento 2 キャッシュ タイプをフラッシュします。](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [すべてのMagento 2 インデクサーの再インデックス化](../../../configuration/cli/manage-indexers.md#reindex)

* DNS とロードバランサーを変更して、Magento2 の実稼動ハードウェアを指すようにします。
