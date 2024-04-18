---
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '1986'
ht-degree: 0%

---
# Magento Open Sourceパッケージ

<!-- The 'packages' variable contains the 'packages' node of the '_data/codebase/open-source/composer_lock.json' file
 -->

<!-- The 'packages-dev' variable contains the 'packages-dev' node of the '_data/codebase/open-source/composer_lock.json' file
 -->

<!-- The 'product' variable contains data of the 'magento/product-community-edition' package
 -->

<!-- The edition variable contains `open-source` value from the _data/names.yml file
 -->

Magento Open Sourceでは、Composer を使用して PHP パッケージを管理します。

この `composer.json` ファイルはパッケージのリストを宣言するのに対して、 `composer.lock` ファイルには、Magento Open Sourceのインストールの構築に使用されるパッケージの完全なリスト（各パッケージの完全なバージョンとその依存関係）が保存されます。

次のリファレンスドキュメントは、 `composer.lock` ファイルで、Magento Open Source 2.4.7 に含まれている必須パッケージについて説明しています。

## 依存関係

`magento/product-community-edition 2.4.7` には次の依存関係があります。

```config
adobe-commerce/os-extensions-metapackage: ~1.0
colinmollenhour/cache-backend-file: ^1.4
colinmollenhour/cache-backend-redis: ^1.16
colinmollenhour/credis: ^1.15
colinmollenhour/php-redis-session-abstract: ^1.5
composer/composer: ^2.0, !=2.2.16
elasticsearch/elasticsearch: ~7.17.0 || ~8.5.0
ext-bcmath: *
ext-ctype: *
ext-curl: *
ext-dom: *
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
laminas/laminas-captcha: ^2.17
laminas/laminas-code: ^4.13
laminas/laminas-db: ^2.19
laminas/laminas-di: ^3.13
laminas/laminas-escaper: ^2.13
laminas/laminas-eventmanager: ^3.11
laminas/laminas-feed: ^2.22
laminas/laminas-file: ^2.13
laminas/laminas-filter: ^2.33
laminas/laminas-http: ^2.15
laminas/laminas-i18n: ^2.17
laminas/laminas-mail: ^2.16
laminas/laminas-mime: ^2.9
laminas/laminas-modulemanager: ^2.11
laminas/laminas-mvc: ^3.6
laminas/laminas-oauth: ^2.6
laminas/laminas-permissions-acl: ^2.10
laminas/laminas-server: ^2.16
laminas/laminas-servicemanager: ^3.16
laminas/laminas-soap: ^2.10
laminas/laminas-stdlib: ^3.11
laminas/laminas-uri: ^2.9
laminas/laminas-validator: ^2.23
league/flysystem: ^2.4
league/flysystem-aws-s3-v3: ^2.4
lib-libxml: *
magento/composer: ^1.10.0-beta1
magento/composer-dependency-version-audit-plugin: ^0.1
magento/framework: 103.0.7
magento/framework-amqp: 100.4.5
magento/framework-bulk: 101.0.3
magento/framework-message-queue: 100.4.7
magento/inventory-metapackage: 1.2.7
magento/language-de_de: 100.4.0
magento/language-en_us: 100.4.0
magento/language-es_es: 100.4.0
magento/language-fr_fr: 100.4.0
magento/language-nl_nl: 100.4.0
magento/language-pt_br: 100.4.0
magento/language-zh_hans_cn: 100.4.0
magento/magento-composer-installer: >=0.4.0
magento/magento2-base: 2.4.7
magento/module-admin-analytics: 100.4.6
magento/module-admin-notification: 100.4.6
magento/module-advanced-pricing-import-export: 100.4.7
magento/module-advanced-search: 100.4.5
magento/module-amqp: 100.4.4
magento/module-analytics: 100.4.7
magento/module-application-performance-monitor: 100.4.0
magento/module-application-performance-monitor-new-relic: 100.4.0
magento/module-async-config: 100.4.0
magento/module-asynchronous-operations: 100.4.7
magento/module-authorization: 100.4.7
magento/module-aws-s3: 100.4.5
magento/module-backend: 102.0.7
magento/module-backup: 100.4.7
magento/module-bundle: 101.0.7
magento/module-bundle-graph-ql: 100.4.7
magento/module-bundle-import-export: 100.4.6
magento/module-cache-invalidate: 100.4.5
magento/module-captcha: 100.4.7
magento/module-cardinal-commerce: 100.4.5
magento/module-catalog: 104.0.7
magento/module-catalog-analytics: 100.4.4
magento/module-catalog-cms-graph-ql: 100.4.3
magento/module-catalog-customer-graph-ql: 100.4.6
magento/module-catalog-graph-ql: 100.4.7
magento/module-catalog-import-export: 101.1.7
magento/module-catalog-inventory: 100.4.7
magento/module-catalog-inventory-graph-ql: 100.4.4
magento/module-catalog-rule: 101.2.7
magento/module-catalog-rule-configurable: 100.4.6
magento/module-catalog-rule-graph-ql: 100.4.4
magento/module-catalog-search: 102.0.7
magento/module-catalog-url-rewrite: 100.4.7
magento/module-catalog-url-rewrite-graph-ql: 100.4.5
magento/module-catalog-widget: 100.4.7
magento/module-checkout: 100.4.7
magento/module-checkout-agreements: 100.4.6
magento/module-checkout-agreements-graph-ql: 100.4.3
magento/module-cms: 104.0.7
magento/module-cms-graph-ql: 100.4.4
magento/module-cms-url-rewrite: 100.4.6
magento/module-cms-url-rewrite-graph-ql: 100.4.5
magento/module-compare-list-graph-ql: 100.4.3
magento/module-config: 101.2.7
magento/module-configurable-import-export: 100.4.5
magento/module-configurable-product: 100.4.7
magento/module-configurable-product-graph-ql: 100.4.7
magento/module-configurable-product-sales: 100.4.4
magento/module-contact: 100.4.6
magento/module-contact-graph-ql: 100.4.0
magento/module-cookie: 100.4.7
magento/module-cron: 100.4.7
magento/module-csp: 100.4.6
magento/module-currency-symbol: 100.4.5
magento/module-customer: 103.0.7
magento/module-customer-analytics: 100.4.4
magento/module-customer-downloadable-graph-ql: 100.4.3
magento/module-customer-graph-ql: 100.4.7
magento/module-customer-import-export: 100.4.7
magento/module-deploy: 100.4.7
magento/module-developer: 100.4.7
magento/module-dhl: 100.4.6
magento/module-directory: 100.4.7
magento/module-directory-graph-ql: 100.4.5
magento/module-downloadable: 100.4.7
magento/module-downloadable-graph-ql: 100.4.7
magento/module-downloadable-import-export: 100.4.6
magento/module-eav: 102.1.7
magento/module-eav-graph-ql: 100.4.4
magento/module-elasticsearch: 101.0.7
magento/module-elasticsearch-7: 100.4.7
magento/module-email: 101.1.7
magento/module-encryption-key: 100.4.5
magento/module-fedex: 100.4.5
magento/module-gift-message: 100.4.6
magento/module-gift-message-graph-ql: 100.4.5
magento/module-google-adwords: 100.4.4
magento/module-google-analytics: 100.4.3
magento/module-google-gtag: 100.4.2
magento/module-google-optimizer: 100.4.6
magento/module-graph-ql: 100.4.7
magento/module-graph-ql-cache: 100.4.4
magento/module-graph-ql-new-relic: 100.4.0
magento/module-graph-ql-resolver-cache: 100.4.0
magento/module-grouped-catalog-inventory: 100.4.4
magento/module-grouped-import-export: 100.4.5
magento/module-grouped-product: 100.4.7
magento/module-grouped-product-graph-ql: 100.4.7
magento/module-import-export: 101.0.7
magento/module-indexer: 100.4.7
magento/module-instant-purchase: 100.4.6
magento/module-integration: 100.4.7
magento/module-integration-graph-ql: 100.4.0
magento/module-jwt-framework-adapter: 100.4.3
magento/module-jwt-user-token: 100.4.2
magento/module-layered-navigation: 100.4.7
magento/module-login-as-customer: 100.4.7
magento/module-login-as-customer-admin-ui: 100.4.7
magento/module-login-as-customer-api: 100.4.6
magento/module-login-as-customer-assistance: 100.4.6
magento/module-login-as-customer-frontend-ui: 100.4.6
magento/module-login-as-customer-graph-ql: 100.4.4
magento/module-login-as-customer-log: 100.4.5
magento/module-login-as-customer-page-cache: 100.4.6
magento/module-login-as-customer-quote: 100.4.5
magento/module-login-as-customer-sales: 100.4.6
magento/module-marketplace: 100.4.5
magento/module-media-content: 100.4.5
magento/module-media-content-api: 100.4.6
magento/module-media-content-catalog: 100.4.5
magento/module-media-content-cms: 100.4.5
magento/module-media-content-synchronization: 100.4.6
magento/module-media-content-synchronization-api: 100.4.5
magento/module-media-content-synchronization-catalog: 100.4.4
magento/module-media-content-synchronization-cms: 100.4.4
magento/module-media-gallery: 100.4.6
magento/module-media-gallery-api: 101.0.6
magento/module-media-gallery-catalog: 100.4.4
magento/module-media-gallery-catalog-integration: 100.4.4
magento/module-media-gallery-catalog-ui: 100.4.4
magento/module-media-gallery-cms-ui: 100.4.4
magento/module-media-gallery-integration: 100.4.6
magento/module-media-gallery-metadata: 100.4.5
magento/module-media-gallery-metadata-api: 100.4.4
magento/module-media-gallery-renditions: 100.4.5
magento/module-media-gallery-renditions-api: 100.4.4
magento/module-media-gallery-synchronization: 100.4.6
magento/module-media-gallery-synchronization-api: 100.4.5
magento/module-media-gallery-synchronization-metadata: 100.4.3
magento/module-media-gallery-ui: 100.4.6
magento/module-media-gallery-ui-api: 100.4.5
magento/module-media-storage: 100.4.6
magento/module-message-queue: 100.4.7
magento/module-msrp: 100.4.6
magento/module-msrp-configurable-product: 100.4.4
magento/module-msrp-grouped-product: 100.4.4
magento/module-multishipping: 100.4.7
magento/module-mysql-mq: 100.4.5
magento/module-new-relic-reporting: 100.4.5
magento/module-newsletter: 100.4.7
magento/module-newsletter-graph-ql: 100.4.4
magento/module-offline-payments: 100.4.5
magento/module-offline-shipping: 100.4.6
magento/module-open-search: 100.4.1
magento/module-order-cancellation: 100.4.0
magento/module-order-cancellation-graph-ql: 100.4.0
magento/module-order-cancellation-ui: 100.4.0
magento/module-page-cache: 100.4.7
magento/module-payment: 100.4.7
magento/module-payment-graph-ql: 100.4.2
magento/module-paypal: 101.0.7
magento/module-paypal-captcha: 100.4.4
magento/module-paypal-graph-ql: 100.4.5
magento/module-persistent: 100.4.7
magento/module-product-alert: 100.4.6
magento/module-product-video: 100.4.7
magento/module-quote: 101.2.7
magento/module-quote-analytics: 100.4.6
magento/module-quote-bundle-options: 100.4.3
magento/module-quote-configurable-options: 100.4.3
magento/module-quote-downloadable-links: 100.4.3
magento/module-quote-graph-ql: 100.4.7
magento/module-related-product-graph-ql: 100.4.4
magento/module-release-notification: 100.4.5
magento/module-remote-storage: 100.4.5
magento/module-reports: 100.4.7
magento/module-require-js: 100.4.3
magento/module-review: 100.4.7
magento/module-review-analytics: 100.4.4
magento/module-review-graph-ql: 100.4.3
magento/module-robots: 101.1.3
magento/module-rss: 100.4.5
magento/module-rule: 100.4.6
magento/module-sales: 103.0.7
magento/module-sales-analytics: 100.4.4
magento/module-sales-graph-ql: 100.4.7
magento/module-sales-inventory: 100.4.4
magento/module-sales-rule: 101.2.7
magento/module-sales-rule-graph-ql: 100.4.0
magento/module-sales-sequence: 100.4.4
magento/module-sample-data: 100.4.5
magento/module-search: 101.1.7
magento/module-security: 100.4.7
magento/module-send-friend: 100.4.5
magento/module-send-friend-graph-ql: 100.4.3
magento/module-shipping: 100.4.7
magento/module-sitemap: 100.4.6
magento/module-store: 101.1.7
magento/module-store-graph-ql: 100.4.5
magento/module-swagger: 100.4.6
magento/module-swagger-webapi: 100.4.3
magento/module-swagger-webapi-async: 100.4.3
magento/module-swatches: 100.4.7
magento/module-swatches-graph-ql: 100.4.5
magento/module-swatches-layered-navigation: 100.4.3
magento/module-tax: 100.4.7
magento/module-tax-graph-ql: 100.4.3
magento/module-tax-import-export: 100.4.6
magento/module-theme: 101.1.7
magento/module-theme-graph-ql: 100.4.4
magento/module-translation: 100.4.7
magento/module-ui: 101.2.7
magento/module-ups: 100.4.7
magento/module-url-rewrite: 102.0.6
magento/module-url-rewrite-graph-ql: 100.4.6
magento/module-user: 101.2.7
magento/module-usps: 100.4.6
magento/module-variable: 100.4.5
magento/module-vault: 101.2.7
magento/module-vault-graph-ql: 100.4.3
magento/module-version: 100.4.4
magento/module-webapi: 100.4.6
magento/module-webapi-async: 100.4.5
magento/module-webapi-security: 100.4.4
magento/module-weee: 100.4.7
magento/module-weee-graph-ql: 100.4.4
magento/module-widget: 101.2.7
magento/module-wishlist: 101.2.7
magento/module-wishlist-analytics: 100.4.5
magento/module-wishlist-graph-ql: 100.4.7
magento/page-builder: 1.7.4
magento/security-package: 1.1.6
magento/theme-adminhtml-backend: 100.4.7
magento/theme-frontend-blank: 100.4.7
magento/theme-frontend-luma: 100.4.7
magento/zend-cache: ^1.16
magento/zend-db: ^1.16
magento/zend-pdf: ^1.16
monolog/monolog: ^2.7
opensearch-project/opensearch-php: ^1.0 || ^2.0
pelago/emogrifier: ^7.0
php: ~8.1.0||~8.2.0||~8.3.0
php-amqplib/php-amqplib: ^3.2
phpseclib/mcrypt_compat: ^2.0
phpseclib/phpseclib: ^3.0
psr/log: ^2 || ^3
ramsey/uuid: ^4.2
symfony/console: ^6.4
symfony/intl: ^6.4
symfony/process: ^6.4
symfony/string: ^6.4
tedivm/jshrink: ^1.4
tubalmartin/cssmin: ^4.1
web-token/jwt-framework: ^3.1
webonyx/graphql-php: ^15.0
wikimedia/less.php: ^3.2
```

