---
title: ' [!DNL Observation for Adobe Commerce] nerdlet の使用方法'
description: ' [!DNL Observation for Adobe Commerce] nerdlet の使用方法を説明します。'
exl-id: 3c368814-0786-4e8f-ac81-9a77cec94677
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '627'
ht-degree: 0%

---

# [!DNL Observation for Adobe Commerce] の使い方

## イシューに対する一般的なアプローチ

環境リソースの状態を確認します。

* **[!UICONTROL Storage Free and MySQL % free storage by node]** フレームの % を調べます。

   * 低いストレージが表示される場合は、フレームのヘッダーにあるリンクに従います。

* **[!UICONTROL free system memory and Swap memory free in bytes]** フレームの % を調べます。

   * これらの表示が非常に低いメモリ状態の場合は、問題の一因になる可能性があります。

* **[!UICONTROL Alerts during the timeframe]** フレームを確認します。

   * クラウドインフラストラクチャー上のAdobe Commerceは [!DNL Managed alerts] を提供します。 ヘッダー内のリンクをクリックすると、特定のアラートに対するユーザー側のアクションを決定するのに役立つ [!DNL Support Knowledge Base] の記事が表示されます。

* **[!UICONTROL CPU % by host]** フレームを調べます。CPUの使用率が高い場合は、フレームのヘッダにある [!DNL Support Knowledge Base] の記事を確認します。 また、トラフィックのピーク時にデータベースの読み込み/書き出しまたはバックアップが行われていないことを確認します。

* **[!UICONTROL Web Traffic volume compared to one week ago]** フレームを確認します。同じ期間中にトラフィックが前週よりずっと多い場合、説明はありますか（販売キャンペーンやマーケティングされた新製品など）?
   * トラフィックの増加を説明できない場合は、実稼動環境の平均応答時間（ミリ秒）を調べます。 応答時間に寄与するトラフィックが多いのは、通常とは異なりますか。 期間を展開して、異常値かどうかを確認します。
   * トラフィックの増加は web トランザクションに影響を与えていますか？ **[!UICONTROL Response Code]** フレームにエラーがないか確認します。 サイトがダウンしている場合は、フレームヘッダーの `Site Down?` リンクをクリックできます。 フレームは、発生しているエラーとその頻度を識別します。
   * 誰かが Web サイトに変更をデプロイしましたか？ **[!UICONTROL Deployment Log Entries]** のフレームは、イシューの期間中にデプロイメントが行われたかどうかを示します。 問題が展開直後にある場合は、展開アクティビティによってサイトに負荷が追加されている可能性があります（キャッシュの消去、サービスの再起動など）。
   * アップサイズまたはダウンサイズが発生したか。 サイトが一時的にアップサイズされた場合は、元のクラスターサイズに戻された可能性があります。 サイトの容量を増やすリクエストが行われた場合、アップサイズが発生する可能性があります。 **[!UICONTROL Upsize/Downsize – vCPU view over the timeline]** フレームを確認します。 このフレームは、特定のノードの停止を検出する場合があります。 サイズが減少した場合は、1 つ以上のノードに問題がある可能性があります。

* 「**[!UICONTROL IP Frequency]**」タブは、オリジンサーバーに対して実行された IP アドレスからリクエストの頻度を識別します（つまり、リクエストはキャッシュされていなかったので、74 を使用して [!DNL Fastly] から提供できませんでした）。

   * その [!DNL Fastly] の関連する問題については、**[!UICONTROL Fastly Cache]** フレームをチェックし、エラーファセットを選択して、エラーであるリクエストの割合を確認します。 Web 以外の読み込みと一致する場合は、バックエンドの問題を示している可能性があります。
   * Web トラフィックが原因ではないと思われる読み込みの場合は、エラーか、低速なクエリや [!DNL crons] ードなどの web 以外のリクエストの蓄積が発生している可能性があります。

* **[!UICONTROL Database Errors]** フレームで、イシュー/問題のタイムラインに合致する可能性のあるエラーを確認します。
* **[!UICONTROL Database mysql-slow.log]** フレームをチェックして、発生している SQL 文を特定します。 クエリが最適化されていない場合、`INSERT`、`UPDATE`、および `DELETE` コマンドに時間がかかる場合があります。 大きなテーブルに対して実行すると、`SELECT` 文でも非常に非効率的になる可能性があります。
* **[!UICONTROL PHP States]** フレームと **[!UICONTROL PHP Errors]** フレームは、PHP の潜在的な問題を示します。 **[!UICONTROL PHP States]** フレームは、PHP プロセスの終了、開始、およびサービスがノードによって準備完了状態に達した時点を示します。 **[!UICONTROL PHP Errors]** フレームは、メモリサイズ、ワーカー、サーバ数など、PHP の問題の箇所を特定するのに役立ちます。
* トランザクションの待ち時間を確認するには、トランザクション – 平均、最大、最小テーブルを列別に並べ替えて、最も長時間実行されているトランザクション時間を表示できます。 過負荷のクラスターは、トランザクションに潜在期間を持ちますが、メソッドや [!DNL cron] の問題を特定できる異常値も示します。
* **[!UICONTROL Cron error]** フレームには、専用のステージング環境がある場合に実稼動環境で実行されている可能性のある [!DNL cron] ロック、[!DNL cron] ログに関連付けられている可能性のある SQL エラー、共有ステージング [!DNL crons] が表示されます。
* [!UICONTROL ElasticSearch Errors] のフレームには、クエリ、データまたはインデックスに関する重大な問題を示す可能性の [!DNL Elasticsearch] るエラーが表示されます。
