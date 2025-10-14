---
title: Redis サービス設定のベストプラクティス
description: Adobe Commerceの拡張 Redis キャッシュ実装を使用して、キャッシュパフォーマンスを向上させる方法を説明します。
role: Developer, Admin
feature: Best Practices, Cache
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
source-git-commit: 9dc17a7ec44d9c146fdc2ec48e128beacc298299
workflow-type: tm+mt
source-wordcount: '1142'
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

`REDIS_BACKEND` 設定ファイルの `.magento.env.yaml` デプロイメント変数を設定して、Redis L2 キャッシュを設定します。

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

クラウドインフラストラクチャー上の環境設定については、[`REDIS_BACKEND` クラウドインフラストラクチャー上のCommerceガイド &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=ja#redis_backend) の __ を参照してください。

オンプレミスのインストールの場合は、[&#x200B; 設定ガイド &#x200B;](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) の _Redis ページ キャッシュの設定_ を参照してください。

>[!NOTE]
>
>`ece-tools` パッケージの最新バージョンを使用していることを確認します。 そうでない場合は [&#x200B; 最新バージョンにアップグレード &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html?lang=ja) します。 `composer show magento/ece-tools` CLI コマンドを使用すると、ローカル環境にインストールされているバージョンを確認できます。


### L2 キャッシュメモリのサイズ設定（Adobe Commerce Cloud）

L2 キャッシュは、ストレージ メカニズムとして [&#x200B; 一時ファイル システム &#x200B;](https://en.wikipedia.org/wiki/Tmpfs) を使用します。 特殊なキー値データベースシステムと比較して、一時ファイルシステムには、メモリの使用を制御するためのキー削除ポリシーがありません。

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

[2&rbrace;Cloud Infrastructure ガイドのCommerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=ja#redis_use_slave_connection)REDIS_USE_SLAVE_CONNECTION&rbrace; を参照してください __

Adobe Commerce オンプレミスのインストールの場合は、`bin/magento:setup` コマンドを使用して新しい Redis キャッシュ実装を設定します。 [&#x200B; 設定ガイド &#x200B;](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) の _デフォルトキャッシュに Redis を使用_ を参照してください。

>[!WARNING]
>
>_拡張/分割アーキテクチャ_ を使用して、クラウドインフラストラクチャプロジェクト用の Redis スレーブ接続を設定する [&#x200B; しないでください &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html?lang=ja)。 これにより、Redis 接続エラーが発生します。 クラウドインフラストラクチャー上の [Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=ja#redis_use_slave_connection) ガイドの _Redis 設定ガイダンス_ を参照してください。

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

オンプレミスのインストールについては、[&#x200B; 設定ガイド &#x200B;](../../../configuration/cache/redis-pg-cache.md#redis-preload-feature) の _Redis プリロード機能_ を参照してください。

## 古いキャッシュを有効にする

新しいキャッシュを並行して生成しながら古いキャッシュを使用することで、特に多数のブロックとキャッシュキーを処理する場合に、ロックの待機時間を短縮し、パフォーマンスを向上させます。 古いキャッシュを有効にして、`config.php` 設定ファイルでキャッシュタイプを定義する（クラウドのみ）:

```php
'cache' => [
        'frontend' => [
            'stale_cache_enabled' => [
                'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
                'backend_options' => [
                    'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                    'remote_backend_options' => [
                        'persistent' => 0,
                        'server' => 'localhost',
                        'database' => '4',
                        'port' => '6370',
                        'password' => ''
                    ],
                    'local_backend' => 'Cm_Cache_Backend_File',
                    'local_backend_options' => [
                        'cache_dir' => '/dev/shm/'
                    ],
                    'use_stale_cache' => true,
                ],
                'frontend_options' => [
                    'write_control' => false,
                ],
            ]
        ],
        'type' => [
            'default' => ['frontend' => 'default'],
            'layout' => ['frontend' => 'stale_cache_enabled'],
            'block_html' => ['frontend' => 'stale_cache_enabled'],
            'reflection' => ['frontend' => 'stale_cache_enabled'],
            'config_integration' => ['frontend' => 'stale_cache_enabled'],
            'config_integration_api' => ['frontend' => 'stale_cache_enabled'],
            'full_page' => ['frontend' => 'stale_cache_enabled'],
            'translate' => ['frontend' => 'stale_cache_enabled']
        ],
    ]
```

>[!NOTE]
>
>前の例では、`full_page` キャッシュは [Fastly](https://experienceleague.adobe.com/ja/docs/commerce-cloud-service/user-guide/cdn/fastly) を使用しているので、クラウドインフラストラクチャプロジェクトのAdobe Commerceには関係ありません。

オンプレミスのインストールを構成する方法については、[&#x200B; 構成ガイド &#x200B;](../../../configuration/cache/level-two-cache.md#stale-cache-options) の _古いキャッシュ オプション_ を参照してください。

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

1. [Adobe Commerce サポートチケット &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=ja#submit-ticket) を送信して、実稼動環境とステージング環境のセッション専用の新しい Redis インスタンスのプロビジョニングをリクエストします。 更新された `.magento/services.yaml` と `.magento.app.yaml` の設定ファイルを含めます。 ダウンタイムは発生しませんが、新しいサービスをアクティブ化するにはデプロイメントが必要です。

1. 新しいインスタンスが実行中であることを確認し、ポート番号をメモします。

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. `.magento.env.yaml` 設定ファイルにポート番号を追加します。

   >[!IMPORTANT]
   >
   >`ece-tools` redis セッションサービス定義から自動的に検出で `MAGENTO_CLOUD_RELATIONSHIPS` ない場合にのみ、redis セッションポートを設定します。

   >[!NOTE]
   >
   >`disable_locking` は `1` に設定する必要があります。

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis:
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. Redis キャッシュインスタンスの [&#x200B; デフォルトデータベース &#x200B;](../../../configuration/cache/redis-pg-cache.md) （`db 0`）からセッションを削除します。

   ```bash
   redis-cli -h 127.0.0.1 -p 6374 -n 0 FLUSHDB
   ```

デプロイメント中、[&#x200B; ビルドおよびデプロイログ &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html?lang=ja#build-and-deploy-logs) に次の行が表示されます。

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

6 GB を超える Redis `maxmemory` を使用している場合は、キャッシュ圧縮を使用して、キーが消費する領域を減らすことができます。 クライアントサイドのパフォーマンスにはトレードオフがあることに注意してください。 予備の CPU がある場合は、有効にします。 [&#x200B; 設定ガイド &#x200B;](../../../configuration/cache/redis-session.md) の _セッションストレージに Redis を使用_ を参照してください。

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

## Redis 非同期解放の有効化（lazyfree）

クラウドインフラストラクチャー上のAdobe Commerceで `lazyfree` を有効にするには、[Adobe Commerce サポートチケットを送信し &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=ja#submit-ticket) 次の Redis 設定が環境に適用されるようにリクエストします。

```
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
lazyfree-lazy-user-del yes
```

lazyfree を有効にすると、Redis はメモリの再利用をバックグラウンド スレッドにオフロードし、削除、サーバーによる削除、ユーザーの削除、レプリカ データセットのフラッシュを行います。 これにより、メインスレッドのブロックが減り、リクエストの待ち時間が短縮されます。

>[!NOTE]
>
>`lazyfree-lazy-user-del yes` オプションを指定すると、`DEL` コマンドは `UNLINK` のように動作します。これにより、キーのリンクが直ちに解除され、メモリが非同期で解放されます。

>[!WARNING]
>
>バックグラウンドで解放が行われるため、削除/期限切れ/削除されたキーが使用するメモリは、バックグラウンドスレッドが作業を完了するまで割り当てられたままです。 お使いの Redis が既にメモリ負荷が高い場合は、慎重にテストし、最初にメモリ負荷を下げることを検討してください（例えば、特定のケースではブロック キャッシュを無効にし、上記のようにキャッシュとセッションの Redis インスタンスを分離します）。

## Redis マルチスレッド I/O を有効にする

クラウドインフラストラクチャでAdobe Commerceの Redis I/O スレッドを有効にするには、[Adobe Commerce サポートチケットを送信し &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=ja#submit-ticket) 以下の設定をリクエストします。 これにより、ソケットの読み取り/書き込みとコマンド解析をメインスレッドからオフロードすることで、スループットが向上しますが、CPUの使用率は高くなります。 負荷の下で検証し、ホストを監視します。

```
io-threads-do-reads yes
io-threads 8 # choose a value lower than the number of CPU cores (check with nproc), then tune under load
```

>[!NOTE]
>
>I/O スレッドは、クライアント I/O と解析のみを並列化します。 Redis コマンドの実行はシングルスレッドのままです。

>[!WARNING]
>
>I/O スレッドを有効にすると、CPUの使用量が増える可能性がありますが、すべてのワークロードにメリットがあるわけではありません。 保守的な価値とベンチマークから始めます。 待ち時間が増加したり、CPUが飽和状態になった場合は、I/O スレッドの読み取りを減らすか、無効 `io-threads` します。

## Redis クライアントのタイムアウトと再試行の回数を増やす

`.magento.env.yaml` でバックエンドオプションを調整して、キャッシュクライアントの許容値を一時的な飽和値に引き上げます。

```yaml
stage:
  deploy:
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            read_timeout: 10
            connect_retries: 5
```

これらの設定により、Redis のクライアント許容値が増加し、返信待ちウィンドウが拡張され、接続設定が再試行されます。 これにより、短いスパイク時の断続的な `cannot connect to localhost:6370` ールと読み取りタイムアウトのエラーを減らすことができます。

>[!NOTE]
>
>これらは、永続的な過負荷の修正ではありません。

## 追加情報

- [Redis ページキャッシュ](../../../configuration/cache/redis-pg-cache.md)
- [セッションストレージに Redis を使用](../../../configuration/cache/redis-session.md)
