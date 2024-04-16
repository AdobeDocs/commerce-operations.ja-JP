---
title: 既定のキャッシュに Redis を使用
description: Adobe Commerceのデフォルトキャッシュとして Redis を設定する方法を説明します。
feature: Configuration, Cache
exl-id: 8c097cfc-85d0-4e96-b56e-284fde40d459
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '1069'
ht-degree: 0%

---

# 既定のキャッシュに Redis を使用

Commerceには、Redis ページとデフォルトのキャッシングを設定するためのコマンドラインオプションが用意されています。 キャッシュを設定するには、を編集します `<Commerce-install-dir>app/etc/env.php` ファイルを開く場合は、特に初期設定において、コマンドラインを使用することをお勧めします。 コマンドラインで検証を行うことにより、設定の構文が正しいことを確認します。

あなたは必要があります [redis のインストール](config-redis.md#install-redis) 続行する前に。

## Redis デフォルトキャッシュの設定

を実行 `setup:config:set` コマンドを実行し、Redis のデフォルトキャッシュに固有のパラメーターを指定します。

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-<parameter>=<value>...
```

次のパラメーターを使用します。

- `--cache-backend=redis` redis のデフォルトキャッシュを有効にします。 この機能が既に有効になっている場合は、このパラメーターを省略します。

- `--cache-backend-redis-<parameter>=<value>` は、デフォルトのキャッシュを設定するキーと値のペアのリストです。

| コマンドラインパラメーター | 値 | 意味 | デフォルト値 |
| ------------------------------ | --------- | ------- | ------------- |
| `cache-backend-redis-server` | サーバー | 完全修飾ホスト名、IP アドレス、または UNIX ソケットへの絶対パス。 デフォルト値の 127.0.0.1 は、Redis がCommerce サーバーにインストールされていることを示します。 | `127.0.0.1` |
| `cache-backend-redis-port` | ポート | Redis サーバーリッスンポート | `6379` |
| `cache-backend-redis-db` | データベース | デフォルトキャッシュとフルページキャッシュの両方に Redis を使用する場合は必須です。 一方のキャッシュのデータベース番号を指定する必要があります。もう一方のキャッシュは、デフォルトで 0 を使用します。<br><br>**重要**：複数のタイプのキャッシュに Redis を使用する場合は、データベース番号は異なる必要があります。 デフォルトのキャッシュ データベース番号を 0、ページ キャッシュ データベース番号を 1、セッション ストレージ データベース番号を 2 に割り当てることをお勧めします。 | `0` |
| `cache-backend-redis-password` | password | Redis パスワードを設定すると、組み込みのセキュリティ機能の 1 つが有効になります。 `auth` コマンド。データベースにアクセスするためにクライアントの認証が必要です。 パスワードは Redis の設定ファイルで直接設定されます。 `/etc/redis/redis.conf` | |

### コマンドの例

次の例では、Redis のデフォルトキャッシュを有効にし、ホストをに設定します。 `127.0.0.1`データベース番号を 0 に割り当てます。 Redis は他のすべてのパラメータにデフォルト値を使用します。

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=127.0.0.1 --cache-backend-redis-db=0
```

## Redis ページキャッシュの設定

Commerceで Redis ページキャッシュを設定するには、 `setup:config:set` コマンドと追加のパラメーター。

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-<parameter>=<value>...
```

次のパラメーターを使用します。

- `--page-cache=redis` redis ページキャッシュを有効にします。 この機能が既に有効になっている場合は、このパラメーターを省略します。

- `--page-cache-redis-<parameter>=<value>` は、ページキャッシュを設定するキーと値のペアのリストです。

| コマンドラインパラメーター | 値 | 意味 | デフォルト値 |
| ------------------------------ | --------- | ------- | ------------- |
| `page-cache-redis-server` | サーバー | 完全修飾ホスト名、IP アドレス、または UNIX ソケットへの絶対パス。 デフォルト値の 127.0.0.1 は、Redis がCommerce サーバーにインストールされていることを示します。 | `127.0.0.1` |
| `page-cache-redis-port` | ポート | Redis サーバーリッスンポート | `6379` |
| `page-cache-redis-db` | データベース | デフォルトおよびフルページキャッシュの両方に Redis を使用する場合は必須です。 一方のキャッシュのデータベース番号を指定する必要があります。もう一方のキャッシュは、デフォルトで 0 を使用します。<br/>**重要**：複数のタイプのキャッシュに Redis を使用する場合は、データベース番号は異なる必要があります。 デフォルトのキャッシュ データベース番号を 0、ページ キャッシュ データベース番号を 1、セッション ストレージ データベース番号を 2 に割り当てることをお勧めします。 | `0` |
| `page-cache-redis-password` | password | Redis パスワードを設定すると、組み込みのセキュリティ機能の 1 つが有効になります。 `auth` コマンド。データベースにアクセスするためにクライアントの認証が必要です。 Redis 設定ファイル内でパスワードを設定します。 `/etc/redis/redis.conf` | |

### コマンドの例

次の例では、Redis ページキャッシュを有効にし、ホストをに設定します。 `127.0.0.1`データベース番号を 1 に割り当てます。 その他のパラメーターはすべてデフォルト値に設定されます。

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-redis-db=1
```

## 結果

2 つのコマンド例の結果、Commerceによって次のような行が追加されます。 `<Commerce-install-dir>app/etc/env.php`:

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

Commerce 2.4.3 以降、Amazon EC2 でホストされるインスタンスは、ローカル Redis インスタンスの代わりにAWS ElastiCache を使用する場合があります。

>[!WARNING]
>
>このセクションは、Amazon EC2 VPC 上で動作するCommerce インスタンスに対してのみ機能します。 オンプレミスのインストールでは機能しません。

### Redis クラスターの設定

後 [AWSでの Redis クラスターの設定](https://aws.amazon.com/getting-started/hands-on/setting-up-a-redis-cluster-with-amazon-elasticache/)を選択し、ElastiCache を使用するように EC2 インスタンスを設定します。

1. [ElastiCache クラスターの作成](https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/set-up.html) EC2 インスタンスと同じリージョンおよび VPC 内。
1. 接続を確認します。

   - EC2 インスタンスへの SSH 接続を開きます。
   - EC2 インスタンスに、Redis クライアントをインストールします。

     ```bash
     sudo apt-get install redis
     ```

   - EC2 セキュリティグループにインバウンド規則を追加します：タイプ `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - ElastiCache クラスターセキュリティ グループに受信規則を追加します：タイプ `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Redis CLI に接続します。

     ```bash
     redis-cli -h <ElastiCache Primary Endpoint host> -p <ElastiCache Primary Endpoint port>
     ```

### クラスターを使用するようにCommerceを設定します

Commerceでは、複数のタイプのキャッシュ設定をサポートしています。 一般に、キャッシュ設定はフロントエンドとバックエンドに分かれます。 フロントエンドキャッシュは次のように分類されます `default`（任意のキャッシュタイプに使用）。 パフォーマンスを向上させるには、カスタマイズするか、下位レベルのキャッシュに分割します。 一般的な Redis 設定は、デフォルトのキャッシュとページキャッシュを独自の Redis データベース（RDB）に分離することです。

実行 `setup` redis エンドポイントを指定するコマンド。

Commerceを Redis 用にデフォルトキャッシュとして設定するには：

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=<ElastiCache Primary Endpoint host> --cache-backend-redis-port=<ElastiCache Primary Endpoint port> --cache-backend-redis-db=0
```

Commerceを Redis ページキャッシュ用に設定するには：

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=<ElastiCache Primary Endpoint host> --page-cache-redis-port=<ElastiCache Primary Endpoint port> --page-cache-redis-db=1
```

セッションストレージに Redis を使用するようにCommerceを設定するには：

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=<ElastiCache Primary Endpoint host> --session-save-redis-port=<ElastiCache Primary Endpoint port> --session-save-redis-log-level=4 --session-save-redis-db=2
```

### 接続の検証

**Commerceが ElastiCache と通信していることを確認するには**:

1. Commerce EC2 インスタンスへの SSH 接続を開きます。
1. Redis モニタを起動します。

   ```bash
   redis-cli -h <ElastiCache-Primary-Endpoint-host> -p <ElastiCache-Primary-Endpoint-port> monitor
   ```

1. Commerce UI でページを開きます。
1. を確認 [キャッシュ出力](#verify-redis-connection) ターミナルの中で。

## 新しい Redis キャッシュの実装

Commerce 2.3.5 以降では、拡張 Redis キャッシュ実装を使用することをお勧めします。 `\Magento\Framework\Cache\Backend\Redis`.

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

## Redis プリロード機能

Commerceは設定データを Redis キャッシュに保存するので、ページ間で再利用されるデータをプリロードできます。 プリロードする必要があるキーを見つけるには、Redis からCommerceに転送されるデータを分析します。 次のような各ページに読み込まれるデータをプリロードすることをお勧めします。 `SYSTEM_DEFAULT`, `EAV_ENTITY_TYPES`, `DB_IS_UP_TO_DATE`.

Redis は `pipeline` 読み込みリクエストを複合するために使用します。 キーにはデータベースのプレフィックスを含める必要があります。例えば、データベースのプレフィックスが `061_`の場合、プリロードキーは次のようになります。 `061_SYSTEM_DEFAULT`

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

L2 キャッシュでプリロード機能を使用する場合は、を追加することを忘れないでください。 `:hash` l2 キャッシュはデータ自体ではなく、データのハッシュのみを転送するので、キーにサフィックスが付きます。

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

## 並列生成

2.4.0 リリースからは、 `allow_parallel_generation` ロックの待機を排除したいユーザーのためのオプション。
デフォルトでは無効になっているので、過剰な設定やブロックが発生するまで無効にすることをお勧めします。

**並列生成を使用可能にする手順は、次のとおりです**:

```bash
bin/magento setup:config:set --allow-parallel-generation
```

フラグなので、コマンドで無効にすることはできません。 設定値を手動でに設定する必要があります `false`:

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

Redis とCommerceが連携していることを確認するには、Redis を実行しているサーバにログインし、ターミナルを開いて Redis monitor コマンドまたは ping コマンドを使用します。

### Redis モニターコマンド

```bash
redis-cli monitor
```

ページキャッシュの出力例：

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

両方のコマンドが成功すると、Redis が正しく設定されます。

### 圧縮データの検査

圧縮されたセッションデータとページキャッシュを検査するには、次の手順に従います。 [RESP.app](https://flathub.org/apps/details/app.resp.RESP) は、Commerce 2 セッションおよびページキャッシュの自動解凍をサポートしており、PHP セッションデータを人間が読み取り可能な形式で表示します。
