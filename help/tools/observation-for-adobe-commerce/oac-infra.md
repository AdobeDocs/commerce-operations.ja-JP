---
title: 「 [!UICONTROL Infra] タブ"
description: この [!UICONTROL Infra] 「 」タブでは、インフラストラクチャの問題と原因を分離できます。
source-git-commit: b0d80d97f60b24bc801063dc484f3a495cf0a036
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---


# この [!UICONTROL Infra] タブ

この **[!UICONTROL Infra]** 「 」タブでは、インフラストラクチャの問題と原因を分離できます。 「 」タブに表示されるフレームについて詳しく説明します。

## [!UICONTROL Service Alerts – Infrastructure Alerts by Application name]

![サービスアラート](../../assets/tools/observation-for-adobe-commerce/service-alerts.jpg)

この **[!UICONTROL Service Alerts – Infrastructure Alerts by Application name]** グラフは、 [!DNL New Relic] インフラストラクチャエージェント これにより、多くのデプロイメントに関連付けられている、サービスの再起動が表示されます。

## [!UICONTROL Inode usage by mount]

![マウント別の i ノード使用量](../../assets/tools/observation-for-adobe-commerce/inode-usage-mount.jpg)

この **[!UICONTROL Inode usage by mount]** frame は、選択した期間をまたいだマウント別の inode 使用量を示します。 空き容量が多い場合でも、ノードが inode を使い果たした場合は、使用可能なストレージが不足していることが示されます。 ファイル（特に小さいファイル）を削除すると、領域が解放され、inode が使用可能になります。

## [!UICONTROL vCPU tier view over timeline GREATER 2 weeks]

![タイムライン上の vCPU 層ビュー 2 週間以上](../../assets/tools/observation-for-adobe-commerce/vCPU-tier.jpg)

この **[!UICONTROL vCPU tier view over timeline GREATER 2 weeks]** frame は、選択した期間の vCPU 層ビューを 2 週間以上表示します。 このフレームは、 [!DNL New Relic] アプリケーション名が表示されます。

## [!UICONTROL vCPU tier view over timeline]

![タイムライン上の vCPU 層ビュー](../../assets/tools/observation-for-adobe-commerce/vcpu-tier-24.jpg)

この **[!UICONTROL vCPU tier view over timeline]** frame は、選択した期間（24 時間以上）の vCPU 層ビューを表示します。 このフレームは、 [!DNL New Relic] アプリケーション名が表示されます。 クラスターのアップサイズとダウンサイズの両方が表示されます。

## [!UICONTROL vCPU tier view over timeline BY NODE]

![NODE 別のタイムライン上の vCPU 層ビュー](../../assets/tools/observation-for-adobe-commerce/infra_by_node.png)

この **[!UICONTROL vCPU tier view over timeline BY NODE]** frame は、選択した期間の vCPU 層ビューをノード別に表示します。 このフレームは、ノードの損失を検出する場合や、ノードが大きくなったり小さくなったりする場合に役立ちます。 タイムライン上の vCPU 層ビュー BY NODE は、24 時間未満のタイムラインを確認する必要があります。

## [!UICONTROL Instance details]

![インスタンスの詳細](../../assets/tools/observation-for-adobe-commerce/instance-details.jpg)

この **[!UICONTROL Instance details]** 表には、各インスタンスの詳細が表示されます [!DNL New Relic] アプリケーション。

## [!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]

![非レスポンシブノード](../../assets/tools/observation-for-adobe-commerce/non-responsive-node.jpg)

この **[!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]** frame は、一定期間、非レスポンシブノードを表示します。
