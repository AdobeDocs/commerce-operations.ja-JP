---
title: オンプレミスインフラストラクチャ
description: Adobe Commerceオンプレミスのインフラストラクチャとサードパーティのクラウドサービスについて説明します。
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: de1467be-acec-4a0d-8229-e7e87614bc55
feature: Install
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '631'
ht-degree: 0%

---

# Adobe Commerceオンプレミスインフラ

新しいAdobe Commerceの実装を開始したり、既存のオンプレミスAdobe Commerceの実装をクラウドに移行したりする動機は多数ありますが、最も一般的な戦略的要因は、設備投資の削減、継続的なコストの削減、拡張性と弾力性の向上、市場投入時間の向上、セキュリティとコンプライアンスの向上です。

次の図は、AWSインフラストラクチャにAdobe Commerceをオンプレミスでデプロイするための参照アーキテクチャを示しています。 Azure、Google Cloud、Alibaba Cloud などの他のクラウドプロバイダーは、同様のインフラストラクチャ設計と相同サービスを共有しています。

![サードパーティのクラウドサービスで自己ホスト型のAdobe Commerceインフラストラクチャを示す図](/help/assets/playbooks/on-premises-infrastructure.svg)

ここでは、上に示したインフラストラクチャの各側面の役割と機能について詳しく説明します。

1. Amazon Route 53 は DNS 設定を提供します。

1. AWS WAF は、一般的な Web の弱点を悪用してAdobe Commerceを保護する Web アプリケーションファイアウォールです。

1. Amazon CloudFront は、静的および動的な Web コンテンツの配信を高速化する高速なコンテンツ配信ネットワーク (CDN) です。

1. 最初の Elastic Load Balancing アプリケーションロードバランサーは、複数のアベイラビリティーゾーンのAWS Auto Scaling グループ内の Varnish インスタンス間でトラフィックを分散します。

1. Vanish Cache は、HTTP リバースプロキシをキャッシュする Web アプリケーションアクセラレータです。 AWS Marketplace で利用可能なエンタープライズバージョンは、動的ホスト間でのクラウドバックエンドとキャッシュのパージをサポートするための機能が強化されたので、お勧めします。

1. 2 つ目の Elastic Load Balancing アプリケーションロードバランサーは、複数のアベイラビリティーゾーンにあるAdobe CommerceインスタンスのAWS Auto Scaling グループ全体に Vanish Cache からのトラフィックを分配します。

1. 最新バージョンのMagento Open SourceまたはAdobe CommerceをAmazon EC2 インスタンスにインストールします。 インストールは、Adobe Commerceアプリケーション、Nginx Web サーバー、PHP で構成されます。 Amazon機械画像 (AMI) を作成して、自動スケーリンググループの新しいインスタンスを起動します。

1. AmazonElasticsearchサービスは、Adobe Commerceカタログ検索用のElasticsearch管理サービスです。

1. Amazon ElastiCache for Redis は、データベース用のキャッシュ層を提供します。

1. Amazon Aurora または AmazonRDS を使用して、データベース管理（高可用性およびマルチマスター設定を含む）をシンプル化します。

1. EFSMount Target は、Amazon Elastic File System(AmazonEFS) を Varnish およびAdobe Commerceインスタンスにマッピングするのを容易にします。

1. Amazon EFS を使用して、Vanish 全体で共有設定にアクセスし、Adobe Commerceインスタンス全体で共有メディアアセットにアクセスします。

## クラウドサービス

AWSは、Adobe Commerce環境におけるAWSでの DevOps プロセスを有効にするためのサポートテクノロジープラットフォームを提供するほか、（がない場合に）提供したり、既存のソフトウェア設定管理 (SCM) ソリューションを拡張したりできるサービスの集まりを提供します。 これには、AWSCodeCommit、AWSCodeBuild、AWSCodePipeline、AWSCodeDeploy が含まれます。この AWSCodeDeploy では、管理されたソース管理、ビルド、継続的統合/継続的デプロイメント (CI/CD)、デプロイメントサービスを実行できます。

## クラウドの移行

Adobe CommerceからAWSへの移行に対する価値提案は、運用上のインサイトと機敏性を提供するいくつかのサービスが利用可能になることで、さらに強化されています。 つまり、技術的な観点（1 時間あたりのリクエスト数など）だけでなく、ビジネス運用の観点（1 時間あたりの注文数など）、特に 2 組のデータを結婚できる場合に、プラットフォームに対する運用上のインサイトです。 これにより、キャンペーンのパフォーマンス、プラットフォーム運用コスト、その他の指標の数がほぼ無限に多く、ほぼリアルタイムで調べられます。

Adobe CommerceをAWSに設定すると、特定のアプリケーションの依存関係を、クラウドで使用可能な完全に管理された代替オプションに置き換えることができます。 例えば、EC2 インスタンス上にリレーショナルデータベースを直接ホストするのではなく、多くのアプリケーションのデータベースをAmazonリレーショナルデータベースサービス (AmazonRDS) で簡単に置き換えることができます。 この戦略の利点は、未分化のコンポーネントの動作責任を、コアアプリケーションに大きな変更を加えることなく、AWSにオフロードできる点です。

AWS上でAdobe Commerce(Magento Open Source版とAdobe Commerce版の両方 ) を実行する場合に使用できる複数のデプロイメントオプションがあります。 最も適切な選択は、コスト、規模、可用性、柔軟性に関する要件と、組織のAWSおよびAdobe Commerceのスキルに応じて異なります。

{{$include /help/_includes/hosting-related-links.md}}
