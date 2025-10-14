---
title: Adobe Commerceの管理されたアラート：重大  [!DNL Apdex]  アラート
description: この記事では、Adobe Commerceの重要なアラートを受信した場合のトラブルシューティ  [!DNL Apdex]  グ手順を示します。アラートを受信した場合、web アプリケーションおよびサービスの応答時間に対するユーザーの満足度をスコアで測定します  [!DNL New Relic]. The [!DNL Apdex]  この問題を修正するには、直ちに対処する必要があります。
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
exl-id: 00e29611-fd4b-45c8-a1e0-56fc3cbe90e0
source-git-commit: 18c8e466bf15957b73cd3cddda8ff078ebeb23b0
workflow-type: tm+mt
source-wordcount: '926'
ht-degree: 0%

---

# Adobe Commerceの管理アラート：重大なアラート [!DNL Apdex] 通知

この記事では、[!DNL Apdex] でAdobe Commerceの [!DNL New Relic] しい重大なアラートを受け取った場合のトラブルシューティング手順を説明します。 [!DNL Apdex] スコアは、web アプリケーションおよびサービスの応答時間に対するユーザーの満足度を測定します。 この問題を修正するには、直ちに対処する必要があります。 選択したアラート通知チャネルに応じて、アラートは次のようになります。

