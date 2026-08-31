---
title: 「[!UICONTROL Redis]」タブ
description: ' [!DNL Observation for Adobe Commerce]の[!UICONTROL Redis] タブについて説明します。'
exl-id: 9c52350d-45a7-4afe-9dd7-c3968bd84d71
feature: Configuration, Observability
source-git-commit: 4caabd1578e56b74600441c9c779b7b2dfd06987
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# 「[!DNL Redis]」タブ

## [!UICONTROL Redis Node summary]

![Redis ノードの概要](../../assets/tools/observation-for-adobe-commerce/redis-tab-1.jpg)

**[!UICONTROL Redis Node summary]**&#x200B;には、環境内のすべてのノードが含まれます。 上記の例には、共有ステージング用のノードが含まれます。 実稼動には1つのプライマリおよび2つのセカンダリがあり、ステージングにも1つのプライマリおよび2つのセカンダリがあります。

## [!UICONTROL Redis node detail]

![Redis サーバーのパフォーマンス指標とノード設定の詳細](../../assets/tools/observation-for-adobe-commerce/redis-tab-2.jpg)

**[!UICONTROL Redis node detail]** フレームは、環境、[!DNL Redis]の役割、ソフトウェア バージョン、およびノード サイズを示します。

## [!UICONTROL Redis node roles timeline]

![Redis ノードの役割のタイムライン ](../../assets/tools/observation-for-adobe-commerce/redis-tab-3.jpg)

**[!UICONTROL Redis node roles timeline]** フレームは、特定の役割で[!DNL Redis] サービスが失われたことを示します。 行がディップした場合、その行が表す特定の役割がノードまたはノードを失ったことを示します。

## [!UICONTROL Connection to Redis]

![Redisへの接続](../../assets/tools/observation-for-adobe-commerce/redis-tab-4.jpg)

**[!UICONTROL Connection to Redis]** フレームには、[!DNL New Relic Redis] サンプルデータのnet.connectedClients値が表示されます。 [!DNL New Relic] アプリケーション （環境）とノードによる接続数が表示されます。

## [!UICONTROL Commands per second by node]

![ ノードごとの1秒あたりのコマンド ](../../assets/tools/observation-for-adobe-commerce/redis-tab-5.jpg)

**[!UICONTROL Commands per second by node]** フレームには、選択した時間枠に対する1秒あたりのノード別の[!DNL Redis] コマンドが表示されます。

## [!UICONTROL Redis % of memory used]

![使用メモリのRedis %です](../../assets/tools/observation-for-adobe-commerce/redis-tab-6.jpg)

**[!UICONTROL Redis % of memory used]** フレームは、[!DNL Redis] サーバーが使用している最大メモリの割合を示します。

## [!UICONTROL Redis used memory]

![Redisはメモリを使用しました](../../assets/tools/observation-for-adobe-commerce/redis-tab-7.jpg)

**[!UICONTROL Redis used memory]** フレームは、メモリのノード使用率をGB/MB単位で示しています。

## [!UICONTROL Redis changes since last db save]

![最後のdb保存以降のRedisの変更](../../assets/tools/observation-for-adobe-commerce/redis-tab-8.jpg)

[!DNL Redis]はメモリ常駐者で、情報をストレージに保存します。 **[!UICONTROL Redis changes since last db save]** フレームは、前回のデータベースがストレージに保存されてから発生したメモリの変更回数を示します。 [!DNL Redis's]の永続性について詳しくは、[Redisの永続性](https://redis.io/docs/latest/operate/oss_and_stack/management/persistence/)を参照してください。

## [!UICONTROL Redis synchronization from Log]

![ ログからのRedis同期](../../assets/tools/observation-for-adobe-commerce/redis-tab-9.jpg)

**[!UICONTROL Redis synchronization from Log]** フレームは、[!DNL Redis]の同期中に発生したエラーまたは同期の問題が原因で発生したエラーに焦点を当てています。 [!DNL Redis]について詳しくは、[[!DNL Redis]  ドキュメント ](https://redis.io/docs/)を参照してください。
