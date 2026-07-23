---
title: パフォーマンス最適化のためのL2 キャッシュ設定
description: Adobe CommerceでL2 キャッシュを設定して、ネットワークトラフィックを削減し、パフォーマンスを向上させる方法を説明します。 レガシーおよびSymfonyの実装オプションをご覧ください。
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
badgePaas: label="オンプレミス" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce オンプレミス プロジェクトにのみ適用されます。"
TQID: 'https://experienceleague.adobe.com/7vswBqyn9UZLmaeirgPRZ4xEQH5F66XUEtY5hPkz9NY'
product_v2: id: b974b164-8a4e-43b8-a9e2-8e67ec131677id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b5f00040-57a0-4a6d-a39e-383b1936c2c9id: dac87252-6066-4d6e-a9d2-f6d84c323de7id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: d9152906a6fbbd765a60e3aeacdbf7cc7527529d
workflow-type: tm+mt
source-wordcount: 1166
ht-degree: 0%

---

# パフォーマンス最適化のためのL2 キャッシュ設定

L2 （2 レベル）キャッシュでは、各web ノードにローカルキャッシュレイヤーを追加することで、リモートキャッシュストレージ（RedisまたはValkey）とCommerce アプリケーション間のネットワークトラフィックを削減します。 標準的なCommerce インスタンスでは、リクエストごとに約300 KBが転送され、状況によってはトラフィックが急速に増加して1,000 リクエストを超える場合があります。

L2 キャッシュでは、各web ノードは頻繁にアクセスされるデータをローカルに保存し、次の2つの目的でリモートキャッシュを使用します。

- キャッシュデータのバージョンを確認して、最新のキャッシュがローカルに保存されていることを確認する
- 更新されたキャッシュデータをリモートストアからローカルマシンに転送する

Commerceは、ハッシュ化されたデータバージョンをリモートキャッシュに保存し、サフィックス `:hash`を通常のキーに追加します。 ローカルキャッシュが古くなると、データはキャッシュアダプタを介してリモートマシンから取得されます。

使用可能なL2 キャッシュ実装は2つあります。

