---
title: キャッシュの概要と設定オプション
description: バックエンドストレージ、フロントエンド設定、Varnish、Redis、Valkey、L2 キャッシュによるフルページキャッシュなど、Adobe Commerceでのキャッシュについて説明します。
feature: Configuration, Cache
exl-id: 6effa069-c043-411a-b161-01210be17391
autotag-review: '2026-06-22T20:28:12.484Z'
TQID: 'https://experienceleague.adobe.com/oDoZ1o2IWXsDTo84XQygWZYVmfVHWbk-CuqaU47laU4'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 8c5dc151b00fd73e939c32fdc083fb0e8fc41dc8
workflow-type: tm+mt
source-wordcount: 536
ht-degree: 0%

---

# キャッシュの概要と設定オプション

Adobe Commerceでは、複数のキャッシングレイヤーを使用して、繰り返し処理の削減、データベースの読み込みの低減、応答時間の短縮を実現します。 これらのレイヤーは、リクエストとアセット配信の異なるポイントで動作します。

- **アプリケーションキャッシュ**&#x200B;は、Commerceのキャッシュタイプを使用して生成または処理されたデータを保存します。
- **HTTP フルページキャッシング**&#x200B;は、Commerce アプリケーションに到達する前にHTTP応答を完全に保存します。
- **L2 キャッシュ**&#x200B;は、共有リモートキャッシュストレージの前にある各web ノードにローカルキャッシュを追加できます。
- **静的コンテンツキャッシュ**&#x200B;を使用すると、ブラウザーでCSS、JavaScript、画像、その他の静的リソースを再利用できます。

このページでは、これらのレイヤーの概念的な概要と、それらの設定ガイダンスへのリンクについて説明します。 バックエンドの選択、実装の詳細、バージョン固有の設定については、[&#x200B; バックエンドのオプションとストレージの参照](cache-options.md)を参照してください。

## レイヤーのキャッシュ

### アプリケーションのキャッシュ

Commerce アプリケーションキャッシュは、次のように構成されています。

>[!BEGINSHADEBOX]

キャッシュタイプ→キャッシュフロントエンド→キャッシュバックエンド

>[!ENDSHADEBOX]

キャッシュの種類&#x200B;**は、設定、レイアウト、ブロック HTML、ページ全体の内容など、キャッシュされるデータの種類を示します。**&#x200B;**キャッシュフロントエンド**&#x200B;は、1つ以上のキャッシュタイプをストレージに接続します。 **キャッシュバックエンド**&#x200B;は、ストレージ実装を提供します。

個別のキャッシュ設定またはストレージが必要な場合は、異なるキャッシュタイプを異なるフロントエンドに割り当てることができます。 設定の詳細については、[&#x200B; キャッシュフロントエンドとタイプの設定](cache-types.md)を参照してください。

### フルページ HTTP キャッシュ

HTTP フルページキャッシングでは、HTTPまたはCDN レイヤーに完全な応答を保存します。 実稼動デプロイメントの場合：

- **Adobe Commerce オンプレミス**:Adobeでは、フルページ キャッシュに[Varnish](config-varnish.md)をお勧めします。 Varnishは、web サーバーの前でリバースプロキシとして動作します。
- **クラウド インフラストラクチャ上のAdobe Commerce**&#x200B;は、エッジおよびページ全体のキャッシュ レイヤーに[Fastly](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/fastly){target="_blank"}を使用します。 クラウドインフラストラクチャでは、個別に管理されたVarnish サービスは使用されません。

>[!NOTE]
>
>Commerce アプリケーションキャッシュバックエンドを変更しても、VarnishやFastlyは設定されません。 フルページのHTTP キャッシュは、ローレベルのアプリケーションキャッシュとは別に設定および管理されます。

### L2 キャッシュ

L2 （2 レベル）のキャッシュでは、各Commerce web ノードにローカルキャッシュが追加されますが、共有リモートキャッシュストレージは保持されます。 頻繁にアクセスされるデータはローカルで提供できるため、マルチノード展開ではリモートキャッシュとの通信が軽減されます。

L2の設定とサポートされている実装は、Commerceのバージョンとデプロイメントタイプによって異なります。 詳しくは、[L2 キャッシュ設定](level-two-cache.md)を参照してください。

### 静的なコンテンツキャッシュ

Commerceでは、デプロイメントバージョンをURLに追加することで、CSS、JavaScript、画像などの静的リソースのブラウザーキャッシュを改善できます。 コンテンツが変更されると、URLが変更され、ブラウザーは古いキャッシュされたコピーを使用する代わりに新しいリソースをリクエストします。

## デプロイメント固有の設定

次の設定タスクは、デプロイメントタイプによって異なります。

| タスク | オンプレミス | クラウド基盤 |
| --- | --- | --- |
| アプリケーションキャッシュバックエンド | [&#x200B; キャッシュバックエンドオプションとストレージ参照](cache-options.md) | [ValkeyとRedis サービス設定のベストプラクティス &#x200B;](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md) |
| HTTP フルページキャッシュ | [Varnish](config-varnish.md)の設定 | [Fastly サービスの概要](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/fastly) |

次のタスクは、すべてのデプロイメントタイプに適用されます。

- **キャッシュタイプとフロントエンドの設定** [&#x200B; キャッシュフロントエンドとキャッシュの種類をキャッシュフロントエンドに関連付けるようにキャッシュフロントエンドとタイプ &#x200B;](cache-types.md)を設定します。
- **L2 キャッシュの設定**—[L2 キャッシュの設定](level-two-cache.md)。
- **静的コンテンツのブラウザーキャッシュ無効化を設定**—[静的コンテンツ署名とブラウザーキャッシュ無効化](static-content-signing.md)。
