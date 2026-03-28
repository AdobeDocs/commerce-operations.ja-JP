---
title: セッション ストレージにValkeyを使用
description: Adobe Commerceでセッションストレージ用にValkeyを設定する方法を説明します。 セットアップ手順、設定オプション、パフォーマンス最適化テクニックをご覧ください。
feature: Configuration, Cache
exl-id: 986ddb5c-8fc5-4210-8a41-a29e3a7625b7
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 1%

---


# セッション ストレージにValkeyを使用

>[!IMPORTANT]
>
>続行する前に[Valkey](config-valkey.md#install-valkey)をインストールする必要があります。

Adobe Commerceには、Valkey セッションストレージを設定するためのコマンドラインオプションが用意されています。

`setup:config:set` コマンドを実行し、Valkey固有のパラメーターを指定します。

```bash
bin/magento setup:config:set --session-save=valkey --session-save-valkey-<parameter_name>=<parameter_value>...
```

- `--session-save=valkey`はValkey セッション ストレージを有効にします。 この機能が既に有効になっている場合は、このパラメーターを省略します。

- `--session-save-valkey-<parameter_name>=<parameter_value>`は、セッション ストレージを構成するパラメーター/値のペアのリストです：


>[!NOTE]
>
>**Adobe Commerce 2.4.9-alpha2**&#x200B;以降、**Valkey**&#x200B;は、ライセンスの変更により、CLI ツールのRedisを正式に置き換えました。 ValkeyはRedisのフォークであり、ほぼ同じ機能を維持しています。 **バージョン 2.4.8以前**&#x200B;の場合、Valkeyの設定に使用するCLI コマンドはRedisの場合と同じままとなり、シームレスな後方互換性を確保し、移行またはデュアル環境のサポートを簡素化します。 次の例は、Valkey固有のコマンドを示しています。

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-<parameter_name>=<parameter_value>...
```

| コマンドラインパラメーター | パラメーター名 | 意味 | デフォルト値 |
|----------------------------------------------|--- |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--- |
| session-save-valkey-host | ホスト | UNIX ソケットを使用している場合は、完全修飾ホスト名、IP アドレス、または絶対パス。 | localhost |
| session-save-valkey-port | ポート | Valkey サーバーのリッスン ポート。 | 6379 |
| session-save-valkey-password | パスワード | Valkey サーバーで認証が必要な場合にパスワードを指定します。 | empty |
| session-save-valkey-timeout | タイムアウト | 接続タイムアウト（秒単位）。 | 2.5 |
| session-save-valkey-persistent-id | persistent_identifier | 永続的な接続を有効にする一意の文字列（sess-db0など）。<br>[phpredisおよびphp-fpm](https://github.com/phpredis/phpredis/issues/70)に関する既知の問題。 |  |
| session-save-valkey-db | データベース | 一意のValkey データベース番号。データ損失から保護するために推奨されます。<br><br>**重要**: Valkeyを複数のタイプのキャッシュに使用する場合、データベース番号は異なる必要があります。 既定のキャッシュ データベース番号を`0`に、ページ キャッシュ データベース番号を`1`に、セッション ストレージ データベース番号を`2`に割り当てることをお勧めします。 | 0 |
| session-save-valkey-compression-threshold | compression_threshold | 圧縮を無効にするには、`0`に設定します（`suhosin.session.encrypt = On`の場合に推奨）。 | 2048 |
| session-save-valkey-compression-lib | compression_library | オプション：gzip、lzf、lz4またはsnappy。 | gzip |
| session-save-valkey-log-level | log_level | 次のいずれかに設定し、最小詳細から最大詳細の順にリストします。<ul><li>0 （緊急：最も重大なエラーのみ）<li>1 （アラート：即時のアクションが必要）<li>2 （クリティカル：アプリケーションコンポーネントが使用できません）<li>3 （エラー：実行時エラー。重要ではありませんが、監視する必要があります）<li>4 （警告：追加情報、推奨）<li>5 （注：正常だが重大な状態）<li>6 （情報：情報メッセージ）<li>7 （デバッグ：開発またはテスト用の情報のみ）</ul> | 1 |
| session-save-valkey-max-concurrency | max_concurrency | 1つのセッションでロックを待機できるプロセスの最大数。 大規模な実稼動クラスターの場合は、これをPHP プロセス数の10%以上に設定します。 | 6 |
| session-save-valkey-break-after-frontend | break_after_frontend | フロントエンド（ストアフロント）セッションのロックを解除するまでの待機時間（秒数）。 | 5 |
| session-save-valkey-break-after-adminhtml | break_after_adminhtml | Adminhtml （つまり、Admin）セッションのロックを解除する前に待機する秒数。 | 30 |
| session-save-valkey-first-lifetime | first_lifetime | 最初の書き込み時に非ボットのセッションの有効期間（秒単位）。または、`0`を使用して無効にします。 | 600 |
| session-save-valkey-bot-first-lifetime | bot_first_lifetime | 最初の書き込み時のボットのセッションの有効期間（秒単位）。または`0`を使用して無効にします。 | 60 |
| session-save-valkey-bot-lifetime | bot_lifetime | 後続の書き込み時のボットのセッションの有効期間（秒単位）、または`0`を使用して無効にします。 | 7200 |
| session-save-valkey-disable-locking | disable_locking | セッションロックを完全に無効にします。 | 0 （false） |
| session-save-valkey-min-lifetime | min_lifetime | セッションの最小有効期間（秒単位）。 | 60 |
| session-save-valkey-max-lifetime | max_lifetime | セッションの最大有効期間（秒）。 | 2592000 （720時間） |
| session-save-valkey-sentinel-master | sentinel_master | Valkey Sentinel マスター名。 | empty |
| session-save-valkey-sentinel-servers | sentinel_servers | Valkey Sentinel サーバーのリスト。コンマ区切りです。 | empty |
| session-save-valkey-sentinel-verify-master | sentinel_verify_master | Valkey Sentinel マスターステータス フラグを確認します。 | 0 （false） |
| session-save-valkey-sentinel-connect-retries | sentinel_connect_retries | 接続はセンチネルの再試行を行います。 | 5 |

## 例

次の例では、Valkeyをセッションデータストアとして設定し、ホストを`127.0.0.1`に設定し、ログレベルを`4`に設定し、データベース番号を`2`に設定します。 その他のパラメーターはすべてデフォルト値に設定されます。

```bash
bin/magento setup:config:set --session-save=valkey --session-save-valkey-host=127.0.0.1 --session-save-valkey-log-level=4 --session-save-valkey-db=2
```

>[!NOTE]
>
>**Adobe Commerce 2.4.9**&#x200B;以降、**Valkey**&#x200B;は、ライセンスの変更により、CLI ツールのRedisを正式に置き換えました。 ValkeyはRedisのフォークであり、ほぼ同じ機能を維持しています。 **バージョン 2.4.8以前**&#x200B;の場合、Valkeyの設定に使用するCLI コマンドはRedisの場合と同じままとなり、シームレスな後方互換性を確保し、移行またはデュアル環境のサポートを簡素化します。 次の例は、Valkey固有のコマンドを示しています。

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=127.0.0.1 --session-save-redis-log-level=4 --session-save-redis-db=2
```

### 結果

Commerceは、次のような行を`<magento_root>app/etc/env.php`に追加します。

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
>セッションレコードのTTLは、管理者で設定されているCookie Lifetimeの値を使用します。 Cookieの有効期間が`0`に設定されている場合（デフォルトは`3600`）、Valkey セッションはmin_lifetimeで指定された秒数で期限切れになります（デフォルトは`60`）。 この不一致は、Valkeyとセッション Cookieが`0`のライフタイム値をどのように解釈するかに違いがあるためです。 その動作が望ましくない場合は、min_lifetimeの値を増やします。

## Valkey接続の検証

ValkeyとCommerceが正常に連携していることを確認するには、Valkeyが動作しているサーバーにログインしてターミナルを開き、`valkey-cli monitor` コマンドまたは`redis-cli ping` コマンドを使用します。

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

予想される応答は`PONG`です。

両方のコマンドが成功した場合、Valkeyは適切に設定されます。

### 圧縮されたデータの検査

圧縮されたセッションデータとページキャッシュを調べるために、[RESP.app](https://flathub.org/apps/app.resp.RESP)は、Commerce 2のセッションとページキャッシュの自動解凍をサポートし、PHP セッションデータを人間が読み取り可能な形式で表示します。
