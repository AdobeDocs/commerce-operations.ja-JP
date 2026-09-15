---
title: パフォーマンス最適化のためのL2 キャッシュ設定
description: Adobe Commerce オンプレミスでL2 キャッシュを設定して、ネットワークトラフィックを削減し、パフォーマンスを向上させる方法を説明します。 従来のRemoteSynchronizedCache実装と最新のSymfony L2実装を比較します。
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
badgePaas: label="オンプレミス" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce オンプレミス プロジェクトにのみ適用されます。"
TQID: 'https://experienceleague.adobe.com/7vswBqyn9UZLmaeirgPRZ4xEQH5F66XUEtY5hPkz9NY'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
    internal-label: Compliance
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
    internal-label: Architecture
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
    internal-label: Optimization
source-git-commit: ea07c4a7e42988b2ede3511273261fa7d560b652
workflow-type: tm+mt
source-wordcount: '1686'
ht-degree: 0%
---
# パフォーマンス最適化のためのL2 キャッシュ設定

L2 （2 レベル）キャッシュでは、各web ノードにローカルキャッシュレイヤーを追加することで、リモートキャッシュサービスとCommerce アプリケーション間のネットワークトラフィックを削減します。 標準のCommerce インスタンスでは、リクエストごとに約300 KBを転送できます。 リクエスト量が多い場合、ネットワークトラフィックは大きくなる可能性があります。

L2 キャッシュでは、各web ノードは頻繁にアクセスされるデータをローカルに保存し、次の2つの目的でリモートキャッシュを使用します。

- キャッシュデータのバージョンを確認して、最新のキャッシュがローカルに保存されていることを確認する
- 更新されたキャッシュデータをリモートキャッシュサービスからローカルマシンに転送する

Commerceは、ハッシュ化されたデータバージョンをリモートキャッシュに保存し、サフィックス `:hash`を通常のキーに追加します。 ローカルキャッシュが古くなると、データはキャッシュアダプタを介してリモートキャッシュサービスから取得されます。

使用可能なL2 キャッシュの実装は、Commerceのバージョンとパッチレベルによって異なります。

