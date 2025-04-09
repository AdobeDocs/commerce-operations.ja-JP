---
source-git-commit: ba444c5f74cdeec86c842014d02775faf16b2f50
workflow-type: tm+mt
source-wordcount: '2073'
ht-degree: 0%

---
# Adobe Commerce パッケージ

<!-- The 'packages' variable contains the 'packages' node of the '_data/codebase/commerce/composer_lock.json' file
 -->

<!-- The 'packages-dev' variable contains the 'packages-dev' node of the '_data/codebase/commerce/composer_lock.json' file
 -->

<!-- The 'product' variable contains data of the 'magento/product-enterprise-edition' package
 -->

<!-- The edition variable contains `commerce` value from the _data/names.yml file
 -->

Adobe Commerceでは、Composer を使用して PHP パッケージを管理します。

`composer.json` ファイルはパッケージのリストを宣言します。`composer.lock` ファイルは、Adobe Commerceのインストールのビルドに使用されるパッケージの完全なリスト（各パッケージの完全なバージョンとその依存関係）を格納します。

次のリファレンスドキュメントは `composer.lock` ファイルから生成され、Adobe Commerce 2.4.8 に含まれている必須パッケージをカバーしています。

## 依存関係

`magento/product-enterprise-edition 2.4.8` には次の依存関係があります。

