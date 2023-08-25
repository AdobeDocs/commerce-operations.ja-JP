---
title: バックエンドのパフォーマンスの最適化
description: Adobe Commerce Sites のバックエンドパフォーマンスの最適化について説明します。
badge: label="オブジェクトソースによる貢献" type="Informative" url="https://objectsource.co.uk/" tooltip="objectsource"
role: Admin, User, Developer
feature: Best Practices
source-git-commit: 2416357d8cacb5627fd24f92b16c2d9839f91082
workflow-type: tm+mt
source-wordcount: '1074'
ht-degree: 0%

---

# バックエンドのパフォーマンスを最適化するためのベストプラクティス

このトピックでは、データベースの最適化とテストに重点を置いて、Adobe Commerceサイトのバックエンドパフォーマンスを調査および最適化するベストプラクティスについて説明します。 開発者は、この情報を使用して各コマースプロジェクトの固有のコンテキストを調査し、サイトのパフォーマンスを向上させるためにバックエンドの設定と操作を最適化する機会を特定できます。

>[!NOTE]
>
>Recommendationsと例は、実際のクライアントエンゲージメントで objectsource が従って、高パフォーマンスのAdobe Commerceサイトを大規模に提供するプロセスに触発されています。

## 影響を受ける製品およびバージョン

[サポートされているすべてのバージョン](../../../release/versions.md) /:

- Adobe Commerce an cloud infrastructure
- Adobe Commerceオンプレミス

## パフォーマンス向上のためにデータベースを最適化

データベースの最適化は、ユーザーエクスペリエンスを強化し、売上を増やす確実な方法です。 コマースサイトの基幹となるデータベースを最適化すると、Web サイトのパフォーマンスが低下するのを防ぎ、顧客にとって摩擦を生じさせる長時間の負荷時間をなくすことができます。

### 応力試験

ブラックフライデーなどの高トラフィック期間では、コマースサイトが大量のトラフィックを処理するように要求されます。 このようなイベントに備えて、応力テストは、指数的な負荷が増加した場合にサイトがどのように動作するかを理解するのに不可欠です。

応力試験に使用できるツールの 1 つは GTmetrix です。 通常の訪問者の行動とアクションをレプリケートおよび乗算するように GTmetrix を設定して、読み込みの増加に対するサイトの対応準備状況を測定します。 次に、テストを実行して、主要な買い物イベントの間にパフォーマンスやサイトの可用性に影響を与える可能性のある問題を特定し、解決します。

高トラフィック期間に対するコマースプロジェクトの準備に関する詳細：

