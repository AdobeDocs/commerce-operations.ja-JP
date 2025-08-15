---
title: Adobe Commerceの管理アラート：メモリ障害アラート
description: この記事では、 [!DNL New Relic] でAdobe Commerceのメモリクリティカルアラートを受け取った場合のトラブルシューティング手順を説明します。 この問題を修正するには、直ちに対処する必要があります。
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
exl-id: 90047f6e-d90a-4980-9700-84c44f2b8494
source-git-commit: 18c8e466bf15957b73cd3cddda8ff078ebeb23b0
workflow-type: tm+mt
source-wordcount: '894'
ht-degree: 0%

---

# Adobe Commerceの管理アラート：メモリ障害アラート

この記事では、[!DNL New Relic] でAdobe Commerceのメモリクリティカルアラートを受け取った場合のトラブルシューティング手順を説明します。 この問題を修正するには、直ちに対処する必要があります。

![disk critical アラート ](../../assets/managed-alerts/memory-critical-magento-managed.png){width="500"}

## 影響を受ける製品とバージョン

クラウドインフラストラクチャー上のAdobe Commerce Pro のすべてのバージョンは、アーキテクチャを計画します。

## 問題

[!DNL New Relic]Adobe Commerceの Managed アラート [ にサインアップし、1 つ以上のアラートしきい値を超えた場合、](managed-alerts-for-magento-commerce.md) で管理アラートを受け取ります。 これらのアラートは、サポートおよびエンジニアリングのインサイトを使用して、標準セットをお客様に提供するために、Adobeで開発されました。

<u> **動け！**</u>

* このアラートがクリアされるまで、スケジュールされている展開を中止します。
* サイトが応答しない、または完全に応答しなくなった場合は、すぐにサイトをメンテナンスモードにします。 手順については、『Commerce インストールガイド』の [ メンテナンスモードの有効化または無効化 ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) を参照してください。 トラブルシューティングのためにサイトに引き続きアクセスできるように、IP を除外 IP アドレスリストに追加してください。 手順については、『Commerce インストールガイド』の [ 除外 IP アドレスのリストを管理する ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses) を参照してください。

<u>**やめて！**</u>

* 追加のマーケティングキャンペーンを開始すると、サイトに追加のページビューが表示される場合があります。
* インデクサーや追加の Cron を実行すると、CPUやディスクにさらに負荷がかかる場合があります。
* 主要な管理タスク（Commerce管理者、データの読み込み/書き出し）を実行します。
* キャッシュをクリアします。

アラートの原因を調査して解決する前に「回避」アクションのいずれかを行った場合、（まだサイトの停止が発生していない場合は）サイトが応答しなくなる可能性があります。

## 解決策

原因の特定とトラブルシューティングを行うには、次の手順に従います。

>[!WARNING]
>
>これは重大なアラートなので、問題のトラブルシューティング（手順 2 以降）を行う前に、**手順 1** を完了することを強くお勧めします。

