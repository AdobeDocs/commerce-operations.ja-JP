---
title: L2 キャッシュ構成
description: L2 キャッシュの設定方法の説明。
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
source-git-commit: ba3c656566af47f16f58f476d7bc9f4781bb0234
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# L2 キャッシュ構成

キャッシュを使用すると、リモートキャッシュストレージとCommerce アプリケーションの間のネットワークトラフィックを減らすことができます。 標準のCommerce インスタンスは、リクエストあたり約 300 kb を転送するので、状況によっては、トラフィックが直ちに最大 1000 件のリクエストに増える可能性があります。

Redis へのネットワーク帯域幅を減らすには、キャッシュデータを各 Web ノードにローカルに保存し、次の 2 つの目的でリモートキャッシュを使用します。

- キャッシュデータのバージョンを確認し、最新のキャッシュがローカルに保存されていることを確認します
- リモート コンピューターからローカル コンピューターに最新のキャッシュを転送します

Commerceは、ハッシュ化されたデータバージョンを Redis に保存し、通常のキーにサフィックス「:hash」を追加します。 古いローカルキャッシュがある場合、データはキャッシュアダプターを使用してローカルマシンに転送されます。

>[!INFO]
>
>クラウドインフラストラクチャー上のAdobe Commerceの場合は、を使用できます [変数のデプロイ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) （L2 キャッシュ設定用）。

## 設定例

次の例を使用して、の既存のキャッシュセクションを変更または置換します `app/etc/env.php` ファイル。

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
],
```

ここで、

- `backend` は L2 キャッシュの実装です。
- `backend_options` は L2 キャッシュ構成です。
   - `remote_backend` はリモートキャッシュの実装です。Redis または MySQL です。
   - `remote_backend_options` はリモートキャッシュ設定です。
   - `local_backend` はローカルキャッシュの実装です。 `Cm_Cache_Backend_File`
   - `local_backend_options` はローカルキャッシュ設定です。
   - `cache_dir` は、ローカルキャッシュが保存されるディレクトリのファイルキャッシュ固有のオプションです。

Adobeでは、リモートキャッシュに Redis を使用することをお勧めします（`\Magento\Framework\Cache\Backend\Redis`）および `Cm_Cache_Backend_File` 共有メモリ内のデータをローカルにキャッシュする場合、次を使用します。 `'local_backend_options' => ['cache_dir' => '/dev/shm/']`

Adobeでは、を使用することをお勧めします [`cache preload`](redis-pg-cache.md#redis-preload-feature) それは Redis への圧力を大幅に減らすので、機能。 プリロードキーには必ずサフィックス「:hash」を追加してください。

## 古いキャッシュオプション

の概要 [!DNL Commerce] 2.4、 `use_stale_cache` 特定の状況では、オプションによってパフォーマンスが向上する場合があります。

一般に、パフォーマンス側ではロック待機のトレードオフは許容できますが、マーチャントが持つブロックまたはキャッシュの数が多いほど、ロックの待機に費やす時間が長くなります。 場合によっては、次の時間待機できます。 **キーの数** \* **参照タイムアウト** プロセスの時間。 まれに、マーチャントが内に何百ものキーを持つこともあります `Block/Config` キャッシュするので、ロックのルックアップタイムアウトが小さくても、数秒かかる場合があります。

古いキャッシュは L2 キャッシュでのみ機能します。 キャッシュが古い場合は、新しいキャッシュが並列プロセスで生成されている間に、古いキャッシュを送信できます。 古いキャッシュを有効にするには、次を追加します `'use_stale_cache' => true` を L2 キャッシュのトップ設定にします。

Adobeでは、 `use_stale_cache` オプションは、次のような最もメリットが大きいキャッシュタイプに対してのみ使用できます。

- `block_html`
- `config_integration_api`
- `config_integration`
- `full_page`
- `layout`
- `reflection`
- `translate`

Adobeは、 `use_stale_cache` オプション： `default` キャッシュタイプ。

次のコードは設定例を示しています。

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
