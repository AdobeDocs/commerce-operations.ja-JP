---
title: デフォルトおよびページキャッシュのValkeyの設定
description: Adobe CommerceのデフォルトおよびページキャッシュバックエンドとしてValkeyを設定する方法について説明します。 CLI コマンド、env.php設定、接続検証を確認します。
feature: Configuration, Cache
exl-id: d0baa2a6-8aa8-4f3f-9edf-102d621430e0
badgePaas: label="オンプレミス" type="Informative" url="https://experienceleague.adobe.com/ja/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce オンプレミス プロジェクトにのみ適用されます。"
autotag-review: '2026-06-22T22:00:55.389Z'
TQID: 'https://experienceleague.adobe.com/AjJ86dYGRVFuY1T73ct1Gpcf6iDbb4ewP8OiGX8otQs'
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
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 1281
ht-degree: 0%

---


# デフォルトおよびページキャッシュのValkeyの設定

Commerceには、Valkeyのデフォルトとページキャッシュを設定するためのコマンドラインオプションが用意されています。 `<Commerce-install-dir>app/etc/env.php` ファイルを編集してキャッシュを設定できますが、特に初期設定では、コマンドラインを使用することをお勧めします。 コマンドラインは検証を提供し、設定が構文的に正しいことを確認します。

{{cloud-cache-config}}

**前提条件：**

