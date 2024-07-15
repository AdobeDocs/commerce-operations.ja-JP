---
title: エンタープライズ向けリファレンスアーキテクチャ
description: Adobeの最新の構成可能なコマーステクノロジーを使用してAdobe Commerceを実装する方法を説明します。
feature: App Builder, Cloud, GraphQL, Integration, Paas, Saas
exl-id: d066ab43-20e2-4e0b-8348-0c52d6a7ac8a
source-git-commit: c2f6b7125f1a611e94f807999787fee48a0e5ece
workflow-type: tm+mt
source-wordcount: '797'
ht-degree: 0%

---

# Adobe Commerce enterprise リファレンスアーキテクチャ

Adobe Commerceは、技術的な柔軟性と使いやすさを独自に組み合わせたエクスペリエンス主導のプラットフォームであり、ビジネスの成果を導く優れたエクスペリエンスを提供します。

Commerceは、パフォーマンス、拡張性、セキュリティに関する大規模企業の要件を満たすように進化してきました。 Adobeの最新のコンポーザブルコマースソリューションを使用する最新の実装アプローチを採用することは、大規模法人の成功にとって重要です。 ここでは、最新のCommerce実装アプローチの技術的な詳細について説明します。

次のアーキテクチャ図は、Adobe CommerceとすべてのAdobe Experience Cloud ソリューション間のデータフローを示しています。

![Adobe CommerceとExperience Cloudソリューションの連携を示すアーキテクチャ図 ](../../assets/playbooks/commerce-architecture-v3.svg){zoomable="yes"}

