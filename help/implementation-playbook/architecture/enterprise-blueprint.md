---
title: エンタープライズリファレンスアーキテクチャ
description: Adobeの最新の合成可能なコマーステクノロジーを使用してAdobe Commerceを実装する方法を説明します。
feature: App Builder, Cloud, GraphQL, Integration, Paas, Saas
exl-id: d066ab43-20e2-4e0b-8348-0c52d6a7ac8a
source-git-commit: 8eab688ed98eb1b9fcf4fc25f90fe2bbf99c02d6
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 0%

---

# Adobe Commerce enterprise reference architecture

Adobe Commerceは、ビジネスの成果を高める優れたエクスペリエンスを作成するサービスで、技術的な柔軟性と使いやすさを独自に組み合わせた、経験豊富なプラットフォームです。

コマースは、パフォーマンス、規模、セキュリティに関する企業の要件を満たすように進化しました。 企業の成功には、Adobeの最新の合成可能なコマースソリューションを使用する最新の実装アプローチを採用することが不可欠です。 ここでは、最新の Commerce 実装アプローチについて技術的に詳しく説明します。

次のアーキテクチャ図は、Adobe CommerceとすべてのAdobe Experience Cloudソリューションとの間のデータフローを示しています。

![Adobe CommerceがExperience Cloudソリューションに接続する方法を示すアーキテクチャ図](../../assets/playbooks/commerce-architecture-v2.svg){zoomable=&quot;yes&quot;}

