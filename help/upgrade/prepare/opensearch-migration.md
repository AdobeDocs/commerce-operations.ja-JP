---
title: Elasticsearchから OpenSearch への移行
description: Adobe Commerceのオンプレミスインストールに使用する検索エンジンの置き換えについて説明します。
feature: Upgrade, Search
exl-id: 56f1e609-83d2-4705-99d8-b395bb511411
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# OpenSearch への移行

OpenSearch は、Elasticsearchのライセンスが変更された後に作成された、Elasticsearch 7.10.2 のオープンソース分岐です。

2.4.4、2.4.3-p2 および 2.3.7-p3 現在、Adobe Commerceは OpenSearch をサポートしています。 オンプレミスインストールは、Elasticsearchを引き続きサポートしますが、クラウドインフラストラクチャー上のAdobe Commerceではサポートされなくなりました。 バージョン 2.4.6 以降、OpenSearch には、管理者設定に独自のモジュールとフィールドがあります。

## 移行パス

OpenSearch に移行する手順は簡単で、主にElasticsearch設定の手順に従います。 これらの手順では、Adobe Commerceが検索エンジンを使用する唯一のアプリケーションであることを前提としています。 複数のアプリケーションで検索エンジンを使用している場合は、公式の移行ガイド [ オープンソースElasticsearchから OpenSearch への移行 ](https://opensearch.org/blog/technical-posts/2021/10/moving-from-opensource-elasticsearch-to-opensearch/) に従ってください。

1. インストール環境が [ 検索エンジンの前提条件 ](../../installation/prerequisites/search-engine/overview.md) を満たしていることを確認します。

1. サイトを [ メンテナンスモード ](../../installation/tutorials/maintenance-mode.md) にします。

1. オプションで、Elasticsearchをアンインストールします。

1. [OpenSearch をインストールします ](https://opensearch.org/docs/latest/opensearch/install/important-settings/)。

1. [ 検索エンジンを設定 ](../../configuration/search/configure-search-engine.md) し、キャッシュのフラッシュやカタログ検索インデックスの再作成などの関連タスクを実行します。

その他の設定値の変更は必要ありません。
