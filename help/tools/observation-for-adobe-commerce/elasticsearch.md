---
title: この [!UICONTROL Elasticsearch] タブ
description: について説明します [!UICONTROL Elasticsearch] タブ / [!DNL Observation for Adobe Commerce].
exl-id: e98d351d-b3b1-47bc-bc0d-f96ba9ec2b80
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 0%

---

# この [!UICONTROL Elasticsearch] タブ

## [!UICONTROL Cluster Status Summary]:

![クラスター状態の概要](../../assets/tools/cluster-status-summary.jpg)

選択した期間、 **[!UICONTROL Cluster Status Summary]** フレームは、のカラーステータスを表示します [!DNL Elasticsearch] クラスターが通過しました。 この例では、選択した期間内に、クラスターは緑色のステータスになり、選択した期間に 1 回は黄色のステータスになりました。

## [!UICONTROL Active Primary Shards]

![アクティブなプライマリ シャード](../../assets/tools/active-primary-shards.jpg)

この **[!UICONTROL Active Primary Shards]** フレームには、選択したアカウントのアクティブなプライマリシャードの数に応じて異なる数が表示されます。 [!DNL Elasticsearch] サービス。

送信元 [!DNL Elasticsearch]：決定的なガイド [2.x]:

&quot;に含む [動的に更新可能なインデックス](https://www.elastic.co/guide/en/elasticsearch/guide/2.x/dynamic-indices.html)シャードは Lucene インデックスで、 [!DNL Elasticsearch] インデックスは、シャードのコレクションです。 アプリケーションがインデックスと通信し、 [!DNL Elasticsearch] リクエストを適切なシャードにルーティングします。 シャードは尺度の単位です。 使用できる最小インデックスは、1 つのシャードを持つインデックスです。 1 つのシャードに大量のデータを格納できるなど、お客様のニーズを満たす以上の機能を実現できますが、拡張の能力は制限されます。」

インデックスが作成されると、そのインデックスで作成されたシャードがいくつか存在します。 デフォルトでは、新しいインデックスごとに 5 つのプライマリシャードが割り当てられます。つまり、1 つのインデックスを 5 つのノード（ノードごとに 1 つのシャード）に分散させることができます。 レプリカシャードもあります。 これらは主にフェイルオーバー用です。 レプリカシャードは、読み取りリクエストに対応できます。

## [!UICONTROL Active Shards in Cluster]

![クラスター内のアクティブなシャード](../../assets/tools/active-shards-in-cluster.jpg)

この **[!UICONTROL Active Shards in Cluster]** フレームは、内のプライマリおよびレプリカのシャードの合計数を示します。 [!DNL Elasticsearch] クラスター。

## [!UICONTROL Index health - this will show the index name and color status]

![インデックスの正常性](../../assets/tools/index-health.jpg)

このフレームには、インデックス名とインデックスの色ステータス数が表示されます。 テーブルを下にスクロールすると、同じインデックス名が黄色と赤のカラーステータスで表示されます。 27 インデックス名の後に続く数字は、ステータスカラーのカウントです。 0 の場合は、選択した期間に、インデックスがカラーのステータスになっているインスタンスはありません。

## [!UICONTROL Elasticsearch Status by node information]

![Elasticsearchステータス](../../assets/tools/elasticsearch-status-by-node.jpg)

この **[!UICONTROL Elasticsearch Status by node information]** フレームは、 [!DNL Elasticsearch] カラーおよびノード別のクラスターステータス。 これは、内のどのノードかを示すのに役立ちます [!DNL Elasticsearch] クラスターは、選択した期間にどのステータスを返すかを示します。

## [!UICONTROL Elasticsearch index information]

![Elasticsearchインデックスの情報](../../assets/tools/elasticsearch-tab-elasticsearch-index-information-image-1.jpg)

この **[!UICONTROL Elasticsearch index information]** テーブルには、インデックス名、ノード、インデックス付きドキュメントの数、インデックスの正常性、特定の時点でのインデックスサイズ（MB 単位）が表示されます。

## [!UICONTROL Elasticsearch process CPU %]

![Elasticsearchプロセス CPU](../../assets/tools/elasticsearch-process-cpu.jpg)

この **[!UICONTROL Elasticsearch process CPU %]** フレームは、プロセスの CPU の割合を [!DNL Elasticsearch] 選択した期間にわたって処理します。

## [!UICONTROL Elasticsearch Memory garbage collection]

![Elasticsearchメモリガベージ](../../assets/tools/elasticsearch-memory-garbage.jpg)

[!DNL Elasticsearch] は Java プロセスです。 割り当てられたメモリが不足している場合は、ガベージコレクションを開始してメモリを解放します。 ガベージコレクションが頻繁に行われる場合は、割り当てられたメモリに対するインデックスまたはシャードが多すぎる可能性があることを示しています。 インデックスやシャードをクリーンアップする機会があるかもしれません [!DNL Elasticsearch] より多くのメモリが必要になることがあります。

## [!UICONTROL Elasticsearch Index information]

![Elasticsearchインデックスの情報](../../assets/tools/elasticsearch-index-information-2.jpg)

インデックスが作成および更新されると、インデックスの正常性が変更される可能性があります。

## [!UICONTROL Elasticsearch Index Size]

![Elasticsearchインデックスサイズ](../../assets/tools/elasticsearch-index-size.jpg)

この **[!UICONTROL Elasticsearch Index Size]** frame は、選択した期間のインデックス名とサイズを示します。 サイトのインデックス作成方法に関する問題を示している場合があります。

## [!UICONTROL Elasticsearch Errors]

![Elasticsearchエラー](../../assets/tools/elasticsearch-tab-elasticsearch-errors.jpg)

この **[!UICONTROL Elasticsearch Errors]** フレームにエラーが表示される [!DNL Elasticsearch] 領域不足の場合や、黄色から赤へのステータスの切り替え、すべてのシャードが失敗した場合、検索でパラメーターに問題が発生した場合、バージョンエラーおよびすべてのノードが使用できない場合と同様です。

## [!UICONTROL Elasticsearch Unassigned Shards]:

![Elasticsearch未割り当てシャード](../../assets/tools/elasticsearch-unassigned-shards.jpg)

シャードの割り当てを解除すると、クラスタのステータスがグリーンからイエローに変わります。
