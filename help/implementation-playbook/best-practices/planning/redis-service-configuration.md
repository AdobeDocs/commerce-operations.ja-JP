---
title: Redis サービス設定のベストプラクティス
description: Adobe Commerceの拡張 Redis キャッシュ実装を使用して、キャッシュパフォーマンスを向上させる方法を説明します。
role: Developer, Admin
feature: Best Practices, Cache
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 0%

---

# Redis サービス設定のベストプラクティス

- Redis L2 キャッシュの設定
- Redis スレーブ接続を有効にする
- キーをプリロード
- 古いキャッシュを有効にする
- Redis キャッシュと Redis セッションを分離します。
- Redis キャッシュを圧縮し、高い圧縮に `gzip` を使用します

## Redis L2 キャッシュの設定

`.magento.env.yaml` 設定ファイルの `REDIS_BACKEND` デプロイメント変数を設定して、Redis L2 キャッシュを設定します。

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

クラウドインフラストラクチャー上の環境設定については、_クラウドインフラストラクチャー上のCommerceガイド_ の [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) を参照してください。

オンプレミスのインストールの場合は、[ 設定ガイド ](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) の _Redis ページ キャッシュの設定_ を参照してください。

>[!NOTE]
>
>`ece-tools` パッケージの最新バージョンを使用していることを確認します。 そうでない場合は [ 最新バージョンにアップグレード ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html) します。 `composer show magento/ece-tools` CLI コマンドを使用すると、ローカル環境にインストールされているバージョンを確認できます。


### L2 キャッシュメモリサイズ設定（Adobe Commerce Cloud）