```config
adobe-commerce/extensions-metapackage: 2.0.1
colinmollenhour/cache-backend-file: ^1.4
colinmollenhour/cache-backend-redis: ^1.16
colinmollenhour/credis: ^1.15
colinmollenhour/php-redis-session-abstract: ^2.0
composer/composer: ^2.0, !=2.2.16
duosecurity/duo_api_php: ^1.1
duosecurity/duo_universal_php: ^1.0
elasticsearch/elasticsearch: ^8.15
ext-bcmath: *
ext-ctype: *
ext-curl: *
ext-dom: *
ext-ftp: *
ext-gd: *
ext-hash: *
ext-iconv: *
ext-intl: *
ext-mbstring: *
ext-openssl: *
ext-pdo_mysql: *
ext-simplexml: *
ext-soap: *
ext-sodium: *
ext-spl: *
ext-xsl: *
ext-zip: *
ezyang/htmlpurifier: ^4.17
guzzlehttp/guzzle: ^7.5
laminas/laminas-captcha: ^2.18
laminas/laminas-code: ^4.13
laminas/laminas-di: ^3.15
laminas/laminas-escaper: ^2.13
laminas/laminas-eventmanager: ^3.11
laminas/laminas-feed: ^2.22
laminas/laminas-filter: ^2.33
laminas/laminas-http: ^2.15
laminas/laminas-i18n: ^2.17
laminas/laminas-modulemanager: ^2.11
laminas/laminas-mvc: ^3.6
laminas/laminas-permissions-acl: ^2.10
laminas/laminas-servicemanager: ^3.16
laminas/laminas-soap: ^2.10
laminas/laminas-stdlib: ^3.11
laminas/laminas-uri: ^2.9
laminas/laminas-validator: ^2.23
league/flysystem: ^3.0
league/flysystem-aws-s3-v3: ^3.0
lib-libxml: *
magento/composer: ^1.10.1-beta1
magento/composer-dependency-version-audit-plugin: ^0.1
magento/framework-foreign-key: 100.4.7
magento/magento-composer-installer: >=0.4.0
magento/magento-zf-db: ^3.21
magento/magento2-ee-base: 2.4.8
magento/module-admin-gws: 100.4.8
magento/module-admin-gws-configurable-product: 100.4.5
magento/module-admin-gws-staging: 100.4.5
magento/module-advanced-catalog: 100.4.5
magento/module-advanced-checkout: 100.4.8
magento/module-advanced-rule: 100.4.5
magento/module-advanced-sales-rule: 100.4.5
magento/module-application-server: 100.4.1
magento/module-application-server-new-relic: 100.4.1
magento/module-application-server-performance-monitor: 100.4.1
magento/module-application-server-state-monitor: 100.4.1
magento/module-application-server-state-monitor-graph-ql: 100.4.1
magento/module-async-order: 100.4.4
magento/module-async-order-graph-ql: 100.4.3
magento/module-aws-s3-customer-custom-attributes: 100.4.5
magento/module-aws-s3-gift-card-import-export: 100.4.5
magento/module-aws-s3-scheduled-import-export: 100.4.5
magento/module-banner: 101.2.8
magento/module-banner-customer-segment: 100.4.6
magento/module-banner-graph-ql: 100.4.4
magento/module-banner-staging: 100.4.2
magento/module-bundle-import-export-staging: 100.4.5
magento/module-bundle-staging: 100.4.8
magento/module-catalog-event: 101.1.7
magento/module-catalog-import-export-staging: 100.4.5
magento/module-catalog-inventory-staging: 100.4.6
magento/module-catalog-permissions: 100.4.8
magento/module-catalog-permissions-graph-ql: 100.4.6
magento/module-catalog-rule-staging: 100.4.8
magento/module-catalog-staging: 100.4.8
magento/module-catalog-staging-graph-ql: 100.4.7
magento/module-catalog-url-rewrite-staging: 100.4.7
magento/module-checkout-address-search: 100.4.7
magento/module-checkout-address-search-gift-registry: 100.4.4
magento/module-checkout-staging: 100.4.7
magento/module-cms-staging: 100.4.8
magento/module-configurable-product-staging: 100.4.7
magento/module-custom-attribute-management: 100.4.7
magento/module-customer-balance: 100.4.8
magento/module-customer-balance-graph-ql: 100.4.5
magento/module-customer-custom-attributes: 100.4.8
magento/module-customer-custom-attributes-graph-ql: 100.4.1
magento/module-customer-finance: 100.4.5
magento/module-customer-segment: 102.1.8
magento/module-customer-segment-graph-ql: 100.4.1
magento/module-deferred-total-calculating: 100.4.3
magento/module-downloadable-staging: 100.4.7
magento/module-elasticsearch-catalog-permissions: 100.4.4
magento/module-elasticsearch-catalog-permissions-graph-ql: 100.4.3
magento/module-enterprise: 100.4.6
magento/module-gift-card: 101.3.8
magento/module-gift-card-account: 101.2.8
magento/module-gift-card-account-graph-ql: 100.4.6
magento/module-gift-card-graph-ql: 100.4.8
magento/module-gift-card-import-export: 100.4.5
magento/module-gift-card-staging: 100.4.5
magento/module-gift-message-staging: 100.4.5
magento/module-gift-registry: 101.2.8
magento/module-gift-registry-graph-ql: 100.4.4
magento/module-gift-wrapping: 101.2.7
magento/module-gift-wrapping-graph-ql: 100.4.5
magento/module-gift-wrapping-staging: 100.4.5
magento/module-google-optimizer-staging: 100.4.5
magento/module-google-tag-manager: 100.4.8
magento/module-grouped-product-staging: 100.4.6
magento/module-import-csv: 100.4.2
magento/module-import-csv-api: 100.4.2
magento/module-import-json: 100.4.1
magento/module-import-json-api: 100.4.1
magento/module-invitation: 100.4.7
magento/module-layered-navigation-staging: 100.4.5
magento/module-logging: 101.2.8
magento/module-login-as-customer-logging: 100.4.8
magento/module-login-as-customer-website-restriction: 100.4.6
magento/module-media-content-catalog-staging: 100.4.5
magento/module-msrp-staging: 100.4.6
magento/module-multicoupon: 100.4.1
magento/module-multicoupon-graph-ql: 100.4.1
magento/module-multicoupon-ui: 100.4.1
magento/module-multiple-wishlist: 100.4.8
magento/module-multiple-wishlist-graph-ql: 100.4.4
magento/module-payment-staging: 100.4.5
magento/module-persistent-history: 100.4.5
magento/module-price-permissions: 100.4.4
magento/module-product-video-staging: 100.4.5
magento/module-promotion-permissions: 100.4.5
magento/module-quote-commerce-graph-ql: 100.4.1
magento/module-quote-gift-card-options: 100.4.5
magento/module-quote-staging: 100.4.5
magento/module-reminder: 101.2.7
magento/module-remote-storage-commerce: 100.4.4
magento/module-resource-connections: 100.4.5
magento/module-review-staging: 100.4.5
magento/module-reward: 101.2.8
magento/module-reward-graph-ql: 100.4.7
magento/module-reward-staging: 100.4.5
magento/module-rma: 101.2.8
magento/module-rma-graph-ql: 100.4.7
magento/module-rma-staging: 100.4.5
magento/module-sales-archive: 101.0.6
magento/module-sales-rule-staging: 100.4.7
magento/module-scalable-checkout: 100.4.7
magento/module-scalable-inventory: 100.4.6
magento/module-scalable-oms: 100.4.6
magento/module-scheduled-import-export: 101.2.8
magento/module-search-staging: 100.4.6
magento/module-staging: 101.2.8
magento/module-staging-graph-ql: 100.4.5
magento/module-support: 101.2.7
magento/module-swat: 100.4.6
magento/module-target-rule: 101.2.8
magento/module-target-rule-graph-ql: 100.4.5
magento/module-versions-cms: 101.2.8
magento/module-versions-cms-page-cache: 100.4.4
magento/module-versions-cms-url-rewrite: 100.4.6
magento/module-versions-cms-url-rewrite-graph-ql: 100.4.4
magento/module-visual-merchandiser: 100.4.8
magento/module-webapi-rest-gws: 100.4.0
magento/module-website-restriction: 100.4.7
magento/module-weee-staging: 100.4.5
magento/module-wishlist-gift-card: 100.4.4
magento/module-wishlist-gift-card-graph-ql: 100.4.4
magento/page-builder-commerce: 1.7.5
magento/product-community-edition: 2.4.8
magento/security-package-ee: 1.0.3
magento/theme-adminhtml-spectrum: 100.4.3
magento/zend-cache: ^1.16
magento/zend-db: ^1.16
magento/zend-pdf: ^1.16
monolog/monolog: ^3.6
opensearch-project/opensearch-php: ^2.3
pelago/emogrifier: ^7.0
php: ~8.2.0||~8.3.0||~8.4.0
php-amqplib/php-amqplib: ^3.2
phpseclib/mcrypt_compat: ^2.0
phpseclib/phpseclib: ^3.0
psr/log: ^2 || ^3
ramsey/uuid: ^4.2
symfony/console: ^6.4
symfony/intl: ^6.4
symfony/mailer: ^6.4
symfony/mime: ^6.4
symfony/process: ^6.4
symfony/string: ^6.4
tedivm/jshrink: ^1.4
tubalmartin/cssmin: ^4.1
web-token/jwt-framework: ^3.4
webonyx/graphql-php: ^15.0
wikimedia/less.php: ^5.0
```

