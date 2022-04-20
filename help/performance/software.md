---
title: ソフトウェアRecommendations
description: Adobe CommerceおよびMagento Open Sourceのデプロイメントの最適なパフォーマンスに関連する推奨ソフトウェアのリストを確認します。
source-git-commit: 1d5956ce22c1a159336e9e7d64064b618fc2e63f
workflow-type: tm+mt
source-wordcount: '1476'
ht-degree: 0%

---


# ソフトウェアの推奨事項

の本番用インスタンスには、次のソフトウェアが必要です。 [!DNL Commerce]:

* [PHP](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html)
* Nginx と [PHP-FPM](https://php-fpm.org/)
* [[!DNL MySQL]](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/mysql.html)
* [[!DNL Elasticsearch] または OpenSearch](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html)

マルチサーバ展開の場合や、ビジネスの拡張を計画しているマーチャントの場合は、次の操作をお勧めします。

* [[!DNL Varnish] キャッシュ](https://devdocs.magento.com/guides/v2.4/config-guide/varnish/config-varnish.html)
* [レディス](https://devdocs.magento.com/guides/v2.4/config-guide/redis/redis-session.html) （2.0.6 以降）
* Redis のインスタンスを [デフォルトキャッシュ](https://devdocs.magento.com/guides/v2.4/config-guide/redis/redis-pg-cache.html) （このインスタンスをページキャッシュに使用しないでください）

詳しくは、 [システム要件](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) 」を参照してください。

## オペレーティングシステム

オペレーティングシステムの設定と最適化は、 [!DNL Commerce] 他の高負荷 web アプリケーションと比較して サーバーが処理する同時接続の数が増えると、使用可能なソケットの数が完全に割り当てられる場合があります。 Linux カーネルは、TCP 接続を「再利用する」メカニズムをサポートしています。 このメカニズムを有効にするには、 `/etc/sysctl.conf`:

>[!INFO]
>
>net.ipv4.tcp_tw_reuse を有効にしても、着信接続には影響しません。

```terminal
net.ipv4.tcp_tw_reuse = 1
```

カーネルパラメータ `net.core.somaxconn` は、接続を待機するオープンソケットの最大数を制御します。 この値は 1024 まで安全に増やすことができますが、この値を処理するサーバーの機能と関連付ける必要があります。 このカーネルパラメータを有効にするには、 `/etc/sysctl.conf`:

`net.core.somaxconn = 1024`

## PHP

Magentoは、PHP 7.3 および 7.4 を完全にサポートしています。PHP を設定する際に、リクエスト処理の速度と効率を最大限に高めるために、いくつかの要因を考慮する必要があります。

### PHP 拡張機能

アクティブな PHP 拡張のリストを、 [!DNL Commerce] 機能。

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

さらに、Adobe Commerceには以下が必要です。

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

拡張機能を追加すると、ライブラリの読み込み時間が長くなります。

>[!INFO]
>
>`php-mcrypt` は PHP 7.2 から削除され、 [`sodium` ライブラリ](https://www.php.net/manual/en/book.sodium.php). 以下を確認します。 [ナトリウム](https://www.php.net/manual/en/sodium.installation.php) は、PHP のアップグレード時に正しく有効になっています。

>[!INFO]
>
>プロファイルおよびデバッグ拡張機能が存在すると、ページの応答時間に悪影響を与える可能性があります。 例えば、デバッグセッションを使用しないアクティブな xDebug モジュールでは、ページの応答時間を最大 30%増やすことができます。

### PHP 設定

すべての [!DNL Commerce] データまたはコードをディスクにダンプしない場合は、次のようにメモリ制限を設定します。

`memory_limit=1G`

デバッグの場合は、この値を 2G に増やします。

#### Realpath_cache の設定

改善するには [!DNL Commerce] パフォーマンス、追加、または更新を行うことをお勧めします `realpath_cache` 設定 `php.ini` ファイル。 この設定により、PHP プロセスは、ページが読み込まれるたびにファイルを検索する代わりに、ファイルへのパスをキャッシュできます。 詳しくは、 [パフォーマンスの調整](https://www.php.net/manual/en/ini.core.php) PHP ドキュメント内。

```text
realpath_cache_size=10M
realpath_cache_ttl=7200
```

#### ByteCode

最大速度を得るには [!DNL Commerce] PHP 7 では、OpCache モジュールをアクティブにし、適切に設定する必要があります。 モジュールでは、次の設定をお勧めします。

```text
opcache.memory_consumption=512
opcache.max_accelerated_files=60000
opcache.consistency_checks=0
opcache.validate_timestamps=0
opcache.enable_cli=1
```

opcache のメモリ割り当てを微調整する場合は、Magentoのコードベースのサイズとすべての拡張機能を考慮に入れます。 Magentoのパフォーマンスチームは、前述の例の値をテストに使用します。これは、インストールされている拡張機能の平均数に十分な領域を opcache に提供するからです。

メモリ不足のマシンがあり、多くの拡張機能やカスタマイズ機能がインストールされていない場合は、次の設定を使用して同様の結果を得ます。

```text
opcache.memory_consumption=64
opcache.max_accelerated_files=60000
```

#### APCU

を有効にすることをお勧めします。 [PHP APCu 拡張機能](https://getcomposer.org/doc/articles/autoloader-optimization.md#optimization-level-2-b-apcu-cache) および [設定 `composer` それを支える](https://devdocs.magento.com/guides/v2.4/performance-best-practices/deployment-flow.html#preprocess-dependency-injection-instructions) 最高のパフォーマンスを得るために最適化する。 この拡張機能は、開かれたファイルのファイルの場所をキャッシュします。これにより、 [!DNL Commerce] ページ、Ajax 呼び出し、エンドポイントを含むサーバー呼び出し。

の `apcu.ini` ファイルに次の情報を含めます。

```text
extension=apcu.so
[apcu]
apc.enabled = 1
```

## Web サーバー

Magentoは、Nginx および Apache Web サーバーを完全にサポートしています。 [!DNL Commerce] には、  `<magento_home>/nginx.conf.sample` (Nginx) および  `<magento_home>.htaccess.sample` (Apache) ファイル。  Nginx サンプルには、パフォーマンスを向上させるための設定が含まれ、再構成が少なくて済むように設計されています。 サンプルファイルに定義されている主な設定のベストプラクティスには、次のものがあります。

* ブラウザーでの静的コンテンツのキャッシュ設定
* PHP のメモリと実行時間の設定
* コンテンツ圧縮設定

次に示すように、入力リクエスト処理のスレッド数も設定する必要があります。

| Web サーバー | 属性名 | 場所 | 関連情報 |
|--- | --- | --- | ---|
| Nginx | `worker_connections` | `/etc/nginx/nginx.conf` (Debian) | [パフォーマンスに対する NGINX の調整](https://www.nginx.com/blog/tuning-nginx/) |
| Apache 2.2 | `MaxClients` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Apache パフォーマンスの調整](http://httpd.apache.org/docs/2.2/misc/perf-tuning.html) |
| Apache 2.4 | `MaxRequestWorkers` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Apache MPM Common Directives](https://httpd.apache.org/docs/2.4/mod/mpm_common.html#maxrequestworkers) |

## [!DNL MySQL]

このドキュメントでは詳細を説明していません [!DNL MySQL] 各ストアと環境が異なるので、調整手順を説明しますが、一般的な推奨事項をいくつか作成できます。

次の点で多くの改善点があります。 [!DNL MySQL] 5.7.9 我々は確信を持っている [!DNL MySQL] は適切なデフォルト設定で配布されます。 最も重要な設定は次のとおりです。

| パラメータ | デフォルト | 説明 |
|--- | --- | ---|
| `innodb_buffer_pool_instances` | 8 | 複数のスレッドが同じインスタンスにアクセスしようとする際の問題を回避するために、デフォルト値は 8 に設定されています。 |
| `innodb_buffer_pool_size` | 128 MB | 上記の複数のプールインスタンスと組み合わせると、1024 MB のデフォルトのメモリ割り当てを意味します。 合計サイズは、すべてのバッファプールで割られます。 最も効率を高めるには、 `innodb_buffer_pool_instances` および `innodb_buffer_pool_size` したがって、各バッファプールインスタンスは少なくとも 1 GB です。 |
| `max_connections` | 150 | の値 `max_connections` パラメータは、アプリケーションサーバーで設定された PHP スレッドの総数と関連付ける必要があります。 小規模の場合は 300、中規模の場合は 1000 を推奨します。 |
| `innodb_thread_concurrency` | 0 | この設定に最適な値は、次の式で計算する必要があります。 `innodb_thread_concurrency = 2 * (NumCPUs + NumDisks)` |

## [!DNL Varnish]

Magentoでは、 [!DNL Varnish] をストアのフルページキャッシュサーバーとして使用します。 PageCache モジュールは、コードベースに引き続き存在しますが、開発目的でのみ使用する必要があります。 と一緒に、またはの代わりにを使用しないでください。 [!DNL Varnish].

インストール [!DNL Varnish] を Web 層の前にある別のサーバーに配置します。 受信するすべてのリクエストを受け入れ、キャッシュされたページコピーを提供する必要があります。 許可する手順は次のとおりです。 [!DNL Varnish] 保護されたページを効果的に操作するために、SSL 終端プロキシを [!DNL Varnish]. Nginx はこの目的で使用できます。

[!DNL Commerce] は、次のサンプル設定ファイルを配布します： [!DNL Varnish] （バージョン 4 および 5）。パフォーマンスに関する推奨設定がすべて含まれています。 パフォーマンスの点で最も重要な要素は次のとおりです。

* **バックエンドのヘルスチェック** 投票する [!DNL Commerce] サーバーを使用して、応答がタイムリーに行われているかどうかを判断します。
* **猶予モード** を使用して、 [!DNL Varnish] ：オブジェクトをキャッシュに保持して有効期間 (TTL) を超えて、この古いコンテンツを提供する場合 ( [!DNL Commerce] は正常でないか、新しいコンテンツがまだ取得されていない場合は除きます。
* **SAINT モード** 不正なブラックリストを表示 [!DNL Commerce] サーバーの設定可能な時間。 その結果、異常なバックエンドは、 [!DNL Varnish] をロードバランサーとして使用します。

詳しくは、 [詳細 [!DNL Varnish] 設定](https://devdocs.magento.com/guides/v2.4/config-guide/varnish/config-varnish-advanced.html) これらの機能の実装の詳細については、を参照してください。

### アセットのパフォーマンスの最適化

一般に、最適なパフォーマンスを得るために、アセット（画像、JS、CSS など）を CDN に保存することをお勧めします。

サイトに大量のロケールをデプロイする必要がなく、サーバーが大多数の顧客と同じ地域にある場合は、にアセットを保存すると、低コストで大幅なパフォーマンス向上が見られる可能性があります [!DNL Varnish] CDN を使用する代わりに使用します。

にアセットを保存するには、以下を実行します。 [!DNL Varnish]」で、 `default.vcl` 次の場所で生成されたファイル [!DNL Commerce] 対象 [!DNL Varnish] 5.

の最後 `if` ステートメントを使用して、 `vcl_recv` サブルーチン、追加：

```javascript
# static files are cacheable. remove SSL flag and cookie

if (req.url ~ "^/(pub/)?(media|static)/.*\.(ico|html|css|js|jpg|jpeg|png|gif|tiff|bmp|mp3|ogg|svg|swf|woff|woff2|eot|ttf|otf)$") {
  unset req.http.Https;
  unset req.http./* {{ ssl_offloaded_header }} */;
  unset req.http.Cookie;
}
```

内 `vcl_backend_response` サブルーチン，探す `if` の cookie の設定を解除するステートメント `GET` または `HEAD` リクエスト。
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

を再起動します。 [!DNL Varnish] サイトをアップグレードしたり、アセットをデプロイ/更新したりするたびに、キャッシュされたアセットをフラッシュするサーバー。

## キャッシュとセッションサーバー

Magentoには、Redis、Memcache、filesystem、database など、キャッシュとセッションのデータを保存する多くのオプションが用意されています。 これらのオプションの一部を以下で説明します。

### 単一の Web ノードの設定

1 つの Web ノードだけですべてのトラフィックを提供する予定がある場合、キャッシュをリモート Redis サーバーに置くのは意味がありません。 代わりに、ファイルシステムまたはローカルの Redis サーバを使用します。 ファイルシステムを使用する場合は、RAM ファイルシステムにマウントされたボリュームにキャッシュフォルダを配置します。 ローカルの Redis サーバーを使用する場合は、HTTP を介したデータ交換ではなく、直接接続にソケットを使用するように Redis を設定することを強くお勧めします。

### 複数の Web ノードの設定

複数の Web ノードを設定する場合、Redis が最適なオプションです。 理由： [!DNL Commerce] 多くのデータをキャッシュしてパフォーマンスを向上させ、Web ノードと Redis サーバー間のネットワークチャネルに注意を払います。 リクエスト処理のボトルネックにならないようにします。

>[!INFO]
>
>数百、数千の同時要求を処理する必要がある場合は、Redis サーバに最大 1 ギガビット（またはより広い）のチャネルが必要になる場合があります。
