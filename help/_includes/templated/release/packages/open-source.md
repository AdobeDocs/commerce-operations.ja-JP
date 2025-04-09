---
source-git-commit: ba444c5f74cdeec86c842014d02775faf16b2f50
workflow-type: tm+mt
source-wordcount: '2073'
ht-degree: 0%

---
# Magento Open Source パッケージ

<!-- The 'packages' variable contains the 'packages' node of the '_data/codebase/open-source/composer_lock.json' file
 -->

<!-- The 'packages-dev' variable contains the 'packages-dev' node of the '_data/codebase/open-source/composer_lock.json' file
 -->

<!-- The 'product' variable contains data of the 'magento/product-community-edition' package
 -->

<!-- The edition variable contains `open-source` value from the _data/names.yml file
 -->

Magento Open Sourceでは、Composer を使用して PHP パッケージを管理します。

`composer.json` ファイルはパッケージのリストを宣言します。`composer.lock` ファイルは、Magento Open Sourceのインストールのビルドに使用されるパッケージの完全なリスト（各パッケージの完全なバージョンとその依存関係）を格納します。

次のリファレンスドキュメントは `composer.lock` ファイルから生成され、Magento Open Source 2.4.8 に含まれている必須パッケージをカバーしています。

## 依存関係

`magento/product-community-edition 2.4.8` には次の依存関係があります。