| 導入 | Commerce版 | リモートキャッシュサービス | 説明 |
| -------------- | ---------------- | -------------------- | ----------- |
| [`RemoteSynchronizedCache`](#remotesynchronizedcache-l2-cache-configuration) | 2.4.9より前（サポートされている場合） | リリースとパッチレベルに応じて、RedisまたはValkey | ローカルストレージ用の`Cm_Cache_Backend_File`を含むZend ベースの2 レベルキャッシュ |
| [Symfony L2 （`symfony_l2`） &#x200B;](#symfony-l2-cache-implementation) | 2.4.9以降 | バルキー | PSR-6準拠の最新のSymfony Cache ベースのL2実装 |

## RemoteSynchronizedCache L2 キャッシュ設定


>[!NOTE]
>
>この節では、2.4.9より前のAdobe Commerce オンプレミス版の`RemoteSynchronizedCache` L2設定について説明します。このバージョンは、正確なCommerce リリースとパッチレベルのサポート マトリックスでサポートされています。
>
>Adobe Commerce 2.4.9以降では、[Symfony L2 キャッシュ &#x200B;](#symfony-l2-cache-implementation)でValkeyを使用します。
>
>Adobe Commerce on Cloud インフラストラクチャの場合、`.magento.env.yaml`のデプロイメント変数を使用してL2 キャッシュを設定します。 `app/etc/env.php`を直接編集しないでください。 [L2 キャッシュの設定](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-l2-cache)を参照してください。

キャッシュの設定手順は、Commerceのバージョンによって異なります。

RedisをサポートするAdobe Commerce オンプレミス バージョンの場合、次の例を使用して、`app/etc/env.php` ファイルの既存のキャッシュ セクションを変更または置き換えます。

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
            'backend_options' => [
                'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                'remote_backend_options' => [
                    'persistent' => 0,
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                ],
                'local_backend' => 'Cm_Cache_Backend_File',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/'
                ]
            ],
            'frontend_options' => [
                'write_control' => false,
            ],
        ]
    ],
    'type' => [
        'default' => ['frontend' => 'default'],
    ],
]
```

どこで：

- `backend`はL2 キャッシュ実装です。
- `backend_options`はL2 キャッシュ設定です。
  - `remote_backend`は、Commerce リリースとパッチレベルのサポートに応じて、RedisまたはValkeyのリモートキャッシュ実装です。
  - `remote_backend_options`はリモート キャッシュ設定です。
  - `local_backend`はローカル キャッシュ実装です：`Cm_Cache_Backend_File`。
  - `local_backend_options`はローカル キャッシュ設定です。
  - `cache_dir`は、ローカルキャッシュが保存されるディレクトリを定義するファイルキャッシュ固有のオプションです。

RedisまたはValkeyをサポートする2.4.9より前のAdobe Commerce バージョンの場合、Adobeでは、正確なリリースでサポートされているように、リモートキャッシュにはRedisまたはValkeyを使用し、ローカルキャッシュには`Cm_Cache_Backend_File`を使用することをお勧めします。 ローカルキャッシュは、通常、`/dev/shm/`などの一時ファイルシステムに保存されます。

```php
'local_backend_options' => [
    'cache_dir' => '/dev/shm/'
]
```

Adobeでは、Redisの負荷を軽減するため、`[cache preload](redis-pg-cache.md#redis-preload-feature)`機能の使用をお勧めします。 プリロード キーのサフィックス `:hash`を追加してください。

## 古いキャッシュオプション

Commerce 2.4以降、`use_stale_cache` オプションは、以前にキャッシュされたデータを処理し、新しいキャッシュデータを並行プロセスで生成することで、特定の場合のパフォーマンスを向上させることができます。 この節で説明する推奨キャッシュの種類とトレードオフは、`RemoteSynchronizedCache`と`symfony_l2`の両方の実装に適用されます。 `symfony_l2`の設定例については、[古いキャッシュを持つSymfony L2 キャッシュ &#x200B;](#symfony-l2-cache-with-stale-cache)を参照してください。

一般的に、ロック待ちのトレードオフは、パフォーマンスの観点から許容されます。 ただし、ブロック数やキャッシュエントリ数が増えると、ロック待ちに時間がかかります。 一部のシナリオでは、プロセスの待機時間は最大&#x200B;**キー数** x **検索タイムアウト**&#x200B;です。 まれに、ユーザーが`Block/Config` キャッシュに数百のキーを持つことがあるため、ロックの小さなルックアップタイムアウトでも数秒かかる場合があります。

>[!IMPORTANT]
>
>古いキャッシュはL2 キャッシュでのみ機能します。 有効にするには、L2 キャッシュフロントエンドのトップレベル設定に`'use_stale_cache' => true`を追加します。

Adobeでは、`use_stale_cache` オプションを有効にすることをお勧めします。これには、次のようなキャッシュタイプが最も利用されます。

- `block_html`
- `config_integration_api`
- `config_integration`
- `full_page`
- `layout`
- `reflection`
- `translate`

Adobeでは、`default` キャッシュタイプに`use_stale_cache` オプションを有効にすることはお勧めしません。

次のコードは、`RemoteSynchronizedCache` バックエンドの設定例を示しています。 `symfony_l2`の例については、[古いキャッシュを持つSymfony L2 キャッシュ &#x200B;](#symfony-l2-cache-with-stale-cache)を参照してください。

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
            'backend_options' => [
                'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                'remote_backend_options' => [
                    'persistent' => 0,
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                ],
                'local_backend' => 'Cm_Cache_Backend_File',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/'
                ]
            ],
            'frontend_options' => [
                'write_control' => false,
            ],
        ],
         'stale_cache_enabled' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
            'backend_options' => [
                'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                'remote_backend_options' => [
                    'persistent' => 0,
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
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
],
```

## Symfony L2 キャッシュ実装

Commerce バージョン 2.4.9以降では、`RemoteSynchronizedCache`の代わりにSymfony L2 キャッシュ実装（`symfony_l2` バックエンド）を使用します。 Symfony L2 キャッシュは、Valkeyを使用してPSR-6準拠のキャッシュ実装を提供します。

>[!IMPORTANT]
>
>Redisは、次のAdobe Commerce リリースのキャッシュ設定ではサポートされていません。
>
>- Adobe Commerce 2.4.9以降
>- Adobe Commerce 2.4.8-p4以降のパッチ
>- Adobe Commerce 2.4.7-p9以降のパッチ
>- Adobe Commerce 2.4.6-p14以降のパッチ
>- Adobe Commerce 2.4.5-p16以降のパッチ
>
>これらのリリースでは、Valkeyを設定します。
>
>Adobe Commerce 2.4.9以降でL2 キャッシュ用に`symfony_l2`を設定する場合は、リモート キャッシュ サービスにValkeyを使用する必要があります。 [Valkeyの設定](config-valkey.md)を参照してください。

### RemoteSynchronizedCacheからSymfony L2への移行

オンプレミスのインストールを`RemoteSynchronizedCache` バックエンドから`symfony_l2`にアップグレードする場合は、`app/etc/env.php`を更新する前に、次の点を確認してください。 `backend`値のみを変更するだけでは不十分です。 設定構造、キー名、および一部のデフォルト動作が異なります。

- **構成構造が変更されます。** `remote_backend`、`remote_backend_options`および`local_backend`は、`symfony_l2`の下で異なる値を使用しています。 例えば、`remote_backend`は完全修飾クラス名ではなく`'valkey'`になります。 既存の`RemoteSynchronizedCache`設定を編集するのではなく、以下の[設定の例](#configuration-example-with-symfony-l2-cache)を出発点として使用します。

- **`preload_keys`は`symfony_l2`.**&#x200B;では推奨されません `RemoteSynchronizedCache`設定に`preload_keys`が含まれている場合は、移行の一部として削除します。 キーのプリロードは`symfony_l2`のパフォーマンスを向上させず、追加の不要なキー検索をトリガーすることでValkeyの負荷を増やす可能性があります。

- **圧縮には明示的なフラグが必要です。** `compression_lib`のみを設定すると、`symfony_l2`の下で圧縮が有効になりません。 必要な`compress_data`設定については、[Symfony L2 キャッシュのバックエンドオプション &#x200B;](#backend-options-for-symfony-l2-cache)を参照してください。

- **手動で構成されたオンプレミスのデプロイメントでは、デフォルトで古いキャッシュが有効になっていません。** `use_stale_cache`のデフォルトは`symfony_l2`の`false`です（[&#x200B; バックエンドオプションの表](#backend-options-for-symfony-l2-cache)を参照）。 `RemoteSynchronizedCache`設定で`stale_cache_enabled` フロントエンドを使用している場合は、[Symfony L2 キャッシュのパターンを使用して、古いキャッシュ &#x200B;](#symfony-l2-cache-with-stale-cache)で明示的に再作成する必要があります。

>[!NOTE]
>
>`VALKEY_BACKEND: symfony_l2` デプロイ変数を設定するAdobe Commerce on Cloud環境には、`stale_cache_enabled` フロントエンドを含む完全なL2設定が`ece-tools`によって自動生成されます。 クラウド固有の動作については、[Symfony L2 キャッシュの設定](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-symfony-l2-cache)を参照してください。

- **Redisは、`symfony_l2`のサポートされているリモート バックエンドではありません。** この変更の一環としてValkeyに移行します。 [Valkeyの設定](config-valkey.md)を参照してください。

### Symfony L2 キャッシュを使用した設定例

>[!IMPORTANT]
>
>この`app/etc/env.php`の例は、オンプレミス インストールにのみ適用されます。 Adobe Commerce on Cloud インフラストラクチャの場合、`app/etc/env.php`を直接編集しないでください。 `VALKEY_BACKEND: symfony_l2`を`.magento.env.yaml`に設定します。 `ece-tools`は、展開中にL2 キャッシュ設定を生成して維持します。 [Symfony L2 キャッシュの設定](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-symfony-l2-cache)を参照してください。

`app/etc/env.php` ファイルで、L2 キャッシュに簡略化された`symfony_l2` バックエンド タイプを使用します。 この例には、`symfony_l2`では推奨されていない`preload_keys`設定は含まれていません。 詳しくは、[RemoteSynchronizedCacheからSymfony L2](#migrating-from-remotesynchronizedcache-to-symfony-l2)への移行を参照してください。

例では、`cleanup_percentage`を`90`に設定します。 デフォルト値は`95`です。 利用可能なローカルキャッシュストレージとCommerceのデプロイメントの要件に従って、この値を調整します。

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'symfony_l2',
            'backend_options' => [
                // L2 (Remote): Valkey with Symfony Cache
                'remote_backend' => 'valkey',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'compress_data' => '1',
                    'persistent_id' => 'magento_l2_default',
                    'timeout' => '2.5',
                    'read_timeout' => '2.0',
                    'use_lua' => '1',
                ],
                // L1 (Local): File cache
                'local_backend' => 'file',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/magento_l1'
                ],
                'cleanup_percentage' => 90,
            ],
        ]
    ],
    'type' => [
        'default' => ['frontend' => 'default'],
    ],
],
```

