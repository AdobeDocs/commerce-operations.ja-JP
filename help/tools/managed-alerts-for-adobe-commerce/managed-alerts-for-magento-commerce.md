---
title: Adobe Commerceの管理アラート
description: Adobe Commerce on cloud infrastructure Pro プランアーキテクチャをご利用のお客様は、管理アラートを使用してサイトの正常性を把握できます。 クラウドインフラストラクチャー上のAdobe Commerce スタータープランアーキテクチャをご利用のお客様は、 [!DNL Apdex]  およびエラー率の条件に関するアラートのみを受け取ることができます。
feature: Observability, Support, Tools and External Services
role: Admin
exl-id: 3fc4b07f-4e27-4833-97a9-cf9741ae5648
source-git-commit: 4560e7d000ad8333c3089b8b5e8ffd25f5d31b67
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 0%

---

# Adobe Commerceの管理アラート


重要なダッシュボードとアラートを設定し、サイトが重要なストレージと [!DNL Apdex] ータレベル（アプリケーションとサービスの応答時間に対するユーザーの満足度）に達している時期を把握できるようにします。 これは、応答時間の遅延や停止に気づく前にアクションを実行するのに役立ちます。 以下に示す記事を使用して、アラートのトラブルシューティングを行うことができます。 アラートを使用する前に、まず通知チャネルを設定します。 Commerce on Cloud ガイドの [[!DNL New Relic]  通知チャネルの設定 &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/monitor/new-relic/new-relic-service) を参照してください。

>[!NOTE]
>
>Adobe Commerceのアラートポリシーの管理アラートが使用できない場合は、このアカウントが新しく作成されたか、最近設定されたこ [!DNL New Relic] が原因である可能性があります。 これらのアカウントにアラート・ポリシーを追加するプロセスは、毎週火曜日に実行されます。 次のプロセスを実行した翌日に、アラート・ポリシーを使用できるようになります。 ポリシーがまだ見つからない場合は、[Adobe Commerce サポートリクエストを送信 &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case) し、プロジェクト ID を含めます。

これらのアラートのトラブルシューティング手順を示すナレッジベース記事へのリンクについては、以下の表を参照してください。

* Adobe Commerceの管理アラート：CPU警告アラート
* Adobe Commerceの管理されたアラート：CPUの重大なアラート
* Managed alerts for Adobe Commerce:memory warning アラート
* Adobe Commerceの管理アラート：メモリ・クリティカル・アラート
* Adobe Commerceの管理アラート：[!DNL Apdex] 警告アラート
* Adobe Commerceの管理アラート：重大なアラート [!DNL Apdex] 通知
* Managed alerts for Adobe Commerce:disk warning アラート
* Adobe Commerceの管理アラート：disk critical アラート
* Adobe Commerceの管理アラート：MariaDB アラート
* Adobe Commerceの管理アラート：[!DNL Redis] memory warning アラート
* Adobe Commerceの管理アラート：[!DNL Redis] memory critical アラート

>[!NOTE]
>
>警告アラートと重要なアラートのしきい値の設定は、お客様ベース全体の過去のパフォーマンスデータを使用して行った調査に基づいており、Adobe Commerceのサポートチームとエンジニアリングチームからの最新のインサイトを示しています。 これらの閾値は、最新の継続的分析に基づいて変更される場合があることに注意してください。 一般的なアラートフローは、重大度の点で低いアラートから高いアラートを受信することです。 そのため、重大なアラートが表示される前に、警告アラートが表示される可能性があります。 トラブルシューティング手順については、記事へのリンクを参照してください。

| 重大度 | CPU | メモリ | ディスク | [!DNL Apdex] | MariaDB | [!DNL Redis] メモリ | トラブルシューティング記事 |
|----------|-----|--------|------|-------|---------|--------------|-------------------------|
| 警告 | ✅ |        |      |       |         |              | [Managed alerts for Adobe Commerce:CPUの警告アラート &#x200B;](managed-alerts-for-magento-commerce-cpu-warning-alert.md) |
| 重大 | ✅ |        |      |       |         |              | [Adobe Commerceの管理アラート：CPUのクリティカルアラート &#x200B;](managed-alerts-on-magento-commerce-cpu-critical-alert.md) |
| 警告 |     | ✅ |      |       |         |              | [Managed alerts for Adobe Commerce:memory warning アラート &#x200B;](managed-alerts-for-magento-commerce-memory-warning-alert.md) |
| 重大 |     | ✅ |      |       |         |              | [Managed alerts for Adobe Commerce:memory critical アラート &#x200B;](managed-alerts-on-magento-commerce-memory-critical-alert.md) |
| 警告 |     |        |      | ✅ |         |              | [Managed alerts for Adobe Commerce: [!DNL Apdex] warning アラート &#x200B;](managed-alerts-for-magento-commerce-apdex-warning-alert.md) |
| 重大 |     |        |      | ✅ |         |              | [Adobe Commerceの管理されたアラート： [!DNL Apdex]  重要なアラート &#x200B;](managed-alerts-for-magento-commerce-apdex-critical-alert.md) |
| 警告 |     |        | ✅ |       |         |              | [Managed alerts for Adobe Commerce:disk warning アラート &#x200B;](managed-alerts-for-magento-commerce-disk-warning-alert.md) |
| 重大 |     |        | ✅ |       |         |              | [Managed alerts for Adobe Commerce:disk critical アラート &#x200B;](managed-alerts-for-magento-commerce-disk-critical-alert.md) |
| 警告と重大 |     |        |      |       | ✅ |              | [Adobe Commerceの管理アラート：MariaDB アラート &#x200B;](managed-alerts-on-magento-commerce-mariadb-alerts.md) |
| 警告 |     |        |      |       |         | ✅ | [Managed alerts on Adobe Commerce: [!DNL Redis] memory warning アラート &#x200B;](managed-alerts-on-magento-commerce-redis-memory-warning-alert.md) |
| 重大 |     |        |      |       |         | ✅ | [Adobe Commerceの管理アラート： [!DNL Redis] memory critical アラート &#x200B;](managed-alerts-on-magento-commerce-redis-memory-critical-alert.md) |

## 管理されたアラートに設定されたアラートしきい値の確認

管理対象アラートに設定されているアラートしきい値は、New Relic アカウントから確認できます。 手順については、[&#x200B; 管理アラートによるパフォーマンスの監視 &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/monitor/new-relic/investigate/investigate-performance#monitor-performance-with-managed-alerts) を参照してください。
