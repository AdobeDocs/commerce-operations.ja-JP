---
title: env.php リファレンス
description: env.php ファイルの値のリストを参照してください。
exl-id: cf02da8f-e0de-4f0e-bab6-67ae02e9166f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 0%

---

# env.php リファレンス

The `env.php` ファイルには次のセクションが含まれます。

| 名前 | 説明 |
|-------------------------------|-----------------------------------------------------------------|
| `backend` | 管理領域の設定 |
| `cache` | Redis ページとデフォルトキャッシュの設定 |
| `cache_types` | キャッシュストレージ設定 |
| `consumers_wait_for_messages` | メッセージキューからのメッセージの処理方法の設定 |
| `cron` | cron ジョブの有効化または無効化 |
| `crypt` | 暗号化関数の暗号化キー |
| `db` | データベース接続設定 |
| `default_connection` | メッセージキューのデフォルト接続 |
| `directories` | コマースディレクトリのマッピング設定 |
| `downloadable_domains` | ダウンロード可能ドメインのリスト |
| `install` | インストール日 |
| `lock` | プロバイダー設定をロックする |
| `MAGE_MODE` | The [アプリケーションモード](../bootstrap/application-modes.md) |
| `queue` | [メッセージキュー](../queues/manage-message-queues.md) 設定 |
| `resource` | 接続へのリソース名のマッピング |
| `session` | セッションストレージデータ |
| `system` | 管理での編集用フィールドを無効にします |
| `x-frame-options` | の設定 [x-frame-options][x-frame-options] |

## backend

を設定します。 **frontName** を使用して Commerce 管理者 url に追加します。 `backend` env.php のノード。

```conf
'backend' => [
  'frontName' => 'admin'
]
```

## キャッシュ

次を使用して、Redis ページとデフォルトのキャッシュを設定します。 `cache` ノードを `env.php` ファイル。

```conf
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
]
```

詳しくは、 [Redis 設定](../cache/redis-pg-cache.md).

## cache_types

すべてのキャッシュタイプ設定は、このノードから使用できます。

```conf
'cache_types' => [
  'config' => 1,
  'layout' => 1,
  'block_html' => 1,
  'collections' => 1,
  'reflection' => 1,
  'db_ddl' => 1,
  'compiled_config' => 1,
  'eav' => 1,
  'customer_notification' => 1,
  'config_integration' => 1,
  'config_integration_api' => 1,
  'full_page' => 1,
  'config_webservice' => 1,
  'translate' => 1,
  'vertex' => 1
]
```

詳細情報 [キャッシュタイプ](../cli/manage-cache.md).

## consumers_wait_for_messages

処理されたメッセージの数が `max_messages` の値です。 デフォルト値は `1`.

```conf
'queue' => [
    'consumers_wait_for_messages' => 1
]
```

次のオプションを使用できます。

- `1` — コンシューマーは、 `max_messages` 指定された値 `env.php` ファイルを開いてから、TCP 接続を閉じ、コンシューマープロセスを終了します。 キューが空になってから `max_messages` の値を指定すると、コンシューマーはより多くのメッセージが到着するのを待ちます。

  大手商人にはこの設定をお勧めします。メッセージのフローが常に発生し、処理の遅延が望ましくないからです。

- `0` — コンシューマーは、キュー内の使用可能なメッセージを処理し、TCP 接続を閉じて、終了します。 処理されたメッセージの数が `max_messages` 指定された値 `env.php` ファイル。 これにより、メッセージキューの処理に長時間の遅延が生じる cron ジョブの問題を防ぐことができます。

  この設定は、常にメッセージの流れが予想されず、数日間メッセージがない場合の処理の遅れが軽微な代わりに、コンピューティングリソースを節約する小規模なマーチャントに対してお勧めします。

## cron

コマースアプリケーションの cron ジョブを有効または無効にします。 デフォルトでは、cron ジョブが有効になっています。 これらを無効にするには、 `cron` 設定を `env.php` ファイルを開き、値を `0`.

```conf
'cron' => [
  'enabled' => 0
]
```

>[!WARNING]
>
>cron ジョブを無効にする場合は注意が必要です。 これらが無効になっている場合、Commerce アプリケーションで必要な必須プロセスは実行されません。

