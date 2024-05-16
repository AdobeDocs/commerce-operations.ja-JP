---
title: env.php リファレンス
description: env.php ファイルの値のリストを参照してください。
exl-id: cf02da8f-e0de-4f0e-bab6-67ae02e9166f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '693'
ht-degree: 0%

---

# env.php リファレンス

この `env.php` ファイルには次のセクションが含まれます。

| 名前 | 説明 |
|-------------------------------|-----------------------------------------------------------------|
| `backend` | 管理領域の設定 |
| `cache` | redis ページとデフォルトキャッシュの設定 |
| `cache_types` | キャッシュストレージ設定 |
| `consumers_wait_for_messages` | コンシューマーがメッセージキューからのメッセージを処理する方法を設定します |
| `cron` | cron ジョブを有効または無効にする |
| `crypt` | 暗号化機能の暗号化キー |
| `db` | データベース接続設定 |
| `default_connection` | メッセージキューのデフォルト接続 |
| `directories` | Commerce ディレクトリのマッピング設定 |
| `downloadable_domains` | ダウンロード可能なドメインのリスト |
| `install` | インストールの日付 |
| `lock` | プロバイダ設定のロック |
| `MAGE_MODE` | この [アプリケーションモード](../bootstrap/application-modes.md) |
| `queue` | [メッセージキュー](../queues/manage-message-queues.md) 設定 |
| `resource` | リソース名の接続へのマッピング |
| `session` | セッションストレージデータ |
| `system` | 管理者で編集するフィールドを無効にします |
| `x-frame-options` | 設定： [x-frame-options][x-frame-options] |

## バックエンド

の設定 **frontName** を使用したCommerce管理者 url 用 `backend` env.php のノード。

```conf
'backend' => [
  'frontName' => 'admin'
]
```

## キャッシュ

を使用して、redis ページとデフォルトのキャッシュを設定します。 `cache` 内のノード `env.php` ファイル。

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

詳しくは、を参照してください。 [Redis 設定](../cache/redis-pg-cache.md).

## cache_type

このノードからは、すべてのキャッシュタイプ設定を使用できます。

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

の詳細 [キャッシュタイプ](../cli/manage-cache.md).

## consumers_wait_for_messages

処理されたメッセージの数がよりも少ない場合に、コンシューマーがメッセージのポーリングを続行するかどうかを指定します `max_messages` の値。 デフォルト値はです `1`.

```conf
'queue' => [
    'consumers_wait_for_messages' => 1
]
```

次のオプションを使用できます。

- `1` – コンシューマーは、 `max_messages` で指定された値 `env.php` tcp 接続を閉じてコンシューマ・プロセスを終了する前のファイル。 に到達する前にキューが空になった場合 `max_messages` の値が設定されている場合、消費者は到着するメッセージが増えるのを待ちます。

  この設定は大規模なマーチャントにお勧めです。メッセージフローが常に発生することが予想され、処理の遅延は望ましくないからです。

- `0` – コンシューマーは、キュー内の使用可能なメッセージを処理し、TCP 接続を閉じて終了します。 処理されたメッセージの数がよりも少ない場合でも、コンシューマーは追加のメッセージがキューに入るのを待ちません `max_messages` で指定された値 `env.php` ファイル。 これにより、メッセージキューの処理に長い遅延が発生することによる cron ジョブの問題を防ぐことができます。

  この設定は、メッセージ フローが常に発生するとは限らない小規模なマーチャントに推奨されます。この場合、数日間メッセージが送信されない可能性がある場合は、小規模な処理の遅延と引き換えに、コンピューティング リソースを節約することをお勧めします。

## cron

Commerce アプリケーションの cron ジョブを有効または無効にします。 デフォルトでは、cron ジョブが有効になっています。 これらを無効にするには、 `cron` への設定 `env.php` ファイルに追加し、値をに設定します。 `0`.

```conf
'cron' => [
  'enabled' => 0
]
```