## サードパーティのライセンス

### Apache-2.0、LGPL-2.1-only

<table>
  <thead>
    <tr>
      <th>名前</th>
      <th>種類</th>
      <th>説明</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/opensearch-project/opensearch-php.git">opensearch-project/opensearch-php</a>
    </td>
    <td>ライブラリ</td>
    <td>OpenSearch 用 PHP クライアント</td>
  </tr>
  </tbody>
</table>

### Apache-2.0

<table>
  <thead>
    <tr>
      <th>名前</th>
      <th>種類</th>
      <th>説明</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/adobe/stock-api-libphp.git">astock/stock-api-libphp</a>
    </td>
    <td>ライブラリ</td>
    <td>Adobe Stock API ライブラリ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/awslabs/aws-crt-php.git">aws/aws-crt-php</a>
    </td>
    <td>ライブラリ</td>
    <td>PHP 用AWS共通ランタイム</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/aws/aws-sdk-php.git">aws/aws-sdk-php</a>
    </td>
    <td>ライブラリ</td>
    <td>AWS SDK for PHP - PHP プロジェクトでAmazon Web Servicesを使用する</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/opentelemetry-php/api.git"> オープンテレメトリ/api</a>
    </td>
    <td>図書館</td>
    <td>OpenTelemetry PHP 用の API。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/opentelemetry-php/context.git"> オープンテレメトリ/コンテキスト </a>
    </td>
    <td>図書館</td>
    <td>OpenTelemetry PHP のコンテキスト実装。</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree
    </td>
    <td>隠喩</td>
    <td>BraintreeMagento</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/wikimedia/less.php.git">wikimedia/less.php</a>
    </td>
    <td>ライブラリ</td>
    <td>LESS プロセッサの PHP ポート</td>
  </tr>
  </tbody>
</table>

### BSD-2 句

<table>
  <thead>
    <tr>
      <th>名前</th>
      <th>タイプ</th>
      <th>説明</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/Bacon/BaconQrCode.git">bacon/bacon-qr-code</a>
    </td>
    <td>ライブラリ</td>
    <td>BaconQrCode は、PHP 用の QR コードジェネレータです。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/DASPRiD/Enum.git">dasprid/enum</a>
    </td>
    <td>図書館</td>
    <td>PHP 7.1 列挙型 実装</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webimpress/safe-writer.git">ウェブインプレス/セーフライター</a>
    </td>
    <td>図書館</td>
    <td>競合状態を避けるために、ファイルを安全に書き込むためのツール</td>
  </tr>
  </tbody>
</table>

### BSD-3 句