![apdex 重大アラート &#x200B;](../../assets/managed-alerts/apdex-critical-magento-managed.png){width="500"}

## 影響を受ける製品とバージョン

* Adobe Commerce on cloud infrastructure Pro プランアーキテクチャ
* Adobe Commerce on cloud infrastructure スタータープランアーキテクチャ

## 問題

[!DNL New Relic]Adobe Commerceの Managed アラート [&#x200B; にサインアップし、1 つ以上のアラートしきい値を超えた場合、](managed-alerts-for-magento-commerce.md) で管理アラートを受け取ります。 これらのアラートは、サポートとエンジニアリングのインサイトを使用して、マーチャントに標準セットを提供するために、Adobeで開発されました。

<u> **動け！**</u>

* このアラートがクリアされるまで、スケジュールされている展開を中止します。
* サイトが応答しない、または完全に応答しなくなった場合は、すぐにサイトをメンテナンスモードにします。 手順については、『Commerce インストールガイド』の [&#x200B; メンテナンスモードの有効化または無効化 &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) を参照してください。 トラブルシューティングのためにサイトに引き続きアクセスできるように、IP を除外 IP アドレスリストに追加してください。 手順については、『Commerce インストールガイド』の [&#x200B; 除外 IP アドレスのリストの管理 &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses) を参照してください。

<u>**やめて！**</u>

* 追加のマーケティングキャンペーンを開始すると、サイトに追加のページビューが表示される場合があります。
* インデクサーや追加の Cron を実行すると、CPUやディスクにさらに負荷がかかる場合があります。
* 主要な管理タスク（Commerce管理者、データの読み込み/書き出し）を実行します。
* キャッシュをクリアします。

アラートの原因をトラブルシューティングする前に、重要なアラートを受け取ったときに上記の手順を実行すると、まだサイトの停止が発生していない場合、サイトが応答しなくなります。

## 解決策

原因の特定とトラブルシューティングを行うには、次の手順に従います。

>[!WARNING]
>
>これは重大なアラートなので、問題のトラブルシューティング（手順 2 以降）を行う前に、**手順 1** を完了することを強くお勧めします。

1. Adobe Commerce サポートチケットが存在するかどうかを確認します。 手順については、Commerce サポートナレッジベースの [&#x200B; サポートチケットのトラッキング &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#track-support-case) を参照してください。 サポートがしきい値アラートを受け取り、チケッ [!DNL New Relic] を作成して、問題の処理を開始した可能性があります。 チケットが存在しない場合は、作成します。 チケットには、次の情報が含まれている必要があります。
   * 連絡先の理由：「**[!UICONTROL New Relic CRITICAL alert received]**」を選択します。
   * アラートの説明。
   * [[!DNL New Relic]  インシデント リンク &#x200B;](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). これは、[Adobe Commerceの Managed アラート &#x200B;](managed-alerts-for-magento-commerce.md) に含まれています。
1. 問題の原因を特定するには、[[!DNL New Relic] APM のトランザクションページ &#x200B;](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) を使用して、パフォーマンスの問題があるトランザクションを特定します。
   * [!DNL Apdex] スコアの昇順でトランザクションを並べ替えます。 [[!DNL Apdex]](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) は、web アプリケーションおよびサービスの応答時間に対するユーザー満足度を指します。 [!DNL Apdex] スコアが低い場合、ボトルネック（応答時間の長いトランザクション）を示している可能性があります。 通常は、データベース、[!DNL Redis]、または PHP です。 手順については、[[!DNL New Relic] Apdex の不満が最も高いトランザクションの表示 &#x200B;](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction/#dissatisfaction) を参照してください。
   * スループット、平均応答時間が最も遅い、最も時間がかかる、およびその他のしきい値でトランザクションを並べ替えます。 手順については、[[!DNL New Relic]  特定のパフォーマンスの問題の検索 &#x200B;](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) を参照してください。 問題の特定に苦労している場合は、[[!DNL New Relic] APM のインフラストラクチャページ &#x200B;](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) を使用します。
1. [[!DNL New Relic] APM のインフラストラクチャページ &#x200B;](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) を使用して、リソースを大量に消費するプロセスを特定します。 手順については、[[!DNL New Relic]  インフラストラクチャ監視ホストのページ：[!UICONTROL Processes tab]](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes) を参照してください。
1. [!DNL Redis] や MySQL などのサービスがメモリ消費の上位ソースである場合は、次の操作を試してください。
   * 最新バージョンを使用していることを確認します。 新しいバージョンでは、メモリリークが修正される場合があります。 最新バージョンでない場合は、アップグレードを検討してください。 手順については、Cloud ガイドのCommerceの [&#x200B; サービスの変更 &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html?lang=ja) を参照してください。
   * 長時間実行中のクエリ、プライマリキーが定義されていない、インデックスが重複しているなど、MySQL の問題を確認します。 手順については、Commerce実装プレイブックの [&#x200B; クラウドインフラストラクチャ上のAdobe Commerceで最も一般的なデータベースの問題 &#x200B;](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html?lang=ja) を参照してください。
   * PHP の問題をチェックします。 CLI/ターミナルで `ps aufx` を実行して、実行中のプロセスを確認します。 ターミナル出力には、現在実行中の cron ジョブとプロセスが表示されます。 出力でプロセスの実行時間を確認します。 実行時間が長い Cron がある場合は、Cron がハングしている可能性があります。 トラブルシューティングの手順については、Commerce サポートナレッジベースの [&#x200B; パフォーマンスが遅い、動作が遅い、長時間動作する Cron](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons) および [Cron ジョブが「実行中」ステータスのままになる &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status) を参照してください。

1. ソースが特定されたら、環境に SSH で接続して詳細を調べます。 手順については、Commerce on Cloud ガイドの [SSH into your environment](https://experienceleague.adobe.com/ja/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh) を参照してください。
1. ソースの特定に引き続き苦労する場合は、最近のトレンドを確認し、最近のコードのデプロイメントまたは設定の変更に関する問題を特定します（例えば、新しい顧客グループやカタログの大幅な変更）。 コードのデプロイメントまたは変更における相関関係について、過去 7 日間のアクティビティを確認することをお勧めします。
1. 妥当な時間内にソリューションが見つからない場合は、アップサイズをリクエストするか、サイトをまだメンテナンスモードに設定していない場合は配置します。 手順については、Commerce サポートナレッジベースの [&#x200B; 一時サイズ変更のリクエスト方法 &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize) および『Commerce インストールガイド』の [&#x200B; メンテナンスモードの有効化または無効化 &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) を参照してください。
1. アップサイズによってサイトが通常の処理に戻った場合は、永続的なアップサイズをリクエストするか（Adobe アカウントチームにお問い合わせください）、負荷テストを実行してクエリまたはサービスの負荷を軽減するコードを最適化し、専用のステージングで問題を再現することを試みてください。 Commerce on Cloud ガイドの [&#x200B; 負荷とストレステスト &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) を参照してください。
