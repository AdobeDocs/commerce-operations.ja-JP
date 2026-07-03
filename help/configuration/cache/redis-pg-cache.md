---
title: デフォルトおよびページキャッシュ用のRedisの設定
description: Adobe CommerceのデフォルトおよびページキャッシュバックエンドとしてRedisを設定する方法について説明します。 CLI コマンド、env.php設定、接続検証を確認します。
feature: Configuration, Cache
exl-id: 8c097cfc-85d0-4e96-b56e-284fde40d459
badgePaas: label="オンプレミス" type="Informative" url="https://experienceleague.adobe.com/ja/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce オンプレミス プロジェクトにのみ適用されます。"
autotag-review: '2026-06-22T21:55:53.227Z'
TQID: 'https://experienceleague.adobe.com/2KjWE19ud32PUdvJQWNWkK338ysaa5vt0mA4EyyP66I'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 7171e5abfad69ad0f2d3f4c4b5eb57c13d07feb4
workflow-type: tm+mt
source-wordcount: 1261
ht-degree: 0%

---

# デフォルトおよびページキャッシュ用にRedisを設定

{{cloud-cache-config}}

Commerceには、Redis ページとデフォルトのキャッシュを設定するためのコマンドラインオプションが用意されています。 `<Commerce-install-dir>app/etc/env.php` ファイルを編集してキャッシュを設定できますが、特に初期設定では、コマンドラインを使用することをお勧めします。 コマンドラインは検証を提供し、設定が構文的に正しいことを確認します。

**前提条件：**