<table>
  <thead>
    <tr>
      <th>名前</th>
      <th>タイプ</th>
      <th>説明</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_File.git">colinmollenhour/cache-backend-file</a>
    </td>
    <td>magento-モジュール</td>
    <td>ストックされた Zend_Cache_Backend_ファイル バックエンドは、タグによるクリーニングのパフォーマンスが極端に悪く、キャッシュされる項目の数が増えると使用できなくなります。 このバックエンドは多くの変更を行い、特にタグクリーニングのパフォーマンスを大幅に向上させます。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/php-redis-session-abstract.git">colinmollenhour/php-redis-session-abstract</a>
    </td>
    <td>ライブラリ</td>
    <td>楽観的ロックを使用した Redis ベースのセッションハンドラー</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/duosecurity/duo_universal_php.git">duosecurity/duo_universal_php</a>
    </td>
    <td>図書館</td>
    <td>Duo Universal SDK の PHP 実装。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/firebase/php-jwt.git">firebase/php-jwt</a>
    </td>
    <td>図書館</td>
    <td>PHP で JSON ウェブトークン（JWT）をエンコードし、デコードするためのシンプルなライブラリ。 現在の仕様に準拠する必要があります。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-captcha.git">laminas/laminas-captcha</a>
    </td>
    <td>ライブラリ</td>
    <td>置物、画像、ReCaptcha などを使用した CAPTCHA の生成と検証</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-code.git">laminas/laminas-code</a>
    </td>
    <td>ライブラリ</td>
    <td>PHP Reflection API、静的コードスキャン、およびコード生成の拡張</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-config.git">laminas/laminas-config</a>
    </td>
    <td>ライブラリ</td>
    <td>アプリケーションコード内でこの構成データにアクセスするための入れ子になったオブジェクトプロパティベースのユーザーインターフェイスを提供します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-di.git">Laminas/laminas-di</a>
    </td>
    <td>図書館</td>
    <td>PSR-11 コンテナの自動依存関係インジェクション</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-escaper.git">ラミナ/ラミナエスケープ</a>
    </td>
    <td>図書館</td>
    <td>HTML、HTML属性、JavaScript、CSS、URL を安全かつ安全にエスケープ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-eventmanager.git"> ラミナス/ラミナス – イベントマネージャ </a>
    </td>
    <td>ライブラリ</td>
    <td>PHP アプリケーション内のイベントをトリガーしてリッスンする</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-feed.git"> ラミナス/ラミナス・フィード </a>
    </td>
    <td>ライブラリ</td>
    <td>rss および Atom フィードを作成および使用する機能を提供します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-filter.git"> ラミナス/ラミナスフィルター </a>
    </td>
    <td>ライブラリ</td>
    <td>データとファイルをプログラムでフィルタリングし、正規化する</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-http.git">laminas/laminas-http</a>
    </td>
    <td>図書館</td>
    <td>ハイパーテキスト転送プロトコル (HTTP) 要求を実行するための簡単なインターフェイスを提供します。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-i18n.git">ラミナ/ラミナ-i18n</a>
    </td>
    <td>ライブラリ</td>
    <td>アプリケーションの翻訳を提供し、国際化値をフィルタリングおよび検証します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-json.git">laminas/laminas-json</a>
    </td>
    <td>ライブラリ</td>
    <td>PHP ネイティブ を JSON にシリアル化し、JSON を PHP にデコードするための便利なメソッドを提供しますネイティブ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-loader.git">ラミナ/ラミナローダー</a>
    </td>
    <td>図書館</td>
    <td>オートロードとプラグインの読み込み方法</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-modulemanager.git"> ラミナス/ラミナス – モジュールマネージャー </a>
    </td>
    <td>ライブラリ</td>
    <td>ラミナス mvc アプリケーション用モジュール式アプリケーションシステム</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mvc.git"> ラミナス/ラミナス – mvc</a>
    </td>
    <td>図書館</td>
    <td>Laminasのイベント駆動型MVCレイヤー(MVCアプリケーション、コントローラー、プラグインを含む)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-permissions-acl.git">laminas/laminas-permissions-acl</a>
    </td>
    <td>図書館</td>
    <td>権限管理のための軽量で柔軟なアクセス制御リスト（ACL）実装を提供します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-recaptcha.git">laminas/laminas-recaptcha</a>
    </td>
    <td>ライブラリ</td>
    <td>ReCaptcha web サービスの OOP ラッパー</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-router.git">laminas/laminas-router</a>
    </td>
    <td>図書館</td>
    <td>HTTP およびコンソールアプリケーション用の柔軟なルーティングシステム</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-server.git">laminas/laminas-server</a>
    </td>
    <td>ライブラリ</td>
    <td>反射ベースの RPC サーバを作成する</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-servicemanager.git"> ラミナス/ラミナス – サービスマネガー </a>
    </td>
    <td>図書館</td>
    <td>ファクトリ駆動型依存関係挿入コンテナー</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-session.git">Laminas/laminas-session</a>
    </td>
    <td>図書館</td>
    <td>PHPセッションとストレージへのオブジェクト指向のインターフェース</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-soap.git"> ラミナス/ラミナス石鹸 </a>
    </td>
    <td>ライブラリ</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-stdlib.git"> ラミナス/ラミナス – stdlib</a>
    </td>
    <td>図書館</td>
    <td>SPL 拡張、配列ユーティリティ、エラーハンドラなど</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-text.git"> ラミナス/ラミナス テキスト </a>
    </td>
    <td>ライブラリ</td>
    <td>FIGlets とテキストベースのテーブルの作成</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-translator.git">ラミナ/ラミナ翻訳者</a>
    </td>
    <td>図書館</td>
    <td>Laminas-i18n のトランスレーターコンポーネントのためのインターフェース</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-uri.git"> ラミナス/ラミナス uri</a>
    </td>
    <td>図書館</td>
    <td>» 均等割り付けリソース識別子(URI)の操作と検証を支援するコンポーネント</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-validator.git">laminas/laminas-validator</a>
    </td>
    <td>ライブラリ</td>
    <td>幅広いドメイン向けの検証クラスと、複雑な検証条件を作成するためにバリデータを連結する機能</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-view.git">ラミナ/ラミナ-表示</a>
    </td>
    <td>図書館</td>
    <td>複数の表示レイヤー、ヘルパーなどをサポートおよび提供する柔軟な表示レイヤー</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/marc-mabe/php-enum.git">marc-mabe/php-enum</a>
    </td>
    <td>図書館</td>
    <td>ネイティブの PHP を使用した定義済みリストのシンプルかつ迅速な実装</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/nikic/PHP-Parser.git">nikic/php-parser</a>
    </td>
    <td>ライブラリ</td>
    <td>PHP で記述された PHP パーサーです</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpfui/recaptcha.git">phpui/recaptcha</a>
    </td>
    <td>ライブラリ</td>
    <td>Googleの reCAPTCHA 用クライアントライブラリ（PHP 8.4 以降）</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tedious/JShrink.git">tedivm/jshrink</a>
    </td>
    <td>ライブラリ</td>
    <td>PHP に組み込まれた JavaScript 縮小機能</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tubalmartin/YUI-CSS-compressor-PHP-port.git"> タバルマーティン/cssmin</a>
    </td>
    <td>ライブラリ</td>
    <td>YUI CSS コンプレッサーの PHP ポート</td>
  </tr>
  </tbody>
</table>

