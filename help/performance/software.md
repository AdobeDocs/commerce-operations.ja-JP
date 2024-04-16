---
title: ソフトウェアRecommendations
description: Adobe Commerceのデプロイメントの最適なパフォーマンスに関連する推奨ソフトウェアのリストを確認します。
feature: Best Practices, Install
exl-id: b091a733-7655-4e91-a988-93271872c5d5
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '1392'
ht-degree: 0%

---

# ソフトウェアの推奨事項

の実稼動インスタンスには、次のソフトウェアが必要です。 [!DNL Commerce]:

* [PHP](../installation/system-requirements.md)
* Nginx と [PHP-FPM](https://php-fpm.org/)
* [[!DNL MySQL]](../installation/prerequisites/database/mysql.md)
* [[!DNL Elasticsearch] または OpenSearch](../installation/prerequisites/search-engine/overview.md)

マルチサーバー環境の場合、またはビジネスの拡大・縮小を計画しているマーチャントの場合は、次の操作をお勧めします。

* [[!DNL Varnish] キャッシュ](../configuration/cache/config-varnish.md)
* [Redis](../configuration/cache/redis-session.md) セッションの場合（2.0.6 以降）
* 個別の Redis インスタンスを使用する [デフォルトキャッシュ](../configuration/cache/redis-pg-cache.md) （このインスタンスをページキャッシュに使用しない）

参照： [必要システム構成](../installation/system-requirements.md) サポートされている各タイプのソフトウェアのバージョンについては、を参照してください。

## オペレーティングシステム

オペレーティングシステムの設定と最適化は、以下の場合で似ています [!DNL Commerce] 他の高負荷 web アプリケーションと比較して。 サーバーが処理する同時接続の数が増えると、使用可能なソケットの数が完全に割り当てられることがあります。 Linux カーネルは、TCP 接続を「再利用」するメカニズムをサポートしている。 このメカニズムを有効にするには、で次の値を設定します `/etc/sysctl.conf`:

>[!INFO]
>
>net.ipv4.tcp_tw_reuse を有効にしても、着信接続には影響しません。

```text
net.ipv4.tcp_tw_reuse = 1
```

カーネルパラメーター `net.core.somaxconn` 接続待ちの開いているソケットの最大数を制御します。 この値は 1024 に安全に増やすことができますが、この量を処理するサーバーの機能と相関させる必要があります。 このカーネルパラメーターを有効にするには、次の値を設定します。 `/etc/sysctl.conf`:

```text
net.core.somaxconn = 1024
```

## PHP

Magentoは PHP 7.3 と 7.4 を完全にサポートしています。リクエスト処理の速度と効率を最大限に高めるために PHP を設定する際に考慮すべき要素はいくつかあります。

### PHP 拡張機能

有効な PHP 拡張モジュールのリストは、必要な拡張モジュールのリストに制限することをお勧めします [!DNL Commerce] 機能。

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
* 外部ナトリウム
* ext-tokenizer
* ext-xmlwriter
* ext-xsl
* ext-zip
* lib-libxml
* lib-openssl

また、Adobe Commerceには次の項目が必要です。

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
* 外部ナトリウム
* ext-spl
* ext-tokenizer
* ext-xmlwriter
* ext-xsl
* ext-zip
* lib-libxml
* lib-openssl

拡張機能を追加すると、ライブラリの読み込み時間が長くなります。

>[!INFO]
>
>`php-mcrypt` は PHP 7.2 から削除され、に置き換えられました。 [`sodium` ライブラリ](https://www.php.net/manual/en/book.sodium.php). を確実にする [ナトリウム](https://www.php.net/manual/en/sodium.installation.php) は、PHP のアップグレード時に適切に有効になります。

>[!INFO]
>
>プロファイリングとデバッグの拡張機能が存在すると、ページの応答時間に悪影響を与える可能性があります。 例えば、デバッグセッションがないアクティブな xDebug モジュールでは、ページの応答時間が最大 30% 長くなる可能性があります。

### PHP 設定

全ての実行が成功することを保証する [!DNL Commerce] データやコードをディスクにダンプしないインスタンスでは、次のようにメモリ制限を設定します。

```text
memory_limit=1G
```

デバッグの場合は、この値を 2G に増やします。

#### Realpath_cache 構成

改善する [!DNL Commerce] パフォーマンス、追加または更新を行う推奨手順 `realpath_cache` の設定 `php.ini` ファイル。 この設定により、PHP プロセスは、ページが読み込まれるたびにパスを検索する代わりに、ファイルへのパスをキャッシュすることができます。 参照： [パフォーマンスチューニング](https://www.php.net/manual/en/ini.core.php) PHP のドキュメントに書かれています。

```text
realpath_cache_size=10M
realpath_cache_ttl=7200
```

#### ByteCode

最大速度を出す [!DNL Commerce] php 7 では、OpCache モジュールを有効にし、適切に設定する必要があります。 モジュールには、次の設定をお勧めします。

```text
opcache.memory_consumption=512
opcache.max_accelerated_files=60000
opcache.consistency_checks=0
opcache.validate_timestamps=0
opcache.enable_cli=1
```

opcache のメモリ割り当てを微調整する場合、Magentoのコードベースとすべてのエクステンションのサイズを考慮します。 Magentoのパフォーマンス・チームは、インストールされた拡張機能の平均数に対して opcache に十分な領域を提供するため、前述の例の値をテストに使用します。

低メモリのマシンで、インストールされている拡張機能やカスタマイズの数が少ない場合は、次の設定を使用して同様の結果を得ます。

```text
opcache.memory_consumption=64
opcache.max_accelerated_files=60000
```

#### APCU

を有効にすることをお勧めします [PHP APCu 拡張モジュール](https://getcomposer.org/doc/articles/autoloader-optimization.md#optimization-level-2-b-apcu-cache) および [設定 `composer` 支持する](../performance/deployment-flow.md#preprocess-dependency-injection-instructions) 最大のパフォーマンスを得るために最適化します。 この拡張機能では、開いたファイルの場所をキャッシュするので、のパフォーマンスが向上します [!DNL Commerce] サーバーコール （ページ、Ajax 呼び出しおよびエンドポイントを含む）。

を編集 `apcu.ini` 次のファイルが含まれます。

```text
extension=apcu.so
[apcu]
apc.enabled = 1
```

## Web サーバー

Magentoは、Nginx および Apache web サーバーを完全にサポートしています。 [!DNL Commerce] には、推奨される設定ファイルのサンプルが  `<magento_home>/nginx.conf.sample` （Nginx）と  `<magento_home>.htaccess.sample` （Apache）ファイル。  Nginx サンプルには、パフォーマンスを向上させるための設定が含まれており、再設定をほとんど必要としないように設計されています。 サンプルファイルで定義されている主な設定のベストプラクティスには、次のものが含まれます。

* ブラウザーで静的コンテンツをキャッシュする設定
* PHP のメモリと実行時間の設定
* コンテンツ圧縮設定

また、次に示すように、入力リクエスト処理のスレッドの数を設定する必要があります。

| Web サーバー | 属性名 | 場所 | 関連情報 |
|--- | --- | --- | ---|
| Nginx | `worker_connections` | `/etc/nginx/nginx.conf` （Debian） | [パフォーマンスのための NGINX のチューニング](https://www.nginx.com/blog/tuning-nginx/) |
| Apache 2.2 | `MaxClients` | `/etc/httpd/conf/httpd.conf` （CentOS） | [Apache パフォーマンスチューニング](https://httpd.apache.org/docs/2.2/misc/perf-tuning.html) |
| Apache 2.4 | `MaxRequestWorkers` | `/etc/httpd/conf/httpd.conf` （CentOS） | [Apache MPM 共通ディレクティブ](https://httpd.apache.org/docs/2.4/mod/mpm_common.html#maxrequestworkers) |

## [!DNL MySQL]

このドキュメントでは、詳細は説明しません [!DNL MySQL] チューニングの手順ストアと環境はそれぞれ異なるので、一般的な推奨事項を作成できます。

～に対して多くの改善がなされてきた [!DNL MySQL] 5.7.9 私たちは以下を確信しています [!DNL MySQL] は、適切なデフォルト設定で配布されます。 最も重要な設定は次のとおりです。

| パラメーター | デフォルト | 説明 |
|--- | --- | ---|
| `innodb_buffer_pool_instances` | 8 | デフォルト値は 8 に設定されています。これにより、同じインスタンスに複数のスレッドがアクセスしようとする問題を回避できます。 |
| `innodb_buffer_pool_size` | 128MB | 前述の複数のプールインスタンスと組み合わせると、デフォルトのメモリ割り当ては 1024 MB になります。 合計サイズは、すべてのバッファ プールで分割されます。 最高の効率を得るには、次の組み合わせを指定します `innodb_buffer_pool_instances` および `innodb_buffer_pool_size` つまり、各バッファ・プール・インスタンスは 1 GB 以上になります。 |
| `max_connections` | 150 | の値 `max_connections` パラメーターは、アプリケーションサーバーで設定された PHP スレッドの合計数に関連付けられる必要があります。 一般的な推奨事項は、小規模の場合は 300、中規模の環境の場合は 1,000 です。 |
| `innodb_thread_concurrency` | 0 | この設定の最適な値は、次の式で計算される必要があります。 `innodb_thread_concurrency = 2 * (NumCPUs + NumDisks)` |

## [!DNL Varnish]

Magentoでは、次を使用することを強くお勧めします [!DNL Varnish] ストアのフルページキャッシュサーバーとして設定します。 PageCache モジュールはコードベースにまだ存在していますが、開発目的でのみ使用する必要があります。 次の代わりにと併用しないでください。 [!DNL Varnish].

インストール [!DNL Varnish] Web 層の前にある別のサーバー上。 すべての受信リクエストを受け入れ、キャッシュされたページコピーを提供する必要があります。 許可する [!DNL Varnish] セキュリティで保護されたページで効果的に動作させるには、SSL ターミネーションプロキシを以下の前面に配置します [!DNL Varnish]. Nginx はこの目的に使用できます。

[!DNL Commerce] サンプル構成ファイルを配布します [!DNL Varnish] （バージョン 4 および 5）に、パフォーマンスに関するすべての推奨設定が含まれています。 パフォーマンスの面で最も重要なものは次のとおりです。

* **バックエンドのヘルスチェック** をポーリングします [!DNL Commerce] サーバーが適切なタイミングで応答しているかどうかを判断します。
* **猶予モード** を指定できます [!DNL Varnish] 次の場合に、オブジェクトを有効期間（TTL）の期間を超えてキャッシュに保持し、この古いコンテンツを提供します [!DNL Commerce] は正常ではない、または新規コンテンツがまだ取得されていない場合。
* **セイント モード** 不健康なブラックリスト [!DNL Commerce] 設定可能な時間の間、サーバーにアクセスします。 その結果、不健康なバックエンドは、を使用する際にトラフィックを提供できません [!DNL Varnish] をロードバランサーとして使用します。

参照： [詳細 [!DNL Varnish] 設定](../configuration/cache/config-varnish-advanced.md) これらの機能の実装に関する詳細情報。

### アセットのパフォーマンスの最適化

通常、最適なパフォーマンスを得るには、アセット（画像、JS、CSS など）を CDN に保存することをお勧めします。

サイトに多数のロケールを導入する必要がなく、お客様の大半の顧客と同じ地域にサーバーを配置している場合、アセットをに保存することで、低コストで大幅なパフォーマンスの向上が得られる可能性があります [!DNL Varnish] cdn を使用する代わりに使用します。

アセットをに保存するには [!DNL Varnish]に以下の VCL エントリを追加します。 `default.vcl` 生成されたファイル [!DNL Commerce] （用） [!DNL Varnish] 5.

の最後 `if` での PURGE リクエストのステートメント `vcl_recv` サブルーチン、追加：

```javascript
# static files are cacheable. remove SSL flag and cookie

if (req.url ~ "^/(pub/)?(media|static)/.*\.(ico|html|css|js|jpg|jpeg|png|gif|tiff|bmp|mp3|ogg|svg|swf|woff|woff2|eot|ttf|otf)$") {
  unset req.http.Https;
  unset req.http./* {{ ssl_offloaded_header }} */;
  unset req.http.Cookie;
}
```

が含まれる `vcl_backend_response` サブルーチン、を探します。 `if` の cookie を設定解除するステートメント `GET` または `HEAD` リクエスト。
更新済み `if` ブロックは次のようになります。

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

を再起動します [!DNL Varnish] サイトのアップグレードやアセットのデプロイ/更新を行うたびに、キャッシュされたアセットをフラッシュするサーバー。

## キャッシュサーバーとセッションサーバー

Magentoは、Redis、Memcache、filesystem、database など、キャッシュとセッションデータを保存する多くのオプションを提供します。 これらのオプションの一部については、以下で説明します。

### 単一 Web ノードの設定

1 つの web ノードですべてのトラフィックを処理する予定がある場合、リモート Redis サーバーにキャッシュを配置しても意味がありません。 代わりに、ファイルシステムまたはローカルの Redis サーバーを使用します。 ファイルシステムを使用する場合は、RAM ファイルシステムにマウントされたボリュームにキャッシュフォルダーを配置します。 ローカルの Redis サーバーを使用する場合は、HTTP 経由でデータを交換するのではなく、直接接続にソケットを使用するように Redis を設定することを強くお勧めします。

### 複数の web ノードの設定

複数の Web ノードを設定する場合は、Redis が最適なオプションです。 なぜなら [!DNL Commerce] パフォーマンスを向上させるために大量のデータをアクティブにキャッシュし、web ノードと Redis サーバーの間のネットワークチャネルに注意を払います。 チャネルがリクエスト処理のボトルネックになることを望まない場合。

>[!INFO]
>
>何百何千もの同時リクエストに対応する必要がある場合は、Redis サーバーに最大 1 Gbit （またはそれ以上）のチャネルが必要になる場合があります。