詳細情報： [Crons](../cli/configure-cron-jobs.md).

## 暗号

Commerce では、パスワードやその他の機密データを保護するために暗号化キーを使用します。 このキーは、インストールプロセス中に生成されます。

```conf
'crypt' => [
  'key' => '63d409380ccb1182bfb27c231b732f05'
]
```

詳細情報： [暗号化キー](https://docs.magento.com/user-guide/system/encryption-key.html) （内） _コマースユーザーガイド_.

## db

このノードでは、すべてのデータベース設定を使用できます。

```conf
'db' => [
  'table_prefix' => '',
  'connection' => [
    'default' => [
      'host' => 'localhost',
      'dbname' => 'magento_db',
      'username' => 'root',
      'password' => 'admin123',
      'model' => 'mysql4',
      'engine' => 'innodb',
      'initStatements' => 'SET NAMES utf8;',
      'active' => '1'
    ]
  ]
]
```

## default_connection

メッセージキューのデフォルト接続を定義します。 値は `db`, `amqp`、またはのようなカスタムキューシステム `redismq`. 次の値以外の値を指定した場合： `db`に設定する場合は、最初にメッセージキューソフトウェアをインストールして設定する必要があります。 そうしないと、メッセージは正しく処理されません。

```conf
'queue' => [
    'default_connection' => 'amqp'
]
```

次の場合 `queue/default_connection` がシステムで指定されている `env.php` ファイルの場合、この接続は、 `queue_topology.xml`, `queue_publisher.xml` または `queue_consumer.xml` ファイル。
例えば、 `queue/default_connection` 次に該当 `amqp` in `env.php` しかし `db` モジュールのキュー設定 XML ファイルで接続が指定されている場合、モジュールは MySQL をメッセージブローカーとして使用します。

## ディレクトリ

Web サーバーが Commerce アプリを `/pub` のディレクトリ [セキュリティの向上](../../installation/tutorials/docroot.md).

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

## downloadable_domains

このノードで使用可能なダウンロード可能ドメインのリスト。 CLI コマンドを使用して、追加のドメインを追加、削除、または表示できます。

```conf
'downloadable_domains' => [
    'local.vanilla.com'
]
```

詳細情報： [ダウンロード可能なドメイン](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#downloadabledomainsadd).

## install

Commerce アプリケーションのインストール日です。

```conf
'install' => [
  'date' => 'Tue, 23 Apr 2019 09:31:07 +0000'
]
```

## ロック

ロックプロバイダーの設定は、 `lock` ノード。

詳細情報： [プロバイダー構成をロック](../../installation/tutorials/lock-provider.md).

## MAGE_MODE

このノードでは、デプロイモードを設定できます。

```conf
'MAGE_MODE' => 'developer'
```

詳細情報： [アプリケーションモード](../cli/set-mode.md).

## キュー

メッセージキューの設定は、このノードで使用できます。

```conf
'queue' => [
  'topics' => [
    'customer.created' => [publisher="default-rabitmq"],
    'order.created' => [publisher="default-rabitmq"],
  ]
]
```

詳細情報： [メッセージキュー][message-queue].

## リソース

このノードでは、リソース設定を使用できます。

```conf
'resource' => [
  'default_setup' => [
    'connection' => 'default'
  ]
]
```

## session

セッション設定は、 `session` ノード。

```conf
'session' => [
  'save' => 'files'
],
```

詳細情報： [セッション](../storage/sessions.md).

## x-frame-options

x-frame-options ヘッダーは、このノードを使用して設定できます。

```conf
'x-frame-options' => 'SAMEORIGIN'
```

詳細情報： [x-frame-options](../security/xframe-options.md).

## システム

このノードを使用して、Commerce は、 `env.php` ファイルを編集してから、管理者のフィールドを無効にします。

```conf
'system' => [
  'default' => [
    'web' => [
      'secure' => [
          'base_url' => 'https://magento.test/'
      ]
    ]
  ]
```

詳しくは、 [env-php-config-set](../cli/set-configuration-values.md).

<!-- Link definitions -->

[message-queue]: https://developer.adobe.com/commerce/php/development/components/message-queues/
