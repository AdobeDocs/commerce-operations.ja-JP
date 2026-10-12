---
title: ElasticsearchからOpenSearchへの移行
description: Adobe Commerceのオンプレミス インストールに使用される検索エンジンの置き換えについて説明します。
feature: Upgrade, Search
exl-id: 56f1e609-83d2-4705-99d8-b395bb511411
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%
---
# OpenSearchへの移行

OpenSearchは、Elasticsearchのライセンス変更後に作成されたElasticsearch 7.10.2のオープンソースフォークです。

2.4.4、2.4.3-p2、および2.3.7-p3の時点で、Adobe CommerceはOpenSearchをサポートしています。 オンプレミスのインストールでは、Elasticsearchは引き続きサポートされますが、Adobe Commerce オンクラウドインフラストラクチャではサポートされなくなりました。 バージョン 2.4.6以降のOpenSearchには、管理者設定に独自のモジュールとフィールドがあります。

## 移行パス

OpenSearchに移行する手順は簡単で、主にElasticsearch設定の手順に従います。 これらの手順では、Adobe Commerceが検索エンジンを使用する唯一のアプリケーションであることを前提としています。 複数のアプリケーションが検索エンジンを使用する場合は、公式の移行ガイド [ オープンソース ElasticsearchからOpenSearchへの移行](https://opensearch.org/blog/moving-from-opensource-elasticsearch-to-opensearch/)に従ってください。

1. インストールが[検索エンジンの前提条件](../../installation/prerequisites/search-engine/overview.md)を満たしていることを確認してください。

1. サイトを[ メンテナンスモード ](../../installation/tutorials/maintenance-mode.md)に配置します。

1. 必要に応じて、Elasticsearchをアンインストールします。

1. [OpenSearch](https://opensearch.org/docs/latest/opensearch/install/important-settings/)をインストールします。

1. [検索エンジン ](../../configuration/search/configure-search-engine.md)を設定し、キャッシュのフラッシュやカタログ検索インデックスのインデックス再作成などの関連タスクを実行します。

これ以上の設定値の変更は必要ありません。
