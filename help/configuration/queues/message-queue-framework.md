---
title: メッセージキューの概要
description: メッセージキューフレームワークとAdobe Commerce アプリケーションとの連携方法について説明します。
exl-id: 21e7bc3e-6265-4399-9d47-d3b9f03dfef6
source-git-commit: 7610a5843b526a765dd35188722b7be8e6051049
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# メッセージキューの概要

メッセージキューフレームワーク（MQF）は、モジュールがキューにメッセージを公開できるようにするシステムです。 また、メッセージを非同期で受信する [&#x200B; コンシューマー &#x200B;](consumers.md) も定義します。 MQF は、複数のメッセージブローカーをサポートします。

- **[[!DNL RabbitMQ]](https://www.rabbitmq.com)** - プライマリメッセージングブローカー。メッセージを送受信するためのスケーラブルなプラットフォームを提供します。 未配信のメッセージを保存するメカニズムが含まれており、Advanced Message Queuing Protocol （AMQP） 0.9.1 仕様に基づいています。
- **[Apache ActiveMQ Artemis](https://activemq.apache.org/components/artemis/)** - STOMP （Simple Text Oriented Messaging Protocol）を使用して信頼性と拡張性の高いメッセージングを行う代替メッセージングブローカー。 Adobe Commerce 2.4.5 以降のバージョンで導入。

## RabbitMQ （AMQP）

次の図に、メッセージキューフレームワークを示します。

![&#x200B; メッセージキューフレームワーク &#x200B;](../../assets/configuration/mq-framework.png)

- パブリッシャーは、メッセージを取引所に送信するコンポーネントです。 公開先の交換と、送信するメッセージの形式がわかります。

- 交換機はパブリッシャーからメッセージを受信し、キューに送信します。 [!DNL RabbitMQ] は複数の種類の交換をサポートしていますが、Commerceではトピック交換のみを使用します。 トピックにはルーティングキーが含まれます。ルーティングキーには、ドットで区切られたテキスト文字列が含まれます。 トピック名の形式は `string1.string2` です。たとえば、`customer.created` または `customer.sent.email` です。

  ブローカーでは、メッセージ転送のルールを設定する際にワイルドカードを使用できます。 アスタリスク（`*`）を使用すると _1_ 文字列を置き換え、シャープ記号（`#`）を使用すると 0 個以上の文字列を置き換えることができます。 例えば、`customer.*` は `customer.create` と `customer.delete` に対してフィルタリングしますが、`customer.sent.email` に対してはフィルタリングしません。 ただし、`customer.#` は `customer.create`、`customer.delete`、`customer.sent.email` に対してフィルタリングします。

- キューは、メッセージを格納するバッファです。

- 消費者がメッセージを受信します。 使用するキューがわかります。 メッセージのプロセッサを特定のキューにマップできます。

## Apache ActiveMQ Artemis （STOMP）

Adobe Commerceは、RabbitMQ の代わりに、Simple Text Oriented Messaging Protocol （STOMP）を使用したメッセージングブローカーとして [Apache ActiveMQ Artemis](https://activemq.apache.org/components/artemis/) もサポートしています。

>[!NOTE]
>
>ActiveMQ Artemis は、Adobe Commerce 2.4.5 以降のバージョンで導入されました。

次の図は、ActiveMQ Artemis を使用した STOMP フレームワークを示しています。

![STOMP フレームワーク &#x200B;](../../assets/configuration/stomp-framework.png)

### STOMP フレームワーク・コンポーネント

- **パブリッシャー** は、メッセージを宛先（キューまたはトピック）に送信するコンポーネントです。 公開先と、送信するメッセージの形式がわかります。

- STOMP の **宛先** は、AMQP の交換と同様の役割を果たし、パブリッシャーからメッセージを受信してルーティングします。 STOMP は、ドット（例：`customer.created` または `inventory.updated`）を使用した階層的な命名パターンを使用して、直接宛先アドレスを使用します。

  Adobe Commerceでは、STOMP 宛先に対して、ポイントツーポイントのメッセージ配信を提供する **ANYCAST** アドレッシングモードを使用します。 ANYCAST モードでは、使用可能なコンシューマーのプールから 1 つのコンシューマーにのみメッセージが配信されるため、複数のコンシューマー・インスタンス間でのロード・バランシングと作業分散が可能になります。

- **キュー** は、メッセージを格納するバッファーです。 ANYCAST アドレッシングを使用すると、キューは、複数のコンシューマーが同じ宛先に接続されている場合でも、メッセージが 1 つのコンシューマーにのみ配信されるようにします。

- **コンシューマー** は、宛先からメッセージを受信します。 購読する宛先を把握し、様々な確認モード（自動、クライアントまたはクライアント個別）でメッセージを処理できます。

## MySQL アダプター（フォールバック）

外部メッセージブローカを使用せずに、基本的なメッセージキューシステムをセットアップすることもできます。 このシステムでは、MySQL アダプタがメッセージをデータベースに格納します。 3 つのデータベース・テーブル（`queue`、`queue_message`、`queue_message_status`）がメッセージ・キューのワークロードを管理します。 Cron ジョブは、コンシューマーがメッセージを受信できるようにします。 このソリューションは拡張性に欠けます。 [!DNL RabbitMQ] や Apache ActiveMQ Artemis などの外部メッセージブローカーは、実稼動環境にできるだけ使用する必要があります。

## 関連情報

インストールおよび設定手順については、以下を参照してください。

- [RabbitMQ のインストールと設定](../../installation/prerequisites/rabbitmq.md)
- [ActiveMQ Artemis のインストールと設定](../../installation/prerequisites/activemq.md)
- [メッセージキューの管理](manage-message-queues.md)
- [メッセージキューコンシューマー](consumers.md)
