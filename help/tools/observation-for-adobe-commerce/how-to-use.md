---
title: の使用方法 [!DNL Observation for Adobe Commerce] オンドレット
description: の使用方法を学ぶ [!DNL Observation for Adobe Commerce] おしゃべり。
exl-id: 3c368814-0786-4e8f-ac81-9a77cec94677
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '627'
ht-degree: 0%

---

# の使用方法 [!DNL Observation for Adobe Commerce] オンドレット

## イシューに対する一般的なアプローチ

環境リソースの状態を確認します。

* ～の % を調べる **[!UICONTROL Storage Free and MySQL % free storage by node]** フレーム。

   * 低いストレージが表示される場合は、フレームのヘッダーにあるリンクに従います。

* ～の % を調べる **[!UICONTROL free system memory and Swap memory free in bytes]** フレーム。

   * これらの表示が非常に低いメモリ状態の場合は、問題の一因になる可能性があります。

* を調べる **[!UICONTROL Alerts during the timeframe]** フレーム。

   * クラウドインフラストラクチャー上のAdobe Commerceの主な機能は次のとおりです [!DNL Managed alerts]. ヘッダーのリンクをクリックして確認できます [!DNL Support Knowledge Base] 特定のアラートに対するユーザー側のアクションを決定するのに役立つ記事。

* を調べる **[!UICONTROL CPU % by host]** フレーム：CPU 使用率が高い場合は、 [!DNL Support Knowledge Base] フレームのヘッダー内の記事。 また、トラフィックのピーク時にデータベースの読み込み/書き出しまたはバックアップが行われていないことを確認します。

* を確認します **[!UICONTROL Web Traffic volume compared to one week ago]** フレーム：同じ期間中にトラフィックが前週よりもずっと多い場合、説明は可能ですか（販売キャンペーンやマーケティングされた新製品など）。
   * トラフィックの増加を説明できない場合は、実稼動環境の平均応答時間（ミリ秒）を調べます。 応答時間に寄与するトラフィックが多いのは、通常とは異なりますか。 期間を展開して、異常値かどうかを確認します。
   * トラフィックの増加は web トランザクションに影響を与えていますか？ を確認します **[!UICONTROL Response Code]** エラーのフレーム。 サイトがダウンしている場合は、 `Site Down?` フレームヘッダーのリンク。 フレームは、発生しているエラーとその頻度を識別します。
   * 誰かが Web サイトに変更をデプロイしましたか？ この **[!UICONTROL Deployment Log Entries]** フレームは、イシューの期間中にデプロイメントが行われたかどうかを示します。 問題が展開直後にある場合は、展開アクティビティによってサイトに負荷が追加されている可能性があります（キャッシュの消去、サービスの再起動など）。
   * アップサイズまたはダウンサイズが発生したか。 サイトが一時的にアップサイズされた場合は、元のクラスターサイズに戻された可能性があります。 サイトの容量を増やすリクエストが行われた場合、アップサイズが発生する可能性があります。 を確認します **[!UICONTROL Upsize/Downsize – vCPU view over the timeline]** フレーム。 このフレームは、特定のノードの停止を検出する場合があります。 サイズが減少した場合は、1 つ以上のノードに問題がある可能性があります。

* この **[!UICONTROL IP Frequency]** タブは、接触チャネルサーバーに対して実行された IP アドレスからリクエストの頻度を識別します（つまり、リクエストをから提供できなかった） [!DNL Fastly] 74 ではキャッシュされませんでした）。

   * 対象： [!DNL Fastly] 関連する問題については、 **[!UICONTROL Fastly Cache]** フレームに収まり、「エラー」ファセットを選択して、エラーであるリクエストの割合を確認します。 Web 以外の読み込みと一致する場合は、バックエンドの問題を示している可能性があります。
   * Web トラフィックが原因でない読み込みの場合は、エラーが発生しているか、低速なクエリやなどの web 以外のリクエストが蓄積している可能性があります。 [!DNL crons].

* を確認します **[!UICONTROL Database Errors]** 問題/問題のタイムラインと一致する可能性のあるエラーのフレーム。
* を確認します **[!UICONTROL Database mysql-slow.log]** 発生している SQL 文を識別するフレーム。 `INSERT`, `UPDATE`、および `DELETE` クエリが最適化されていない場合、コマンドに時間がかかる場合があります。 偶数 `SELECT` 文を大きなテーブルに対して実行すると、非常に非効率的になる場合があります。
* **[!UICONTROL PHP States]** および **[!UICONTROL PHP Errors]** フレームは PHP の潜在的な問題を示します。 この **[!UICONTROL PHP States]** フレームは、PHP プロセスの終了、開始、およびサービスがノードによって準備完了状態に達した時点を示します。 この **[!UICONTROL PHP Errors]** フレームは、メモリサイズ、ワーカー、サーバ数など、PHP の問題の箇所を特定するのに役立ちます。
* トランザクションの待ち時間を確認するには、トランザクション – 平均、最大、最小テーブルを列別に並べ替えて、最も長時間実行されているトランザクション時間を表示できます。 過負荷のクラスターは、トランザクションに潜在期間を持ちますが、メソッドまたはに関する問題を特定できる異常も示します。 [!DNL cron].
* この **[!UICONTROL Cron error]** フレームに表示 [!DNL cron] ロック、関連付けられる SQL エラー [!DNL cron] ログ、共有ステージング [!DNL crons] 専用のステージング環境がある場合、実稼動環境で実行されている可能性があります。
* この [!UICONTROL ElasticSearch Errors] フレームは、の重大な問題を示す可能性のあるエラーを表示します。 [!DNL Elasticsearch] クエリ、データ、インデックス。
