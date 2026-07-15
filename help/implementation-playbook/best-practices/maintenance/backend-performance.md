---
title: バックエンドパフォーマンスの最適化
description: Adobe Commerce Sitesのバックエンドのパフォーマンスを最適化する方法について説明します。
badge: label="協力：objectsource" type="Informative" url="https://objectsource.co.uk/" tooltip="objectsource"
role: Admin, User, Developer
feature: Best Practices
exl-id: 18bc97a0-3d34-4d48-a3e2-84af2da7d0d3
source-git-commit: d884d434e696a911de626dc76983468556cf451f
workflow-type: tm+mt
source-wordcount: '1157'
ht-degree: 0%

---

# バックエンドパフォーマンスを最適化するためのベストプラクティス

このトピックでは、データベースの最適化とテストに重点を置いて、Adobe Commerce サイトのバックエンドパフォーマンスを調査および最適化するためのベストプラクティスについて説明します。 開発者は、このデータを使用して、各Commerceプロジェクトの固有のコンテキストを調査し、バックエンドの設定と運用を最適化してサイトパフォーマンスを向上させる機会を特定できます。

>[!NOTE]
>
>レコメンデーションと例は、objectsourceが実際の顧客エンゲージメントに従って、パフォーマンスの高いAdobe Commerce サイトを大規模に提供するプロセスから着想を得ています。

## 影響を受ける製品とバージョン

