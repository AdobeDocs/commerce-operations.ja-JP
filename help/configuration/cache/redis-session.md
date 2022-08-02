---
title: セッションストレージに Redis を使用
description: セッションストレージ用に Redis を設定する方法を説明します。
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '730'
ht-degree: 1%

---


# セッションストレージに Redis を使用

>[!IMPORTANT]
>
>必ず [Redis をインストール](config-redis.md#install-redis) 続行する前に


Commerce に、Redis セッションストレージを設定するコマンドラインオプションが追加されました。 以前のリリースでは、 `<Commerce install dir>app/etc/env.php` ファイル。 コマンドラインは検証機能を提供し、これが推奨される設定方法ですが、編集は可能です `env.php` ファイル。

を実行します。 `setup:config:set` コマンドを使用して、Redis 固有のパラメータを指定します。

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-<parameter_name>=<parameter_value>...
```

場所

`--session-save=redis` Redis セッションストレージを有効にします。 この機能が既に有効になっている場合は、このパラメータを省略します。

`--session-save-redis-<parameter_name>=<parameter_value>` は、セッションストレージを設定するパラメーターと値のペアのリストです。

| コマンドラインパラメータ | パラメーター名 | 意味 | デフォルト値 |
|--- |--- |--- |--- |
| session-save-redis-host | ホスト | UNIX ソケットを使用する場合は、完全修飾ホスト名、IP アドレス、または絶対パス。 | localhost |
| session-save-redis-port | ポート | Redis サーバーのリスンポート。 | 6379 |
| session-save-redis-password | パスワード | Redis サーバーが認証を必要とする場合にパスワードを指定します。 | 空 |
| session-save-redis-timeout | timeout | 接続タイムアウト（秒）。 | 2.5 |
| session-save-redis-persistent-id | persistent_identifier | 永続的な接続を有効にする一意の文字列（例：sess-db0）。<br>[phpredis と php-fpm に関する既知の問題](https://github.com/phpredis/phpredis/issues/70). |
| session-save-redis-db | データベース | 一意の Redis データベース番号。データの損失から保護することをお勧めします。<br><br>**重要**:Redis を複数のタイプのキャッシュに使用する場合、データベースの数が異なる必要があります。 デフォルトのキャッシュデータベース番号を 0 に、ページキャッシュデータベース番号を 1 に、セッションストレージデータベース番号を 2 に割り当てることをお勧めします。 | 0 |
| session-save-redis-compression-threshold | compression_threshold | 圧縮を無効にするには 0 に設定します ( [suhosin.session.encrypt =オン](https://suhosin.org/stories/howtos.html)) をクリックします。<br>[64 KB を超える文字列に関する既知の問題](https://github.com/colinmollenhour/Cm_Cache_Backend_Redis/issues/18). | 2048 |
| session-save-redis-compression-lib | compression_library | オプション：gzip、lzf、lz4 または snappy。 | gzip |
| session-save-redis-log-level | log_level | を次のいずれかに設定し、最も詳細でないものから最も詳細なものまで順に表示します。<ul><li>0 ( 緊急：最も重大なエラーのみ )<li>1 ( アラート：即時対応が必要です )<li>2 ( 重要：アプリケーションコンポーネントを使用できません )<li>3 ( エラー：ランタイムエラー（重要ではないが、監視が必要）<li>4 ( 警告：追加情報（推奨）<li>5 ( 通知：正常だが有意な状態 )<li>6 ( 情報：情報メッセージ )<li>7 ( デバッグ：開発またはテストに関する最も多い情報 )</ul> | 1 |
| session-save-redis-max-concurrency | max_concurrency | 1 つのセッションでロックを待機できるプロセスの最大数。 大規模な実稼働クラスタの場合は、PHP プロセスの数の 10%以上に設定します。 | 6 |
| session-save-redis-break-after-frontend | break_after_frontend | フロントエンド（つまりストアフロント）セッションのロックを解除しようとするまでの待機時間（秒）。 | 5 |
| session-save-redis-break-after-adminhtml | break_after_adminhtml | adminhtml（つまり、Admin）セッションのロックを解除しようとするまでの待機時間（秒）。 | 30 |
| session-save-redis-first-lifetime | first_lifetime | 最初の書き込み時の非ボットのセッションの有効期間（秒）。0 を使用して無効にします。 | 600 |
| session-save-redis-bot-first-lifetime | bot_first_lifetime | 最初の書き込み時のボットのセッションの有効期間（秒）。無効にするには 0 を使用します。 | 60 |
| session-save-redis-bot-lifetime | bot_lifetime | 後続の書き込み時のボットのセッションの有効期間（秒）。0 を使用して無効にします。 | 7200 |
| session-save-redis-disable-locking | disable_locking | セッションロックを完全に無効にします。 | 0 (false) |
| session-save-redis-min-lifetime | min_lifetime | セッションの最小有効期間（秒）。 | 60 |
| session-save-redis-max-lifetime | max_lifetime | 最大セッションの有効期間（秒）。 | 2592000（720 時間） |
| session-save-redis-sentinel-master | sentinel_master | Redis Sentinel のマスター名 | 空 |
| session-save-redis-sentinel-servers | sentinel_servers | Redis Sentinel サーバーのリスト（コンマ区切り） | 空 |
| session-save-redis-sentinel-verify-master | sentinel_verify_master | Redis Sentinel マスターの状態フラグを確認します | 0 (false) |
| session-save-redis-sentinel-connect-retries | sentinel_connect_retries | 歩哨の接続再試行 | 5 |

## 例

次の例では、Redis をセッションデータストアに設定し、ホストをに設定します。 `127.0.0.1`では、ログレベルを 4 に設定し、データベース番号を 2 に設定します。 その他のパラメータはすべてデフォルト値に設定されます。

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=127.0.0.1 --session-save-redis-log-level=4 --session-save-redis-db=2
```

### 結果

Commerce は、次のような行をに追加します。 `<magento_root>app/etc/env.php`:

```php
    'session' =>
    array (
      'save' => 'redis',
      'redis' =>
      array (
        'host' => '127.0.0.1',
        'port' => '6379',
        'password' => '',
        'timeout' => '2.5',
        'persistent_identifier' => '',
        'database' => '2',
        'compression_threshold' => '2048',
        'compression_library' => 'gzip',
        'log_level' => '4',
        'max_concurrency' => '6',
        'break_after_frontend' => '5',
        'break_after_adminhtml' => '30',
        'first_lifetime' => '600',
        'bot_first_lifetime' => '60',
        'bot_lifetime' => '7200',
        'disable_locking' => '0',
        'min_lifetime' => '60',
        'max_lifetime' => '2592000'
      )
    ),
```

>[!INFO]
>
>セッションレコードの TTL は、Cookie の有効期間の値を使用します。この値は管理者で設定されます。 Cookie の有効期間を 0（デフォルトは 3600）に設定した場合、Redis セッションは min_lifetime で指定した秒数（デフォルトは 60）で期限切れになります。 この相違は、Redis とセッション cookie のライフタイム値 0 の解釈の違いに起因します。 この動作が望ましくない場合は、 min_lifetime の値を増やします。

## Redis 接続の確認

Redis と Commerce が連携して動作していることを確認するには、Redis を実行しているサーバにログインし、ターミナルを開いて、Redis monitor コマンドまたは ping コマンドを使用します。

### Redis モニタコマンド

```bash
redis-cli monitor
```

session-storage 出力の例：

```terminal
1476824834.187250 [0 127.0.0.1:52353] "select" "0"
1476824834.187587 [0 127.0.0.1:52353] "hmget" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "data" "writes"
1476824834.187939 [0 127.0.0.1:52353] "expire" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "1200"
1476824834.257226 [0 127.0.0.1:52353] "select" "0"
1476824834.257239 [0 127.0.0.1:52353] "hmset" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "data" "_session_validator_data|a:4:{s:11:\"remote_addr\";s:12:\"10.235.34.14\";s:8:\"http_via\";s:0:\"\";s:20:\"http_x_forwarded_for\";s:0:\"\";s:15:\"http_user_agent\";s:115:\"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/53.0.2785.143 Safari/537.36\";}_session_hosts|a:1:{s:12:\"10.235.32.10\";b:1;}admin|a:0:{}default|a:2:{s:9:\"_form_key\";s:16:\"e331ugBN7vRjGMgk\";s:12:\"visitor_data\";a:3:{s:13:\"last_visit_at\";s:19:\"2016-10-18 21:06:37\";s:10:\"session_id\";s:26:\"sgmeh2k3t7obl2tsot3h2ss0p1\";s:10:\"visitor_id\";s:1:\"9\";}}adminhtml|a:0:{}customer_base|a:1:{s:20:\"customer_segment_ids\";a:1:{i:1;a:0:{}}}checkout|a:0:{}" "lock" "0"
... more ...
```

### Redis ping コマンド

```bash
redis-cli ping
```

`PONG` は応答です。

両方のコマンドが成功した場合、Redis は正しく設定されます。

### 圧縮データの検査

圧縮されたセッションデータとページキャッシュを調べるには、 [RESP.app](https://flathub.org/apps/details/app.resp.RESP) は、Commerce 2 セッションとページのキャッシュの自動解凍をサポートし、PHP セッションデータを人間が読み取り可能な形式で表示します。

