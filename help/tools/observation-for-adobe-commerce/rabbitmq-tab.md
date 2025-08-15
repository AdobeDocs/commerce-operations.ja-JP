---
title: '[[!UICONTROL [!DNL RabbitMQ]] タブ'
description: '[!UICONTROL [!DNL RabbitMQ] の [ [!DNL Observation for Adobe Commerce]] タブについて説明します。'
exl-id: c5370c30-fed8-4f45-89c3-ef0d6ad41a89
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# 「[!UICONTROL [!DNL RabbitMQ]]」タブ

「**[!UICONTROL [!DNL RabbitMQ]]**」タブには、[!DNL RabbitMQ] 信号に焦点を当てた情報があります。

## [!UICONTROL [!DNL RabbitMQ] Infrastructure events]

![[!DNL RabbitMQ] Infrastructure イベント ](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-1.jpeg)

**[!UICONTROL [!DNL RabbitMQ] Infrastructure events]** のフレームは、選択した期間に発生した [!DNL RabbitMQ] ストに関連するインフラストラクチャイベントを示します。

* `%Response [error] for node [rabbit@host1]: unexpected http response from%`） as `unexpected_resp_node1`
* `%Response [error] for node [rabbit@host2]: unexpected http response from%`） as `unexpected_resp_node2`
* `%Response [error] for node [rabbit@host3]: unexpected http response from%`） as `unexpected_resp_node3`
* `%Response [error] for node [rabbit@host3]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host3": context deadline exceeded%`） as `node3_timeout_exceeded`
* `%Response [error] for node [rabbit@host1]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host1": context deadline exceeded%`） as `node1_timeout_exceeded`
* `%Response [error] for node [rabbit@host2]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host2": context deadline exceeded%`） as `node2_timeout_exceeded`
* `%401 Unauthorized%`） as `401_unauth`
* `%401 Unauthorized%`） as `401_unauth`
* `%Service restarted: rabbitmq-server%`） as `rmq_service_restart`
* `%Response [failed] for node [rabbit@host1]: nodedown%`） as `rmq_node1_down`
* `%Response [failed] for node [rabbit@host2]: nodedown%`） as `rmq_node2_down`
* `%Response [failed] for node [rabbit@host2]: nodedown%`） as `rmq_node2_down`
* `%Entity modified: exchange/bindings.destination%`） as `rmq_entity_modified`
* `%Entity modified: exchange/bindings.destination%`） as `rmq_entity_modified`
* `%Entity modified: queue/exclusive%`） as `rmq_entity_created_q_exclusive` `%Entity modified: queue/auto_delete%`） as `rmq_entity_q_delete`
* `%Entity modified: queue/durable%`） as `rmq_entity_modified_q_durable`
* `%Entity modified: version/management%`） as `rmq_entity_modified_ver_mgt`
* `%Entity modified: version/management%`） as `rmq_entity_modified_ver_mgt`

## [!UICONTROL [!DNL RabbitMQ] service start/stop signals]

サ ![[!DNL RabbitMQ] ビス開始/停止シグナル ](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-2.jpeg)

このフレームは [!DNL RabbitMQ] 選択した期間に発生したサービス開始/停止シグナルを示します。

* `%RabbitMQ is asked to stop...%`） as `rabbitmq_stop`
* `%Starting RabbitMQ%`） as `rabbitmq_start`

## [!UICONTROL [!DNL RabbitMQ] errors]

![[!DNL RabbitMQ] エラー ](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-3.jpeg)

このフレームには、選択 [!DNL RabbitMQ] た期間に発生したエラーが表示されます。

* `%exit with reason {case_clause,timeout} and stacktrace {rabbit_mgmt_wm_healthchecks%}` as `exit_timeout`
* `%client unexpectedly closed TCP connection%`） as `client_closed_tcp_conn`
* `%at undefined exit with reason shutdown in context shutdown_error%`） as `undef_exit`
* `%Connection attempt from disallowed node%`） as `disallowed_node`
* `%closing AMQP connection%`） as `rmq_err_amqp_conn`

## [!UICONTROL [!DNL RabbitMQ] node status]

![[!DNL RabbitMQ] ノードのステータス ](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-4.jpeg)

* `%rabbit on node rabbit@host1 down%`） as `rmq_node1_down`
* `%rabbit on node rabbit@host2 down%`） as `rmq_node2_down`
* `%rabbit on node rabbit@host3 down%`） as `rmq_node3_down`
* `%rabbit on node rabbit@host1 up%`） as `rmq_node1_up`
* `%rabbit on node rabbit@host2 up%`） as `rmq_node2_up`
* `%rabbit on node rabbit@host3 up%`） as `rmq_node3_up`

## [!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]

![[!DNL RabbitMQ] メッセージの概要ステータス（キュー別） ](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-5.jpeg)

**[!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]** のグラフは、選択した期間の [!DNL RabbitMQ] キューによる公開済みメッセージの数を示します。

## [!UICONTROL [!DNL RabbitMQ] Message Detail Summary]

メッセ ![[!DNL RabbitMQ] ジの詳細の概要 ](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-6.jpeg)

* `%report.ERROR: Cron Job consumers_runner has an error: NOT_FOUND - no queue%`） as `queue_err`
* `%report.ERROR: Cron Job consumers_runner has an error: NOT_FOUND - no queue%`） as `queue_err`
* `%authenticated and granted access to vhost%`） as `auth`
* `%closing AMQP connection%`） as `close_conn`

## [!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]

![[!DNL RabbitMQ] キュー消費 MB](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-7.jpeg)

**[!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]** のグラフは、選択した期間に各 [!DNL RabbitMQ] キューで消費されたバイト数を示します。

## [!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]

公開済みメッセージをキュー別に ![[!DNL RabbitMQ] スト ](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-8.jpeg)

**[!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]** のグラフは、選択した期間に各 [!DNL RabbitMQ] キューで消費されたバイト数を示します。

## [!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]

公開 ![[!DNL RabbitMQ] れたメッセージのスループット （キュー別） ](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-9.jpeg)

**[!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]** のグラフは、選択した期間の [!DNL RabbitMQ] キューごとの 1 秒あたりの公開済みメッセージの平均数を示します。

## [!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]

![[!DNL RabbitMQ] キュー別の合計メッセージ スループット ](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-10.jpeg)

**[!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]** のグラフは、選択した期間の [!DNL RabbitMQ] キューごとの 1 秒あたりの平均メッセージ総数を示します。

## [!UICONTROL [!DNL RabbitMQ] Consumers by Queue]

キュー別の ![[!DNL RabbitMQ] コンシューマー ](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-11.jpeg)

**[!UICONTROL [!DNL RabbitMQ] Consumers by Queue]** のグラフは、選択した期間の各 [!DNL RabbitMQ] キュー別のコンシューマーの平均合計数を示します。
