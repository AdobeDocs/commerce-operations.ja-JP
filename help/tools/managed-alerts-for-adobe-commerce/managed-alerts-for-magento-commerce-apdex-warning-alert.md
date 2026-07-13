---
title: 'Adobe Commerce: [!DNL Apdex] 警告アラートの管理'
description: この記事では、Adobe Commerceの [!DNL Apdex] 警告アラートを [!DNL New Relic]. The [!DNL Apdex]  スコアで受け取った場合のトラブルシューティング手順について説明します。ユーザーの満足度をWeb アプリケーションとサービスの応答時間に測定します。 この問題を解決するには早急な行動が必要だ。
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
exl-id: 1d79d2bc-01de-432f-84a0-9571016e7e9c
source-git-commit: 18c8e466bf15957b73cd3cddda8ff078ebeb23b0
workflow-type: tm+mt
source-wordcount: '1013'
ht-degree: 0%

---

# Adobe Commerceの管理されたアラート：[!DNL Apdex]警告アラート

この記事では、[!DNL New Relic]でAdobe Commerceの[!DNL Apdex]警告アラートを受け取った場合のトラブルシューティング手順について説明します。 [!DNL Apdex] スコアは、web アプリケーションとサービスの応答時間に対するユーザーの満足度を測定します。 この問題を解決するには早急な行動が必要だ。 選択したアラート通知チャネルに応じて、アラートは次のようになります。

![apdex警告アラート &#x200B;](../../assets/managed-alerts/apdex-warning-magento-managed.png){width="500"}

## 影響を受ける製品とバージョン

* Adobe Commerce on cloud infrastructure Pro プランアーキテクチャ
* Adobe Commerce on cloud infrastructure スタータープランアーキテクチャ

## イシュー

Adobe Commerce[&#128279;](managed-alerts-for-magento-commerce.md)の管理対象アラートにサインアップし、1つ以上のアラートしきい値を超えた場合、[!DNL New Relic]に管理対象アラートが届きます。 これらのアラートは、Adobeが開発したもので、サポートとエンジニアリングからのインサイトを利用して、マーチャントに標準セットを提供します。

<u> **実行！** </u>

* このアラートがクリアされるまでスケジュールされたデプロイメントをすべて中止します。
* サイトが完全に応答しない、または応答しなくなった場合は、すぐにメンテナンスモードにします。 手順については、『Commerce インストールガイド』の「[&#x200B; メンテナンスモードを有効または無効にする](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode)」を参照してください。 トラブルシューティングのためにサイトにアクセスできるように、IPを免除IP アドレスリストに追加してください。 手順については、Commerce インストールガイドの「[除外IP アドレスのリストを管理する](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses)」を参照してください。

<u>**やめて！**</u>

* 追加のページビューをサイトに呼び込む可能性のある、追加のマーケティング施策を開始します。
* CPUまたはディスクに負荷がかかる可能性があるインデクサーまたは別のクローンを実行します。
* 主要な管理作業（Commerce管理者、データの読み込み/書き出しなど）を行います。
* キャッシュをクリアします。

## Solution

以下の手順に従って、原因を特定し、トラブルシューティングします。

1. 問題の原因を特定するには、[[!DNL New Relic APM's]  トランザクションページ &#x200B;](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems)を使用して、パフォーマンスの問題を含むトランザクションを特定します。
   * [!DNL Apdex scores]を昇順で並べ替えます。 [[!DNL Apdex]](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction)は、web アプリケーションおよびサービスの応答時間に対するユーザー満足度を指します。 [低 [!DNL Apdex]  スコア &#x200B;](managed-alerts-for-magento-commerce-apdex-warning-alert.md)は、ボトルネック（応答時間が長いトランザクション）を示している可能性があります。 通常は、データベース、[!DNL Redis]、またはPHPです。 手順については、[[!DNL New Relic] 最も高いトランザクションを表示 [!DNL Apdex] 不満](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat)を参照してください。
   * 最も高いスループット、最も遅い平均応答時間、最も時間がかかるその他のしきい値などによってトランザクションを並べ替えます。 手順については、[[!DNL New Relic] 特定のパフォーマンスの問題を見つける](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems)を参照してください。
1. [[!DNL New Relic] APMのインフラストラクチャ ページ &#x200B;](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/)を使用して、リソース集約的なプロセスを特定します。 手順については、[[!DNL New Relic]  インフラストラクチャ監視ホスト ページ：[!UICONTROL Processes] タブ &#x200B;](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes)を参照してください。
1. [!DNL Redis]やMySQLなどのサービスがメモリ消費の上位ソースである場合は、次の操作を試してください。
   * 最新バージョンであることを確認してください。 新しいバージョンでは、メモリリークを修正できることがあります。 最新バージョンを使用していない場合は、アップグレードを検討してください。 手順については、Commerce on Cloud ガイドの[Change Services](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html)を参照してください。
1. 問題の原因がサービスのバージョンではない場合：
   * 長時間実行中のクエリ、プライマリキーが定義されていない、重複インデックスなど、その他のMySQLの問題を確認します。 手順については、Commerce実装プレイブックの「[&#x200B; クラウドインフラストラクチャ上のAdobe Commerceの最も一般的なデータベースの問題](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html)」を参照してください。
   * 他のPHPの問題を確認します。 CLI/ターミナルで`ps aufx`を実行して、実行中のプロセスを確認します。 ターミナル出力には、現在実行中のcron ジョブとプロセスが表示されます。 プロセスの実行時間の出力を確認します。 実行時間が長いcronがある場合は、cronがぶら下がっている可能性があります。 トラブルシューティングの手順については、Commerce サポート サポート ナレッジベースの「[&#x200B; パフォーマンスが遅い、実行が遅い](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons)、実行が長い[Cron ジョブが「実行中」ステータス &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status)で停止する」を参照してください。
1. 問題の潜在的な原因を特定したら、環境にSSHで接続して、さらに調査します。 手順については、『Commerce on Cloud Guide 』の「[SSH into your environment](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh)」を参照してください。
1. ソースの特定に苦慮している場合は、最近のトレンドを確認して、最近のコードのデプロイや設定の変更（新しい顧客グループやカタログの大幅な変更など）に関する問題を特定します。 コードのデプロイメントまたは変更の相関関係については、過去7日間のアクティビティを確認することをお勧めします。
1. 合理的な時間内にソリューションが見つからない場合は、まだ行っていない場合は、アップサイズを要求するか、サイトをメンテナンスモードに配置します。 手順については、Commerce サポート サポート サポート技術情報の[一時サイズ変更をリクエストする方法](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize)、およびCommerce インストールガイドの[&#x200B; メンテナンスモードを有効または無効にする](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode)を参照してください。
1. [upsize](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize)がサイトを通常の動作に戻す場合は、永続的なアップサイズをリクエストすることを検討するか（Adobeのアカウントチームにお問い合わせください）、読み込みテストを実行してクエリを最適化するか、サービスへのプレッシャーを軽減するコードを実行して、専用ステージングで問題を再現してみてください。 Commerce on Cloud ガイドの[負荷および負荷テスト &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing)を参照してください。
