---
title: この [!UICONTROL MySQL] タブ
description: 詳しくは、 [!UICONTROL MySQL] タブ [!DNL Observation for Adobe Commerce].
exl-id: 1d8dd07c-15fd-4ffd-ad10-0d886bf1579e
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '2030'
ht-degree: 0%

---

# この [!UICONTROL MySQL] タブ

## [!UICONTROL MySQL% free storage by node]

![ノード別の MySQL%の空きストレージ](../../assets/tools/observation-for-adobe-commerce/mysql-tab-1.jpg)

MySQL に割り当てられたストレージのストレージが不足しているため、多くの問題が発生します (`datadir` MySQL 構成設定。デフォルトは `/data/mysql`) または `tmpdir` 空き容量が不足しています。 デフォルト `tmpdir` （MySQL 設定）は `/tmp`. この **[!UICONTROL MySQL% free storage by node]** フレームは `/, /tmp` （別のマウントとして定義されている場合）と `/data/mysql` 空きストレージの割合。 MySQL バージョン 5.7（MariaDB バージョン 10.2）以降、非圧縮 `tmp` テーブルは `tmp` テーブル領域 `/data/mysql` ファイルのディレクトリ (ibtmp1)。 このファイルは、デフォルトでは制限なしで自動的に展開されます。 これはテーブル領域なので、サイズは減少せず、MySQL の再起動時に 12MB にリセットされます。

## [!UICONTROL MySQL Connections by Node]

![ノード別の MySQL 接続](../../assets/tools/observation-for-adobe-commerce/mysql-tab-2.jpg)

この **[!UICONTROL MySQL Connections by Node]** frame は、データベース・ノードの停止または大量の接続の期間を示します。

## [!UICONTROL MySQL Node Summary]

![MySQL ノードの概要](../../assets/tools/observation-for-adobe-commerce/mysql-tab-3.jpg)

この **[!UICONTROL MySQL Node Summary]** この表は、ソフトウェアのバージョンやインスタンスの種類（サイズ）など、データベースノードの詳細を示しています。

## [!UICONTROL Galera Number of Nodes in cluster]

![クラスタ内の Galera ノード数](../../assets/tools/observation-for-adobe-commerce/mysql-tab-4.jpg)

この **[!UICONTROL Galera Number of Nodes in cluster]** frame は、MySQL ログからの情報を表示します。 ノードがクラスターに参加して離脱すると、選択した期間のメッセージのみが表示されます。 期間より前にノードがクラスターから離れた場合、その期間中にメッセージは存在しません。 データベースがノード不足していると思われる場合は、期間を長く展開して、追加情報が表示されるかどうかを確認します。 期間中に、内のすべてのノードよりも少ない情報が存在する場合 [!DNL Galera] クラスターで、期間を展開して、ノードがクラスターから離脱した時期を判断できるかどうかを確認します。

## [!UICONTROL MySQL shutdowns and starts]

![MySQL がシャットダウンし、起動する](../../assets/tools/observation-for-adobe-commerce/mysql-tab-5.jpg)

この **[!UICONTROL MySQL shutdowns and starts]** frame は、ノードのシャットダウンが発生した場合に検出します。 この [!DNL Galera] ノードは削除され、自己排除されます [!DNL Galera] ノード。 これにより、通常は MySQL サービスが再起動します。

## [!UICONTROL Galera log]

![Galera ログ](../../assets/tools/observation-for-adobe-commerce/mysql-tab-6.jpg)

この **[!UICONTROL Galera log]** frame は、MySQL ログから以下に示す特定のシグナルの数を示します。 [!DNL Galera] ノード、状態、状態の変化 [!DNL Galera] クラスター。

