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
>クラウドインフラストラクチャー上のAdobe Commerceの場合、L2 キャッシュ設定に [ 変数をデプロイ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) を使用できます。

## 設定例

次の例を使用して、`app/etc/env.php` ファイル内の既存のキャッシュセクションを変更または置き換えます。

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
- `backend_options` は L2 キャッシュの設定です。
   - `remote_backend` は、リモートキャッシュの実装です（Redis または MySQL）。
   - `remote_backend_options` は、リモートキャッシュの設定です。
   - `local_backend` はローカル キャッシュの実装です：`Cm_Cache_Backend_File`
   - ローカルキャッシュの設定は `local_backend_options` のとおりです。
   - ローカルキャッシュ `cache_dir` 格納されるディレクトリのファイルキャッシュ固有のオプションです。

Adobeでは、リモートキャッシングには Redis （`\Magento\Framework\Cache\Backend\Redis`）を使用し、共有メモリ内のデータのローカルキャッシングには `Cm_Cache_Backend_File` （`'local_backend_options' => ['cache_dir' => '/dev/shm/']`）を使用することをお勧めします。

Adobeは、Redis への圧力を大幅に減らすため、[`cache preload`](redis-pg-cache.md#redis-preload-feature) 機能を使用することをお勧めします。 プリロードキーには必ずサフィックス「:hash」を追加してください。

## 古いキャッシュオプション

[!DNL Commerce] 2.4 以降では、`use_stale_cache` オプションを使用すると、特定のケースでのパフォーマンスを向上させることができます。

一般に、パフォーマンス側ではロック待機のトレードオフは許容できますが、マーチャントが持つブロックまたはキャッシュの数が多いほど、ロックの待機に費やす時間が長くなります。 一部のシナリオでは、**キーの数**\* **ルックアップタイムアウト** の時間をプロセスのために待機することができます。 まれに、マーチャントが `Block/Config` キャッシュに数百のキーを保持している場合があるので、ロックのルックアップタイムアウトが小さくても数秒かかる場合があります。

古いキャッシュは L2 キャッシュでのみ機能します。 キャッシュが古い場合は、新しいキャッシュが並列プロセスで生成されている間に、古いキャッシュを送信できます。 古いキャッシュを有効にするには、L2 キャッシュのトップ設定に `'use_stale_cache' => true` を追加します。

Adobeでは、`use_stale_cache` オプションを有効にすることをお勧めします。このオプションのメリットが最も大きいキャッシュタイプに対しては、次のようなメリットがあります。

- `block_html`
- `config_integration_api`
- `config_integration`
- `full_page`
- `layout`
- `reflection`
- `translate`

Adobeでは、`default` しいキャッシュタイプに対して `use_stale_cache` オプションを有効にすることはお勧めしません。

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
