---
title: env.php リファレンス
description: Adobe Commerceのenv.php ファイルの設定値とセクションについて説明します。 環境設定と設定オプションの詳細。
exl-id: cf02da8f-e0de-4f0e-bab6-67ae02e9166f
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '1071'
ht-degree: 0%

---

# env.php リファレンス

`env.php` ファイルには、次のセクションが含まれています。

| 名前 | 説明 |
|-------------------------------|-----------------------------------------------------------------|
| `backend` | 管理者領域の設定 |
| `cache` | redis ページとデフォルトのキャッシュの設定 |
| `cache_types` | キャッシュストレージ設定 |
| `consumers_wait_for_messages` | 消費者がメッセージキューからのメッセージを処理する方法を設定します |
| `cron` | cron ジョブを有効または無効にする |
| `crypt` | 暗号関数の暗号化キー |
| `db` | データベース接続の設定 |
| `default_connection` | メッセージキューのデフォルト接続 |
| `directories` | Commerce ディレクトリマッピング設定 |
| `downloadable_domains` | ダウンロード可能なドメインのリスト |
| `install` | インストール日 |
| `lock` | プロバイダー設定のロック |
| `MAGE_MODE` | [ アプリケーションモード ](../bootstrap/application-modes.md) |
| `queue` | [ メッセージキュー](../queues/manage-message-queues.md)設定 |
| `resource` | 接続へのリソース名のマッピング |
| `session` | セッションストレージデータ |
| `system` | 管理画面で編集するフィールドを無効にします |
| `x-frame-options` | [x-frame-options](../security/xframe-options.md)の設定 |

## バックエンド

env.phpの`backend` ノードを使用して、Commerce管理者URLの&#x200B;**frontName**&#x200B;を設定します。

```conf
'backend' => [
  'frontName' => 'admin'
]
```

## キャッシュ

`env.php` ファイルの`cache` ノードを使用して、redis ページとデフォルトのキャッシュを設定します。

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

詳しくは、[Redis Configuration](../cache/redis-pg-cache.md)を参照してください。

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

様々な[ キャッシュタイプ ](../cli/manage-cache.md)について詳しく説明します。

## consumers_wait_for_messages

処理済みメッセージの数が`max_messages`値未満の場合、消費者がメッセージのポーリングを続行するかどうかを指定します。 デフォルト値は`1`です。

```conf
'queue' => [
    'consumers_wait_for_messages' => 1
]
```

次のオプションを使用できます。

- `1` - TCP接続を閉じてコンシューマープロセスを終了する前に、`env.php` ファイルで指定された`max_messages`値に達するまで、消費者はメッセージキューからのメッセージを処理し続けます。 キューが`max_messages`の値に達する前に空になった場合、消費者はより多くのメッセージが届くのを待ちます。

  一定のメッセージフローが期待され、処理の遅延が望ましくないため、大規模なマーチャントにこの設定をお勧めします。

- `0` - コンシューマーはキュー内の使用可能なメッセージを処理し、TCP接続を閉じて終了します。 処理済みメッセージの数が`env.php` ファイルで指定された`max_messages`値より少ない場合でも、消費者は追加のメッセージがキューに入るのを待ちません。 これにより、メッセージキュー処理の遅延が長くなることによるcron ジョブの問題を回避できます。

  この設定は、一定のメッセージフローを期待せず、メッセージが何日も表示されない可能性がある場合に小さな処理の遅延と引き換えにコンピューティングリソースを節約することを好む小規模なマーチャントにお勧めします。

## cron

Commerce アプリケーションのcron ジョブを有効または無効にします。 デフォルトでは、cron ジョブは有効になっています。 無効にするには、`cron`設定を`env.php` ファイルに追加し、値を`0`に設定します。

```conf
'cron' => [
  'enabled' => 0
]
```

>[!WARNING]
>
>cron ジョブを無効にする場合は注意してください。 無効にすると、Commerce アプリケーションで必要な基本的なプロセスが実行されません。

[Crons](../cli/configure-cron-jobs.md)の詳細をご覧ください。

## 暗号化

Commerceでは、暗号化キーを使用してパスワードやその他の機密データを保護しています。 このキーは、インストールプロセス中に生成されます。

```conf
'crypt' => [
  'key' => '63d409380ccb1182bfb27c231b732f05'
]
```

[暗号化キー](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/encryption-key)の詳細については、_Commerce ユーザーガイド_&#x200B;を参照してください。

## db

すべてのデータベース設定は、このノードで使用できます。

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

メッセージキューのデフォルト接続を定義します。 値は、`db`、`amqp`、`stomp`、または`redismq`のようなカスタムキューシステムにすることができます。 `db`以外の値を指定する場合は、最初にメッセージキューソフトウェアをインストールして設定する必要があります。 それ以外の場合、メッセージは正しく処理されません。

```conf
'queue' => [
    'default_connection' => 'amqp'
]
```

STOMP （ActiveMQ Artemis）の場合：

```conf
'queue' => [
    'default_connection' => 'stomp'
]
```

`queue/default_connection`がシステム `env.php` ファイルで指定されている場合、特定の接続が`queue_topology.xml`、`queue_publisher.xml`または`queue_consumer.xml` ファイルで定義されていない限り、この接続はシステムを介するすべてのメッセージキューに使用されます。
例えば、`queue/default_connection`が`env.php`の`amqp`であるが、`db`接続がモジュールのキュー構成XML ファイルで指定されている場合、モジュールはMySQLをメッセージブローカーとして使用します。

## ディレクトリ