- [休日の準備](https://experienceleague.adobe.com/docs/events/mbi-webinars-recordings/2021/holiday-readiness.html)
- [ホリデーショッピング分析](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/performance/holiday-season-perf.html)
- [サージ容量の増加](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/2021-holiday-surge-capacity-requests-for-magento-commerce-cloud.html)

### 負荷テスト

また、GTmetrix や類似のツールを使用して、テスト用の Commerce プロジェクトを読み込むこともできます。 負荷テストは、ストレステストの前駆として、大規模な高トラフィックサイトに不可欠な手法です。 ピーク負荷時のサイトのパフォーマンスに影響を与える問題を予測および軽減することで、予期しないサイト停止、不満を抱く顧客、財務上の損失を防ぎます。

GTmetrix を使用して大量のトラフィックをシミュレートし、サイトのパフォーマンスを分析して、サイト容量に関する明確な情報を得ます。 この分析は、ボトルネックを特定して対処し、最適化する機会を特定するのに役立ち、コマースサイトが負荷の増大に伴って効果的に運用できるようにします。

Adobe Commerceプロジェクトのテストの詳細を説明します。

- [テストガイダンス](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/guidance.html)  （クラウドインフラストラクチャ）
- [アプリケーションのテスト](https://developer.adobe.com/commerce/testing/guide/)

### パフォーマンスの問題を特定して解決する

New RelicやAdobe Commerceの監視などの様々なツールを使用してボトルネックを検出し、コマースサイトを効果的に最適化することで、パフォーマンスの問題に対処します。 [New Relic](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic.html) は、クラウドインフラストラクチャ上のAdobe Commerceに含まれ、 [Adobe Commerceの観測](/help/tools/observation-for-adobe-commerce/intro.md) は、クラウドおよびオンプレミスの両方のデプロイメントに含まれています。

これらのツールを使用して、サイトのパフォーマンスを分析し、以下に関連するパフォーマンスの問題を特定します。

- CPU 負荷の高い機能
- クエリおよびバックエンド操作のキャッシュ管理設定
- サードパーティ API 呼び出し
- Cron スケジュール

例えば、製品の詳細ページとカテゴリページに焦点を当てて、トランザクションを詳細に調べることができます。 パフォーマンスを向上させるために最適化できる、時間のかかるプロセスを特定します。 あるクライアントのエンゲージメントで、 objectsource が製品の詳細ページでパフォーマンスの問題に気づき、パフォーマンス時間の 3.5%を消費していた API 呼び出しを見つけました。 この結果に基づいて、コード実行の階層を調べ、ボトルネックの原因となる問題を特定し、修正しました。

サイトのパフォーマンス管理の詳細：

- [パフォーマンスの監視](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/performance.html) （クラウドインフラストラクチャ）
- [パフォーマンス最適化のレビュー](/help/implementation-playbook/infrastructure/performance/recommendations.md)
- [設定のベストプラクティス](/help/performance/configuration.md)
- [Adobe Commerceの観測](/help/tools/observation-for-adobe-commerce/intro.md)

### MySQL のパフォーマンスの最適化

データベースのクラスタリングとクエリの最適化を実装することで、MySQL のパフォーマンスの問題に対処することは、ブラックフライデーのような高トラフィック期間の前後のパフォーマンスを向上させる有効なアプローチです。

#### データベースクラスタリングの実装

多くの場合、高トラフィックの Web サイトはデータベースのボトルネックに直面します。これは主に単一の MySQL サーバへの依存が原因です。 これらのボトルネックに対処するには、データベース・クラスタリングを導入します。これは、パフォーマンスを向上させ、高い可用性を確保する分散アーキテクチャです。

データベースクラスタリングを使用すると、複数の Web ノードを複数の MySQL サーバーに接続できるので、トラフィックのピーク時にデータベースに関する問題が及ぼす影響を最小限に抑えることができます。 Galera Cluster などのツールを使用して、コマースサイトのデータベースクラスタリングを設定します。 Galera Cluster は、 [クラウドインフラストラクチャにデプロイされたAdobe Commerceプロジェクト](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/infrastructure/cloud/technology.html).

#### MySQL クエリの最適化

通常、ほとんどのAdobe Commerceサイトのインフラストラクチャは、1 つの MySQL サーバーに接続された複数の Web ノードで構成されます。

この設定では、各フロントエンド Web ノードが Galera クラスターに接続し、複数の MySQL サーバーを使用できます。 フロントエンド Web ノードの数を増やすと、アプリケーションのパフォーマンスが向上しますが、単一の MySQL サーバーがボトルネックとなり続けます。

MySQL Server のパフォーマンスを最適化し、ボトルネックを最小限に抑えるには、不要なクエリを特定して削減する必要があります。 例えば、1 秒あたり 1,000 個のクエリを送信していて、必要なクエリは 200 個のみである場合、最適化とクエリ数の減少により、パフォーマンスが大幅に向上する可能性があります。

MySQL の設定と最適化について詳しくは、以下を参照してください。

- [データベース設定のベストプラクティス](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html)
- [Galera DB レプリケーションのレプリケーションが遅い](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/galera-db-slow-replication.html)
- [一般的な MySQL ガイドライン](/help/installation/prerequisites/database/mysql.md)
- [MySQL クエリのキャッシュ](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/mysql-query-cache.html)

## cron ジョブを効果的に管理：パフォーマンスとタイミング

Cron ジョブは、レポートの生成や製品のインデックス作成など、サイトのバックグラウンドタスクの処理にとって重要な役割を果たします。 ただし、cron ジョブの最適化では、全体的なパフォーマンスに与える影響を慎重に考慮する必要があります。 開発者は、スケジューリングの頻度を評価し、特定の要件に基づいて最適なタイミングを決定する必要があります。

パフォーマンスと利便性のバランスを取る場合、多くの場合、低トラフィック期間に cron ジョブをスケジュールすることをお勧めします。 ただし、異なるタイムゾーンでクライアントを扱う場合は課題が生じ、複数の地域で調和したエクスペリエンスを実現するための思慮深いアプローチが必要になる可能性があります。

Cron のパフォーマンスとタイミングの最適化を担当する場合は、コマース管理から現在の Cron 設定を確認し、コマースプロジェクトの Cron ジョブの設定と設定について学びます。

また、「観測 (Adobe Commerce) 」を使用して、cron 関連のパフォーマンス指標を表示することもできます。 このツールは、複数のソースからのログデータを組み合わせて、Adobe Commerceサイトのパフォーマンスの管理と問題の診断に役立ちます。

Adobe Commerce Cron の実装について詳しくは、以下を参照してください。

- [Cron（予定タスク）](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) （内） _Commerce Admin Systems ユーザーガイド_
- [アプリケーション設定 — crons プロパティ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html) （クラウドインフラストラクチャ）
- [Cron の設定と実行](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html) （オンプレミス）
- [Adobe Commerceの観測](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html) ( [!UICONTROL Cron] および [!UICONTROL MySQL] タブ )
