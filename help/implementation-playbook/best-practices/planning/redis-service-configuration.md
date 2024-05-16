---
title: Redis サービス設定のベストプラクティス
description: Adobe Commerceの拡張 Redis キャッシュ実装を使用して、キャッシュパフォーマンスを向上させる方法を説明します。
role: Developer, Admin
feature: Best Practices, Cache
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
source-git-commit: 6772c4fe31cfcd18463b9112f12a2dc285b39324
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
- Redis キャッシュを圧縮して使用 `gzip` 圧縮率を高くするために

## Redis L2 キャッシュの設定

を設定して、Redis L2 キャッシュを設定します。 `REDIS_BACKEND` のデプロイメント変数 `.magento.env.yaml` 設定ファイル。

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

クラウドインフラストラクチャの環境設定については、を参照してください [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) が含まれる _クラウドインフラストラクチャー上のCommerce ガイド_.

オンプレミスでのインストールについては、を参照してください。 [Redis ページキャッシュの設定](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) が含まれる _設定ガイド_.

>[!NOTE]
>
>の最新バージョンを使用していることを確認します `ece-tools` パッケージ。 そうでない場合、 [最新バージョンへのアップグレード](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html). ローカル環境にインストールされているバージョンは、 `composer show magento/ece-tools` CLI コマンド。


### L2 キャッシュメモリサイズ設定（Adobe Commerce Cloud）

L2 キャッシュは [一時ファイルシステム](https://en.wikipedia.org/wiki/Tmpfs) ストレージメカニズムとして使用されます。 特殊なキー値データベースシステムと比較して、一時ファイルシステムには、メモリの使用を制御するためのキー削除ポリシーがありません。

メモリ使用量の制御がないと、古くなったキャッシュが蓄積され、L2 キャッシュのメモリ使用量が時間の経過とともに増加する可能性があります。

L2 キャッシュ実装のメモリ不足を避けるために、Adobe Commerceは、特定のしきい値に達するとストレージをクリアします。 デフォルトのしきい値は 95% です。

キャッシュストレージのプロジェクト要件に基づいて、L2 キャッシュメモリの最大使用量を調整することが重要です。 次のいずれかの方法を使用して、メモリキャッシュサイズを設定します。

- のサイズ変更をリクエストするためのサポートチケットを作成します `/dev/shm` マウント。
- を調整 `cleanup_percentage` ストレージの最大充填率をキャップするアプリケーションレベルのプロパティ。 残りの空きメモリは、他のサービスで使用できます。
設定は、キャッシュ設定グループの下にあるデプロイメント設定で調整できます `cache/frontend/default/backend_options/cleanup_percentage`.

>[!NOTE]
>
>この `cleanup_percentage` 設定可能なオプションは、Adobe Commerce 2.4.4 で導入されました。

次のコードは、での設定例を示しています。 `.magento.env.yaml` ファイル：

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

以下の CLI コマンドを使用して、クラスターの各ノードでの L2 キャッシュストレージメモリの使用状況を確認し、 `/dev/shm` ライン。
使用方法はノードによって異なる場合がありますが、同じ値に収束する必要があります。

```bash
df -h
```

## Redis スレーブ接続を有効にする

で Redis スレーブ接続を有効にする `.magento.env.yaml` 設定ファイル。1 つのノードのみが読み取り/書き込みトラフィックを処理し、他のノードが読み取り専用トラフィックを処理できるようにします。

```yaml
stage:
  deploy:
    REDIS_USE_SLAVE_CONNECTION: true
```

参照： [REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) が含まれる _クラウドインフラストラクチャー上のCommerce ガイド_.

Adobe Commerceのオンプレミスインストールの場合は、を使用して新しい Redis キャッシュ実装を設定します。 `bin/magento:setup` コマンド。 参照： [既定のキャッシュに Redis を使用](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) が含まれる _設定ガイド_.

>[!WARNING]
>
>実行 _ではない_ を使用したクラウドインフラストラクチャプロジェクト用の Redis スレーブ接続の設定 [拡張/分割アーキテクチャ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html). これにより、Redis 接続エラーが発生します。 参照： [Redis 設定ガイダンス](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) が含まれる _クラウドインフラストラクチャー上の Commerce_ ガイド。

## キーをプリロード

ページ間でデータを再利用するには、プリロードするキーを `.magento.env.yaml` 設定ファイル。

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

オンプレミスでのインストールについては、を参照してください。 [Redis プリロード機能](../../../configuration/cache/redis-pg-cache.md#redis-preload-feature) が含まれる _設定ガイド_.

## 古いキャッシュを有効にする

新しいキャッシュを並行して生成しながら古いキャッシュを使用することで、特に多数のブロックとキャッシュキーを処理する場合に、ロックの待機時間を短縮し、パフォーマンスを向上させます。 で古いキャッシュを有効にし、キャッシュタイプを定義する `.magento.env.yaml` 設定ファイル：

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

オンプレミスのインストールの設定については、を参照してください。 [古いキャッシュオプション](../../../configuration/cache/level-two-cache.md#stale-cache-options) が含まれる _設定ガイド_.

## Redis のキャッシュとセッションのインスタンスを分離する

Redis キャッシュと Redis セッションを分離すると、キャッシュとセッションを個別に管理できます。 キャッシュの問題がセッションに影響を与え、売上高に影響を与える可能性を防ぐことができます。 各 Redis インスタンスは独自のコアで実行されるため、パフォーマンスが向上します。

1. を更新 `.magento/services.yaml` 設定ファイル。

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

1. を更新 `.magento.app.yaml` 設定ファイル。

   ```yaml
   relationships:
       database: "mysql:mysql"
       redis: "redis:redis"
       redis-session: "redis-session:redis"   # Relationship of the new Redis instance
       search: "search:elasticsearch"
       rabbitmq: "rabbitmq:rabbitmq"
   ```

1. を送信 [Adobe Commerce サポートチケット](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) 実稼動環境とステージング環境のセッション専用の新しい Redis インスタンスのプロビジョニングをリクエストします。 更新されたを含める `.magento/services.yaml` および `.magento.app.yaml` 設定ファイル。 ダウンタイムは発生しませんが、新しいサービスをアクティブ化するにはデプロイメントが必要です。

1. 新しいインスタンスが実行中であることを確認し、ポート番号をメモします。

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. ポート番号をに追加します。 `.magento.env.yaml` 設定ファイル。

   >[!NOTE]
   >`disable_locking` に設定する必要があります。 `1`.
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

1. からのセッションの削除 [デフォルトデータベース](../../../configuration/cache/redis-pg-cache.md) （`db 0`）に設定する必要があります。

   ```bash
   redis-cli -h 127.0.0.1 -p 6374 -n 0 FLUSHDB
   ```

デプロイ時には、に次の行が表示されます。 [ログのビルドとデプロイ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html#build-and-deploy-logs):

```terminal
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

6 GB を超える Redis を使用している場合 `maxmemory`を使用すると、キャッシュ圧縮を使用して、キーが消費する領域を減らすことができます。 クライアントサイドのパフォーマンスにはトレードオフがあることに注意してください。 予備の CPU がある場合は、有効にします。 参照： [セッションストレージに Redis を使用](../../../configuration/cache/redis-session.md) が含まれる _設定ガイド_.

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
