---
title: キャッシュの概要と設定オプション
description: バックエンドストレージ、フロントエンド設定、Varnish、Redis、Valkey、L2 キャッシュによるフルページキャッシュなど、Adobe Commerceでのキャッシュについて説明します。
feature: Configuration, Cache
exl-id: 6effa069-c043-411a-b161-01210be17391
autotag-review: '2026-06-22T20:28:12.484Z'
TQID: 'https://experienceleague.adobe.com/oDoZ1o2IWXsDTo84XQygWZYVmfVHWbk-CuqaU47laU4'
product_v2: id: b974b164-8a4e-43b8-a9e2-8e67ec131677id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2: id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: dbc1f6d0edff87130604d4762477ee5892a7aafc
workflow-type: tm+mt
source-wordcount: 589
ht-degree: 0%

---

# キャッシュの概要と設定オプション

Adobe Commerceは、データベースの負荷を軽減し、冗長な処理を最小限に抑え、ページ配信を高速化するために、多層キャッシングアーキテクチャに依存しています。 アプリケーションレベルでは、Commerceは12種類以上の[ キャッシュタイプ ](../cli/manage-cache.md#clean-and-flush-cache-types)を管理します。これらは、設定、レイアウト、ブロックHTML、コレクションなど、それぞれ[Redis](config-redis.md)や[Valkey](config-valkey.md)などの専用のストレージバックエンドにルーティングできます。 オンプレミスのデプロイメントでのフルページキャッシュの場合、Adobeでは[Varnish](config-varnish.md)を強くお勧めします。 Commerce on Cloudのデプロイメントでは、Fastlyを使用します。 [L2 キャッシュ ](level-two-cache.md)や[静的コンテンツ署名](static-content-signing.md)などの追加レイヤーは、高トラフィックのマルチノード展開のパフォーマンスをさらに向上させます。

このガイドでは、各キャッシングレイヤーの仕組みを説明し、デプロイメント要件に合わせてフロントエンド、バックエンド、高度なオプションを設定する方法を説明します。

## フロントエンドのキャッシュ

キャッシュフロントエンドとは、Commerceとキャッシュストレージバックエンド間のインターフェイスのことです。 複数のフロントエンドを定義し、それぞれ異なるバックエンド設定を使用して、特定の[ キャッシュタイプ ](../cli/manage-cache.md#clean-and-flush-cache-types)を各フロントエンドに割り当てることができます。  設定の詳細については、[ キャッシュフロントエンドの設定](cache-types.md)を参照してください。

## バックエンドのキャッシュ

キャッシュバックエンドは、キャッシュされたデータの基礎となるストレージメカニズムです。 Commerceにはデフォルトのファイルシステムバックエンドが用意されていますが、RedisやValkeyなどの他のバックエンドを設定して、パフォーマンスと拡張性を向上させることができます。 使用可能なオプションについて詳しくは、[ キャッシュバックエンドオプション ](cache-options.md)を参照してください。

## Varnishによるフルページのキャッシュ

[Varnish Cache](config-varnish.md)は、すべてのページをメモリにキャッシュするHTTP アクセラレータです。 オンプレミスの本番環境では、組み込みのフルページキャッシュよりも大幅に高速であるため、AdobeではVarnishを強くお勧めします。 クラウド環境のCommerceでは、Varnishの代わりに[Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly)をフルページのキャッシュに使用します。

>[!NOTE]
>
>Varnishは、web サーバーの前でリバースプロキシとして動作し、Commerce キャッシュバックエンド設定を変更する必要はありません。

## L2 （2 レベル）キャッシュ

[L2 キャッシュ ](level-two-cache.md)は、リモート キャッシュ （RedisまたはValkey）を信頼できる唯一の情報源として使用しながら、各web ノードにキャッシュ データをローカルに保存します。 これにより、web ノードとリモートキャッシュ間のネットワークトラフィックが削減され、トラフィックの多いサイトのパフォーマンスが向上します。

## 静的なコンテンツキャッシュ

[静的コンテンツ署名](static-content-signing.md)は、デプロイメントバージョンをファイル URLに埋め込むことで、静的リソース（CSS、JavaScript、画像）のブラウザーキャッシュを無効にします。

## キャッシュ用語

[!DNL Commerce]は次のキャッシュ用語を使用しています：

- **Frontend** — ストレージをキャッシュするためのインターフェイスまたはゲートウェイ。[Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend)によって実装されています。
- **キャッシュタイプ** — [!DNL Commerce]で提供される組み込み型（`config`、`layout`、`block_html`、`full_page`など）または[ カスタムタイプ ](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/)のいずれか。
- **Backend** — [Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend)によって実装された[ キャッシュストレージ ](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html)の詳細を指定します。
- **2 レベルのバックエンド** — キャッシュ レコードを、ローカル （高速） キャッシュとリモート （共有） キャッシュの2つのバックエンドに保存します。 [L2 キャッシュ設定](level-two-cache.md)を参照してください。

## 設定オプション

フロントエンドからタイプへのマッピングとキャッシュ設定構文の場合：

**オンプレミス** – キャッシュ設定は2つのファイルに保存されます。

- `<magento_root>/app/etc/di.xml` — グローバル依存関係インジェクション設定。 指定された`default` キャッシュ フロントエンドを変更するには、このファイルを変更します。
- `<magento_root>/app/etc/env.php` – 環境固有の設定。 カスタムキャッシュフロントエンドを設定するには、このファイルを変更します。 このファイルは、`di.xml`の同等の設定を上書きします。

詳細は、次を参照してください。

- [ キャッシュフロントエンドの設定](cache-types.md) – 特定のキャッシュタイプにキャッシュフロントエンドを関連付ける
- [ キャッシュバックエンドオプション ](cache-options.md) – バックエンドオプション参照

**クラウド上のAdobe Commerce**-`.magento.env.yaml`の`CACHE_CONFIGURATION`とのキャッシュを設定します。 RedisおよびValkey サービス設定に関する[ ベストプラクティス ](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md)を参照してください。
