---
title: 検索エンジンの概要
description: Adobe CommerceとMagento Open Sourceの検索エンジンオプションの概要。
source-git-commit: 52c472bf80942339b511292243b5da9babf829d9
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# 検索エンジンの概要

バージョン 2.4.4 以降、Adobe CommerceおよびMagento Open Sourceには次のいずれかが必要です。 [Elasticsearch] または [OpenSearch] をカタログ検索エンジンに設定します。 以前のバージョンの 2.4.x では、Elasticsearchが必要です。 検索エンジンのインストールと初期設定について詳しくは、次のトピックを参照してください。

- [検索エンジンの前提条件]
- [検索エンジン用に nginx を設定する]
- [検索エンジン用に Apache を設定]
- [Commerce ソフトウェアのインストール] （コマンドラインインターフェイス）

検索エンジンをインストールしてAdobe Commerceと統合した後、追加のメンテナンスをおこなう必要があります。

- [検索ストップワードの設定](search-stopwords.md)
- [検索エンジンの設定](configure-search-engine.md)

<!-- Link Definitions -->

[検索エンジンの前提条件]: https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html
[検索エンジン用に nginx を設定する]: https://devdocs.magento.com/guides/v2.4/install-gde/prereq/es-config-nginx.html
[検索エンジン用に Apache を設定]: https://devdocs.magento.com/guides/v2.4/install-gde/prereq/es-config-apache.html
[Elasticsearch]: https://www.elastic.co
[Elasticsearch documentation]: https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html
[Commerce ソフトウェアのインストール]: https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-install.html
[OpenSearch]: https://opensearch.org/docs/latest/opensearch/install/index/
