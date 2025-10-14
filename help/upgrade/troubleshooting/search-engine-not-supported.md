---
title: 現在の検索エンジンはサポートされていません
description: サポートされていない検索エンジンに関するエラーが発生した後の、Adobe Commerceのアップグレードのトラブルシューティング。
feature: Upgrade, Search
exl-id: 11479d23-53a5-4086-9f9a-c3420ccad073
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# 現在の検索エンジンはサポートされていません

次のエラーメッセージは、アップグレード元のAdobe Commerceのバージョンが、アップグレード先のバージョンではサポートされていないカタログ検索エンジンを使用するように設定されていることを示しています。

```
Your current search engine, <Engine Name>, is not supported. You must install a supported search engine before upgrading. See the System Upgrade Guide for more information.
```

このエラーは、Adobe Commerceのダウンレベルバージョンで次の条件のいずれかが当てはまることを意味します。

- 検索エンジンは MySQL に設定されています。
- サポートされなくなったバージョンのElasticsearchが検索エンジンに設定されています。

次のコマンドを使用して、現在の検索エンジンを確認します。

```bash
bin/magento config:show catalog/search/engine
```

このエラーは、返される値が `mysql`、`elasticsearch`、または `elasticsearch6` の場合に発生します。

>[!WARNING]
>
>このエラーが表示された場合は、インストールの状態が矛盾しており、管理者にアクセスできません。 このエラーを解決する間は、以前のバージョンに戻すことをお勧めします。 それには、次のいずれかのコマンドを実行します。
>
>```bash
>composer require-commerce magento/product-enterprise-edition=<version>
>```
>
>```bash
>composer require-commerce magento/product-community-edition=<version>
>```
>
>ここで、`<version>` はアップグレード前に実行していたMagentoのバージョン **す**。 例：`2.3.5`。

以下のセクションで説明するガイドラインに従って、矛盾した状態から回復します。

## 検索エンジンが `mysql` の場合

2.4 以前は、MySQL がデフォルトのカタログ検索エンジンでしたが、この機能では MySQL はサポートされなくなりました。 2.4 にアップグレードする前に、検索エンジンとしてElasticsearchまたは OpenSearch をインストールして設定する必要があります。

このプロセスのガイドとして役立つ次のリソースを使用します。

- [検索エンジンのインストールと設定](../../configuration/search/overview-search.md)
- [検索エンジン設定](../../configuration/search/configure-search-engine.md)

検索エンジンを設定して再インデックス化したら、2.4 にアップグレードする準備が整います。

## 検索エンジンが `elasticsearch` の場合

Elasticsearch 6 以前はサポートされなくなりました。

値が `elasticsearch` の場合、Adobe CommerceのダウンレベルバージョンがElasticsearch 2.x を使用するように設定されています。このバージョンのElasticsearchはサポートされなくなりました。

2.4 にアップグレードする前に、次のタスクを実行する必要があります。

1. CommerceでサポートされているElasticsearchのバージョンへのアップデート。 データのバックアップ、潜在的な移行の問題の検出、実稼動環境にデプロイする前のアップグレードのテストに関する手順について詳しくは、[Elasticsearchのアップグレード &#x200B;](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) を参照してください。 現在のElasticsearchのバージョンに応じて、クラスターの完全な再起動は必要な場合も必要ない場合もあります。

   >[!NOTE]
   >
   >Elasticsearchには JDK 1.8 以降が必要です。 インストールされている JDK のバージョンを確認するには、[Java Software Development Kit （JDK）をインストールする &#x200B;](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) を参照してください。

1. [Elasticsearchを設定 &#x200B;](../../configuration/search/configure-search-engine.md) て、再インデックスを実行します。

検索エンジンを設定して再インデックス化したら、2.4 にアップグレードする準備が整います。