続行する前に[Valkey](config-valkey.md#install-valkey)をインストールします。

## サポートされているフレームワーク

>[!BEGINTABS]

>[!TAB Zend キャッシュ （2.4.8以前） ]

- **Zend Cache （2.4.8以前）** — Commerce 2.4.8以前の以前のValkey バックエンド：
   - **Legacy Valkey backend** – 完全なクラス パス （`Magento\Framework\Cache\Backend\Valkey`）を使用します
   - **プリロード キー** – 頻繁に使用するキャッシュ キーのプリロードをサポート
   - **Lua スクリプト** — ガベージコレクション用Lua
   - **圧縮** — データ圧縮をサポート

>[!TAB Symfony キャッシュ （2.4.9+） ]

- **Symfony Cache （2.4.9+）** — Commerce 2.4.9以降、Symfony CacheはValkeyに最新のPSR-6準拠キャッシュ実装を提供し、大幅なパフォーマンス向上を実現しました。
   - **自動バルキーパイプライン** – 複数の操作を単一のリクエストにバッチ処理して、待ち時間を短縮します
   - **PSR-6 TagAwareAdapter** — アトミックオペレーションによる効率的なタグベースのキャッシュ無効化
   - **Igbinary serialization** — バイナリのシリアル化により、キャッシュ エントリ サイズが45%削減され、速度が5 ～ 10%向上します
   - **永続的な接続の強化** – より安定した接続プールと、フォークされたプロセスの処理の改善
   - **最適化されたLua スクリプト** — サーバーサイドの実行とパイプライン処理を組み合わせて、効率を最大化

>[!ENDTABS]

## Valkeyのデフォルトキャッシュの設定

`setup:config:set` コマンドを実行し、Valkeyの既定のキャッシュのパラメーターを指定します。

```shell
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-<parameter>=<value>...
```

- `--cache-backend=valkey`は、Valkeyの既定のキャッシュを有効にします。 この機能が既に有効になっている場合は、このパラメーターを省略します。

- `--cache-backend-valkey-<parameter>=<value>`は、デフォルトのキャッシュを設定するキーと値のペアのリストです。

{{valkey-redis-cli-note}}

| コマンドラインパラメーター | 値 | 意味 | デフォルト値 |
|---------------------------------| --------- |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `cache-backend-valkey-server` | サーバー | 完全修飾ホスト名、IP アドレス、またはUNIX ソケットへの絶対パス。 デフォルト値`127.0.0.1`は、ValkeyがCommerce サーバーにインストールされていることを示します。 | `127.0.0.1` |
| `cache-backend-valkey-port` | ポート | Valkey サーバーのリッスン ポート | `6379` |
| `cache-backend-valkey-db` | データベース | デフォルトとページ全体のキャッシュの両方にValkeyを使用する場合は必須です。 いずれかのキャッシュのデータベース番号を指定します。他のキャッシュはデフォルトで`0`を使用します。<br><br>**重要**: Valkeyを複数のタイプのキャッシュに使用する場合、データベース番号は異なる必要があります。 Adobeでは、デフォルトのキャッシュ データベース番号を`0`に、ページ キャッシュ データベース番号を`1`に、セッション ストレージ データベース番号を`2`に割り当てることをお勧めします。 | `0` |
| `cache-backend-valkey-password` | パスワード | Valkey パスワードを設定すると、組み込みのセキュリティ機能の1つである`auth` コマンドが有効になり、クライアントはデータベースにアクセスするために認証する必要があります。 パスワードは、Valkeyの設定ファイル `/etc/valkey/valkey.conf`で直接設定されます | |
| `cache-backend-valkey-use-lua` | use_lua | LUAを有効または無効にします。 <br><br>**LUA**: Luaを使用すると、Valkey内でアプリケーションロジックの一部を実行できるようになり、パフォーマンスが向上し、アトミックな実行を通じてデータの一貫性が確保されます。 | `0` |
| `cache-backend-valkey-use-lua-on-gc` | use_lua_on_gc | ガベージコレクションのLUAを有効または無効にします。 <br><br>**LUA**: Luaを使用すると、Valkey内でアプリケーションロジックの一部を実行できるようになり、パフォーマンスが向上し、アトミックな実行を通じてデータの一貫性が確保されます。 | `1` |

## コマンドの例（デフォルトのキャッシュ）

次の例では、Valkeyのデフォルトのキャッシュを有効にし、ホストを`127.0.0.1`に設定し、データベース番号を`0`に割り当てます。 Valkeyは、他のすべてのパラメーターにデフォルト値を使用します。

```shell
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-server=127.0.0.1 --cache-backend-valkey-db=0
```

{{valkey-redis-cli-note}}

## Valkey ページキャッシュの設定

CommerceでValkey ページキャッシュを設定するには、パラメーターを追加して`setup:config:set` コマンドを実行します。

```shell
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-<parameter>=<value>...
```

次のパラメーターを使用します。

- `--page-cache=valkey`はValkey ページのキャッシュを有効にします。 この機能が既に有効になっている場合は、このパラメーターを省略します。

- `--page-cache-valkey-<parameter>=<value>`は、ページキャッシュを設定するキーと値のペアのリストです。

| コマンドラインパラメーター | 値 | 意味 | デフォルト値 |
|----------------------------------------| --------- |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `page-cache-valkey-server` | サーバー | 完全修飾ホスト名、IP アドレス、またはUNIX ソケットへの絶対パス。 デフォルト値`127.0.0.1`は、ValkeyがCommerce サーバーにインストールされていることを示します。 | `127.0.0.1` |
| `page-cache-valkey-port` | ポート | Valkey サーバーのリッスン ポート。 | `6379` |
| `page-cache-valkey-db` | データベース | デフォルトとフルページの両方のキャッシュにValkeyを使用する場合は必須です。 いずれかのキャッシュのデータベース番号を指定します。他のキャッシュはデフォルトで`0`を使用します。<br/>**重要**: Valkeyを複数のタイプのキャッシュに使用する場合、データベース番号は異なる必要があります。 既定のキャッシュ データベース番号を`0`に、ページ キャッシュ データベース番号を`1`に、セッション ストレージ データベース番号を`2`に割り当てることをお勧めします。 | `0` |
| `page-cache-valkey-password` | パスワード | Valkey パスワードを設定すると、組み込みのセキュリティ機能の1つである`auth` コマンドが有効になり、クライアントはデータベースにアクセスするために認証する必要があります。 Valkey設定ファイル内でパスワードを設定します：`/etc/valkey/valkey.conf` | |

### コマンドの例（ページキャッシュ）

次の例では、Valkey ページのキャッシュを有効にし、ホストを`127.0.0.1`に設定し、データベース番号を`1`に割り当てます。 その他のパラメーターはすべてデフォルト値に設定されます。

```shell
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-server=127.0.0.1 --page-cache-valkey-db=1
```

{{valkey-redis-cli-note}}

### Commerce環境設定の確認

Valkey キャッシュを構成するコマンドを実行すると、Commerce環境設定（`<Commerce-install-dir>app/etc/env.php`）が更新されます。

>[!BEGINTABS]

>[!TAB Zend キャッシュ （2.4.8以前） ]

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

>[!TAB Symfony キャッシュ （2.4.9+） ]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'valkey',
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

>[!NOTE]
>
>Commerce 2.4.9以降では、完全なクラスパスの代わりに、簡略化されたバックエンドタイプ `'backend' => 'valkey'`を使用します。 シンフォニーキャッシュは、簡略化された名前が指定されると自動的に使用されます。

>[!ENDTABS]

## その他のキャッシュオプションの設定

### Valkey プリロード機能

Commerceでは、設定データがValkey キャッシュに保存されるので、ページ間で再利用されるデータをプリロードできます。 プリロードする必要があるキーを見つけるには、ValkeyからCommerceに転送されるデータを分析します。 Adobeは、`SYSTEM_DEFAULT`、`EAV_ENTITY_TYPES`、`DB_IS_UP_TO_DATE`など、すべてのページに読み込まれるデータのプリロードを提案します。

Valkeyは`pipeline`を使用して読み込み要求を合成します。 キーには、データベースのプレフィックスを含める必要があります。例えば、データベースのプレフィックスが`061_`の場合、プリロードキーは`061_SYSTEM_DEFAULT`のようになります

>[!BEGINTABS]

>[!TAB Zend キャッシュ ]

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

>[!TAB Symfony キャッシュ ]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => '061_',
            'backend' => 'valkey',
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

>[!ENDTABS]

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

>[!BEGINTABS]

>[!TAB Zend キャッシュ ]

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
                'backend_options' => [
                    'server' => 'valkey',
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

>[!TAB Symfony キャッシュ ]

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'valkey',
                'backend_options' => [
                    'server' => 'valkey',
                    'database' => '0',
                    'port' => '6379',
                    'serializer' => 'igbinary',
                    'compress_data' => '1',
                    'compression_lib' => 'gzip'
                ]
            ],
            'page_cache' => [
                'id_prefix' => 'b0b_'
            ]
        ],
        'allow_parallel_generation' => false
    ],
