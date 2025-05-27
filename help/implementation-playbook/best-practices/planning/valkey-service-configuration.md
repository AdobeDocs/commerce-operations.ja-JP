---
title: Valkey サービス設定のベストプラクティス
description: Adobe Commerce用の拡張された Valkey キャッシュ実装を使用して、キャッシュパフォーマンスを向上させる方法を説明します。
role: Developer, Admin
feature: Best Practices, Cache
source-git-commit: 107b5bb19c3375be64c216bd89feb8410e2fc2bd
workflow-type: tm+mt
source-wordcount: '682'
ht-degree: 0%

---

# Valkey サービス設定のベストプラクティス

Adobeでは、Valkey サービスを設定する際に、次のベストプラクティスを推奨します。

## Valkey L2 キャッシュの設定

`.magento.env.yaml` 設定ファイルの `VALKEY_BACKEND` デプロイメント変数を設定して、Valkey L2 キャッシュを設定します。

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

クラウドインフラストラクチャー上の環境設定については、_クラウドインフラストラクチャー上のCommerceガイド_ の [`VALKEY_BACKEND`](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_backend) を参照してください。

オンプレミスでのインストールの場合は、[ 設定ガイド ](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) の _Valkey ページのキャッシュの設定_ を参照してください。

>[!NOTE]
>
>`ece-tools` パッケージの最新バージョンを使用していることを確認します。 そうでない場合は [ 最新バージョンにアップグレード ](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package) します。 `composer show magento/ece-tools` CLI コマンドを使用すると、ローカル環境にインストールされているバージョンを確認できます。

### L2 キャッシュメモリのサイズ設定（Adobe Commerce Cloud）

