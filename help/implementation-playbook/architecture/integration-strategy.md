---
title: Adobe Commerce統合戦略
description: Adobe Commerce実装の統合戦略とオプションを確認します。
exl-id: af7cc59a-3ee2-461a-8489-a35fe0288277
source-git-commit: 639dca9ee715f2f9ca7272d3b951d3315a85346c
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# Adobe Commerce統合戦略

プラットフォームを統合する機能は「非交渉」です。 企業は、さまざまなタッチポイントからアクセス可能な e コマースプラットフォームを求め、特に ERP に対応するテクノロジーシステムにシームレスに統合されています。 カスタマイズ性、グローバルな拡張性、手頃な価格も、最終的なプラットフォーム購入において重要な役割を果たします。

ストアフロントとバックエンドの両方のシステムの総合的な統合アプローチは、パフォーマンスの高い GraphQL API、包括的な REST API、Adobe Commerceと他のシステムまたはサービスとの間のバッチファイルインポートでサポートされます。

Adobe Commerce GraphQL API は、次のような他のストアフロントとの統合に使用できる、包括的なストアフロントカバレッジを提供します。

- Adobe Experience Managerや Bloomreach などのデジタルエクスペリエンスプラットフォーム (DXP)
- Drupal や WordPress などのコンテンツ管理システム (CMS)
- Adobe Commerce、PWA Studio、Vue Storefront などの最新のカスタムストアフロントアプリケーション

GraphQL は、効率的でチャネル固有の応答、データの過剰取得なし、新しいタッチポイント機能の迅速なデプロイメントを提供します。 また、モバイルネイティブアプリ、POS、IoT、ソーシャルチャネル、Facebook、Google、Instagram、WeChat、TikTokなどのライブストリームコマースチャネルなどのセールスチャネルとの統合も選択されます。

Adobe Commerce REST API は、製品やカタログを含む、包括的なシステム設定範囲とデータ管理機能を提供します。買い物かご、見積もり、チェックアウト顧客、アカウント、会社注文と返品。 REST API は一括操作、複数の認証モード、詳細な認証をサポートするので、多くの場合、REST API は次のようなエンタープライズシステムと統合するように選択されます。

- SAP などのエンタープライズ・リソース・プランニング (ERP) システム
- Akeneo などの製品情報管理 (PIM) システム
- Salesforce などの顧客関係管理 (CRM) システム
- MOM、マンハッタン、SAP などの注文管理システム (OMS)
- oracle、NetSuite、SAP WM などの Warehouse Management System(WMS) またはサード・パーティ製ロジスティクス (3PL)
- SalesforceCPQ のような構成、価格、見積 (CPQ)
- デジタルアセット管理 (DAM)(AdobeDAM など )

また、ERP や PIM などのエンタープライズシステムを統合する場合は、バッチファイルのインポートも適した方法と見なされます。データの変更頻度が低く、多くの場合、スケジュールされたファイルのインポートでパフォーマンスが向上します。 そのため、バッチファイルのインポートは、通常、毎日/毎週の一括データ同期と月次の完全データ同期で選択されます。一方、REST API は、パフォーマンスを向上させるために、増分データ変更同期で選択されます。 また、これはスケジュールされたジョブと見なされるだけですが、ビジネスニーズに応じて、頻繁に（15 分から 1 時間ごとに）おこなうことができます。

## 統合オプション

Adobe Commerceには、次の 3 つの柔軟な統合オプションが用意されています。

- 事前に構築されたコネクタを使用した、システム間の直接統合。 一部のシステムでは、Adobe Commerce Marketplace または独自の Web サイトに既にAdobe Commerce拡張機能が存在している場合があります。

- カスタムミドルウェアによるシステム間の統合。 展開されたカスタムミドルウェアソリューションは、プロセスデータのマッピング、翻訳、管理に使用されます。

- iPaaS(Integration Platform-as-a-Service) を通じたシステム間の統合 (EAI(Enterprise Application Integration Platform) とも呼ばれます。Mulesoft、Boomi、Software AG など。

![Adobe Commerce統合オプション](../../assets/playbooks/integration-options.svg)

通常、リアルタイム統合が必要ですが、一部のシナリオでは必要ありません。 Adobe Commerceネイティブサポート [!DNL RabbitMQ] 非同期プロセスを有効にするメッセージバスとして。非同期プロセスを有効にすることをお勧めします。これは、リアルタイムで交換する必要がない一部のデータで、非同期に処理するためにバッチファイル交換または REST バッチデータ処理 API で更新することをお勧めします。