>[!NOTE]
>
>図に示す大まかなデータフローは、ほとんどのエンタープライズ実装で一貫しています。 実装を一意にできる重要なコンポーネントは、カタログを作成する方法です（特に B2B の場合）。 カタログアーキテクチャを [Commerce web API](https://developer.adobe.com/commerce/webapi/get-started/) に慎重にマッピングする必要があります。

## クラウド基盤

[ クラウドインフラストラクチャー上のAdobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/overview) は、Commerce実装の基盤となります。 クラウドネイティブ環境でCommerce アプリケーションを構築、デプロイ、モニタリング、管理するためのセルフサービスアプローチを備えた [ セキュア ](../../security-and-compliance/shared-responsibility.md) 自動ホスティングプラットフォームを提供します。

Cloud Foundation の技術的な詳細については、以下を参照してください。

- [**拡張アーキテクチャ**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture)：容量を自動的に調整して、安定した予測可能なパフォーマンスを維持
- [**複数の環境**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture) - PHP、MySQL （MariaDB）、Redis、RabbitMQ、およびサポートされている検索エンジンテクノロジーを使用して事前にプロビジョニングされ、サイトの開発、テスト、デプロイが行われます。
- [**構成管理**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/overview) - カスタマイズ可能な環境設定ファイルと CLI （コマンド・ライン・インタフェース）により、アプリケーション設定、ルート、アクション、通知の作成と展開を管理します。
- [**Git ベースのワークフロー**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow) – 迅速な開発と継続的なデプロイメントを実現するために、コードの変更をプッシュした後に、自動的にビルドおよびデプロイします
- [**組み込みの可観測性**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/performance) – 複数のソースからのログデータを組み合わせて、サイトのパフォーマンスの管理と問題の診断に役立つツール
- コアのCommerce アプリケーションをサードパーティシステムと統合し、GraphQLの機能を拡張するための [**包括的な API の対象範囲**](https://developer.adobe.com/commerce/webapi/get-started/)—[Commerce](https://developer.adobe.com/commerce/webapi/graphql/) および [REST](https://developer.adobe.com/commerce/webapi/rest) API

## Experience Cloudとの統合

Adobe Commerceは、すべてのExperience Cloudソリューションと統合して、[ パーソナライズされたコマースエクスペリエンスを大規模に ](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/customers-menu/personalize-scale#customers-menu) 提供します。

[Data Connection](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/overview) を使用すると、買い物客の購買行動に関するインサイトを解き放ち、他のAdobeデジタルエクスペリエンス製品と共に、すべてのチャネルにわたってパーソナライズされたショッピングエクスペリエンスを作成できます。

>[!NOTE]
>
>技術的な詳細については、[ デジタルエクスペリエンスブループリント ](https://experienceleague.adobe.com/en/docs/blueprints-learn/architecture/overview) を参照してください。


## サードパーティシステムとの統合

Adobeは、Commerceのコア機能を拡張するアプリケーションを構築し、Commerceをサードパーティシステム（CRM、ERPS、PIMS など）と統合するための包括的な拡張ポイントとツールを開発者に提供します。 これらのツールは、次の方法でプラットフォームの総所有コストを削減します。

- **拡張性**：アプリケーションをコア・ソフトウェアとは別に拡張できるため、効率性が向上し、アップグレードが容易になります。
- **分離** – 分離された環境とは、開発者がコアリリースに頼らずに自分の裁量で拡張機能をアップグレードまたは変更できることを意味します。
- **技術的独立性** – 開発者は、ニーズに合ったテクノロジースタックとコーディング言語を選択できます。

Adobeは、統合とカスタマイズを構築するための以下の開発ツールを提供しています。

- [**Adobe Developer App Builderの API メッシュ**](https://developer.adobe.com/graphql-mesh-gateway/) – 複数の API、GraphQL、REST、その他のソースを調整し、1 つのクエリ可能なGraphQL エンドポイントに組み合わせます。
- [**App Builder**](https://developer.adobe.com/app-builder/docs/overview/) - Commerce機能を拡張し、サードパーティのソリューションと統合する、セキュリティで保護されたスケーラブルな web アプリケーションを構築およびデプロイします。
- [**イベント**](https://developer.adobe.com/commerce/extensibility/events/) - カスタムイベントトリガーを使用して、その他の拡張可能な開発ツールとやり取りします。
- [**Webhook**](https://developer.adobe.com/commerce/extensibility/webhooks/) - Webhook を使用すると、Commerceとサードパーティシステム間のインタラクションを自動的にトリガー化できます。
- [**管理 UI SDK**](https://developer.adobe.com/commerce/extensibility/admin-ui-sdk/) - マーチャント向けの新しいページと機能で、Commerce管理者をカスタマイズおよび強化します。

## ストアフロントサービス

Adobeは、主要なビジネス目標をサポートするのに役立つ、インテリジェントで構成可能なマーチャンダイジングサービスの豊富なセットを提供します。 また、これらのサービスは、パフォーマンスを大規模に最適化するために重要な API も提供します。

- [ ライブ検索 ](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/overview) – この AI を活用した検索ツールにより、買い物客によりスマートで迅速かつ適切な結果を提供します。
- [ 商品Recommendations](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/overview) – 買い物客の行動、人気のトレンド、商品の類似性などに基づいて、AI を活用したレコメンデーションを追加します。
- [ カタログサービス ](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/catalog-service/guide-overview) – 顧客に最適化された製品体験を提供すると同時に、パフォーマンスの向上、スケーラビリティの向上、コンバージョンの増加を実現します。
- [ 支払いサービス ](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/payment-services/guide-overview)：利息なしの分割払い、支払い処理、オーダー、請求書の単一ビューなど、さまざまな支払い方法を提供することにより、顧客満足度を向上させます。

## ヘッドレスストアフロント

ヘッドレスコマースは API ファーストのコマースです。 Adobe Commerceは、GraphQL API レイヤーを通じてすべてのコマースサービスとデータを提供する、分離されたアーキテクチャを持つ、完全なヘッドレスです。 このアーキテクチャにより、チームはコアアプリケーションとは独立してフロントエンドを開発でき、新しいテクノロジーを使用して新しいタッチポイントを迅速に構築およびテストする俊敏性が提供されます。

Adobeは、[Edge Delivery Servicesと同じ利点と機能を備えた最新のヘッドレスストアフロントテクノロジーを提供し ](https://www.aem.live/home) ドキュメントベースのオーサリング、パフォーマンスを重視したアーキテクチャ、標準のネイティブ実験を実現します。 Adobe Commerce[ ストアフロントサービス ](#storefront-services) の拡張性とパフォーマンス、および [ ドロップインコンポーネント ](https://experienceleague.adobe.com/developer/commerce/storefront/) の柔軟性と利便性を活用して、コマース機能を提供します。