* &#39;%1047 WSREP は、&#39;node_not_prep_for_use&#39;として、アプリケーション使用用のノードをまだ準備していません%&#39;)
* &#39;%\[ERROR\] WSREP:次の読み取りに失敗しました：wsrep_sst_xtrabackup-v2%) を&#39;xtrabackup_read_fail&#39;として使用する
* &#39;%\[ERROR\] WSREP:次のエラーでプロセスが完了しました：wsrep_sst_xtrabackup-v2 %) を&#39;xtrabackup_compl_w_err&#39;として設定する
* &#39;%\[ERROR\] WSREP:rbr write fail%) を&#39;rbr_write_fail&#39;として
* &#39;%self-leave%&#39;) を&#39;susp_node&#39;として
* &#39;%members = 3/3 （結合/合計）%&#39;) as&#39;3of3&#39;
* &#39;%members = 2/3 （結合/合計）%&#39;) as&#39;2of3&#39;
* &#39;%members = 2/2%&#39;) (&#39;2of2&#39;)
* &#39;%members = 1/2%&#39;) を&#39;1of2&#39;として&#39;
* &#39;%members = 1/3%&#39;) を&#39;1of3&#39;として&#39;
* &#39;%members = 1/1%&#39;) を&#39;1of1&#39;として&#39;
* &#39;%\[ 注意\] /usr/sbin/mysqld (mysqld 10.%&#39;) を&#39;sql_restart&#39;として
* &#39;%Quorum:「no_node_count」として、完全な状態：%」を持つノードがありません
* &#39;%WSREP:&#39;mem_0&#39;としてのメンバ 0%&#39;)
* &#39;%WSREP:Member 1.0%) を&#39;mem_1&#39;として
* &#39;%WSREP:メンバー 2%&#39;) を&#39;mem2&#39;として
* &#39;%WSREP:グループと同期（接続の準備完了%）を「準備完了」として
* &#39;%/usr/sbin/mysqld, Version:%&#39;) を&#39;mysql_restart_mysql.slow&#39;として
* &#39;%\[ 注記\] WSREP:新しいクラスタービュー：「galera_cluster_view_chng」としてのグローバル状態：%&#39;)

## [!UICONTROL Galera Log by Host]

![ホスト別 Galera ログ](../../assets/tools/observation-for-adobe-commerce/mysql-tab-7.jpg)

この **[!UICONTROL Galera Log by Host]** フレームは **[!UICONTROL Galera log]** フレーム内に配置されますが、トラブルシューティングに役立つノード別に分割される点が異なります。

## [!UICONTROL Database performance]

![データベースのパフォーマンス](../../assets/tools/observation-for-adobe-commerce/mysql-tab-8.jpg)