```

>[!ENDTABS]

## Symfony Cacheのパフォーマンス最適化

Symfony Cacheを使用している場合は、Igbinary シリアライザーの設定、igbinary PHP拡張機能およびphpredis拡張機能のインストール、および永続的な接続の有効化により、パフォーマンスをさらに最適化できます。

### バイナリシリアライザー

Igbinary シリアライザーは、PHPのデフォルトのシリアル化よりもパフォーマンスを大幅に向上させます。 `app/etc/env.php`で手動で設定する必要があります：

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend_options' => [
                'server' => 'valkey',
                'database' => '0',
                'port' => '6379',
                'serializer' => 'igbinary',  // Enable Igbinary serialization
            ]
        ],
        'page_cache' => [
            'backend_options' => [
                'server' => 'valkey',
                'database' => '1',
                'port' => '6379',
                'serializer' => 'igbinary',  // Enable Igbinary for page cache too
            ]
        ]
    ]
]
```

### PHP Igbinary拡張機能のインストール

バイナリのシリアル化を使用するには、PHP Igbinary拡張機能をインストールする必要があります。

**aptを使用しています（Debian/Ubuntu向けに推奨）**:

```bash
sudo apt-get install php-igbinary
sudo systemctl restart php-fpm
php -m | grep igbinary
```

**PECL （代替メソッド）を使用**:

```bash
sudo pecl install igbinary
echo "extension=igbinary.so" | sudo tee /etc/php/8.3/mods-available/igbinary.ini
sudo phpenmod igbinary
sudo systemctl restart php-fpm
php -m | grep igbinary
```

### PHP Redis拡張機能：phpredisとPredis

