---
title: Adobe Commerceの管理アラート：CPUの重大なアラート
description: この記事では、 [!DNL New Relic] でAdobe CommerceのCPU クリティカルアラートを受け取った場合のトラブルシューティング手順を説明します。 この問題を修正するには、直ちに対処する必要があります。
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
exl-id: 8629ab18-5eef-4d76-9cf8-88fe2d3439df
source-git-commit: 18c8e466bf15957b73cd3cddda8ff078ebeb23b0
workflow-type: tm+mt
source-wordcount: '776'
ht-degree: 0%

---

# Adobe Commerceの管理アラート：CPUの重大なアラート

この記事では、[!DNL New Relic] でAdobe CommerceのCPU クリティカルアラートを受け取った場合のトラブルシューティング手順を説明します。 この問題を修正するには、直ちに対処する必要があります。 選択したアラート通知チャネルに応じて、アラートは次のようになります。

![disk critical アラート ](../../assets/managed-alerts/cpu-critical-magento-managed.png){width="500"}

## 影響を受ける製品とバージョン

Adobe Commerce on cloud infrastructure Pro プランアーキテクチャ

## 問題

[!DNL New Relic]Adobe Commerceの Managed アラート [ にサインアップし、1 つ以上のアラートしきい値を超えた場合、](managed-alerts-for-magento-commerce.md) で管理アラートを受け取ります。 これらのアラートは、サポートおよびエンジニアリングのインサイトを使用して、標準セットをお客様に提供するために、Adobe Commerceで開発されました。

<u>**実行**</u>:

* このアラートがクリアされるまで、スケジュールされている展開を中止します。
* サイトが応答しない、または完全に応答しなくなった場合は、すぐにサイトをメンテナンスモードにします。 手順については、『Commerce インストールガイド』の [ メンテナンスモードの有効化または無効化 ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) を参照してください。 トラブルシューティングのためにサイトに引き続きアクセスできるように、IP を除外 IP アドレスリストに追加してください。 手順については、『Commerce インストールガイド』の [ 除外 IP アドレスのリストの管理 ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses) を参照してください。

<u>**止めて！**</u>:

* 追加のマーケティングキャンペーンを開始すると、サイトに追加のページビューが表示される場合があります。
* インデクサーや追加の Cron を実行すると、CPUやディスクにさらに負荷がかかる場合があります。
* 主要な管理タスク（Commerce管理者、データの読み込み/書き出し）を実行します。
* キャッシュをクリアします。

アラートの原因を調査して解決する前に「回避」アクションのいずれかを行った場合、（サイトの停止が発生していない場合は）サイトが応答しなくなる可能性があります。

## 解決策

原因の特定とトラブルシューティングを行うには、次の手順に従います。

>[!WARNING]
>
>これは重大なアラートなので、問題のトラブルシューティング（手順 2 以降）を行う前に、**手順 1** を完了することを強くお勧めします。

Adobe Commerce サポートチケットが存在するかどうかを確認します。 手順については、Commerce サポートナレッジベースの [ サポートチケットのトラッキング ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#track-support-case) を参照してください。 サポートがしきい値アラートを受け取り、チケッ [!DNL New Relic] を作成して、問題の処理を開始した可能性があります。 チケットが存在しない場合は、作成します。 チケットには、次の情報が含まれている必要があります。

1. 連絡先の理由：「**[!UICONTROL New Relic CRITICAL alert received]**」を選択します。
1. アラートの説明。
1. [[!DNL New Relic]  インシデント リンク ](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). これは、[Adobe Commerceの Managed アラート ](managed-alerts-for-magento-commerce.md) に含まれています。
1. [[!DNL New Relic] APM のトランザクションページ ](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) を使用して、パフォーマンスの問題があるトランザクションを特定します。
   * Apdex スコアの昇順でトランザクションを並べ替えます。 [[!DNL Apdex]](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) は、web アプリケーションおよびサービスの応答時間に対するユーザー満足度を指します。 [ 低スコア  [!DNL Apdex]  は ](managed-alerts-for-magento-commerce-apdex-warning-alert.md) ボトルネック（応答時間の長いトランザクション）を示している場合があります。 通常は、データベース、[!DNL Redis]、または PHP に関連しています。 手順については、New Relic[ 最も不満の多いトランザクションを表示  [!DNL Apdex]  を参照 ](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat) てください。
   * スループット、平均応答時間が遅い、時間がかかる、その他のしきい値の高い順にトランザクションを並べ替えます。 手順については、[!DNL New Relic] 特定のパフォーマンスの問題の検索 [ を参照してください ](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems)。
1. ソースの特定に依然として苦労している場合は、[[!DNL New Relic] APM のインフラストラクチャページ ](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page) を使用して、リソースが多いサービスを特定します。 手順については、[!DNL New Relic]Infrastructure 監視ホスト ページ：「プロセス」タブ [](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes) 参照してください。
1. ソースを特定した場合は、環境に SSH で接続して詳細を調べます。 手順については、Commerce on Cloud ガイドの [SSH into your environment](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) を参照してください。
1. ソースの特定に苦労する場合：
   * 最近のトレンドを確認して、最近のコードのデプロイメントや設定の変更に関する問題を特定します（例えば、新しい顧客グループやカタログの大幅な変更）。 コードのデプロイメントまたは変更における相関関係について、過去 7 日間のアクティビティを確認することをお勧めします。
   * フラットカタログの確認と無効化を検討します。 手順については、Commerce サポートナレッジベースの [ パフォーマンスが遅い、動作が遅い、動作が長い ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons) を参照してください。
   * DDoS 攻撃が発生していると思われる場合は、ボットトラフィックをブロックしてみてください。 手順については、Commerce サポートナレッジベースの [Fastly レベルでクラウドインフラストラクチャ上のAdobe Commerceの悪意のあるトラフィックをブロックする方法 ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/block-malicious-traffic-for-magento-commerce-on-fastly-level) を参照してください。
1. 問題が一時的であると思われる場合は、アップサイズなどの軽減手順を実行するか、サイトをメンテナンスモードにします。 手順については、Commerce サポートナレッジベースの [ 一時サイズ変更のリクエスト方法 ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize) および『Commerce インストールガイド』の [ メンテナンスモードの有効化または無効化 ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) を参照してください。 アップサイズによってサイトが通常の処理に戻った場合は、永続的なアップサイズを要求するか（Adobe アカウントチームにお問い合わせください）、負荷テストを実行してクエリまたはコードを最適化し、サービスに対する圧力を軽減することにより、専用ステージングで問題を再現することを試みてください。 手順については、Cloud Guide のCommerceの [ 負荷とストレステスト ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) を参照してください。