| 導入 | バージョン | 説明 |
| -------------- | ------- | ----------- |
| [ レガシー（`RemoteSynchronizedCache`） ](#legacy-l2-cache-configuration-remotesynchronizedcache) | &lt;2.4.9 | ローカルストレージ用の`Cm_Cache_Backend_File`を含むZend ベースの2 レベルキャッシュ |
| [最新（`symfony_l2`） ](#modern-symfony-l2-cache-implementation) | 2.4.9+ | PSR-6準拠のSymfony Cache ベースのL2とパフォーマンスの向上。 Valkeyのみをサポートします。 |

## 従来のL2 キャッシュ設定（RemoteSynchronizedCache）

>[!NOTE]
>
>従来のL2 キャッシュの設定手順は、古いバージョンのAdobe Commerceに適用されます。 Adobe Commerce バージョン 2.4.9以降を使用している場合は、[Symfony 2でValkeyを使用してL2 キャッシュ ](#modern-symfony-l2-cache-implementation)を実行します。

キャッシュ設定の手順は、デプロイメントタイプによって異なります。

- **Cloud**&#x200B;上のAdobe Commerceの場合、`.magento.env.yaml`で[`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend)または[`VALKEY_BACKEND`](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_backend) デプロイ変数を設定してL2 キャッシュを構成します。 設定例については、[L2 キャッシュの設定](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-l2-cache)を参照してください。

- **Redis**&#x200B;をサポートするAdobe Commerce オンプレミス バージョンの場合、次の例を使用して、`app/etc/env.php` ファイルの既存のキャッシュ セクションを変更または置換します。

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
  - `remote_backend`はリモート キャッシュ実装です：RedisまたはMySQL。
  - `remote_backend_options`はリモート キャッシュ設定です。
  - `local_backend`はローカル キャッシュ実装です：`Cm_Cache_Backend_File`
  - `local_backend_options`はローカル キャッシュ設定です。
  - `cache_dir`は、ローカルキャッシュが保存されているディレクトリのファイルキャッシュ固有のオプションです。

Adobe Commerce Adobeでは、次を使用して、リモート キャッシュ （`\Magento\Framework\Cache\Backend\Redis`）および`Cm_Cache_Backend_File`にRedisを使用することをお勧めします。共有メモリ内のデータのローカル キャッシュには、`'local_backend_options' => ['cache_dir' => '/dev/shm/']`を使用します

Adobeでは、Redisへの負荷を大幅に軽減するため、[`cache preload`](redis-pg-cache.md#redis-preload-feature)機能の使用をお勧めします。 プリロード キーのサフィックス &#39;:hash&#39;を追加することを忘れないでください。

## 古いキャッシュオプション

Commerce 2.4以降、`use_stale_cache` オプションは、以前にキャッシュされたデータを処理し、新しいキャッシュデータを並行プロセスで生成することで、特定の場合のパフォーマンスを向上させることができます。

一般的に、ロック待ちのトレードオフは、パフォーマンスの観点から許容されます。 ただし、ブロック数やキャッシュエントリ数が増えると、ロック待ちに時間がかかります。 一部のシナリオでは、プロセスの待機時間は最大&#x200B;**キー数** x **検索タイムアウト**&#x200B;です。 まれに、マーチャントが`Block/Config` キャッシュに数百のキーを持つことがあるため、ロックの小さなルックアップタイムアウトでも数秒かかる場合があります。

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

次のコードは、設定例を示しています。

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

## 最新のSymfony L2 キャッシュ実装

Commerce バージョン 2.4.9以降では、従来のL2 キャッシュの代わりにSymfony Cache ベースのL2 キャッシュ実装（`symfony_l2` バックエンド）を使用します。 Symfony L2 キャッシュは、PSR-6に準拠した最新のキャッシュ実装を提供し、従来の`RemoteSynchronizedCache`よりもパフォーマンスが大幅に向上しました。

>[!NOTE]
>
>Adobe Commerce on Cloudの場合、ECE ツールパッケージ （`ece-tools`）はこの設定を自動的に管理します。 `app/etc/env.php`を直接編集しないでください。デプロイメントによって手動での変更が上書きされます。 クラウド設定については、代わりに[Symfony L2 キャッシュの設定](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-symfony-l2-cache)を参照してください。

>[!IMPORTANT]
>
>{{redis-cache-support}}
>
>`symfony_l2`はAdobe Commerce 2.4.9以降でのみ使用できるため、Valkeyをリモートバックエンドとして設定します。 Redisは、`symfony_l2`の正式にサポートされているリモート バックエンドではありません。 リリース別のサポートされているキャッシュサービスについては、[必要システム構成](../../installation/system-requirements.md)を参照してください。

### Symfony L2 キャッシュのメリット

- **最新のアーキテクチャ**: Symfony Cache コンポーネント上に構築（PSR-6準拠）
- **パフォーマンスの向上**: Igbinaryのシリアル化、gzip圧縮、およびLua スクリプトのネイティブサポート
- **永続的な接続**：接続プールでValkey接続のオーバーヘッドを削減
- **キーのプリロード**：重要なデータのキャッシュ キーのプリロードをサポートしています
- **古いキャッシュ サポート**: `use_stale_cache` オプションとの完全な互換性
- **簡略化された設定**：よりクリーンなバックエンドの型名（`valkey`、`file`）

### Symfony L2 キャッシュを使用した設定例

L2 キャッシュに簡略化された`symfony_l2` バックエンドタイプを使用します。

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
                    'persistent_id' => 'magento_l2_default',
                    'timeout' => '2.5',
                    'read_timeout' => '2.0',
                    'use_lua' => '1',
                    'preload_keys' => [
                        'prefix_EAV_ENTITY_TYPES:hash',
                        'prefix_GLOBAL_PLUGIN_LIST:hash',
                        'prefix_DB_IS_UP_TO_DATE:hash',
                        'prefix_SYSTEM_DEFAULT:hash',
                    ],
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

古いキャッシュをサポートするように個別のフロントエンドを設定します。

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
|--------|------|---------|-------------------------------------------------------------------|
| `remote_backend` | 文字列 | `'valkey'` | リモート バックエンドの種類：`valkey`または`file` L2 キャッシュに`valkey`を使用します。 |
| `remote_backend_options` | 配列 | `[]` | リモートバックエンド設定（Valkey ドキュメントを参照） |
| `local_backend` | 文字列 | `'file'` | ローカル バックエンドの種類：`file`または`apcu` |
| `local_backend_options` | 配列 | `[]` | ローカルバックエンド設定 |
| `cleanup_percentage` | 整数 | `95` | L1 キャッシュ クリーンアップしきい値（1 ～ 100） |
| `use_stale_cache` | ブーリアン | `false` | 高可用性のために古いキャッシュを有効にする |

>[!NOTE]
>
>`remote_backend` オプションは`redis`の値も受け入れます。 ただし、Redisは、Adobe Commerce 2.4.9以降で正式にサポートされているキャッシュサービスではありません。 Adobeでは、`symfony_l2`を`valkey`のみで設定することをお勧めします。 リリース別のサポートされているキャッシュサービスについては、[必要システム構成](../../installation/system-requirements.md)を参照してください。

### Symfony L2 キャッシュのパフォーマンスと信頼性の向上

>[!NOTE]
>
>これらの機能強化は、`symfony_l2`を使用したAdobe Commerce 2.4.9のデプロイメントに適用され、ACP2E-5132 パッチで利用できます。 最新のパッチリリースノートについては、「[Commerceのクラウドパッチ ](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/release-notes/cloud-patches#latest)」を参照してください。

#### 最適化されたSymfony L2 キャッシュタグストレージ

冗長なファイルシステムタグインデックス書き込みを排除することで、Valkeyに基づくデプロイメント用にSymfony L2 キャッシュ動作を最適化しました。 キャッシュタグはValkeyにのみ保存されるようになり、Symfony L2のキャッシュ動作と従来のキャッシュ実装が一致するようになりました。 これにより、不要なディスク I/Oが減り、キャッシュの書き込みパフォーマンスが向上し、`var/cache/symfony/tags/` ディレクトリの拡張が妨げられます。

#### ファイルベースのキャッシュ動作の改善

ファイルベースのキャッシュ（Valkeyを使用しない）を使用するデプロイメントの場合、ローカルタグインデックスは引き続き維持され、キャッシュの無効化がサポートされます。 タグインデックスは、以前にハードコードされた`var/cache`の場所ではなく、設定された`cache_dir`に書き込まれるようになりました。これにより、キャッシュディレクトリの使用状況が一貫し、カスタムキャッシュ設定のサポートが向上しました。

#### キャッシュ無効化の改善

キャッシュの無効化では、適切なL1 タグのクリーンアップでTTL ベースの再生ロックが使用されるようになり、以前はタグの無効化の後に永続化していた古いキャッシュエントリが削除されるようになりました。

#### デフォルトで圧縮を有効にする

Redis/Valkey圧縮（`compress_data`）がSymfony L2 キャッシュに対してデフォルトで有効になり、メモリ消費とネットワークトラフィックが削減され、従来のキャッシュ実装のデフォルト動作と一致するようになりました。

#### 効果

- Valkeyに基づいたSymfony L2 キャッシュのデプロイメントに対する冗長なファイルシステムタグインデックスの書き込みを排除します。
- ディスク I/Oを減らし、キャッシュ書き込みパフォーマンスを向上させます。
- `var/cache/symfony/tags/` ディレクトリの不要な拡張を防ぎます。
- ファイルベースのキャッシュのデプロイメントでは、キャッシュの無効化の動作を維持しながら、設定された`cache_dir`を一貫して使用します。
- TTL ベースの再生ロックと適切なL1 タグクリーンアップにより、古いキャッシュエントリを削除します。
- デフォルトで`compress_data`が有効になっているため、メモリ消費とネットワークトラフィックが削減されます。

設定オプションの詳細については、次を参照してください。
- [Symfony Cacheを使用したValkey キャッシュ設定](valkey-pg-cache.md)

