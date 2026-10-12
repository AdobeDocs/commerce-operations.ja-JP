---
title: 検索エンジンの概要
description: ElasticsearchとOpenSearch for Adobe Commerceのカタログ検索、前提条件、web サーバーの設定、インストール後のメンテナンスタスクについて説明します。
feature: Configuration, Search
exl-id: 0ea78ca2-0bca-4d61-980a-02fb7da04553
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
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
source-wordcount: '117'
ht-degree: 0%
---
# 検索エンジンの概要

バージョン 2.4.4以降、Adobe Commerceでは、[Elasticsearch](https://www.elastic.co)または[OpenSearch](https://opensearch.org/docs/latest/opensearch/install/index/)のいずれかをカタログ検索エンジンにする必要があります。 以前のバージョンの2.4.xでは、Elasticsearchが必要でした。 検索エンジンのインストールと初期設定について詳しくは、次のトピックを参照してください。

- [検索エンジンの前提条件](../../installation/prerequisites/search-engine/overview.md)
- [検索エンジン用にnginxを設定する](../../installation/prerequisites/search-engine/configure-nginx.md)
- [検索エンジン用のApacheの設定](../../installation/prerequisites/search-engine/configure-apache.md)
- [Commerce ソフトウェアのインストール &#x200B;](../../installation/composer.md) （コマンドライン インターフェイス）

検索エンジンをインストールしてAdobe Commerceと統合したら、追加のメンテナンスを実行する必要があります。

- [検索ストップワードの設定](search-stopwords.md)
- [検索エンジン設定](configure-search-engine.md)

