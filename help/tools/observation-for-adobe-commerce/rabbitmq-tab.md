---
title: The [!UICONTROL [!DNL RabbitMQ]] タブ
description: 詳しくは、 [!UICONTROL [!DNL RabbitMQ]] タブ [!DNL Observation for Adobe Commerce].
exl-id: c5370c30-fed8-4f45-89c3-ef0d6ad41a89
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# The [!UICONTROL [!DNL RabbitMQ]] タブ

The **[!UICONTROL [!DNL RabbitMQ]]** タブには、次の項目に焦点を当てた情報が含まれます： [!DNL RabbitMQ] シグナル。

## [!UICONTROL [!DNL RabbitMQ] Infrastructure events]

![[!DNL RabbitMQ] インフラストラクチャイベント](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-1.jpeg)

The **[!UICONTROL [!DNL RabbitMQ] Infrastructure events]** frame は、 [!DNL RabbitMQ] 選択した期間内に発生した

* `%Response [error] for node [rabbit@host1]: unexpected http response from%`) として `unexpected_resp_node1`
* `%Response [error] for node [rabbit@host2]: unexpected http response from%`) として `unexpected_resp_node2`
* `%Response [error] for node [rabbit@host3]: unexpected http response from%`) として `unexpected_resp_node3`
* `%Response [error] for node [rabbit@host3]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host3": context deadline exceeded%`) として `node3_timeout_exceeded`
* `%Response [error] for node [rabbit@host1]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host1": context deadline exceeded%`) として `node1_timeout_exceeded`
* `%Response [error] for node [rabbit@host2]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host2": context deadline exceeded%`) として `node2_timeout_exceeded`
* `%401 Unauthorized%`) として `401_unauth`
* `%401 Unauthorized%`) として `401_unauth`
* `%Service restarted: rabbitmq-server%`) として `rmq_service_restart`
* `%Response [failed] for node [rabbit@host1]: nodedown%`) として `rmq_node1_down`
* `%Response [failed] for node [rabbit@host2]: nodedown%`) として `rmq_node2_down`
* `%Response [failed] for node [rabbit@host2]: nodedown%`) として `rmq_node2_down`
* `%Entity modified: exchange/bindings.destination%`) として `rmq_entity_modified`
* `%Entity modified: exchange/bindings.destination%`) として `rmq_entity_modified`
* `%Entity modified: queue/exclusive%`) として `rmq_entity_created_q_exclusive` `%Entity modified: queue/auto_delete%`) として `rmq_entity_q_delete`
* `%Entity modified: queue/durable%`) として `rmq_entity_modified_q_durable`
* `%Entity modified: version/management%`) として `rmq_entity_modified_ver_mgt`
* `%Entity modified: version/management%`) として `rmq_entity_modified_ver_mgt`

## [!UICONTROL [!DNL RabbitMQ] service start/stop signals]

![[!DNL RabbitMQ] サービス開始/停止シグナル](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-2.jpeg)

このフレームには [!DNL RabbitMQ] 選択した期間に発生したサービス開始/停止シグナル：

* `%RabbitMQ is asked to stop...%`) として `rabbitmq_stop`
* `%Starting RabbitMQ%`) として `rabbitmq_start`

## [!UICONTROL [!DNL RabbitMQ] errors]

![[!DNL RabbitMQ] エラー](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-3.jpeg)

このフレームには [!DNL RabbitMQ] 選択した期間中に発生したエラー：

* `%exit with reason {case_clause,timeout} and stacktrace {rabbit_mgmt_wm_healthchecks%}` as `exit_timeout`
* `%client unexpectedly closed TCP connection%`) として `client_closed_tcp_conn`
* `%at undefined exit with reason shutdown in context shutdown_error%`) として `undef_exit`
* `%Connection attempt from disallowed node%`) として `disallowed_node`
* `%closing AMQP connection%`) として `rmq_err_amqp_conn`

## [!UICONTROL [!DNL RabbitMQ] node status]

![[!DNL RabbitMQ] ノードステータス](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-4.jpeg)

* `%rabbit on node rabbit@host1 down%`) として `rmq_node1_down`
* `%rabbit on node rabbit@host2 down%`) として `rmq_node2_down`
* `%rabbit on node rabbit@host3 down%`) として `rmq_node3_down`
* `%rabbit on node rabbit@host1 up%`) として `rmq_node1_up`
* `%rabbit on node rabbit@host2 up%`) として `rmq_node2_up`
* `%rabbit on node rabbit@host3 up%`) として `rmq_node3_up`

## [!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]

![[!DNL RabbitMQ] キュー別メッセージの概要ステータス](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-5.jpeg)

The **[!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]** グラフには、 [!DNL RabbitMQ] 選択した期間のキュー。

## [!UICONTROL [!DNL RabbitMQ] Message Detail Summary]

![[!DNL RabbitMQ] メッセージの詳細の概要](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-6.jpeg)

* `%report.ERROR: Cron Job consumers_runner has an error: NOT_FOUND - no queue%`) として `queue_err`
* `%report.ERROR: Cron Job consumers_runner has an error: NOT_FOUND - no queue%`) として `queue_err`
* `%authenticated and granted access to vhost%`) として `auth`
* `%closing AMQP connection%`) として `close_conn`

## [!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]

![[!DNL RabbitMQ] キュー消費 MB](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-7.jpeg)

The **[!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]** グラフは、それぞれが消費したバイト数を示します [!DNL RabbitMQ] 選択した期間にキューを追加します。

## [!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]

![[!DNL RabbitMQ] 公開済みメッセージ（キュー別）](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-8.jpeg)

The **[!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]** グラフは、それぞれが消費したバイト数を示します [!DNL RabbitMQ] 選択した期間にキューを追加します。

## [!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]

![[!DNL RabbitMQ] キュー別の公開済みメッセージのスループット](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-9.jpeg)

The **[!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]** グラフには、1 秒あたりの平均公開済みメッセージ数が表示されます [!DNL RabbitMQ] 選択した期間にキューを追加します。

## [!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]

![[!DNL RabbitMQ] キュー別の合計メッセージスループット](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-10.jpeg)

The **[!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]** グラフは、1 秒あたりの平均メッセージ総数を示します [!DNL RabbitMQ] 選択した期間にキューを追加します。

## [!UICONTROL [!DNL RabbitMQ] Consumers by Queue]

![[!DNL RabbitMQ] キュー別消費者](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-11.jpeg)

The **[!UICONTROL [!DNL RabbitMQ] Consumers by Queue]** グラフは、それぞれの平均消費者総数を示します [!DNL RabbitMQ] 選択した期間にキューを追加します。
