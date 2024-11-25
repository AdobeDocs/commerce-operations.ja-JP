---
title: バックエンドのパフォーマンスの最適化
description: Adobe Commerce Sites のバックエンドパフォーマンスの最適化について説明します。
badge: label="寄稿者：objectsource" type="Informative" url="https://objectsource.co.uk/" tooltip="objectsource"
role: Admin, User, Developer
feature: Best Practices
exl-id: 18bc97a0-3d34-4d48-a3e2-84af2da7d0d3
source-git-commit: ee7551374aa6d4ad462dd64ee3d05b934b43ce45
workflow-type: tm+mt
source-wordcount: '977'
ht-degree: 0%

---

# バックエンドのパフォーマンスを最適化するためのベストプラクティス

このトピックでは、データベースの最適化とテストに重点を置いて、Adobe Commerce Sites のバックエンドパフォーマンスを調査および最適化するためのベストプラクティスの概要を説明します。 開発者はこの情報を使用して、各Commerce プロジェクトの固有のコンテキストを調査し、バックエンドの設定と操作を最適化してサイトのパフォーマンスを向上させる機会を特定できます。

>[!NOTE]
>
>Recommendationsと例は、objectsource が実際のクライアント契約でたどるプロセスからインスピレーションを得て、パフォーマンスの高いAdobe Commerce サイトを大規模に提供します。

## 影響を受ける製品とバージョン

[ サポートされているすべてのバージョン ](../../../release/versions.md):

- クラウドインフラストラクチャー上のAdobe Commerce
- Adobe Commerce オンプレミス

## データベースを最適化してパフォーマンスを向上

データベースの最適化は、ユーザーエクスペリエンスを向上させ、売上高を増やすための確実な方法です。 Commerce サイトのバックボーンであるデータベースを最適化すると、web サイトのパフォーマンスが低下するのを防ぎ、読み込み時間が長くなることで顧客の手間をかけるのを防ぐことができます。

### 負荷試験

ブラックフライデーのようなトラフィックが多い時期には、Commerce サイトで大量のトラフィックを処理するよう求められます。 このようなイベントに備えて、負荷試験は、指数関数的な負荷の増加の下でサイトがどのように動作するかを理解するために不可欠です。

GTmetrix はストレステストに使用できるツールです。 GTmetrix を設定して、通常の訪問者の行動とアクションを再現および乗算することで、負荷の増加に対するサイトの準備状況を測定します。 次に、テストを実行して、主要な買い物イベント中にパフォーマンスとサイトの可用性に影響を与える可能性のある問題を特定し、解決します。

トラフィックが多い時期にCommerce プロジェクトを準備する方法の詳細を説明します。

