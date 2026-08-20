---
title: Adobe Commerceのアラートの管理
description: Adobe Commerce on cloud infrastructure Pro プランアーキテクチャをご利用のお客様は、マネージドアラートを使用して、サイトの健全性を把握できます。 Adobe Commerce on cloud infrastructure スタータープラン アーキテクチャのお客様は、 [!DNL Apdex] およびエラー率の条件に関するアラートのみを受け取ります。
feature: Observability, Support, Tools and External Services
role: Admin
exl-id: 3fc4b07f-4e27-4833-97a9-cf9741ae5648
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 0%

---

# Adobe Commerceのアラートの管理


サイトが重要なストレージと[!DNL Apdex] レベルに達しているタイミングを把握するために、主要なダッシュボードとアラートを設定しました（アプリケーションとサービスの応答時間に対するユーザーの満足度）。 これにより、応答時間の遅れや障害に気づく前に対応することができます。 以下の記事を含むアラートをトラブルシューティングできます。 アラートを使用する前に、まず通知チャネルを設定します。 Commerce on Cloud ガイドの[[!DNL New Relic] 通知チャネルの設定](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/monitor/new-relic/new-relic-service)を参照してください。

>[!NOTE]
>
>Adobe Commerce アラートポリシーの管理アラートが利用できない場合は、このアカウントが新しく作成されたか、最近設定された[!DNL New Relic]が原因である可能性があります。 これらのアカウントにアラートポリシーを追加するプロセスが毎週火曜日に実行されます。 アラートポリシーは、次のプロセスを実行した翌日に使用できます。 まだポリシーが見つからない場合は、[Adobe Commerce サポートリクエストを送信し](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#support-case) プロジェクト IDを含めてください。

これらのアラートのトラブルシューティング手順を提供するKB記事へのリンクについては、以下の表を参照してください。

* Adobe Commerceの管理されたアラート：CPUの警告アラート
* Adobe Commerceの管理アラート：CPUのクリティカルアラート
* Adobe Commerceの管理されたアラート：メモリ警告アラート
* Adobe Commerceの管理アラート：メモリクリティカルアラート
* Adobe Commerceの管理されたアラート：[!DNL Apdex]警告アラート
* Adobe Commerceの管理アラート：[!DNL Apdex] クリティカルアラート
* Adobe Commerceの管理アラート：ディスクの警告アラート
* Adobe Commerceの管理アラート：ディスククリティカルアラート
* Adobe Commerceでのアラートの管理：MariaDB アラート
* Adobe Commerceの管理されたアラート：[!DNL Redis] メモリ警告アラート
* Adobe Commerceで管理されたアラート：[!DNL Redis] メモリ クリティカル アラート

>[!NOTE]
>
>「警告アラート」と「重大アラート」の両方に設定されたしきい値は、お客様ベース全体の過去のパフォーマンスデータを使用して実施している調査に基づいており、Adobe Commerceのサポート部門とエンジニアリング部門からの最新のインサイトを表しています。 これらのしきい値は、最新の継続的な分析に基づいて変更される場合があります。 一般的なアラートフローでは、深刻度が低いアラートから高いアラートを受け取ります。 そのため、クリティカルアラートを受け取る前に、警告アラートが届く可能性があります。 トラブルシューティング手順については、記事へのリンクを参照してください。

| 重要度 | CPU | メモリ | 円盤 | [!DNL Apdex] | MariaDB | [!DNL Redis] メモリ | トラブルシューティング記事 |
|----------|-----|--------|------|-------|---------|--------------|-------------------------|
| 警告 | ✅ |        |      |       |         |              | [Adobe Commerceの管理アラート：CPUの警告アラート ](managed-alerts-for-magento-commerce-cpu-warning-alert.md) |
| 重要 | ✅ |        |      |       |         |              | [Adobe Commerceのアラートの管理：CPU クリティカルアラート ](managed-alerts-on-magento-commerce-cpu-critical-alert.md) |
| 警告 |     | ✅ |      |       |         |              | [Adobe Commerceの管理アラート：メモリ警告アラート ](managed-alerts-for-magento-commerce-memory-warning-alert.md) |
| 重要 |     | ✅ |      |       |         |              | [Adobe Commerceの管理アラート：メモリ クリティカル アラート ](managed-alerts-on-magento-commerce-memory-critical-alert.md) |
| 警告 |     |        |      | ✅ |         |              | Adobe Commerceの[管理アラート： [!DNL Apdex] 警告アラート ](managed-alerts-for-magento-commerce-apdex-warning-alert.md) |
| 重要 |     |        |      | ✅ |         |              | Adobe Commerceの[管理アラート： [!DNL Apdex]  クリティカルアラート ](managed-alerts-for-magento-commerce-apdex-critical-alert.md) |
| 警告 |     |        | ✅ |       |         |              | [Adobe Commerceの管理アラート：ディスク警告アラート ](managed-alerts-for-magento-commerce-disk-warning-alert.md) |
| 重要 |     |        | ✅ |       |         |              | [Adobe Commerceの管理アラート：ディスク クリティカル アラート ](managed-alerts-for-magento-commerce-disk-critical-alert.md) |
| 警告/重要 |     |        |      |       | ✅ |              | [Adobe Commerceのアラートの管理：MariaDB アラート ](managed-alerts-on-magento-commerce-mariadb-alerts.md) |
| 警告 |     |        |      |       |         | ✅ | [Adobe Commerceのアラートを管理： [!DNL Redis]  メモリ警告アラート ](managed-alerts-on-magento-commerce-redis-memory-warning-alert.md) |
| 重要 |     |        |      |       |         | ✅ | Adobe Commerceの[管理アラート： [!DNL Redis]  メモリ クリティカル アラート ](managed-alerts-on-magento-commerce-redis-memory-critical-alert.md) |

## 管理アラート用に設定されたアラートしきい値の確認

New Relic アカウントから、管理対象アラート用に設定されたアラートしきい値を確認できます。 手順については、[管理済みアラートを使用したパフォーマンスの監視](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/monitor/new-relic/investigate/investigate-performance#monitor-performance-with-managed-alerts)を参照してください。