>[!WARNING]
>
>cron ジョブを無効にする場合は注意が必要です。 無効にすると、Commerce アプリケーションで必要な必須プロセスは実行されません。

の詳細情報 [クローン](../cli/configure-cron-jobs.md).

## 陰窩

Commerceでは、パスワードやその他の機密データを保護するために暗号化キーを使用します。 このキーは、インストールプロセス中に生成されます。

```conf
'crypt' => [
  'key' => '63d409380ccb1182bfb27c231b732f05'
]
```

の詳細情報 [暗号化キー](https://docs.magento.com/user-guide/system/encryption-key.html) が含まれる _Commerce ユーザーガイド_.

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

メッセージキューのデフォルト接続を定義します。 値は以下のようになります `db`, `amqp`、またはのようなカスタムキューシステム `redismq`. 以外の値を指定した場合 `db`最初に、メッセージキューソフトウェアをインストールして設定する必要があります。 そうしないと、メッセージは正しく処理されません。

```conf
'queue' => [
    'default_connection' => 'amqp'
]
```

次の場合 `queue/default_connection` はシステムで指定されています `env.php` ファイルに含まれます。ただし、で特定の接続が定義されていない場合、この接続はシステムを通じてすべてのメッセージキューで使用されます。 `queue_topology.xml`, `queue_publisher.xml` または `queue_consumer.xml` ファイル。
例えば、 `queue/default_connection` 等しい `amqp` 。対象： `env.php` しかし、 `db` 接続はモジュールのキュー設定 XML ファイルで指定され、モジュールは MySQL をメッセージブローカとして使用します。

## ディレクトリ

からCommerce アプリケーションを提供するように web サーバーが設定されている場合に設定する必要がある、オプションのディレクトリマッピングオプション。 `/pub` ディレクトリ： [セキュリティの向上](../../installation/tutorials/docroot.md).

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

## downloadable_domains

このノードで利用できるダウンロード可能なドメインのリスト。 追加のドメインは、CLI コマンドを使用して追加、削除、一覧表示できます。

```conf
'downloadable_domains' => [
    'local.vanilla.com'
]
```

の詳細情報 [ダウンロード可能ドメイン](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#downloadabledomainsadd).

## install

Commerce アプリケーションのインストール日。

```conf
'install' => [
  'date' => 'Tue, 23 Apr 2019 09:31:07 +0000'
]
```

## ロック

ロックプロバイダーの設定は、次を使用して設定します `lock` ノード。

の詳細情報 [プロバイダ構成のロック](../../installation/tutorials/lock-provider.md).

## MAGE_モード

デプロイモードは、このノードで設定できます。

```conf
'MAGE_MODE' => 'developer'
```

の詳細情報 [アプリケーションモード](../cli/set-mode.md).

## キュー

このノードでは、メッセージキュー設定を使用できます。

```conf
'queue' => [
  'topics' => [
    'customer.created' => [publisher="default-rabitmq"],
    'order.created' => [publisher="default-rabitmq"],
  ]
]
```

の詳細情報 [メッセージキュー][message-queue].

## resource

リソース設定は、このノードで使用できます。

```conf
'resource' => [
  'default_setup' => [
    'connection' => 'default'
  ]
]
```

## session

セッション設定は、に保存されます。 `session` ノード。

```conf
'session' => [
  'save' => 'files'
],
```

の詳細情報 [Session](../storage/sessions.md).

## x-frame-options

x-frame-options ヘッダーは、このノードを使用して設定できます。

```conf
'x-frame-options' => 'SAMEORIGIN'
```

の詳細情報 [x-frame-options](../security/xframe-options.md).

## system

このノードを使用すると、Commerceは以下の設定値をロックします。 `env.php` を入力し、管理者でそのフィールドを無効にします。

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

詳しくは、を参照してください。 [env-php-config-set](../cli/set-configuration-values.md).

<!-- Link definitions -->

[message-queue]: https://developer.adobe.com/commerce/php/development/components/message-queues/