## サードパーティライセンス

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
      <a href="https://github.com/elastic/elasticsearch-php.git">elasticsearch/elasticsearch</a>
    </td>
    <td>ライブラリ</td>
    <td>Elasticsearch用 PHP クライアント</td>
  </tr>
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
      <th>タイプ</th>
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
      <a href="https://github.com/colinmollenhour/php-redis-session-abstract.git">colinmollenhour/php-redis-session-abstract</a>
    </td>
    <td>ライブラリ</td>
    <td>楽観的ロックを使用した Redis ベースのセッションハンドラー</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/firebase/php-jwt.git">firebase/php-jwt</a>
    </td>
    <td>ライブラリ</td>
    <td>PHP で JSON ウェブトークン（JWT）をエンコードし、デコードするためのシンプルなライブラリ。 現在の仕様に準拠する必要があります。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/google/recaptcha.git">google/recaptcha</a>
    </td>
    <td>ライブラリ</td>
    <td>Web サイトをスパムや不正使用から保護する無料サービスである reCAPTCHA のクライアントライブラリ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-captcha.git">ラミナス/ラミナス – キャプチャ</a>
    </td>
    <td>ライブラリ</td>
    <td>置物、画像、ReCaptcha などを使用した CAPTCHA の生成と検証</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-code.git">ラミナス/ラミナス符号</a>
    </td>
    <td>ライブラリ</td>
    <td>PHP Reflection API、静的コードスキャン、およびコード生成の拡張</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-config.git">laminas/laminas-config</a>
    </td>
    <td>ライブラリ</td>
    <td>アプリケーション コード内でこの構成データにアクセスするための、ネストされたオブジェクト プロパティ ベースのユーザーインターフェイスを提供します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-crypt.git">ラミナス/ラミナス陰窩</a>
    </td>
    <td>ライブラリ</td>
    <td>強力な暗号化ツールとパスワードハッシュ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-db.git">ラミナス/ラミナス – db</a>
    </td>
    <td>ライブラリ</td>
    <td>データベース抽象化レイヤー、SQL 抽象化、結果セット抽象化、RowDataGateway および TableDataGateway の実装</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-di.git">ラミナス/ラミナス – ディ</a>
    </td>
    <td>ライブラリ</td>
    <td>PSR-11 コンテナの自動依存関係インジェクション</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-escaper.git">ラミナス/ラミナスエスケープ</a>
    </td>
    <td>ライブラリ</td>
    <td>HTML、HTML属性、JavaScript、CSS および URL を安全かつ安全にエスケープ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-eventmanager.git">ラミナス/ラミナス – イベントマネージャ</a>
    </td>
    <td>ライブラリ</td>
    <td>PHP アプリケーション内のイベントをトリガーしてリッスンする</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-feed.git">ラミナス/ラミナス供給</a>
    </td>
    <td>ライブラリ</td>
    <td>rss および Atom フィードを作成および使用する機能を提供します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-file.git">ラミナス/ラミナス ファイル</a>
    </td>
    <td>ライブラリ</td>
    <td>PHP クラスファイルを見つける</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-filter.git">ラミナス/ラミナスフィルター</a>
    </td>
    <td>ライブラリ</td>
    <td>データとファイルをプログラムでフィルタリングし、正規化する</td>
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
      <a href="https://github.com/laminas/laminas-i18n.git">ラミナス/ラミナス – i18n</a>
    </td>
    <td>ライブラリ</td>
    <td>アプリケーションの翻訳を提供し、国際化値をフィルタリングおよび検証します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-json.git">laminas/laminas-json</a>
    </td>
    <td>ライブラリ</td>
    <td>は、ネイティブの PHP を JSON にシリアル化し、JSON をネイティブの PHP にデコードする便利なメソッドを提供します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-loader.git">ラミナス/ラミナスローダー</a>
    </td>
    <td>ライブラリ</td>
    <td>自動読み込みとプラグインの読み込み戦略</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mail.git">laminas/laminas-mail</a>
    </td>
    <td>ライブラリ</td>
    <td>テキストと MIME に準拠したマルチパート形式のメールメッセージを作成して送信する一般的な機能を提供</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-math.git">laminas/laminas-math</a>
    </td>
    <td>ライブラリ</td>
    <td>暗号学的に安全な擬似乱数を作成し、大きな整数を管理します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mime.git">laminas/laminas-mime</a>
    </td>
    <td>ライブラリ</td>
    <td>MIME メッセージおよび部分の作成と解析</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-modulemanager.git">ラミナス/ラミナス – モジュールマネージャー</a>
    </td>
    <td>ライブラリ</td>
    <td>ラミナス mvc アプリケーション用モジュール式アプリケーションシステム</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mvc.git">ラミナス/ラミナス – mvc</a>
    </td>
    <td>ライブラリ</td>
    <td>Laminas のイベント駆動型 MVC レイヤー（MVC アプリケーション、コントローラ、プラグインを含む）</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-oauth.git">laminas/laminas-oauth</a>
    </td>
    <td>ライブラリ</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-permissions-acl.git">laminas/laminas-permissions-acl</a>
    </td>
    <td>ライブラリ</td>
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
    <td>ライブラリ</td>
    <td>HTTP およびコンソールアプリケーション用の柔軟なルーティングシステム</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-server.git">ラミナス/ラミナス サーバ</a>
    </td>
    <td>ライブラリ</td>
    <td>反射ベースの RPC サーバを作成する</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-servicemanager.git">ラミナス/ラミナス – サービスマネガー</a>
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
      <a href="https://github.com/laminas/laminas-soap.git">ラミナス・ラミナス石鹸</a>
    </td>
    <td>ライブラリ</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-stdlib.git">laminas/laminas-stdlib</a>
    </td>
    <td>ライブラリ</td>
    <td>SPL 拡張機能、配列ユーティリティ、エラーハンドラーなど</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-text.git">ラミナス/ラミナス テキスト</a>
    </td>
    <td>ライブラリ</td>
    <td>FIGlets とテキストベースのテーブルの作成</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-uri.git">laminas/laminas-uri</a>
    </td>
    <td>ライブラリ</td>
    <td>操作と検証を支援するコンポーネント » Uniform Resource Identifier （URI）</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-validator.git">ラミナス/ラミナスバリデーター</a>
    </td>
    <td>ライブラリ</td>
    <td>幅広いドメイン向けの検証クラスと、複雑な検証条件を作成するためにバリデータを連結する機能</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-view.git">laminas/laminas-view</a>
    </td>
    <td>ライブラリ</td>
    <td>複数のビューレイヤー、ヘルパーなどをサポートおよび提供する柔軟なビューレイヤー</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/nikic/PHP-Parser.git">nikic/php-parser</a>
    </td>
    <td>ライブラリ</td>
    <td>PHP で書かれた PHP パーサ</td>
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
      <a href="https://github.com/tubalmartin/YUI-CSS-compressor-PHP-port.git">ツバルマーティン/cssmin</a>
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
    <td>ライブラリ</td>
    <td>PHP で書かれた標準準拠のHTMLフィルタ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-amqplib/php-amqplib.git">php-amqplib/php-amqplib</a>
    </td>
    <td>ライブラリ</td>
    <td>以前は videlalvaro/php-amqplib でした。  このライブラリは、AMQP プロトコルを PHP で実装したものです。 RabbitMQに対してテストされています。</td>
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
      <a href="https://github.com/brick/math.git">れんが/数学</a>
    </td>
    <td>ライブラリ</td>
    <td>任意精度演算ライブラリ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/varexporter.git">レンガ/ベラエクスポーター</a>
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
      <a href="https://github.com/colinmollenhour/credis.git">コリンモレン時間/単位</a>
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
    <td>ライブラリ</td>
    <td>PHP コードをスキャンし、クラスマップを生成するためのユーティリティ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/composer.git">composer/composer</a>
    </td>
    <td>ライブラリ</td>
    <td>Composer を使用すると、PHP プロジェクトの依存関係を宣言、管理、およびインストールできます。 あらゆる場所に適切なスタックを確保できます。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/metadata-minifier.git">コンポーザー/メタデータ縮小子</a>
    </td>
    <td>ライブラリ</td>
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
    <td>ライブラリ</td>
    <td>Guzzle Promises ライブラリ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/psr7.git">guzzlehttp/psr7</a>
    </td>
    <td>ライブラリ</td>
    <td>共通のユーティリティメソッドも提供する PSR-7 メッセージ実装</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/justinrainbow/json-schema.git">justinrainbow/json-schema</a>
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
      <a href="https://github.com/thephpleague/mime-type-detection.git">league/mime-type-detection</a>
    </td>
    <td>ライブラリ</td>
    <td>Flysystem の MIME タイプ検出</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/monolog.git">モノローグ/モノローグ</a>
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
      <a href="https://github.com/MyIntervals/emogrifier.git">ペラゴ/顔文字</a>
    </td>
    <td>ライブラリ</td>
    <td>CSS スタイルをHTMLコードのインラインスタイル属性に変換します</td>
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
    <td>ライブラリ</td>
    <td>プロパティのアクセサ関数とミューテータ関数。</td>
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
      <a href="https://github.com/php-fig/clock.git">psr/clock</a>
    </td>
    <td>ライブラリ</td>
    <td>クロックを読み取るための共通インターフェイス。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/container.git">psr/コンテナ</a>
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
    <td>PSR-7 HTTP メッセージファクトリの共通インターフェイス</td>
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
      <a href="https://github.com/ramsey/collection.git">ラムジー/コレクション</a>
    </td>
    <td>ライブラリ</td>
    <td>コレクションを表現および操作するための PHP ライブラリ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/uuid.git">ramsey/uuid</a>
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
    <td>を使用すると、アプリケーションでのオブジェクトの作成方法を標準化および一元化できます</td>
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
    <td>ライブラリ</td>
    <td>ファイルシステムの基本的なユーティリティを提供します</td>
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
      <a href="https://github.com/symfony/polyfill-ctype.git">symfony/polyfill-type</a>
    </td>
    <td>ライブラリ</td>
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
    <td>ライブラリ</td>
    <td>intl の idn_to_ascii 関数と idn_to_utf8 関数に対するシンボリックリポリフィル</td>
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
      <a href="https://github.com/symfony/polyfill-php72.git">symfony/polyfill-php72</a>
    </td>
    <td>ライブラリ</td>
    <td>Symfony polyfill は、PHP 7.2 以降の機能を下位の PHP バージョンにバックポートします。</td>
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
    <td>Symfony polyfill は、PHP 8.0 以降の機能を下位の PHP バージョンにバックポートします。</td>
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
      <a href="https://github.com/symfony/polyfill-php83.git">symfony/polyfill-php83</a>
    </td>
    <td>ライブラリ</td>
    <td>Symfony polyfill は、PHP 8.3 以降の機能を下位の PHP バージョンにバックポートする</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/process.git">交信/プロセス</a>
    </td>
    <td>ライブラリ</td>
    <td>サブプロセスでコマンドを実行します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/service-contracts.git">symfony/service-contract</a>
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
    <td>ライブラリ</td>
    <td>シリアライズ可能な PHP データ構造をプレーンな PHP コードにエクスポートする</td>
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
      <a href="https://github.com/webmozarts/assert.git">webmozart/assert</a>
    </td>
    <td>ライブラリ</td>
    <td>メソッドの入力/出力を有効なエラーメッセージで検証するアサーション。</td>
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
      paypal/module-braintree-gift-card-account
    </td>
    <td>magento2-module</td>
    <td>該当なし</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-gift-wrapping
    </td>
    <td>magento2-module</td>
    <td>該当なし</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-graph-ql
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
      <th>タイプ</th>
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

### 専有

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
    <td>PayPal 用の Gene Commerce によるMagentoBraintree 2.2.0 モジュールから分岐。</td>
  </tr>
  </tbody>
</table>
