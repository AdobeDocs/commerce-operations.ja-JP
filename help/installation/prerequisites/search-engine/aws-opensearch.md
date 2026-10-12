---
title: AWS OpenSearch
description: 次の手順に従って、Adobe Commerceのオンプレミスインストール用にAWS OpenSearch web サービスを設定します。
feature: Install, Search
exl-id: 39ca7fd0-e21f-4f14-bda6-ff00a61a1a4d
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
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
source-wordcount: '341'
ht-degree: 0%
---
# AWS OpenSearch

Adobe Commerce 2.4.5は、Amazon OpenSearch Service クラスターの使用をサポートしています。 このサービスは、Amazon Elasticsearch サービスの後継です。 このトピックでは、AWS OpenSearchを使用するようにCommerceを設定する方法と、ローカルのElasticsearchまたはOpenSearch インスタンスからAWS OpenSearch クラスターにデータを移行する方法について説明します。

## AWS OpenSearch サービスドメインの作成

まず、AWSでOpenSearch インスタンスを確立する必要があります。
詳しい手順については、[Amazon OpenSearch Service ドメインの作成と管理](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/createupdatedomains.html)を参照してください。

## AWS OpenSearchにデータを取得

AWSで準備が整ったら、データを入力します。

小規模なインストールでは、次の理由から、AWS インスタンスで直接インデックスを作成することをお勧めします。

* インデックスの再作成は簡単な操作です。
* 古いインスタンスとAWS インスタンスの間にはバージョンの非互換性がある可能性があり、AWS インスタンスに直接構築することで回避できます。

大規模なインストールでは、既存のインスタンスからAWSへのデータインデックスの移行を検討する場合があります。 これによりダウンタイムが減少する可能性がありますが、古いElasticsearch サーバーとAWSのバージョンが異なるため、互換性の問題が発生するリスクは少なくなります。

AWS インスタンスで簡単に再作成できるため、インデックスを移行する必要はありません。
ただし、データインデックスを移行する場合は、Elasticsearch/OpenSearchのバージョンが互換性があることを確認してください。

詳しくは、Amazonの[Amazon OpenSearch Serviceへの移行手順](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/migration.html)を参照してください。

### OpenSearch用にCommerceを設定

OpenSearchを設定する手順については、[高度なインストール ](../../advanced.md) トピックを参照してください。

新しい設定が機能していることをテストするには、OpenSearch エンドポイントを直接テストします。

1. Adminで製品を作成します（例：sku=&quot;testproduct1&quot;）。
1. 管理者を使用してインデックスを再作成します。
1. OpenSearch エンドポイントのクエリ（AWS UIで見つかる）:

   インデックスを取得するには、次のURLに`/_cat/indices/*?v=true`を追加します。
   `<AWS OS endpoint>/_cat/indices/*?v=true`

インデックスから製品を取得するには、次のURLに`/magento2docker_product_1/_search?q=*`を追加します。
`<AWS OS endpoint>/magento2docker_product_1/_search?q=testproduct1`

## 関連資料

詳しくは、[OpenSearch AWSのドキュメント ](https://docs.aws.amazon.com/opensearch-service/index.html)を参照してください。
