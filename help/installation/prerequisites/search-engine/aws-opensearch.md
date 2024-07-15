---
title: AWS OpenSearch
description: 次の手順に従って、Adobe Commerceのオンプレミスインストール用にAWS OpenSearch web サービスを設定します。
feature: Install, Search
exl-id: 39ca7fd0-e21f-4f14-bda6-ff00a61a1a4d
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# AWS OpenSearch

Adobe Commerce 2.4.5 では、Amazon OpenSearch サービスクラスターの使用がサポートされています。 このサービスは、Amazon Elasticsearchサービスの後継となるものです。 ここでは、AWS OpenSearch を使用するようにCommerceを設定する方法と、ローカルElasticsearchまたは OpenSearch インスタンスからAWS OpenSearch クラスターにデータを移行する方法について説明します。

## AWS OpenSearch サービスドメインの作成

まず、AWSで OpenSearch インスタンスを確立する必要があります。
手順について詳しくは、[Amazon OpenSearch サービスドメインの作成と管理 ](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/createupdatedomains.html) を参照してください。

## AWS OpenSearch へのデータの取得

AWSですべてが準備されたら、データを入力する時間です。

小規模なインストールの場合は、次の理由により、AWS インスタンスで直接インデックスを作成することをお勧めします。

* インデックスの再作成は、迅速な操作です。
* 古いインスタンスとAWS インスタンスの間にバージョンの非互換性がある場合があり、AWS インスタンス上に直接構築することで、これを回避できます。

大規模なインストールでは、データインデックスを既存のインスタンスからAWSに移行することを検討する場合があります。 これによりダウンタイムが短縮される場合がありますが、古いElasticsearchサーバーとAWSの間でバージョンが異なるので、互換性の問題が発生するリスクがわずかながら存在します。

インデックスはAWS インスタンスで簡単に再作成できるので、インデックスを移行する必要はありません。
ただし、データインデックスを移行する場合は、Elasticsearch/OpenSearch のバージョンに互換性があることを確認します。

詳しくは、Amazonの [Amazon OpenSearch Service への移行 ](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/migration.html) 手順を参照してください。

### OpenSearch 用のCommerceの設定

OpenSearch を設定する手順については、[ 詳細インストール ](../../advanced.md) トピックを参照してください。

新しい設定が機能していることをテストするには、OpenSearch エンドポイントを直接テストします。

1. 管理者で製品を作成します（例：sku=&quot;testproduct1&quot;）。
1. 管理者を使用して再インデックス化します。
1. OpenSearch エンドポイント（AWS UI 内）をクエリします。

   インデックスを取得するには、URL に `/_cat/indices/*?v=true` を追加します。
   `<AWS OS endpoint>/_cat/indices/*?v=true`

インデックスから製品を取得するには、URL に `/magento2docker_product_1/_search?q=*` を追加します。
`<AWS OS endpoint>/magento2docker_product_1/_search?q=testproduct1`

## その他のリソース

詳しくは、[OpenSearch AWS ドキュメント ](https://docs.aws.amazon.com/opensearch-service/index.html) を参照してください。
