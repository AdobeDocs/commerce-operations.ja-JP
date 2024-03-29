---
title: The [!DNL Infra] タブ
description: The [!DNL Infra] 「 」タブでは、インフラストラクチャの問題と原因を分離できます。
exl-id: 45f24177-3264-4848-99bc-951be32c1f7b
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# The [!DNL Infra] タブ

The **[!DNL Infra]** 「 」タブでは、インフラストラクチャの問題と原因を分離できます。 「 」タブに表示されるフレームについて詳しく説明します。

## [!UICONTROL Service Alerts – Infrastructure Alerts by Application name]

![サービスアラート](../../assets/tools/observation-for-adobe-commerce/service-alerts.jpg)

The **[!UICONTROL Service Alerts – Infrastructure Alerts by Application name]** グラフは、 [!DNL New Relic] インフラストラクチャエージェント これにより、多くのデプロイメントに関連付けられている、サービスの再起動が表示されます。

## [!UICONTROL Inode usage by mount]

![マウント別の i ノード使用量](../../assets/tools/observation-for-adobe-commerce/inode-usage-mount.jpg)

The **[!UICONTROL Inode usage by mount]** フレーム表示 [!DNL inode] 選択した期間をまたいだマウント別の使用状況。 ノードが使い果たした場合は、ストレージの空き容量が多い可能性がありますが、 [!DNL inodes]に設定すると、使用可能なストレージが不足していることが示されます。 ファイル（特に小さいファイル）を削除すると、空き容量が増え、 [!DNL inodes] 使用可能

## [!UICONTROL vCPU tier view over timeline GREATER 2 weeks]

![タイムライン上の vCPU 層ビュー 2 週間以上](../../assets/tools/observation-for-adobe-commerce/vCPU-tier.jpg)

The **[!UICONTROL vCPU tier view over timeline GREATER 2 weeks]** frame は、選択した期間の vCPU 層ビューを 2 週間以上表示します。 このフレームでは、 [!DNL New Relic] アプリケーション名が表示されます。

## [!UICONTROL vCPU tier view over timeline]

![タイムライン上の vCPU 層ビュー](../../assets/tools/observation-for-adobe-commerce/vcpu-tier-24.jpg)

The **[!UICONTROL vCPU tier view over timeline]** frame は、選択した期間（24 時間以上）の vCPU 層ビューを表示します。 このフレームでは、 [!DNL New Relic] アプリケーション名が表示されます。 クラスターのアップサイズとダウンサイズの両方が表示されます。

## [!UICONTROL vCPU tier view over timeline BY NODE]

![NODE 別のタイムライン上の vCPU 層ビュー](../../assets/tools/observation-for-adobe-commerce/infra_by_node.png)

The **[!UICONTROL vCPU tier view over timeline BY NODE]** frame は、選択した期間の vCPU 層ビューをノード別に表示します。 このフレームは、ノードの損失を検出する場合や、ノードが大きくなったり小さくなったりする場合に役立ちます。 タイムライン上の vCPU 層ビュー BY NODE は、24 時間未満のタイムラインを確認する必要があります。

## [!UICONTROL Instance details]

![インスタンスの詳細](../../assets/tools/observation-for-adobe-commerce/instance-details.jpg)

The **[!UICONTROL Instance details]** 表には、各インスタンスの詳細が表示されます [!DNL New Relic] アプリケーション。

## [!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]

![非レスポンシブノード](../../assets/tools/observation-for-adobe-commerce/non-responsive-node.jpg)

The **[!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]** frame は、一定期間、非レスポンシブノードを表示します。
