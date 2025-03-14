---
title: セッションストレージに Redis を使用
description: セッションストレージ用に Redis を設定する方法を説明します。
feature: Configuration, Cache
exl-id: f93f500d-65b0-4788-96ab-f1c3d2d40a38
source-git-commit: 3886bf261f8f9d2594602850bef9c54db03fb269
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 1%

---

# セッションストレージに Redis を使用

>[!IMPORTANT]
>
>続行する前に [Redis をインストール ](config-redis.md#install-redis) してください。


Commerceには、Redis セッションストレージを設定するためのコマンドラインオプションが追加されました。 以前のリリースでは、`<Commerce install dir>app/etc/env.php` ファイルを編集していました。 コマンドラインで検証を行う場合や、このコマンドラインを使用して設定することをお勧めしますが、`env.php` ファイルは編集できます。

`setup:config:set` コマンドを実行し、Redis 固有のパラメーターを指定します。

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-<parameter_name>=<parameter_value>...
```

ここで、

`--session-save=redis` は Redis セッションストレージを有効にします。 この機能が既に有効になっている場合は、このパラメーターを省略します。

セッションストレージを構成するパラメーターと値のペアのリストを `--session-save-redis-<parameter_name>=<parameter_value>` に示します。

| コマンドラインパラメーター | パラメーター名 | 意味 | デフォルト値 |
|--- |--- |--- |--- |
| session-save-redis-host | host | 完全修飾ホスト名、IP アドレス、または UNIX ソケットを使用する場合は絶対パス。 | localhost |
| session-save-redis-port | ポート | Redis サーバーリッスンポート。 | 6379 |
| session-save-redis-password | password | Redis サーバーが認証を要求する場合、パスワードを指定します。 | 空 |
| session-save-redis-timeout | timeout | 接続タイムアウト （秒）。 | 2.5 |
| session-save-redis-persistent-id | persistent_identifier | 永続接続を有効にする一意の文字列（例：sess-db0）。<br>[phpredis および php-fpm の既知の問題 ](https://github.com/phpredis/phpredis/issues/70)。 |
| session-save-redis-db | データベース | 一意の Redis データベース番号。データ損失から保護することをお勧めします。<br><br>**重要**：複数のタイプのキャッシュに Redis を使用する場合は、データベース番号が異なっている必要があります。 デフォルトのキャッシュ データベース番号を 0、ページ キャッシュ データベース番号を 1、セッション ストレージ データベース番号を 2 に割り当てることをお勧めします。 | 0 |
| session-save-redis-compression-threshold | compression_threshold | 0 に設定すると、圧縮が無効になります（`suhosin.session.encrypt = On` の場合に推奨）。<br>[64 KB を超える文字列の既知の問題 ](https://github.com/colinmollenhour/Cm_Cache_Backend_Redis/issues/18)。 | 2048 |
| session-save-redis-compression-lib | compression_library | オプション：gzip、lzf、lz4 または snappy。 | gzip |
| session-save-redis-log-level | log_level | 最小の詳細から最大の詳細の順にリストされた次のいずれかに設定します：<ul><li>0 （緊急：最も重大なエラーのみ）<li>1 （アラート：直ちにアクションが必要）<li>2 （重大：アプリケーションコンポーネントを使用できない）<li>3 （エラー：実行時エラー。重要ではありませんが監視する必要があります）<li>4 （警告：追加情報、推奨）<li>5 （注意：正常だが重大な状態）<li>6 （情報：情報メッセージ）<li>7 （デバッグ：開発またはテスト用の最も多い情報のみ）</ul> | 1 |
| session-save-redis-max-concurrency | max_concurrency | 1 つのセッションでロックを待機できるプロセスの最大数。 大規模な実稼動クラスターの場合は、これを PHP プロセス数の 10% 以上に設定します。 | 6 |
| session-save-redis-break-after-frontend | break_after_frontend | フロントエンド（ストアフロント）セッションのロックを解除しようとする前に待機する秒数。 | 5 |
| session-save-redis-break-after-adminhtml | break_after_adminhtml | 管理者（管理者） セッションのロックを解除しようとする前の待機秒数。 | 30 |
| session-save-redis-first-lifetime | first_lifetime | 最初の書き込み時の非ボットのセッションの有効期間（秒単位）。0 を使用すると無効になります。 | 600 |
| session-save-redis-bot-first-lifetime | bot_first_lifetime | 最初の書き込み時のボットのセッションの有効期間（秒単位）。0 を使用すると無効になります。 | 60 |
| session-save-redis-bot-lifetime | bot_lifetime | 以降の書き込み時のボットのセッションの有効期間（秒単位）。0 を使用すると無効になります。 | 7200 |
| session-save-redis-disable-locking | disable_locking | セッションロックを完全に無効にします。 | 0 （false） |
| session-save-redis-min-lifetime | min_lifetime | セッションの最短有効期間（秒単位）。 | 60 |
| session-save-redis-max-lifetime | max_lifetime | セッションの最長有効期間（秒単位）。 | 2592000 （720 時間） |
| session-save-redis-sentinel-master | sentinel_master | Redis Sentinel のマスター名 | 空 |
| session-save-redis-sentinel-servers | sentinel_server | Redis Sentinel サーバーのリスト、コンマ区切り | 空 |
| session-save-redis-sentinel-verify-master | sentinel_verify_master | Redis Sentinel マスターステータスフラグを確認します。 | 0 （false） |
| session-save-redis-sentinel-connect-retries | sentinel_connect_retries | 標識の接続再試行 | 5 |

## 例

次の例では、Redis をセッション データ ストアとして設定し、ホストを `127.0.0.1` に設定し、ログ レベルを 4 に設定し、データベース番号を 2 に設定します。 その他のパラメーターはすべてデフォルト値に設定されます。

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=127.0.0.1 --session-save-redis-log-level=4 --session-save-redis-db=2
```

### 結果

Commerceは、次のような行を `<magento_root>app/etc/env.php` に追加します。

```php
'session' => [
    'save' => 'redis',
    'redis' => [
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
        'max_lifetime' => '2592000',
    ],
],
```

>[!INFO]
>
>セッションレコードの TTL は、Cookie の有効期間の値を使用します。この値は、管理者で設定します。 Cookie の有効期間が 0 （デフォルトは 3600）に設定されている場合、Redis セッションは min_lifetime で指定された秒数（デフォルトは 60）で期限切れになります。 この不一致は、Redis とセッション Cookie がライフタイム値 0 を解釈する方法の違いによるものです。 この動作が望ましくない場合は、min_lifetime の値を増やします。

## Redis 接続の確認

Redis とCommerceが連携していることを確認するには、Redis を実行しているサーバにログインし、ターミナルを開いて Redis monitor コマンドまたは ping コマンドを使用します。

### Redis モニターコマンド

```bash
redis-cli monitor
```

セッションストレージ出力のサンプル：

```
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

応答は `PONG` のようになります。

両方のコマンドが成功すると、Redis が正しく設定されます。

### 圧縮データの検査

[RESP.app](https://flathub.org/apps/details/app.resp.RESP) は、圧縮されたセッションデータとページキャッシュを検査するために、Commerce 2 Session and Page cache の自動解凍をサポートし、PHP セッションデータを人間が読み取り可能な形式で表示します。