Web サーバーが`/pub` ディレクトリから[ セキュリティの向上](../../installation/tutorials/docroot.md)のためにCommerce アプリを提供するように設定されている場合に設定する必要がある、オプションのディレクトリマッピングオプション。

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

## downloadable_domain

このノードで使用可能なダウンロード可能なドメインのリスト。 追加のドメインは、CLI コマンドを使用して追加、削除、または一覧表示できます。

```conf
'downloadable_domains' => [
    'local.vanilla.com'
]
```

[ ダウンロード可能なドメイン ](/help/tools/reference/commerce-on-premises.md#downloadabledomainsadd)の詳細をご覧ください。

## インストール

Commerce アプリケーションのインストール日。

```conf
'install' => [
  'date' => 'Tue, 23 Apr 2019 09:31:07 +0000'
]
```

## ロック

ロックプロバイダーの設定は、`lock` ノードを使用して設定されます。

[ プロバイダ設定のロック ](../../installation/tutorials/lock-provider.md)の詳細を説明します。

## MAGE_MODE

デプロイモードは、このノードで設定できます。

```conf
'MAGE_MODE' => 'developer'
```

[ アプリケーションモード ](../cli/set-mode.md)の詳細をご覧ください。

## キュー

メッセージキューの設定は、このノードで使用できます。 RabbitMQ （AMQP）またはActiveMQ Artemis （STOMP）をメッセージブローカーとして設定できます。

```conf
'queue' => [
  'topics' => [
    'customer.created' => [publisher="default-broker"],
    'order.created' => [publisher="default-broker"],
  ]
]
```

[ メッセージキュー](https://developer.adobe.com/commerce/php/development/components/message-queues/)の詳細をご覧ください。

## リソース

リソース設定は、このノードで使用できます。

```conf
'resource' => [
  'default_setup' => [
    'connection' => 'default'
  ]
]
```

## セッション

セッション設定は`session` ノードに保存されます。

```conf
'session' => [
  'save' => 'files'
],
```

[ セッション ](../storage/sessions.md)の詳細をご覧ください。

## x-frame-options

x-frame-options ヘッダーは、このノードを使用して設定できます。

```conf
'x-frame-options' => 'SAMEORIGIN'
```

[x-frame-options](../security/xframe-options.md)の詳細をご覧ください。

## システム

このノードを使用すると、Commerceは`env.php` ファイル内の設定値をロックし、管理者のフィールドを無効にします。

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

詳しくは、[env-php-config-set](../cli/set-configuration-values.md)を参照してください。



## ファイル設定への変数の追加

オペレーティングシステム（OS）レベルの環境変数を使用して、すべての設定オプション（値を持つ変数）を設定または上書きできます。

`env.php`設定は、ネストされたレベルを持つ配列に格納されます。 ネストされた配列パスをOS環境変数の文字列に変換するには、パス内の各キーをダブルアンダースコア文字`__`、大文字、および接頭辞`MAGENTO_DC_`で連結します。

例えば、セッション保存ハンドラーを`env.php`設定からOS環境変数に変換します。

```conf
'session' => [
  'save' => 'files'
],
```

`__`と連結され、大文字のキーは`SESSION__SAVE`になります。

次に、`MAGENTO_DC_`という接頭辞を付けて、結果として得られるOS環境変数名`MAGENTO_DC_SESSION__SAVE`を取得します。

```shell
export MAGENTO_DC_SESSION__SAVE=files
```

別の例として、スカラー`env.php`設定オプションパスを変換してみましょう。

```conf
'x-frame-options' => 'SAMEORIGIN'
```

>[!INFO]
>
>変数名は大文字にする必要がありますが、値は大文字と小文字が区別され、文書化されたとおりに保持する必要があります。

最終的なOS環境変数名`MAGENTO_DC_X-FRAME-OPTIONS`を受け取るには、大文字と`MAGENTO_DC_`をプレフィックスするだけです。

```shell
export MAGENTO_DC_X-FRAME-OPTIONS=SAMEORIGIN
```

>[!INFO]
>
>`env.php` コンテンツは、OS環境変数よりも優先されます。

## 変数でファイル設定を上書き

既存の`env.php`設定オプションをOS環境変数で上書きするには、設定の配列要素をJSON エンコードし、`MAGENTO_DC__OVERRIDE` OS変数の値として設定する必要があります。

`MAGENTO_DC__OVERRIDE`が設定されると、Commerce フレームワークは`env.php` ファイル内の対応する値をバイパスし、環境変数から直接設定を読み取ります。 `env.php` ファイルの値は変更されませんが、上書きされた設定セクションでは無視されます。

>[!IMPORTANT]
>
>`MAGENTO_DC__OVERRIDE`変数は、`env.php` ファイル内の指定された構成セクションを完全にバイパスします。 この動作は、`env.php` ファイルの値よりも優先度が低い個々の`MAGENTO_DC_`変数とは異なります。

複数の設定オプションを上書きする必要がある場合は、JSON エンコーディングの前に、すべての設定を1つの配列に組み立てます。

例えば、次の`env.php`設定を上書きします。

```conf
'session' => [
  'save' => 'files'
],
'x-frame-options' => 'SAMEORIGIN'
```

上記の配列のJSON エンコードされたテキストは
`{"session":{"save":"files"},"x-frame-options":"SAMEORIGIN"}`.

次に、`MAGENTO_DC__OVERRIDE` OS変数の値として設定します。

```shell
export MAGENTO_DC__OVERRIDE='{"session":{"save":"files"},"x-frame-options":"SAMEORIGIN"}'
```

>[!INFO]
>
>JSON エンコードされた配列が適切に引用符で囲まれているか、必要に応じてエスケープされていることを確認し、OSがエンコードされた文字列を破損しないようにします。