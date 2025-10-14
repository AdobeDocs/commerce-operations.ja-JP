---
title: Elasticsearchから OpenSearch への移行
description: Adobe Commerceのオンプレミスインストールに使用する検索エンジンの置き換えについて説明します。
feature: Upgrade, Search
exl-id: 56f1e609-83d2-4705-99d8-b395bb511411
source-git-commit: 54aef3d7db7b8333721fb56db0ba8f098aea030b
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# OpenSearch への移行

OpenSearch は、Elasticsearchのライセンスの変更後に作成された、Elasticsearch 7.10.2 のオープンソースのフォークです。

2.4.4、2.4.3-p2 および 2.3.7-p3 現在、Adobe Commerceは OpenSearch をサポートしています。 オンプレミスインストールは、クラウドインフラストラクチャー上のElasticsearchではサポートされなくなりましたが、引き続きAdobe Commerceをサポートします。 バージョン 2.4.6 以降、OpenSearch には、管理者設定に独自のモジュールとフィールドがあります。

## 移行パス

OpenSearch への移行手順は簡単で、主にElasticsearchの設定手順に従います。 これらの手順では、Adobe Commerceが検索エンジンを使用する唯一のアプリケーションであることを前提としています。 複数のアプリケーションで検索エンジンを使用している場合は、公式の移行ガイド [&#x200B; オープンソースのElasticsearchから OpenSearch への移行 &#x200B;](https://opensearch.org/blog/moving-from-opensource-elasticsearch-to-opensearch/) に従ってください。

1. インストール環境が [&#x200B; 検索エンジンの前提条件 &#x200B;](../../installation/prerequisites/search-engine/overview.md) を満たしていることを確認します。

1. サイトを [&#x200B; メンテナンスモード &#x200B;](../../installation/tutorials/maintenance-mode.md) にします。

1. 必要に応じて、Elasticsearchをアンインストールします。

1. [OpenSearch をインストールします &#x200B;](https://opensearch.org/docs/latest/opensearch/install/important-settings/)。

1. [&#x200B; 検索エンジンを設定 &#x200B;](../../configuration/search/configure-search-engine.md) し、キャッシュのフラッシュやカタログ検索インデックスの再作成などの関連タスクを実行します。

その他の設定値の変更は必要ありません。