1. Adobe Commerce サポートチケットが存在するかどうかを確認します。 手順については、Commerce サポートナレッジベースの [ サポートチケットのトラッキング ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#track-support-case) を参照してください。 サポートは、既に [!DNL New Relic] のしきい値アラートを受け取り、チケットを作成して、問題の処理を開始した可能性があります。 チケットが存在しない場合は、作成します。 チケットには、次の情報が含まれている必要があります。
   * 連絡先の理由：受信した重大なアラート **[!UICONTROL New Relic]** 選択します
   * アラートの説明
   * [[!DNL New Relic]  インシデント リンク ](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). これは、[Adobe Commerceの Managed アラート ](managed-alerts-for-magento-commerce.md) に含まれています。

1. [[!DNL New Relic] APM のインフラストラクチャページ ](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) を使用して、メモリを大量に消費する上位のプロセスを特定します。 手順については、[[!DNL New Relic]  インフラストラクチャ監視ホスト ページ：「プロセス」タブ ](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes) を参照してください。
   * [!DNL Redis]、MySQL、PHP などのサービスがメモリ消費の上位ソースである場合は、次の操作を試してください。
1.最新バージョンを使用していることを確認します。 新しいバージョンでは、メモリリークが修正される場合があります。 最新バージョンでない場合は、アップグレードを検討してください。 手順については、Cloud ガイドのCommerceの [ サービスの変更 ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) を参照してください。
1. サービスの問題がバージョンに関連したものでない場合は、次の操作を試してください。
1. **MySQL**：クエリの長時間実行、プライマリキーが定義されていない、インデックスが重複しているなどの問題がないか確認してください。 手順については、Commerce実装プレイブックの [ クラウドインフラストラクチャ上のAdobe Commerceで最も一般的なデータベースの問題 ](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) を参照してください。
1. **[!DNL Redis]**:[!DNL Redis] がメモリ消費の上位ソースの場合は、[ サポートチケットを送信 ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case) します。
1. **PHP**: PHP がメモリ消費の上位のソースである場合は、CLI/ターミナルで `ps aufx` を実行して、実行中のプロセスを確認します。 ターミナル出力には、現在実行中の cron ジョブとプロセスが表示されます。 出力でプロセスの実行時間を確認します。 実行時間が長い Cron がある場合は、Cron がハングしている可能性があります。 トラブルシューティングの手順については、Commerce サポートナレッジベースの [ パフォーマンスが遅い、動作が遅い、動作が長い ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons) および [Cron ジョブが「実行中」ステータスのままになる ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status) を参照してください。
1. それでも問題の原因を特定できない場合は、[[!DNL New Relic] APM のトランザクションページ ](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) を使用して、パフォーマンスの問題があるトランザクションを特定します。
   * [!DNL Apdex] スコアの昇順でトランザクションを並べ替えます。 [[!DNL Apdex]](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) は、web アプリケーションおよびサービスの応答時間に対するユーザー満足度を指します。 [[!DNL Apdex score]](managed-alerts-for-magento-commerce-apdex-warning-alert.md) は、ボトルネック（応答時間の長いトランザクション）を示している場合があります。 通常は、データベース、[!DNL  Redis]、または PHP です。 手順については、[[!DNL New Relic]  不満が最も高いトランザクション  [!DNL Apdex]  表示 ](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat) を参照してください。
   * スループット、平均応答時間が最も遅い、最も時間がかかる、およびその他のしきい値でトランザクションを並べ替えます。 手順については、[[!DNL New Relic] [ 特定のパフォーマンスの問題の検索 ]](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) を参照してください。 それでも問題を特定できない場合は、[[!DNL New Relic] APM のインフラストラクチャページ ](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) を使用します。
1. メモリ消費が増加した原因を特定できない場合は、最近の傾向を確認して、最近のコードのデプロイメントまたは設定の変更に関する問題（新しい顧客グループやカタログの大幅な変更など）を特定します。 コードのデプロイメントまたは変更における相関関係について、過去 7 日間のアクティビティを確認することをお勧めします。
1. 上記の方法で適切な時間内に原因や解決策を見つけることができない場合は、アップサイズをリクエストするか、まだサイトをメンテナンスモードに設定していない場合は、サイトをメンテナンスモードに設定します。 手順については、Commerce サポートナレッジベースの [ 一時サイズ変更のリクエスト方法 ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize) および『Commerce インストールガイド』の [ メンテナンスモードの有効化または無効化 ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) を参照してください。
1. アップサイズによってサイトが通常の処理に戻った場合は、永続的なアップサイズをリクエストするか（Adobe アカウントチームにお問い合わせください）、負荷テストを実行してクエリまたはサービスの負荷を軽減するコードを最適化し、専用のステージングで問題を再現することを試みてください。 Commerce on Cloud ガイドの [ 読み込みとストレステスト ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) を参照してください。
