---
title: Redis サービス設定のベストプラクティス
description: Adobe Commerce用の拡張 Redis キャッシュ実装を使用して、キャッシュのパフォーマンスを向上させる方法を説明します。
role: Developer, Admin
feature: Best Practices, Cache
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
source-git-commit: 156e6412b9f94b74bad040b698f466808b0360e3
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 0%

---

# Redis サービス設定のベストプラクティス

- Redis L2 キャッシュの設定
- Redis スレーブ接続を有効にする
- キーをプリロード
- 古いキャッシュを有効にする
- Redis のキャッシュを Redis のセッションから分離する
- Redis キャッシュを圧縮し、次を使用します。 `gzip` より高い圧縮のために

## Redis L2 キャッシュの設定

Redis L2 キャッシュを設定するには、 `REDIS_BACKEND` デプロイメント変数を `.magento.env.yaml` 設定ファイル。

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

クラウドインフラストラクチャの環境設定については、 [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) （内） _Commerce on Cloud Infrastructure ガイド_.

オンプレミスでのインストールについては、 [Redis ページキャッシュの設定](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) （内） _設定ガイド_.

>[!NOTE]
>
>最新バージョンの `ece-tools` パッケージ。 そうでない場合、 [最新バージョンにアップグレード](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html). ローカル環境にインストールされているバージョンを確認するには、 `composer show magento/ece-tools` CLI コマンド。

## Redis スレーブ接続を有効にする

で Redis スレーブ接続を有効にする `.magento.env.yaml` 読み取り/書き込みトラフィックを処理するノードを 1 つにし、読み取り専用トラフィックを処理するノードを他のノードに許可する設定ファイル。

```yaml
stage:
  deploy:
    REDIS_USE_SLAVE_CONNECTION: true
```

詳しくは、 [REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) （内） _Commerce on Cloud Infrastructure ガイド_.

Adobe Commerceのオンプレミスでのインストールの場合、 `bin/magento:setup` コマンド。 詳しくは、 [デフォルトのキャッシュに Redis を使用](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) （内） _設定ガイド_.

>[!WARNING]
>
>実行 _not_ を使用してクラウドインフラストラクチャプロジェクトに Redis スレーブ接続を設定する [拡張/分割アーキテクチャ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html). これにより、Redis 接続エラーが発生します。 詳しくは、 [Redis 設定ガイダンス](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) （内） _クラウドインフラストラクチャ上のコマース_ ガイド。

## キーをプリロード

ページ間でデータを再利用するには、 `.magento.env.yaml` 設定ファイル。

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

オンプレミスでのインストールについては、 [Redis のプリロード機能](../../../configuration/cache/redis-pg-cache.md#redis-preload-feature) （内） _設定ガイド_.

## 古いキャッシュを有効にする

新しいキャッシュを並行して生成しながら古いキャッシュを使用することで、ロック待ち時間を短縮し、多数のブロックやキャッシュキーを処理する場合に特にパフォーマンスを向上させます。 古いキャッシュを有効にし、 `.magento.env.yaml` 設定ファイル：

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

オンプレミスでのインストールの設定については、 [古いキャッシュオプション](../../../configuration/cache/level-two-cache.md#stale-cache-options) （内） _設定ガイド_.

## Redis キャッシュとセッションインスタンスを分離

Redis のキャッシュを Redis のセッションから分離すると、キャッシュとセッションを個別に管理できます。 キャッシュの問題がセッションに影響を与えるのを防ぎ、売上高に影響を与える可能性があります。 各 Redis インスタンスは、それぞれのコアで実行され、パフォーマンスが向上します。

1. を更新します。 `.magento/services.yaml` 設定ファイル。

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

1. を更新します。 `.magento.app.yaml` 設定ファイル。

   ```yaml
   relationships:
       database: "mysql:mysql"
       redis: "redis:redis"
       redis-session: "redis-session:redis"   # Relationship of the new Redis instance
       search: "search:elasticsearch"
       rabbitmq: "rabbitmq:rabbitmq"
   ```

1. を送信 [Adobe Commerceサポートチケット](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) 実稼動環境とステージング環境でのセッション専用の新しい Redis インスタンスのプロビジョニングをリクエストする場合。 更新された `.magento/services.yaml` および `.magento.app.yaml` 設定ファイル。 これによってダウンタイムは発生しませんが、新しいサービスを有効化するには、デプロイメントが必要です。

1. 新しいインスタンスが実行中であることを確認し、ポート番号をメモします。

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. にポート番号を追加します。 `.magento.env.yaml` 設定ファイル。

   >[!NOTE]
   >`disable_locking` は、次のように設定する必要があります `1`.
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

1. からセッションを削除 [デフォルトデータベース](../../../configuration/cache/redis-pg-cache.md) (`db 0`) を Redis キャッシュインスタンスに置き換えます。

   ```bash
   redis-cli -h 127.0.0.1 -p 6374 -n 0 FLUSHDB
   ```

配置時に、次の行が [ログの作成とデプロイ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html#build-and-deploy-logs):

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

## キャッシュの圧縮

6 GB を超える Redis を使用している場合 `maxmemory`キャッシュ圧縮を使用すると、キーの消費容量を減らすことができます。 クライアント側のパフォーマンスにトレードオフがあることに注意してください。 予備の CPU がある場合は、有効にします。 詳しくは、 [セッションストレージに Redis を使用](../../../configuration/cache/redis-session.md) （内） _設定ガイド_.

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
