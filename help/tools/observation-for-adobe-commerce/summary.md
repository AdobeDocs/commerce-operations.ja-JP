---
title: 「[!UICONTROL Summary]」タブ
description: '[!UICONTROL Summary] の「 [!DNL Observation for Adobe Commerce]」タブについて説明します。'
exl-id: b07ed898-a211-4353-a1d4-1b71d4898b93
feature: Configuration, Observability
source-git-commit: 790089c178570ee69f33cc04b17800db5563741e
workflow-type: tm+mt
source-wordcount: '2462'
ht-degree: 0%

---

# 「[!UICONTROL Summary]」タブ

[!UICONTROL Summary] の「[!DNL Observation for Adobe Commerce]」タブを使用すると、サイトで発生した問題をすばやく確認して、サイトの問題の潜在的な根本原因を自動解決または特定するのに役立ちます。 追加のタブでは、コンポーネント・サービス、データベース、インフラストラクチャ、プロセスの状態に関する詳細な情報を提供します。

## [!UICONTROL Transaction Overview]

![ 取引の概要 ](../../assets/tools/transaction-overview.jpg)

### [ トランザクションとは ](https://docs.newrelic.com/docs/apm/transactions/intro-transactions/transactions-new-relic-apm/#:%7E:text=transactions%20are%20reported.-,What%20is%20a%20transaction%3F,work%20in%20a%20software%20application.&text=For%20APM%2C%20it%20will%20often, when%20the%20response%20is%20sent)

「[!DNL New Relic] 時点では、トランザクションは、ソフトウェアアプリケーション内の 1 つの作業の論理単位として定義されています。 具体的には、その作業単位を構成する関数呼び出しとメソッド呼び出しを指します。 多くの場合、web トランザクションを指します。これは、アプリケーションが web リクエストを受信したときから応答が送信されたときに発生するアクティビティを表します。」

### トランザクションのタイプ：

**Web:** web トランザクションは、HTTP リクエストで開始されます。 ほとんどの組織では、これらは顧客中心のインタラクションを表しているので、監視が最も重要なトランザクションです。

**Web 以外：** Web 以外のトランザクションは、Web リクエストでは開始されません。 Web ワーカー以外のプロセス、バックグラウンドプロセス、スクリプト、メッセージキューアクティビティなどのタスクが含まれます。

上記の **[!UICONTROL Transaction Overview]** フレームを見ると、平均 APDEX スコアが 0.76 のトランザクションは約 53,000 件あり、これらのトランザクションの 95% は 2.313 秒未満で発生しました。 これは、短い時間枠で APDEX がヒットした場合、より厳密な時間枠では現在の平均からの偏差が表示されるフレームです。

## [!UICONTROL 404 page errors frame]

![404 ページエラーフレーム ](../../assets/tools/404-page-errors.jpg)

**[!UICONTROL 404 page errors]** のフレームには、選択した期間の [URI](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier) と 404 ページエラー数が一覧表示されます。

## [!UICONTROL % of Storage Free frame]

![ ストレージの空きフレームの割合 ](../../assets/tools/percent-of-storage-free.jpg)

**[!UICONTROL % of Storage Free]** フレームには、クラスタのすべてのノードにわたるストレージ・マウントの平均空き率が表示されます。 例えば、3 つのノードクラスターがある場合、フレームには\&lt; マウントポイント\>、\&lt; 環境名\> が表示されます。 このフレームは、3 つのノード間に相違がある場合に偽装される可能性があります。 分散の例としては、`/data/mysql` マウントポイントの解放が 3 つのノードクラスター間で異なる値であった場合があります。 「[!UICONTROL MySQL]」タブの下には、各ノード上の `/data/mysql` ストレージの空き容量をより正確に確認するために、ノード名ごとにマウント・ポイントをファセットするフレームがあります。

## [!UICONTROL % of system memory that is free frame]

![ システム メモリの空きフレームの割合 ](../../assets/tools/percent-of-system-memory-that-is-free.jpg)

空きシステムメモリの **% のフレームは** 各ノード上の空きシステムメモリの量をノードごとに表示します。

## [!UICONTROL Swap memory free in bytes]

![ メモリ空き容量（バイト単位）のスワップ ](../../assets/tools/swap-memory-free-in-bytes.jpg)

**[!UICONTROL Swap memory free in bytes]** フレームは、ノード上で空いている SWAP メモリの量をノードごとに表示します。