### BSD-3 句の変更

<table>
  <thead>
    <tr>
      <th>名前</th>
      <th>種類</th>
      <th>説明</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_Redis.git">colinmollenhour/cache-backend-redis</a>
    </td>
    <td>magento-module</td>
    <td>タグを完全にサポートする Redis を使用した Zend_Cache バックエンド。</td>
  </tr>
  </tbody>
</table>

### ISC

<table>
  <thead>
    <tr>
      <th>名前</th>
      <th>種類</th>
      <th>説明</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/paragonie/sodium_compat.git">パラゴニー/sodium_compat</a>
    </td>
    <td>図書館</td>
    <td>純粋な PHP の libsodium の実装。存在する場合は PHP の拡張機能を使用します。</td>
  </tr>
  </tbody>
</table>

### LGPL-2.1 以降

<table>
  <thead>
    <tr>
      <th>名前</th>
      <th>タイプ</th>
      <th>説明</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/ezyang/htmlpurifier.git">ezyang/htmlpurifier</a>
    </td>
    <td>ライブラリ</td>
    <td>PHP で記述された標準準拠のHTML フィルタ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-amqplib/php-amqplib.git">php-amqplib/php-amqplib</a>
    </td>
    <td>図書館</td>
    <td>以前の videlalvaro/php-amqplib  このライブラリは、AMQP プロトコルの純粋な PHP 実装です。 これは RabbitMQ に対してテストされています。</td>
  </tr>
  </tbody>
</table>

### MIT

