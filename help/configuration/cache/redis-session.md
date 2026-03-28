---
title: セッション ストレージにRedisを使用
description: Adobe Commerceでセッションストレージ用にRedisを設定する方法について説明します。 コマンドラインのセットアップ、設定オプション、パフォーマンスの最適化手法について説明します。
feature: Configuration, Cache
exl-id: f93f500d-65b0-4788-96ab-f1c3d2d40a38
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 1%

---

# セッション ストレージにRedisを使用

>[!IMPORTANT]
>
>続行する前に、[Redis](config-redis.md#install-redis)をインストールする必要があります。


Commerceには、Redis セッションストレージを設定するためのコマンドラインオプションが用意されています。 以前のリリースでは、`<Commerce install dir>app/etc/env.php` ファイルを編集しました。 コマンドラインは検証を提供し、推奨される設定方法ですが、`env.php` ファイルは引き続き編集できます。

`setup:config:set` コマンドを実行し、Redis固有のパラメーターを指定します。

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-<parameter_name>=<parameter_value>...
```

どこで

`--session-save=redis`はRedis セッション ストレージを有効にします。 この機能が既に有効になっている場合は、このパラメーターを省略します。

`--session-save-redis-<parameter_name>=<parameter_value>`は、セッション ストレージを構成するパラメーター/値のペアのリストです：

| コマンドラインパラメーター | パラメーター名 | 意味 | デフォルト値 |
|--- |--- |--- |--- |
| session-save-redis-host | ホスト | UNIX ソケットを使用している場合は、完全修飾ホスト名、IP アドレス、または絶対パス。 | localhost |
| session-save-redis-port | ポート | Redis サーバーのリッスン ポート。 | 6379 |
| session-save-redis-password | パスワード | Redis サーバーで認証が必要な場合にパスワードを指定します。 | empty |
| session-save-redis-timeout | タイムアウト | 接続タイムアウト（秒単位）。 | 2.5 |
| session-save-redis-persistent-id | persistent_identifier | 永続的な接続を有効にする一意の文字列（sess-db0など）。<br>[phpredisおよびphp-fpm](https://github.com/phpredis/phpredis/issues/70)に関する既知の問題。 |  |
| session-save-redis-db | データベース | 一意のRedis データベース番号。データ損失から保護するために推奨されます。<br><br>**重要**：複数のタイプのキャッシュにRedisを使用する場合、データベース番号は異なる必要があります。 デフォルトのキャッシングデータベース番号を0に、ページキャッシングデータベース番号を1に、セッションストレージデータベース番号を2に割り当てることをお勧めします。 | 0 |
| session-save-redis-compression-threshold | compression_threshold | 圧縮を無効にするには0に設定します（`suhosin.session.encrypt = On`の場合に推奨）。<br>[64 KBを超える文字列に関する既知の問題](https://github.com/colinmollenhour/Cm_Cache_Backend_Redis/issues/18)。 | 2048 |
| session-save-redis-compression-lib | compression_library | オプション：gzip、lzf、lz4またはsnappy。 | gzip |
| session-save-redis-log-level | log_level | 次のいずれかに設定し、最小詳細から最大詳細の順にリストします。<ul><li>0 （緊急：最も重大なエラーのみ）<li>1 （アラート：即時のアクションが必要）<li>2 （クリティカル：アプリケーションコンポーネントが使用できません）<li>3 （エラー：実行時エラー。重要ではありませんが、監視する必要があります）<li>4 （警告：追加情報、推奨）<li>5 （注：正常だが重大な状態）<li>6 （情報：情報メッセージ）<li>7 （デバッグ：開発またはテスト用の情報のみ）</ul> | 1 |
| session-save-redis-max-concurrency | max_concurrency | 1つのセッションでロックを待機できるプロセスの最大数。 大規模な実稼動クラスターの場合は、これをPHP プロセス数の10%以上に設定します。 | 6 |
| session-save-redis-break-after-frontend | break_after_frontend | フロントエンド（ストアフロント）セッションのロックを解除するまでの待機時間（秒数）。 | 5 |
| session-save-redis-break-after-adminhtml | break_after_adminhtml | Adminhtml （つまり、Admin）セッションのロックを解除する前に待機する秒数。 | 30 |
| session-save-redis-first-lifetime | first_lifetime | 最初の書き込み時に非ボットのセッションの有効期間（秒単位）。または0を使用して無効にします。 | 600 |
| session-save-redis-bot-first-lifetime | bot_first_lifetime | 最初の書き込み時のボットのセッションのライフタイム（秒単位）または0を使用して無効にします。 | 60 |
| session-save-redis-bot-lifetime | bot_lifetime | 後続の書き込み時のボットのセッションの有効期間（秒単位）、または0を使用して無効にします。 | 7200 |
| session-save-redis-disable-locking | disable_locking | セッションロックを完全に無効にします。 | 0 （false） |
| session-save-redis-min-lifetime | min_lifetime | セッションの最小有効期間（秒単位）。 | 60 |
| session-save-redis-max-lifetime | max_lifetime | セッションの最大有効期間（秒）。 | 2592000 （720時間） |
| session-save-redis-sentinel-master | sentinel_master | Redis Sentinel マスター名 | empty |
| session-save-redis-sentinel-servers | sentinel_servers | Redis Sentinel サーバーのリスト （コンマ区切り） | empty |
| session-save-redis-sentinel-verify-master | sentinel_verify_master | Redis Sentinel マスターステータス フラグの検証 | 0 （false） |
| session-save-redis-sentinel-connect-retries | sentinel_connect_retries | センチネルの接続の再試行 | 5 |

## 例

次の例では、Redisをセッションデータストアとして設定し、ホストを`127.0.0.1`に設定し、ログレベルを4に設定し、データベース番号を2に設定します。 その他のパラメーターはすべてデフォルト値に設定されます。

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=127.0.0.1 --session-save-redis-log-level=4 --session-save-redis-db=2
```

### 結果

Commerceは、次のような行を`<magento_root>app/etc/env.php`に追加します。

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
>セッションレコードのTTLは、管理者で設定されているCookie Lifetimeの値を使用します。 Cookieの有効期間が0に設定されている場合（デフォルトは3600）、Redis セッションはmin_lifetimeで指定された秒数（デフォルトは60）で期限切れになります。 この不一致は、Redisとセッション Cookieが生涯値0をどのように解釈するかによる違いによるものです。 その動作が望ましくない場合は、min_lifetimeの値を増やします。

## Redis接続の確認

RedisとCommerceが連携していることを確認するには、Redisを実行しているサーバーにログインしてターミナルを開き、Redis monitor コマンドまたはping コマンドを使用します。

### Redis monitor コマンド

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

`PONG`は応答である必要があります。

両方のコマンドが成功した場合、Redisは適切に設定されます。

### 圧縮されたデータの検査

圧縮されたセッションデータとページキャッシュを調べるために、[RESP.app](https://flathub.org/apps/details/app.resp.RESP)は、Commerce 2 セッションとページキャッシュの自動解凍をサポートし、PHP セッションデータを人間が読み取り可能な形式で表示します。