この **[!UICONTROL Database performance]** frame は、特定のリクエスト時のデータベースのパフォーマンスを表示します。 グラフの下の色付きのアイコンで各指標をクリックすると、それらの指標を確認できます。 多くの指標が [New Relicでの MySQL データベースのパフォーマンスの監視](https://newrelic.com/blog/how-to-relic/how-to-monitor-mysql) がこのフレームに見つかります。

* average(query.queriesPerSecond)
* average(query.slowQueriesPerSecond)
* average(db.createdTmpDiskTablesPerSecond)
* average(db.createdTmpFilesPerSecond)
* average(db.tablesLocksWaitedPerSecond)
* average(db.innodb.rowLockTimeAvg)
* average(db.innodb.rowLockWaitsPerSecond)

## [!UICONTROL Transaction Database Call Count]

![トランザクションデータベース呼び出し数](../../assets/tools/observation-for-adobe-commerce/mysql-tab-9.jpg)

この **[!UICONTROL Transaction Database Call Count]** frame は、各トランザクションファセットによって実行されたデータベース呼び出しの数を示します。 これは行に焦点を当てており、ステートメントではないようです。

## [!UICONTROL Cron_schedule table updates]

![Cron_schedule テーブルの更新](../../assets/tools/observation-for-adobe-commerce/mysql-tab-10.jpg)

この **[!UICONTROL Cron_schedule table updates]** frame は、選択した期間の cron_schedule テーブルに対するデータベース更新の最大期間を表示します。

## [!UICONTROL Slow Query Traces]

![処理に時間のかかるクエリトレース](../../assets/tools/observation-for-adobe-commerce/mysql-tab-11.jpg)

この **[!UICONTROL Slow Query Traces]** frame は、低速のクエリトレースが存在するテーブルとリクエストタイプを表示します。 5 秒以上かかるクエリトランザクションに対して、低速なクエリトレースが作成されます。 このフレームの重要性は、更新クエリです。 テーブルが `UPDATE`, `DELETE`、および `INSERT` ステートメントを使用すると、テーブルを一定期間ロックできます。

偶数 `SELECT` 文は、FOR UPDATE と一緒に使用すると行をロックする場合があります。

## [!UICONTROL Datastore Operations tables]

![データストア操作テーブル](../../assets/tools/observation-for-adobe-commerce/mysql-tab-12.jpg)

## [!UICONTROL Cron table change]

![Cron テーブルの変更](../../assets/tools/observation-for-adobe-commerce/mysql-tab-13.jpg)

この **[!UICONTROL Cron table change]** frame は、「cron ジョブのロックを取得できませんでした：」というエラーメッセージと、特定の PHP メモリエラーおよび `cron_schedule` 表。 この `cron_schedule` テーブルがロックされている ( 例えば、 `DELETE` クエリを実行する ) 場合は、他の cron が実行されるのをブロックします。

## [!UICONTROL Deadlocks]

![Deadlocks](../../assets/tools/observation-for-adobe-commerce/mysql-tab-14.jpg)

この **[!UICONTROL Deadlocks]** frame は、MySQL ログから解析された次の文字列を調べます。

* &#39;%PHP 致命的なエラー：（%&#39;のメモリサイズを許可）php_mem_error として
* &#39;%get lock;トランザクションを再開してみます。クエリは次のようになりました。DELETEFROM \&#39;cron_schedule%&#39;) を cron_sched_lock_del として
* cron ジョブの&#39;%ロック：indexer_reindex_all_invalid%) を&#39;lock_indexer_reindex_all_invalid%&#39;として
* cron ジョブの&#39;%ロック：cron_schedule%) を「lock_cron_schedule」として
* &#39;% lock - cron ジョブ：%&#39;) を&#39;total_cron_lock&#39;として
* &#39;%一般エラー：1205 ロック待機のタイムアウトが%を超えました ) (&#39;sql_1205_lock&#39;)
* &#39;%ERROR 1213 (40001):&#39;sql_1213_lock&#39;として lock%を取得しようとした際にデッドロックが見つかりました
* &#39;%SQLSTATE[40001]:シリアル化エラー：1213 Deadlock found%&#39;) は&#39;sql_1213_lock2&#39;として見つかりました
* cron ジョブの&#39;%ロック：indexer_update_all_views%) を&#39;lock_indexer_update_all_views&#39;として
* cron ジョブの&#39;%ロック：sales_grid_order_invoice_async_insert%&#39;) を&#39;lock_sales_grid_order_invoice_async_insert&#39;として
* cron ジョブの&#39;%ロック：staging_remove_updates%) を&#39;lock_staging_remove_updates&#39;として
* cron ジョブの&#39;%ロック：sales_grid_order_shipment_async_insert%&#39;) を&#39;lock_sales_grid_order_shipment_async_insert&#39;として
* cron ジョブの&#39;%ロック：amazon_payments_process_queued_refunds%) を「lock_amazon_payments_process_queued_refunds」として
* cron ジョブの&#39;%ロック：sales_send_order_shipment_emails%&#39;) を「lock_sales_send_order_shipment_emails」として
* cron ジョブの&#39;%ロック：staging_synchronize_entities_period%) を&#39;lock_staging_synchronize_entities_period&#39;として
* cron ジョブの&#39;%ロック：indexer_clean_all_changelogs%) を&#39;lock_indexer_clean_all_changelogs&#39;として
* cron ジョブの&#39;%ロック：magento_targetrule_index_reindex%) を「lock_magento_targetrule_index_reindex」として
* cron ジョブの&#39;%ロック：newsletter_send_all%) を&#39;lock_newsletter_send_all&#39;として
* cron ジョブの&#39;%ロック：newsletter_send_all%) を&#39;lock_newsletter_send_all&#39;として
* cron ジョブの&#39;%ロック：sales_send_order_emails%) を&#39;lock_sales_send_order_emails&#39;として
* cron ジョブの&#39;%ロック：sales_send_order_creditmemo_emails%&#39;) を&#39;lock_sales_send_order_creditmemo_emails&#39;として
* cron ジョブの&#39;%ロック：sales_grid_order_creditmemo_async_insert%&#39;) を&#39;lock_sales_grid_order_creditmemo_async_insert&#39;として
* cron ジョブの&#39;%ロック：bulk_cleanup%) を「lock_bulk_cleanup」として
* cron ジョブの&#39;%ロック：flush_preview_quotas%) を「lock_flush_preview_quotas」として
* cron ジョブの&#39;%ロック：sales_send_order_invoice_emails%&#39;) を&#39;lock_sales_send_order_invoice_emails&#39;として
* cron ジョブの&#39;%ロック：sales_send_order_invoice_emails%&#39;) を&#39;lock_sales_send_order_invoice_emails&#39;として
* cron ジョブの&#39;%ロック：captcha_delete_expired_images%) を「lock_captcha_delete_expired_images」として使用する場合
* cron ジョブの&#39;%ロック：magento_newrelicreporting_cron%) を「lock_magento_newrelicreporting_cron」として使用する
* cron ジョブの&#39;%ロック：outdated_authentication_failures_cleanup%) を「lock_outdated_authentication_failures_cleanup」として
* cron ジョブの&#39;%ロック：send_notification%) を&#39;lock_send_notification&#39;として
* cron ジョブの&#39;%ロック：magento_giftcardaccount_generage_codes_pool%) を「lock_magento_giftcardaccount_generage_codes_pool」として使用する
* cron ジョブの&#39;%ロック：catalog_product_frontend_actions_flush%) を「lock_catalog_product_frontend_actions_flush」として使用する場合
* cron ジョブの&#39;%ロック：mysqlmq_clean_messages%) を&#39;mysqlmq_clean_messages&#39;として
* cron ジョブの&#39;%ロック：catalog_product_attribute_value_synchronize%) を「lock_catalog_product_attribute_value_synchronize」として
* cron ジョブの&#39;%ロック：ddg_automation_importer%) を&#39;lock_ddg_automation_importer&#39;として
* cron ジョブの&#39;%ロック：ddg_automation_reviews_and_wishlist%) を&#39;lock_ddg_automation_reviews_and_wishlist&#39;として追加
* cron ジョブの&#39;%ロック：captcha_delete_old_attempts%) を&#39;lock_captcha_delete_old_attempts&#39;として使用する
* cron ジョブの&#39;%ロック：catalog_product_outdated_price_values_cleanup%) を「lock_catalog_product_outdated_price_values_cleanup」として
* cron ジョブの&#39;%ロック：consumers_runner%) を&#39;lock_consumers_runner&#39;として設定する
* cron ジョブの&#39;%ロック：ddg_automation_customer_subscriber_guest_sync%) を「lock_ddg_automation_customer_subscriber_guest_sync」として
* cron ジョブの&#39;%ロック：get_amazon_capture_updates%) を「lock_get_amazon_capture_updates」として設定する
* cron ジョブの&#39;%ロック：get_amazon_authorization_updates%) を「lock_send_get_amazon_authorization_updates」として設定する
* cron ジョブの&#39;%ロック：temando_process_platform_events%) を「lock_temando_process_platform_events」として
* cron ジョブの&#39;%ロック：ddg_automation_status%) を「lock_ddg_automation_status」として設定する
* cron ジョブの&#39;%ロック：ddg_automation_status%) を「lock_ddg_automation_status」として設定する
* cron ジョブの&#39;%ロック：sales_clean_orders%&#39;) を&#39;lock_sales_clean_orders&#39;として使用する
* cron ジョブの&#39;%ロック：catalog_index_refresh_price%) を「lock_catalog_index_refresh_price」として
* cron ジョブの&#39;%ロック：magento_reward_balance_warning_notification%) を「lock_magento_reward_balance_warning_notification」として使用する場合
* cron ジョブの&#39;%ロック：analytics_update%) を&#39;lock_analytics_update&#39;として
* cron ジョブの&#39;%ロック：messagequeue_clean_utdated_locks%) を&#39;lock_messagequeue_clean_utdated_locks&#39;として
* cron ジョブの&#39;%ロック：messagequeue_clean_utdated_locks%) を&#39;lock_messagequeue_clean_utdated_locks&#39;として
* cron ジョブの&#39;%ロック：staging_apply_version%) を&#39;lock_staging_apply_version&#39;として設定する
* cron ジョブの&#39;%ロック：magento_reword_expire_points%) を「lock_magento_reword_expire_points」として
* cron ジョブの&#39;%ロック：yotpo_yotpo_orders_sync%) を&#39;lock_yotpo_yotpo_orders_sync&#39;として設定する
* cron ジョブの&#39;%ロック：catalog_event_status_checker%) を「lock_catalog_event_status_checker」として使用する
* cron ジョブの&#39;%ロック：ddg_automation_campaign%) を「lock_ddg_automation_campaign」として設定する
* cron ジョブの&#39;%ロック：visitor_clean%) を&#39;lock_visitor_clean&#39;として使用する
* cron ジョブの&#39;%ロック：scconnector_verify_website%) を&#39;lock_scconnector_verify_website&#39;として
* cron ジョブの&#39;%ロック：ddg_automation_email_templates%) を「lock_ddg_automation_email_templates」として
* cron ジョブの&#39;%ロック：aggregate_sales_report_order_data%&#39;) を&#39;lock_aggregate_sales_report_order_data&#39;として
* cron ジョブの&#39;%ロック：ddg_automation_catalog_sync%) を「lock_ddg_automation」として設定する

## [!UICONTROL DB Statistics]

![DB 統計](../../assets/tools/observation-for-adobe-commerce/mysql-tab-15.jpg)

この **[!UICONTROL DB Statistics]** frame は、1 秒あたりの削除、書き込み、読み取り、更新、遅いクエリを表示します。

## [!UICONTROL Request frequency]

![リクエスト頻度](../../assets/tools/observation-for-adobe-commerce/mysql-tab-16.jpg)

## [!UICONTROL Database Errors]

![データベースエラー](../../assets/tools/observation-for-adobe-commerce/mysql-tab-17.jpg)

この **[!UICONTROL Database Errors]** frame は、様々なデータベースを示します [警告とエラー](https://mariadb.com/kb/en/mariadb-error-codes/):

* &#39;%一時テーブルに割り当てられたメモリサイズが、&#39;temp_tbl_buff_pool&#39;として innodb_buffer_pool_size%&#39;の 20%を超えています
* &#39;%\[ERROR\] WSREP:rbr write fail%) を&#39;rbr_write_fail&#39;として
* &#39;%mysqld:ディスク容量超過%) （&#39;disk_full&#39;として）
* &#39;%エラー番号 28%&#39;) (&#39;err_28&#39;)
* &#39;%rollback%&#39;は&#39;rollback&#39;として
* &#39;%外部キー制約がテーブル%&#39;に対して失敗しました ) (&#39;foreign_key_constraint&#39;)
* &#39;%Error_code:1114%) を&#39;sql_1114_full&quot;%CRITICAL:SQLSTATE[HY000] [2006] MySQL サーバが&#39;sql_gone&#39;として消えました%&#39;)
* &#39;%SQLSTATE[HY000] [1040] 接続数が多すぎます (%) (&#39;sql_1040&#39;)
* &#39;%CRITICAL:SQLSTATE[HY000] [2002 年]%) を&#39;sql_2002&#39;として
* &#39;%SQLSTATE[08S01]:%&#39;) を&#39;sql_1047&#39;として
* &#39;%[警告] 「aborted_conn」として接続%を中止しました
* &#39;%SQLSTATE[23000]:整合性制約違反： %&#39;) (&#39;sql_23000&#39;として )
* &#39;%1205 ロック待機タイムアウト%&#39;) (&#39;sql_1205&#39;)
* &#39;%SQLSTATE[HY000] [1049] 不明なデータベース%) （&#39;sql_1049&#39;として）
* &#39;%SQLSTATE[42S02]:「sql_42S02」としてのベーステーブルまたはビューが見つかりません：%」)
* &#39;%一般エラー：1114%&#39;) を&#39;sql_1114&#39;として
* &#39;%SQLSTATE[40001]%) を&#39;sql_1213&#39;として
* &#39;%SQLSTATE[42S22]:列が見つかりません：1054 不明な列%) （&#39;sq1_1054&#39;として）
* &#39;%SQLSTATE[42000]:構文エラーまたはアクセス違反： %&#39;) は&#39;sql_42000&#39;として
* &#39;%SQLSTATE[21000]:基数違反： %&#39;) （&#39;sql_1241&#39;として）
* &#39;%SQLSTATE[22003]:%&#39;) を&#39;sql_22003&#39;として
* &#39;%SQLSTATE[HY000] [9000] IP アドレス%&#39;のクライアント ) を&#39;sql_9000&#39;として
* &#39;%SQLSTATE[HY000]:一般エラー：2014%&#39;) を&#39;sql_2014&#39;として
* &#39;%1927 接続が強制終了されました%&#39;) （&#39;sql_1927&#39;として）
* &#39;%1062 \[ERROR\] InnoDB:%&#39;) (&#39;sql_1062_e&#39;)
* &quot;%[注意] WSREP:メモリマップをディスクにフラッシュしています…%&#39;) を&#39;mem_map_flush&#39;として
* &#39;%Internal MariaDB エラーコード：1146%) を&#39;sql_1146&#39;として
* &#39;%Internal MariaDB エラーコード：1062%) (&#39;sql_1062&#39; * &#39;%1062) [警告] InnoDB:%&#39;) を&#39;sql_1062_w&#39;として
* &#39;%Internal MariaDB エラーコード：1064%) を&#39;sql_1064&#39;として
* &#39;%InnoDB:&#39;assertion_err&#39;としてのアサーションエラー (file%&#39;)
* &#39;%mysqld_safe 現在実行中のプロセスの数：0%) を&#39;mysql_oom&#39;として
* &#39;%\[ERROR\] mysqld は&#39;mysql_sigterm&#39;としてシグナル%&#39;を取得しました
* &#39;%1452%&#39;を&#39;sql_1452&#39;として追加できません
* &#39;%ERROR 1698%&#39;) （&#39;sql_1698&#39;として）
* &#39;%SQLSTATE[HY000]:一般エラー：3%) を&#39;cnt_wrt_tmp&#39;として
* &#39;%一般エラー：1 %) を&#39;sql_syntax&#39;として
* &#39;%42S22%&#39;) （&#39;sql_42S22&#39;として）
* &#39;%InnoDB:FROM Log TIMESERIES で&#39;innodb_dup_key&#39;としてエラー (Duplicate key)%&#39;) が発生しました

## [!UICONTROL DB Error Table]

![DB エラーテーブル](../../assets/tools/observation-for-adobe-commerce/mysql-tab-18.jpg)

この **[!UICONTROL DB Error Table]** フレームには **[!UICONTROL Database Errors]** フレーム内に配置されますが、ノード別およびテーブル形式で表示できます。 詳しくは、 [MariaDB エラーコード](https://mariadb.com/kb/en/mariadb-error-codes/) を参照してください。

## [!UICONTROL Database Traces]

![データベーストレース](../../assets/tools/observation-for-adobe-commerce/mysql-tab-19.jpg)

この **[!UICONTROL Database Traces]** frame は、選択したタイムライン全体で、データベーストレースをタイプ別に表示します。

## [!UICONTROL Database processes]

![データベースプロセス](../../assets/tools/observation-for-adobe-commerce/mysql-tab-20.jpg)

この **[!UICONTROL Database processes]** frame は、データベースプロセス、環境、およびノード識別子を示します。

## [!UICONTROL MySQL Non-Sleeping Threads by Node]

![ノード別の MySQL 非スリープスレッド](../../assets/tools/observation-for-adobe-commerce/mysql-tab-21.jpg)

この **[!UICONTROL MySQL Non-Sleeping Threads by Node]** frame は、データベースへの接続スレッドを示します。 このフレームは、アクティブなスレッドを示します。

## [!UICONTROL MySQL Running and Sleeping Threads by environment]

![環境別の MySQL 実行スレッドとスリープスレッド](../../assets/tools/observation-for-adobe-commerce/mysql-tab-22.jpg)

この **[!UICONTROL MySQL Running and Sleeping Threads by environment]** frame は、データベースへのアクティブな接続とスリープ状態の接続の両方を示します。 低速なクエリがスリープ状態になったデータベースへの接続がある場合、スリープ状態の接続が存在します。 スリープ接続は、ロックされた行またはテーブルによってブロックされるデータベースクエリです。 これらのスリープ接続は、PHP のワーカー接続も保持しています。

## [!UICONTROL MySQL mem used by node]

![ノードが使用する MySQL メモリ](../../assets/tools/observation-for-adobe-commerce/mysql-tab-23.jpg)

この **[!UICONTROL MySQL mem used by node]** frame は、MySQL によるメモリのノード使用量を示します。 大規模なサイトでは、このフレームは、GB 分のメモリを使用した連続したバーになる場合があります。

## [!UICONTROL Database mysql-slow.log]

![データベース mysql-slow.log](../../assets/tools/observation-for-adobe-commerce/mysql-tab-24.jpg)

この **[!UICONTROL Database mysql-slow.log]** frame は、 `mysql-slow.log` ファイルの数を指定できます。
