---
title: セッションストレージに Valkey を使用
description: セッションストレージ用の Valkey を設定する方法を説明します。
feature: Configuration, Cache
source-git-commit: 1850301e0b7f1abbc54613209940dd63d16ef145
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 1%

---

# セッションストレージに Valkey を使用

>[!IMPORTANT]
>
>続行する前に [Valkey をインストール ](config-valkey.md#install-valkey) する必要があります。

Adobe Commerceには、Valkey セッションストレージを設定するためのコマンドラインオプションが用意されています。

`setup:config:set` コマンドを実行し、Valkey 固有のパラメーターを指定します。

```bash
bin/magento setup:config:set --session-save=valkey --session-save-valkey-<parameter_name>=<parameter_value>...
```

- `--session-save=valkey` は、Valkey セッションストレージを有効にします。 この機能が既に有効になっている場合は、このパラメーターを省略します。

- セッションストレージを構成するパラメーターと値のペアのリストを `--session-save-valkey-<parameter_name>=<parameter_value>` に示します。

| コマンドラインパラメーター | パラメーター名 | 意味 | デフォルト値 |
|----------------------------------------------|--- |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--- |
| session-save-valkey-host | host | 完全修飾ホスト名、IP アドレス、または UNIX ソケットを使用する場合は絶対パス。 | localhost |
| session-save-valkey-port | ポート | 有効なサーバーリッスンポート。 | 6379 |
| session-save-valkey-password | password | Valkey サーバーで認証が必要な場合にパスワードを指定します。 | 空 |
| session-save-valkey-timeout | timeout | 接続タイムアウト （秒）。 | 2.5 |
| session-save-valkey-persistent-id | persistent_identifier | 永続接続を有効にする一意の文字列（例：sess-db0）。<br>[phpredis および php-fpm の既知の問題 ](https://github.com/phpredis/phpredis/issues/70)。 |
| session-save-valkey-db | データベース | 一意の Valkey データベース番号。データの損失から保護することをお勧めします。<br><br>**重要**：複数のタイプのキャッシュに Valkey を使用する場合、データベース番号は異なる必要があります。 デフォルトのキャッシュ・データベース番号を `0`、ページ・キャッシュ・データベース番号を `1`、セッション・ストレージ・データベース番号を `2` に割り当てることをお勧めします。 | 0 |
| session-save-valkey-compression-threshold | compression_threshold | 圧縮を無効にするには、`0` に設定します（`suhosin.session.encrypt = On` の場合に推奨されます）。 | 2048 |
| session-save-valkey-compression-lib | compression_library | オプション：gzip、lzf、lz4 または snappy。 | gzip |
| session-save-valkey-log-level | log_level | 最小の詳細から最大の詳細の順にリストされた次のいずれかに設定します：<ul><li>0 （緊急：最も重大なエラーのみ）<li>1 （アラート：直ちにアクションが必要）<li>2 （重大：アプリケーションコンポーネントを使用できない）<li>3 （エラー：実行時エラー。重要ではありませんが監視する必要があります）<li>4 （警告：追加情報、推奨）<li>5 （注意：正常だが重大な状態）<li>6 （情報：情報メッセージ）<li>7 （デバッグ：開発またはテスト用の最も多い情報のみ）</ul> | 1 |
| session-save-valkey-max-concurrency | max_concurrency | 1 つのセッションでロックを待機できるプロセスの最大数。 大規模な実稼動クラスターの場合は、これを PHP プロセス数の 10% 以上に設定します。 | 6 |
| session-save-valkey-break-after-frontend | break_after_frontend | フロントエンド（ストアフロント）セッションのロックを解除しようとする前に待機する秒数。 | 5 |
| session-save-valkey-break-after-adminhtml | break_after_adminhtml | 管理者（管理者） セッションのロックを解除しようとする前の待機秒数。 | 30 |
| session-save-valkey-first-lifetime | first_lifetime | 最初の書き込み時の非ボットのセッションの有効期間（秒）、または `0` を使用して無効にします。 | 600 |
| session-save-valkey-bot-first-lifetime | bot_first_lifetime | 最初の書き込み時のボットのセッションの有効期間（秒単位）。または、`0` を使用して無効にします。 | 60 |
| session-save-valkey-bot-lifetime | bot_lifetime | 以降の書き込み時のボットのセッションの有効期間（秒単位）。または、`0` を使用して無効にします。 | 7200 |
| session-save-valkey-disable-locking | disable_locking | セッションロックを完全に無効にします。 | 0 （false） |
| session-save-valkey-min-lifetime | min_lifetime | セッションの最短有効期間（秒単位）。 | 60 |
| session-save-valkey-max-lifetime | max_lifetime | セッションの最長有効期間（秒単位）。 | 2592000 （720 時間） |
| session-save-valkey-sentinel-master | sentinel_master | Valkey Sentinel のマスター名。 | 空 |
| session-save-valkey-sentinel-servers | sentinel_server | Valkey Sentinel サーバーのリスト （コンマ区切り）。 | 空 |
| session-save-valkey-sentinel-verify-master | sentinel_verify_master | Valkey Sentinel のマスターステータスフラグを確認します。 | 0 （false） |
| session-save-valkey-sentinel-connect-retries | sentinel_connect_retries | センサーの接続が再試行されます。 | 5 |

## 例

次の例では、Valkey をセッション・データ・ストアとして設定し、ホストを `127.0.0.1` に設定し、ログ・レベルを `4` に設定し、データベース番号を `2` に設定します。 その他のパラメーターはすべてデフォルト値に設定されます。

```bash
bin/magento setup:config:set --session-save=valkey --session-save-valkey-host=127.0.0.1 --session-save-valkey-log-level=4 --session-save-valkey-db=2
```

### 結果

Commerceは、次のような行を `<magento_root>app/etc/env.php` に追加します。

```php
'session' => [
    'save' => 'valkey',
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
>セッションレコードの TTL は、Cookie の有効期間の値を使用します。この値は、管理者で設定します。 Cookie の有効期間が `0` に設定されている場合（デフォルトは `3600`）、Valkey セッションは min_lifetime に指定された秒数で期限切れになります（デフォルトは `60`）。 この不一致は、Valkey Cookie とセッション Cookie が `0` のライフタイム値を解釈する方法の違いによるものです。 この動作が望ましくない場合は、min_lifetime の値を増やします。

## Valkey 接続の確認

Valkey とCommerceが正しく連携していることを確認するには、Valkey が動作しているサーバーにログインし、ターミナルを開いて `valkey-cli monitor` コマンドまたは `redis-cli ping` コマンドを使用します。

### Valkey monitor コマンド

```bash
valkey-cli monitor
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

### Valkey ping コマンド

```bash
valkey-cli ping
```

期待される応答は `PONG` です。

両方のコマンドが成功した場合は、Valkey が正しく設定されています。

### 圧縮データの検査

[RESP.app](https://flathub.org/apps/app.resp.RESP) は、圧縮されたセッションデータとページキャッシュを検査するために、Commerce 2 セッションとページキャッシュの自動解凍をサポートし、PHP セッションデータを人間が読み取り可能なフォーマットで表示します。
