---
title: 現在の検索エンジンはサポートされていません
description: サポートされていない検索エンジンに関するエラーが発生した場合は、Adobe CommerceまたはMagento Open Sourceのアップグレードをトラブルシューティングします。
source-git-commit: 4c18f00e0b92e49924676274c4ed462a175a7e4b
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---


# 現在の検索エンジンはサポートされていません

次のエラーメッセージは、アップグレード元のAdobe CommerceまたはMagento Open Sourceのバージョンが、アップグレード先のバージョンでサポートされていないカタログ検索エンジンを使用するように設定されていることを示します。

```terminal
Your current search engine, <Engine Name>, is not supported. You must install a supported search engine before upgrading. See the System Upgrade Guide for more information.
```

このエラーは、Adobe CommerceまたはMagento Open Sourceのダウンレベルバージョンで、次の条件の 1 つが真であることを意味します。

- 検索エンジンが MySQL に設定されている。
- 検索エンジンが、サポートされなくなったElasticsearchのバージョンに設定されています。

現在の検索エンジンを確認するには、次のコマンドを使用します。

```bash
bin/magento config:show catalog/search/engine
```

返される値が `mysql`, `elasticsearch`または `elasticsearch6`.

>[!WARNING]
>
>このエラーが発生した場合は、インストールの状態が不整合になり、管理者にアクセスできなくなります。 このエラーを解決する前に、以前のバージョンに戻すことをお勧めします。 これをおこなうには、次のいずれかのコマンドを実行します。
>
>
```bash
>composer require-commerce magento/product-enterprise-edition=<version>
>```
>
>
```bash
>composer require-commerce magento/product-community-edition=<version>
>```
>
>ここで、 `<version>` は、実行していたMagentoのバージョンです **前** アップグレード。 例： `2.3.5`.

一貫性のない状態から回復するには、次のセクションで説明するガイドラインに従います。

## 検索エンジンが `mysql`

2.4 以前は、MySQL がデフォルトのカタログ検索エンジンでしたが、この容量では MySQL はサポートされなくなりました。 次に、2.4 にアップグレードする前に、Elasticsearchまたは OpenSearch を検索エンジンとしてインストールして設定する必要があります。

このプロセスの手引きとして、次のリソースを使用します。

- [検索エンジンのインストールと設定](../../configuration/search/overview-search.md)
- [検索エンジンの設定](../../configuration/search/configure-search-engine.md)

検索エンジンを設定してインデックスを再作成した後、2.4 にアップグレードする準備が整いました。

## 検索エンジンが `elasticsearch`

Elasticsearch6 以前のはサポートされなくなりました。

値： `elasticsearch` は、Elasticsearch2.x を使用するようにAdobe CommerceまたはMagento Open Sourceのダウンレベルバージョンが設定されていることを示します。このバージョンのElasticsearchはサポートされなくなりました。

2.4 にアップグレードする前に、次のタスクを実行する必要があります。

1. コマースでサポートされているElasticsearchのバージョンに更新します。 参照： [アップグレードElasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) データのバックアップ、移行に関する潜在的な問題の検出、アップグレードのテストを実稼動環境にデプロイする前に行う手順について詳しくは、 現在のバージョンのElasticsearchに応じて、完全なクラスターの再起動が必要な場合と不要な場合があります。

   >[!NOTE]
   >
   >Elasticsearchには JDK 1.8 以降が必要です。 詳しくは、 [Java Software Development Kit(JDK) のインストール](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) をクリックして、インストールされている JDK のバージョンを確認します。

1. [設定Elasticsearch](../../configuration/search/configure-search-engine.md) とインデックスを再作成します。

検索エンジンを設定してインデックスを再作成した後、2.4 にアップグレードする準備が整いました。
