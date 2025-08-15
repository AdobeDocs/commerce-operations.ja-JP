---
title: ソフトウェアの推奨事項
description: Adobe Commerceのデプロイメントの最適なパフォーマンスに関連する推奨ソフトウェアのリストを確認します。
feature: Best Practices, Install
exl-id: b091a733-7655-4e91-a988-93271872c5d5
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '1392'
ht-degree: 0%

---

# ソフトウェアの推奨事項

[!DNL Commerce] の実稼動インスタンスには、次のソフトウェアが必要です。

* [PHP](../installation/system-requirements.md)
* Nginx と [PHP-FPM](https://php-fpm.org/)
* [[!DNL MySQL]](../installation/prerequisites/database/mysql.md)
* [[!DNL Elasticsearch] または OpenSearch](../installation/prerequisites/search-engine/overview.md)

マルチサーバー環境の場合、またはビジネスの拡大・縮小を計画しているマーチャントの場合は、次の操作をお勧めします。

* [[!DNL Varnish] キャッシュ](../configuration/cache/config-varnish.md)
* セッション用 [Redis](../configuration/cache/redis-session.md) （2.0.6 以降）
* [ デフォルトキャッシュ ](../configuration/cache/redis-pg-cache.md) として個別の Redis インスタンスを使用します（ページキャッシュにはこのインスタンスを使用しないでください）。

各タイプのソフトウェアでサポートされるバージョンの詳細については、[ システム要件 ](../installation/system-requirements.md) を参照してください。

## オペレーティングシステム

オペレーティングシステムの設定と最適化は、他の高負荷 web アプリケーションと比較して、[!DNL Commerce] で同様です。 サーバーが処理する同時接続の数が増えると、使用可能なソケットの数が完全に割り当てられることがあります。 Linux カーネルは、TCP 接続を「再利用」するメカニズムをサポートしている。 このメカニズムを有効にするには、`/etc/sysctl.conf` に次の値を設定します。

>[!INFO]
>
>net.ipv4.tcp_tw_reuse を有効にしても、着信接続には影響しません。

```text
net.ipv4.tcp_tw_reuse = 1
```

カーネルパラメータ `net.core.somaxconn` は、接続を待っている開いているソケットの最大数を制御します。 この値は 1024 に安全に増やすことができますが、この量を処理するサーバーの機能と相関させる必要があります。 このカーネルパラメーターを有効にするには、`/etc/sysctl.conf` に次の値を設定します。

```text
net.core.somaxconn = 1024
```

## PHP

Magentoは PHP 7.3 および 7.4 を完全にサポートしています。リクエスト処理の速度と効率を最大限に高めるために PHP を設定する際に考慮すべき要素はいくつかあります。

### PHP 拡張機能

アクティブな PHP 拡張モジュールのリストは、[!DNL Commerce] の機能に必要なものに制限することをお勧めします。

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
>`php-mcrypt` は PHP 7.2 から削除され、[`sodium` ライブラリ ](https://www.php.net/manual/en/book.sodium.php) に置き換えられました。 PHP のアップグレード時に [sodium](https://www.php.net/manual/en/sodium.installation.php) が適切に有効になっていることを確認してください。

>[!INFO]
>
>プロファイリングとデバッグの拡張機能が存在すると、ページの応答時間に悪影響を与える可能性があります。 例えば、デバッグセッションがないアクティブな xDebug モジュールでは、ページの応答時間が最大 30% 長くなる可能性があります。

### PHP 設定

データやコードをディスクにダンプせずに、すべての [!DNL Commerce] インスタンスが正常に実行されるようにするには、次のようにメモリ制限を設定します。

```text
memory_limit=1G
```

デバッグの場合は、この値を 2G に増やします。

#### Realpath_cache 構成

[!DNL Commerce] のパフォーマンスを向上させるには、`realpath_cache` ファイルで以下の推奨 `php.ini` 設定を追加または更新します。 この設定により、PHP プロセスは、ページが読み込まれるたびにパスを検索する代わりに、ファイルへのパスをキャッシュすることができます。 PHP ドキュメントの [ パフォーマンスチューニング ](https://www.php.net/manual/en/ini.core.php) を参照してください。

```text
realpath_cache_size=10M
realpath_cache_ttl=7200
```

#### ByteCode

PHP 7 上で [!DNL Commerce] から最大の速度を得るには、OpCache モジュールを有効にし、適切に設定しなければなりません。 モジュールには、次の設定をお勧めします。

```text
opcache.memory_consumption=512
opcache.max_accelerated_files=60000
opcache.consistency_checks=0
opcache.validate_timestamps=0
opcache.enable_cli=1
```

opcache のメモリ割り当てを微調整する場合は、Magentoのコードベースとすべてのエクステンションのサイズを考慮します。 Magento performance team は、インストールされた拡張機能の平均数に対して opcache に十分な領域を提供するので、上記の例の値をテストに使用します。

低メモリのマシンで、インストールされている拡張機能やカスタマイズの数が少ない場合は、次の設定を使用して同様の結果を得ます。

```text
opcache.memory_consumption=64
opcache.max_accelerated_files=60000
```

#### APCU

[PHP APCu 拡張モジュールを有効にし ](https://getcomposer.org/doc/articles/autoloader-optimization.md#optimization-level-2-b-apcu-cache) それをサポートするために [ を設定する `composer` を有効にして、パフォーマンスを最大限に高めるための最適化を行うことをお勧めします ](../performance/deployment-flow.md#preprocess-dependency-injection-instructions) この拡張機能では、開いたファイルの場所をキャッシュするので、ページ、Ajax 呼び出し、エンドポイントを含む [!DNL Commerce] サーバー呼び出しのパフォーマンスが向上します。

`apcu.ini` ファイルを編集して、以下を含めます。

```text
extension=apcu.so
[apcu]
apc.enabled = 1
```

## Web サーバー

Magentoは、Nginx web サーバーと Apache web サーバーを完全にサポートしています。 [!DNL Commerce] には、`<magento_home>/nginx.conf.sample` （Nginx）ファイルと `<magento_home>.htaccess.sample` （Apache）ファイルで推奨される設定ファイルのサンプルが用意されています。  Nginx サンプルには、パフォーマンスを向上させるための設定が含まれており、再設定をほとんど必要としないように設計されています。 サンプルファイルで定義されている主な設定のベストプラクティスには、次のものが含まれます。

* ブラウザーで静的コンテンツをキャッシュする設定
* PHP のメモリと実行時間の設定
* コンテンツ圧縮設定

また、次に示すように、入力リクエスト処理のスレッドの数を設定する必要があります。

| Web サーバー | 属性名 | 場所 | 関連情報 |
|--- | --- | --- | ---|
| Nginx | `worker_connections` | `/etc/nginx/nginx.conf` （Debian） | [ パフォーマンスのための NGINX のチューニング ](https://www.nginx.com/blog/tuning-nginx/) |
| Apache 2.2 | `MaxClients` | `/etc/httpd/conf/httpd.conf` （CentOS） | [Apache パフォーマンスチューニング ](https://httpd.apache.org/docs/2.2/misc/perf-tuning.html) |
| Apache 2.4 | `MaxRequestWorkers` | `/etc/httpd/conf/httpd.conf` （CentOS） | [Apache MPM 共通ディレクティブ ](https://httpd.apache.org/docs/2.4/mod/mpm_common.html#maxrequestworkers) |

## [!DNL MySQL]

このドキュメントでは、各ストアと環境が異な [!DNL MySQL] ので、詳細なチューニング手順は提供しませんが、一般的な推奨事項を作成しておくことはできます。

[!DNL MySQL] 5.7.9 には多くの改善が行われています。[!DNL MySQL] は適切なデフォルト設定で配布されていると確信しています。 最も重要な設定は次のとおりです。

| パラメーター | デフォルト | 説明 |
|--- | --- | ---|
| `innodb_buffer_pool_instances` | 8 | デフォルト値は 8 に設定されています。これにより、同じインスタンスに複数のスレッドがアクセスしようとする問題を回避できます。 |
| `innodb_buffer_pool_size` | 128MB | 前述の複数のプールインスタンスと組み合わせると、デフォルトのメモリ割り当ては 1024 MB になります。 合計サイズは、すべてのバッファ プールで分割されます。 最適な効率を得るには、`innodb_buffer_pool_instances` と `innodb_buffer_pool_size` の組み合わせを指定して、各バッファープールインスタンスが少なくとも 1 GB になるようにします。 |
| `max_connections` | 150 | `max_connections` パラメーターの値は、アプリケーションサーバーで設定された PHP スレッドの合計数に関連付ける必要があります。 一般的な推奨事項は、小規模の場合は 300、中規模の環境の場合は 1,000 です。 |
| `innodb_thread_concurrency` | 0 | この設定の最適な値は、次の式で計算する必要があります：`innodb_thread_concurrency = 2 * (NumCPUs + NumDisks)` |

## [!DNL Varnish]

Magentoでは、ストアのフルページキャッシュサーバーとして [!DNL Varnish] を使用することを強くお勧めします。 PageCache モジュールはコードベースにまだ存在していますが、開発目的でのみ使用する必要があります。 [!DNL Varnish] と一緒に、または代わりに使用しないでください。

Web 層の前にある別のサーバーに [!DNL Varnish] をインストールします。 すべての受信リクエストを受け入れ、キャッシュされたページコピーを提供する必要があります。 セキュリティで保護されたページで [!DNL Varnish] が効果的に作業できるように、SSL ターミネーションプロキシを [!DNL Varnish] の前に配置できます。 Nginx はこの目的に使用できます。

[!DNL Commerce] は、パフォーマンスのためのすべての推奨設定を含む [!DNL Varnish] （バージョン 4 および 5）のサンプル構成ファイルを配布します。 パフォーマンスの面で最も重要なものは次のとおりです。

* **バックエンドのヘルスチェック** は、[!DNL Commerce] サーバーをポーリングして、サーバーが適切なタイミングで応答しているかどうかを判断します。
* **猶予モード** を使用すると、オブジェクトを有効期間（TTL）の期間を超えてキャッシュに保持し、正常でない場合や新しいコンテンツがまだ取得されていない場合に、この古 [!DNL Varnish] いコンテンツを提供するように [!DNL Commerce] に指示できます。
* **セントモード** は、設定可能な時間、異常な [!DNL Commerce] サーバーをブラックリストに登録します。 その結果、正常でないバックエンドは、[!DNL Varnish] をロードバランサーとして使用する場合、トラフィックを提供できません。

これらの機能の実装について詳しくは、[ 詳細  [!DNL Varnish]  設定 ](../configuration/cache/config-varnish-advanced.md) を参照してください。

### アセットのパフォーマンスの最適化

通常、最適なパフォーマンスを得るには、アセット（画像、JS、CSS など）を CDN に保存することをお勧めします。

サイトで多数のロケールをデプロイする必要がなく、サーバーが大部分の顧客と同じ地域にある場合は、CDN を使用する代わりにアセットを [!DNL Varnish] に保存することで、低コストで大幅なパフォーマンスの向上が得られる可能性があります。

アセットを [!DNL Varnish] に保存するには、`default.vcl` for [!DNL Commerce] 5 で生成された [!DNL Varnish] ファイルに次の VCL エントリを追加します。

`if` サブルーチンの PURGE リクエストの `vcl_recv` 文の最後に、次を追加します。

```javascript
# static files are cacheable. remove SSL flag and cookie

if (req.url ~ "^/(pub/)?(media|static)/.*\.(ico|html|css|js|jpg|jpeg|png|gif|tiff|bmp|mp3|ogg|svg|swf|woff|woff2|eot|ttf|otf)$") {
  unset req.http.Https;
  unset req.http./* {{ ssl_offloaded_header }} */;
  unset req.http.Cookie;
}
```

`vcl_backend_response` サブルーチンで、`if` 要求または `GET` 要求の Cookie を設定解除する `HEAD` ステートメントを探します。
更新された `if` ブロックは次のようになります。

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

サイトをアップグレードしたり、アセットをデプロイまたは更新したりするたびに、[!DNL Varnish] サーバーを再起動して、キャッシュされたアセットをフラッシュします。

## キャッシュサーバーとセッションサーバー

Magentoには、Redis、Memcache、filesystem、database など、キャッシュとセッションデータを保存する多数のオプションが用意されています。 これらのオプションの一部については、以下で説明します。

### 単一 Web ノードの設定

1 つの web ノードですべてのトラフィックを処理する予定がある場合、リモート Redis サーバーにキャッシュを配置しても意味がありません。 代わりに、ファイルシステムまたはローカルの Redis サーバーを使用します。 ファイルシステムを使用する場合は、RAM ファイルシステムにマウントされたボリュームにキャッシュフォルダーを配置します。 ローカルの Redis サーバーを使用する場合は、HTTP 経由でデータを交換するのではなく、直接接続にソケットを使用するように Redis を設定することを強くお勧めします。

### 複数の web ノードの設定

複数の Web ノードを設定する場合は、Redis が最適なオプションです。 パフォーマンスを向上 [!DNL Commerce] せるために大量のデータを能動的にキャッシュするので、web ノードと Redis サーバーの間のネットワークチャネルに注意を払います。 チャネルがリクエスト処理のボトルネックになることを望まない場合。

>[!INFO]
>
>何百何千もの同時リクエストに対応する必要がある場合は、Redis サーバーに最大 1 Gbit （またはそれ以上）のチャネルが必要になる場合があります。
