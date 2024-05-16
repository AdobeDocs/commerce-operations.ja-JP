---
title: この [!DNL Infra] タブ
description: この [!DNL Infra] tab は、インフラストラクチャの問題の問題と原因を分離します。
exl-id: 45f24177-3264-4848-99bc-951be32c1f7b
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---

# この [!DNL Infra] タブ

この **[!DNL Infra]** tab は、インフラストラクチャの問題の問題と原因を分離します。 さらに、タブに表示されるフレームについて説明します。

## [!UICONTROL Service Alerts – Infrastructure Alerts by Application name]

![サービスアラート](../../assets/tools/observation-for-adobe-commerce/service-alerts.jpg)

この **[!UICONTROL Service Alerts – Infrastructure Alerts by Application name]** グラフ：によって収集されたサービスアラートを表示 [!DNL New Relic] インフラストラクチャエージェント。 これにより、サービスの再起動が表示され、多くはデプロイメントに関連しています。

## [!UICONTROL Inode usage by mount]

![マウントによる inode の使用](../../assets/tools/observation-for-adobe-commerce/inode-usage-mount.jpg)

この **[!UICONTROL Inode usage by mount]** フレーム表示 [!DNL inode] 選択した期間におけるマウントによる使用。 十分な空きストレージがある場合でも、ノードが不足した場合には [!DNL inodes]使用可能なストレージが不足していることが示されます。 ファイル（特に小さいファイル）を削除すると、領域とサイズの両方が解放されます [!DNL inodes] 使用可能。

## [!UICONTROL vCPU tier view over timeline GREATER 2 weeks]

![タイムラインに対する vCPU 層の表示 2 週間以上](../../assets/tools/observation-for-adobe-commerce/vCPU-tier.jpg)

この **[!UICONTROL vCPU tier view over timeline GREATER 2 weeks]** フレームには、選択した期間（2 週間を超える）の vCPU 階層ビューが表示されます。 このフレームは、に割り当てられた vCPU の数を調べます。 [!DNL New Relic] アプリケーション名が表示されます。

## [!UICONTROL vCPU tier view over timeline]

![vCPU 階層ビュー（タイムラインを超える）](../../assets/tools/observation-for-adobe-commerce/vcpu-tier-24.jpg)

この **[!UICONTROL vCPU tier view over timeline]** フレームには、選択した期間（24 時間を超える）の vCPU 階層ビューが表示されます。 このフレームは、に割り当てられた vCPU の数を調べます。 [!DNL New Relic] アプリケーション名が表示されます。 クラスターのアップサイズとダウンサイズの両方が表示されます。

## [!UICONTROL vCPU tier view over timeline BY NODE]

![ノード別タイムラインの vCPU 層ビュー](../../assets/tools/observation-for-adobe-commerce/infra_by_node.png)

この **[!UICONTROL vCPU tier view over timeline BY NODE]** フレームには、選択した期間の vCPU 階層ビューがノード別に表示されます。 このフレームは、ノードの損失を検出する場合や、ノードがアップサイズまたはダウンサイズされる場合に役立ちます。 ノード別のタイムラインの vCPU 階層ビューは、24 時間未満のタイムラインを表示する必要があります。

## [!UICONTROL Instance details]

![インスタンスの詳細](../../assets/tools/observation-for-adobe-commerce/instance-details.jpg)

この **[!UICONTROL Instance details]** 次の表に、各インスタンスの詳細を示します [!DNL New Relic] アプリケーション。

## [!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]

![non-responsive-node](../../assets/tools/observation-for-adobe-commerce/non-responsive-node.jpg)

この **[!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]** フレームは、ある期間にわたって応答しないノードを表示します。
