---
title: この [!UICONTROL Redis] タブ
description: について説明します [!UICONTROL Redis] タブ / [!DNL Observation for Adobe Commerce].
exl-id: 9c52350d-45a7-4afe-9dd7-c3968bd84d71
feature: Configuration, Observability
source-git-commit: 06f015139683f319f11317f8d7f0029cbd2548e3
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# この [!DNL Redis] タブ

## [!UICONTROL Redis Node summary]

![Redis ノードの概要](../../assets/tools/observation-for-adobe-commerce/redis-tab-1.jpg)

この **[!UICONTROL Redis Node summary]** は、環境内のすべてのノードを含みます。 上記の例には、共有ステージング用のノードが含まれています。 実稼動環境には 1 つのプライマリと 2 つのセカンダリがあり、ステージング環境にも 1 つのプライマリと 2 つのセカンダリがあります。

## [!UICONTROL Redis node detail]

![Redis ノードの詳細](../../assets/tools/observation-for-adobe-commerce/redis-tab-2.jpg)

この **[!UICONTROL Redis node detail]** frame は環境を示します。 [!DNL Redis] ロール、ソフトウェア・バージョン、ノード・サイズ。

## [!UICONTROL Redis node roles timeline]

![Redis ノードロールのタイムライン](../../assets/tools/observation-for-adobe-commerce/redis-tab-3.jpg)

この **[!UICONTROL Redis node roles timeline]** フレームは、の損失を示します [!DNL Redis] サービス、特に役割。 行が減っている場合は、その行が表す特定の役割が 1 つまたは複数のノードを失ったことを示します。

## [!UICONTROL Connection to Redis]

![Redis への接続](../../assets/tools/observation-for-adobe-commerce/redis-tab-4.jpg)

この **[!UICONTROL Connection to Redis]** frame は、から net.connectedClients 値を表示します [!DNL New Relic Redis] サンプルデータ。 接続数が次の基準で表示されます [!DNL New Relic] アプリケーション（環境）とノード。

## [!UICONTROL Commands per second by node]

![1 秒あたりのコマンド数（ノード別）](../../assets/tools/observation-for-adobe-commerce/redis-tab-5.jpg)

この **[!UICONTROL Commands per second by node]** フレームは、 [!DNL Redis] 選択した期間、1 秒あたりのノード数でコマンドを処理します。

## [!UICONTROL Redis % of memory used]

![使用メモリの Redis %](../../assets/tools/observation-for-adobe-commerce/redis-tab-6.jpg)

この **[!UICONTROL Redis % of memory used]** frame は、によって使用される最大メモリの割合を示します [!DNL Redis] サーバー。

## [!UICONTROL Redis used memory]

![Redis 使用メモリ](../../assets/tools/observation-for-adobe-commerce/redis-tab-7.jpg)

この **[!UICONTROL Redis used memory]** フレームは、メモリのノード使用量を GB/MB 単位で示します。

## [!UICONTROL Redis changes since last db save]

![最後に db を保存してから redis が変更されました](../../assets/tools/observation-for-adobe-commerce/redis-tab-8.jpg)

[!DNL Redis] はメモリに常駐し、情報をストレージに保存します。 この **[!UICONTROL Redis changes since last db save]** frame は、最後のデータベースがストレージに保存された後にメモリに加えられた変更の回数を示します。 こちらを参照してください [Redis 永続性](https://redis.io/docs/latest/operate/oss_and_stack/management/persistence/) 詳しくは、 [!DNL Redis's] 永続性。

## [!UICONTROL Redis synchronization from Log]

![ログからの Redis 同期](../../assets/tools/observation-for-adobe-commerce/redis-tab-9.jpg)

この **[!UICONTROL Redis synchronization from Log]** フレームは、次の期間に発生したエラーに焦点を当てています [!DNL Redis] 同期または同期の問題が原因で発生するエラー。 について詳しくは、 [!DNL Redis]を参照してください。 [[!DNL Redis] マニュアル](https://redis.io/docs/).
