---
title: Managed alerts for Adobe Commerce:Memory warning アラート
description: この記事では、 [!DNL New Relic] のAdobe Commerceでメモリワーニングアラートが表示された場合のトラブルシューティング手順を説明します。 この問題を修正するには、直ちに対処する必要があります。
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
exl-id: 0910a431-bf2c-469e-81e2-92c8d9be3249
source-git-commit: 18c8e466bf15957b73cd3cddda8ff078ebeb23b0
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 0%

---

# Managed alerts for Adobe Commerce:Memory warning アラート

この記事では、[!DNL New Relic] でAdobe Commerceのメモリワーニングアラートが表示された場合のトラブルシューティング手順を説明します。 この問題を修正するには、直ちに対処する必要があります。 選択したアラート通知チャネルに応じて、アラートは次のようになります。

![ メモリ警告 ](../../assets/managed-alerts/memory-warning-magento-managed.png){width="500"}

## 影響を受ける製品とバージョン

Adobe Commerce on cloud infrastructure Pro プランアーキテクチャ

## 問題

[!DNL New Relic]Adobe Commerceの Managed アラート [ にサインアップし、1 つ以上のアラートしきい値を超えた場合、](managed-alerts-for-magento-commerce.md) でアラートが届きます。 これらのアラートは、サポートおよびエンジニアリングのインサイトを使用して、標準セットをお客様に提供するために、Adobe Commerceで開発されました。

<u>**実行**</u>:

* このアラートがクリアされるまで、スケジュールされているデプロイメントを中止することをお勧めします。
* サイトが応答しない、または完全に応答しなくなった場合は、すぐにサイトをメンテナンスモードにします。 手順については、『Commerce インストールガイド』の [ メンテナンスモードの有効化または無効化 ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) を参照してください。 トラブルシューティングのためにサイトに引き続きアクセスできるように、IP を除外 IP アドレスリストに追加してください。 手順については、『Commerce インストールガイド』の [ 除外 IP アドレスのリストの管理 ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses) を参照してください。

<u>**止めて！**</u>:

* 追加のマーケティングキャンペーンを開始すると、サイトに追加のページビューが表示される場合があります。
* インデクサーや追加の Cron を実行すると、CPUやディスクにさらに負荷がかかる場合があります。
* 主要な管理タスク（管理者、データの読み込み/書き出し）を実行します。
* キャッシュをクリアします。

## 解決策

原因の特定とトラブルシューティングを行うには、次の手順に従います。

1. [[!DNL New Relic] APM のインフラストラクチャページ ](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) を使用して、メモリを大量に消費する上位のプロセスを特定します。 手順については、[[!DNL New Relic] [Infrastructure monitoring Hosts page: [!UICONTROL Processes] tab]](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes) を参照してください。 [!DNL Redis] や MySQL などのサービスがメモリ消費の上位ソースである場合は、次の操作を試してください。

   * 最新バージョンを使用していることを確認します。 新しいバージョンでは、メモリリークが修正される場合があります。 最新バージョンでない場合は、アップグレードを検討してください。 手順については、Cloud ガイドのCommerceの [ サービスの変更 ](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml) を参照してください。
   * それでもメモリ消費量が増加した原因を特定できない場合は、クエリの長時間実行、プライマリキーが定義されていない、インデックスが重複しているなど、MySQL の問題がないかどうかを確認します。 手順については、Commerce実装プレイブックの [ クラウドインフラストラクチャ上のAdobe Commerceで最も一般的なデータベースの問題 ](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) を参照してください。
   * MySQL の問題がない場合は、PHP の問題を確認してください。 CLI/ターミナルで `ps aufx` を実行して、実行中のプロセスを確認します。 端末の出力には、現在実行中の cron ジョブとプロセスが表示されます。 出力でプロセスの実行時間を確認します。 実行時間が長い Cron がある場合は、Cron がハングしている可能性があります。 トラブルシューティングの手順については、Commerce サポートナレッジベースの [ パフォーマンスが遅い、動作が遅い、長時間実行されている Cron](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons) および [Cron ジョブが「実行中」ステータスのままになる ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status) を参照してください。

1. それでも問題の原因を特定できない場合は、[[!DNL New Relic] APM のトランザクションページ ](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) を使用して、パフォーマンスの問題があるトランザクションを特定します。

   * [!DNL Apdex] スコアの昇順でトランザクションを並べ替えます。 [[!DNL Apdex]](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) は、web アプリケーションおよびサービスの応答時間に対するユーザー満足度を指します。 [ 低スコア  [!DNL Apdex]  は ](managed-alerts-for-magento-commerce-apdex-warning-alert.md) ボトルネック（応答時間の長いトランザクション）を示している場合があります。 通常は、データベース、[!DNL Redis]、または PHP です。 手順については、New Relic[ 最も不満の多いトランザクションを表示  [!DNL Apdex]  を参照 ](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat) てください。
   * スループット、平均応答時間が最も遅い、最も時間がかかる、およびその他のしきい値でトランザクションを並べ替えます。 手順については、[[!DNL New Relic]  特定のパフォーマンスの問題の検索 ](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) を参照してください。 それでも問題を特定できない場合は、[[!DNL New Relic] APM のインフラストラクチャページ ](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) を使用します。

1. メモリ消費が増加した原因を特定できない場合は、最近の傾向を確認して、最近のコードのデプロイメントまたは設定の変更に関する問題（新しい顧客グループやカタログの大幅な変更など）を特定します。 コードのデプロイメントまたは変更における相関関係について、過去 7 日間のアクティビティを確認することをお勧めします。

1. 上記の方法で適切な時間内に原因や解決策を見つけられなかった場合は、アップサイズをリクエストするか、まだサイトをメンテナンスモードに設定します（まだ設定していない場合）。 手順については、Commerce サポートナレッジベースの [ 一時サイズ変更のリクエスト方法 ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize) および『Commerce インストールガイド』の [ メンテナンスモードの有効化または無効化 ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) を参照してください。

1. アップサイズによってサイトが通常の処理に戻った場合は、永続的なアップサイズをリクエストするか（Adobe アカウントチームにお問い合わせください）、負荷テストを実行してクエリまたはサービスの負荷を軽減するコードを最適化し、専用のステージングで問題を再現することを試みてください。 Commerce on Cloud ガイドの [ 負荷とストレステスト ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) を参照してください。
