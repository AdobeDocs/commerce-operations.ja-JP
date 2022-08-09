---
title: メッセージキュー：概要
description: メッセージキューのフレームワークと、Adobe CommerceおよびMagento Open Sourceアプリケーションでの動作についてお読みください。
source-git-commit: c65c065c5f9ac2847caa8898535afdacf089006a
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---


# メッセージキュー：概要

Message Queue Framework（MQF；メッセージキューフレームワーク）は、 [モジュール](https://glossary.magento.com/module) メッセージをキューに公開する場合。 また、非同期でメッセージを受信するコンシューマーも定義します。 MQF は [RabbitMQ](https://www.rabbitmq.com) メッセージを送受信するためのスケーラブルなプラットフォームを提供するメッセージングブローカーとして。 また、配信されなかったメッセージを保存するメカニズムも含まれています。 RabbitMQ は、Advanced Message Queuing Protocol(AMQP)0.9.1 の仕様に基づいています。

次の図に、メッセージキューフレームワークを示します。

![メッセージキューフレームワーク](../../assets/configuration/mq-framework.png)

- A [媒体社](https://glossary.magento.com/publisher-subscriber-pattern) は、exchange にメッセージを送信するコンポーネントです。 公開先の交換と、送信するメッセージの形式を把握します。

- Exchange は、パブリッシャーからメッセージを受け取り、キューに送信します。 RabbitMQ は複数のタイプの交換をサポートしていますが、コマースはトピック交換のみを使用します。 トピックには、ドットで区切られたテキスト文字列を含むルーティングキーが含まれます。 トピック名の形式は次のとおりです。 `string1.string2`:例： `customer.created` または `customer.sent.email`.

   ブローカーでは、メッセージの転送ルールを設定する際にワイルドカードを使用できます。 アスタリスク (`*`) を置き換えます。 _1 つ_ 文字列またはシャープ記号 (`#`) をクリックして、0 個以上の文字列を置き換えます。 例： `customer.*` 次の項目をフィルターします： `customer.create` および `customer.delete`ではなく `customer.sent.email`. ただし、 `customer.#` 次の項目をフィルターします： `customer.create`,  `customer.delete`、および `customer.sent.email`.

- キューは、メッセージを格納するバッファです。

- 消費者がメッセージを受け取る。 どのキューを使用するかを把握します。 メッセージのプロセッサーを特定のキューにマッピングできます。

基本的なメッセージキューシステムは、RabbitMQ を使用せずに設定することもできます。 このシステムでは、MySQL [アダプタ](https://glossary.magento.com/adapter) メッセージをデータベースに格納します。 3 つのデータベーステーブル (`queue`, `queue_message`、および `queue_message_status`) メッセージキューのワークロードを管理します。 Cron ジョブは、消費者がメッセージを受信できるようにします。 このソリューションは、あまり拡張性が高くありません。 可能な限り、RabbitMQ を使用する必要があります。
