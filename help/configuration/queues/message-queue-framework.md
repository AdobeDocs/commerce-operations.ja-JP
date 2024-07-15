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

メッセージキューフレームワーク（MQF）は、モジュールがキューにメッセージを公開できるようにするシステムです。 また、メッセージを非同期で受信する [ コンシューマー ](consumers.md) も定義します。 MQF は、メッセージの送受信に使用できるスケーラブルなプラットフォームを提供するメッセージング ブローカーとして [[!DNL RabbitMQ]](https://www.rabbitmq.com) を使用します。 また、未配信メッセージを保存するメカニズムも含まれています。 [!DNL RabbitMQ] は、Advanced Message Queuing Protocol （AMQP） 0.9.1 仕様に基づいています。

次の図に、メッセージキューフレームワークを示します。

![ メッセージキューフレームワーク ](../../assets/configuration/mq-framework.png)

- パブリッシャーは、メッセージを取引所に送信するコンポーネントです。 公開先の交換と、送信するメッセージの形式がわかります。

- 交換機はパブリッシャーからメッセージを受信し、キューに送信します。 [!DNL RabbitMQ] は複数の種類の交換をサポートしていますが、Commerceではトピック交換のみを使用します。 トピックにはルーティングキーが含まれます。ルーティングキーには、ドットで区切られたテキスト文字列が含まれます。 トピック名の形式は `string1.string2` です。たとえば、`customer.created` または `customer.sent.email` です。

  ブローカーでは、メッセージ転送のルールを設定する際にワイルドカードを使用できます。 アスタリスク（`*`）を使用すると _1_ 文字列を置き換え、シャープ記号（`#`）を使用すると 0 個以上の文字列を置き換えることができます。 例えば、`customer.*` は `customer.create` と `customer.delete` に対してフィルタリングしますが、`customer.sent.email` に対してはフィルタリングしません。 ただし、`customer.#` は `customer.create`、`customer.delete`、`customer.sent.email` に対してフィルタリングします。

- キューは、メッセージを格納するバッファです。

- 消費者がメッセージを受信します。 使用するキューがわかります。 メッセージのプロセッサを特定のキューにマップできます。

基本的なメッセージキューシステムは、[!DNL RabbitMQ] を使用せずにセットアップすることもできます。 このシステムでは、MySQL アダプタがメッセージをデータベースに格納します。 3 つのデータベース・テーブル（`queue`、`queue_message`、`queue_message_status`）がメッセージ・キューのワークロードを管理します。 Cron ジョブは、コンシューマーがメッセージを受信できるようにします。 このソリューションは拡張性に欠けます。 可能な限り [!DNL RabbitMQ] を使用すべきである。
