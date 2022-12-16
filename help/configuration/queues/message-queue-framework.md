---
title: メッセージキュー：概要
description: メッセージキューのフレームワークと、Adobe CommerceおよびMagento Open Sourceアプリケーションでの動作についてお読みください。
source-git-commit: 78ad565f051f254229424ddcdb8ce633d3a78ec6
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---


# メッセージキュー：概要

Message Queue Framework（MQF；メッセージキューフレームワーク）は、 [モジュール](https://glossary.magento.com/module) メッセージをキューに公開する場合。 また、 [消費者](consumers.md) を呼び出すと、メッセージが非同期で受信されます。 MQF は [[!DNL RabbitMQ]](https://www.rabbitmq.com) メッセージを送受信するためのスケーラブルなプラットフォームを提供するメッセージングブローカーとして。 また、配信されなかったメッセージを保存するメカニズムも含まれています。 [!DNL RabbitMQ] は、AMQP(Advanced Message Queuing Protocol) 0.9.1 仕様に基づいています。

次の図に、メッセージキューフレームワークを示します。

![メッセージキューフレームワーク](../../assets/configuration/mq-framework.png)

- A [媒体社](https://glossary.magento.com/publisher-subscriber-pattern) は、exchange にメッセージを送信するコンポーネントです。 公開先の交換と、送信するメッセージの形式を把握します。

- Exchange は、パブリッシャーからメッセージを受け取り、キューに送信します。 ただし [!DNL RabbitMQ] は複数のタイプの交換をサポートしています。Commerce ではトピック交換のみを使用します。 トピックには、ドットで区切られたテキスト文字列を含むルーティングキーが含まれます。 トピック名の形式は次のとおりです。 `string1.string2`:例： `customer.created` または `customer.sent.email`.

   ブローカーでは、メッセージの転送ルールを設定する際にワイルドカードを使用できます。 アスタリスク (`*`) を置き換えます。 _1 つ_ 文字列またはシャープ記号 (`#`) をクリックして、0 個以上の文字列を置き換えます。 例： `customer.*` 次の項目をフィルターします： `customer.create` および `customer.delete`ではなく `customer.sent.email`. ただし、 `customer.#` 次の項目をフィルターします： `customer.create`,  `customer.delete`、および `customer.sent.email`.

- キューは、メッセージを格納するバッファです。

- 消費者がメッセージを受け取る。 どのキューを使用するかを把握します。 メッセージのプロセッサーを特定のキューにマッピングできます。

基本的なメッセージキューシステムは、 [!DNL RabbitMQ]. このシステムでは、MySQL [アダプタ](https://glossary.magento.com/adapter) メッセージをデータベースに格納します。 3 つのデータベーステーブル (`queue`, `queue_message`、および `queue_message_status`) メッセージキューのワークロードを管理します。 Cron ジョブは、消費者がメッセージを受信できるようにします。 このソリューションは、あまり拡張性が高くありません。 [!DNL RabbitMQ] 可能な限り使用する必要があります。