続行する前に[Redis](config-redis.md#install-redis)をインストールします。

>[!NOTE]
>
>EC2でホストされているCommerce インスタンスの場合、ローカル Redis インスタンスの代わりにAWS ElastiCacheを使用できます。 EC2 インスタンスの[Elasticacheの設定](redis-elasticache-for-ec2.md)を参照してください。

## Redis キャッシュ実装

Adobe Commerceでは、以下のRedis キャッシュバックエンド実装を使用しています。

- **従来のRedis バックエンド** （`Cm_Cache_Backend_Redis`） – 古いRedis構成で使用されている非推奨の実装。
- **Redis backend** （`Magento\Framework\Cache\Backend\Redis`） – このトピックのコマンドライン設定でデフォルトおよびページキャッシュに使用されるバックエンド。
- **L2 キャッシュ バックエンド** （`Magento\Framework\Cache\Backend\RemoteSynchronizedCache`） - Redisをリモート バックエンドおよびローカル ファイル キャッシュ ストレージとして使用し、ノード間でキャッシュ データを同期する2段階キャッシュ実装。 [2 レベル キャッシュ設定](level-two-cache.md)を参照してください。

## Redisのデフォルトキャッシュの設定

`setup:config:set` コマンドを実行し、Redisの既定のキャッシュに固有のパラメーターを指定します。

```shell
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-<parameter>=<value>...
```

一般的なパラメーターは次のとおりです。

- `--cache-backend=redis`は、Redisの既定のキャッシュを有効にします。 この機能が既に有効になっている場合は、このパラメーターを省略します。

- `--cache-backend-redis-<parameter>=<value>`は、デフォルトのキャッシュを設定するキーと値のペアのリストです。

| コマンドラインパラメーター | 値 | 意味 | デフォルト値 |
| --- | --- | --- | --- |
| `cache-backend-redis-server` | サーバー | 完全修飾ホスト名、IP アドレス、またはUNIX ソケットへの絶対パス。 デフォルト値127.0.0.1は、RedisがCommerce サーバーにインストールされていることを示します。 | `127.0.0.1` |
| `cache-backend-redis-port` | ポート | Redis サーバーのリッスン ポート | `6379` |
| `cache-backend-redis-db` | データベース | デフォルトのキャッシュとページ全体のキャッシュの両方にRedisを使用する場合は必須です。 1つのキャッシュのデータベース番号を指定します。他のキャッシュはデフォルトで0を使用します。<br><br>**重要**: Redisを複数のタイプのキャッシュに使用する場合、データベース番号は異なる必要があります。 デフォルトのキャッシングデータベース番号を0に、ページキャッシングデータベース番号を1に、セッションストレージデータベース番号を2に割り当てることをお勧めします。 | `0` |
| `cache-backend-redis-password` | パスワード | Redis パスワードを設定すると、組み込みのセキュリティ機能の1つである`auth` コマンドが有効になり、クライアントはデータベースにアクセスするために認証する必要があります。 パスワードは、Redisの設定ファイル `/etc/redis/redis.conf`で直接設定されています | |
| `cache-backend-redis-compress-data` | compress_data | 圧縮を無効にするには、`0`に設定します。 | `1` |
| `cache-backend-redis-compression-lib` | compression_lib | 使用する圧縮ライブラリ。 サポートされている値には、`snappy`、`lzf`、`l4z`、`zstd`および`gzip`が含まれます。 自動的に決定するには、空白のままにします。 | |
| `cache-backend-redis-use-lua` | use_lua | すべてのRedis操作でLua スクリプトを有効または無効にします。 <br><br>**既定：`0`.**&#x200B;に保つ Lua モードはデフォルトで無効になっており、Luaが有効になったときにバンドルされたRedis ライブラリ（1.17.x）で発生する既知のパフォーマンスのリグレッションとGraphQL キャッシュミスの問題を防ぎます。 | `0` |
| `cache-backend-redis-use-lua-on-gc` | use_lua_on_gc | ガベージコレクション （cron ジョブ `backend_clean_cache`）のLua スクリプトを有効または無効にします。 <br><br>**既定：`1`.**&#x200B;に保つ GC中にアトミックタグ設定のクリーンアップを確保するために、意図的に有効にします。 これを指定しないと、`backend_clean_cache` cronがキャッシュ保存操作と同時に実行され、キャッシュタグインデックスに対応するレコードが含まれていないキャッシュエントリが残ると、競合状態が発生する可能性があります。 これにより、タグベースの無効化がサイレントに失敗します。例えば、製品価格を更新しても製品キャッシュが無効化されない場合、代わりに完全なキャッシュのフラッシュが必要になります。 | `1` |

### Lua モード

Lua モードを有効にすると、複数のRedis操作（キャッシュ書き込み、タグ更新、ガベージコレクション）が、`EVALSHA`経由でサーバーサイドで実行される単一のアトミックスクリプトにバンドルされます。 これにより、同時リクエストからのインターリーブを防ぐことができます。例えば、キャッシュエントリとそのタグメンバーシップが一緒に書き込まれます。

>[!WARNING]
>
>Adobe Commerce版の影響を理解せずに、`use_lua`および`use_lua_on_gc`のデフォルト値を変更しないでください。
>
>- **`use_lua`**：これをAdobe Commerce 2.4.7または2.4.8 （ライブラリ `colinmollenhour/cache-backend-redis` 1.17.1）で有効にすると、キャッシュの破損とGraphQL キャッシュの失敗の問題が発生する可能性があります。
>- **`use_lua_on_gc`**: Adobe Commerce 2.4.8でこれを無効にすると、ガベージコレクション中にアトミックプロテクションが削除され、タグベースのキャッシュ無効化がサイレントで失敗する可能性があります。その場合、完全なキャッシュフラッシュが必要になります。

## コマンドの例（デフォルトのキャッシュ）

次の例では、Redisのデフォルトのキャッシュを有効にし、ホストを`127.0.0.1`に設定し、データベース番号を0に割り当てます。 Redisは、他のすべてのパラメーターにデフォルト値を使用します。

```shell
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=127.0.0.1 --cache-backend-redis-db=0
```

## Redis ページキャッシュの設定

CommerceでRedis ページキャッシュを設定するには、パラメーターを追加して`setup:config:set` コマンドを実行します。

```shell
bin/magento setup:config:set --page-cache=redis --page-cache-redis-<parameter>=<value>...
```

一般的なパラメーターは次のとおりです。

- `--page-cache=redis`はRedis ページのキャッシュを有効にします。 この機能が既に有効になっている場合は、このパラメーターを省略します。

- `--page-cache-redis-<parameter>=<value>`は、ページキャッシュを設定するキーと値のペアのリストです。

| コマンドラインパラメーター | 値 | 意味 | デフォルト値 |
| --- | --- | --- | --- |
| `page-cache-redis-server` | サーバー | 完全修飾ホスト名、IP アドレス、またはUNIX ソケットへの絶対パス。 デフォルト値127.0.0.1は、RedisがCommerce サーバーにインストールされていることを示します。 | `127.0.0.1` |
| `page-cache-redis-port` | ポート | Redis サーバーのリッスン ポート | `6379` |
| `page-cache-redis-db` | データベース | デフォルトとフルページキャッシュの両方にRedisを使用する場合は必須です。 1つのキャッシュのデータベース番号を指定します。他のキャッシュはデフォルトで0を使用します。<br/>**重要**: Redisを複数のタイプのキャッシュに使用する場合、データベース番号は異なる必要があります。 デフォルトのキャッシングデータベース番号を0に、ページキャッシングデータベース番号を1に、セッションストレージデータベース番号を2に割り当てることをお勧めします。 | `0` |
| `page-cache-redis-password` | パスワード | Redis パスワードを設定すると、組み込みのセキュリティ機能の1つである`auth` コマンドが有効になり、クライアントはデータベースにアクセスするために認証する必要があります。 Redis設定ファイル内でパスワードを設定します：`/etc/redis/redis.conf` | |
| `page-cache-redis-compress-data` | compress_data | ページ全体のキャッシュを圧縮するには、`1`に設定します。 圧縮を無効にするには、`0`を使用します。 | `0` |
| `page-cache-redis-compression-lib` | compression_lib | 使用する圧縮ライブラリ。 サポートされている値には、`snappy`、`lzf`、`l4z`、`zstd`および`gzip`が含まれます。 自動的に決定するには、空白のままにします。 | |

次の例では、Redis ページキャッシュを有効にし、ホストを`127.0.0.1`に設定し、データベース番号を`1`に割り当てます。 その他のパラメーターはすべてデフォルト値に設定されます。

```shell
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-redis-db=1
```

{{valkey-redis-cli-note}}

### Commerce環境設定の確認

Redis キャッシュを構成するコマンドを実行すると、Commerce環境設定（`<Commerce-install-dir>app/etc/env.php`）が更新されます。

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'port' => '6379',
                'database' => '1',
                'compress_data' => '0'
            ]
        ]
    ]
],
```

## その他のキャッシュオプションの設定

### Redis プリロード機能

Commerceは設定データをRedis キャッシュに保存するため、ページ間で再利用されるデータをプリロードできます。 プリロードする必要があるキーを見つけるには、RedisからCommerceに転送されるデータを分析します。 Adobeは、`SYSTEM_DEFAULT`、`EAV_ENTITY_TYPES`、`DB_IS_UP_TO_DATE`など、すべてのページに読み込まれるデータのプリロードを提案します。

Redisは`pipeline`を使用して読み込み要求を合成します。 キーには、データベースのプレフィックスを含める必要があります。例えば、データベースのプレフィックスが`061_`の場合、プリロードキーは`061_SYSTEM_DEFAULT`のようになります

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => '061_',
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => 'redis',
                'database' => '0',
                'port' => '6379',
                'password' => '',
                'compress_data' => '1',
                'compression_lib' => '',
                'preload_keys' => [
                    '061_EAV_ENTITY_TYPES',
                    '061_GLOBAL_PLUGIN_LIST',
                    '061_DB_IS_UP_TO_DATE',
                    '061_SYSTEM_DEFAULT',
                ],
            ]
        ],
        'page_cache' => [
            'id_prefix' => '061_'
        ]
    ]
]
```

