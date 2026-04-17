---
title: RedisおよびValkey サービス設定のベストプラクティス
description: Adobe Commerce用にRedis サービスとValkey サービスを設定する方法について説明します。 L2 キャッシュ、スレーブ接続、古いキャッシュ、セッションの分離により、キャッシュパフォーマンスを向上させます。
solution: Commerce
role: Developer, Admin
level: Intermediate
feature: Best Practices, Cache
feature-set: Commerce
topic: Performance
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
source-git-commit: 381d58d5fc9844aca88239e8e7ac39151dfc766c
workflow-type: tm+mt
source-wordcount: '1909'
ht-degree: 0%

---


# RedisおよびValkey サービス設定のベストプラクティス

以下の推奨事項を使用して、Adobe Commerceのキャッシュとセッション用にRedisまたはValkeyを設定します。

- L2 キャッシュの設定
- スレーブ接続を有効にする
- キーのプリロード
- 古いキャッシュを有効にする
- キャッシュとセッションの分離
- キャッシュを圧縮
- 設定例

>[!NOTE]
>
>Commerce on Cloud インフラストラクチャ環境の場合は、最新バージョンの`ece-tools` パッケージを使用していることを確認します。 そうでない場合は、[最新バージョン &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html?lang=ja)にアップグレードしてください。 ローカル環境にインストールされているバージョンは、`composer show magento/ece-tools` CLI コマンドを使用して確認できます。

## L2 キャッシュの設定

`REDIS_BACKEND`構成ファイルで`VALKEY_BACKEND`または`.magento.env.yaml`のデプロイメント変数を設定して、L2 キャッシュを構成します。

>[!BEGINTABS]

>[!TAB Redis設定]

