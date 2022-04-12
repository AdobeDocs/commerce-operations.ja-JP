---
title: Elasticsearchから OpenSearch への移行
description: Adobe CommerceとMagento Open Sourceのオンプレミスインストールに使用する検索エンジンの置き換えについて説明します。
source-git-commit: 8007ff2e77689ec2058a326924dc34b8d91ee570
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---


# OpenSearch への移行

OpenSearch は、Elasticsearchのライセンス変更後に作成されたElasticsearch7.10.2のオープンソースフォークです。

2.4.4、2.4.3-p2、2.3.7-p3 の時点で、Adobe CommerceとMagento Open Sourceは OpenSearch をサポートしています。 オンプレミスでのインストールでは、クラウドインフラストラクチャ上のAdobe Commerceではサポートされなくなりましたが、Elasticsearchは引き続きサポートされます。

## 移行パス

OpenSearch に移行する手順は簡単で、主にElasticsearch設定の手順に従います。 これらの手順では、検索エンジンを使用するアプリケーションはAdobe Commerceのみであることを前提としています。 複数のアプリケーションで検索エンジンを使用する場合は、正式な移行ガイドに従ってください [オープンソースElasticsearchから OpenSearch への移行](https://opensearch.org/blog/technical-posts/2021/10/moving-from-opensource-elasticsearch-to-opensearch/).

1. インストールが [検索エンジンの前提条件](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html).

1. 次の場所にサイトを配置します。 [メンテナンスモード](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html).

1. オプションでアンインストールElasticsearch。

1. [OpenSearch のインストール](https://opensearch.org/docs/latest/opensearch/install/important-settings/).

1. [検索エンジンの設定](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/configure-magento.html) および関連タスク（キャッシュのフラッシュやカタログ検索インデックスの再インデックスなど）を実行します。

設定値の変更は、それ以上必要ありません。
