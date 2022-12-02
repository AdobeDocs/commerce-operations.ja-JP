---
title: デフォルトのキャッシュに Redis を使用
description: Adobe CommerceとMagento Open Sourceのデフォルトのキャッシュとして Redis を設定する方法を説明します。
source-git-commit: 47d513e7ca51ad7dbc149d0f1e076f673452918c
workflow-type: tm+mt
source-wordcount: '1067'
ht-degree: 0%

---


# デフォルトのキャッシュに Redis を使用

Commerce には、Redis ページとデフォルトのキャッシュを設定するコマンドラインオプションが用意されています。 キャッシュは `<Commerce-install-dir>app/etc/env.php` ファイルの場合は、特に初期設定では、コマンドラインを使用することをお勧めします。 コマンドラインに検証が表示され、設定が構文的に正しいことが確認されます。

必ず [Redis をインストール](config-redis.md#install-redis) 続行する前に

## Redis のデフォルトキャッシュの設定

を実行します。 `setup:config:set` コマンドを実行し、Redis のデフォルトキャッシュに固有のパラメータを指定します。

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-<parameter>=<value>...
```

次のパラメーターを使用します。

- `--cache-backend=redis` Redis のデフォルトのキャッシュを有効にします。 この機能が既に有効になっている場合は、このパラメータを省略します。

- `--cache-backend-redis-<parameter>=<value>` は、デフォルトのキャッシュを設定するキーと値のペアのリストです。

| コマンドラインパラメータ | 値 | 意味 | デフォルト値 |
| ------------------------------ | --------- | ------- | ------------- |
| `cache-backend-redis-server` | server | 完全修飾ホスト名、IP アドレス、または UNIX ソケットへの絶対パス。 デフォルト値の 127.0.0.1 は、Redis が Commerce サーバーにインストールされていることを示します。 | `127.0.0.1` |
| `cache-backend-redis-port` | ポート | Redis サーバーのリスンポート | `6379` |
| `cache-backend-redis-db` | データベース | デフォルトのキャッシュとフルページのキャッシュの両方に Redis を使用する場合に必須です。 1 つのキャッシュのデータベース番号を指定する必要があります。その他のキャッシュは、デフォルトで 0 を使用します。<br><br>**重要**:Redis を複数のタイプのキャッシュに使用する場合、データベースの数が異なる必要があります。 デフォルトのキャッシュデータベース番号を 0 に、ページキャッシュデータベース番号を 1 に、セッションストレージデータベース番号を 2 に割り当てることをお勧めします。 | `0` |
| `cache-backend-redis-password` | パスワード | Redis のパスワードを設定すると、組み込みのセキュリティ機能の 1 つが有効になります。の `auth` コマンドを使用します。データベースにアクセスするためにクライアントに認証を要求します。 パスワードは Redis の設定ファイルで直接設定されます。 `/etc/redis/redis.conf` |  |

### コマンドの例

次の例では、Redis のデフォルトのキャッシュを有効にし、ホストをに設定します。 `127.0.0.1`を呼び出し、データベース番号を 0 に割り当てます。 Redis は、他のすべてのパラメータにデフォルト値を使用します。

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=127.0.0.1 --cache-backend-redis-db=0
```

## Redis ページキャッシュの設定

Commerce で Redis ページのキャッシュを設定するには、 `setup:config:set` コマンドに追加のパラメータを追加します。

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-<parameter>=<value>...
```

次のパラメーターを使用します。

- `--page-cache=redis` Redis ページのキャッシュを有効にします。 この機能が既に有効になっている場合は、このパラメータを省略します。

- `--page-cache-redis-<parameter>=<value>` は、ページキャッシュを設定するキーと値のペアのリストです。

| コマンドラインパラメータ | 値 | 意味 | デフォルト値 |
| ------------------------------ | --------- | ------- | ------------- |
| `page-cache-redis-server` | server | 完全修飾ホスト名、IP アドレス、または UNIX ソケットへの絶対パス。 デフォルト値の 127.0.0.1 は、Redis が Commerce サーバーにインストールされていることを示します。 | `127.0.0.1` |
| `page-cache-redis-port` | ポート | Redis サーバーのリスンポート | `6379` |
| `page-cache-redis-db` | データベース | デフォルトのページキャッシュとフルページキャッシュの両方に Redis を使用する場合に必須です。 1 つのキャッシュのデータベース番号を指定する必要があります。その他のキャッシュは、デフォルトで 0 を使用します。<br/>**重要**:Redis を複数のタイプのキャッシュに使用する場合、データベースの数が異なる必要があります。 デフォルトのキャッシュデータベース番号を 0 に、ページキャッシュデータベース番号を 1 に、セッションストレージデータベース番号を 2 に割り当てることをお勧めします。 | `0` |
| `page-cache-redis-password` | パスワード | Redis のパスワードを設定すると、組み込みのセキュリティ機能の 1 つが有効になります。の `auth` コマンドを使用します。データベースにアクセスするためにクライアントに認証を要求します。 Redis 設定ファイル内でパスワードを設定します。 `/etc/redis/redis.conf` |  |

### コマンドの例

次の例では、Redis ページのキャッシュを有効にし、ホストをに設定します。 `127.0.0.1`をクリックし、データベース番号を 1 に割り当てます。 その他のパラメータはすべてデフォルト値に設定されます。

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-redis-db=1
```

## 結果

Commerce では、2 つのコマンド例の結果、次のような行が `<Commerce-install-dir>app/etc/env.php`:

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

## EC2 インスタンスでのAWS ElastiCache の使用

Commerce 2.4.3 以降、Amazon EC2 でホストされるインスタンスは、ローカルの Redis インスタンスの代わりにAWS ElastiCache を使用できます。

>[!WARNING]
>
>このセクションは、Amazon EC2 VPC で実行されるコマースインスタンスでのみ機能します。 オンプレミスでのインストールでは機能しません。

### Redis クラスターの設定

後 [AWSでの Redis クラスターの設定](https://aws.amazon.com/getting-started/hands-on/setting-up-a-redis-cluster-with-amazon-elasticache/)ElastiCache を使用するように EC2 インスタンスを設定します。

1. [ElastiCache クラスターの作成](https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/set-up.html) EC2 インスタンスの同じ地域と VPC 内で
1. 接続を確認します。

   - EC2 インスタンスへの SSH 接続を開く
   - EC2 インスタンスで、Redis クライアントをインストールします。

      ```bash
      sudo apt-get install redis
      ```

   - EC2 セキュリティグループにインバウンド規則を追加します。タイプ `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - ElastiCache クラスターセキュリティグループにインバウンド規則を追加します：タイプ `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Redis CLI に接続します。

      ```bash
      redis-cli -h <ElastiCache Primary Endpoint host> -p <ElastiCache Primary Endpoint port>
      ```

### クラスターを使用するように Commerce を設定

Commerce は、複数の種類のキャッシュ設定をサポートしています。 一般に、キャッシュ設定はフロントエンドとバックエンドの間で分割されます。 フロントエンドキャッシュは、 `default`：任意のキャッシュタイプに使用されます。 パフォーマンスを向上させるために、をカスタマイズしたり、下位レベルのキャッシュに分割したりできます。 共通の Redis 設定は、デフォルトのキャッシュとページキャッシュを、それぞれ独自の Redis データベース (RDB) に分割することです。

実行 `setup` Redis エンドポイントを指定するコマンド

Commerce for Redis をデフォルトのキャッシュとして設定するには：

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=<ElastiCache Primary Endpoint host> --cache-backend-redis-port=<ElastiCache Primary Endpoint port> --cache-backend-redis-db=0
```

Commerce for Redis のページキャッシュを設定するには：

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=<ElastiCache Primary Endpoint host> --page-cache-redis-port=<ElastiCache Primary Endpoint port> --page-cache-redis-db=1
```

Redis をセッションストレージに使用するように Commerce を設定するには：

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=<ElastiCache Primary Endpoint host> --session-save-redis-port=<ElastiCache Primary Endpoint port> --session-save-redis-log-level=4 --session-save-redis-db=2
```

### 接続を確認

**Commerce が ElastiCache と通信していることを確認するには**:

1. Commerce EC2 インスタンスへの SSH 接続を開きます。
1. Redis モニタを起動します。

   ```bash
   redis-cli -h <ElastiCache-Primary-Endpoint-host> -p <ElastiCache-Primary-Endpoint-port> monitor
   ```

1. Commerce UI でページを開きます。
1. を確認します。 [キャッシュ出力](#verify-redis-connection) を設定します。

## 新しい Redis キャッシュの実装

Commerce 2.3.5 の時点では、拡張 Redis キャッシュ実装を使用することをお勧めします。 `\Magento\Framework\Cache\Backend\Redis`.

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
],
```

## Redis のプリロード機能

Commerce は設定データを Redis キャッシュに保存するので、ページ間で再利用されるデータをプリロードできます。 プリロードが必要なキーを見つけるには、Redis から Commerce に転送されるデータを分析します。 各ページに読み込まれるデータ（例： ）をプリロードすることをお勧めします。 `SYSTEM_DEFAULT`, `EAV_ENTITY_TYPES`, `DB_IS_UP_TO_DATE`.

Redis は `pipeline` を使用して読み込みリクエストを複合化できます。 キーには、データベースのプレフィックスを含める必要があります。例えば、データベースのプレフィックスが `061_`では、プリロードキーは次のようになります。 `061_SYSTEM_DEFAULT`

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

L2 キャッシュでプリロード機能を使用する場合は、必ず `:hash` L2 キャッシュはデータ自体ではなく、データのハッシュのみを転送するので、サフィックスをキーに追加します。

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

## 並列生成

2.4.0 リリースから、 `allow_parallel_generation` ロック待ちを排除するユーザー用のオプション。
これはデフォルトで無効になっています。過剰な設定やブロックができるまで無効にすることをお勧めします。

**並列生成を有効にするには**:

```bash
bin/magento setup:config:set --allow-parallel-generation
```

これはフラグなので、コマンドで無効にすることはできません。 設定値を手動でに設定する必要があります。 `false`:

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

## Redis 接続の確認

Redis と Commerce が連携して動作していることを確認するには、Redis を実行しているサーバにログインし、ターミナルを開いて、Redis monitor コマンドまたは ping コマンドを使用します。

### Redis モニタコマンド

```bash
redis-cli monitor
```

ページキャッシュ出力の例：

```terminal
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

```bash
redis-cli ping
```

期待される応答は次のとおりです。 `PONG`

両方のコマンドが成功した場合、Redis は正しく設定されます。

### 圧縮データの検査

圧縮されたセッションデータとページキャッシュを調べるには、 [RESP.app](https://flathub.org/apps/details/app.resp.RESP) は、Commerce 2 セッションとページのキャッシュの自動解凍をサポートし、PHP セッションデータを人間が読み取り可能な形式で表示します。
