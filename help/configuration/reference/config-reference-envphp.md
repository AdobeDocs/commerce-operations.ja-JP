---
title: env.php リファレンス
description: env.php ファイルの設定値と、Adobe Commerceの節について説明します。 環境設定と設定オプションについて説明します。
exl-id: cf02da8f-e0de-4f0e-bab6-67ae02e9166f
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '1016'
ht-degree: 0%

---

# env.php リファレンス

`env.php` ファイルには、次のセクションが含まれます。

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
| `MAGE_MODE` | [ アプリケーションモード ](../bootstrap/application-modes.md) |
| `queue` | [ メッセージキュー ](../queues/manage-message-queues.md) 設定 |
| `resource` | リソース名の接続へのマッピング |
| `session` | セッションストレージデータ |
| `system` | 管理者で編集するフィールドを無効にします |
| `x-frame-options` | [x-frame-options][x-frame-options] の設定 |

## バックエンド

env.php の **ノードを使用して、Commerceの管理者 URL の** frontName`backend` を設定します。

```conf
'backend' => [
  'frontName' => 'admin'
]
```

## キャッシュ

`cache` ファイルのノードを使用して、redis ページとデフォルト `env.php` キャッシュを設定します。

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

詳しくは、[Redis 設定 ](../cache/redis-pg-cache.md) を参照してください。

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

様々な [ キャッシュタイプ ](../cli/manage-cache.md) の詳細をご覧ください。

## consumers_wait_for_messages

処理されたメッセージの数が `max_messages` 未満の場合に、コンシューマーがメッセージのポーリングを続行するかどうかを指定します。 デフォルト値は `1` です。

```conf
'queue' => [
    'consumers_wait_for_messages' => 1
]
```

次のオプションを使用できます。

- `1` - コンシューマは、TCP 接続を閉じてコンシューマ・プロセスを終了する前に、メッセージ・キューからメッセージの処理を `max_messages` ファイルで指定された `env.php` 値に達するまで続行します。 キューが `max_messages` 値に達する前に空になった場合、コンシューマーは到着するメッセージがさらに届くのを待ちます。

  この設定は大規模なマーチャントにお勧めです。メッセージフローが常に発生することが予想され、処理の遅延は望ましくないからです。

- `0` - コンシューマーはキュー内の使用可能なメッセージを処理し、TCP 接続を閉じて終了します。 コンシューマーは、処理されたメッセージの数が `max_messages` ファイルで指定された `env.php` 値より少ない場合でも、追加のメッセージがキューに入るのを待ちません。 これにより、メッセージキューの処理に長い遅延が発生することによる cron ジョブの問題を防ぐことができます。

  この設定は、メッセージ フローが常に発生するとは限らない小規模なマーチャントに推奨されます。この場合、数日間メッセージが送信されない可能性がある場合は、小規模な処理の遅延と引き換えに、コンピューティング リソースを節約することをお勧めします。

## cron

Commerce アプリケーションの cron ジョブを有効または無効にします。 デフォルトでは、cron ジョブが有効になっています。 無効にするには、`cron` ファイルに `env.php` 設定を追加し、値を `0` に設定します。

```conf
'cron' => [
  'enabled' => 0
]
```

>[!WARNING]
>
>cron ジョブを無効にする場合は注意が必要です。 無効にすると、Commerce アプリケーションで必要な必須プロセスは実行されません。

詳しくは、[Cron](../cli/configure-cron-jobs.md) を参照してください。

## 陰窩

Commerceでは、パスワードやその他の機密データを保護するために暗号化キーを使用します。 このキーは、インストールプロセス中に生成されます。

```conf
'crypt' => [
  'key' => '63d409380ccb1182bfb27c231b732f05'
]
```

[ 暗号化キー ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/encryption-key) について詳しくは、_Commerce ユーザーガイド_ を参照してください。

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

メッセージキューのデフォルト接続を定義します。 値には、`db`、`amqp`、または `redismq` などのカスタムキューシステムを指定できます。 `db` 以外の値を指定する場合は、最初にメッセージキューソフトウェアをインストールして設定する必要があります。 そうしないと、メッセージは正しく処理されません。

```conf
'queue' => [
    'default_connection' => 'amqp'
]
```

システムの `queue/default_connection` ファイルで `env.php` が指定されている場合、`queue_topology.xml`、`queue_publisher.xml`、または `queue_consumer.xml` ファイルで特定の接続が定義されていない限り、この接続はシステムを通じてすべてのメッセージキューで使用されます。
例えば、`queue/default_connection` に `amqp` が `env.php` まれているのに、モジュールのキュー設定 XML ファイルで `db` 接続が指定されている場合、モジュールは MySQL をメッセージブローカーとして使用します。

## ディレクトリ

Web サーバーが `/pub` ディレクトリからCommerce アプリケーションを提供するように設定されている場合に設定する必要があるオプションのディレクトリマッピングオプション [ セキュリティの向上 ](../../installation/tutorials/docroot.md)。

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