## [!UICONTROL CPU % by host]

![ ホスト別のCPUの割合 ](../../assets/tools/cpu-percent-by-host.jpg)

すべての環境とノードの集計が **[!UICONTROL CPU % by host]** のフレームに表示されます。 非実稼動環境の選択を解除する必要があります。 また、実稼動環境のすべてのノードが存在しないインスタンスも注目してください。 CPUの使用率が高い場合のヒントについて詳しくは、[Adobe CommerceでNew Relicを使用したパフォーマンスのトラブルシューティング ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-performance-using-new-relic-on-magento-commerce.html) を参照してください。

## [!UICONTROL Alerts during timeframe]

![ 期間中のアラート ](../../assets/tools/alerts-during-timeframe.jpg)

**[!UICONTROL Alerts during timeframe]** には、Adobe Commerce サポートによって追加された [!UICONTROL Managed Alerts] を含む、すべてのアラートが表示されます。

## [!UICONTROL CPU Usage]

![CPUの使用状況 ](../../assets/tools/cpu-usage.jpg)

**[!UICONTROL CPU Usage]** フレームが空白の場合は、[!DNL New Relic] のインフラストラクチャアプリケーションが有効になっていないことを示します。 サイトが Starter 上にある場合、この情報は表示されません。 サイトが Pro の場合は、[ サポートチケット ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html) を開いて、サイトを有効に [!DNL New Relic Infrastructure] ます。

## [!UICONTROL Average Response Time]

![ 平均応答時間 ](../../assets/tools/average-response-time.jpg)

**[!UICONTROL Average Response Time]** グラフは、トランザクション（web など）の平均応答時間を示します。

## [!UICONTROL Long duration cron_schedule updates]

![ 長い期間の cron_schedule の更新 ](../../assets/tools/long-duration-cron-schedule-updates.jpg)

**[!UICONTROL cron_schedule]** テーブルは、cron ジョブの開始と終了の際に書き込まれます。 所要時間が長い cron ジョブでは、このテーブルの更新に遅延が生じる可能性があります。これは、cron スタックアップまたは cron のスケジュール方法に関する問題を示す場合があります。

## [!UICONTROL Response Code]

![ 応答コード ](../../assets/tools/response-code.jpg)

