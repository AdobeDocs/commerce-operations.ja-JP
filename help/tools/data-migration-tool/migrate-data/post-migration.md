---
title: データ移行後の手順
description: を使用した後に実行する手順を説明します。 [!DNL Data Migration Tool] データをMagento1 からMagento2 に移行する場合
source-git-commit: b5a2c362b09de993e1dc196bdda90e74cf4a8ba2
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 0%

---


# データ移行後の手順

移行を完了し、新しいMagento2 サイトを十分にテストした後、次のタスクを実行します。

* Magento1 をメンテナンスモードにし、すべてを永久に停止します [管理者](https://glossary.magento.com/admin) アクティビティ

* Magento2 cron ジョブを開始

* [すべてのMagento2 キャッシュタイプをフラッシュ](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-cache.html#clean-and-flush-cache-types)

* [すべてのMagento2 のインデクサーを再インデックス化](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html#reindex)

* DNS およびロードバランサーを、Magento2 の本番ハードウェアを指すように変更します。