L2 キャッシュは、ストレージ メカニズムとして [ 一時ファイル システム ](https://en.wikipedia.org/wiki/Tmpfs) を使用します。 特殊なキー値データベースシステムと比較して、一時ファイルシステムには、メモリの使用を制御するためのキー削除ポリシーがありません。

メモリ使用量の制御がないと、古くなったキャッシュが蓄積され、L2 キャッシュのメモリ使用量が時間の経過とともに増加する可能性があります。

L2 キャッシュ実装のメモリ不足を避けるために、Adobe Commerceは、特定のしきい値に達するとストレージをクリアします。 デフォルトのしきい値は 95% です。

キャッシュストレージのプロジェクト要件に基づいて、L2 キャッシュメモリの最大使用量を調整することが重要です。 次のいずれかの方法を使用して、メモリキャッシュサイズを設定します。

- `/dev/shm` マウントのサイズ変更をリクエストするサポートチケットを作成します。
- ストレージの最大充填率に上限を設定するようにアプリケーションレベルで `cleanup_percentage` プロパティを調整します。 残りの空きメモリは、他のサービスで使用できます。
設定は、キャッシュ設定グループ `cache/frontend/default/backend_options/cleanup_percentage` の下にあるデプロイメント設定で調整できます。

>[!NOTE]
>
>`cleanup_percentage` の設定可能なオプションは、Adobe Commerce 2.4.4 で導入されました。

次のコードは、`.magento.env.yaml` ファイルの設定例を示しています。

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            cleanup_percentage: 90
```

キャッシュ要件は、プロジェクト設定とカスタムサードパーティコードによって異なる場合があります。 L2 キャッシュ メモリ サイズのスコープにより、しきい値のヒット数が多くなりすぎることなく、L2 キャッシュを動作させることができます。
ストレージのクリアが頻繁に行われるのを避けるために、L2 キャッシュメモリの使用状況が、しきい値を下回る一定のレベルで安定していることが理想的です。

以下の CLI コマンドを使用してクラスターの各ノードでの L2 キャッシュストレージメモリの使用状況を確認し、`/dev/shm` 行を探すことができます。
使用方法はノードによって異なる場合がありますが、同じ値に収束する必要があります。

```bash
df -h
```

## Redis スレーブ接続を有効にする

`.magento.env.yaml` 設定ファイルの Redis スレーブ接続を有効にして、1 つのノードだけが読み取り/書き込みトラフィックを処理し、他のノードが読み取り専用トラフィックを処理できるようにします。

```yaml
stage:
  deploy:
    REDIS_USE_SLAVE_CONNECTION: true
```

[2}Cloud Infrastructure ガイドのCommerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection)REDIS_USE_SLAVE_CONNECTION} を参照してください __

Adobe Commerce オンプレミスのインストールの場合は、`bin/magento:setup` コマンドを使用して新しい Redis キャッシュ実装を設定します。 _設定ガイド_ の [ デフォルトキャッシュに Redis を使用 ](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) を参照してください。

>[!WARNING]
>
>[ 拡張/分割アーキテクチャ _を使用して、クラウドインフラストラクチャプロジェクト用の Redis スレーブ接続を設定する_ しないでください ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html)。 これにより、Redis 接続エラーが発生します。 クラウドインフラストラクチャー上の _Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) ガイドの [Redis 設定ガイダンス_ を参照してください。

## キーをプリロード

ページ間でデータを再利用するには、プリロードのキーを `.magento.env.yaml` 設定ファイルにリストします。

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '061_'                       # Prefix for keys to be preloaded
          backend_options:
            preload_keys:                         # List the keys to be preloaded
              - '061_EAV_ENTITY_TYPES:hash'
              - '061_GLOBAL_PLUGIN_LIST:hash'
              - '061_DB_IS_UP_TO_DATE:hash'
              - '061_SYSTEM_DEFAULT:hash'
```

オンプレミスのインストールについては、[ 設定ガイド ](../../../configuration/cache/redis-pg-cache.md#redis-preload-feature) の _Redis プリロード機能_ を参照してください。

## 古いキャッシュを有効にする

新しいキャッシュを並行して生成しながら古いキャッシュを使用することで、特に多数のブロックとキャッシュキーを処理する場合に、ロックの待機時間を短縮し、パフォーマンスを向上させます。 `.magento.env.yaml` 設定ファイルで、古いキャッシュを有効にして、キャッシュタイプを定義します。

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      default:
        backend_options:
          use_stale_cache: false
      stale_cache_enabled:
        backend_options:
          use_stale_cache: true
      type:
        default:
          frontend: "default"
        layout:
          frontend: "stale_cache_enabled"
        block_html:
          frontend: "stale_cache_enabled"
        reflection:
          frontend: "stale_cache_enabled"
        config_integration:
          frontend: "stale_cache_enabled"
        config_integration_api:
          frontend: "stale_cache_enabled"
        full_page:
          frontend: "stale_cache_enabled"
        translate:
          frontend: "stale_cache_enabled"
```

オンプレミスのインストールを構成する方法については、[ 構成ガイド ](../../../configuration/cache/level-two-cache.md#stale-cache-options) の _古いキャッシュ オプション_ を参照してください。

## Redis のキャッシュとセッションのインスタンスを分離する

Redis キャッシュと Redis セッションを分離すると、キャッシュとセッションを個別に管理できます。 キャッシュの問題がセッションに影響を与え、売上高に影響を与える可能性を防ぐことができます。 各 Redis インスタンスは独自のコアで実行されるため、パフォーマンスが向上します。

1. `.magento/services.yaml` 設定ファイルを更新します。

   ```yaml
   mysql:
       type: mysql:10.4
       disk: 35000
   
   redis:
      type: redis:6.0
   
   redis-session:              # This is for the new Redis instance
      type: redis:6.0
   
   search:
      type: elasticsearch:7.9
      disk: 5000
   
   rabbitmq:
      type: rabbitmq:3.8
      disk: 2048
   ```

1. `.magento.app.yaml` 設定ファイルを更新します。

   ```yaml
   relationships:
       database: "mysql:mysql"
       redis: "redis:redis"
       redis-session: "redis-session:redis"   # Relationship of the new Redis instance
       search: "search:elasticsearch"
       rabbitmq: "rabbitmq:rabbitmq"
   ```

1. [Adobe Commerce サポートチケット ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) を送信して、実稼動環境とステージング環境のセッション専用の新しい Redis インスタンスのプロビジョニングをリクエストします。 更新された `.magento/services.yaml` と `.magento.app.yaml` の設定ファイルを含めます。 ダウンタイムは発生しませんが、新しいサービスをアクティブ化するにはデプロイメントが必要です。

1. 新しいインスタンスが実行中であることを確認し、ポート番号をメモします。

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. `.magento.env.yaml` 設定ファイルにポート番号を追加します。

   >[!NOTE]
   >`disable_locking` は `1` に設定する必要があります。
   >   

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis:
       port: 6374       # check the port in $MAGENTO_CLOUD_RELATIONSHIPS
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. Redis キャッシュインスタンスの [ デフォルトデータベース ](../../../configuration/cache/redis-pg-cache.md) （`db 0`）からセッションを削除します。

   ```bash
   redis-cli -h 127.0.0.1 -p 6374 -n 0 FLUSHDB
   ```

デプロイメント中、[ ビルドおよびデプロイログ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html#build-and-deploy-logs) に次の行が表示されます。

```
W:   - Downloading colinmollenhour/credis (1.11.1)
W:   - Downloading colinmollenhour/php-redis-session-abstract (v1.4.5)
...
W:   - Installing colinmollenhour/credis (1.11.1): Extracting archive
W:   - Installing colinmollenhour/php-redis-session-abstract (v1.4.5): Extracting archive
...
[2022-08-17 01:13:40] INFO: Version of service 'redis' is 6.0
[2022-08-17 01:13:40] INFO: Version of service 'redis-session' is 6.0
[2022-08-17 01:13:40] INFO: redis-session will be used for session if it was not override by SESSION_CONFIGURATION
```

## キャッシュ圧縮

6 GB を超える Redis `maxmemory` を使用している場合は、キャッシュ圧縮を使用して、キーが消費する領域を減らすことができます。 クライアントサイドのパフォーマンスにはトレードオフがあることに注意してください。 予備の CPU がある場合は、有効にします。 _設定ガイド_ の [ セッションストレージに Redis を使用 ](../../../configuration/cache/redis-session.md) を参照してください。

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true;
      frontend:
        default:
          backend_options:
            compress_data: 4              # 0-9
            compress_tags: 4              # 0-9
            compress_threshold: 20480     # don't compress files smaller than this value
            compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)
```

## 追加情報

- [Redis ページキャッシュ](../../../configuration/cache/redis-pg-cache.md)
- [セッションストレージに Redis を使用](../../../configuration/cache/redis-session.md)
