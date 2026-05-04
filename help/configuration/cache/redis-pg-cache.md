---
title: デフォルトのキャッシュにRedisを使用
description: Adobe CommerceのデフォルトキャッシュとしてRedisを設定する方法を説明します。 コマンドラインのセットアップ、設定オプション、検証手法について説明します。
feature: Configuration, Cache
exl-id: 8c097cfc-85d0-4e96-b56e-284fde40d459
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '907'
ht-degree: 0%

---

# デフォルトのキャッシュにRedisを使用

Commerceには、Redis ページとデフォルトのキャッシュを設定するためのコマンドラインオプションが用意されています。 `<Commerce-install-dir>app/etc/env.php` ファイルを編集してキャッシュを設定できますが、特に初期設定では、コマンドラインを使用することをお勧めします。 コマンドラインは検証を提供し、設定が構文的に正しいことを確認します。

続行する前に、[Redis](config-redis.md#install-redis)をインストールする必要があります。

>[!NOTE]
>
>EC2でホストされているCommerce インスタンスの場合、ローカル Redis インスタンスの代わりにAWS ElastiCacheを使用できます。 EC2 インスタンスの[Elasticacheの設定](redis-elasticache-for-ec2.md)を参照してください。

## Redisのデフォルトキャッシュの設定

`setup:config:set` コマンドを実行し、Redisの既定のキャッシュに固有のパラメーターを指定します。

```shell
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-<parameter>=<value>...
```

次のパラメーターを使用します。

- `--cache-backend=redis`は、Redisの既定のキャッシュを有効にします。 この機能が既に有効になっている場合は、このパラメーターを省略します。

- `--cache-backend-redis-<parameter>=<value>`は、デフォルトのキャッシュを設定するキーと値のペアのリストです。

| コマンドラインパラメーター | 値 | 意味 | デフォルト値 |
| ------------------------------ | --------- | ------- | ------------- |
| `cache-backend-redis-server` | サーバー | 完全修飾ホスト名、IP アドレス、またはUNIX ソケットへの絶対パス。 デフォルト値127.0.0.1は、RedisがCommerce サーバーにインストールされていることを示します。 | `127.0.0.1` |
| `cache-backend-redis-port` | ポート | Redis サーバーのリッスン ポート | `6379` |
| `cache-backend-redis-db` | データベース | デフォルトのキャッシュとページ全体のキャッシュの両方にRedisを使用する場合は必須です。 いずれかのキャッシュのデータベース番号を指定する必要があります。他のキャッシュはデフォルトで0を使用します。<br><br>**重要**：複数のタイプのキャッシュにRedisを使用する場合、データベース番号は異なる必要があります。 デフォルトのキャッシングデータベース番号を0に、ページキャッシングデータベース番号を1に、セッションストレージデータベース番号を2に割り当てることをお勧めします。 | `0` |
| `cache-backend-redis-password` | パスワード | Redis パスワードを設定すると、組み込みのセキュリティ機能の1つである`auth` コマンドが有効になり、クライアントはデータベースにアクセスするために認証する必要があります。 パスワードは、Redisの設定ファイル `/etc/redis/redis.conf`で直接設定されています | |
| `--cache-backend-redis-use-lua` | use_lua | LUAを有効または無効にします。 <br><br>**LUA**: Luaを使用すると、Redis内でアプリケーションロジックの一部を実行できるようになり、パフォーマンスが向上し、アトミックな実行を通じてデータの一貫性が確保されます。 | `0` |
| `--cache-backend-redis-use-lua-on-gc` | use_lua_on_gc | ガベージコレクションのLUAを有効または無効にします。 <br><br>**LUA**: Luaを使用すると、Redis内でアプリケーションロジックの一部を実行できるようになり、パフォーマンスが向上し、アトミックな実行を通じてデータの一貫性が確保されます。 | `1` |

### コマンド例

次の例では、Redisのデフォルトのキャッシュを有効にし、ホストを`127.0.0.1`に設定し、データベース番号を0に割り当てます。 Redisは、他のすべてのパラメーターにデフォルト値を使用します。

```shell
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=127.0.0.1 --cache-backend-redis-db=0
```

## Redis ページキャッシュの設定

CommerceでRedis ページキャッシュを設定するには、パラメーターを追加して`setup:config:set` コマンドを実行します。

```shell
bin/magento setup:config:set --page-cache=redis --page-cache-redis-<parameter>=<value>...
```

次のパラメーターを使用します。

- `--page-cache=redis`はRedis ページのキャッシュを有効にします。 この機能が既に有効になっている場合は、このパラメーターを省略します。

- `--page-cache-redis-<parameter>=<value>`は、ページキャッシュを設定するキーと値のペアのリストです。

| コマンドラインパラメーター | 値 | 意味 | デフォルト値 |
| ------------------------------ | --------- | ------- | ------------- |
| `page-cache-redis-server` | サーバー | 完全修飾ホスト名、IP アドレス、またはUNIX ソケットへの絶対パス。 デフォルト値127.0.0.1は、RedisがCommerce サーバーにインストールされていることを示します。 | `127.0.0.1` |
| `page-cache-redis-port` | ポート | Redis サーバーのリッスン ポート | `6379` |
| `page-cache-redis-db` | データベース | デフォルトとフルページキャッシュの両方にRedisを使用する場合は必須です。 いずれかのキャッシュのデータベース番号を指定する必要があります。他のキャッシュはデフォルトで0を使用します。<br/>**重要**：複数のタイプのキャッシュにRedisを使用する場合、データベース番号は異なる必要があります。 デフォルトのキャッシングデータベース番号を0に、ページキャッシングデータベース番号を1に、セッションストレージデータベース番号を2に割り当てることをお勧めします。 | `0` |
| `page-cache-redis-password` | パスワード | Redis パスワードを設定すると、組み込みのセキュリティ機能の1つである`auth` コマンドが有効になり、クライアントはデータベースにアクセスするために認証する必要があります。 Redis設定ファイル内でパスワードを設定します：`/etc/redis/redis.conf` | |

### コマンド例

次の例では、Redis ページキャッシュを有効にし、ホストを`127.0.0.1`に設定し、データベース番号を1に割り当てます。 その他のパラメーターはすべてデフォルト値に設定されます。

```shell
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-redis-db=1
```

## Commerce環境設定の確認

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

この節では、デフォルトで無効になっているオプションの設定設定を有効にする方法について説明します。

### Redis プリロード機能

Commerceは設定データをRedis キャッシュに保存するため、ページ間で再利用されるデータをプリロードできます。 プリロードする必要があるキーを見つけるには、RedisからCommerceに転送されるデータを分析します。 `SYSTEM_DEFAULT`、`EAV_ENTITY_TYPES`、`DB_IS_UP_TO_DATE`など、すべてのページに読み込まれるデータをプリロードすることをお勧めします。

Redisは、読み込み要求を合成するために`pipeline`を使用します。 キーには、データベースのプレフィックスを含める必要があります。例えば、データベースのプレフィックスが`061_`の場合、プリロード キーは`061_SYSTEM_DEFAULT`のようになります

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

L2 キャッシュでプリロード機能を使用している場合は、L2 キャッシュはデータ自体ではなくデータのハッシュのみを転送するため、`:hash` サフィックスをキーに追加することを忘れないでください。

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

### 並列生成

`allow_parallel_generation` オプションを有効にすることで、ロック待ちの必要がなくなります。

このオプションはデフォルトで無効になっており、Adobeでは、多数の設定またはブロックが含まれるまで無効にすることをお勧めします。

**並列生成を有効にするには**:

```shell
bin/magento setup:config:set --allow-parallel-generation
```

このオプションはフラグなので、コマンドで無効にすることはできません。 設定値を手動で`false`に設定する必要があります：

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

## Redis接続の確認

RedisとCommerceが連携していることを確認するには、Redisを実行しているサーバーにログインしてターミナルを開き、Redis monitor コマンドまたはping コマンドを使用します。

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
1476826133.883312 [0 127.0.0.1:52369] "hget" "zc:k:ea6_GLOBAL__EVENT_CONFIG_CACHE" "d"
1476826133.898431 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DB_PDO_MYSQL_DDL_STAGING_UPDATE_1" "d"
1476826133.898794 [0 127.0.0.1:52369] "hget" "zc:k:ea6_RESOLVED_STORES_D1BEFA03C79CA0B84ECC488DEA96BC68" "d"
1476826133.905738 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DEFAULT_CONFIG_CACHE_STORE_DEFAULT_10__235__32__1080MAGENTO2" "d"

... more ...

1476826210.634998 [0 127.0.0.1:52439] "hmset" "zc:k:ea6_MVIEW_CONFIG" "d" "a:18:{s:19:\"design_config_dummy\";a:4:{s:7:\"view_id\";s:19:\"design_config_dummy\";s:12:\"action_class\";s:39:\"Magento\\Theme\\Model\\Indexer\\Mview\\Dummy\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:0:{}}s:14:\"customer_dummy\";a:4:{s:7:\"view_id\";s:14:\"customer_dummy\";s:12:\"action_class\";s:42:\"Magento\\Customer\\Model\\Indexer\\Mview\\Dummy\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:0:{}}s:13:\"cms_page_grid\";a:4:{s:7:\"view_id\";s:13:\"cms_page_grid\";s:12:\"action_class\";s:43:\"Magento\\Catalog\\Model\\Indexer\\Category\\Flat\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:1:{s:8:\"cms_page\";a:3:{s:4:\"name\";s:8:\"cms_page\";s:6:\"column\";s:7:\"page_id\";s:18:\"subscription_model\";N;}}}s:21:\"catalog_category_flat\";a:4:{s:7:\"view_id\";s:21:\"catalog_category_flat\";s:12:\"action_class\";s:43:\"Magento\\Catalog\\Model\\Indexer\\Category\\Flat\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:6:{s:23:\"catalog_category_entity\";a:3:{s:4:\"name\";s:23:\"catalog_category_entity\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";N;}s:31:\"catalog_category_entity_decimal\";a:3:{s:4:\"name\";s:31:\"catalog_category_entity_decimal\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:27:\"catalog_category_entity_int\";a:3:{s:4:\"name\";s:27:\"catalog_category_entity_int\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:28:\"catalog_category_entity_text\";a:3:{s:4:\"name\";s:28:\"catalog_category_entity_text\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:31:\"catalog_category_entity_varchar\";a:3:{s:4:\"name\";s:31:\"catalog_category_entity_varchar\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:32:\"catalog_category_entity_datetime\";a:3:{s:4:\"name\";s:32:\"catalog_category_entity_datetime\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}}}s:24:\"catalog_category_product\";a:4:{s:7:\"view_id\";s:24:\"catalog_category_product\";s:12:\"action_class\";s:46:\"Magento\\Catalog\\Model\\Indexer\\Category\\Product\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:2:{s:23:\"catalog_category_entity\";a:3:{s:4:\"name\";s:23:\"catalog_category_entity\";s:6:\"column\"

... more ...
```

### Redis ping コマンド

```shell
redis-cli ping
```

予想される応答は`PONG`です

両方のコマンドが成功した場合、Redisは適切に設定されます。

### 圧縮されたデータの検査

圧縮されたセッションデータとページキャッシュを調べるために、[RESP.app](https://flathub.org/apps/details/app.resp.RESP)は、Commerce 2 セッションとページキャッシュの自動解凍をサポートし、PHP セッションデータを人間が読み取り可能な形式で表示します。