Commerce 2.4.9以降では、phpredis （ネイティブ C拡張機能）とPredis （純粋なPHP ライブラリ）の間で自動フォールバックが行われます。 最適なパフォーマンスを得るには、phpredisをインストールしてください：

**aptを使用しています（Debian/Ubuntu向けに推奨）**:

```bash
sudo apt-get install php-redis
sudo systemctl restart php-fpm
php -m | grep redis
```

**PECL （代替メソッド）を使用**:

```bash
sudo pecl install redis
echo "extension=redis.so" | sudo tee /etc/php/8.3/mods-available/redis.ini
sudo phpenmod redis
sudo systemctl restart php-fpm
php -m | grep redis
```

**パフォーマンスの比較**:

| 操作 | Predis | phpredis | 改善 |
|-----------|--------|----------|-------------|
| Cache GET | 1 ～ 5 ミリ秒 | 0.5～2ms | 2～3倍高速 |
| キャッシュセット | 2～6 ミリ秒 | 0.8～2.5ms | 2～3倍高速 |
| タグ操作 | 10～30 ミリ秒 | 3～10 ミリ秒 | 3～4倍高速 |

### 永続的な接続

永続的な接続リクエストをまたいで既存のValkey接続を再利用することで、キャッシュ運用を5～15%高速化できます。 `app/etc/env.php`で設定：

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend_options' => [
                'server' => 'valkey',
                'database' => '0',
                'port' => '6379',
                'persistent' => '1',
                'persistent_id' => 'cache_default',
                'timeout' => '2.5',
                'read_timeout' => '2.0',
            ]
        ],
        'page_cache' => [
            'backend_options' => [
                'server' => 'valkey',
                'database' => '1',
                'port' => '6379',
                'persistent' => '1',
                'persistent_id' => 'cache_fpc',
            ]
        ]
    ]
]
```

>[!IMPORTANT]
>
>接続の競合を防ぐには、各キャッシュ タイプに一意の`persistent_id`を使用します。

### 最適化された設定を完了

以下は、すべてのパフォーマンス最適化を組み合わせた実稼動対応の設定です。

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => 'b0b_',
            'backend' => 'valkey',
            'backend_options' => [
                'server' => 'valkey',
                'database' => '0',
                'port' => '6379',
                'serializer' => 'igbinary',
                'compress_data' => '1',
                'compression_lib' => 'gzip',
                'persistent' => '1',
                'persistent_id' => 'cache_default',
                'timeout' => '2.5',
                'read_timeout' => '2.0',
                'use_lua' => '1',
                'use_lua_on_gc' => '1',
                'preload_keys' => [
                    'b0b_EAV_ENTITY_TYPES',
                    'b0b_GLOBAL_PLUGIN_LIST',
                    'b0b_DB_IS_UP_TO_DATE',
                    'b0b_SYSTEM_DEFAULT',
                ],
            ]
        ],
        'page_cache' => [
            'id_prefix' => 'b0b_',
            'backend' => 'valkey',
            'backend_options' => [
                'server' => 'valkey',
                'database' => '1',
                'port' => '6379',
                'serializer' => 'igbinary',
                'compress_data' => '0',
                'persistent' => '1',
                'persistent_id' => 'cache_fpc',
            ]
        ]
    ],
    'allow_parallel_generation' => false
]
```

## Valkey接続の検証

ValkeyとCommerceが正しく連携していることを確認するには：

1. ValkeyとCommerceを実行するサーバーにログインします。
1. ターミナルを開きます。
1. `valkey-cli monitor` コマンドまたは`valkey-cli ping` コマンドを使用して、接続を確認します。

コマンドが正常に実行された場合、Valkeyは実行中で、Commerce アプリケーションと通信できます。 それらが失敗した場合、ValkeyとCommerceの間に解決する必要がある接続の問題があります。

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

### 圧縮データの検査

圧縮されたセッション データとページ キャッシュを調べるには、[RESP.app](https://flathub.org/apps/app.resp.RESP) ツールを使用します。 Commerce 2のセッションデータとページキャッシュデータの自動解凍をサポートし、PHP セッションデータを人間が読める形式で表示します。

