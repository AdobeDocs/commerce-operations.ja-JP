---
title: ソフトウェアの推奨事項
description: Adobe Commerceの必要ソフトウェア構成と推奨事項について説明します。 本番環境でサポートされているバージョンと設定のベストプラクティスを確認します。
feature: Best Practices, Install
exl-id: b091a733-7655-4e91-a988-93271872c5d5
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '1488'
ht-degree: 0%
---
# ソフトウェアの推奨事項

実稼動インスタンス [!DNL Commerce]には次のソフトウェアが必要です：

* [PHP](../installation/system-requirements.md)
* Nginxおよび[PHP-FPM](https://www.php.net/manual/en/install.fpm.php)
* [[!DNL MySQL]](../installation/prerequisites/database/mysql.md)
* [[!DNL Elasticsearch]またはOpenSearch](../installation/prerequisites/search-engine/overview.md)

マルチサーバー展開の場合、またはビジネスの拡大を計画しているマーチャントの場合は、次をお勧めします。

* [[!DNL Varnish] キャッシュ](../configuration/cache/config-varnish.md)
* セッション用[Redis](../configuration/cache/redis-session.md) （2.0.6以降）
* [ デフォルトキャッシュ ](../configuration/cache/redis-pg-cache.md)として別のRedis インスタンスを使用します（このインスタンスをページキャッシュに使用しないでください）

各タイプのソフトウェアでサポートされているバージョンについて詳しくは、[必要システム構成](../installation/system-requirements.md)を参照してください。

## オペレーティングシステム

オペレーティングシステムの設定と最適化は、他の高負荷web アプリケーションと比較して[!DNL Commerce]で類似しています。 サーバーが処理する同時接続の数が増えると、利用可能なソケットの数が完全に割り当てられます。 Linux カーネルは、TCP接続を「再利用」するメカニズムをサポートしています。 このメカニズムを有効にするには、`/etc/sysctl.conf`に次の値を設定します。

>[!INFO]
>
>net.ipv4.tcp_tw_reuseを有効にしても、着信接続には影響しません。

```text
net.ipv4.tcp_tw_reuse = 1
```

カーネルパラメーター`net.core.somaxconn`は、接続を待機している開いているソケットの最大数を制御します。 この値は1024に安全に増やすことができますが、この量を処理するサーバーの能力と相関させる必要があります。 このカーネルパラメーターを有効にするには、`/etc/sysctl.conf`に次の値を設定します。

```text
net.core.somaxconn = 1024
```

## PHP

[必要システム構成](../installation/system-requirements.md)に記載されているように、インストール中のAdobe Commerce リリースでサポートされているPHP バージョンを使用します。 PHPを設定してリクエスト処理の速度と効率を最大化する場合は、いくつかの要素を考慮する必要があります。

### PHP拡張機能

アクティブなPHP拡張機能のリストは、[!DNL Commerce]機能に必要な拡張機能に制限することをお勧めします。

Magento Open SourceとAdobe Commerce:

* ext-bcmath
* ext-ctype
* ext-curl
* ext-dom
* ext-fileinfo
* ext-gd
* ext-hash
* ext-iconv
* ext-intl
* ext-json
* ext-libxml
* ext-mbstring
* ext-openssl
* ext-pcre
* ext-pdo_mysql
* ext-simplexml
* ext-soap
* ext-sockets
* ext-sodium
* ext-tokenizer
* ext-xmlwriter
* ext-xsl
* ext-zip
* lib-libxml
* lib-openssl

さらに、Adobe Commerceには次の機能が必要です。

* ext-bcmath
* ext-ctype
* ext-curl
* ext-dom
* ext-fileinfo
* ext-gd
* ext-hash
* ext-iconv
* ext-intl
* ext-json
* ext-libxml
* ext-mbstring
* ext-openssl
* ext-pcre
* ext-pdo_mysql
* ext-simplexml
* ext-soap
* ext-sockets
* ext-sodium
* ext-spl
* ext-tokenizer
* ext-xmlwriter
* ext-xsl
* ext-zip
* lib-libxml
* lib-openssl

拡張機能を追加すると、ライブラリの読み込み時間が増加します。

>[!INFO]
>
>`php-mcrypt`はPHP 7.2から削除され、[`sodium` ライブラリ ](https://www.php.net/manual/en/book.sodium.php)に置き換えられました。 PHPをアップグレードする際は、[ ナトリウム ](https://www.php.net/manual/en/sodium.installation.php)が適切に有効になっていることを確認してください。

>[!INFO]
>
>プロファイリング拡張機能とデバッグ拡張機能が存在すると、ページの応答時間に悪影響を及ぼす可能性があります。 例えば、デバッグセッションのないアクティブなxDebug モジュールでは、ページの応答時間が最大30%向上します。

### PHP設定

データまたはコードをディスクにダンプせずに、すべての[!DNL Commerce] インスタンスを正常に実行することを保証するには、メモリ制限を次のように設定します。

```text
memory_limit=1G
```

デバッグの場合は、この値を2Gに増やします。

#### Realpath_cache設定

[!DNL Commerce]のパフォーマンスを向上させるには、`php.ini` ファイルに次の推奨`realpath_cache`設定を追加または更新してください。 この設定を使用すると、PHP プロセスは、ページが読み込まれるたびにファイルを検索するのではなく、ファイルにパスをキャッシュできます。 PHP ドキュメントの[ パフォーマンスチューニング ](https://www.php.net/manual/en/ini.core.php)を参照してください。

```text
realpath_cache_size=10M
realpath_cache_ttl=7200
```

#### ByteCode

[!DNL Commerce]から最大速度を得るには、OpCache モジュールをアクティブ化し、適切に設定する必要があります。 モジュールには、次の設定をお勧めします。

```text
opcache.memory_consumption=512
opcache.max_accelerated_files=60000
opcache.consistency_checks=0
opcache.validate_timestamps=0
opcache.enable_cli=1
```

opcacheのメモリ割り当てを微調整する場合は、Magentoのコードベースのサイズとすべての拡張機能を考慮してください。 Magentoのパフォーマンスチームは、インストールされている拡張機能の平均数に対してopcacheに十分なスペースを提供するため、テストに上記の例の値を使用します。

低メモリのマシンがあり、多くの拡張機能やカスタマイズがインストールされていない場合は、次の設定を使用して同様の結果を得ます。

```text
opcache.memory_consumption=64
opcache.max_accelerated_files=60000
```

#### APCU

[PHP APCu拡張機能](https://getcomposer.org/doc/articles/autoloader-optimization.md#optimization-level-2-b-apcu-cache)と[を有効にして、パフォーマンスを最大化するために](../performance/deployment-flow.md#preprocess-dependency-injection-instructions)をサポートするように`composer`を設定することをお勧めします。 この拡張機能は、開いているファイルのファイルの場所をキャッシュします。これにより、ページ、Ajax呼び出し、エンドポイントを含む[!DNL Commerce] サーバー呼び出しのパフォーマンスが向上します。

`apcu.ini` ファイルを編集して、次の内容を含めます。

```text
extension=apcu.so
[apcu]
apc.enabled = 1
```

## Web サーバー

Magentoは、NginxおよびApacheのweb サーバーを完全にサポートしています。 [!DNL Commerce]は、`<magento_home>/nginx.conf.sample` （Nginx）および`<magento_home>.htaccess.sample` （Apache）ファイルに推奨される構成ファイルのサンプルを提供します。  Nginxのサンプルには、パフォーマンスを向上させるための設定が含まれており、再構成が少ない必要があるように設計されています。 サンプルファイルで定義される主な設定のベストプラクティスには、次のものが含まれます。

* ブラウザーで静的コンテンツをキャッシュするための設定
* PHPのメモリと実行時間の設定
* コンテンツ圧縮設定

また、次に示すように、入力リクエスト処理のスレッド数を設定する必要があります。

| Web サーバー | 属性名 | ロケーション | 関連情報 |
|--- | --- | --- | ---|
| Nginx | `worker_connections` | `/etc/nginx/nginx.conf` （Debian） | [ パフォーマンス用NGINXのチューニング ](https://www.f5.com/company/blog/nginx/tuning-nginx) |
| Apache 2.4 | `MaxRequestWorkers` | `/etc/httpd/conf/httpd.conf` （CentOS） | [Apache MPM共通ディレクティブ ](https://httpd.apache.org/docs/2.4/mod/mpm_common.html#maxrequestworkers) |

## [!DNL MySQL]

このドキュメントでは、各ストアと環境が異なるため、詳細な[!DNL MySQL]の調整手順は提供されていませんが、一般的な推奨事項をいくつか確認できます。

最近の[!DNL MySQL]件のリリースには多くのパフォーマンス改善が含まれており、[!DNL MySQL]は一般的に適切なデフォルト設定で配布されています。 最も重要な設定は次のとおりです。

| パラメーター | Default | 説明 |
|--- | --- | ---|
| `innodb_buffer_pool_instances` | 8 | デフォルト値は8に設定され、複数のスレッドが同じインスタンスにアクセスしようとする問題を回避します。 |
| `innodb_buffer_pool_size` | 128MB | 上記の複数のプールインスタンスと組み合わせると、デフォルトのメモリ割り当て量は1024 MBになります。 合計サイズは、すべてのバッファープール間で分割されます。 最高の効率を得るには、各バッファープールインスタンスが1 GB以上になるように、`innodb_buffer_pool_instances`と`innodb_buffer_pool_size`の組み合わせを指定します。 |
| `max_connections` | 150 | `max_connections` パラメーターの値は、アプリケーションサーバーで設定されたPHP スレッドの合計数と関連付ける必要があります。 一般的な推奨事項は、小規模の場合は300、中規模の環境の場合は1,000です。 |
| `innodb_thread_concurrency` | 0 | この設定の最適な値は、次の式で計算する必要があります：`innodb_thread_concurrency = 2 * (NumCPUs + NumDisks)` |

## [!DNL Varnish]

Magentoでは、ストアのフルページキャッシュサーバーとして[!DNL Varnish]を使用することを強くお勧めします。 PageCache モジュールは引き続きコードベースに存在しますが、開発目的でのみ使用する必要があります。 [!DNL Varnish]と一緒に、またはの代わりに使用しないでください。

Web層の前にある別のサーバーに[!DNL Varnish]をインストールします。 すべての受信リクエストを受け入れ、キャッシュされたページコピーを提供する必要があります。 [!DNL Varnish]がセキュリティで保護されたページで効果的に作業できるようにするには、SSL終了プロキシを[!DNL Varnish]の前に配置します。 Nginxは、この目的で使用できます。

[!DNL Commerce]は、パフォーマンスのすべての推奨設定を含む、サポートされている[!DNL Varnish] バージョンのサンプル設定ファイルを配布します。 その中でもパフォーマンスに関して最も重要なのは次の通りです。

* **バックエンド ヘルスチェック**&#x200B;は、[!DNL Commerce] サーバーをポーリングして、タイムリーに応答しているかどうかを判断します。
* **猶予モード**&#x200B;を使用すると、[!DNL Varnish]に対して、オブジェクトを有効期間（TTL）を超えてキャッシュに保持するように指示できます。また、[!DNL Commerce]が正常でない場合や、新しいコンテンツがまだ取得されていない場合は、この古いコンテンツを提供できます。
* **Saint mode**&#x200B;は、設定可能な時間に対して異常な[!DNL Commerce] サーバーをブラックリストに登録します。 その結果、[!DNL Varnish]をロードバランサーとして使用する場合、正常でないバックエンドはトラフィックを提供できません。

これらの機能の実装について詳しくは、[詳細 [!DNL Varnish] 設定](../configuration/cache/config-varnish-advanced.md)を参照してください。

### アセットのパフォーマンスを最適化

一般的に、最適なパフォーマンスを実現するために、アセット（画像、JS、CSSなど）をCDNに保存することをお勧めします。

サイトで多数のロケールをデプロイする必要がなく、サーバーが大部分の顧客と同じ地域にある場合は、CDNを使用する代わりに[!DNL Varnish]にアセットを保存することで、パフォーマンスが大幅に向上する可能性があります。

アセットを[!DNL Varnish]に保存するには、[!DNL Commerce]によって生成された`default.vcl` ファイルに次のVCL エントリを追加します。

`vcl_recv` サブルーチンのPURGE リクエストの`if` ステートメントの最後に、次を追加します。

```javascript
# static files are cacheable. remove SSL flag and cookie

if (req.url ~ "^/(pub/)?(media|static)/.*\.(ico|html|css|js|jpg|jpeg|png|gif|tiff|bmp|mp3|ogg|svg|swf|woff|woff2|eot|ttf|otf)$") {
  unset req.http.Https;
  unset req.http./* {{ ssl_offloaded_header }} */;
  unset req.http.Cookie;
}
```

`vcl_backend_response` サブルーチンで、`GET`または`HEAD`要求のCookieを設定解除する`if` ステートメントを探します。
更新された`if` ブロックは次のようになります。

```javascript
# validate if we need to cache it and prevent from setting cookie
# images, css and js are cacheable by default so we have to remove cookie also

if (beresp.ttl > 0s && (bereq.method == "GET" || bereq.method == "HEAD")) {
  unset beresp.http.set-cookie;
if (bereq.url !~ "\.(ico|css|js|jpg|jpeg|png|gif|tiff|bmp|gz|tgz|bz2|tbz|mp3|ogg|svg|swf|woff|woff2|eot|ttf|otf)(\?|$)") {
  set beresp.http.Pragma = "no-cache";
  set beresp.http.Expires = "-1";
  set beresp.http.Cache-Control = "no-store, no-cache, must-revalidate, max-age=0";
  }
}
```

サイトをアップグレードするか、アセットをデプロイまたは更新するたびに、キャッシュされたアセットをフラッシュするには、[!DNL Varnish] サーバーを再起動します。

## キャッシュおよびセッションサーバー

Magentoには、Redis、Memcache、ファイルシステム、データベースなど、キャッシュおよびセッションデータを保存するための多くのオプションが用意されています。 これらのオプションの一部については、以下で説明します。

### 単一のweb ノードの設定

1つのweb ノードだけであらゆるトラフィックを処理する場合、キャッシュをリモート Redis サーバーに配置することは意味がありません。 代わりに、ファイルシステムまたはローカルのRedis サーバーを使用してください。 ファイルシステムを使用する場合は、RAM ファイルシステムにマウントされたボリュームにキャッシュフォルダーを配置します。 ローカル Redis サーバーを使用する場合は、HTTP経由でデータを交換するのではなく、直接接続にソケットを使用するようにRedisを設定することを強くお勧めします。

### 複数のweb ノードの設定

複数のweb ノードを設定する場合は、Redisが最適なオプションです。 [!DNL Commerce]はパフォーマンスを向上させるために大量のデータを積極的にキャッシュするので、Web ノードとRedis サーバー間のネットワーク チャネルに注意してください。 チャネルをリクエスト処理のボトルネックにしたくはありません。

>[!INFO]
>
>何十万もの同時リクエストを処理する必要がある場合、Redis サーバーに最大1 Gbit （またはさらに広い）のチャネルが必要になる場合があります。
