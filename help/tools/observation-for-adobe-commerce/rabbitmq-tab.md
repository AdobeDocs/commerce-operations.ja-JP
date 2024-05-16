---
title: この [!UICONTROL [!DNL RabbitMQ]「」タブ
description: について説明します [!UICONTROL [!DNL RabbitMQ]] タブ / [!DNL Observation for Adobe Commerce].
exl-id: c5370c30-fed8-4f45-89c3-ef0d6ad41a89
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# この [!UICONTROL [!DNL RabbitMQ]] タブ

この **[!UICONTROL [!DNL RabbitMQ]]** タブには、に焦点を当てた情報があります [!DNL RabbitMQ] シグナル。

## [!UICONTROL [!DNL RabbitMQ] Infrastructure events]

![[!DNL RabbitMQ] インフラストラクチャイベント](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-1.jpeg)

この **[!UICONTROL [!DNL RabbitMQ] Infrastructure events]** フレームは、次の関連するインフラストラクチャイベントを示します [!DNL RabbitMQ] 選択した期間に発生したイベント：

* `%Response [error] for node [rabbit@host1]: unexpected http response from%`）を次として `unexpected_resp_node1`
* `%Response [error] for node [rabbit@host2]: unexpected http response from%`）を次として `unexpected_resp_node2`
* `%Response [error] for node [rabbit@host3]: unexpected http response from%`）を次として `unexpected_resp_node3`
* `%Response [error] for node [rabbit@host3]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host3": context deadline exceeded%`）を次として `node3_timeout_exceeded`
* `%Response [error] for node [rabbit@host1]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host1": context deadline exceeded%`）を次として `node1_timeout_exceeded`
* `%Response [error] for node [rabbit@host2]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host2": context deadline exceeded%`）を次として `node2_timeout_exceeded`
* `%401 Unauthorized%`）を次として `401_unauth`
* `%401 Unauthorized%`）を次として `401_unauth`
* `%Service restarted: rabbitmq-server%`）を次として `rmq_service_restart`
* `%Response [failed] for node [rabbit@host1]: nodedown%`）を次として `rmq_node1_down`
* `%Response [failed] for node [rabbit@host2]: nodedown%`）を次として `rmq_node2_down`
* `%Response [failed] for node [rabbit@host2]: nodedown%`）を次として `rmq_node2_down`
* `%Entity modified: exchange/bindings.destination%`）を次として `rmq_entity_modified`
* `%Entity modified: exchange/bindings.destination%`）を次として `rmq_entity_modified`
* `%Entity modified: queue/exclusive%`）を次として `rmq_entity_created_q_exclusive` `%Entity modified: queue/auto_delete%`）を次として `rmq_entity_q_delete`
* `%Entity modified: queue/durable%`）を次として `rmq_entity_modified_q_durable`
* `%Entity modified: version/management%`）を次として `rmq_entity_modified_ver_mgt`
* `%Entity modified: version/management%`）を次として `rmq_entity_modified_ver_mgt`

## [!UICONTROL [!DNL RabbitMQ] service start/stop signals]

![[!DNL RabbitMQ] サービス開始/停止シグナル](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-2.jpeg)

このフレームは、 [!DNL RabbitMQ] 選択した期間に発生したサービス開始/停止シグナル：

* `%RabbitMQ is asked to stop...%`）を次として `rabbitmq_stop`
* `%Starting RabbitMQ%`）を次として `rabbitmq_start`

## [!UICONTROL [!DNL RabbitMQ] errors]

![[!DNL RabbitMQ] エラー](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-3.jpeg)

このフレームは、 [!DNL RabbitMQ] 選択した期間に発生したエラー：

* `%exit with reason {case_clause,timeout} and stacktrace {rabbit_mgmt_wm_healthchecks%}` as `exit_timeout`
* `%client unexpectedly closed TCP connection%`）を次として `client_closed_tcp_conn`
* `%at undefined exit with reason shutdown in context shutdown_error%`）を次として `undef_exit`
* `%Connection attempt from disallowed node%`）を次として `disallowed_node`
* `%closing AMQP connection%`）を次として `rmq_err_amqp_conn`

## [!UICONTROL [!DNL RabbitMQ] node status]

![[!DNL RabbitMQ] ノードステータス](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-4.jpeg)

* `%rabbit on node rabbit@host1 down%`）を次として `rmq_node1_down`
* `%rabbit on node rabbit@host2 down%`）を次として `rmq_node2_down`
* `%rabbit on node rabbit@host3 down%`）を次として `rmq_node3_down`
* `%rabbit on node rabbit@host1 up%`）を次として `rmq_node1_up`
* `%rabbit on node rabbit@host2 up%`）を次として `rmq_node2_up`
* `%rabbit on node rabbit@host3 up%`）を次として `rmq_node3_up`

## [!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]

![[!DNL RabbitMQ] キュー別メッセージの高レベルの概要ステータス](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-5.jpeg)

この **[!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]** グラフは、による公開済みメッセージ数を表示します [!DNL RabbitMQ] 選択した期間のキュー。

## [!UICONTROL [!DNL RabbitMQ] Message Detail Summary]

![[!DNL RabbitMQ] メッセージの詳細の概要](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-6.jpeg)

* `%report.ERROR: Cron Job consumers_runner has an error: NOT_FOUND - no queue%`）を次として `queue_err`
* `%report.ERROR: Cron Job consumers_runner has an error: NOT_FOUND - no queue%`）を次として `queue_err`
* `%authenticated and granted access to vhost%`）を次として `auth`
* `%closing AMQP connection%`）を次として `close_conn`

## [!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]

![[!DNL RabbitMQ] キュー消費 MB](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-7.jpeg)

この **[!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]** グラフは、各で消費されたバイト数を示します [!DNL RabbitMQ] 選択した期間にキューに入れます。

## [!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]

![[!DNL RabbitMQ] 公開済みメッセージ （キュー別）](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-8.jpeg)

この **[!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]** グラフは、各で消費されたバイト数を示します [!DNL RabbitMQ] 選択した期間にキューに入れます。

## [!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]

![[!DNL RabbitMQ] 公開済みメッセージのスループット （キュー別）](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-9.jpeg)

この **[!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]** グラフは、1 秒あたりの平均公開済みメッセージ数をそれぞれで表示します [!DNL RabbitMQ] 選択した期間にキューに入れます。

## [!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]

![[!DNL RabbitMQ] キュー別の合計メッセージスループット](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-10.jpeg)

この **[!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]** グラフには、1 秒あたりのメッセージの平均合計数が各別に表示されます [!DNL RabbitMQ] 選択した期間にキューに入れます。

## [!UICONTROL [!DNL RabbitMQ] Consumers by Queue]

![[!DNL RabbitMQ] キュー別コンシューマー](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-11.jpeg)

この **[!UICONTROL [!DNL RabbitMQ] Consumers by Queue]** グラフは、平均消費者合計数を各別に表示します [!DNL RabbitMQ] 選択した期間にキューに入れます。
