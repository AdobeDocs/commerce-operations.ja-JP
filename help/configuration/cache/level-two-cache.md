---
title: L2 キャッシュの設定
description: L2 キャッシュを設定する方法を説明します。
source-git-commit: 02f02393878d04b4a0fcdae256ac1ac5dd13b7f6
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# L2 キャッシュの設定

キャッシュを使用すると、リモートキャッシュストレージとコマースアプリケーション間のネットワークトラフィックを減らすことができます。 標準の Commerce インスタンスは、リクエストごとに約 300 KB 転送し、場合によってはトラフィックが急速に 1,000 件を超えるリクエストに増えることがあります。

ネットワーク帯域幅を Redis に減らすには、キャッシュデータを各 Web ノードにローカルに保存し、リモートキャッシュを次の 2 つの目的で使用します。

- キャッシュデータのバージョンを確認し、最新のキャッシュがローカルに保存されていることを確認します
- 最新のキャッシュをリモートマシンからローカルマシンに転送する

Commerce は、ハッシュ化されたデータバージョンを Redis に格納し、サフィックス「:hash」を正規キーに追加します。 古いローカルキャッシュがある場合、データはキャッシュアダプタを使用してローカルマシンに転送されます。

>[!INFO]
>
>クラウドインフラストラクチャ上のAdobe Commerceの場合は、 [拡張 Redis キャッシュの実装](https://support.magento.com/hc/en-us/articles/360049292532) サポート記事。

## 設定例

次の例を使用して、 `app/etc/env.php` ファイル。

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
                ],
                'use_stale_cache' => false,
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

- `backend` は、L2 キャッシュの実装です。
- `backend_options` は L2 キャッシュ設定です。
   - `remote_backend` はリモートキャッシュ実装です。Redis または MySQL。
   - `remote_backend_options` は、リモートキャッシュ設定です。
   - `local_backend` はローカルキャッシュ実装です。 `Cm_Cache_Backend_File`
   - `local_backend_options` は、ローカルキャッシュの設定です。
      - `cache_dir` は、ローカルキャッシュが保存されるディレクトリのファイルキャッシュ固有のオプションです。
   - `use_stale_cache` は、古いキャッシュの使用を有効または無効にするフラグです。

Adobeでは、リモートキャッシュ (`\Magento\Framework\Cache\Backend\Redis`) および `Cm_Cache_Backend_File` 共有メモリ内のデータのローカルキャッシュの場合は、次を使用します。 `'local_backend_options' => ['cache_dir' => '/dev/shm/']`

Adobeでは、 [`cache preload`](redis-pg-cache.md#redis-preload-feature) 特徴は、レディスの圧力を大幅に減らすので。 キーをプリロードする際は、必ずサフィックス「:hash」を追加してください。

## 古いキャッシュオプション

の使用を開始 [!DNL Commerce] 2.4, `stale_cache` オプションを使用すると、特定の状況でパフォーマンスを向上させることができます。

一般に、ロック待ちを伴うトレードオフは、パフォーマンス側から受け入れられますが、商人が持つブロックやキャッシュの数が多いほど、ロック待ちに費やされる時間が長くなります。 状況によっては、 **キーの数** \* **参照タイムアウト** プロセスの時間。 稀に、商人が何百もの鍵を `Block/Config` キャッシュのため、ロックの小さな参照タイムアウトでも、数秒かかる場合があります。

古いキャッシュは L2 キャッシュでのみ機能します。 古いキャッシュがある場合、新しいキャッシュが並行処理で生成されている間に、古いキャッシュを送信できます。 古いキャッシュを有効にするには、 `'use_stale_cache' => true` を L2 キャッシュの最上位の設定に追加します。