**[!UICONTROL Response Code]** フレームは、web トラフィックとリクエストの応答コードを示す優れた指標です。 これはトランザクションデータ [!DNL New Relic's] あり、返された `httpResponseCode` によってファセットされます。

## [!UICONTROL Web Traffic volume compared with one week ago Magento Managed Alerts Information]

![1 週間前と比較した web トラフィック量 ](../../assets/tools/web-traffic-volume-compared.jpg)

このフレームには、過去 1 週間と現在 1 週間の web トラフィックの比較量が表示されます。

## [!UICONTROL Deployment Log Entries]

![ デプロイメントログエントリ ](../../assets/tools/deployment-log-entries.jpg)

**[!UICONTROL Deployment Log Entries]** フレームには、デプロイメントとクラウドログエントリの数が表示され、デプロイメントログ名の横にその数をファセットします。

## [!UICONTROL Deployment State]

![ デプロイメントの状態 ](../../assets/tools/deployment-state.jpg)

**[!UICONTROL Deployment State]** のフレームファセットは、デプロイログの特定のデプロイメントフェーズを示しています。 次に、ログにカウントされるフェーズとファセット名の例を示します。

**デプロイメントログフェーズ：**

* &#39;%Starting generate command%&#39;） as &#39;start_gen&#39;
* &#39;%git apply /app/vendor/magento/ece-tools/patches%&#39;） as &#39;apply_patches&#39;
* &#39;%Set フラグ：.static_content_deploy%&#39;）を&#39;SCD&#39;として設定
* &#39;% 注意：コマンド生成が完了しました %&#39;）を&#39;gen_compl&#39;として生成します
* &#39;%NOTICE: Deployment completed%&#39;）を&#39;deploy_compl&#39;として設定します
* &#39;%NOTICE: ポスト デプロイを開始しています。%&#39;） as &#39;start_pdeploy&#39;
* &#39;%NOTICE: Post-deploy is complete%&#39;） as &#39;pdeploy&#39;
* &#39;%deploy-complete%&#39;）を&#39;cl_deploy_compl&#39;として使用します。

## [!UICONTROL IP Frequency]

![IP 頻度 ](../../assets/tools/ip-frequency.jpg)

**[!UICONTROL IP Frequency]** フレームは、[!DNL Fastly] ログから各 IP の（「MISS」および「PASS」）ステータスをカウントします。 これらのステータスを持つ web リクエストは接触チャネルサーバーに到達し、サーバーに読み込みを追加します。 これは、頻度の上位 20 件のアドレスを表示します。 このフレームは、Web サイトに対する IP 攻撃や高負荷のソースを検出するために使用できます。

## [!UICONTROL IP Response – top 20 URLs in duration]

![ip 応答 – 期間の上位 20 個の url](../../assets/tools/ip-response-top-20-urls.jpg)

**[!UICONTROL IP Response – top 20 URLs in duration]** フレームには、応答時間が最も長い URL が表示されます。 サイズの大きい画像ファイルまたはページ、API または応答時間が最長のページを示す場合があります。

## [!UICONTROL API Calls by IP]

![ip による api 呼び出し ](../../assets/tools/api-calls-by-ip.jpg)

**[!UICONTROL API Calls by IP]** フレームは、API に対する大量のトラフィックや、API の URL からリクエストを送信する IP アドレスを識別するのに役立ちます。

## [!UICONTROL API Calls by IP, details by URL]

![ip による api 呼び出しの url 別詳細 ](../../assets/tools/api-calls-by-ip-details-by-url.jpg)

**[!UICONTROL API Calls by IP, details by URL]** フレームは、API に対する大量のトラフィックの詳細と、リクエストを送信する URL の詳細を提供します。

## [!UICONTROL IP Frequency Rate per minute]

![1 分あたりの ip 頻度レート ](../../assets/tools/ip-frequency-rate-per-minute.jpg)

他のフレームで最も多くのリクエストがどの IP アドレスに割り当てられているかを判断するのが難しい場合があります。 **[!UICONTROL IP Frequency Rate per minute]** フレームには、IP アドレスごとの 1 分あたりのレートが表示されます。

## [!UICONTROL Potential Bots]

![ 潜在的なボット ](../../assets/tools/potential-bots.jpg)

**[!UICONTROL Potential Bots]** フレームは、request_user_agent 名が NULL または「%bot%」などのリクエストを調べます。 通常、&#39;%bot%&#39; request_user_agent はファイル内のポリシー設定に従 `robots.txt` ます。

## [!UICONTROL Transaction Errors]

![ トランザクションエラー ](../../assets/tools/transaction-errors.jpg)

**[!UICONTROL Transaction Errors]** フレームには、[!DNL New Relic] からのトランザクションエラーの数が表示されます。

## [!UICONTROL Nginx access by node]

![ ノードによる nginx アクセス ](../../assets/tools/nginx-access-by-node.jpg)

**[!UICONTROL Nginx access by node]** フレームは、`access.log` からのカウントをノード別に調べます。 負荷が均等に分散されているかどうかを確認すると便利です。 多くの場合、ノードがドロップしたときに表示されます。 また、このフレームには、サイト全体の負荷も表示されます。

## [!UICONTROL Galera Log]

![galera ログ ](../../assets/tools/galera-log.jpg)

[[!DNL Galera]](https://galeracluster.com/library/galera-documentation.pdf) は、データベースクラスターに使用されます。 このフレームは、[!UICONTROL Galera] クラスタからの特定の信号に焦点を当てています。 シグナルは、クラスターに入るノードとクラスターから出るノードに焦点を当てます。これは、データベースのデータ整合性を維持する通常の動作です。 ノードは、[!UICONTROL Galera] のクラスター状態が変更されても、同期されたままになります。

**[!UICONTROL Galera] 状態の変更のリスト：**

* &#39;%1047 WSREP はまだアプリケーションの使用 %&#39;用のノードを準備していません）。&#39;node_not_prep_for_use&#39;
* &#39;%\[ERROR\] WSREP: wsrep_sst_xtrabackup-v2%&#39;）から&#39;xtrabackup_read_fail&#39;として読み取れませんでした
* &#39;%\[ERROR\] WSREP: プロセスが完了しましたが、エラーが発生しました：wsrep_sst_xtrabackup-v2 %&#39;） as &#39;xtrabackup_compl_w_err&#39;
* &#39;%\[ERROR\] WSREP: rbr write fail%&#39;） as &#39;rbr_write_fail&#39;
* &#39;%self-leave%&#39;）を&#39;susp_node&#39;
* &#39;%members = 3/3 （結合/合計） %&#39;）を&#39;3of3&#39;として使用
* &#39;%members = 2/3 （結合/合計） %&#39;）を&#39;2of3&#39;として使用
* &#39;%members = 2/2%&#39;）を&#39;2of2&#39;として* &#39;%members = 1/2%&#39;）を&#39;1of2&#39;として* &#39;%members = 1/3%&#39;）を&#39;1of3&#39;として
* &#39;%members = 1/1%&#39;）を&#39;1of1&#39;として使用します
* &#39;%\[ 注意\] /usr/sbin/mysqld （mysqld 10.%&#39;） as &#39;sql_restart&#39;
* &#39;%Quorum：完全な状態を持つノードがありません：%&#39;） （&#39;no_node_count&#39;として）
* &#39;%WSREP: メンバー 0%&#39;）を&#39;mem_0&#39;として使用します
* &#39;%WSREP: メンバ 1.0%&#39;）を&#39;mem_1&#39;として使用します
* &#39;%WSREP: メンバ 2%&#39;）を&#39;mem2&#39;として使用します
* &#39;%WSREP: グループと同期されました。接続の準備が完了しました %&#39;）。&#39;準備完了&#39;です。
* &#39;%/usr/sbin/mysqld, Version:%&#39;）を&#39;mysql_restart_mysql.slow&#39;として使用します
* &#39;%\[Note\] WSREP: New cluster view: global state:%&#39;）を&#39;galera_cluster_view_chng&#39;として使用

状態が頻繁に変更される場合、これらのシグナルは、ストレージ、メモリ、またはクエリの問題を示している可能性があります。

## [!UICONTROL Database errors]

![ データベース エラー ](../../assets/tools/database-errors.jpg)

**データベースのエラーまたはメッセージのリストが検出されました：**

* &#39;% 一時テーブルに割り当てられたメモリサイズが innodb_buffer_pool_size%&#39;）の 20% を超えています（「temp_tbl_buff_pool」として）
* &#39;%\[ERROR\] WSREP: rbr write fail%&#39;） as &#39;rbr_write_fail&#39;
* &#39;%mysqld: Disk full%&#39;）を&#39;disk_full&#39;として使用します
* &#39;% エラー番号 28%&#39;）は&#39;err_28&#39;です。
* &#39;%rollback%&#39;）を&#39;rollback&#39;として使用します
* &#39;%Foreign key constraint failes for table%&#39;） as &#39;foreign_key_constraint&#39;
* &#39;%Error_code: 1114%&#39;） as &#39;sql_1114_full&#39;
* &#39;%CRITICAL: SQLSTATE\[HY000\] \[2006\] MySQL server has gone away%&#39;）を&#39;sql_gone&#39;として使用します
* &#39;%SQLSTATE\[HY000\] \[1040\] Too many connections%&#39;）を&#39;sql_1040&#39;として指定します
* &#39;%CRITICAL: SQLSTATE\[HY000\] \[2002\]%&#39;）を&#39;sql_2002&#39;として使用します
* &#39;%SQLSTATE\[08S01\]:%&#39;）を&#39;sql_1047&#39;として使用します
* &#39;%\[ 警告\] は&#39;aborted_conn&#39;として接続を中止しました %&#39;）
* &#39;%SQLSTATE\[23000\]：整合性制約違反：%&#39;）を&#39;sql_23000&#39;として使用します
* &#39;%1205 ロック待機タイムアウト %&#39;）を&#39;sql_1205&#39;として使用します
* &#39;%SQLSTATE\[HY000\] \[1049\] 不明なデータベース %&#39;）を&#39;sql_1049&#39;として使用します
* &#39;%SQLSTATE\[42S02\]: ベース テーブルまたはビューが見つかりません：%&#39;）を&#39;sql_42S02&#39;として使用します
* &#39;% 一般エラー：1114%&#39;）を&#39;sql_1114&#39;として返します
* &#39;%SQLSTATE\[40001\]%&#39;）を&#39;sql_1213&#39;として使用します
* &#39;%SQLSTATE\[42S22\]：列が見つかりません：1054 不明な列 %&#39;）を&#39;sq1_1054&#39;として
* &#39;%SQLSTATE\[42000\]：構文エラーまたはアクセス違反：%&#39;）を&#39;sql_42000&#39;として返します
* &#39;%SQLSTATE\[21000\]: カーディナリティ違反：%&#39;）を&#39;sql_1241&#39;として返します
* &#39;%SQLSTATE\[22003\]:%&#39;）を&#39;sql_22003&#39;として使用します
* &#39;%SQLSTATE\[HY000\] \[9000\] クライアント （IP アドレスが %&#39;）を&#39;sql_9000&#39;として使用
* &#39;%SQLSTATE\[HY000\]：一般エラー：2014%&#39;）を&#39;sql_2014&#39;として返します
* &#39;%1927 接続が切断されました %&#39;）を&#39;sql_1927&#39;として使用しました
* &#39;%1062 \[\ERROR\] InnoDB:%&#39;）を&#39;sql_1062_e&#39;として使用します
* &#39;%\[Note\] WSREP: メモリ マップをディスクにフラッシュしています…%&#39;） （&#39;mem_map_flush&#39;として）
* &#39;% 内部 MariaDB エラーコード：1146%&#39;）を&#39;sql_1146&#39;として返します
* &#39;%Internal MariaDB エラーコード：1062%&#39;）を&#39;sql_1062&#39; * &#39;%1062 \[ 警告\] InnoDB:%&#39;）を&#39;sql_1062_w&#39;として設定します
* &#39;% 内部 MariaDB エラーコード：1064%&#39;）を&#39;sql_1064&#39;として返します
* &#39;%InnoDB: ファイル %&#39;）で&#39;assertion_err&#39;としてアサーションに失敗しました
* &#39;%mysqld_safe 現在実行中のプロセスの数：0%&#39;）を&#39;mysql_oom&#39;として返します。
* &#39;%\[ERROR\] mysqld は&#39;mysql_sigterm&#39;として signal%&#39;）を取得しました
* &#39;%1452%&#39;）を&#39;sql_1452&#39;として追加できません
* &#39;%ERROR 1698%&#39;）を&#39;sql_1698&#39;として返します
* &#39;%SQLSTATE\[HY000\]：一般エラー：3%&#39;）を&#39;cnt_wrt_tmp&#39;として使用します
* &#39;% 一般エラー：1 %&#39;）を&#39;sql_syntax&#39;として使用します
* &#39;%42S22%&#39;）を&#39;sql_42S22&#39;として使用します
* &#39;%InnoDB: エラー（キーの重複） %&#39;）を&#39;innodb_dup_key&#39;として返します

## [!UICONTROL Database traces]

![ データベース トレース ](../../assets/tools/database-traces.jpg)

**[!UICONTROL Database traces]** フレームは、[ の ](https://docs.newrelic.com/docs/apm/transactions/transaction-traces/transaction-traces-database-queries-page/)sql trace[!DNL New Relic] エンティティからのデータを参照し、トレースのパスを返します。

## [!UICONTROL Database mysql-slow.log]

![database mysql-slow.log](../../assets/tools/database-mysql-slow-log.jpg)

**[!UICONTROL Database mysql-slow.log]** フレームは、クエリリリクエストタイプごとに [mysql-slow.log](https://dev.mysql.com/doc/refman/5.7/en/slow-query-log.html) 内のエントリの数をカウントします。 mysql-slow.log （低速クエリログ）に記録される可能性のある期間が視覚的に分離されます。 インデックスのないテーブルのクエリや、大きなテーブルを更新するクエリは、他のクエリをブロックする場合があります。

## [!UICONTROL Redis synchronization from Log]

![ ログからの redis 同期 ](../../assets/tools/redis-synchronization-from-log.jpg)

[[!DNL Redis]](https://redis.io/docs/about/) は、データベース、キャッシュ、およびメッセージブローカとして使用されるオープンソース（BSD ライセンス）のメモリ内データ構造ストアです。 データベースおよびセッションのキャッシュが可能です（設定されている場合）。 **[!UICONTROL Redis synchronization from Log]** フレームは [[!DNL Redis]  同期 ](https://redis.io/docs/latest/operate/oss_and_stack/management/replication/) に焦点を当てています。 [!DNL Redis] のデータセットが大きいほど、同期に問題が発生する可能性が高くなります（同期を維持するデータが多くなります）。

**[!DNL Redis]のエラーとメッセージ：**

* &#39;%SLAVE 同期：デバイス %&#39;）に&#39;スペース&#39;として残っているスペースがありません
* &#39;%Server started, Redis version%&#39;）を&#39;serv_start&#39;として設定します。
* &#39;% サーバーは接続を受け付ける準備ができました。%&#39;） &#39;準備完了&#39;
* &#39;% マスターとの接続が失われました。%&#39;） as &#39;mstr_lost&#39;
* &#39;%+sentinel%&#39;）を&#39;+sentinal&#39;として保存します
* &#39;%-sdown sentinel%&#39;）を&#39;-sentinal&#39;として使用します
* &#39;%-sdown slave%&#39;）は&#39;-slave&#39;、&#39;%+sdown slave%&#39;）は&#39;+slave&#39;
* &#39;%-failover-abort-not-elected master mymaster%&#39;） as &#39;-failover&#39;
* &#39;%+failover-abort-not-elected master mymaster%&#39;） as &#39;+failover&#39;
* &#39;part_sync_err&#39;として&#39;% 部分的な再同期はできません（キャッシュされたマスタがありません） %&#39;）
* &#39;%マスターはレプリケーションを中止しました。エラー：ERR Can%&#39;）は&#39;mstr_sync_err&#39;です
* &#39;%マスターは PSYNC をサポートしないか、エラー状態 %&#39;）が&#39;mstr_psync_err&#39;です。
* &#39;%SLAVE 同期：成功 %&#39;で終了しました） &#39; slv_sync_suc&#39;
* &#39;%マスターはレプリケーションを中止しました。エラー：ERR Can%&#39;）は&#39;mstr_sync_err,coun&#39;です
* &#39;%OOM コマンドは、使用されたメモリ %&#39;）が&#39; max_mem_err&#39;の場合は使用できません。
* &#39;%CredisException （コード：0）：接続 %&#39;の読み取りエラーは&#39;credis_read_error&#39;です。
* &#39;%Uncaught RedisException:%&#39;）を&#39;redis_excp_err&#39;として検出しました
* &#39;%psync は、出力バッファを克服するために可能な限り早く閉じるようにスケジュールされました。&#39;%&#39;） as &#39;output_buf_err&#39;

## [!UICONTROL PHP process states]

![PHP プロセスの状態 ](../../assets/tools/php-process-states.jpg)

PHP プロセスの動作は [configuration](https://www.php.net/manual/en/install.fpm.configuration.php) に依存します。 設定は複雑で、多くの変数とオプションがあります。 **[!UICONTROL PHP process states]** フレームは、PHP プロセスがいつ終了し、再起動するかを理解するのに役立ちます。

### [!UICONTROL PHP errors]

![php エラー ](../../assets/tools/php-errors.jpg)

**[!UICONTROL PHP errors]** フレームには、選択した期間におけるワーカーの PHP エラー数が表示されます。 詳しくは、[Adobe Commerce PHP 設定 ](../../installation/prerequisites/php-settings.md) を参照してください。

**PHP エラーとメッセージ：**

* &#39;%worker_connections は十分ではありません %&#39;） （&#39;worker&#39;として）
* &#39;%PHP 致命的なエラー：許可されたメモリ サイズ！%&#39;） as &#39;mem_size&#39;
* &#39;%exited on signal 11 （SIGSEGV） %&#39;） as &#39;sig_11&#39;
* &#39;% はシグナル 7 （SIGBUS） %&#39;）で&#39;sig_7&#39;として終了しました
* &#39;%increase pm.start_servers%&#39;）を&#39;pmstart_serv&#39;として使用します
* &#39;%max_children%&#39;）を&#39;max_children_cnt&#39;として使用
* &#39;%PHP 致命的なエラー：メモリ サイズが %&#39;）を&#39;mem_exhst_count&#39;として許可しました
* &#39;%pool%&#39;のメモリを割り当てることができません）。&#39;opc_mem_count&#39;
* &#39;%Warning Interned string buffer overflow%&#39;）を&#39;opc_str_buf&#39;として設定します
* &#39;% 無効な文字列 offsetl%&#39;）を&#39;opc_sv_comments&#39;として使用します
* &#39;%PHP Fatal error: Uncaught RedisException: read error on connection%&#39;） as &#39;php_exc&#39;

## [!UICONTROL PHP processes]

![php プロセス ](../../assets/tools/php-processes.jpg)

[PHP-FPM](https://php-fpm.org/) は、[!UICONTROL FastCGI Process Manager] で使用される [!DNL Nginx] です。 システム要件については、[Adobe Commerceのバージョンにマッピングされる PHP のバージョン要件 ](../../installation/system-requirements.md) を参照してください。 **[!UICONTROL PHP processes]** のフレームは、選択したタイムラインの特定の時点で実行されている PHP プロセスの数を示します。

## [!UICONTROL Secondary processes]

![ セカンダリ プロセス ](../../assets/tools/secondary-processes.jpg)

セカンダリプロセスは、サイトの反応に影響を与える可能性があります。 **[!UICONTROL Secondary processes]** のフレームは、サイトに負荷を追加している可能性のあるプロセスを示します。 データベースには、主に実行されているセカンダリ・プロセスが多く含まれています。

## [!UICONTROL Traffic vs Week Ago]

![ トラフィック対週間前 ](../../assets/tools/traffic-vs-week-ago.jpg)

**[!UICONTROL Traffic vs Week Ago]** フレームは、（「MISS」、「PASS」）キャッシュステータスを含む [!DNL Fastly] ログからの web サイトトラフィック（リクエスト）を調べます。 これらのリクエストにより、接触チャネルサーバーに負荷が追加されます。 このフレームには、同じ期間内の現在の週と過去 1 週間前の web リクエストの量の比較が表示されます。

## [!UICONTROL Fastly Cache]

![fastly キャッシュ ](../../assets/tools/fastly-cache.jpg)

**[!UICONTROL Fastly Cache]** フレームは、[!DNL Fastly] ログからのリクエストのキャッシュ ステータスの集約ビューを表示します。 「エラー」を選択すると、リクエストのエラーの割合が表示されます。 これは通常、接触チャネルサーバーがページリクエストに十分な速さで応答しない場合に増加します。

## [!UICONTROL Page Rendering]

![ ページレンダリング ](../../assets/tools/page-rendering.jpg)

**[!UICONTROL Page Rendering]** フレームには、[!DNL New Relic] のページビューソースから得られた今週の平均ページレンダリング時間が、同期間の前週と比較して表示されます。

## [!UICONTROL Page loading detail]

![ ページ読み込みの詳細 ](../../assets/tools/page-loading-detail.png)

**[!UICONTROL Page loading detail]** のフレームは、ページ読み込みイベントを説明します。 これらの側面の意味を詳しく述べている。 このフレームに対して実行されるクエリは次のとおりです。

`SELECT percentile(timeToResponseStart, 50) AS 'first byte', percentile(firstPaint, 50) as 'First paint', percentile(firstContentfulPaint, 50) as 'First contentful paint', percentile(timeToDomContentLoadedEventEnd, 50) AS 'DOM content loaded', percentile(duration, 50) AS 'Window load + AJAX' FROM BrowserInteraction TIMESERIES`

## [!UICONTROL Transactions – Avg, Max, Min]

![ トランザクション – 平均、最大、最小 ](../../assets/tools/transactions-avg-max-min.jpg)

トランザクション期間は秒単位です。 トランザクションによっては、長時間実行されると他のトランザクションに影響を与える可能性があります。 「名前」と「期間」の下にリストされるトランザクションは、特定の期間のものです。 簡潔な問題の期間がある場合は、[!DNL Observation for Adobe Commerce] の日付/時間セレクターのサイズを、その狭い期間に変更します。

## [!UICONTROL Admin Activities]

![ 管理アクティビティ ](../../assets/tools/admin-activities.jpg)

**[!UICONTROL Admin Activities]** フレームは、管理者ユーザーとのトランザクションを識別します。

## [!UICONTROL Order transactions (default?)]

![ 注文トランザクションのデフォルト ](../../assets/tools/order-transactions-default.jpg)

**[!UICONTROL Order transactions (default?)]** フレームは、名前= `request.headers.host` のトランザクションから `WebTransaction/Action/checkout/onepage/success` まるトランザクションを検索します。 注文成功 URL が異なる場合、このフレームにはデータがありません。

## [!UICONTROL Elasticsearch Index information]

![elasticsearch インデックス情報 ](../../assets/tools/elasticsearch-tab-elasticsearch-index-information-image-1.jpg)

**[Elasticsearchの状態：](https://www.elastic.co/guide/en/elasticsearch/reference/current/cluster-health.html)**

* 緑：すべてのシャードが割り当てられます。
* 黄：すべてのプライマリ・シャードが割り当てられているが、1 つ以上のレプリカ・シャードが未割り当てである。 クラスター内のノードに障害が発生した場合、そのノードが修復されるまで、一部のデータが使用できなくなる可能性があります。
* 赤：1 つ以上のプライマリシャードの割り当てが解除されており、一部のデータが使用できない。 これは、主シャードが割り当てられているときに、クラスタの起動時に短時間だけ発生する場合があります。

## [!UICONTROL Elasticsearch Errors]

![elasticsearch エラー ](../../assets/tools/elasticsearch-errors.jpg)

**[!DNL Elasticsearch]エラー：**

* 「all_shards_failed」として「%all shards failed%」
* &#39;%NoNodesAvailableException%&#39;を&#39;no_alive_nodes&#39;として
* &#39;%PHP Fatal error: Uncaught Error: Elasticsearch%&#39;の間違ったパラメータを&#39;wrong_param&#39;として設定します
* &#39;% この問題は、Magento Cloud インフラストラクチャのElasticsearch サービスを&#39;ver_err&#39;として version%&#39;にアップグレードすることで解決できます。
* &#39;%cluster の正常性状態が\[YELLOW\] から\[RED\] に変更されました（理由：%&#39;が&#39;yel_red&#39;です）
* &#39;%No space on device%&#39; as &#39;no_space&#39;
* &#39;% は、&#39;failed_query&#39;として [SearchRequest{searchType=%&#39;を実行できませんでした

## [!UICONTROL Cron view]

![cron ビュー ](../../assets/tools/cron-view.jpg)

**[!UICONTROL Cron view]** フレームは、cron ログを参照して、開始した cron 数と終了した cron 数のバランスを確認します。


## [!UICONTROL Cron error]

![cron エラー ](../../assets/tools/cron-error.png)

**cron.log からの Cron エラー：**

* &#39;%_stg%&#39; as &#39;stg_cron&#39;
* &#39;%cron job%&#39;のロックを&#39;cron_lock&#39;として取得できませんでした
* &#39;% 一般エラー：2006 MySQL server has gone away%&#39; as &#39;mysql_has_gone_away&#39;
* 「%error%」が「エラー」として表示される
* &#39;% 一般エラー：sql_1205_cron として 1205 ロック待機タイムアウト超過 %&#39;

## [!UICONTROL cron_schedule table updates]

![cron_schedule テーブルの更新 ](../../assets/tools/cron-schedule-table-updates.jpg)

**[!UICONTROL cron_schedule table updates]** フレームは、データストア操作の更新に cron_schedule テーブルが関与する最大期間（秒単位）を調べます。 これは、SQL リクエストタイプでファセットされます。

## [!UICONTROL Datastore Operations Tables]

![ データストア操作テーブル ](../../assets/tools/datastore-operations-tables.jpg)

この **[!UICONTROL Datastore Operations Tables]** フレームには、期間、テーブル名および SQL 要求タイプ別の上位 25 の操作が表示されます。 スパイクにカーソルを合わせると、アクセスされているテーブルとリクエストタイプの詳細が表示されます。

## [!UICONTROL Cache Flush]

![ キャッシュフラッシュ ](../../assets/tools/cache-flush.jpg)

**キャッシュのフラッシュが検出されました：**

* &#39;%config%&#39;を&#39;config_cache_flushed&#39;として設定
* &#39;layout_cache_flush&#39;としての&#39;%layout%&#39;
* &#39;%block_html%&#39; as &#39;block_html_cache_flush&#39;
* &#39;%collections%&#39;が&#39;collections_cache_flush&#39;として設定されました
* &#39;%reflection%&#39; as &#39;reflection_cache_flush&#39;
* &#39;%db_ddl%&#39; as &#39;db_ddl_cache_flush&#39;
* &#39;%compiled_config%&#39; as &#39;compiled_config_cache_flush&#39;
* &#39;%eav%&#39; as &#39;eav_cache_flush&#39;
* &#39;cust_notif_cache_flush&#39;としての&#39;%customer_notification%&#39;
* &#39;%config_integration%&#39; as &#39;config_integ_cache_flush&#39;
* &#39;%config_integration_api%&#39; as &#39;config_integ_api_cache_flush&#39;
* &#39;%full_page%&#39; as &#39;full_page_cache_flush&#39;
* &#39;%config_webservice%&#39; as &#39;config_webserv_cache_flush&#39;
* &#39;%translate%&#39; as &#39;translate_cache_flush&#39;