<table>
  <thead>
    <tr>
      <th>名前</th>
      <th>種類</th>
      <th>説明</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/braintree/braintree_php.git">braintree/braintree_php</a>
    </td>
    <td>ライブラリ</td>
    <td>Braintree PHP クライアントライブラリ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/math.git">レンガ/数学</a>
    </td>
    <td>図書館</td>
    <td>任意精度の算術演算ライブラリ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/varexporter.git">brick/varexporter</a>
    </td>
    <td>図書館</td>
    <td>__set_state()なしでクロージャとオブジェクトをエクスポートできるvar_export()の強力な代替手段</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ChristianRiesen/base32.git">クリスチャン・リーゼン/base32</a>
    </td>
    <td>図書館</td>
    <td>RFC 4648 に準拠した Base32 エンコーダ/デコーダー</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/credis.git"> コリンモレンアワー/クレディ </a>
    </td>
    <td>ライブラリ</td>
    <td>Credis は Redis のキー値ストアへの軽量なインターフェースで、パフォーマンスを向上させるために利用可能な場合は phpredis ライブラリをラップします。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/ca-bundle.git">composer/ca-bundle</a>
    </td>
    <td>ライブラリ</td>
    <td>システム CA バンドルへのパスを検索し、Mozilla CA バンドルへのフォールバックを含めることができます。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/class-map-generator.git">composer/class-map-generator</a>
    </td>
    <td>図書館</td>
    <td>PHPコードをスキャンし、クラスマップを生成するためのユーティリティ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/composer.git">作曲家/作曲家</a>
    </td>
    <td>図書館</td>
    <td>Composer を使用すると、PHP プロジェクトの依存関係を宣言、管理、およびインストールできます。 あらゆる場所に適切なスタックを確保できます。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/metadata-minifier.git">composer/metadata-minifier</a>
    </td>
    <td>ライブラリ</td>
    <td>メタデータ縮小と拡張を処理する 小 ユーティリティライブラリ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/pcre.git">composer/pcre</a>
    </td>
    <td>図書館</td>
    <td>タイプ セーフな preg_* 置換を提供する PCRE ラッピング ライブラリ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/semver.git">作曲家/センバー</a>
    </td>
    <td>ライブラリ</td>
    <td>ユーティリティ、バージョン制約の解析、および検証を提供する Semver ライブラリ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/spdx-licenses.git">composer/spdx-licenses</a>
    </td>
    <td>図書館</td>
    <td>SPDX ライセンスのリストと検証ライブラリ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/xdebug-handler.git">composer/xdebug-handler</a>
    </td>
    <td>ライブラリ</td>
    <td>Xdebug を指定せずにプロセスを再起動する。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/doctrine/lexer.git">教義/レクサー</a>
    </td>
    <td>図書館</td>
    <td>PHPドクトリンレクサーパーサーライブラリ、トップダウンの再帰的降下パーサーで使用できます。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/egulias/EmailValidator.git">egulias/email-validator</a>
    </td>
    <td>図書館</td>
    <td>複数の RFC に対して電子メールを検証するためのライブラリ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/elastic/elastic-transport-php.git">弾性/輸送</a>
    </td>
    <td>図書館</td>
    <td>Elastic 製品用の HTTP トランスポート PHP ライブラリ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/elastic/elasticsearch-php.git">LasticSearch/LasticSearch</a>
    </td>
    <td>図書館</td>
    <td>PHP クライアント for Elasticsearch</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/endroid/qr-code.git">endroid/qr-code</a>
    </td>
    <td>図書館</td>
    <td>エンドロイドQR Code</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/guzzlestreams.git">ezimuel/guzzlestreams</a>
    </td>
    <td>図書館</td>
    <td>弾性検索-phpで使用するガズル/ストリーム(放棄)のフォーク</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/ringphp.git">ezimuel/ringphp</a>
    </td>
    <td>ライブラリ</td>
    <td>Elasticsearch-php で使用される guzzle/RingPHP のフォーク（放棄）</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/guzzle.git">guzzlehttp/guzzle</a>
    </td>
    <td>ライブラリ</td>
    <td>Guzzle は PHP HTTP クライアントライブラリです</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/promises.git">guzzlehttp/promises</a>
    </td>
    <td>図書館</td>
    <td>ガズルはライブラリ約束します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/psr7.git">guzzleHTTP/PSR7</a>
    </td>
    <td>図書館</td>
    <td>共通のユーティリティメソッドも提供する PSR-7 メッセージ実装</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jsonrainbow/json-schema.git">justinrainbow/json-schema</a>
    </td>
    <td>図書館</td>
    <td>JSON スキーマを検証するライブラリ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem.git">リーグ/フライシステム</a>
    </td>
    <td>図書館</td>
    <td>PHP の ストレージ 抽象化ファイル</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-aws-s3-v3.git">league/flysystem-aws-s3-v3</a>
    </td>
    <td>ライブラリ</td>
    <td>Flysystem 用のAWS S3 ファイルシステムアダプタ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-local.git">league/flysystem-local</a>
    </td>
    <td>図書館</td>
    <td>Fly システム用のローカルファイルシステムアダプタ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/mime-type-detection.git">league/mime-type-detection</a>
    </td>
    <td>ライブラリ</td>
    <td>フライシステムのMIMEタイプ検出</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/monolog.git"> 独白/独白 </a>
    </td>
    <td>図書館</td>
    <td>ログをファイル、ソケット、受信トレイ、データベース、およびさまざまなWebサービスに送信します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jmespath/jmespath.php.git">mtdowling/jmespath.php</a>
    </td>
    <td>図書館</td>
    <td>JSON ドキュメントから要素エクストラクト方法を宣言的に指定する</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/constant_time_encoding.git">パラゴニー/constant_time_encoding</a>
    </td>
    <td>図書館</td>
    <td>RFC 4648 エンコーディングの定数時間実装 (ベース-64、ベース-32、ベース-16)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/random_compat.git">パラゴニー/random_compat</a>
    </td>
    <td>図書館</td>
    <td>PHP 7 の random_bytes() および random_int() 用の PHP 5.x ポリフィル</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/emogrifier.git">Pelago/Emogrifier</a>
    </td>
    <td>図書館</td>
    <td>HTML コード内で CSS スタイルをインラインスタイル属性に変換します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/discovery.git">php-http/discovery</a>
    </td>
    <td>composer-プラグイン</td>
    <td>PSR-7、PSR-17、PSR-18、およびHTTPlugの実装を検索してインストールします</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/httplug.git">php-http/httplug</a>
    </td>
    <td>ライブラリ</td>
    <td>HTTPlug、PHP 用の HTTP クライアントの抽象化</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/promise.git">php-http/promise</a>
    </td>
    <td>ライブラリ</td>
    <td>非同期 HTTP 要求に使用するプロミス</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/CssXPath.git">phpgt/cssxpath</a>
    </td>
    <td>図書館</td>
    <td>CSS セレクターを XPath クエリに変換します。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/Dom.git">phpgt/dom</a>
    </td>
    <td>図書館</td>
    <td>最新の DOM API。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/PropFunc.git">phpgt/propfunc</a>
    </td>
    <td>ライブラリ</td>
    <td>プロパティのアクセサ関数とミューテータ関数。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/mcrypt_compat.git">phpseclib/mcrypt_compat</a>
    </td>
    <td>図書館</td>
    <td>mcrypt 拡張のための PHP 5.x-8.x polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/phpseclib.git">phpseclib/phpseclib</a>
    </td>
    <td>図書館</td>
    <td>PHP Secure Communications Library - RSA、AES、SSH2、SFTP、X.509 などの純粋な PHP 実装。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/cache.git">PSR/キャッシュ</a>
    </td>
    <td>図書館</td>
    <td>キャッシュライブラリ用の共通インターフェイス</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/clock.git">psr/clock</a>
    </td>
    <td>ライブラリ</td>
    <td>時計を読み取るための共通インターフェース。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/container.git">psr/コンテナ</a>
    </td>
    <td>図書館</td>
    <td>Common Container インターフェイス (PHP FIG PSR-11)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/event-dispatcher.git">psr/イベント-dispatcher</a>
    </td>
    <td>図書館</td>
    <td>イベント処理のための 標準 インターフェイス。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-client.git">psr/http-client</a>
    </td>
    <td>図書館</td>
    <td>HTTP クライアント用の共通インターフェース</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-factory.git">psr/http-factory</a>
    </td>
    <td>図書館</td>
    <td>PSR-17: PSR-7 HTTP メッセージ ファクトリの共通インターフェイス</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-message.git">psr/http-message</a>
    </td>
    <td>図書館</td>
    <td>HTTP メッセージの共通インターフェイス</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/log.git">psr/log</a>
    </td>
    <td>図書館</td>
    <td>ログライブラリ用の共通インターフェイス</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ralouphie/getallheaders.git">ralouphie/getallheaders</a>
    </td>
    <td>ライブラリ</td>
    <td>getallheaders のポリフィル。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/collection.git"> ラムジー/コレクション </a>
    </td>
    <td>ライブラリ</td>
    <td>コレクションを表現および操作するための PHP ライブラリ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/uuid.git"> ラムジー/uuid</a>
    </td>
    <td>ライブラリ</td>
    <td>ユニバーサル固有識別子（UUID）を生成し、操作するための PHP ライブラリ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/reactphp/promise.git">react/promise</a>
    </td>
    <td>ライブラリ</td>
    <td>CommonJS Promises/A for PHP の軽量実装</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/PHP-CSS-Parser.git">sabberworm/php-css-parser</a>
    </td>
    <td>ライブラリ</td>
    <td>PHP で書かれた CSS ファイルのパーサ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/jsonlint.git">seld/jsonlint</a>
    </td>
    <td>図書館</td>
    <td>JSON リンター</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/phar-utils.git">seld/phar-utils</a>
    </td>
    <td>図書館</td>
    <td>PHARファイル形式ユーティリティ、PHPがあなたを悩ませるときのために</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/signal-handler.git">seld/signal-handler</a>
    </td>
    <td>図書館</td>
    <td>単純なUNIXシグナルハンドラは、クロスプラットフォーム開発を容易にするために、シグナルがサポートされていない場合にサイレントに失敗します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/aes-key-wrap.git">spomky-labs/aes-key-wrap</a>
    </td>
    <td>ライブラリ</td>
    <td>PHP 用の AES キーラップ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/otphp.git">spomky-labs/otphp</a>
    </td>
    <td>図書館</td>
    <td>RFC 4226(HOTPアルゴリズム)およびRFC 6238(TOTPアルゴリズム)に準拠し、Google認証システムと互換性のあるワンタイムパスワードを生成するためのPHPライブラリ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/pki-framework.git">spomky-labs/pki-framework</a>
    </td>
    <td>図書館</td>
    <td>公開鍵基盤を管理するための PHP フレームワーク。 これは、X.509 公開キー証明書、属性証明書、証明要求、および認証パス検証で構成されます。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/config.git">symfony/config</a>
    </td>
    <td>図書館</td>
    <td>あらゆる種類の設定値を検索、ロード、結合、自動入力、検証</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/console.git">symfony/console</a>
    </td>
    <td>図書館</td>
    <td>美しくテスト可能なコマンドラインインターフェイスの作成を容易にします</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/css-selector.git">symfony/css-セレクター</a>
    </td>
    <td>図書館</td>
    <td>CSS セレクターを XPath 式に変換します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/dependency-injection.git">symfony/dependency-injection</a>
    </td>
    <td>図書館</td>
    <td>を使用すると、アプリケーションでのオブジェクトの作成方法を標準化および一元化できます</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/deprecation-contracts.git">symfony/deprecation-contracts</a>
    </td>
    <td>図書館</td>
    <td>廃止のお知らせをトリガーする汎用関数および規則</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/error-handler.git">symfony/error-handler</a>
    </td>
    <td>ライブラリ</td>
    <td>エラーを管理し、PHP コードのデバッグを容易にするツールを提供します。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher.git">symfony/event-dispatcher</a>
    </td>
    <td>ライブラリ</td>
    <td>は、イベントをディスパッチしてリッスンすることで、アプリケーションコンポーネントが相互に通信できるようにするツールを提供します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher-contracts.git">symfony/event-dispatcher-contracts</a>
    </td>
    <td>ライブラリ</td>
    <td>イベントのディスパッチに関連する一般的な抽象概念</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/filesystem.git">symfony/filesystem</a>
    </td>
    <td>図書館</td>
    <td>ファイルシステムの基本的なユーティリティを提供します。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/finder.git">symfony/finder</a>
    </td>
    <td>ライブラリ</td>
    <td>直感的な fluent インターフェイスを使用してファイルとディレクトリを検索します。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client.git">symfony/http-client</a>
    </td>
    <td>ライブラリ</td>
    <td>HTTP リソースを同期または非同期で取得する強力なメソッドを提供</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client-contracts.git">symfony/http-client-contracts</a>
    </td>
    <td>ライブラリ</td>
    <td>HTTP クライアントに関連する一般的な抽象概念</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-foundation.git">symfony/http-foundation</a>
    </td>
    <td>ライブラリ</td>
    <td>HTTP 仕様のオブジェクト指向レイヤーを定義します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-kernel.git">symfony/http-kernel</a>
    </td>
    <td>ライブラリ</td>
    <td>リクエストを応答に変換する構造化されたプロセスを提供します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/intl.git">symfony/intl</a>
    </td>
    <td>ライブラリ</td>
    <td>ICU ライブラリのローカリゼーションデータへのアクセスを提供します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/mailer.git">symfony/mailer</a>
    </td>
    <td>ライブラリ</td>
    <td>メール送信に役立ちます</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/mime.git">symfony/mime</a>
    </td>
    <td>図書館</td>
    <td>MIME メッセージの操作を許可</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-ctype.git">symfony/polyfill-ctype</a>
    </td>
    <td>図書館</td>
    <td>ctype 関数のシンボリックリポリ入力</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-grapheme.git">symfony/polyfill-intl-grapheme</a>
    </td>
    <td>ライブラリ</td>
    <td>intl の grapheme_*関数のシンフォニーポリフィル</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-idn.git">symfony/polyfill-intl-idn</a>
    </td>
    <td>図書館</td>
    <td>intl のidn_to_asciiとidn_to_utf8関数のための symfony ポリフィル</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-normalizer.git">symfony/polyfill-intl-normalizer</a>
    </td>
    <td>ライブラリ</td>
    <td>Intl の Normalizer クラスおよび関連する関数に対する Symfony polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-mbstring.git">symfony/polyfill-mbstring</a>
    </td>
    <td>ライブラリ</td>
    <td>Mbstring 拡張機能用のシンボリックポリフィル</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php73.git">symfony/polyfill-php73</a>
    </td>
    <td>ライブラリ</td>
    <td>Symfony polyfill は、PHP 7.3 以降の機能を下位の PHP バージョンにバックポートします。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php80.git">symfony/polyfill-php80</a>
    </td>
    <td>ライブラリ</td>
    <td>symfony ポリフィルがいくつかの PHP 8.0+ 機能を下位の PHP バージョンにバックポートする</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php81.git">symfony/polyfill-php81</a>
    </td>
    <td>ライブラリ</td>
    <td>Symfony polyfill は、PHP 8.1 以降の機能を下位の PHP バージョンにバックポートする</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php82.git">symfony/polyfill-php82</a>
    </td>
    <td>ライブラリ</td>
    <td>Symfony polyfill は、PHP 8.2 以降の機能を下位の PHP バージョンにバックポートする</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php83.git">symfony/polyfill-php83</a>
    </td>
    <td>ライブラリ</td>
    <td>Symfony polyfill は、PHP 8.3 以降の機能を下位の PHP バージョンにバックポートする</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/process.git">symfony/process</a>
    </td>
    <td>ライブラリ</td>
    <td>サブプロセスでコマンドを実行します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/service-contracts.git">symfony/service-contracts</a>
    </td>
    <td>ライブラリ</td>
    <td>記述サービスに関連する一般的な抽象化</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/string.git">symfony/string</a>
    </td>
    <td>図書館</td>
    <td>文字列にオブジェクト指向のAPIを提供し、バイト、UTF-8コードポイント、書記素クラスターを統一された方法で処理します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-dumper.git">symfony/var-dumper</a>
    </td>
    <td>ライブラリ</td>
    <td>任意の PHP 変数を参照するためのメカニズムを提供します。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-exporter.git">symfony/var-exporter</a>
    </td>
    <td>図書館</td>
    <td>任意のシリアル化可能なPHPデータ構造をプレーンなPHPコードにエクスポートできます</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/yaml.git">symfony/yaml</a>
    </td>
    <td>図書館</td>
    <td>YAML ファイルの読み込みとダンプ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/web-token/jwt-framework.git">web-token/jwt-framework</a>
    </td>
    <td>交響束</td>
    <td>PHP および Symfony バンドル用の JSON オブジェクト署名および暗号化ライブラリ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webonyx/graphql-php.git">webonyx/graphql-php</a>
    </td>
    <td>図書館</td>
    <td>PHP ポート of GraphQL reference 実装</td>
  </tr>
  </tbody>
