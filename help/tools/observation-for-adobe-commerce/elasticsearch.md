---
title: 「[!UICONTROL Elasticsearch]」タブ
description: ' [!DNL Observation for Adobe Commerce] の「[!UICONTROL Elasticsearch]」タブについて説明します。'
exl-id: e98d351d-b3b1-47bc-bc0d-f96ba9ec2b80
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 0%

---

# 「[!UICONTROL Elasticsearch]」タブ

## [!UICONTROL Cluster Status Summary]:

![ クラスタ状態の概要 ](../../assets/tools/cluster-status-summary.jpg)

選択した期間にわたって、**[!UICONTROL Cluster Status Summary]** のフレームには、[!DNL Elasticsearch] クラスターが通過したカラーステータスが表示されます。 この例では、選択した期間内に、クラスターは緑色のステータスになり、選択した期間に 1 回は黄色のステータスになりました。

## [!UICONTROL Active Primary Shards]

![ アクティブプライマリシャード ](../../assets/tools/active-primary-shards.jpg)

**[!UICONTROL Active Primary Shards]** フレームには、選択したアカウントの [!DNL Elasticsearch] サービスのアクティブなプライマリシャードの数に応じて異なる数が表示されます。

[!DNL Elasticsearch] から：確定ガイド [2.x]:

「[ 動的に更新可能なインデックス ](https://www.elastic.co/guide/en/elasticsearch/guide/2.x/dynamic-indices.html) では、シャードは Lucene インデックスであり、[!DNL Elasticsearch] インデックスはシャードのコレクションであることを説明しました。 アプリケーションはインデックスと通信し、リクエスト [!DNL Elasticsearch] 適切なシャードにルーティングします。 シャードは尺度の単位です。 使用できる最小インデックスは、1 つのシャードを持つインデックスです。 1 つのシャードに大量のデータを格納できるなど、お客様のニーズを満たす以上の機能を実現できますが、拡張の能力は制限されます。」

インデックスが作成されると、そのインデックスで作成されたシャードがいくつか存在します。 デフォルトでは、新しいインデックスごとに 5 つのプライマリシャードが割り当てられます。つまり、1 つのインデックスを 5 つのノード（ノードごとに 1 つのシャード）に分散させることができます。 レプリカシャードもあります。 これらは主にフェイルオーバー用です。 レプリカシャードは、読み取りリクエストに対応できます。

## [!UICONTROL Active Shards in Cluster]

![ クラスター内のアクティブなシャード ](../../assets/tools/active-shards-in-cluster.jpg)

**[!UICONTROL Active Shards in Cluster]** フレームは、[!DNL Elasticsearch] クラスタ内のプライマリ・シャードとレプリカ・シャードの合計数を示します。

## [!UICONTROL Index health - this will show the index name and color status]

![ インデックスの正常性 ](../../assets/tools/index-health.jpg)

このフレームには、インデックス名とインデックスの色ステータス数が表示されます。 テーブルを下にスクロールすると、同じインデックス名が黄色と赤のカラーステータスで表示されます。 27 インデックス名の後に続く数字は、ステータスカラーのカウントです。 0 の場合は、選択した期間に、インデックスがカラーのステータスになっているインスタンスはありません。

## [!UICONTROL Elasticsearch Status by node information]

![Elasticsearchの状態 ](../../assets/tools/elasticsearch-status-by-node.jpg)

**[!UICONTROL Elasticsearch Status by node information]** のフレームは、[!DNL Elasticsearch] のクラスターのステータスを色別およびノード別に示しています。 これは、[!DNL Elasticsearch] クラスター内のどのノードが、選択した期間にどのステータスを返しているかを示すのに役立ちます。

## [!UICONTROL Elasticsearch index information]

![Elasticsearchインデックス情報 ](../../assets/tools/elasticsearch-tab-elasticsearch-index-information-image-1.jpg)

**[!UICONTROL Elasticsearch index information]** テーブルには、インデックス名、ノード、インデックス付きドキュメントの数、インデックスの正常性、特定の時点でのインデックスサイズ（MB 単位）が表示されます。

## [!UICONTROL Elasticsearch process CPU %]

![Elasticsearch プロセス CPU](../../assets/tools/elasticsearch-process-cpu.jpg)

**[!UICONTROL Elasticsearch process CPU %]** のフレームは、選択した期間の [!DNL Elasticsearch] プロセスによるプロセス CPU の割合を示します。

## [!UICONTROL Elasticsearch Memory garbage collection]

![Elasticsearch メモリ ガベージ ](../../assets/tools/elasticsearch-memory-garbage.jpg)

[!DNL Elasticsearch] は Java プロセスです。 割り当てられたメモリが不足している場合は、ガベージコレクションを開始してメモリを解放します。 ガベージコレクションが頻繁に行われる場合は、割り当てられたメモリに対するインデックスまたはシャードが多すぎる可能性があることを示しています。 インデックスやシャードをクリーンアップする機会がある場合や、より多くのメモリが必要 [!DNL Elasticsearch] 場合があります。

## [!UICONTROL Elasticsearch Index information]

![Elasticsearch インデックス情報 ](../../assets/tools/elasticsearch-index-information-2.jpg)

インデックスが作成および更新されると、インデックスの正常性が変更される可能性があります。

## [!UICONTROL Elasticsearch Index Size]

![Elasticsearch インデックス サイズ ](../../assets/tools/elasticsearch-index-size.jpg)

**[!UICONTROL Elasticsearch Index Size]** のフレームは、選択した期間のインデックス名とサイズを示します。 サイトのインデックス作成方法に関する問題を示している場合があります。

## [!UICONTROL Elasticsearch Errors]

![Elasticsearchエラー ](../../assets/tools/elasticsearch-tab-elasticsearch-errors.jpg)

**[!UICONTROL Elasticsearch Errors]** フレームには、領域不足、黄色から赤への切り替え、すべてのシャードが失敗した場合、検索でパラメーターに問題がある場合、バージョンエラー、すべてのノードが使用できない場合などの [!DNL Elasticsearch] ラーが表示されます。

## [!UICONTROL Elasticsearch Unassigned Shards]:

![Elasticsearchの未割り当てシャード ](../../assets/tools/elasticsearch-unassigned-shards.jpg)

シャードの割り当てを解除すると、クラスタのステータスがグリーンからイエローに変わります。
