---
title: デフォルトのキャッシュにValkeyを使用
description: ValkeyをAdobe Commerceのデフォルトキャッシュとして設定する方法について説明します。 コマンドラインのセットアップ、設定オプション、検証手法について説明します。
feature: Configuration, Cache
exl-id: d0baa2a6-8aa8-4f3f-9edf-102d621430e0
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '1084'
ht-degree: 0%

---


# デフォルトのキャッシュにValkeyを使用

Commerceには、Valkey ページとデフォルトのキャッシュを設定するためのコマンドラインオプションが用意されています。 `<Commerce-install-dir>app/etc/env.php` ファイルを編集してキャッシュを設定できますが、特に初期設定では、コマンドラインを使用することをお勧めします。 コマンドラインは検証を提供し、設定が構文的に正しいことを確認します。

続行する前に[Valkey](config-redis.md#install-redis)をインストールする必要があります。

## Valkeyのデフォルトキャッシュの設定

`setup:config:set` コマンドを実行し、Valkeyの既定のキャッシュのパラメーターを指定します。

```shell
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-<parameter>=<value>...
```

- `--cache-backend=valkey`は、valkeyの既定のキャッシュを有効にします。 この機能が既に有効になっている場合は、このパラメーターを省略します。

- `--cache-backend-valkey-<parameter>=<value>`は、デフォルトのキャッシュを設定するキーと値のペアのリストです。

>[!NOTE]
>
>**Adobe Commerce 2.4.9-alpha2**&#x200B;以降、**Valkey**&#x200B;は、ライセンスの変更により、CLI ツールのRedisを正式に置き換えました。 ValkeyはRedisのフォークであり、ほぼ同じ機能を維持しています。 **バージョン 2.4.8以前**&#x200B;の場合、Valkeyの設定に使用するCLI コマンドはRedisの場合と同じままとなり、シームレスな後方互換性を確保し、移行またはデュアル環境のサポートを簡素化します。 次の例は、Valkey固有のコマンドを示しています。

```shell
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-<parameter>=<value>...
```

| コマンドラインパラメーター | 値 | 意味 | デフォルト値 |
|---------------------------------| --------- |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `cache-backend-valkey-server` | サーバー | 完全修飾ホスト名、IP アドレス、またはUNIX ソケットへの絶対パス。 デフォルト値`127.0.0.1`は、ValkeyがCommerce サーバーにインストールされていることを示します。 | `127.0.0.1` |
| `cache-backend-valkey-port` | ポート | Valkey サーバーのリッスン ポート | `6379` |
| `cache-backend-valkey-db` | データベース | デフォルトとページ全体のキャッシュの両方にValkeyを使用する場合は必須です。 いずれかのキャッシュのデータベース番号を指定する必要があります。他のキャッシュはデフォルトで`0`を使用します。<br><br>**重要**: Valkeyを複数のタイプのキャッシュに使用する場合、データベース番号は異なる必要があります。 Adobeでは、デフォルトのキャッシュ データベース番号を`0`に、ページ キャッシュ データベース番号を`1`に、セッション ストレージ データベース番号を`2`に割り当てることをお勧めします。 | `0` |
| `cache-backend-valkey-password` | パスワード | Valkey パスワードを設定すると、組み込みのセキュリティ機能の1つである`auth` コマンドが有効になり、クライアントはデータベースにアクセスするために認証する必要があります。 パスワードは、Valkeyの設定ファイル `/etc/valkey/valkey.conf`で直接設定されます | |

### コマンド例

次の例では、Valkeyのデフォルトのキャッシュを有効にし、ホストを`127.0.0.1`に設定し、データベース番号を`0`に割り当てます。 Valkeyは、他のすべてのパラメーターにデフォルト値を使用します。

```shell
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-server=127.0.0.1 --cache-backend-valkey-db=0
```

>[!NOTE]
>
>**Adobe Commerce 2.4.9-alpha2**&#x200B;以降、**Valkey**&#x200B;は、ライセンスの変更により、CLI ツールのRedisを正式に置き換えました。 ValkeyはRedisのフォークであり、ほぼ同じ機能を維持しています。 **バージョン 2.4.8以前**&#x200B;の場合、Valkeyの設定に使用するCLI コマンドはRedisの場合と同じままとなり、シームレスな後方互換性を確保し、移行またはデュアル環境のサポートを簡素化します。 次の例は、Valkey固有のコマンドを示しています。

```shell
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=127.0.0.1 --cache-backend-redis-db=0
```

## ページキャッシュの設定

CommerceでValkey ページキャッシュを設定するには、パラメーターを追加して`setup:config:set` コマンドを実行します。

```shell
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-<parameter>=<value>...
```

次のパラメーターを使用します。

- `--page-cache=valkey`はValkey ページのキャッシュを有効にします。 この機能が既に有効になっている場合は、このパラメーターを省略します。

- `--page-cache-valkey-<parameter>=<value>`は、ページキャッシュを設定するキーと値のペアのリストです。

>[!NOTE]
>
>**Adobe Commerce 2.4.9-alpha2**&#x200B;以降、**Valkey**&#x200B;は、ライセンスの変更により、CLI ツールのRedisを正式に置き換えました。 ValkeyはRedisのフォークであり、ほぼ同じ機能を維持しています。 **バージョン 2.4.8以前**&#x200B;の場合、Valkeyの設定に使用するCLI コマンドはRedisの場合と同じままとなり、シームレスな後方互換性を確保し、移行またはデュアル環境のサポートを簡素化します。 次の例は、Valkey固有のコマンドを示しています。

```shell
bin/magento setup:config:set --page-cache=redis --page-cache-redis-<parameter>=<value>...
```

| コマンドラインパラメーター | 値 | 意味 | デフォルト値 |
|------------------------------| --------- |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `page-cache-valkey-server` | サーバー | 完全修飾ホスト名、IP アドレス、またはUNIX ソケットへの絶対パス。 デフォルト値`127.0.0.1`は、ValkeyがCommerce サーバーにインストールされていることを示します。 | `127.0.0.1` |
| `page-cache-valkey-port` | ポート | Valkey サーバーのリッスン ポート。 | `6379` |
| `page-cache-valkey-db` | データベース | デフォルトとフルページの両方のキャッシュにValkeyを使用する場合は必須です。 いずれかのキャッシュのデータベース番号を指定する必要があります。他のキャッシュはデフォルトで`0`を使用します。<br/>**重要**: Valkeyを複数のタイプのキャッシュに使用する場合、データベース番号は異なる必要があります。 既定のキャッシュ データベース番号を`0`に、ページ キャッシュ データベース番号を`1`に、セッション ストレージ データベース番号を`2`に割り当てることをお勧めします。 | `0` |
| `page-cache-valkey-password` | パスワード | Valkey パスワードを設定すると、組み込みのセキュリティ機能の1つである`auth` コマンドが有効になり、クライアントはデータベースにアクセスするために認証する必要があります。 Valkey設定ファイル内でパスワードを設定します：`/etc/valkey/valkey.conf` | |

### コマンド例

次の例では、Valkey ページのキャッシュを有効にし、ホストを`127.0.0.1`に設定し、データベース番号を`1`に割り当てます。 その他のパラメーターはすべてデフォルト値に設定されます。

```shell
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-server=127.0.0.1 --page-cache-valkey-db=1
```

>[!NOTE]
>
>**Adobe Commerce 2.4.9-alpha2**&#x200B;以降、**Valkey**&#x200B;は、ライセンスの変更により、CLI ツールのRedisを正式に置き換えました。 ValkeyはRedisのフォークであり、ほぼ同じ機能を維持しています。 **バージョン 2.4.8以前**&#x200B;の場合、Valkeyの設定に使用するCLI コマンドはRedisの場合と同じままとなり、シームレスな後方互換性を確保し、移行またはデュアル環境のサポートを簡素化します。 次の例は、Valkey固有のコマンドを示しています。

```shell
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-valkey-db=1
```

## 成果

2つの例コマンドの結果として、Commerceは次のような行を`<Commerce-install-dir>app/etc/env.php`に追加します。

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
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

## 新しいValkey キャッシュの実装

[!BADGE 2.4.9-alpha]{type=Negative tooltip="2.4.9-alphaでのみ使用できます。"}

Adobe Commerce 2.4.9以降、Adobeでは、Valkey キャッシュ実装を使用することをお勧めします：`\Magento\Framework\Cache\Backend\Valkey`。

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\Valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
],
```

## Valkey プリロード機能

Commerceでは、設定データがValkey キャッシュに保存されるので、ページ間で再利用されるデータをプリロードできます。 プリロードする必要があるキーを見つけるには、ValkeyからCommerceに転送されるデータを分析します。 Adobeは、`SYSTEM_DEFAULT`、`EAV_ENTITY_TYPES`、`DB_IS_UP_TO_DATE`など、すべてのページに読み込まれるデータのプリロードを提案します。

Valkeyは`pipeline`を使用して読み込み要求を合成します。 キーにはデータベースのプレフィックスを含める必要があります。例えば、データベースのプレフィックスが`061_`の場合、プリロードキーは`061_SYSTEM_DEFAULT`のようになります

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => '061_',
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
            'backend_options' => [
                'server' => 'valkey',
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

## 並列生成

Commerce 2.4.0 リリース以降、Adobeでは、ロックの待ち時間を排除したいユーザーに対して`allow_parallel_generation` オプションが導入されました。
デフォルトでは無効になっています。Adobeでは、過剰な設定やブロックがあるまで無効にすることをお勧めします。

**並列生成を有効にするには**:

```shell
bin/magento setup:config:set --allow-parallel-generation
```

フラグなので、コマンドで無効にすることはできません。 設定値を手動で`false`に設定する必要があります：

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
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

## Valkey接続の検証

ValkeyとCommerceが正常に連携していることを確認するには、Valkeyを実行するサーバーにログインしてターミナルを開き、`valkey-cli monitor` コマンドまたは`redis-cli ping` コマンドを使用します。

### Valkey monitor コマンド

```shell
valkey-cli monitor
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

### Valkey ping コマンド

```shell
valkey-cli ping
```

予想される応答は`PONG`です

両方のコマンドが成功した場合、Valkeyは適切に設定されます。

### 圧縮されたデータの検査

圧縮されたセッションデータとページキャッシュを調べるために、[RESP.app](https://flathub.org/apps/app.resp.RESP)は、Commerce 2のセッションとページキャッシュの自動解凍をサポートし、PHP セッションデータを人間が読み取り可能な形式で表示します。