>[!NOTE]
>
>図に示す概要レベルのデータフローは、ほとんどの企業の実装で一貫しています。 実装を一意にできる主要なコンポーネントは、カタログを作成する方法です（特に B2B の場合）。 カタログアーキテクチャを [コマース Web API](https://developer.adobe.com/commerce/webapi/get-started/).

## クラウド基盤

[Adobe Commerce an cloud infrastructure](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/overview) は、コマース実装の基盤です。 これにより、 [secure](../../security-and-compliance/shared-responsibility.md) クラウドネイティブな環境でコマースアプリケーションを構築、デプロイ、監視、管理するセルフサービスアプローチを備えた、自動ホスティングプラットフォーム。

次の Cloud Foundation の技術的詳細を参照してください。

- [**拡張アーキテクチャ**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture) — 容量を自動的に調整し、安定した予測可能なパフォーマンスを維持
- [**複数の環境**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture)—PHP、MySQL(MariaDB)、Redis、RabbitMQ、およびサポートされる検索エンジンテクノロジーを使用して事前にプロビジョニングされ、サイトの開発、テスト、デプロイを行います。
- [**設定の管理**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/overview) — カスタマイズ可能な環境設定ファイルと CLI（コマンドラインインターフェイス）を使用して、アプリケーション設定、ルート、ビルド、デプロイアクション、および通知を管理します。
- [**Git ベースのワークフロー**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow) — コードの変更をプッシュした後、自動的にビルドおよびデプロイし、迅速な開発と継続的な導入を実現
- [**組み込みの観察性**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/performance) — 複数のソースからのログデータを組み合わせて、サイトのパフォーマンスの管理や問題の診断に役立つツール
- [**包括的な API カバレッジ**](https://developer.adobe.com/commerce/webapi/get-started/)—[GraphQL](https://developer.adobe.com/commerce/webapi/graphql/) および [REST](https://developer.adobe.com/commerce/webapi/rest) コアコマースアプリケーションをサードパーティのシステムと統合し、コマース機能を拡張するための API

## Experience Cloudとの統合

Adobe CommerceはすべてのExperience Cloudソリューションを統合して提供 [規模に応じてパーソナライズされたコマースエクスペリエンス](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/customers-menu/personalize-scale#customers-menu).

[データ接続](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/overview) 買い物客の購入行動に関するインサイトをアンロックして、他のAdobeのデジタルエクスペリエンス製品と共に、すべてのチャネルをまたいでパーソナライズされたショッピングエクスペリエンスを作成できます。

>[!NOTE]
>
>詳しくは、 [デジタルエクスペリエンスのブループリント](https://experienceleague.adobe.com/en/docs/blueprints-learn/architecture/overview) を参照してください。


## サードパーティ製システムとの統合

Adobeは、コアコマース機能を拡張し、コマースをサードパーティのシステム（CRM、ERPS、PIMS など）と統合するアプリケーションを構築するための、包括的な拡張ポイントとツールを開発者に提供します。 これらのツールを使用すると、次の方法でプラットフォームの総所有コストを削減できます。

- **拡張性**：アプリケーションをコア・ソフトウェアとは別に拡張できるため、効率性が高く、アップグレードが簡単になります。
- **分離** — 独立した環境とは、開発者が、コアリリースに依存することなく、自分の判断で拡張機能をアップグレードまたは変更できることを意味します。
- **技術的独立性** — 開発者は、どのテクノロジースタックと、ニーズに合うコーディング言語を選択できます。

Adobeは、統合とカスタマイズを構築するための次の開発者ツールを提供します。

- [**Adobe Developer App Builder の API メッシュ**](https://developer.adobe.com/graphql-mesh-gateway/) — 複数の API、GraphQL、REST および他のソースを調整して結合し、1 つのクエリ可能なGraphQLエンドポイントにします。
- [**App Builder**](https://developer.adobe.com/app-builder/docs/overview/) — コマース機能を拡張し、サードパーティのソリューションと統合する、安全で拡張性の高い Web アプリケーションを構築およびデプロイします。
- [**イベント**](https://developer.adobe.com/commerce/extensibility/events/) — カスタムイベントトリガーを使用して、他の拡張可能な開発ツールとやり取りします。
- [**ウェブフック**](https://developer.adobe.com/commerce/extensibility/webhooks/)- Commerce とサードパーティシステム間のやり取りを自動的にトリガー化するには、Web フックを使用します。
- [**管理 UI SDK**](https://developer.adobe.com/commerce/extensibility/admin-ui-sdk/) — マーチャント向けの新しいページや機能を使用して、コマース管理をカスタマイズおよび拡張します。

## ストアフロントサービス

Adobeは、主要なビジネス目標をサポートするのに役立つ、インテリジェントで合成可能なマーチャンダイジングサービスの豊富なセットを提供します。 また、これらのサービスは、パフォーマンスを大規模に最適化する上で重要な API も提供します。

- [ライブ検索](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/overview) — この AI を利用した検索ツールを使用して、よりスマートで迅速かつ関連性の高い結果を買い物客に提供します。
- [製品Recommendations](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/overview) — 買い物客の行動、人気の傾向、製品の類似性などに基づいて、AI によるレコメンデーションを追加します。
- [カタログサービス](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/catalog-service/guide-overview) — パフォーマンスを向上させ、拡張性を向上させ、コンバージョンを増やしながら、最適化された製品エクスペリエンスを提供します。
- [支払いサービス](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/payment-services/guide-overview) — 無利子支払いの分割払い、支払処理、注文、請求書の一目での表示など、様々な支払い方法を提供することで、顧客満足度を高めます。

## ヘッドレスストアフロント

ヘッドレスコマースは API ファーストのコマースです。 Adobe Commerceは、GraphQL API レイヤーを通じてすべてのコマースサービスとデータを提供する、切り離されたアーキテクチャに完全にヘッドレスです。 このアーキテクチャにより、チームは、コアアプリケーションとは独立したフロントエンドを開発でき、新しいテクノロジーを使用して新しいタッチポイントを迅速に構築し、テストする機敏性を提供します。

Adobeは、が提供するのと同じ利点と機能を備えた、最新のヘッドレスストアフロントテクノロジーを提供します。 [Edge Delivery Services](https://www.aem.live/home) ドキュメントベースのオーサリング、パフォーマンスに優れたアーキテクチャ、標準のネイティブ実験を使用できます。 Adobe Commerceの規模とパフォーマンスを活用します。 [storefront サービス](#storefront-services) そしての柔軟性と利便性 [ドロップインコンポーネント](https://experienceleague.adobe.com/developer/commerce/storefront/) コマース機能を提供する。