- [ 休日への対応 ](https://experienceleague.adobe.com/docs/events/commerce-intelligence-webinar-recordings/2021/holiday-readiness.html)
- [ ホリデーショッピング分析 ](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/performance/holiday-season-perf.html)
- [ サージ容量増加 ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/2021-holiday-surge-capacity-requests-for-magento-commerce-cloud.html)

### 負荷テスト

GTmetrix や同様のツールを使用して、テスト用Commerce プロジェクトを読み込むこともできます。 負荷テストは、ストレステストの前段階として、大規模でトラフィックの多いサイトでは不可欠なプラクティスです。 ピーク時の負荷でサイトのパフォーマンスに影響を与える問題を予測して軽減することで、予期しないサイトの停止、フラストレーションが発生した顧客、財務上の損失を防ぎます。

GTmetrix を使用してトラフィック量の多いシミュレーションを行い、サイトのパフォーマンスを分析して、サイトの容量に関する明確な情報を取得します。 この分析は、ボトルネックを特定して対処し、最適化する機会を特定するのに役立ち、負荷が増えた場合にCommerce Sites を効果的に運用できるようになります。

Adobe Commerce プロジェクトのテストの詳細：

- [ テストガイダンス ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/guidance.html) （クラウドインフラストラクチャ）
- [ アプリケーションのテスト ](https://developer.adobe.com/commerce/testing/guide/)

### パフォーマンスの問題の特定と解決

New Relicや Observation for Commerceなどの様々なツールを使用してボトルネックを検出し、Adobe Commerce サイトを効果的に最適化することで、パフォーマンスの問題に対処します。 [New Relic](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service.html) はクラウドインフラストラクチャー上のAdobe Commerceに含まれており、[Adobe Commerceの監視 ](/help/tools/observation-for-adobe-commerce/intro.md) はクラウドとオンプレミスの両方のデプロイメントに含まれています。

これらのツールを使用して、サイトのパフォーマンスを分析し、次の項目に関連するパフォーマンスの問題を特定します。

- CPU 負荷の高い機能
- クエリおよびバックエンド操作のキャッシュ管理設定
- サードパーティ API 呼び出し
- Cron スケジュール

例えば、製品の詳細ページやカテゴリページを中心にトランザクションを詳細に調べることができます。 パフォーマンスを向上させるために最適化できる、時間がかかるプロセスを特定します。 あるクライアントエンゲージメントで、objectsource は、製品の詳細ページでパフォーマンスの問題に気づき、パフォーマンス時間の 3.5% を消費している API 呼び出しを見つけました。 この結果に基づいて、ボトルネックとなっている問題をピンポイントで特定し、修正するために、コード実行の階層を調査しました。

サイトのパフォーマンス管理の詳細：

- [ パフォーマンス監視 ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/performance.html) （クラウドインフラストラクチャ）
- [設定のベストプラクティス](/help/performance/configuration.md)
- [Adobe Commerceの監視](/help/tools/observation-for-adobe-commerce/intro.md)

### MySQL のパフォーマンスの最適化

データベースクラスタリングとクエリ最適化を実装して MySQL のパフォーマンス問題に対処することは、ブラックフライデーのようなトラフィック量の多い時期の前後でパフォーマンスを向上させるための効果的なアプローチです。

#### データベースクラスタリングの実装

高トラフィックの Web サイトは、多くの場合、データベースのボトルネックに直面します。これは主に、1 台の MySQL サーバーに依存することに起因します。 パフォーマンスの向上と高可用性の確保を実現する分散アーキテクチャであるデータベース・クラスタリングを導入することで、これらのボトルネックに対処できます。

データベースクラスタリングを使用すると、複数の web ノードを複数の MySQL サーバーに接続できるので、トラフィックのピーク時にデータベースに関する問題の影響を最小限に抑えることができます。 Galera クラスターなどのツールを使用して、Commerce サイトのデータベースクラスタリングを設定します。 Galera クラスターは、[ クラウドインフラストラクチャにデプロイされたAdobe Commerce プロジェクト ](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/infrastructure/cloud/technology.html) に含まれています。

#### MySQL クエリの最適化

通常、ほとんどのAdobe Commerce サイトのインフラストラクチャは、1 台の MySQL サーバーに接続された複数の web ノードで構成されます。

この設定では、各フロントエンド web ノードは Galera クラスターに接続され、複数の MySQL サーバーを使用できます。 フロントエンド web ノードの数を増やすと、アプリケーションのパフォーマンスが向上しますが、単一の MySQL サーバーがボトルネックのままになります。

MySQL サーバーのパフォーマンスを最適化し、ボトルネックを最小限に抑えるには、不要なクエリを特定して減らすことが不可欠です。 例えば、1 秒あたり 1,000 件のクエリを送信していて、必要なのは 200 件しかない場合、クエリ数を最適化および減らすと、パフォーマンスが大幅に向上する可能性があります。

MySQL の設定と最適化の詳細を説明します。

- [ データベース設定のベストプラクティス ](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html)
- [Galera DB レプリケーションの低速レプリケーション ](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/galera-db-slow-replication.html)
- [一般的な MySQL ガイドライン](/help/installation/prerequisites/database/mysql.md)
- [MySQL クエリキャッシュ ](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/mysql-query-cache.html)

## Cron ジョブの効果的な管理：パフォーマンスとタイミング

Cron ジョブは、レポートの生成や製品のインデックス作成など、サイトのバックグラウンドタスクを処理する上で重要な役割を果たします。 ただし、cron のジョブ最適化では、全体的なパフォーマンスに対する影響を慎重に考慮する必要があります。 開発者は、スケジュールの頻度を評価し、特定の要件に基づいて最適なタイミングを決定する必要があります。

パフォーマンスと利便性のバランスを取りながら、トラフィックが少ない時間帯に cron ジョブをスケジュールすることをお勧めします。 しかし、異なるタイムゾーンでクライアントと取引することは課題を提示する可能性があり、複数の地域で調和のとれたエクスペリエンスを確保するために思慮深いアプローチが必要となります。

Cron のパフォーマンスとタイミングの最適化を担当する場合は、Commerce管理者が現在行っている cron 設定を確認し、Commerce プロジェクトの cron ジョブの設定および設定について学習します。

また、Adobe Commerceの監視を使用して、cron 関連の業績評価指標を表示できます。 このツールは、複数のソースからのログデータを組み合わせて、Adobe Commerce サイトのパフォーマンスをより適切に管理し、問題を診断するのに役立ちます。

Adobe Commerce cron 実装の詳細情報：

- [2}Commerce管理システムユーザーガイドの {Cron （スケジュールされたタスク） ](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html)__
- [ アプリケーション設定 – crons プロパティ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html) （クラウドインフラストラクチャ）
- [cron の設定と実行 ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html) （オンプレミス）
- [Adobe Commerceの監視 ](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html) （「[!UICONTROL Cron]」タブと「[!UICONTROL MySQL]」タブを参照）。
