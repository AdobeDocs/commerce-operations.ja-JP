---
title: AWS OpenSearch
description: Adobe CommerceとMagento Open SourceのオンプレミスインストールでAWS OpenSearch Web サービスを設定するには、次の手順に従います。
source-git-commit: 3692dcfd5b50c2f036b005d40a22db061b9ea5fd
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---


# AWS OpenSearch

Adobe CommerceおよびMagento Open Source2.4.5 では、Amazon OpenSearch Service クラスターの使用がサポートされます。 このサービスは、AmazonElasticsearchサービスの後継サービスです。 ここでは、AWS OpenSearch を使用するように Commerce を設定する方法と、ローカルElasticsearchまたは OpenSearch インスタンスからAWS OpenSearch クラスターにデータを移行する方法について説明します。

## AWS OpenSearch サービスドメインの作成

最初に、AWSで OpenSearch インスタンスを確立する必要があります。
読み取り [Amazon OpenSearch Service ドメインの作成と管理](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/createupdatedomains.html) を参照してください。

## AWS OpenSearch へのデータの取得

AWSですべての準備が整ったら、データを入力する時です。

小規模なインストールの場合、次の理由により、AWSインスタンスで直接インデックスを作成することをお勧めします。

* インデックスの再作成は、簡単な操作です。
* 古いインスタンスとAWSインスタンスの間にはバージョンの非互換性が存在する可能性があります。これらは、AWSインスタンス上で直接ビルドすることで回避できます。

大規模なインストールでは、データインデックスを既存のインスタンスからAWSに移行することを検討する必要が生じる場合があります。 これによりダウンタイムが短縮される可能性がありますが、古いElasticsearchサーバーとAWSのバージョンが異なるので、非互換性の問題が生じるリスクはまだ小さくなります。

インデックスをAWSインスタンス上で簡単に再作成できるので、インデックスを移行する必要はありません。
ただし、データインデックスを移行する場合は、Elasticsearch/OpenSearch のバージョンに互換性があることを確認してください。

Amazonの設定を参照 [Amazon OpenSearch Service への移行](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/migration.html) 手順を参照してください。

### OpenSearch 用の Commerce の設定

OpenSearch を設定する手順については、 [高度なインストール](../../advanced.md) トピック。

新しい設定が機能しているかをテストするには、OpenSearch エンドポイントを直接テストします。

1. 管理者で製品を作成します ( 例：sku=&quot;testproduct1&quot;) と同じです。
1. 管理者を通じてインデックスを再作成します。
1. OpenSearch エンドポイント (AWS UI にある ) をクエリします。

   インデックスを取得するには、次の文字列を追加します。 `/_cat/indices/*?v=true` を URL に追加します。
   `<AWS OS endpoint>/_cat/indices/*?v=true`

インデックスから製品を取得するには、以下を追加します。 `/magento2docker_product_1/_search?q=*` を URL に追加します。
`<AWS OS endpoint>/magento2docker_product_1/_search?q=testproduct1`

## その他のリソース

詳しくは、 [OpenSearch AWS documentation](https://docs.aws.amazon.com/opensearch-service/index.html).
