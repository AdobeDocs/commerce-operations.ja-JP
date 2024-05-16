---
title: この [!UICONTROL PHP] タブ
description: について説明します [!UICONTROL PHP] タブ / [!DNL Observation for Adobe Commerce].
exl-id: 0989a7f5-75b0-4fb5-ac5e-2618603bf548
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---

# この [!UICONTROL PHP] タブ

この **PHP** タブは、PHP の問題をより深く分析するために PHP プロセスの問題を表示します。

## [!UICONTROL PHP active process details]

![PHP アクティブなプロセスの詳細](../../assets/tools/php-active-process-details.jpg)

この **[!UICONTROL PHP active process details]** frame は、選択した期間における php-fpm を含む PHP プロセスを表示します。

## [!UICONTROL PHP process load (# of PHP processes and % of CPU load)]

![PHP プロセスのロード](../../assets/tools/php-process-load.jpg)

この **[!UICONTROL PHP process load (# of PHP processes and % of CPU load)]** frame は、選択した期間における PHP-FPM プロセスの CPU 負荷を示します。

## [!UICONTROL PHP Memory detail]

![PHP メモリの詳細](../../assets/tools/php-memory-detail.jpg)

この **[!UICONTROL PHP Memory detail]** frame は、選択した期間における PHP プロセスのメモリ使用量を示します。

## [!UICONTROL PHP CPU Utilization]

![PHP の CPU 使用率](../../assets/tools/php-cpu-utilization.jpg)

この **[!UICONTROL PHP CPU Utilization]** frame は、選択した期間における PHP プロセスの CPU 使用率を示します。

## [!UICONTROL PHP Process states]

![PHP プロセスの状態](../../assets/tools/php-process-states-image-1.jpg)

この **[!UICONTROL PHP Process states]** フレーム：選択した期間の PHP プロセスの状態を表示します。 PHP のプロセスが終了し、再起動すると表示されます。 再起動を表示しない終了した PHP プロセスには注意してください。

* &#39;%NOTICE: ...%&#39;）を&#39;php_term&#39;として終了しています
* &#39;% NOTICE: exiting, bye-bye!%&#39;） as &#39;php_exit&#39;
* 「% 注意：fpm は実行中です。pid%」）を「fpm_start」として
* &#39;%NOTICE: connections%&#39;）を&#39;php_ready&#39;として処理する準備ができました

## [!UICONTROL PHP Errors]

![PHP エラー](../../assets/tools/php-errors-image-1.jpg)

この **[!UICONTROL PHP Errors]** frame は、選択した期間における PHP ワーカーエラー数を表示します。 解析および表示されるエラーメッセージは次のとおりです。

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

## [!UICONTROL PHP processes count]

![PHP プロセス数](../../assets/tools/php-processes-count.jpg)

この **[!UICONTROL PHP processes count]** フレームは、選択した期間における PHP プロセスの数を表示します。

## [!UICONTROL Database Errors]

![データベースエラー](../../assets/tools/php-tab-database-errors.jpg)

この **[!UICONTROL Database Errors]** フレーム：選択した期間のデータベースエラーを表示します。 解析されるエラーは次のとおりです。

* &#39;% 一時テーブルに割り当てられたメモリサイズが innodb_buffer_pool_size%&#39;）の 20% を超えています（「temp_tbl_buff_pool」として）
* &#39;%\[ERROR\] WSREP: rbr write fail%&#39;） as &#39;rbr_write_fail&#39;
* &#39;%mysqld: Disk full%&#39;）を&#39;disk_full&#39;として使用します
* &#39;% エラー番号 28%&#39;）は&#39;err_28&#39;です。
* &#39;%rollback%&#39;）を&#39;rollback&#39;として使用します
* &#39;%Foreign key constraint failes for table%&#39;） as &#39;foreign_key_constraint&#39;
* &#39;%Error_code: 1114%&#39;） as &#39;sql_1114_full&#39;
* &#39;%CRITICAL: SQLSTATE[000 HY] [2006] MySQL server has gone away%&#39;）を&#39;sql_gone&#39;として設定します
* &#39;%SQLSTATE[000 HY] [1040] 「sql_1040」として設定された接続が多すぎます（%）
* &#39;%CRITICAL: SQLSTATE[000 HY] [2002]%&#39;） as &#39;sql_2002&#39;
* &#39;%SQLSTATE[08S01]:%&#39;） as &#39;sql_1047&#39;
* &#39;%[警告] 接続 %&#39;）を&#39;aborted_conn&#39;として中止しました
* &#39;%SQLSTATE[23000]：整合性制約違反：%&#39;）を「sql_23000」として使用しました
* &#39;%1205 ロック待機タイムアウト %&#39;）を&#39;sql_1205&#39;として使用します
* &#39;%SQLSTATE[000 HY] [1049] Unknown database%&#39;） as &#39;sql_1049&#39;
* &#39;%SQLSTATE[42S02]: ベース テーブルまたはビューが見つかりません：%&#39;） （&#39;sql_42S02&#39;）
* &#39;% 一般エラー：1114%&#39;）を&#39;sql_1114&#39;として返します
* &#39;%SQLSTATE[40001]%&#39;） as &#39;sql_1213&#39;
* &#39;%SQLSTATE[42S22]：列が見つかりません：1054 不明な列 %） （「sq1_1054」として）
* &#39;%SQLSTATE[42000]：構文エラーまたはアクセス違反：%&#39;）を「sql_42000」として使用します
* &#39;%SQLSTATE[21000]: カーディナリティ違反：%&#39;）を「sql_1241」として使用します
* &#39;%SQLSTATE[22003]:%&#39;） as &#39;sql_22003&#39;
* &#39;%SQLSTATE[000 HY] [9000] IP アドレスが %）のクライアントを&#39;sql_9000&#39;として設定します
* &#39;%SQLSTATE[000 HY]：一般エラー：2014%）が「sql_2014」として返されます
* &#39;%1927 接続が切断されました %&#39;）を&#39;sql_1927&#39;として使用しました
* &#39;%1062 \[ERROR\] InnoDB:%&#39;）を&#39;sql_1062_e&#39;として使用します
* &#39;%[注意] WSREP: メモリ マップをディスクにフラッシュしています…%&#39;）を&#39;mem_map_flush&#39;として使用しています
* &#39;% 内部 MariaDB エラーコード：1146%&#39;）を&#39;sql_1146&#39;として返します
* &#39;% 内部 MariaDB エラーコード：1062%&#39;）を&#39;sql_1062&#39; * &#39;%1062 [警告] InnoDB:%&#39;）を&#39;sql_1062_w&#39;として使用します
* &#39;% 内部 MariaDB エラーコード：1064%&#39;）を&#39;sql_1064&#39;として返します
* &#39;%InnoDB: ファイル %&#39;）で&#39;assertion_err&#39;としてアサーションに失敗しました
* &#39;%mysqld_safe 現在実行中のプロセスの数：0%&#39;）を&#39;mysql_oom&#39;として返します。
* &#39;%\[ERROR\] mysqld は&#39;mysql_sigterm&#39;として signal%&#39;）を取得しました
* &#39;%1452%&#39;）を&#39;sql_1452&#39;として追加できません
* &#39;%ERROR 1698%&#39;）を&#39;sql_1698&#39;として返します
* &#39;%SQLSTATE[000 HY]：一般的なエラー：3%）を「cnt_wrt_tmp」として使用する
* &#39;% 一般エラー：1 %&#39;）を&#39;sql_syntax&#39;として使用します
* &#39;%42S22%&#39;）を&#39;sql_42S22&#39;として使用します
* &#39;%InnoDB: エラー（キーの重複） %&#39;）を&#39;innodb_dup_key&#39;として返します

## [!UICONTROL Database traces]

![データベースのトレース](../../assets/tools/php-tab-database-traces.jpg)

この **[!UICONTROL Database traces]** フレームは、データベース・トレース情報を表示します。 このフレームは、選択したタイムラインの APM トランザクションの概要ビューに合わせて配置されます。

## [!UICONTROL Database mysql-slow.log]

![データベース mysql-slow.log](../../assets/tools/php-tab-database-mysql-slow-log.jpg)

この **[!UICONTROL Database mysql-slow.log]** フレームは、内にあったクエリステートメントのタイプを示します。 `mysql-slow.log` 選択した期間のファイル。