L2 キャッシュは、ストレージ メカニズムとして [ 一時ファイル システム ](https://en.wikipedia.org/wiki/Tmpfs) を使用します。 特殊なキー値データベース・システムと比較して、一時ファイル・システムには、メモリの使用を制御するためのキー削除ポリシーがありません。

メモリ使用量の制御がないと、古くなったキャッシュが蓄積され、L2 キャッシュのメモリ使用量が時間の経過とともに増加する可能性があります。

L2 キャッシュ実装のメモリ不足を避けるために、Adobe Commerceは、特定のしきい値に達するとストレージをクリアします。 デフォルトのしきい値は 95% です。

キャッシュストレージのプロジェクト要件に基づいて、L2 キャッシュメモリの最大使用量を調整することが重要です。 次のいずれかの方法を使用して、メモリキャッシュサイズを設定します。

- `/dev/shm` マウントのサイズ変更をリクエストするサポートチケットを作成します。
- ストレージの最大充填率に上限を設定するようにアプリケーションレベルで `cleanup_percentage` プロパティを調整します。 残りの空きメモリは、他のサービスで使用できます。
設定は、キャッシュ設定グループ `cache/frontend/default/backend_options/cleanup_percentage` の下にあるデプロイメント設定で調整できます。

>[!NOTE]
>
>`cleanup_percentage` 設定オプションは、Adobe Commerce 2.4.4 で導入されました。

次の例は、`.magento.env.yaml` ファイルの `CACHE_CONFIGURATION` を示しています。

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

キャッシュ要件は、プロジェクト設定とカスタムサードパーティコードによって異なる場合があります。 L2 キャッシュのサイズ設定の範囲を使用すると、不要なしきい値のヒットなしで L2 キャッシュを動作させることができます。
ストレージのクリアが頻繁に行われるのを避けるために、L2 キャッシュメモリの使用状況が、しきい値を下回る一定のレベルで安定していることが理想的です。

以下の CLI コマンドを使用して、クラスターの各ノードでの L2 キャッシュストレージメモリの使用状況を確認し、`/dev/shm` 行を検索できます。
使用方法はノードによって異なる場合がありますが、同じ値に収束する必要があります。

```bash
df -h
```

## 有効なスレーブ接続を有効にする

`.magento.env.yaml` 設定ファイルの Valkey スレーブ接続を有効にして、1 つのノードだけが読み取り/書き込みトラフィックを処理し、他のノードが読み取り専用トラフィックを処理できるようにします。

```yaml
stage:
  deploy:
    VALKEY_USE_SLAVE_CONNECTION: true
```

Commerce詳しくは、_Cloud Infrastructure ガイドの [VALKEY_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy.html#valkey_use_slave_connection) を参照してください_

Adobe Commerceのオンプレミスインストールの場合は、`bin/magento:setup` コマンドを使用して、新しい Valkey キャッシュ実装を設定します。 詳しくは、『 _設定ガイド_ の [ デフォルトキャッシュに対する Valkey の使用 ](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) を参照してください。

>[!WARNING]
>
>[ 拡張/分割アーキテクチャ _を使用して、クラウドインフラストラクチャプロジェクト用の Valkey スレーブ接続を設定しないでください ](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/architecture/scaled-architecture)_。 これにより、Redis 接続エラーが発生します。 詳しくは、_Cloud Infrastructure のCommerce[ ガイドの ](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection)Redis 設定ガイダンス_ を参照してください。

## キーをプリロード

ページ間でデータを再利用するには、プリロードのキーを `.magento.env.yaml` 設定ファイルにリストします。

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
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

オンプレミス環境でのインストールについては、[ 設定ガイド ](../../../configuration/cache/redis-pg-cache.md#redis-preload-feature) の _Valkey プリロード機能_ を参照してください。

## 古いキャッシュを有効にする

新しいキャッシュを並行して生成しながら古いキャッシュを使用することで、特に多数のブロックとキャッシュキーを処理する場合に、ロックの待ち時間を短縮し、パフォーマンスを向上させます。 古くなったキャッシュを有効にし、`.magento.env.yaml` 設定ファイルでキャッシュタイプを定義します。

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
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

>[!NOTE]
>
>前の例では、`full_page` キャッシュは [Fastly](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/fastly) を使用しているので、クラウドインフラストラクチャプロジェクトのAdobe Commerceには関係ありません。

オンプレミスのインストールを構成する方法については、[ 構成ガイド ](../../../configuration/cache/level-two-cache.md#stale-cache-options) の _古いキャッシュ オプション_ を参照してください。

デプロイメント中、[ ビルドおよびデプロイログ ](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/test/log-locations.html#build-and-deploy-logs) に次の行が表示されます。

```
W:   - Downloading colinmollenhour/credis (1.11.1)
W:   - Downloading colinmollenhour/php-redis-session-abstract (v1.4.5)
...
W:   - Installing colinmollenhour/credis (1.11.1): Extracting archive
W:   - Installing colinmollenhour/php-redis-session-abstract (v1.4.5): Extracting archive
...
[2022-08-17 01:13:40] INFO: Version of service 'valkey' is 8.0
[2022-08-17 01:13:40] INFO: Version of service 'valkey-session' is 8.0
[2022-08-17 01:13:40] INFO: valkey-session will be used for the session if it was not overridden by SESSION_CONFIGURATION.
```

## キャッシュ圧縮

6 GB を超える Valkey `maxmemory` を使用している場合は、キャッシュ圧縮を使用して、キーが消費する領域を減らすことができます。 クライアントサイドのパフォーマンスにはトレードオフがあることに注意してください。 空きの CPU がある場合は、Adobeが有効にすることをお勧めします。 _設定ガイド_ の [ セッションストレージに Redis を使用 ](../../../configuration/cache/redis-session.md) を参照してください。

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true;
      frontend:
        default:
          backend_options:
            compress_data: 4              # 0-9
            compress_tags: 4              # 0-9
            compress_threshold: 20480     # do not compress files smaller than this value
            compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~70%)
```

## 追加情報

- [Redis ページキャッシュ](../../../configuration/cache/redis-pg-cache.md)
- [セッションストレージに Redis を使用](../../../configuration/cache/redis-session.md)
