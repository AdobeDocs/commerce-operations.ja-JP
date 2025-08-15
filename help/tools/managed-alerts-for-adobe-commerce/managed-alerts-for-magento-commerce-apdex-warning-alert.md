---
title: 'Managed alerts for Adobe Commerce: [!DNL Apdex] warning アラート'
description: この記事では、Adobe Commerceの警告アラートを受信した場合のトラブルシューティ  [!DNL Apdex]  グ手順を示し、web アプリケーションおよびサ  [!DNL New Relic]. The [!DNL Apdex]  ビスの応答時間に対するユーザーの満足度をスコアで測定します。 この問題を修正するには、直ちに対処する必要があります。
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
exl-id: 1d79d2bc-01de-432f-84a0-9571016e7e9c
source-git-commit: 18c8e466bf15957b73cd3cddda8ff078ebeb23b0
workflow-type: tm+mt
source-wordcount: '796'
ht-degree: 0%

---

# Adobe Commerceの管理アラート：[!DNL Apdex] 警告アラート

この記事では、[!DNL Apdex] でAdobe Commerceの [!DNL New Relic] 警告アラートが表示された場合のトラブルシューティング手順を説明します。 [!DNL Apdex] スコアは、web アプリケーションおよびサービスの応答時間に対するユーザーの満足度を測定します。 この問題を修正するには、直ちに対処する必要があります。 選択したアラート通知チャネルに応じて、アラートは次のようになります。

![apdex 警告アラート ](../../assets/managed-alerts/apdex-warning-magento-managed.png){width="500"}

## 影響を受ける製品とバージョン

* Adobe Commerce on cloud infrastructure Pro プランアーキテクチャ
* Adobe Commerce on cloud infrastructure スタータープランアーキテクチャ

## 問題

[!DNL New Relic]Adobe Commerceの Managed アラート [ にサインアップし、1 つ以上のアラートしきい値を超えた場合、](managed-alerts-for-magento-commerce.md) で管理アラートを受け取ります。 これらのアラートは、サポートとエンジニアリングのインサイトを使用して、マーチャントに標準セットを提供するために、Adobeで開発されました。

<u> **動け！**</u>

* このアラートがクリアされるまで、スケジュールされている展開を中止します。
* サイトが応答しない、または完全に応答しなくなった場合は、すぐにサイトをメンテナンスモードにします。 手順については、『Commerce インストールガイド』の [ メンテナンスモードの有効化または無効化 ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) を参照してください。 トラブルシューティングのためにサイトに引き続きアクセスできるように、IP を除外 IP アドレスリストに追加してください。 手順については、『Commerce インストールガイド』の [ 除外 IP アドレスのリストの管理 ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses) を参照してください。

<u>**やめて！**</u>

* 追加のマーケティングキャンペーンを開始すると、サイトに追加のページビューが表示される場合があります。
* インデクサーや追加の Cron を実行すると、CPUやディスクにさらに負荷がかかる場合があります。
* 主要な管理タスク（Commerce管理者、データの読み込み/書き出し）を実行します。
* キャッシュをクリアします。

## 解決策

原因の特定とトラブルシューティングを行うには、次の手順に従います。

1. 問題の原因を特定するには、[[!DNL New Relic APM's]  トランザクションページ ](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) を使用して、パフォーマンスの問題があるトランザクションを特定します。
   * トランザクションを昇 [!DNL Apdex scores] で並べ替えます。 [[!DNL Apdex]](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) は、web アプリケーションおよびサービスの応答時間に対するユーザー満足度を指します。 [ 低スコア  [!DNL Apdex]  は ](managed-alerts-for-magento-commerce-apdex-warning-alert.md) ボトルネック（応答時間の長いトランザクション）を示している場合があります。 通常は、データベース、[!DNL Redis]、または PHP です。 手順については、[[!DNL New Relic]  不満が最も高いトランザクション  [!DNL Apdex]  表示 ](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat) を参照してください。
   * スループット、平均応答時間が最も遅い、最も時間がかかる、およびその他のしきい値でトランザクションを並べ替えます。 手順については、[[!DNL New Relic]  特定のパフォーマンスの問題の検索 ](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) を参照してください。
1. [[!DNL New Relic] APM のインフラストラクチャページ ](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) を使用して、リソースを大量に消費するプロセスを特定します。 手順については、[[!DNL New Relic]  インフラストラクチャ監視ホスト ページ：[!UICONTROL Processes] ールタブ ](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes) を参照してください。
1. [!DNL Redis] や MySQL などのサービスがメモリ消費の上位ソースである場合は、次の操作を試してください。
   * 最新バージョンを使用していることを確認します。 新しいバージョンでは、メモリリークが修正される場合があります。 最新バージョンでない場合は、アップグレードを検討してください。 手順については、Cloud ガイドのCommerceの [ サービスの変更 ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) を参照してください。
1. 問題がサービスのバージョンに起因するものではない場合：
   * 長時間実行中のクエリ、プライマリキーが定義されていない、インデックスが重複しているなど、MySQL のその他の問題を確認します。 手順については、Commerce実装プレイブックの [ クラウドインフラストラクチャ上のAdobe Commerceで最も一般的なデータベースの問題 ](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) を参照してください。
   * その他の PHP の問題をチェックします。 CLI/ターミナルで `ps aufx` を実行して、実行中のプロセスを確認します。 ターミナル出力には、現在実行中の cron ジョブとプロセスが表示されます。 出力でプロセスの実行時間を確認します。 実行時間が長い Cron がある場合は、Cron がハングしている可能性があります。 トラブルシューティングの手順については、Commerce サポートナレッジベースの [ パフォーマンスが遅い、動作が遅い、長時間動作する Cron](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons) および [Cron ジョブが「実行中」ステータスのままになる ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status) を参照してください。
1. 問題の潜在的な原因が特定されたら、環境に SSH で問い合わせて詳細を確認します。 手順については、Commerce on Cloud ガイドの [SSH into your environment](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh) を参照してください。
1. ソースの特定に引き続き苦労する場合は、最近のトレンドを確認し、最近のコードのデプロイメントまたは設定の変更に関する問題を特定します（例えば、新しい顧客グループやカタログの大幅な変更）。 コードのデプロイメントまたは変更における相関関係について、過去 7 日間のアクティビティを確認することをお勧めします。
1. 妥当な時間内にソリューションが見つからない場合は、アップサイズをリクエストするか、サイトをまだメンテナンスモードに設定していない場合は配置します。 手順については、Commerce サポートナレッジベースの [ 一時サイズ変更のリクエスト方法 ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize) および『Commerce インストールガイド』の [ メンテナンスモードの有効化または無効化 ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) を参照してください。
1. [upsize](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize) によってサイトが通常の処理に戻った場合は、永続的なアップサイズのリクエスト（Adobe アカウントチームにお問い合わせください）を検討するか、負荷テストを実行してクエリまたはサービスの負荷を軽減するコードを最適化し、専用ステージングで問題を再現してみてください。 Commerce on Cloud ガイドの [ 負荷とストレステスト ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) を参照してください。
