---
title: 「[!UICONTROL Redis]」タブ
description: ' [!DNL Observation for Adobe Commerce] の「[!UICONTROL Redis]」タブについて説明します。'
exl-id: 9c52350d-45a7-4afe-9dd7-c3968bd84d71
feature: Configuration, Observability
source-git-commit: 06f015139683f319f11317f8d7f0029cbd2548e3
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# 「[!DNL Redis]」タブ

## [!UICONTROL Redis Node summary]

![Redis ノードの概要 ](../../assets/tools/observation-for-adobe-commerce/redis-tab-1.jpg)

**[!UICONTROL Redis Node summary]** は、環境内のすべてのノードを含みます。 上記の例には、共有ステージング用のノードが含まれています。 実稼動環境には 1 つのプライマリと 2 つのセカンダリがあり、ステージング環境にも 1 つのプライマリと 2 つのセカンダリがあります。

## [!UICONTROL Redis node detail]

![Redis ノードの詳細 ](../../assets/tools/observation-for-adobe-commerce/redis-tab-2.jpg)

**[!UICONTROL Redis node detail]** のフレームは、環境、[!DNL Redis] の役割、ソフトウェアのバージョン、ノードサイズを示します。

## [!UICONTROL Redis node roles timeline]

![Redis ノードロールのタイムライン ](../../assets/tools/observation-for-adobe-commerce/redis-tab-3.jpg)

**[!UICONTROL Redis node roles timeline]** のフレームは、特定の役割 [!DNL Redis] サービスが失われたことを示しています。 行が減っている場合は、その行が表す特定の役割が 1 つまたは複数のノードを失ったことを示します。

## [!UICONTROL Connection to Redis]

![Redis との連携 ](../../assets/tools/observation-for-adobe-commerce/redis-tab-4.jpg)

**[!UICONTROL Connection to Redis]** フレームには、[!DNL New Relic Redis] のサンプル データから net.connectedClients 値が表示されます。 アプリケーション（環境）とノードご [!DNL New Relic] の接続数が表示されます。

## [!UICONTROL Commands per second by node]

![1 秒あたりのコマンド数（ノード別） ](../../assets/tools/observation-for-adobe-commerce/redis-tab-5.jpg)

**[!UICONTROL Commands per second by node]** のフレームには、選択した期間の 1 秒あたりのノード数で [!DNL Redis] のコマンドが表示されます。

## [!UICONTROL Redis % of memory used]

![ 使用されるメモリの Redis %](../../assets/tools/observation-for-adobe-commerce/redis-tab-6.jpg)

**[!UICONTROL Redis % of memory used]** フレームは、[!DNL Redis] サーバが使用する最大メモリの割合を示します。

## [!UICONTROL Redis used memory]

![Redis 使用メモリ ](../../assets/tools/observation-for-adobe-commerce/redis-tab-7.jpg)

**[!UICONTROL Redis used memory]** のフレームは、メモリのノード使用量を GB/MB 単位で示しています。

## [!UICONTROL Redis changes since last db save]

![ 最後にデータベースを保存してから Redis が変更されました ](../../assets/tools/observation-for-adobe-commerce/redis-tab-8.jpg)

[!DNL Redis] はメモリに常駐し、情報をストレージに保存します。 **[!UICONTROL Redis changes since last db save]** フレームは、最後のデータベースがストレージに保存された以降にメモリに対して発生した変更の数を示します。 永続性について詳しくは、[Redis 永続性 ](https://redis.io/docs/latest/operate/oss_and_stack/management/persistence/) を参照 [!DNL Redis's] てください。

## [!UICONTROL Redis synchronization from Log]

![ ログからの Redis 同期 ](../../assets/tools/observation-for-adobe-commerce/redis-tab-9.jpg)

**[!UICONTROL Redis synchronization from Log]** フレームでは、同期中に発生したエラーや、同期 [!DNL Redis] 問題が原因で発生したエラーに焦点を当てます。 [!DNL Redis] について詳しくは、[[!DNL Redis]  ドキュメント ](https://redis.io/docs/) を参照してください。
