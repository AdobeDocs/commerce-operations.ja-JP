---
title: メッセージキューの概要
description: メッセージキューフレームワークとAdobe Commerce アプリケーションとの連携方法について説明します。
exl-id: 21e7bc3e-6265-4399-9d47-d3b9f03dfef6
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# メッセージキューの概要

メッセージキューフレームワーク（MQF）は、モジュールがキューにメッセージを公開できるようにするシステムです。 また、 [消費者](consumers.md) はメッセージを非同期で受信します。 この MQF は、 [[!DNL RabbitMQ]](https://www.rabbitmq.com) メッセージを送受信するためのスケーラブルなプラットフォームを提供するメッセージングブローカーとして。 また、未配信メッセージを保存するメカニズムも含まれています。 [!DNL RabbitMQ] は、Advanced Message Queuing Protocol （AMQP） 0.9.1 仕様に基づいています。

次の図に、メッセージキューフレームワークを示します。

![メッセージキューフレームワーク](../../assets/configuration/mq-framework.png)

- パブリッシャーは、メッセージを取引所に送信するコンポーネントです。 公開先の交換と、送信するメッセージの形式がわかります。

- 交換機はパブリッシャーからメッセージを受信し、キューに送信します。 ただし [!DNL RabbitMQ] は複数の種類の交換をサポートしていますが、Commerceではトピック交換のみを使用します。 トピックにはルーティングキーが含まれます。ルーティングキーには、ドットで区切られたテキスト文字列が含まれます。 トピック名の形式は、です。 `string1.string2`：例： `customer.created` または `customer.sent.email`.

  ブローカーでは、メッセージ転送のルールを設定する際にワイルドカードを使用できます。 アスタリスク（`*`）に変更します _1_ 文字列またはポンド記号（`#`）を選択して、0 個以上の文字列を置き換えます。 例： `customer.*` 次の条件でフィルタリングします `customer.create` および `customer.delete`が、ではない `customer.sent.email`. しかし `customer.#` 次の条件でフィルタリングします `customer.create`,  `customer.delete`、および `customer.sent.email`.

- キューは、メッセージを格納するバッファです。

- 消費者がメッセージを受信します。 使用するキューがわかります。 メッセージのプロセッサを特定のキューにマップできます。

基本的なメッセージキューシステムは、を使用せずにセットアップすることもできます [!DNL RabbitMQ]. このシステムでは、MySQL アダプタがメッセージをデータベースに格納します。 3 つのデータベーステーブル（`queue`, `queue_message`、および `queue_message_status`）メッセージキューのワークロードを管理します。 Cron ジョブは、コンシューマーがメッセージを受信できるようにします。 このソリューションは拡張性に欠けます。 [!DNL RabbitMQ] 可能な限り使用してください。
