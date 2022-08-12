---
title: 「 [!UICONTROL Redis] タブ"
description: 詳しくは、 [!UICONTROL Redis] タブ [!DNL Observation for Adobe Commerce].
source-git-commit: 3f2a401bb916fc04405f21ba2acfc42f7defdccb
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# この [!DNL Redis] タブ

## [!UICONTROL Redis Node summary]

![Redis ノードの概要](../../assets/tools/observation-for-adobe-commerce/redis-tab-1.jpg)

この **[!UICONTROL Redis Node summary]** は、環境内のすべてのノードを含みます。 この例には、共有ステージング用のノードが含まれます。 実稼動環境には 1 つのプライマリと 2 つのセカンダリが存在し、ステージング環境には 1 つのプライマリと 2 つのセカンダリが存在します。

## [!UICONTROL Redis node detail]

![Redis ノードの詳細](../../assets/tools/observation-for-adobe-commerce/redis-tab-2.jpg)

この **[!UICONTROL Redis node detail]** frame は環境を示します。 [!DNL Redis] 役割、ソフトウェアのバージョン、およびノードサイズ。

## [!UICONTROL Redis node roles timeline]

![Redis ノードの役割のタイムライン](../../assets/tools/observation-for-adobe-commerce/redis-tab-3.jpg)

この **[!UICONTROL Redis node roles timeline]** frame は、 [!DNL Redis] 特定の役割のサービス 行が減少した場合、その行が表す特定の役割がノード（複数可）を失ったことを示します。

## [!UICONTROL Connection to Redis]

![Redis への接続](../../assets/tools/observation-for-adobe-commerce/redis-tab-4.jpg)

この **[!UICONTROL Connection to Redis]** frame は、 [!DNL New Relic Redis] サンプルデータ。 接続数を次の単位で表示します。 [!DNL New Relic] アプリケーション（環境）とノード。

## [!UICONTROL Commands per second by node]

![1 秒あたりのコマンド数（ノード別）](../../assets/tools/observation-for-adobe-commerce/redis-tab-5.jpg)

この **[!UICONTROL Commands per second by node]** frame は、 [!DNL Redis] 選択した期間の 1 秒あたりのノード別のコマンド数。

## [!UICONTROL Redis % of memory used]

![使用メモリの Redis %](../../assets/tools/observation-for-adobe-commerce/redis-tab-6.jpg)

この **[!UICONTROL Redis % of memory used]** frame は、 [!DNL Redis] サーバー。

## [!UICONTROL Redis used memory]

![Redis が使用したメモリ](../../assets/tools/observation-for-adobe-commerce/redis-tab-7.jpg)

この **[!UICONTROL Redis used memory]** frame は、メモリのノード使用量を GB/MB 単位で示します。

## [!UICONTROL Redis changes since last db save]

![前回の db 保存以降の変更を修正](../../assets/tools/observation-for-adobe-commerce/redis-tab-8.jpg)

[!DNL Redis] はメモリ常駐型で、情報をストレージに保存します。 この **[!UICONTROL Redis changes since last db save]** frame は、最後のデータベースがストレージに保存されてから発生したメモリに対する変更の数を示します。 [この情報](https://redis.io/docs/manual/persistence/) 説明 [!DNL Redis's] 永続性。

## [!UICONTROL Redis synchronization from Log]

![ログからの Redis 同期](../../assets/tools/observation-for-adobe-commerce/redis-tab-9.jpg)

この **[!UICONTROL Redis synchronization from Log]** frame は、次の間に発生したエラーに焦点を当てます。 [!DNL Redis] 同期または同期の問題が原因で発生するエラー。 詳しくは、 [Redis ドキュメント](https://redis.io/docs/).