Redisの場合は、次を使用します。

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Cloud Infrastructureでの環境設定については、[`REDIS_BACKEND`Cloud Infrastructure Guide](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=ja#redis_backend)の&#x200B;__&#x200B;設定リファレンスを参照してください。Commerce on Cloud Infrastructure Guide

オンプレミスのインストールについては、[設定ガイド &#x200B;](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching)の「_Redis ページキャッシュの設定_」を参照してください。

>[!TAB Valkey設定]

Valkeyの場合は、次を使用します。

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

クラウドインフラストラクチャでの環境設定については、[`VALKEY_BACKEND`Commerce on Cloud Infrastructure ガイド &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_backend)の&#x200B;__&#x200B;設定リファレンスを参照してください。

オンプレミスのインストールについては、[設定ガイド &#x200B;](../../../configuration/cache/config-valkey.md)の&#x200B;_Valkey_&#x200B;の設定を参照してください。

>[!ENDTABS]


### Adobe Commerce CloudのL2 キャッシュメモリサイズ

L2 キャッシュでは、ストレージメカニズムとして[一時ファイルシステム &#x200B;](https://en.wikipedia.org/wiki/Tmpfs) （`/dev/shm`）が使用されます。 特殊なキー値ストアとは異なり、tmpfsにはキーの立ち退きポリシーがないので、メモリの使用量は制限なく増加する可能性があります。 Adobe Commerceでは、使用状況が設定可能なしきい値（デフォルトでは95%）に達すると、自動的にL2 ストレージがクリアされます。 大きな`/dev/shm` マウントを要求するか、クリーンアップしきい値を下げることで、メモリ消費を制御できます。

プロジェクトの要件に基づいて、L2 キャッシュメモリの最大使用量を調整します。 次のいずれかの方法を使用します。

- サポートチケットを作成して、`/dev/shm` マウントサイズを調整します。 この場合、Adobeでは、`/dev/shm` マウントサイズを15 GBに設定することをお勧めします。
- アプリケーションレベルで`cleanup_percentage` プロパティを調整して、他のサービスで利用可能なストレージ使用量と空きメモリを制限します。
キャッシュ構成グループ `cache/frontend/default/backend_options/cleanup_percentage`の配備構成で構成を調整できます。

>[!NOTE]
>
>設定可能な`cleanup_percentage` オプションは、Adobe Commerce 2.4.4で導入されました。

次の例は、`.magento.env.yaml` ファイルの設定コードを示しています。

>[!BEGINTABS]

>[!TAB Redis設定]

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

>[!TAB Valkey設定]

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            cleanup_percentage: 90
```

>[!ENDTABS]

キャッシュの要件は、プロジェクトの設定とカスタムのサードパーティコードによって異なります。 L2 キャッシュメモリのサイズを調整して、頻繁なスレッショルドヒットなしでキャッシュを動作できるようにします。

理想的には、L2 キャッシュメモリの使用は、頻繁なストレージのクリアを避けるために、しきい値を下回って安定します。

次のCLI コマンドを実行し、`/dev/shm`行を確認することで、クラスターの各ノードでのL2 キャッシュストレージメモリの使用状況を確認できます。

```bash
df -h /dev/shm
```

使用状況はノードによって異なりますが、同様の値に収束する必要があります。

## スレーブ接続を有効にする

`.magento.env.yaml` ファイルでスレーブ接続を有効にして、Adobe Commerceがプライマリエンドポイントを書き込みに引き続き使用しながら、読み取りに対してさらに読み取り専用キャッシュ接続を使用できるようにします。 この設定により、プライマリキャッシュサービスの読み取り負荷を軽減し、より効果的に読み取りトラフィックを分散させることができます。

>[!BEGINTABS]

>[!TAB Redis設定]

Redisの場合は、次を使用します。

```yaml
stage:
  deploy:
    REDIS_USE_SLAVE_CONNECTION: true
```

Commerce Cloud インフラストラクチャの環境設定については、[Commerce on Cloud Infrastructure ガイド &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=ja#redis_use_slave_connection)の&#x200B;_REDIS_USE_SLAVE_CONNECTION_&#x200B;を参照してください。

Adobe Commerce オンプレミス インストールの場合、`bin/magento setup` コマンドを使用して新しいRedis キャッシュ実装を設定します。 [設定ガイド &#x200B;](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching)の「_デフォルトのキャッシュにRedisを使用する_」を参照してください。

>[!TAB Valkey設定]

Valkeyの場合は、次を使用します。

```yaml
stage:
  deploy:
    VALKEY_USE_SLAVE_CONNECTION: true
```

Commerce Cloud インフラストラクチャの環境設定については、[Commerce on Cloud Infrastructure ガイド &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=ja#valkey_use_slave_connection)の&#x200B;_VALKEY_USE_SLAVE_CONNECTION_&#x200B;を参照してください。

Adobe Commerce オンプレミス インストールの場合、`bin/magento setup` コマンドを使用して新しいValkey キャッシュ実装を設定します。 [設定ガイド &#x200B;](../../../configuration/cache/config-valkey.md)の「_Valkey_&#x200B;の設定」を参照してください。

>[!ENDTABS]

## キーのプリロード

Magentoは通常、Redis キーまたはValkey キーからキャッシュエントリを一度に1つずつ読み込みます。 プリロード機能を使用すると、Magentoがリクエスト中に最初にアクセスしたときに1つのパイプラインで取得する、頻繁に使用されるキーのリストを提供できます。 Magentoは、そのリクエストの残りの部分について取得した値をPHP メモリに保持します。これにより、RedisまたはValkeyへの繰り返しラウンドトリップが削減され、それらのキーのリクエストブートストラップのパフォーマンスが向上します。

RedisまたはValkeyでアクティブなコマンドを監視することで、頻繁に使用されるキーを特定できます。

>[!BEGINTABS]

>[!TAB Redis プリロード キー設定]

プリロードキーは、`.magento.env.yaml`設定ファイルで設定されます。

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '061_' # Prefix for keys to be preloaded, it can be any random string
          backend_options:
            preload_keys: # List the keys to be preloaded
              - '061_EAV_ENTITY_TYPES:hash' # The key name must start with the id_prefix set above
              - '061_GLOBAL_PLUGIN_LIST:hash'
              - '061_DB_IS_UP_TO_DATE:hash'
              - '061_SYSTEM_DEFAULT:hash'
```

キーを一覧表示するには、次のコマンドを実行します。

```terminal
redis-cli -p 6370 -n 1 MONITOR > /tmp/list.keys
```

10秒後、**[!UICONTROL Ctrl+C]**&#x200B;を押します。 次に、次のコマンドを実行します。

```terminal
cat /tmp/list.keys | grep "HGET" | awk '{print $5}' | sort | uniq -c | sort -nr | head -n 50
```

このログには、プリロードできるキーが一覧表示されます。 キーの内容を確認するには、次のコマンドを実行します。

```terminal
redis-cli -p 6370 -n 1 hgetall "<key_name>"
```

オンプレミスのインストールについては、[設定ガイド &#x200B;](../../../configuration/cache/redis-pg-cache.md#redis-preload-feature)の&#x200B;_Redis プリロード機能_&#x200B;を参照してください。

>[!TAB キーの事前読み込みキーの設定が有効です]

プリロードキーは、`.magento.env.yaml`設定ファイルで設定されます。

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '061_' # Prefix for keys to be preloaded, it can be any random string
          backend_options:
            preload_keys: # List the keys to be preloaded
              - '061_EAV_ENTITY_TYPES:hash' # The key name must start with the id_prefix set above
              - '061_GLOBAL_PLUGIN_LIST:hash'
              - '061_DB_IS_UP_TO_DATE:hash'
              - '061_SYSTEM_DEFAULT:hash'
```

キーを一覧表示するには、次のコマンドを実行します。

```terminal
valkey-cli -p 6370 -n 1 MONITOR > /tmp/list.keys
```

10秒後、**[!UICONTROL Ctrl+C]**&#x200B;を押します。 次に、次のコマンドを実行します。

```terminal
cat /tmp/list.keys | grep "HGET" | awk '{print $5}' | sort | uniq -c | sort -nr | head -n 50
```

このログには、プリロードできるキーが一覧表示されます。 キーの内容を確認するには、次のコマンドを実行します。

```terminal
valkey-cli -p 6370 -n 1 hgetall "<key_name>"
```

オンプレミスのインストールについては、[設定ガイド &#x200B;](../../../configuration/cache/valkey-pg-cache.md#valkey-preload-feature)の&#x200B;_Valkey プリロード機能_&#x200B;を参照してください。

>[!ENDTABS]

## 古いキャッシュを有効にする

古いキャッシュは、`RemoteSynchronizedCache`のL2 キャッシュ機能です。 これを有効にすると、Adobe Commerceは既存のローカルキャッシュ値を`/dev/shm`から提供できますが、別のリクエストでは既に同じエントリが再生成されており、すべての同時リクエストを待つ必要はありません。 これにより、高価なキャッシュエントリの再生中にキャッシュスタンピングとロック競合が減少します。

### 仕組み

`RemoteSynchronizedCache`では、Magentoは各キャッシュエントリの2つのコピー（`/dev/shm`のローカルコピーとRedisまたはValkeyのリモートコピー）を保持します。 リモートコピーが利用できず、そのキーに対する再生ロックが既に存在する場合、同時要求は、新しい値が書き込まれるまで待つのではなく、以前のローカル値を受け取ることができます。

古いキャッシュを有効にするには、`.magento.env.yaml` ファイルで設定します。

>[!BEGINTABS]

>[!TAB Redisの古いキャッシュの設定]

Redisの場合

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            use_stale_cache: true
```

>[!TAB Valkeyの古いキャッシュの設定]

Valkeyの場合：

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            use_stale_cache: true
```

>[!ENDTABS]

>[!NOTE]
>
>`full_page` キャッシュの種類は、[Fastly](https://experienceleague.adobe.com/ja/docs/commerce-cloud-service/user-guide/cdn/fastly)を使用しているため、Cloud インフラストラクチャプロジェクト上のAdobe Commerceとは関係ありません。

オンプレミスのインストールについては、[設定ガイド &#x200B;](../../../configuration/cache/level-two-cache.md#stale-cache-options)の&#x200B;_古いキャッシュオプション_&#x200B;を参照してください。

>[!WARNING]
>
>上記の設定により、`default` キャッシュフロントエンドで古いキャッシュが有効になり、そのフロントエンドを使用するすべてのキャッシュエントリに古いキャッシュ動作が適用されます。 Magento コアキャッシュの種類は、通常、この設定で期待どおりに動作します。 ただし、専用のキャッシュフロントエンドを使用せずに汎用`\Magento\Framework\App\Cache` API （例：`$this->cache->save()`）を介してキャッシュに書き込むカスタムコードまたは拡張機能がプロジェクトに含まれている場合、それらのエントリは再生中に古い値を提供することもできます。
>
>
>これにより、カスタマイズで予期しない動作が発生する場合は、`default` フロントエンドで古いキャッシュを無効のままにし、選択したキャッシュタイプに対してのみ有効にします。これは、一般的に[&#x200B; オンプレミス &#x200B;](../../../configuration/cache/level-two-cache.md#stale-cache-options)で行われるのと同じです。

### キャッシュタイプごとに個別に古いキャッシュを有効にする

`.magento.env.yaml`で専用のキャッシュフロントエンドを定義し、選択したキャッシュタイプをそれにマッピングすることで、選択したキャッシュタイプに対してのみ古いキャッシュを有効にできます。

正しく動作させるには、カスタムフロントエンドを`CACHE_CONFIGURATION.frontend`の下の完全なフロントエンドとして定義する必要があります。 新しいフロントエンド名の`use_stale_cache: true`のみを定義するだけでは不十分です。

**設定例**

>[!BEGINTABS]

>[!TAB Redisの古いキャッシュの設定]

Redisの場合

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # In this frontend, we keep stale cache set to false.
          id_prefix: '001_'
          backend_options:
            use_stale_cache: false

        # Now, create a new frontend called 'stale_cache_enabled'.
        # It must contain the same backend connection settings as the frontend 'default':

        stale_cache_enabled:
          id_prefix: '001_'
          backend: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
          backend_options:
            remote_backend: '\Magento\Framework\Cache\Backend\Redis'
            remote_backend_options:
              server: localhost
              port: 6370 # Use the same port used by the frontend 'default' in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same port used by the frontend 'default' in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: 'Cm_Cache_Backend_File'
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true # stale cache here is enabled

      # Now select which cache types you want to enable (stale_cache_enabled), or disable (default)

      type:
        default:
          frontend: default
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...
```

>[!TAB Valkeyの古いキャッシュの設定]

Valkeyの場合：

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # In this frontend, we keep stale cache set to false.
          id_prefix: '001_'
          backend_options:
            use_stale_cache: false

        # Now, create a new frontend called 'stale_cache_enabled'.
        # It must contain the same backend connection settings as the frontend 'default':
 
        stale_cache_enabled:
          id_prefix: '001_'
          backend: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
          backend_options:
            remote_backend: '\Magento\Framework\Cache\Backend\Redis'
            remote_backend_options:
              server: localhost
              port: 6370 # Use the same port used by the frontend 'default' in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same port used by the frontend 'default' in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: 'Cm_Cache_Backend_File'
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true # stale cache here is enabled

      # Now select which cache types you want to enable (stale_cache_enabled), or disable (default)

      type:
        default:
          frontend: default
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...
```

>[!ENDTABS]

>[!NOTE]
>
>ソースフロントエンドに、圧縮、再試行、プリロードキー、その他の調整値などの追加のバックエンドオプションが設定されている場合は、新しいフロントエンドが同じ動作を維持するように、これらのオプションを`stale_cache_enabled`にコピーします。


## キャッシュインスタンスとセッションインスタンスの分離

キャッシュをセッションから分離すると、キャッシュを個別に管理できます。 キャッシュとセッショントラフィック間の競合を減らし、キャッシュ関連のプレッシャーがセッションに影響を与えるのを防ぎ、各RedisまたはValkey インスタンスを独自のワークロードに合わせてサイズと調整を行うことができます。

セッション用の専用インスタンスをプロビジョニングするには、次の手順に従います。

>[!BEGINTABS]

>[!TAB Redis]

1. `.magento/services.yaml`設定ファイルを更新します。

   ```yaml
   mysql:
     type: mysql:10.4
     disk: 35000
   
   redis:
     type: redis:6.0
   
   redis-session: # This is for the new Redis instance
     type: redis:6.0
   
   search:
     type: elasticsearch:7.9
     disk: 5000
   
   rabbitmq:
     type: rabbitmq:3.8
     disk: 2048
   ```

1. `.magento.app.yaml`設定ファイルを更新します。

   ```yaml
      relationships:
        database: "mysql:mysql"
        redis: "redis:redis"
        redis-session: "redis-session:redis"   # Relationship of the new Redis instance
        search: "search:elasticsearch"
        rabbitmq: "rabbitmq:rabbitmq"
   ```

1. 実稼動環境とステージング環境のセッション専用の新しいRedis インスタンスをリクエストします。

   [Adobe Commerce サポートチケット &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=ja#submit-ticket)を送信します。 更新された`.magento/services.yaml`および`.magento.app.yaml`設定ファイルを含めます。

   このアップデートはダウンタイムを引き起こしませんが、新しいサービスをアクティブ化するにはデプロイメントが必要です。

1. 新しいインスタンスが実行中であることを確認し、ポート番号を書き留めます。

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. ポート番号を`.magento.env.yaml`設定ファイルに追加します。

   >[!IMPORTANT]
   >
   >`ece-tools`が`MAGENTO_CLOUD_RELATIONSHIPS` Redis セッション サービス定義から自動的に検出できない場合にのみ、Redis セッション ポートを設定します。

   >[!NOTE]
   >
   >パフォーマンスを最適化するために`disable_locking`を`1`に設定します。 同時セッションのアクティビティが多いために競合状態が発生するまれに、ロックを有効にするには`0`に設定します。

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

1. Redis キャッシュインスタンスの[&#x200B; デフォルト データベース &#x200B;](../../../configuration/cache/redis-pg-cache.md) （`db 0`）からセッションを削除します。

   ```terminal
   redis-cli -h 127.0.0.1 -p 6370 -n 0 FLUSHDB
   ```

>[!TAB Valkey]

1. `.magento/services.yaml`設定ファイルを更新します。

   ```yaml
   mysql:
     type: mysql:10.4
     disk: 35000
   
   valkey:
     type: valkey:8.0
   
   valkey-session: # This is for the new Valkey instance
     type: valkey:8.0
   
   search:
     type: elasticsearch:7.9
     disk: 5000
   
   rabbitmq:
     type: rabbitmq:3.8
     disk: 2048
   ```

1. `.magento.app.yaml`設定ファイルを更新します。

   ```yaml
   relationships:
     database: "mysql:mysql"
     valkey: "valkey:valkey"
     valkey-session: "valkey-session:valkey"   # Relationship of the new Valkey instance
     search: "search:elasticsearch"
     rabbitmq: "rabbitmq:rabbitmq"
   ```

1. 実稼動環境とステージング環境のセッション専用の新しいValkey インスタンスをリクエストします。

   [Adobe Commerce サポートチケット &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=ja#submit-ticket)を送信します。 更新された`.magento/services.yaml`および`.magento.app.yaml`設定ファイルを含めます。

   このアップデートはダウンタイムを引き起こしませんが、新しいサービスをアクティブ化するにはデプロイメントが必要です。

1. 新しいインスタンスが実行中であることを確認し、ポート番号を書き留めます。

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. ポート番号を`.magento.env.yaml`設定ファイルに追加します。

   >[!IMPORTANT]
   >
   >Valkey セッションポートを設定するのは、`ece-tools`が`MAGENTO_CLOUD_RELATIONSHIPS` Valkey セッションサービス定義から自動的に検出できない場合のみです。

   >[!NOTE]
   >
   >パフォーマンスを最適化するために`disable_locking`を`1`に設定します。 同時セッションのアクティビティが多いために競合状態が発生するまれに、ロックを有効にするには`0`に設定します。

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis: # keep 'redis' even if you are using Valkey.
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. Valkey キャッシュインスタンスの[&#x200B; デフォルト データベース &#x200B;](../../../configuration/cache/redis-pg-cache.md) （`db 0`）からセッションを削除します。

   ```terminal
   valkey-cli -h 127.0.0.1 -p 6370 -n 0 FLUSHDB
   ```

>[!ENDTABS]

## キャッシュ圧縮

6 GBを超えるRedisまたはValkey `maxmemory`を使用する場合は、キャッシュ圧縮を有効にして、キーが消費する領域を削減できます。 この設定は、クライアント側のパフォーマンスを処理してメモリを節約することに注意してください。 CPUのキャパシティが空いている場合は、有効にすることを検討してください。 [設定ガイド &#x200B;](../../../configuration/cache/redis-session.md)の「[&#x200B; セッションストレージにRedisを使用する](../../../configuration/cache/valkey-session.md)」または「_セッションストレージにValkeyを使用する_」を参照してください。

```yaml
stage:
  deploy:
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            compress_data: 4              # 0-9
            compress_tags: 4              # 0-9
            compress_threshold: 20480     # don't compress files smaller than this value
            compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)
```

## 非同期解放を有効にする

クラウドインフラストラクチャ上のAdobe Commerceで`lazyfree`を有効にするには、次のRedisまたはValkey設定を環境に適用することを要求する[Adobe Commerce サポートチケット &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=ja#submit-ticket)を送信します。

```text
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
lazyfree-lazy-user-del yes
```

`lazyfree`が有効になっている場合、RedisまたはValkeyは、メモリの再利用を、削除、有効期限、サーバー主導の削除、ユーザー削除、レプリカデータセットのフラッシュのために、バックグラウンドスレッドにオフロードします。 これにより、メインスレッドのブロックが減り、リクエストの待ち時間が短縮されます。

>[!NOTE]
>
>`lazyfree-lazy-user-del yes` オプションを使用すると、`DEL` コマンドが`UNLINK`のように動作し、キーのリンクがすぐに解除され、メモリが非同期で解放されます。

>[!WARNING]
>
>解放はバックグラウンドで行われるため、削除されたキー、期限切れのキー、または削除されたキーで使用されるメモリは、バックグラウンドスレッドが作業を完了するまで割り当てられたままになります。 RedisまたはValkey インスタンスが既にメモリの負荷が厳しい場合は、慎重にテストし、まずメモリ負荷を軽減することを検討してください。 例えば、前述のように、特定のケースと個別のキャッシュおよびセッション Redis インスタンスのブロックキャッシュを無効にします。

## マルチスレッド I/Oを有効にする

クラウドインフラストラクチャ上のAdobe CommerceでRedis I/O スレッドを有効にするには、以下のI/O スレッド設定をリクエストする[Adobe Commerce サポートチケット &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=ja#submit-ticket)を送信します。 これにより、CPUの使用率を高くしながらも、ソケットの読み取りと書き込みをオフロードし、メインスレッドからコマンド解析を行うことで、スループットを向上させることができます。 負荷の下で検証し、ホストを監視します。

>[!BEGINTABS]

>[!TAB RedisのI/O スレッドの設定]

Redisの場合

```text
io-threads-do-reads yes
io-threads 8 # Choose a value lower than the number of CPU cores (check with nproc), and then tune under load.
```

>[!TAB ValkeyのI/O スレッドを設定]

Valkeyの場合：

```text
io-threads-do-reads yes
io-threads 8 # choose a value lower than the number of CPU cores (check with nproc), then tune under load
events-per-io-thread 2
```

>[!ENDTABS]


>[!NOTE]
>
>I/O スレッドは、クライアント I/Oと解析のみを並列化します。 Redis コマンドの実行はシングルスレッドのままです。

>[!WARNING]
>
>I/O スレッドを有効にすると、CPUの使用量が増加する可能性があり、すべてのワークロードにメリットがあるわけではありません。 まず、保守的な値とベンチマークを設定します。 待ち時間が長くなったり、CPUが飽和状態になったりした場合は、`io-threads`を減らすか、I/O スレッドの読み取りを無効にします。


## クライアントのタイムアウトと再試行の増加

`.magento.env.yaml`のバックエンドオプションを調整することで、RedisまたはValkey キャッシュクライアントの許容値を飽和期間の短い期間に増やします。

```yaml
stage:
  deploy:
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            connect_retries: 3 # Number of connection retries
            remote_backend_options:
              read_timeout: 10 # Timeout
```

これらの設定により、接続の設定を再試行し、RedisまたはValkeyからの応答により多くの時間をかけることで、短いスパイク中の断続的な接続と読み取りタイムアウトエラーを減らすことができます。

>[!NOTE]
>
>これらの設定は、一時的な過負荷の解消には役立ちますが、永続的な過負荷を修正することはありません。

## 設定例

RedisまたはValkey サービス設定の出発点として、次の例を使用します。


### ベストプラクティスの推奨事項をすべて適用

>[!BEGINTABS]

>[!TAB Redis]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
    REDIS_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '001_' # Any prefix is fine, but keep it consistent.
          backend_options:
            use_stale_cache: true             # Enables stale cache feature for all cache types
            connect_retries: 3                # Number of connection retries
            preload_keys:                     # Preload keys at backend_options level (official Adobe placement)
              - '001_EAV_ENTITY_TYPES:hash'   # Bootstrap: entity types
              - '001_GLOBAL_PLUGIN_LIST:hash' # Bootstrap: DI plugin list
              - '001_DB_IS_UP_TO_DATE:hash'   # Bootstrap: schema version
              - '001_SYSTEM_DEFAULT:hash'     # Config: system defaults
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1        # Required for split architecture
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4              # 0-9
            # compress_tags: 4              # 0-9
            # compress_threshold: 20480     # don't compress files smaller than this value
            # compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)

    SESSION_CONFIGURATION:
      _merge: true
      redis:

        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.

        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!TAB Valkey設定の例]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    VALKEY_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
    VALKEY_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '001_' # any prefix is fine, but keep it consistent.
          backend_options:
            use_stale_cache: true             # Enables stale cache feature for all cache types
            connect_retries: 3                # Number of connection retries
            preload_keys:                     # Preload keys at backend_options level (official Adobe placement)
              - '001_EAV_ENTITY_TYPES:hash'   # Bootstrap: entity types
              - '001_GLOBAL_PLUGIN_LIST:hash' # Bootstrap: DI plugin list
              - '001_DB_IS_UP_TO_DATE:hash'   # Bootstrap: schema version
              - '001_SYSTEM_DEFAULT:hash'     # Config: system defaults
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1        # Required for split architecture
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4              # 0-9
            # compress_tags: 4              # 0-9
            # compress_threshold: 20480     # don't compress files smaller than this value
            # compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)

    SESSION_CONFIGURATION:
      _merge: true
      redis:
        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.
        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!ENDTABS]

### すべてのベストプラクティスの推奨事項を適用し、古いキャッシュをキャッシュタイプごとに分離します

>[!BEGINTABS]

>[!TAB Redis]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
    REDIS_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # Keep stale cache disabled on the broad default frontend.
          id_prefix: '001_' # Keep this prefix consistent with the frontend configuration generated in env.php
          backend_options:
            use_stale_cache: false # stale cache false here
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

        stale_cache_enabled: # New frontend with stale cache enabled only for selected cache types.
          id_prefix: '001_' # Use the same id_prefix used by the source frontend in env.php
          backend: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
          backend_options:
            remote_backend: \Magento\Framework\Cache\Backend\Redis
            remote_backend_options:
              server: localhost
              port: 6370   # Use the same port used by the source frontend in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same slave connection/read port used by the source frontend in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: Cm_Cache_Backend_File
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

      type:
        default:
          frontend: default # Keeps stale cache disabled on the broad default frontend, including generic cache writes that use \Magento\Framework\App\Cache, such as $this->cache->save().
        block_html:
          frontend: stale_cache_enabled # This is often one of the cache types that benefits the most from stale cache, because it is heavily used and can contribute significantly to lock contention during regeneration. In most cases, it can remain enabled. Exclude it only if the project has customization-specific issues caused by stale block output.
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...

    SESSION_CONFIGURATION:
      _merge: true
      redis:
        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.
        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!TAB Valkey]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    VALKEY_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
    VALKEY_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # Keep stale cache disabled on the broad default frontend.
          id_prefix: '001_' # Keep this prefix consistent with the frontend configuration generated in env.php
          backend_options:
            use_stale_cache: false # stale cache false here
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

        stale_cache_enabled: # New frontend with stale cache enabled only for selected cache types.
          id_prefix: '001_' # Use the same id_prefix used by the source frontend in env.php
          backend: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
          backend_options:
            remote_backend: \Magento\Framework\Cache\Backend\Redis
            remote_backend_options:
              server: localhost
              port: 6370   # Use the same port used by the source frontend in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same slave connection/read port used by the source frontend in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: Cm_Cache_Backend_File
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

      type:
        default:
          frontend: default # Keeps stale cache disabled on the broad default frontend, including generic cache writes that use \Magento\Framework\App\Cache, such as $this->cache->save().
        block_html:
          frontend: stale_cache_enabled # This is often one of the cache types that benefits the most from stale cache, because it is heavily used and can contribute significantly to lock contention during regeneration. In most cases, it can remain enabled. Exclude it only if the project has customization-specific issues caused by stale block output.
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...

    SESSION_CONFIGURATION:
      _merge: true
      redis: # keep 'redis' even if you are using Valkey.
        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.
        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!ENDTABS]

## 追加情報

次の関連トピックを参照してください。

- [Redis ページキャッシュ](../../../configuration/cache/redis-pg-cache.md)
- [セッション ストレージにRedisを使用](../../../configuration/cache/redis-session.md)
- [デフォルトのキャッシュにValkeyを使用](../../../configuration/cache/valkey-pg-cache.md)
- [セッション ストレージにValkeyを使用](../../../configuration/cache/valkey-session.md)