詳細情報 [ ダウンロード可能なドメイン ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/cli-reference/commerce-on-premises#downloadabledomainsadd)。

## install

Commerce アプリケーションのインストール日。

```conf
'install' => [
  'date' => 'Tue, 23 Apr 2019 09:31:07 +0000'
]
```

## ロック

ロックプロバイダーの設定は、`lock` ノードを使用して設定します。

詳細情報 [ ロックプロバイダー設定 ](../../installation/tutorials/lock-provider.md)。

## MAGE_モード

デプロイモードは、このノードで設定できます。

```conf
'MAGE_MODE' => 'developer'
```

[ アプリケーションモード ](../cli/set-mode.md) の詳細情報。

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

詳細情報：[ メッセージキュー ][message-queue]。

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

セッション設定は、`session` ノードに保存されます。

```conf
'session' => [
  'save' => 'files'
],
```

詳細情報：[ セッション ](../storage/sessions.md)。

## x-frame-options

x-frame-options ヘッダーは、このノードを使用して設定できます。

```conf
'x-frame-options' => 'SAMEORIGIN'
```

詳しくは、[x-frame-options](../security/xframe-options.md) を参照してください。

## system

このノードを使用して、Commerceは `env.php` ファイル内の設定値をロックし、管理者でそのフィールドを無効にします。

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

詳しくは、[env-php-config-set](../cli/set-configuration-values.md) を参照してください。

<!-- Link definitions -->

[message-queue]: https://developer.adobe.com/commerce/php/development/components/message-queues/


## ファイル設定への変数の追加

オペレーティングシステム（OS）レベルの環境変数を使用して、すべての設定オプション（値を持つ変数）を設定または上書きできます。

`env.php` 設定は、ネストされたレベルを持つ配列に格納されます。 ネストされた配列パスを OS 環境変数の文字列に変換するには、パス内の各キーを、アンダースコアを 2 文字の `__`、大文字および `MAGENTO_DC_` のプレフィックスで連結します。

例えば、セッション保存ハンドラーを設定から OS 環境変数 `env.php` 変換します。

```conf
'session' => [
  'save' => 'files'
],
```

`__` と連結され、大文字のキーが `SESSION__SAVE` になります。

次に、プレフィックスとして `MAGENTO_DC_` を指定し、結果の OS 環境変数名 `MAGENTO_DC_SESSION__SAVE` を取得します。

```shell
export MAGENTO_DC_SESSION__SAVE=files
```

別の例として、スカラー `env.php` 設定オプションのパスを変換します。

```conf
'x-frame-options' => 'SAMEORIGIN'
```

>[!INFO]
>
>変数名は大文字にする必要がありますが、値は大文字と小文字が区別され、ドキュメントに記載されているように保持される必要があります。

単に大文字にして `MAGENTO_DC_` というプレフィックスを付けることで、最終的な OS 環境変数名 `MAGENTO_DC_X-FRAME-OPTIONS` を受け取ります。

```shell
export MAGENTO_DC_X-FRAME-OPTIONS=SAMEORIGIN
```

>[!INFO]
>
>コンテンツ `env.php`OS の環境変数よりも優先されることに注意してください。

## 変数によるファイル設定の上書き

OS 環境変数で既存の `env.php` 設定オプションを上書きするには、設定の配列要素を JSON エンコードし、`MAGENTO_DC__OVERRIDE` OS 変数の値として設定する必要があります。

`MAGENTO_DC__OVERRIDE` が設定されている場合、Commerce フレームワークでは `env.php` ファイル内の対応する値をバイパスし、環境変数から直接設定を読み取ります。 `env.php` ファイルの値は変更されませんが、オーバーライドされた設定セクションでは無視されます。

>[!IMPORTANT]
>
>`MAGENTO_DC__OVERRIDE` 変数は、`env.php` ファイルで指定された設定セクションを完全にバイパスします。 この動作は、`MAGENTO_DC_` ファイル内の値よりも優先度が低い個々の `env.php` 変数とは異なります。

複数の設定オプションを上書きする必要がある場合は、JSON エンコーディングの前に、すべてを 1 つの配列に組み合わせます。

例えば、次の `env.php` 設定を上書きします。

```conf
'session' => [
  'save' => 'files'
],
'x-frame-options' => 'SAMEORIGIN'
```

上記の配列の JSON エンコードされたテキストは、次のようになります
`{"session":{"save":"files"},"x-frame-options":"SAMEORIGIN"}`。

次に、これを `MAGENTO_DC__OVERRIDE` OS 変数の値として設定します。

```shell
export MAGENTO_DC__OVERRIDE='{"session":{"save":"files"},"x-frame-options":"SAMEORIGIN"}'
```

>[!INFO]
>
>OS によってエンコードされた文字列が破損するのを防ぐため、JSON でエンコードされた配列が適切に引用符で囲まれているか、必要に応じてエスケープされていることを確認します。