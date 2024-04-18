---
title: オンプレミスのインフラストラクチャ
description: Adobe Commerceのオンプレミスインフラストラクチャとサードパーティのクラウドサービスについて説明します。
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: de1467be-acec-4a0d-8229-e7e87614bc55
feature: Install
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 0%

---

# Adobe Commerceのオンプレミスインフラストラクチャ

新しいAdobe Commerceの導入を始める、または既存のオンプレミスAdobe Commerceの導入をクラウドに移行する動機は数多くありますが、最も一般的な戦略的な推進要因は、設備投資の削減、継続的なコストの削減、拡張性と弾力性の向上、市場投入までの時間の短縮、セキュリティとコンプライアンスの向上です。

次の図は、Adobe CommerceをオンプレミスのAWS インフラストラクチャにデプロイするためのリファレンスアーキテクチャを示しています。 Azure、Google Cloud、Alibaba Cloud などの他のクラウドプロバイダーも、同様のインフラストラクチャデザインと相同サービスを共有しています。

![サードパーティのクラウドサービス上の自己ホスト型Adobe Commerce インフラストラクチャを示す図](/help/assets/playbooks/on-premises-infrastructure.svg)

次に、上記のインフラストラクチャの各側面の役割と機能について詳しく説明します。

1. Amazon Route 53 は DNS 設定を提供します。

1. AWS WAF は、一般的な web 攻撃からAdobe Commerceを保護する web アプリケーションファイアウォールです。

1. Amazon CloudFront は、静的および動的 web コンテンツの配信を高速化する高速コンテンツ配信ネットワーク（CDN）です。

1. 最初の Elastic Load Balancing アプリケーションロードバランサーは、複数のアベイラビリティーゾーンにあるAWS Auto Scaling グループの Varnish インスタンス全体にトラフィックを分散させます。

1. Varnish Cache は、HTTP リバースプロキシをキャッシュする web アプリケーションアクセラレーターです。 AWS Marketplace から利用できるエンタープライズバージョンは、クラウドバックエンドと動的ホスト間のキャッシュパージをサポートするためのより良い機能を備えているので、お勧めします。

1. 2 つ目の Elastic Load Balancing アプリケーションロードバランサーは、複数のアベイラビリティーゾーンにあるAdobe Commerce インスタンスのAWS Auto Scaling グループ全体に、Varnish Cache からのトラフィックを分散させます。

1. Amazon EC2 インスタンスに最新バージョンのAdobe Commerceをインストールします。 インストールは、Adobe Commerce アプリケーション、Nginx web サーバ、および PHP で構成されています。 Amazon Machine Image （AMI）を構築し、Auto Scaling グループで新しいインスタンスを起動します。

1. Amazon Elasticsearchサービスは、Adobe Commerce カタログ検索用の管理されたElasticsearchサービスです。

1. Amazon Redis 用 ElastiCache は、データベースのキャッシュレイヤーを提供します。

1. Amazon Aurora または AmazonRDS を使用すると、データベース管理（高可用性とマルチマスター設定を含む）をシンプル化できます。

1. EFSMount Target は、Amazon Elastic File System （AmazonEFS）を Varnish およびAdobe Commerce インスタンスにマッピングするのに役立ちます。

1. Amazon EFS を使用して、Adobe Commerce インスタンス全体のワニスおよび共有メディアアセットにわたる共有設定にアクセスします。

## クラウドサービス

AWSは、Adobe Commerce環境でAWS上の DevOps プロセスを可能にするサポートテクノロジープラットフォームを提供するだけでなく、（不在時に）既存の Software Configuration Management （SCM）ソリューションを提供または拡張できる一連のサービスを提供します。 これには、AWSCodeCommit、AWSCodeBuild、AWSCodePipeline、AWSCodeDeploy が含まれます。これらのサービスを使用すると、ソース管理、ビルド、継続的統合/継続的デプロイメント（CI/CD）、デプロイメントサービスを実行できます。

## クラウドの移行

Adobe CommerceからAWSへの移行に関する価値提案は、運用に関するインサイトと俊敏性を提供する複数のサービスの利用によってさらに強化されます。 つまり、技術的な観点（1 時間あたりのリクエスト数など）だけでなく、ビジネス運用上の観点（1 時間あたりの注文数など）からも、プラットフォームに関する運用上のインサイトを得ることができます。特に、2 つのデータセットが既婚の可能性がある場合に有効です。 これにより、キャンペーンのパフォーマンス、プラットフォームの運用コスト、その他の指標がほぼ無限にリアルタイムで表示されます。

Adobe CommerceをAWSにセットアップすると、特定のアプリケーションの依存関係を、クラウドで使用可能な完全に管理された代替手段に置き換えることができます。 例えば、EC2 インスタンスでリレーショナルデータベースを直接ホストするのではなく、多くのアプリケーションのデータベースをAmazon リレーショナルデータベースサービス（AmazonRDS）で簡単に置き換えることができます。 この戦略の利点は、コアアプリケーションを大幅に変更することなく、未分化のコンポーネントの運用責任をAWSにオフロードできることです。

AWS上でAdobe Commerceを実行する場合に使用できるデプロイメントオプションはいくつかあります。 どの選択肢が最適かは、コスト、拡張性、可用性、柔軟性の要件のほか、AWSとAdobe Commerceのスキルによっても異なります。

{{$include /help/_includes/hosting-related-links.md}}
