---
title: Managed alerts for Adobe Commerce:Disk warning アラート
description: この記事では、 [!DNL New Relic] でAdobe Commerceの警告ディスクアラートを受け取った場合のトラブルシューティング手順を説明します。 この問題を修正するには、直ちに対処する必要があります。
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
exl-id: 90ea4384-97aa-499d-93c1-b40c3a4eed42
source-git-commit: 8fa8e72252cc80637be229bba5a7fac20cbdd28b
workflow-type: tm+mt
source-wordcount: '545'
ht-degree: 0%

---

# Managed alerts for Adobe Commerce:Disk warning アラート

この記事では、Adobe Commerce in [!DNL New Relic] で警告ディスクアラートが表示された場合のトラブルシューティング手順を説明します。 この問題を修正するには、直ちに対処する必要があります。 選択したアラート通知チャネルに応じて、アラートは次のようになります。

![disk warning アラート ](../../assets/managed-alerts/disk-warning-magento-managed.png){width="500"}

## 影響を受ける製品とバージョン

* クラウドインフラストラクチャー上のAdobe Commerce、Pro プランアーキテクチャ。

## 問題

[!DNL New Relic]Adobe Commerceの Managed アラート [ にサインアップし、1 つ以上のアラートしきい値を超えた場合、](managed-alerts-for-magento-commerce.md) でアラートが届きます。 これらのアラートは、サポートおよびエンジニアリングのインサイトを使用して、標準セットをお客様に提供するために、Adobeで開発されました。

<u> **動け！**</u>

* このアラートがクリアされるまで、スケジュールされている展開を中止します。
* サイトが応答しない、または完全に応答しなくなった場合は、すぐにサイトをメンテナンスモードにします。 手順については、『Commerce インストールガイド』の [ メンテナンスモードの有効化または無効化 ](https://experienceleague.adobe.com/ja/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) を参照してください。 トラブルシューティングのためにサイトに引き続きアクセスできるように、IP を除外 IP アドレスリストに追加してください。 手順については、『Commerce インストールガイド』の [ 除外 IP アドレスのリストの管理 ](https://experienceleague.adobe.com/ja/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses) を参照してください。

<u> **やめて！**</u>

* 追加のマーケティングキャンペーンを開始すると、サイトに追加のページビューが表示される場合があります。
* インデクサーや追加の Cron を実行すると、CPUやディスクにさらに負荷がかかる場合があります。
* 主要な管理タスク（Commerce管理者、データの読み込み/書き出し）を実行します。
* キャッシュをクリアします。 アラートの原因を調査して解決する前に「回避」アクションのいずれかを行った場合、（まだサイトの停止が発生していない場合は）サイトが応答しなくなる可能性があります。

## 解決策

原因の特定とトラブルシューティングを行うには、次の手順に従います。

1. [!DNL New Relic] では、ディスクの使用率を最も高く確認します。 手順については、**[!UICONTROL Storage]** Infrastructure 監視ホスト ページ：[[!DNL New Relic]  タブ [!UICONTROL Storage] の ](https://docs.newrelic.com/docs/infrastructure/infrastructure-data/infrastructure-ui-pages/infra-hosts-ui-page/#storage) のタブを参照してください。
   * ディスクの使用量が徐々に増加する [!DNL New Relic] 合は、次のオプションを試してください。
      * ディスク領域の割り当てを調整してディスク領域を最適化しています。 Commerce手順については、Cloud ガイドの [ ディスク容量の管理 ](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/storage/manage-disk-space) を参照してください。 また、より多くのディスク容量をリクエストする必要が生じる場合があります（Adobe アカウントチームにお問い合わせください）。
      * MySQL のディスク領域をクリアします。 手順については、[MySQL のディスク容量が少ない ](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud) を参照してください。
      * ディスク使用量が急激に増加している [!DNL New Relic] 合は、ディレクトリ内のファイルが非常に急速に増加する原因となった問題が存在する可能性があります。 次のチェックを実行します。
         1. CLI/ターミナルで次のコマンドを実行して、ディスクの空き領域全体を確認し、問題を特定します。`df -h`
         1. ディスク使用量が予想外に大きく、増加しているディレクトリを特定したら、影響を受けるファイルシステムを確認する必要があります。 次の例は、ファイルディレクトリ `pub/media/` を確認する方法を示しています。 これは、Adobe Commerceがログや大きなメディアファイルの保存に使用するディレクトリです。 ただし、予期しないディスク使用量を示すディレクトリに対して、次のコマンドを実行する必要があります：`du -sch ~/pub/media/*`。

端末からの出力で、ディスク使用量が急激に増加しているこれらのディレクトリの 1 つにファイルが表示されていて、そのファイルの内容が不要であることがわかっている場合は、ファイルを削除することを検討してください。 この操作に不安がある場合は、[Adobe Commerce サポートチケットを送信 ](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case) してください。
