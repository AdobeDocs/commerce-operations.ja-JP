---
title: 現在の検索エンジンはサポートされていません
description: サポートされていない検索エンジンに関するエラーが発生した場合のAdobe Commerce アップグレードのトラブルシューティング。
feature: Upgrade, Search
exl-id: 11479d23-53a5-4086-9f9a-c3420ccad073
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# 現在の検索エンジンはサポートされていません

次のエラーメッセージは、アップグレード元のAdobe Commerce バージョンが、アップグレード先のバージョンでサポートされていないカタログ検索エンジンを使用するように設定されていることを示しています。

```text
Your current search engine, <Engine Name>, is not supported. You must install a supported search engine before upgrading. See the System Upgrade Guide for more information.
```

このエラーは、Adobe Commerceのダウンレベル版で、次のいずれかの条件が当てはまる場合に発生します。

- 検索エンジンはMySQLに設定されます。
- 検索エンジンは、サポートされなくなったElasticsearchのバージョンに設定されています。

次のコマンドを使用して、現在の検索エンジンを確認します。

```shell
bin/magento config:show catalog/search/engine
```

返された値が`mysql`、`elasticsearch`または`elasticsearch6`の場合、エラーが発生します。

>[!WARNING]
>
>このエラーが発生した場合、インストールの状態が不安定になり、管理者にアクセスできません。 このエラーを解決する間は、以前のバージョンに戻すことをお勧めします。 これを行うには、次のいずれかのコマンドを実行します。
>
>```shell
>composer require-commerce magento/product-enterprise-edition=<version>
>```
>
>```shell
>composer require-commerce magento/product-community-edition=<version>
>```
>
>ここで、`<version>`は、アップグレードの&#x200B;**前**&#x200B;に実行していたMagentoのバージョンです。 例：`2.3.5`。

一貫性のない状態から回復するには、次の節で説明するガイドラインに従います。

## 検索エンジンが`mysql`の場合

2.4より前は、MySQLがデフォルトのカタログ検索エンジンでしたが、この機能ではMySQLはサポートされなくなりました。 次に、2.4にアップグレードする前に、ElasticsearchまたはOpenSearchを検索エンジンとしてインストールして設定する必要があります。

次のリソースを使用して、このプロセスをガイドします。

- [検索エンジンのインストールと設定](../../configuration/search/overview-search.md)
- [検索エンジン設定](../../configuration/search/configure-search-engine.md)

検索エンジンを設定してインデックスを再作成したら、2.4にアップグレードする準備が整います。

## 検索エンジンが`elasticsearch`の場合

Elasticsearch 6以前はサポートされなくなりました。

値`elasticsearch`は、ダウンレベル バージョンのAdobe CommerceがElasticsearch 2.xを使用するように設定されていることを示します。 このバージョンのElasticsearchはサポートされなくなりました。

2.4にアップグレードする前に、次のタスクを実行する必要があります。

1. CommerceでサポートされているElasticsearchのバージョンにアップデートします。 データのバックアップ、潜在的な移行の問題の検出、実稼動環境にデプロイする前のアップグレードのテストについて詳しくは、[Elasticsearchのアップグレード &#x200B;](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html)を参照してください。 現在のバージョンのElasticsearchによっては、クラスター全体の再起動が必要な場合とそうでない場合があります。

   >[!NOTE]
   >
   >ElasticsearchにはJDK 1.8以降が必要です。 [Java Software Development Kit （JDK） &#x200B;](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk)をインストールして、どのバージョンのJDKがインストールされているかを確認してください。

1. [Elasticsearch](../../configuration/search/configure-search-engine.md)を構成してインデックスを再作成します。

検索エンジンを設定してインデックスを再作成したら、2.4にアップグレードする準備が整います。