L2 キャッシュでプリロード機能を使用する場合は、キーに`:hash` サフィックスを追加する必要があります。 L2 キャッシュは、実際のデータではなく、データのハッシュのみを転送します。

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

### 並列生成

Commerce 2.4.0 リリース以降、Adobeでは、ロック待ちを排除するユーザーに対して`allow_parallel_generation` オプションが導入されました。 デフォルトでは無効になっています。Adobeでは、過剰な設定やブロックがあるまで無効にすることをお勧めします。

**並列生成を有効にするには**:

```shell
bin/magento setup:config:set --allow-parallel-generation
```

フラグなので、コマンドで無効にすることはできません。 設定値を手動で`false`に設定します。

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
                'backend_options' => [
                    'server' => 'redis',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                    'compression_lib' => ''
                ]
            ],
            'page_cache' => [
                'id_prefix' => 'b0b_'
            ]
        ],
        'allow_parallel_generation' => false
    ],
```

### PHP Redis拡張機能

ご使用の環境でサポートされている場合は、ネイティブ PHP Redis拡張機能（`phpredis`）を使用します。

#### Aptを使用

DebianまたはUbuntuの場合は、`apt`を使用します。

```bash
sudo apt-get install php-redis
sudo systemctl restart php-fpm
php -m | grep redis
```

#### Pclを使用

代わりに、`pecl`を使用してください。

```bash
sudo pecl install redis
echo "extension=redis.so" | sudo tee /etc/php/<version>/mods-available/redis.ini
sudo phpenmod redis
sudo systemctl restart php-fpm
php -m | grep redis
```

## Redis接続の確認

RedisとCommerceが正常に連携していることを確認するには：

1. RedisとCommerceを実行するサーバーにログインします。
1. ターミナルを開きます。
1. `redis-cli monitor` コマンドまたは`redis-cli ping` コマンドを使用して、接続を確認します。

コマンドが成功した場合、Redisは実行中であり、Commerce アプリケーションと通信できます。 エラーが発生した場合は、RedisとCommerce間の接続の問題を解決する必要があります。

### Redis monitor コマンド

```shell
redis-cli monitor
```

ページキャッシュ出力の例：

```text
1476826133.810090 [0 127.0.0.1:52366] "select" "1"
1476826133.816293 [0 127.0.0.1:52367] "select" "0"
1476826133.817461 [0 127.0.0.1:52367] "hget" "zc:k:ea6_GLOBAL__DICONFIG" "d"
1476826133.829666 [0 127.0.0.1:52367] "hget" "zc:k:ea6_DICONFIG049005964B465901F774DB9751971818" "d"
1476826133.837854 [0 127.0.0.1:52367] "hget" "zc:k:ea6_INTERCEPTION" "d"
1476826133.868374 [0 127.0.0.1:52368] "select" "1"
1476826133.869011 [0 127.0.0.1:52369] "select" "0"
1476826133.869601 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DEFAULT_CONFIG_CACHE_DEFAULT__10__235__32__1080MAGENTO2" "d"
1476826133.872317 [0 127.0.0.1:52369] "hget" "zc:k:ea6_INITIAL_CONFIG" "d"
1476826133.879267 [0 127.0.0.1:52369] "hget" "zc:k:ea6_GLOBAL_PRIMARY_PLUGIN_LIST" "d"
...
```

両方のコマンドが成功した場合、Redisは適切に設定されます。

### 圧縮データの検査

圧縮されたセッション データとページ キャッシュを調べるには、[RESP.app](https://flathub.org/apps/details/app.resp.RESP) ツールを使用します。 Commerce 2のセッションデータとページキャッシュデータの自動解凍をサポートし、PHP セッションデータを人間が読める形式で表示します。
