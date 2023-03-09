---
title: Redis サービス設定のベストプラクティス
description: Adobe Commerce用の拡張 Redis キャッシュ実装を使用して、キャッシュのパフォーマンスを向上させる方法を説明します。
role: Developer, Admin
feature-set: Commerce
feature: Best Practices
source-git-commit: e7888688803d86ec342b156da77adc663475fe20
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---


# Redis サービス設定のベストプラクティス

- Adobe Commerceからの各要求に対して実行される Redis クエリの数を最小限に抑えるために、次の最適化を含む、拡張された Redis キャッシュ実装を使用します。
   - Redis とAdobe Commerceの間のネットワークデータ転送のサイズを小さくします
   - 読み込む必要のある項目を自動的に決定するアダプタの機能を改善し、CPU サイクルの消費を削減します。
   - Redis の書き込み操作の競合状態を軽減
- Redis のキャッシュを Redis のセッションから分離する
- Redis キャッシュを圧縮し、次を使用します。 `gzip` 性能を高める

## 拡張 Redis キャッシュの実装

拡張された Redis キャッシュ実装を使用するように設定を更新します `\Magento\Framework\Cache\Backend\Redis`.

### クラウドデプロイメントの設定

拡張された Redis キャッシュを設定するには、 `REDIS_BACKEND` デプロイメント変数を `.magento.env.yaml` 設定ファイル。

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\Redis'
```

詳しくは、 [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) 変数の説明 _Commerce on Cloud Infrastructure ガイド_.

>[!NOTE]
>
> 次を確認します。 `ece-tools` コマンドラインからローカル環境にインストールされたバージョン `composer show magento/ece-tools` コマンドを使用します。 必要に応じて、 [最新バージョンに更新](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html).

>[!WARNING]
>
>実行 _not_ クラウドインフラストラクチャプロジェクトの Redis スレーブ接続を [スケールアーキテクチャ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html). これにより、Redis 接続エラーが発生します。 詳しくは、 [レディスの構成指導](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) 内 _クラウドインフラストラクチャ上のコマース_ ガイド。

### オンプレミスデプロイメントの設定

Adobe Commerceのオンプレミスデプロイメントの場合は、 `bin/magento:setup` コマンド 手順については、 [デフォルトのキャッシュに Redis を使用](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching).

## キャッシュとセッションインスタンスを分離

Redis のキャッシュを Redis のセッションから分離すると、キャッシュとセッションを個別に管理して、キャッシュの問題がセッションに影響を与えないようにできます。

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

1. 送信 [Adobe Commerceサポートチケット](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) :Pro 実稼動環境とステージング環境で Redis サービス設定を変更する場合。 更新された `.magento/services.yaml` および `.magento.app.yaml` 設定ファイル。

1. 新しいインスタンスが実行中であることを確認し、ポート番号をメモします。

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. ポート番号を `.magento.env.yaml` 設定ファイル。

   >[!NOTE]
   >`disable_locking` は、次のように設定する必要があります `1`.

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

1. からセッションを削除 [デフォルトデータベース](../../../configuration/cache/redis-pg-cache.md) (`db 0`) を Redis キャッシュインスタンスに追加します。

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

## キャッシュ圧縮

キャッシュ圧縮を使用しますが、クライアント側のパフォーマンスにトレードオフがあることに注意してください。 予備の CPU がある場合は、有効にします。 詳しくは、 [セッションストレージに Redis を使用](../../../configuration/cache/redis-session.md).

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
