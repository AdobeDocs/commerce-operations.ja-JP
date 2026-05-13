---
title: キャッシュの概要と設定オプション
description: バックエンドストレージ、フロントエンド設定、Varnish、Redis、Valkey、L2 キャッシュによるフルページキャッシュなど、Adobe Commerceでのキャッシュについて説明します。
feature: Configuration, Cache
exl-id: 6effa069-c043-411a-b161-01210be17391
source-git-commit: 9cd0f2a84772e2d68fd15a00651216abfa9ec91c
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---

# キャッシュの概要と設定オプション

Adobe Commerceは、データベースの負荷を軽減し、冗長な処理を最小限に抑え、ページ配信を高速化するために、多層キャッシングアーキテクチャに依存しています。 アプリケーションレベルでは、Commerceは12種類以上の[&#x200B; キャッシュタイプ &#x200B;](../cli/manage-cache.md#clean-and-flush-cache-types)を管理します。これらは、設定、レイアウト、ブロックHTML、コレクションなど、それぞれ[Redis](config-redis.md)や[Valkey](config-valkey.md)などの専用のストレージバックエンドにルーティングできます。 フルページキャッシュの場合、Adobeでは、キャッシュされたページをメモリから直接提供するHTTP アクセラレータである[Varnish](config-varnish.md)を強くお勧めします。 [L2 キャッシュ &#x200B;](level-two-cache.md)や[静的コンテンツ署名](static-content-signing.md)などの追加レイヤーは、高トラフィックのマルチノード展開のパフォーマンスをさらに向上させます。

このガイドでは、各キャッシングレイヤーの仕組みを説明し、デプロイメント要件に合わせてフロントエンド、バックエンド、高度なオプションを設定する方法を説明します。

## フロントエンドのキャッシュ

キャッシュフロントエンドとは、Commerceとキャッシュストレージバックエンド間のインターフェイスのことです。 複数のフロントエンドを定義し、それぞれ異なるバックエンド設定を使用して、特定の[&#x200B; キャッシュタイプ &#x200B;](../cli/manage-cache.md#clean-and-flush-cache-types)を各フロントエンドに割り当てることができます。  設定の詳細については、[&#x200B; キャッシュフロントエンドの設定](cache-types.md)を参照してください。

## バックエンドのキャッシュ

キャッシュバックエンドは、キャッシュされたデータの基礎となるストレージメカニズムです。 Commerceにはデフォルトのファイルシステムバックエンドが用意されていますが、RedisやValkeyなどの他のバックエンドを設定して、パフォーマンスと拡張性を向上させることができます。 使用可能なオプションについて詳しくは、[&#x200B; キャッシュバックエンドオプション &#x200B;](cache-options.md)を参照してください。

## Varnishによるフルページのキャッシュ

[Varnish Cache](config-varnish.md)は、すべてのページをメモリにキャッシュするHTTP アクセラレータです。 Adobeでは、組み込みのフルページキャッシュよりも大幅に高速なVarnishを本番環境に強くお勧めします。

>[!NOTE]
>
>Varnishは、web サーバーの前でリバースプロキシとして動作し、Commerce キャッシュバックエンド設定を変更する必要はありません。

## L2 （2 レベル）キャッシュ

[L2 キャッシュ &#x200B;](level-two-cache.md)は、リモート キャッシュ （RedisまたはValkey）を信頼できる唯一の情報源として使用しながら、各web ノードにキャッシュ データをローカルに保存します。 これにより、web ノードとリモートキャッシュ間のネットワークトラフィックが削減され、トラフィックの多いサイトのパフォーマンスが向上します。

## 静的なコンテンツキャッシュ

[静的コンテンツ署名](static-content-signing.md)は、デプロイメントバージョンをファイル URLに埋め込むことで、静的リソース（CSS、JavaScript、画像）のブラウザーキャッシュを無効にします。

## キャッシュ用語

[!DNL Commerce]は次のキャッシュ用語を使用しています：

- **Frontend** — ストレージをキャッシュするためのインターフェイスまたはゲートウェイ。[Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend)によって実装されています。
- **キャッシュタイプ** — [!DNL Commerce]で提供される組み込み型（`config`、`layout`、`block_html`、`full_page`など）または[&#x200B; カスタムタイプ &#x200B;](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/)のいずれか。
- **Backend** — [Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend)によって実装された[&#x200B; キャッシュストレージ &#x200B;](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html)の詳細を指定します。
- **2 レベルのバックエンド** — キャッシュ レコードを、ローカル （高速） キャッシュとリモート （共有） キャッシュの2つのバックエンドに保存します。 [L2 キャッシュ設定](level-two-cache.md)を参照してください。

## 設定オプション

キャッシュ設定は、次の2つのファイルに保存されます。

- `<magento_root>/app/etc/di.xml` — グローバル依存関係インジェクション設定。 指定された`default` キャッシュ フロントエンドを変更するには、このファイルを変更します。
- `<magento_root>/app/etc/env.php` – 環境固有の設定。 カスタムキャッシュフロントエンドを設定するには、このファイルを変更します。 このファイルは、`di.xml`の同等の設定を上書きします。

フロントエンドからタイプへのマッピングとキャッシュ設定の構文について詳しくは、次を参照してください。

- [&#x200B; キャッシュフロントエンドの設定](cache-types.md) – 特定のキャッシュタイプにキャッシュフロントエンドを関連付けます
- [&#x200B; キャッシュバックエンドオプション &#x200B;](cache-options.md) — バックエンドオプション参照