</table>

### OSL-3.0、AFL-3.0

<table>
  <thead>
    <tr>
      <th>名前</th>
      <th>タイプ</th>
      <th>説明</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      paypal/module-braintree-customer-balance
    </td>
    <td>magento2-module</td>
    <td>該当なし</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-gift-card
    </td>
    <td>magento2-module</td>
    <td>該当なし</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-gift-card-account
    </td>
    <td>magento2-module</td>
    <td>該当なし</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-gift-wrapping
    </td>
    <td>マジェント2-モジュール</td>
    <td>該当なし</td>
  </tr>
  <tr>
    <td>
      PayPal/モジュール-braintree-graph-ql
    </td>
    <td>マジェント2-モジュール</td>
    <td>該当なし</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-reward
    </td>
    <td>magento2-module</td>
    <td>該当なし</td>
  </tr>
  </tbody>
</table>

### OSL-3.0

<table>
  <thead>
    <tr>
      <th>名前</th>
      <th>タイプ</th>
      <th>説明</th>
    </tr>
  </thead>
  <tbody>
  </tbody>
</table>

### PHP

<table>
  <thead>
    <tr>
      <th>名前</th>
      <th>種類</th>
      <th>説明</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/2tvenom/CBOREncode.git">2tvenom/cborencode</a>
    </td>
    <td>ライブラリ</td>
    <td>PHP 用 CBOR エンコーダ</td>
  </tr>
  </tbody>
</table>

### 独自の

<table>
  <thead>
    <tr>
      <th>名前</th>
      <th>種類</th>
      <th>説明</th>
    </tr>
  </thead>
  <tbody>
  </tbody>
</table>

### 独自

<table>
  <thead>
    <tr>
      <th>名前</th>
      <th>タイプ</th>
      <th>説明</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      paypal/module-braintree-core
    </td>
    <td>magento2-module</td>
    <td>Magento Braintree 2.2.0 モジュールから PayPal 用に Gene Commerceでフォークします。</td>
  </tr>
  </tbody>
</table>