```config
adobe-commerce/os-extensions-metapackage: 1.0.1
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
magento/framework: 103.0.8
magento/framework-amqp: 100.4.6
magento/framework-bulk: 101.0.4
magento/framework-message-queue: 100.4.8
magento/inventory-metapackage: 1.2.8
magento/language-de_de: 100.4.0
magento/language-en_us: 100.4.0
magento/language-es_es: 100.4.0
magento/language-fr_fr: 100.4.0
magento/language-nl_nl: 100.4.0
magento/language-pt_br: 100.4.0
magento/language-zh_hans_cn: 100.4.0
magento/magento-composer-installer: >=0.4.0
magento/magento-zf-db: ^3.21.0
magento/magento2-base: 2.4.8
magento/module-admin-analytics: 100.4.7
magento/module-admin-notification: 100.4.7
magento/module-advanced-pricing-import-export: 100.4.8
magento/module-advanced-search: 100.4.6
magento/module-amqp: 100.4.5
magento/module-analytics: 100.4.8
magento/module-application-performance-monitor: 100.4.1
magento/module-application-performance-monitor-new-relic: 100.4.1
magento/module-async-config: 100.4.1
magento/module-asynchronous-operations: 100.4.8
magento/module-authorization: 100.4.8
magento/module-aws-s3: 100.4.6
magento/module-backend: 102.0.8
magento/module-backup: 100.4.8
magento/module-bundle: 101.0.8
magento/module-bundle-graph-ql: 100.4.8
magento/module-bundle-import-export: 100.4.7
magento/module-cache-invalidate: 100.4.6
magento/module-captcha: 100.4.8
magento/module-cardinal-commerce: 100.4.6
magento/module-catalog: 104.0.8
magento/module-catalog-analytics: 100.4.5
magento/module-catalog-cms-graph-ql: 100.4.4
magento/module-catalog-customer-graph-ql: 100.4.7
magento/module-catalog-graph-ql: 100.4.8
magento/module-catalog-import-export: 101.1.8
magento/module-catalog-inventory: 100.4.8
magento/module-catalog-inventory-graph-ql: 100.4.5
magento/module-catalog-rule: 101.2.8
magento/module-catalog-rule-configurable: 100.4.7
magento/module-catalog-rule-graph-ql: 100.4.5
magento/module-catalog-search: 102.0.8
magento/module-catalog-url-rewrite: 100.4.8
magento/module-catalog-url-rewrite-graph-ql: 100.4.6
magento/module-catalog-widget: 100.4.8
magento/module-checkout: 100.4.8
magento/module-checkout-agreements: 100.4.7
magento/module-checkout-agreements-graph-ql: 100.4.4
magento/module-cms: 104.0.8
magento/module-cms-graph-ql: 100.4.5
magento/module-cms-url-rewrite: 100.4.7
magento/module-cms-url-rewrite-graph-ql: 100.4.6
magento/module-compare-list-graph-ql: 100.4.4
magento/module-config: 101.2.8
magento/module-configurable-import-export: 100.4.6
magento/module-configurable-product: 100.4.8
magento/module-configurable-product-graph-ql: 100.4.8
magento/module-configurable-product-sales: 100.4.5
magento/module-contact: 100.4.7
magento/module-contact-graph-ql: 100.4.1
magento/module-cookie: 100.4.8
magento/module-cron: 100.4.8
magento/module-csp: 100.4.7
magento/module-currency-symbol: 100.4.6
magento/module-customer: 103.0.8
magento/module-customer-analytics: 100.4.5
magento/module-customer-downloadable-graph-ql: 100.4.4
magento/module-customer-graph-ql: 100.4.8
magento/module-customer-import-export: 100.4.8
magento/module-deploy: 100.4.8
magento/module-developer: 100.4.8
magento/module-dhl: 100.4.7
magento/module-directory: 100.4.8
magento/module-directory-graph-ql: 100.4.6
magento/module-downloadable: 100.4.8
magento/module-downloadable-graph-ql: 100.4.8
magento/module-downloadable-import-export: 100.4.7
magento/module-eav: 102.1.8
magento/module-eav-graph-ql: 100.4.5
magento/module-elasticsearch: 101.0.8
magento/module-elasticsearch-8: 101.0.0
magento/module-email: 101.1.8
magento/module-encryption-key: 100.4.6
magento/module-fedex: 100.4.6
magento/module-gift-message: 100.4.7
magento/module-gift-message-graph-ql: 100.4.6
magento/module-google-adwords: 100.4.5
magento/module-google-analytics: 100.4.4
magento/module-google-gtag: 100.4.3
magento/module-google-optimizer: 100.4.7
magento/module-graph-ql: 100.4.8
magento/module-graph-ql-cache: 100.4.5
magento/module-graph-ql-new-relic: 100.4.1
magento/module-graph-ql-resolver-cache: 100.4.1
magento/module-grouped-catalog-inventory: 100.4.5
magento/module-grouped-import-export: 100.4.6
magento/module-grouped-product: 100.4.8
magento/module-grouped-product-graph-ql: 100.4.8
magento/module-import-export: 101.0.8
magento/module-indexer: 100.4.8
magento/module-instant-purchase: 100.4.7
magento/module-integration: 100.4.8
magento/module-integration-graph-ql: 100.4.1
magento/module-jwt-framework-adapter: 100.4.4
magento/module-jwt-user-token: 100.4.3
magento/module-layered-navigation: 100.4.8
magento/module-login-as-customer: 100.4.8
magento/module-login-as-customer-admin-ui: 100.4.8
magento/module-login-as-customer-api: 100.4.7
magento/module-login-as-customer-assistance: 100.4.7
magento/module-login-as-customer-frontend-ui: 100.4.7
magento/module-login-as-customer-graph-ql: 100.4.5
magento/module-login-as-customer-log: 100.4.6
magento/module-login-as-customer-page-cache: 100.4.7
magento/module-login-as-customer-quote: 100.4.6
magento/module-login-as-customer-sales: 100.4.7
magento/module-marketplace: 100.4.6
magento/module-media-content: 100.4.6
magento/module-media-content-api: 100.4.7
magento/module-media-content-catalog: 100.4.6
magento/module-media-content-cms: 100.4.6
magento/module-media-content-synchronization: 100.4.7
magento/module-media-content-synchronization-api: 100.4.6
magento/module-media-content-synchronization-catalog: 100.4.5
magento/module-media-content-synchronization-cms: 100.4.5
magento/module-media-gallery: 100.4.7
magento/module-media-gallery-api: 101.0.7
magento/module-media-gallery-catalog: 100.4.5
magento/module-media-gallery-catalog-integration: 100.4.5
magento/module-media-gallery-catalog-ui: 100.4.5
magento/module-media-gallery-cms-ui: 100.4.5
magento/module-media-gallery-integration: 100.4.7
magento/module-media-gallery-metadata: 100.4.6
magento/module-media-gallery-metadata-api: 100.4.5
magento/module-media-gallery-renditions: 100.4.6
magento/module-media-gallery-renditions-api: 100.4.5
magento/module-media-gallery-synchronization: 100.4.7
magento/module-media-gallery-synchronization-api: 100.4.6
magento/module-media-gallery-synchronization-metadata: 100.4.4
magento/module-media-gallery-ui: 100.4.7
magento/module-media-gallery-ui-api: 100.4.6
magento/module-media-storage: 100.4.7
magento/module-message-queue: 100.4.8
magento/module-msrp: 100.4.7
magento/module-msrp-configurable-product: 100.4.5
magento/module-msrp-grouped-product: 100.4.5
magento/module-multishipping: 100.4.8
magento/module-mysql-mq: 100.4.6
magento/module-new-relic-reporting: 100.4.6
magento/module-newsletter: 100.4.8
magento/module-newsletter-graph-ql: 100.4.5
magento/module-offline-payments: 100.4.6
magento/module-offline-shipping: 100.4.7
magento/module-open-search: 100.4.2
magento/module-order-cancellation: 100.4.1
magento/module-order-cancellation-graph-ql: 100.4.1
magento/module-order-cancellation-ui: 100.4.1
magento/module-page-cache: 100.4.8
magento/module-payment: 100.4.8
magento/module-payment-graph-ql: 100.4.3
magento/module-paypal: 101.0.8
magento/module-paypal-captcha: 100.4.5
magento/module-paypal-graph-ql: 100.4.6
magento/module-persistent: 100.4.8
magento/module-product-alert: 100.4.7
magento/module-product-video: 100.4.8
magento/module-quote: 101.2.8
magento/module-quote-analytics: 100.4.7
magento/module-quote-bundle-options: 100.4.4
magento/module-quote-configurable-options: 100.4.4
magento/module-quote-downloadable-links: 100.4.4
magento/module-quote-graph-ql: 100.4.8
magento/module-related-product-graph-ql: 100.4.5
magento/module-release-notification: 100.4.6
magento/module-remote-storage: 100.4.6
magento/module-reports: 100.4.8
magento/module-require-js: 100.4.4
magento/module-review: 100.4.8
magento/module-review-analytics: 100.4.5
magento/module-review-graph-ql: 100.4.4
magento/module-robots: 101.1.4
magento/module-rss: 100.4.6
magento/module-rule: 100.4.7
magento/module-sales: 103.0.8
magento/module-sales-analytics: 100.4.5
magento/module-sales-graph-ql: 100.4.8
magento/module-sales-inventory: 100.4.5
magento/module-sales-rule: 101.2.8
magento/module-sales-rule-graph-ql: 100.4.1
magento/module-sales-sequence: 100.4.5
magento/module-sample-data: 100.4.6
magento/module-search: 101.1.8
magento/module-security: 100.4.8
magento/module-send-friend: 100.4.6
magento/module-send-friend-graph-ql: 100.4.4
magento/module-shipping: 100.4.8
magento/module-sitemap: 100.4.7
magento/module-store: 101.1.8
magento/module-store-graph-ql: 100.4.6
magento/module-swagger: 100.4.7
magento/module-swagger-webapi: 100.4.4
magento/module-swagger-webapi-async: 100.4.4
magento/module-swatches: 100.4.8
magento/module-swatches-graph-ql: 100.4.6
magento/module-swatches-layered-navigation: 100.4.4
magento/module-tax: 100.4.8
magento/module-tax-graph-ql: 100.4.4
magento/module-tax-import-export: 100.4.7
magento/module-theme: 101.1.8
magento/module-theme-graph-ql: 100.4.5
magento/module-translation: 100.4.8
magento/module-ui: 101.2.8
magento/module-ups: 100.4.8
magento/module-url-rewrite: 102.0.7
magento/module-url-rewrite-graph-ql: 100.4.7
magento/module-user: 101.2.8
magento/module-usps: 100.4.7
magento/module-variable: 100.4.6
magento/module-vault: 101.2.8
magento/module-vault-graph-ql: 100.4.4
magento/module-version: 100.4.5
magento/module-webapi: 100.4.7
magento/module-webapi-async: 100.4.6
magento/module-webapi-security: 100.4.5
magento/module-weee: 100.4.8
magento/module-weee-graph-ql: 100.4.5
magento/module-widget: 101.2.8
magento/module-wishlist: 101.2.8
magento/module-wishlist-analytics: 100.4.6
magento/module-wishlist-graph-ql: 100.4.8
magento/page-builder: 1.7.5
magento/security-package: 1.1.7
magento/theme-adminhtml-backend: 100.4.8
magento/theme-frontend-blank: 100.4.8
magento/theme-frontend-luma: 100.4.8
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
      <th>タイプ</th>
      <th>説明</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/opensearch-project/opensearch-php.git">opensearch-project/opensearch-php</a>
    </td>
    <td>図書館</td>
    <td>OpenSearch 用の PHP クライアント</td>
  </tr>
  </tbody>
</table>

### Apache-2.0

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
      <a href="https://github.com/adobe/stock-api-libphp.git">astock/stock-api-libphp</a>
    </td>
    <td>図書館</td>
    <td>Adobe Stock API ライブラリ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/awslabs/aws-crt-php.git">aws/aws-crt-php</a>
    </td>
    <td>図書館</td>
    <td>PHP 用 AWS 共通ランタイム</td>
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
      <a href="https://github.com/opentelemetry-php/api.git">オープン テレメトリ/API</a>
    </td>
    <td>図書館</td>
    <td>OpenTelemetry PHP 用の API。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/opentelemetry-php/context.git"> オープンテレメトリ/コンテキスト </a>
    </td>
    <td>図書館</td>
    <td>OpenTelemetry PHP の コンテキスト 実装 です。</td>
  </tr>
  <tr>
    <td>
      PayPal/モジュール-ブレインツリー
    </td>
    <td>メタパッケージ</td>
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
      <th>種類</th>
      <th>説明</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/Bacon/BaconQrCode.git">ベーコン/ベーコンQRコード</a>
    </td>
    <td>図書館</td>
    <td>BaconQrCode は PHP 用のQR コードジェネレータです。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/DASPRiD/Enum.git">dasprid/enum</a>
    </td>
    <td>ライブラリ</td>
    <td>PHP 7.1 列挙実装</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webimpress/safe-writer.git">webimpress/safe-writer</a>
    </td>
    <td>ライブラリ</td>
    <td>競合状態を避けるため、ファイルを安全に書き込むためのツール</td>
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
    <td>magento-module</td>
    <td>ストックの Zend_Cache_Backend_File バックエンドは、タグによるクリーニングのパフォーマンスが非常に悪く、キャッシュされたアイテムの数が増えると使用できなくなります。 このバックエンドは多くの変更を加え、特にタグのクリーニングのパフォーマンスを大幅に向上させます。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/php-redis-session-abstract.git">Colinmollenhour/php-redis-session-abstract</a>
    </td>
    <td>図書館</td>
    <td>楽観的ロックを備えた Redis ベースのセッションハンドラー</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/duosecurity/duo_universal_php.git">DuoSecurity/duo_universal_php</a>
    </td>
    <td>ライブラリ</td>
    <td>Duo Universal SDKの PHP 実装。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/firebase/php-jwt.git">firebase/php-jwt</a>
    </td>
    <td>ライブラリ</td>
    <td>PHP で JSON Web トークン (JWT) をエンコードおよびデコードするための単純なライブラリ。 現在の仕様に準拠する必要があります。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-captcha.git">laminas/laminas-captcha</a>
    </td>
    <td>図書館</td>
    <td>フィグレット、画像、ReCaptcha などを使用して CAPTCHA を生成および検証します。</td>
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
    <td>図書館</td>
    <td>アプリケーションコード内でこの構成データにアクセスするための入れ子になったオブジェクトプロパティベースのユーザーインターフェイスを提供します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-di.git">Laminas/laminas-di</a>
    </td>
    <td>図書館</td>
    <td>PSR-11コンテナへの依存性注入の自動化</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-escaper.git"> ラミナス/ラミナスエスケープ </a>
    </td>
    <td>ライブラリ</td>
    <td>安全かつ安全にHTML、HTML属性、JavaScript、CSS および URL をエスケープ</td>
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
    <td>図書館</td>
    <td>RSS フィードおよび Atom フィードを作成および使用する機能を提供します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-filter.git">ラミナ/ラミナフィルター</a>
    </td>
    <td>図書館</td>
    <td>プログラムによるデータとファイルのフィルタリングと正規化</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-http.git">laminas/laminas-http</a>
    </td>
    <td>ライブラリ</td>
    <td>ハイパーテキスト転送プロトコル （HTTP） リクエストを実行するための簡単なインターフェイスを提供します。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-i18n.git"> ラミナス/ラミナス – i18n</a>
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
      <a href="https://github.com/laminas/laminas-loader.git"> ラミナス/ラミナスローダー </a>
    </td>
    <td>ライブラリ</td>
    <td>自動読み込みとプラグインの読み込み戦略</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-modulemanager.git">Laminas/Laminas-ModuleManager</a>
    </td>
    <td>図書館</td>
    <td>Laminas-MVCアプリケーション用のモジュール式アプリケーションシステム</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mvc.git">Laminas/Laminas-MVC</a>
    </td>
    <td>ライブラリ</td>
    <td>Laminas のイベント駆動型 MVC レイヤー（MVC アプリケーション、コントローラ、プラグインを含む）</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-permissions-acl.git">laminas/laminas-permissions-acl</a>
    </td>
    <td>ライブラリ</td>
    <td>特権管理のための軽量で柔軟なアクセス制御リスト(ACL)実装を提供します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-recaptcha.git">laminas/laminas-recaptcha</a>
    </td>
    <td>図書館</td>
    <td>ReCaptcha Web サービスの OOP ラッパー</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-router.git">laminas/laminas-router</a>
    </td>
    <td>ライブラリ</td>
    <td>HTTP およびコンソールアプリケーション用の柔軟なルーティングシステム</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-server.git">laminas/laminas-server</a>
    </td>
    <td>ライブラリ</td>
    <td>作成 Reflection ベースの RPC サーバー</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-servicemanager.git">Laminas/Laminas-ServiceManager</a>
    </td>
    <td>ライブラリ</td>
    <td>ファクトリ駆動の依存関係挿入コンテナ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-session.git">laminas/laminas-session</a>
    </td>
    <td>ライブラリ</td>
    <td>PHP セッションおよびストレージへのオブジェクト指向インタフェース</td>
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
    <td>ライブラリ</td>
    <td>SPL 拡張機能、配列ユーティリティ、エラーハンドラーなど</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-text.git">ラミナ/ラミナテキスト</a>
    </td>
    <td>図書館</td>
    <td>作成 図レットとテキストベースのテーブル</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-translator.git"> ラミナス/ラミナス – トランスレータ </a>
    </td>
    <td>ライブラリ</td>
    <td>Laminas-i18n の Translator コンポーネント用インターフェイス</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-uri.git"> ラミナス/ラミナス uri</a>
    </td>
    <td>ライブラリ</td>
    <td>操作と検証を支援するコンポーネント » Uniform Resource Identifier （URI）</td>
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
      <a href="https://github.com/laminas/laminas-view.git"> ラミナス/ラミナス ビュー </a>
    </td>
    <td>ライブラリ</td>
    <td>複数のビューレイヤー、ヘルパーなどをサポートおよび提供する柔軟なビューレイヤー</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/marc-mabe/php-enum.git">marc-mabe/php-enum</a>
    </td>
    <td>ライブラリ</td>
    <td>ネイティブの PHP を使用した定義済みリストのシンプルかつ迅速な実装</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/nikic/PHP-Parser.git">nikic/php-parser</a>
    </td>
    <td>図書館</td>
    <td>PHP で書かれた PHP パーサ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpfui/recaptcha.git">phpui/recaptcha</a>
    </td>
    <td>図書館</td>
    <td>Google の reCAPTCHA for PHP 8.4 以降の クライアント ライブラリ</td>
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
    <td>YUI CSS コンプレッサの PHP ポート</td>
  </tr>
  </tbody>
</table>

### BSD-3 句の変更

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
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_Redis.git">colinmollenhour/cache-backend-redis</a>
    </td>
    <td>magento-モジュール</td>
    <td>タグを完全にサポートする Redis を使用するバックエンドZend_Cache。</td>
  </tr>
  </tbody>
</table>

### ISC

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
      <a href="https://github.com/paragonie/sodium_compat.git">paragonie/sodium_compat</a>
    </td>
    <td>ライブラリ</td>
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
    <td>図書館</td>
    <td>PHPで書かれた標準規格準拠のHTMLフィルタ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-amqplib/php-amqplib.git">php-amqplib/php-amqplib</a>
    </td>
    <td>ライブラリ</td>
    <td>以前は videlalvaro/php-amqplib でした。  このライブラリは、AMQP プロトコルを PHP で実装したものです。 RabbitMQ に対してテストされています。</td>
  </tr>
  </tbody>
</table>

### MIT

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
      <a href="https://github.com/braintree/braintree_php.git">braintree/braintree_php</a>
    </td>
    <td>ライブラリ</td>
    <td>Braintree PHP クライアントライブラリ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/math.git">レンガ/数学</a>
    </td>
    <td>ライブラリ</td>
    <td>任意精度演算ライブラリ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/varexporter.git">brick/varexporter</a>
    </td>
    <td>ライブラリ</td>
    <td>var_export （）の代わりとなる強力な関数で、__set_state （）を使用せずにクロージャやオブジェクトをエクスポートすることができます。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ChristianRiesen/base32.git">christian-riesen/base32</a>
    </td>
    <td>ライブラリ</td>
    <td>RFC 4648 に準拠した Base32 エンコーダー/デコーダー</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/credis.git"> コリンモレンアワー/クレディ </a>
    </td>
    <td>図書館</td>
    <td>Credis は Redis キーと値のストアへの軽量インターフェイスで、パフォーマンスを向上させるために phpredis ライブラリ をラップします。</td>
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
    <td>ライブラリ</td>
    <td>PHP コードをスキャンし、クラスマップを生成するためのユーティリティ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/composer.git">composer/composer</a>
    </td>
    <td>ライブラリ</td>
    <td>Composerは、PHPプロジェクトの依存関係を宣言、管理、およびインストールするのに役立ちます。 これにより、どこにでも適切なスタックを確保できます。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/metadata-minifier.git">composer/メタデータ-minifier</a>
    </td>
    <td>図書館</td>
    <td>メタデータの縮小と拡張を処理する小さなユーティリティライブラリ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/pcre.git">composer/pcre</a>
    </td>
    <td>ライブラリ</td>
    <td>タイプセーフな preg_*代替品を提供する PCRE ラッピングライブラリ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/semver.git">composer/semver</a>
    </td>
    <td>ライブラリ</td>
    <td>ユーティリティ、バージョン制約の解析、および検証を提供する Semver ライブラリ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/spdx-licenses.git">composer/spdx-licenses</a>
    </td>
    <td>ライブラリ</td>
    <td>SPDXライセンスリストおよび検証ライブラリ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/xdebug-handler.git">composer/xdebug-handler</a>
    </td>
    <td>図書館</td>
    <td>Xdebug なしでプロセスを再起動します。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/doctrine/lexer.git"> ドクトリン/レキサー </a>
    </td>
    <td>ライブラリ</td>
    <td>トップダウン、再帰的なディセントリーパーサーで使用できる PHP ドクトリンレクサーパーサーライブラリ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/egulias/EmailValidator.git">egulias/email-validator</a>
    </td>
    <td>ライブラリ</td>
    <td>複数の RFC に対してメールを検証するためのライブラリ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/elastic/elastic-transport-php.git"> 弾力性/輸送性 </a>
    </td>
    <td>ライブラリ</td>
    <td>Elastic 製品用の HTTP トランスポート PHP ライブラリ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/elastic/elasticsearch-php.git">elasticsearch/elasticsearch</a>
    </td>
    <td>ライブラリ</td>
    <td>Elasticsearch用 PHP クライアント</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/endroid/qr-code.git">endroid/qr-code</a>
    </td>
    <td>ライブラリ</td>
    <td>Endroid QR コード</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/guzzlestreams.git">ezimuel/guzzlestreams</a>
    </td>
    <td>ライブラリ</td>
    <td>elasticsearch-php で使用される guzzle/streams のフォーク（放棄）</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/ringphp.git">ezimuel/ringphp</a>
    </td>
    <td>図書館</td>
    <td>弾性検索-phpで使用するためのguzzle/RingPHPのフォーク(放棄)</td>
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
    <td>ライブラリ</td>
    <td>Guzzle Promises ライブラリ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/psr7.git">guzzlehttp/psr7</a>
    </td>
    <td>ライブラリ</td>
    <td>一般的なユーティリティメソッドも提供するPSR-7メッセージ実装</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jsonrainbow/json-schema.git">justinrainbow/json-スキーマ</a>
    </td>
    <td>ライブラリ</td>
    <td>JSON スキーマを検証するためのライブラリ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem.git">league/flysystem</a>
    </td>
    <td>ライブラリ</td>
    <td>PHP のファイルストレージの抽象化</td>
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
    <td>ライブラリ</td>
    <td>Flysystem 用のローカルファイルシステムアダプタ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/mime-type-detection.git">league/mime-type-detection</a>
    </td>
    <td>ライブラリ</td>
    <td>Flysystem の MIME タイプ検出</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/monolog.git"> 独白/独白 </a>
    </td>
    <td>ライブラリ</td>
    <td>ファイル、ソケット、受信ボックス、データベース、および様々な web サービスにログを送信します。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jmespath/jmespath.php.git">mtdowling/jmespath.php</a>
    </td>
    <td>ライブラリ</td>
    <td>JSON ドキュメントから要素を抽出する方法を宣言的に指定します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/constant_time_encoding.git">paragonie/constant_time_encoding</a>
    </td>
    <td>ライブラリ</td>
    <td>RFC 4648 エンコーディングの定時間実装（Base-64、Base-32、Base-16）</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/random_compat.git">paragonie/random_compat</a>
    </td>
    <td>ライブラリ</td>
    <td>PHP 5.x における random_bytes （）と random_int （）のポリフィルは PHP 7 から提供されています。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/emogrifier.git"> ペラゴ/顔文字 </a>
    </td>
    <td>ライブラリ</td>
    <td>CSS スタイルをHTML コードのインラインスタイル属性に変換します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/discovery.git">php-http/discovery</a>
    </td>
    <td>composer-plugin</td>
    <td>PSR-7、PSR-17、PSR-18 および HTTPlug 実装を検索してインストールします</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/httplug.git">php-http/httplug</a>
    </td>
    <td>図書館</td>
    <td>HTTPlug:PHP 用の HTTP クライアントの抽象化</td>
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
    <td>ライブラリ</td>
    <td>CSS セレクターを XPath クエリに変換します。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/Dom.git">phpgt/dom</a>
    </td>
    <td>ライブラリ</td>
    <td>最新の DOM API。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/PropFunc.git">phpgt/propfunc</a>
    </td>
    <td>図書館</td>
    <td>プロパティアクセサー関数とミューテータ関数。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/mcrypt_compat.git">phpseclib/mcrypt_compat</a>
    </td>
    <td>ライブラリ</td>
    <td>PHP 5.x-8.x polyfill （mcrypt 拡張モジュール用）</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/phpseclib.git">phpseclib/phpseclib</a>
    </td>
    <td>ライブラリ</td>
    <td>PHP Secure Communications Library - RSA、AES、SSH2、SFTP、X.509 などの純粋な PHP 実装。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/cache.git">psr/cache</a>
    </td>
    <td>ライブラリ</td>
    <td>ライブラリをキャッシュするための共通インターフェイス</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/clock.git">psr/clock</a>
    </td>
    <td>ライブラリ</td>
    <td>クロックを読み取るための共通インターフェイス。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/container.git">psr/container</a>
    </td>
    <td>ライブラリ</td>
    <td>共通コンテナインタフェース （PHP FIG PSR-11）</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/event-dispatcher.git">psr/event-dispatcher</a>
    </td>
    <td>ライブラリ</td>
    <td>イベント処理の標準インターフェイス。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-client.git">psr/http-client</a>
    </td>
    <td>ライブラリ</td>
    <td>HTTP クライアントの共通インターフェイス</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-factory.git">psr/http-factory</a>
    </td>
    <td>ライブラリ</td>
    <td>PSR-17:PSR-7 HTTP メッセージファクトリの共通インターフェイス</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-message.git">psr/http-message</a>
    </td>
    <td>ライブラリ</td>
    <td>HTTP メッセージの共通インターフェイス</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/log.git">psr/log</a>
    </td>
    <td>ライブラリ</td>
    <td>ライブラリをログに記録するための共通インターフェイス</td>
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
    <td>PHP 用の CommonJS Promises/A の軽量実装</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/PHP-CSS-Parser.git">sabberworm/php-css-parser</a>
    </td>
    <td>図書館</td>
    <td>PHP で記述された CSS ファイルパーサ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/jsonlint.git">seld/jsonlint</a>
    </td>
    <td>ライブラリ</td>
    <td>JSON リンター</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/phar-utils.git">seld/phar-utils</a>
    </td>
    <td>ライブラリ</td>
    <td>PHAR ファイル形式ユーティリティ（PHP が起動した場合に使用）</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/signal-handler.git">seld/signal-handler</a>
    </td>
    <td>ライブラリ</td>
    <td>クロスプラットフォーム開発を容易にするためにシグナルがサポートされていない場合にサイレントに失敗するシンプルな Unix シグナルハンドラー</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/aes-key-wrap.git">spomky-labs/aes-key-wrap</a>
    </td>
    <td>ライブラリ</td>
    <td>PHP 用の AES キーのラップ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/otphp.git">spomky-labs/otphp</a>
    </td>
    <td>ライブラリ</td>
    <td>RFC 4226 （HOTP アルゴリズム）および RFC 6238 （TOTP アルゴリズム）に従ってワンタイム パスワードを生成し、Google Authenticator と互換性のある PHP ライブラリ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/pki-framework.git">spomky-labs/pki-framework</a>
    </td>
    <td>ライブラリ</td>
    <td>公開鍵インフラストラクチャを管理するための PHP フレームワーク。 X.509 公開鍵証明書、属性証明書、証明書リクエストおよび証明書パス検証で構成されます。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/config.git">symfony/config</a>
    </td>
    <td>ライブラリ</td>
    <td>あらゆる種類の設定値を検索、読み込み、組み合わせ、自動入力および検証するのに役立ちます</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/console.git">symfony/console</a>
    </td>
    <td>ライブラリ</td>
    <td>美しくテスト可能なコマンドラインインターフェイスの作成が容易になります。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/css-selector.git">symfony/css-selector</a>
    </td>
    <td>ライブラリ</td>
    <td>CSS セレクターを XPath 式に変換</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/dependency-injection.git">symfony/dependency-injection</a>
    </td>
    <td>ライブラリ</td>
    <td>アプリケーション内でのオブジェクトの構築方法を標準化および集中化できます。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/deprecation-contracts.git">symfony/deprecation-contracts</a>
    </td>
    <td>ライブラリ</td>
    <td>トリガー廃止通知の一般的な関数と規則</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/error-handler.git">symfony/error-handler</a>
    </td>
    <td>図書館</td>
    <td>エラーを管理し、PHPコードのデバッグを容易にするツールを提供します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher.git">symfony/イベント-dispatcher</a>
    </td>
    <td>図書館</td>
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
    <td>図書館</td>
    <td>直感的で流暢なインターフェースを介してファイルとディレクトリを検索します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client.git">symfony/http-client</a>
    </td>
    <td>図書館</td>
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
    <td>図書館</td>
    <td>要求を応答に変換するための構造化されたプロセスを提供します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/intl.git">symfony/intl</a>
    </td>
    <td>図書館</td>
    <td>ICUライブラリのローカライゼーションデータへのアクセスを提供</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/mailer.git">symfony/mailer</a>
    </td>
    <td>図書館</td>
    <td>メールの送信に役立ちます</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/mime.git">symfony/mime</a>
    </td>
    <td>ライブラリ</td>
    <td>MIME メッセージの操作を許可</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-ctype.git">symfony/polyfill-ctype</a>
    </td>
    <td>ライブラリ</td>
    <td>ctype 関数のシンボリックリポリ入力</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-grapheme.git">symfony/polyfill-intl-grapheme</a>
    </td>
    <td>図書館</td>
    <td>intl の grapheme_* 関数のための symfony polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-idn.git">symfony/polyfill-intl-idn</a>
    </td>
    <td>ライブラリ</td>
    <td>intl の idn_to_ascii 関数と idn_to_utf8 関数に対するシンボリックリポリフィル</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-normalizer.git">symfony/polyfill-intl-normalizer</a>
    </td>
    <td>ライブラリ</td>
    <td>symfony polyfill for intl のノーマライザークラスと関連関数</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-mbstring.git">symfony/polyfill-mbstring</a>
    </td>
    <td>図書館</td>
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
    <td>図書館</td>
    <td>symfony ポリフィルがいくつかの PHP 8.0+ 機能を下位の PHP バージョンにバックポートする</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php81.git">symfony/polyfill-php81</a>
    </td>
    <td>図書館</td>
    <td>symfony ポリフィル PHP 8.1+ の機能を下位の PHP バージョンにバックポートする</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php82.git">symfony/polyfill-php82</a>
    </td>
    <td>図書館</td>
    <td>symfony ポリフィルがいくつかの PHP 8.2+ 機能を下位の PHP バージョンにバックポートする</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php83.git">symfony/polyfill-php83</a>
    </td>
    <td>ライブラリ</td>
    <td>symfony ポリフィル PHP 8.3+ の機能を下位の PHP バージョンにバックポートする</td>
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
    <td>サービスの記述に関連する一般的な抽象概念</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/string.git">symfony/string</a>
    </td>
    <td>ライブラリ</td>
    <td>文字列へのオブジェクト指向 API を提供し、バイト、UTF-8 コードポイントおよび grapheme クラスターを統一された方法で処理します</td>
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
    <td>ライブラリ</td>
    <td>YAML ファイルの読み込みとダンプ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/web-token/jwt-framework.git">web-token/jwt-framework</a>
    </td>
    <td>交響束</td>
    <td>PHP と symfony バンドル用の JSON オブジェクト の署名と暗号化のライブラリ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webonyx/graphql-php.git">webonyx/graphql-php</a>
    </td>
    <td>ライブラリ</td>
    <td>GraphQL参照実装の PHP ポート</td>
  </tr>
  </tbody>
</table>

### OSL-3.0、AFL-3.0

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
      PayPal/モジュール-ブレインツリー-顧客-バランス
    </td>
    <td>マジェント2-モジュール</td>
    <td>該当なし</td>
  </tr>
  <tr>
    <td>
      PayPal/モジュール-ブレインツリー-ギフト-カード
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
      PayPal/モジュール-ブレインツリー-ギフトラッピング
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
      PayPal/モジュール-ブレインツリー-報酬
    </td>
    <td>マジェント2-モジュール</td>
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
      <th>タイプ</th>
      <th>説明</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/2tvenom/CBOREncode.git">2tvenom/cborencode</a>
    </td>
    <td>図書館</td>
    <td>PHP 用 CBOR エンコーダ</td>
  </tr>
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
    <td>Magentoからのフォーク Braintree 2.2.0 モジュール PayPalのためのジーンコマースによって。</td>
  </tr>
  </tbody>
</table>
