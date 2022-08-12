---
title: 「 [!DNL Observation for Adobe Commerce] お節介さん」
description: 使用方法 [!DNL Observation for Adobe Commerce] オタクが
source-git-commit: 69bcb755c3c1f9a820856ac69ce12eb85c686213
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# の使用方法 [!DNL Observation for Adobe Commerce] お節介

## 問題に対する一般的なアプローチ

環境リソースの状態を確認します。

* %を調べる **[!UICONTROL Storage Free and MySQL % free storage by node]** フレーム

   * ストレージ容量が少ない場合は、フレームのヘッダーにあるリンクに従います。

* %を調べる **[!UICONTROL free system memory and Swap memory free in bytes]** フレーム

   * これらの表示が非常に低いメモリ状態の場合、問題の原因になる可能性があります。

* を調べます。 **[!UICONTROL Alerts during the timeframe]** フレーム

   * Adobe Commerce an cloud infrastructure 提供 [!DNL Managed alerts]. ヘッダーのリンクをクリックすると、 [!DNL Support Knowledge Base] 特定のアラートに対するユーザー側のアクションを決定するのに役立つ記事です。

* を調べます。 **[!UICONTROL CPU % by host]** フレーム：CPU 使用率が高い場合は、 [!DNL Support Knowledge Base] 記事が含まれます。 また、ピーク時のトラフィック期間にデータベースのインポート/エクスポートまたはバックアップが実行されていないことを確認します。

* 次を確認します。 **[!UICONTROL Web Traffic volume compared to one week ago]** フレーム：同じ期間の前週よりトラフィックがはるかに多い場合は、説明することができますか（販売キャンペーンや新商品など）?
   * トラフィックの増加について説明できない場合は、実稼動環境の平均応答時間（ミリ秒）を確認してください。 トラフィックが多いほど、応答時間は通常のトラフィックとは異なりますか。 期間を展開して、異常値かどうかを確認します。
   * トラフィックの増加は Web トランザクションに影響を与えますか。 次を確認します。 **[!UICONTROL Response Code]** エラーのフレーム。 サイトがダウンしている場合は、 *[!UICONTROL Site Down?]* リンクを使用して、 フレームは、発生しているエラーとその頻度を識別します。
   * 誰かが Web サイトに変更をデプロイしましたか？ この **[!UICONTROL Deployment Log Entries]** フレームは、問題の発生期間中にデプロイメントがおこなわれたかどうかを示します。 デプロイメント直後に問題が発生した場合は、デプロイメントアクティビティがサイトに追加の負荷を追加している可能性があります（キャッシュがクリアされ、サービスが再起動されたなど）。
   * サイズが大きくなったか、または小さくなったか。 サイトが一時的にアップサイズされた場合は、元のクラスターサイズに戻されている可能性があります。 サイト容量を増やすリクエストが行われた場合、サイズが大きくなる可能性があります。 次を確認します。 **[!UICONTROL Upsize/Downsize – vCPU view over the timeline]** フレーム このフレームは、特定のノードで停止を検出する場合があります。 サイズが小さくなる場合は、1 つ以上のノードに問題がある可能性があります。

* この **[!UICONTROL IP Frequency]** 「 」タブは、オリジンサーバーに対しておこなわれた IP アドレスからのリクエスト頻度を識別します ( つまり、リクエストは [!DNL Fastly] （74 はキャッシュされませんでした）。

   * 任意の [!DNL Fastly] 関連する問題： **[!UICONTROL Fastly Cache]** フレームを選択し、エラーファセットを選択して、エラーであるリクエストの割合を表示します。 これらは、Web 以外の読み込みと一致する場合、バックエンドの問題を示す可能性があります。
   * 読み込みが Web トラフィックに起因しないように見える場合は、エラーが発生したか、低速なクエリや Cron など、Web 以外のリクエストが構築された可能性があります。

* 次を確認します。 **[!UICONTROL Database Errors]** 問題/問題のタイムラインと一致する可能性のあるエラーのフレーム。
* 次を確認します。 **[!UICONTROL Database mysql-slow.log]** 発生している SQL 文を識別するフレーム。 `INSERT`, `UPDATE`、および `DELETE` クエリが最適化されていない場合、コマンドに時間がかかる場合があります。 偶数 `SELECT` 文は、大きなテーブルに対して実行すると、非常に非効率になる可能性があります。
* **[!UICONTROL PHP States]** および **[!UICONTROL PHP Errors]** フレームは、PHP に関する潜在的な問題を示します。 この **[!UICONTROL PHP States]** frame は、PHP プロセスの終了、開始、サービスがノードごとに ready 状態に達した時点を表示します。 この **[!UICONTROL PHP Errors]** frame は、メモリサイズ、ワーカー、サーバ数など、PHP の問題がどこにあるかを特定するのに役立ちます。
* トランザクションの待ち時間を確認するために、Transactions - Avg、Max、Min テーブルを列で並べ替えて、最も長く実行されたトランザクション期間を示すことができます。 過負荷のクラスターは、トランザクションに潜在的な期間が含まれますが、メソッドまたは cron の問題を特定する可能性のある異常値も示されます。
* この **[!UICONTROL Cron error]** frame には、cron ロック、cron ログに関連付けられる可能性のある SQL エラー、専用のステージング環境がある場合に実稼動環境で実行されている可能性のある共有ステージング cron が表示されます。
* この [!UICONTROL ElasticSearch Errors] フレームは、 [!DNL Elasticsearch] クエリ、データ、またはインデックス。