[&#x200B; サポートされているすべてのバージョン &#x200B;](../../../release/versions.md) /:

- Adobe Commerce on cloud infrastructure
- Adobe Commerce オンプレミス

## パフォーマンスを向上させるためにデータベースを最適化する

データベースの最適化は、ユーザーエクスペリエンスを向上させ、売上を増加させるための優れた方法です。 Commerceサイトのバックボーンであるデータベースを最適化することで、web サイトのパフォーマンスの低下を防ぎ、顧客がつまずきやすい長い読み込み時間を排除することができます。

### ストレステスト

ブラックフライデーのようなトラフィックの多い時期には、Commerceのサイトが大量のトラフィックを処理することが求められます。 このようなイベントに備えるためには、負荷が急激に増加する中でサイトの動作を理解するために、ストレステストが不可欠です。

ストレステストに使用できるツールの1つがGTmetrixです。 Gtmetrixを設定して、通常の訪問者の行動とアクションを再現し、乗算することで、サイトの読み込み増加に対する準備状況を測定します。 その後、テストを実行して、主要なショッピングイベント中のパフォーマンスとサイトの可用性に影響を与える可能性のある問題を特定し、解決します。

Commerce プロジェクトのトラフィック量が多い時間帯の準備について詳しくは、以下を参照してください。

- [ホリデーシーズン](https://experienceleague.adobe.com/docs/events/commerce-intelligence-webinar-recordings/2021/holiday-readiness.html?lang=ja)
- [ホリデーショッピングの分析](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/performance/holiday-season-perf.html?lang=ja)
- [サージキャパシティの増加](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/2021-holiday-surge-capacity-requests-for-magento-commerce-cloud.html?lang=ja)

### 負荷テスト

また、GTmetrixなどのツールを使用して、テスト用のCommerce プロジェクトを読み込むこともできます。 負荷テストは、負荷テストの先駆者として、大規模でトラフィックの多いサイトに不可欠な手法です。 ピーク時の読み込み時にサイトパフォーマンスに影響を与える問題を予測して軽減することで、予期しないサイトの停止、顧客の不満、経済的損失を防ぎます。

Gtmetrixを使用して大量のトラフィックをシミュレートし、サイトのパフォーマンスを分析して、サイトのキャパシティに関する明確な情報を取得します。 この分析は、ボトルネックを特定して対処し、最適化する機会を特定するのに役立ちます。これにより、負荷が増加した場合でもCommerceのサイトが効果的に動作できるようになります。

Adobe Commerce プロジェクトのテストについて詳しくは、次を参照してください。

- [&#x200B; ガイダンスのテスト &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/guidance.html?lang=ja) （クラウド インフラストラクチャ）
- [アプリケーションテスト](https://developer.adobe.com/commerce/testing/guide/)

### パフォーマンスの問題を特定して解決する

New RelicやObservation for Adobe Commerceなどのさまざまなツールを使用して、ボトルネックを検出し、Commerceサイトを効果的に最適化することで、パフォーマンスの問題に対処します。 [New Relic](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service.html?lang=ja)はAdobe Commerce on cloud infrastructureに含まれており、Adobe Commerce[&#128279;](/help/tools/observation-for-adobe-commerce/intro.md)のObservationはクラウドとオンプレミスの両方のデプロイメントに含まれています。

これらのツールを使用して、サイトパフォーマンスを分析し、次に関連するパフォーマンスの問題を特定します。

- CPUを多用した機能
- クエリとバックエンド操作のキャッシュ管理設定
- サードパーティ API呼び出し
- Cron スケジュール

例えば、商品の詳細ページとカテゴリーページに焦点を当てて、取引を綿密に調査できます。 パフォーマンスを向上させるために最適化できる、時間のかかるプロセスを特定します。 ある顧客とのエンゲージメントにおいて、objectsourceは商品の詳細ページでパフォーマンスの問題に気づき、パフォーマンス時間の3.5%を費やしていたAPI呼び出しを発見しました。 この結果に基づいて、コード実行の階層を調べ、ボトルネックの原因となる問題を特定して修正しました。

サイトパフォーマンスの管理について詳しく見る：

- [&#x200B; パフォーマンスの監視](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/performance.html?lang=ja) （クラウド インフラストラクチャ）
- [設定のベストプラクティス](/help/performance/configuration.md)
- [Adobe Commerceの観測](/help/tools/observation-for-adobe-commerce/intro.md)

### MySQL パフォーマンスの最適化

データベースのクラスタリングとクエリの最適化を実装してMySQLのパフォーマンス問題に対処することは、ブラックフライデーのようなトラフィックの多い時間前と時間中にパフォーマンスを向上させるための効果的なアプローチです。

#### データベースクラスタリングの実装

トラフィックの多いweb サイトは、主に単一のMySQL サーバーへの依存によって、データベースのボトルネックに直面することがよくあります。 パフォーマンスを向上させ、高可用性を確保する分散型アーキテクチャであるデータベースクラスタリングを導入することで、これらのボトルネックに対処できます。

データベースクラスタリングは、複数のweb ノードを複数のMySQL サーバーに接続できるようにすることで、トラフィックのピーク時におけるデータベース関連の問題の影響を最小限に抑えます。 Galera Clusterなどのツールを使用して、Commerce サイトのデータベースクラスタリングを設定します。 Galera Clusterは、[&#x200B; クラウドインフラストラクチャにデプロイされたAdobe Commerce プロジェクト &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-cloud-service/user-guide/architecture/pro-architecture)に含まれています。

#### MySQL クエリの最適化

通常、ほとんどのAdobe Commerce サイトのインフラストラクチャは、1台のMySQL サーバーに接続された複数のweb ノードで構成されます。

この設定では、各フロントエンド web ノードがGalera クラスターに接続し、複数のMySQL サーバーを使用できます。 フロントエンド web ノードの数を増やすと、アプリケーションのパフォーマンスが向上しますが、単一のMySQL サーバーがボトルネックのままになります。

MySQL サーバーのパフォーマンスを最適化し、ボトルネックを最小限に抑えるには、不要なクエリを特定して削減することが不可欠です。 例えば、1秒間に1,000件のクエリを送信するものの、200件しか必要ない場合、クエリ数を最適化および削減することでパフォーマンスを大幅に向上できます。

MySQLの設定と最適化について詳しくは、以下を参照してください。

- [データベース設定のベストプラクティス](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html?lang=ja)
- [Galera DB レプリケーションのレプリケーションが遅い](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/galera-db-slow-replication.html?lang=ja)
- [一般的なMySQL ガイドライン](/help/installation/prerequisites/database/mysql.md)
- [MySQL クエリのキャッシュ](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/mysql-query-cache.html?lang=ja)

## cron ジョブの効果的な管理：パフォーマンスとタイミング

Cron ジョブは、レポートの生成や製品のインデックス作成など、サイトのバックグラウンド タスクを処理する上で重要な役割を果たします。 ただし、cron ジョブの最適化には、全体的なパフォーマンスに対する影響を慎重に考慮する必要があります。 開発者は、スケジュール設定の頻度を評価し、特定の要件にもとづいて最適なタイミングを決定する必要があります。

パフォーマンスと利便性のバランスを取りながら、トラフィックの少ない期間にcron ジョブをスケジュールすることをお勧めします。 しかし、異なるタイムゾーンの顧客に対応する場合、複数の地域をまたいで調和の取れた体験を提供するために、入念なアプローチが必要になり、課題が生じる可能性があります。

cronのパフォーマンスとタイミングの最適化を担当する場合は、Commerce管理者から現在のcron設定を確認し、Commerce プロジェクトのcron ジョブの設定と設定について説明します。

また、Adobe CommerceのObservationを使用して、cron関連の業績評価指標を表示することもできます。 複数のソースから収集したログデータを組み合わせることで、Adobe Commerceサイトのパフォーマンスをより適切に管理し、問題を診断できます。

Adobe Commerce cronの導入について詳しく見る：

- _Commerce Admin Systems ユーザーガイド_&#x200B;の[Cron （スケジュール済みタスク） &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html?lang=ja)
- [&#x200B; アプリケーション設定 – crons プロパティ &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html?lang=ja) （クラウドインフラストラクチャ）
- [crons](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html?lang=ja)の設定と実行（オンプレミス）
- Adobe Commerce[&#128279;](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html?lang=ja)の観察（[!UICONTROL Cron]および[!UICONTROL MySQL] タブを参照）