### Symfony L2 キャッシュと古いキャッシュ

どのキャッシュタイプが古いキャッシュから恩恵を受けるか、その理由については、[古いキャッシュオプション &#x200B;](#stale-cache-options)を参照してください。

次の例を使用して、`symfony_l2`個の古いキャッシュ サポート用に個別のフロントエンドを設定します。

```php
'cache' => [
    'frontend' => [
        // Default frontend: NO stale cache
        'default' => [
            'backend' => 'symfony_l2',
            'backend_options' => [
                'remote_backend' => 'valkey',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'compress_data' => '1',
                    'persistent_id' => 'magento_l2_default',
                ],
                'local_backend' => 'file',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/magento_l1'
                ],
            ],
        ],
        // Stale cache enabled frontend
        'stale_cache_enabled' => [
            'backend' => 'symfony_l2',
            'backend_options' => [
                'remote_backend' => 'valkey',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'compress_data' => '1',
                    'persistent_id' => 'magento_l2_stale',
                ],
                'local_backend' => 'file',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/magento_l1_stale'
                ],
                'use_stale_cache' => true,
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
        'translate' => ['frontend' => 'stale_cache_enabled'],
    ],
],
```

### Symfony L2 キャッシュのバックエンドオプション

| オプション | タイプ | Default | 説明 |
| -------- | ------ | --------- | ----------- |
| `remote_backend` | 文字列 | `'valkey'` | リモートキャッシュバックエンド： Symfony L2で`valkey`を使用します。 Redisは正式にはサポートされていません。 |
| `remote_backend_options` | 配列 | `[]` | Remote Valkey バックエンド設定 |
| `local_backend` | 文字列 | `'file'` | ローカル バックエンドの種類：`file`または`apcu` |
| `local_backend_options` | 配列 | `[]` | ローカルバックエンド設定 |
| `cleanup_percentage` | 整数 | `95` | L1 キャッシュのクリーンアップしきい値。1 ～ 100の割合で表されます |
| `use_stale_cache` | ブーリアン | `false` | フロントエンドの古いキャッシュを有効にします |
| `compress_data` | ブーリアン | `false` | `compression_lib`と組み合わせると圧縮を有効にします。 このオプションは、リモート Valkey バックエンドオプションで設定します。 |
| `persistent` | ブーリアン | `true` | リモートバックエンドへの永続的な接続を制御します。 Zend キャッシュの動作に一致するように`false` （`'0'`）に設定します。デフォルトは非永続的な接続です。 |

>[!NOTE]
>
>`frontend_options.write_control` オプションは`RemoteSynchronizedCache`設定に適用され、`symfony_l2`には適用されません。

### Symfony L2 キャッシュのパフォーマンスと信頼性の向上

>[!NOTE]
>
>これらの機能強化は、`symfony_l2`を使用したAdobe Commerce 2.4.9のデプロイメントに適用され、ACP2E-5132 パッチで利用できます。
>
>Adobe Commerce オンプレミスの場合は、品質パッチツール（QPT）を使用してこのパッチを適用します。 Adobe Commerce on Cloud インフラストラクチャの場合、パッチは`ece-tools`の依存関係であるCloud Patches for Commerce パッケージに含まれます。 デプロイメント中に最新のCloud パッチを受け取るには、最新バージョンの`ece-tools`にアップデートしてください。

最新のアップデートにより、Symfony L2 キャッシュのスケーラビリティが向上し、不要なファイルシステム I/Oが減り、キャッシュの一貫性と信頼性が向上しました。

#### 最適化されたSymfony L2 キャッシュタグストレージ

ValkeyがサポートするSymfony L2 キャッシュのデプロイメントの場合、キャッシュタグはValkeyにのみ保存されます。 これにより、冗長なファイルシステムのタグインデックス書き込みが不要になり、ディスク I/Oが減少し、`var/cache/symfony/tags/` ディレクトリが不要に増えるのを防ぐことができます。

#### ファイルベースのキャッシュ動作の改善

ファイルベースのキャッシュ（Valkeyを使用しない）を使用するデプロイメントの場合、ローカルタグインデックスは引き続き維持され、キャッシュの無効化がサポートされます。 タグインデックスは、以前にハードコードされた`var/cache`の場所ではなく、設定された`cache_dir`に書き込まれるようになりました。これにより、キャッシュディレクトリの使用状況が一貫し、カスタムキャッシュ設定のサポートが向上しました。

#### 再タグ化後の古いタグメンバーシップの修正

キャッシュエントリを再タグ化すると、そのエントリが属していないタグに関連付けられたままになります。 古いタグメンバーシップは再タグ時にクリアされるようになったため、キャッシュエントリは現在割り当てられているタグによってのみ無効化されます。

#### 変更されていない保存に対する冗長なリモート書き込み修正

変更されていないコンテンツを含むキャッシュエントリを保存すると、リモート（Valkey）バックエンドへの書き込みがトリガーされます。 コンテンツが変更されていないときに保存がスキップされ、不要なリモート書き込みが減少するようになりました。

#### L1 サイズベースの立ち退き修正（cleanup_percentage）

L1 サイズベースの立ち退きに使用されたしきい値`cleanup_percentage`は、常にトリガークリーンアップを実行できませんでした。 L1 キャッシュの削除が、設定済みの`cleanup_percentage`を正しく尊重するようになりました。

#### 古いキャッシュの再生ロック

`use_stale_cache`が有効になっていて、エントリのリモートコピーが一時的に利用できない場合、1つのプロセスのみが、そのエントリを再生成するために短時間のみ有効なロックを取得するようになりました。 同じエントリに対するその他の同時リクエストは、それ自体を再生成するのではなく、既存のローカル値を引き続き提供し、再生成スタンプードと冗長なバックエンド負荷を軽減します。

#### 効果

- ValkeyがサポートするSymfony L2 キャッシュのデプロイメントに対する冗長なファイルシステムのタグインデックス書き込みを排除し、ディスク I/Oを減らし、`var/cache/symfony/tags/` ディレクトリの不要な増加を防ぎます。
- ファイルベースのキャッシュのデプロイメントでは、キャッシュの無効化の動作を維持しながら、ローカルタグインデックス用に設定された`cache_dir`を一貫して使用します。
- 再タグ化後に残された古いタグメンバーシップによる誤ったキャッシュ無効化を防止します。
- 変更されていないキャッシュ保存に対する不要なリモート書き込みを減らし、ネットワークとバックエンドの負荷を軽減します。
- 設定された`cleanup_percentage`しきい値でL1 キャッシュの削除を確実にトリガーします。
- キーごとに1つのリジェネレーターを選択することで、`use_stale_cache`個のエントリの再生成スタンプを減らします。すべての同時リクエストでエントリを再構築する必要はありません。

設定オプションの詳細については、次を参照してください。

- [Symfony Cacheを使用したValkey キャッシュ設定](valkey-pg-cache.md)
