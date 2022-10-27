---
source-git-commit: a3fa25993f365a85307db45ef16f68eeb12604bb
workflow-type: tm+mt
source-wordcount: '2193'
ht-degree: 0%

---
# Adobe Commerceパッケージ

<!-- The 'packages' variable contains the 'packages' node of the '_data/codebase/commerce/composer_lock.json' file
 -->

<!-- The 'packages-dev' variable contains the 'packages-dev' node of the '_data/codebase/commerce/composer_lock.json' file
 -->

<!-- The 'product' variable contains data of the 'magento/product-enterprise-edition' package
 -->

<!-- The edition variable contains `commerce` value from the _data/names.yml file
 -->

Adobe Commerceは、Composer を使用して PHP パッケージを管理します。

この `composer.json` ファイルはパッケージのリストを宣言し、 `composer.lock` ファイルには、Adobe CommerceまたはMagento Open Sourceのインストールに使用するパッケージの完全なリスト（各パッケージの完全版とその依存関係）が格納されます。

次の参照ドキュメントは、 `composer.lock` ファイルに含まれ、Adobe Commerce 2.4.5 に含まれる必要なパッケージが含まれています。

## 依存関係

`magento/product-enterprise-edition 2.4.5` には次の依存関係があります。

```config
colinmollenhour/cache-backend-file: ~1.4.1
colinmollenhour/cache-backend-redis: 1.14.2
colinmollenhour/credis: 1.13.0
colinmollenhour/php-redis-session-abstract: ~1.4.5
composer/composer: ^1.9 || ^2.0, !=2.2.16
elasticsearch/elasticsearch: ~7.17.0
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
ext-spl: *
ext-xsl: *
ext-zip: *
ezyang/htmlpurifier: ^4.14
guzzlehttp/guzzle: ^7.4.2
laminas/laminas-captcha: ^2.12
laminas/laminas-code: ~4.5.0
laminas/laminas-db: ^2.15.0
laminas/laminas-dependency-plugin: ^2.2.0
laminas/laminas-di: ^3.7.0
laminas/laminas-escaper: ~2.10.0
laminas/laminas-eventmanager: ^3.5.0
laminas/laminas-feed: ^2.17.0
laminas/laminas-http: ^2.15.0
laminas/laminas-json: ^3.3.0
laminas/laminas-mail: ^2.16.0
laminas/laminas-mime: ^2.9.1
laminas/laminas-modulemanager: ^2.11.0
laminas/laminas-mvc: ^3.3.3
laminas/laminas-server: ^2.11.1
laminas/laminas-servicemanager: ^3.11.0
laminas/laminas-soap: ^2.10.0
laminas/laminas-stdlib: ^3.7.1
laminas/laminas-uri: ^2.9.1
laminas/laminas-validator: ^2.17.0
league/flysystem: ~2.4.5
league/flysystem-aws-s3-v3: ^2.4.3
lib-libxml: *
magento/composer: ~1.8.0
magento/composer-dependency-version-audit-plugin: ~0.1
magento/framework-foreign-key: 100.4.4
magento/magento-composer-installer: >=0.3.0
magento/magento2-ee-base: 2.4.5
magento/module-admin-gws: 100.4.5
magento/module-admin-gws-configurable-product: 100.4.2
magento/module-admin-gws-staging: 100.4.2
magento/module-advanced-catalog: 100.4.2
magento/module-advanced-checkout: 100.4.5
magento/module-advanced-rule: 100.4.2
magento/module-advanced-sales-rule: 100.4.2
magento/module-async-order: 100.4.1
magento/module-async-order-graph-ql: 100.4.0
magento/module-aws-s3-customer-custom-attributes: 100.4.2
magento/module-aws-s3-gift-card-import-export: 100.4.2
magento/module-aws-s3-scheduled-import-export: 100.4.2
magento/module-banner: 101.2.5
magento/module-banner-customer-segment: 100.4.3
magento/module-banner-graph-ql: 100.4.1
magento/module-bundle-import-export-staging: 100.4.2
magento/module-bundle-staging: 100.4.5
magento/module-catalog-event: 101.1.4
magento/module-catalog-import-export-staging: 100.4.2
magento/module-catalog-inventory-staging: 100.4.3
magento/module-catalog-permissions: 100.4.5
magento/module-catalog-permissions-graph-ql: 100.4.3
magento/module-catalog-rule-staging: 100.4.5
magento/module-catalog-staging: 100.4.5
magento/module-catalog-staging-graph-ql: 100.4.4
magento/module-catalog-url-rewrite-staging: 100.4.4
magento/module-checkout-address-search: 100.4.4
magento/module-checkout-address-search-gift-registry: 100.4.1
magento/module-checkout-staging: 100.4.4
magento/module-cms-staging: 100.4.5
magento/module-configurable-product-staging: 100.4.4
magento/module-custom-attribute-management: 100.4.4
magento/module-customer-balance: 100.4.5
magento/module-customer-balance-graph-ql: 100.4.2
magento/module-customer-custom-attributes: 100.4.5
magento/module-customer-finance: 100.4.2
magento/module-customer-segment: 102.1.5
magento/module-deferred-total-calculating: 100.4.0
magento/module-downloadable-staging: 100.4.4
magento/module-elasticsearch-catalog-permissions: 100.4.1
magento/module-elasticsearch-catalog-permissions-graph-ql: 100.4.0
magento/module-enterprise: 100.4.3
magento/module-gift-card: 101.3.5
magento/module-gift-card-account: 101.2.5
magento/module-gift-card-account-graph-ql: 100.4.3
magento/module-gift-card-graph-ql: 100.4.5
magento/module-gift-card-import-export: 100.4.2
magento/module-gift-card-staging: 100.4.2
magento/module-gift-message-staging: 100.4.2
magento/module-gift-registry: 101.2.5
magento/module-gift-registry-graph-ql: 100.4.1
magento/module-gift-wrapping: 101.2.4
magento/module-gift-wrapping-graph-ql: 100.4.2
magento/module-gift-wrapping-staging: 100.4.2
magento/module-google-optimizer-staging: 100.4.2
magento/module-google-tag-manager: 100.4.5
magento/module-grouped-product-staging: 100.4.3
magento/module-invitation: 100.4.4
magento/module-layered-navigation-staging: 100.4.2
magento/module-logging: 101.2.5
magento/module-login-as-customer-logging: 100.4.5
magento/module-login-as-customer-website-restriction: 100.4.3
magento/module-media-content-catalog-staging: 100.4.2
magento/module-msrp-staging: 100.4.3
magento/module-multiple-wishlist: 100.4.5
magento/module-multiple-wishlist-graph-ql: 100.4.1
magento/module-payment-staging: 100.4.2
magento/module-persistent-history: 100.4.2
magento/module-price-permissions: 100.4.1
magento/module-product-video-staging: 100.4.2
magento/module-promotion-permissions: 100.4.2
magento/module-quote-gift-card-options: 100.4.2
magento/module-quote-staging: 100.4.2
magento/module-reminder: 101.2.4
magento/module-remote-storage-commerce: 100.4.1
magento/module-resource-connections: 100.4.2
magento/module-review-staging: 100.4.2
magento/module-reward: 101.2.5
magento/module-reward-graph-ql: 100.4.4
magento/module-reward-staging: 100.4.2
magento/module-rma: 101.2.5
magento/module-rma-graph-ql: 100.4.4
magento/module-rma-staging: 100.4.2
magento/module-sales-archive: 101.0.3
magento/module-sales-rule-staging: 100.4.4
magento/module-scalable-checkout: 100.4.4
magento/module-scalable-inventory: 100.4.3
magento/module-scalable-oms: 100.4.3
magento/module-scheduled-import-export: 101.2.5
magento/module-search-staging: 100.4.3
magento/module-staging: 101.2.5
magento/module-staging-graph-ql: 100.4.2
magento/module-support: 101.2.4
magento/module-swat: 100.4.3
magento/module-target-rule: 101.2.5
magento/module-target-rule-graph-ql: 100.4.2
magento/module-versions-cms: 101.2.5
magento/module-versions-cms-page-cache: 100.4.1
magento/module-versions-cms-url-rewrite: 100.4.3
magento/module-versions-cms-url-rewrite-graph-ql: 100.4.1
magento/module-visual-merchandiser: 100.4.5
magento/module-website-restriction: 100.4.4
magento/module-weee-staging: 100.4.2
magento/module-wishlist-gift-card: 100.4.1
magento/module-wishlist-gift-card-graph-ql: 100.4.1
magento/page-builder-commerce: 1.7.2
magento/product-community-edition: 2.4.5
magento/security-package-ee: 1.0.0
magento/theme-adminhtml-spectrum: 100.4.0
magento/zendframework1: ~1.15.0
monolog/monolog: ^2.7
pelago/emogrifier: ^6.0.0
php: ~7.4.0||~8.1.0
php-amqplib/php-amqplib: ~3.2.0
phpseclib/mcrypt_compat: ~2.0.2
phpseclib/phpseclib: ~3.0.13
ramsey/uuid: ~4.2.0
symfony/console: ~4.4.0
symfony/process: ~4.4.0
tedivm/jshrink: ~1.4.0
tubalmartin/cssmin: 4.1.1
web-token/jwt-framework: ^v2.2.7
webonyx/graphql-php: ~14.11.6
wikimedia/less.php: ^3.0.0
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
    <td>PHP 用AWS Common Runtime</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/aws/aws-sdk-php.git">aws/aws-sdk-php</a>
    </td>
    <td>ライブラリ</td>
    <td>PHP 用AWS SDK - PHP プロジェクトでAmazon Web Servicesを使用します。</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree
    </td>
    <td>メタパッケージ</td>
    <td>BraintreeMagento</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/wikimedia/less.php.git">wikimedia/less.php</a>
    </td>
    <td>ライブラリ</td>
    <td>LESS http://lesscss.orgの JavaScript バージョンの PHP ポート（元々 Josh Schmidt が管理）</td>
  </tr>
  </tbody>
</table>

### BSD-2-Clause

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
      <a href="https://github.com/beberlei/assert.git">beberlei/assert</a>
    </td>
    <td>ライブラリ</td>
    <td>ビジネスモデルでの入力検証用のシンアサーションライブラリ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/DASPRiD/Enum.git">dasprid/enum</a>
    </td>
    <td>ライブラリ</td>
    <td>PHP 7.1 enum 実装</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webimpress/safe-writer.git">webimpress/safe-writer</a>
    </td>
    <td>ライブラリ</td>
    <td>競合状態を避けるため、安全にファイルを書き込むツール</td>
  </tr>
  </tbody>
</table>

### BSD-3-Clause

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
    <td>Zend_Cache_Backend_File のバックエンドは、キャッシュされた項目の数が増えるにつれて、タグによるクリーニングのパフォーマンスが非常に低下しています。 このバックエンドでは、多くの変更がおこなわれ、特にタグのクリーニングにおいて、パフォーマンスが大幅に向上します。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_Redis.git">colinmollenhour/cache-backend-redis</a>
    </td>
    <td>magento-module</td>
    <td>Redis を使用する Zend_Cache バックエンドは、タグを完全にサポートします。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/php-redis-session-abstract.git">colinmollenhour/php-redis-session-abstract</a>
    </td>
    <td>ライブラリ</td>
    <td>Redis ベースのセッションハンドラーで、楽観的なロック機能を備えています</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/google/recaptcha.git">google/recaptcha</a>
    </td>
    <td>ライブラリ</td>
    <td>スパムや不正使用から Web サイトを保護する無料のサービス、reCAPTCHA 用のクライアントライブラリ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-captcha.git">ラミナ/ラミナ/カプチャ</a>
    </td>
    <td>ライブラリ</td>
    <td>フィグレット、画像、ReCaptcha などを使用して CAPTCHA を生成および検証します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-code.git">ラミナ/ラミナコード</a>
    </td>
    <td>ライブラリ</td>
    <td>PHP Reflection API、静的コードスキャン、およびコード生成の拡張</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-config.git">laminas/laminas-config</a>
    </td>
    <td>ライブラリ</td>
    <td>は、アプリケーションコード内のこの設定データにアクセスするための、ネストされたオブジェクトプロパティベースのユーザーインターフェイスを提供します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-db.git">laminas/laminas-db</a>
    </td>
    <td>ライブラリ</td>
    <td>データベース抽象レイヤー、SQL の抽象化、結果セットの抽象化、RowDataGateway と TableDataGateway の実装</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-dependency-plugin.git">laminas/laminas-dependency-plugin</a>
    </td>
    <td>composer-plugin</td>
    <td>zendframework および zfcampus パッケージを、Laminas Project に相当するものに置き換えます。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-di.git">ラミナ/ラミナスジ</a>
    </td>
    <td>ライブラリ</td>
    <td>PSR-11 コンテナの自動依存関係挿入</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-escaper.git">ラミナ/ラミナ脱進機</a>
    </td>
    <td>ライブラリ</td>
    <td>HTML、HTML属性、JavaScript、CSS、URL を安全かつ安全にエスケープする</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-eventmanager.git">laminas/laminas-eventmanager</a>
    </td>
    <td>ライブラリ</td>
    <td>PHP アプリケーション内のトリガーとイベントのリッスン</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-feed.git">ラミナ/ラミナフィード</a>
    </td>
    <td>ライブラリ</td>
    <td>は、RSS および Atom フィードを作成および使用する機能を提供します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-http.git">laminas/laminas-http</a>
    </td>
    <td>ライブラリ</td>
    <td>ハイパーテキスト転送プロトコル (HTTP) 要求を実行するための簡単なインターフェイスを提供</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-json.git">laminas/laminas-json</a>
    </td>
    <td>ライブラリ</td>
    <td>は、ネイティブ PHP を JSON にシリアル化し、JSON をネイティブ PHP にデコードする便利な方法を提供します。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-loader.git">ラミナ/ラミナスローダ</a>
    </td>
    <td>ライブラリ</td>
    <td>自動読み込みとプラグインの読み込み戦略</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mail.git">ラミナ/ラミナスメール</a>
    </td>
    <td>ライブラリ</td>
    <td>テキストと MIME 準拠のマルチパート電子メールメッセージの両方を作成および送信する汎用機能を提供</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mime.git">laminas/laminas-mime</a>
    </td>
    <td>ライブラリ</td>
    <td>MIME メッセージと部分の作成と解析</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-modulemanager.git">laminas/laminas-modulemanager</a>
    </td>
    <td>ライブラリ</td>
    <td>ラミナス —mvc アプリケーション用のモジュラーアプリケーションシステム</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mvc.git">ラミナ/ラミナス/mvc</a>
    </td>
    <td>ライブラリ</td>
    <td>MVC アプリケーション、コントローラ、プラグインを含む Laminas のイベント駆動型 MVC レイヤ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-recaptcha.git">laminas/laminas-recaptcha</a>
    </td>
    <td>ライブラリ</td>
    <td>ReCaptcha Web サービス用の OOP ラッパー</td>
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
      <a href="https://github.com/laminas/laminas-server.git">ラミナ/ラミナサーバ</a>
    </td>
    <td>ライブラリ</td>
    <td>Reflection ベースの RPC サーバを作成する</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-servicemanager.git">laminas/laminas-servicemanager</a>
    </td>
    <td>ライブラリ</td>
    <td>工場主導型の依存関係注入コンテナ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-session.git">ラミナ/ラミナセッション</a>
    </td>
    <td>ライブラリ</td>
    <td>PHP セッションとストレージに対するオブジェクト指向のインタフェース</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-soap.git">ラミナ/ラミナス石鹸</a>
    </td>
    <td>ライブラリ</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-stdlib.git">laminas/laminas-stdlib</a>
    </td>
    <td>ライブラリ</td>
    <td>SPL 拡張機能、配列ユーティリティ、エラーハンドラなど</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-text.git">laminas/laminas-text</a>
    </td>
    <td>ライブラリ</td>
    <td>FIGlet とテキストベースのテーブルを作成する</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-uri.git">ラミナス/ラミナス —uri</a>
    </td>
    <td>ライブラリ</td>
    <td>「URI(Uniform Resource Identifier)」の操作と検証を支援するコンポーネント</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-validator.git">laminas/laminas-validator</a>
    </td>
    <td>ライブラリ</td>
    <td>様々なドメインの検証クラス、および複雑な検証基準を作成するためのバリデータを連結する機能</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-view.git">ラミナ/ラミナスビュー</a>
    </td>
    <td>ライブラリ</td>
    <td>複数のビュー画層、ヘルパーなどをサポートし、提供する柔軟なビュー画層</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-zendframework-bridge.git">laminas/laminas-zendframework-bridge</a>
    </td>
    <td>ライブラリ</td>
    <td>従来の ZF クラス名を Laminas Project に相当する名前にエイリアスします。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/nikic/PHP-Parser.git">nikic/php-parser</a>
    </td>
    <td>ライブラリ</td>
    <td>PHP で書かれた PHP パーサー</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tedious/JShrink.git">tedivm/jshrink</a>
    </td>
    <td>ライブラリ</td>
    <td>PHP で構築された JavaScript Minifier</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tubalmartin/YUI-CSS-compressor-PHP-port.git">tubalmartin/cssmin</a>
    </td>
    <td>ライブラリ</td>
    <td>YUI CSS コンプレッサの PHP ポート</td>
  </tr>
  </tbody>
</table>

### LGPL-2.1-or-later

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
      <a href="https://github.com/ezyang/htmlpurifier.git">ezyang/htmlprifier</a>
    </td>
    <td>ライブラリ</td>
    <td>PHP で記述された標準準拠HTMLフィルタ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-amqplib/php-amqplib.git">php-amqplib/php-amqplib</a>
    </td>
    <td>ライブラリ</td>
    <td>以前は videlalvaro/php-amqplib でした。  このライブラリは、AMQP プロトコルの純粋な PHP 実装です。 RabbitMQ に対するテストが実施されています。</td>
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
    <td>BraintreePHP クライアントライブラリ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/math.git">レンガ/数学</a>
    </td>
    <td>ライブラリ</td>
    <td>任意精度の算術ライブラリ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/varexporter.git">brick/varexporter</a>
    </td>
    <td>ライブラリ</td>
    <td>var_export() に代わる強力な代替手段で、__set_state() を使用せずにクロージャやオブジェクトをエクスポートできます。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ChristianRiesen/base32.git">christian-riesen/base32</a>
    </td>
    <td>ライブラリ</td>
    <td>RFC 4648 に従った Base32 エンコーダ/デコーダ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/credis.git">colinmollenhour/credits</a>
    </td>
    <td>ライブラリ</td>
    <td>Credis は、パフォーマンスを向上させるために phpredis ライブラリをラップする Redis キー値ストアへの軽量なインターフェイスです。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/ca-bundle.git">composer/ca-bundle</a>
    </td>
    <td>ライブラリ</td>
    <td>システム CA バンドルへのパスを検索し、Mozilla CA バンドルへのフォールバックを含めます。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/composer.git">composer/composer</a>
    </td>
    <td>ライブラリ</td>
    <td>Composer は、PHP プロジェクトの依存関係を宣言、管理、インストールする際に役立ちます。 これにより、適切なスタックをどこにでも持つことができます。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/metadata-minifier.git">composer/metadata-minifier</a>
    </td>
    <td>ライブラリ</td>
    <td>メタデータの縮小と拡張を処理する小さなユーティリティライブラリ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/pcre.git">composer/pcre</a>
    </td>
    <td>ライブラリ</td>
    <td>タイプセーフ preg_*の置き換えを提供する PCRE ラッピングライブラリ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/semver.git">composer/semver</a>
    </td>
    <td>ライブラリ</td>
    <td>ユーティリティ、バージョン制約の解析および検証を提供する semver ライブラリ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/spdx-licenses.git">composer/spdx-licenses</a>
    </td>
    <td>ライブラリ</td>
    <td>SPDX ライセンスの一覧と検証ライブラリ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/xdebug-handler.git">composer/xdebug-handler</a>
    </td>
    <td>ライブラリ</td>
    <td>Xdebug を使用せずにプロセスを再起動します。</td>
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
    <td>elasticsearch-php で使用する guzzle/streams のフォーク（廃止）</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/ringphp.git">ezimuel/ringphp</a>
    </td>
    <td>ライブラリ</td>
    <td>guzzle/RingPHP （廃止）のフォークは、elasticsearch-php で使用されます。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/fgrosse/PHPASN1.git">fgrosse/phpasn1</a>
    </td>
    <td>ライブラリ</td>
    <td>ITU-T X.690 エンコーディング規則を使用して任意の ASN.1 構造をエンコードおよびデコードできる PHP フレームワーク。</td>
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
    <td>Guzzle promises ライブラリ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/psr7.git">guzzlehttp/psr7</a>
    </td>
    <td>ライブラリ</td>
    <td>一般的なユーティリティメソッドも提供する PSR-7 メッセージ実装</td>
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
    <td>PHP 用のファイルストレージの抽象化</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-aws-s3-v3.git">league/flysystem-aws-s3-v3</a>
    </td>
    <td>ライブラリ</td>
    <td>Flysystem 用AWS S3 ファイルシステムアダプター。</td>
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
      <a href="https://github.com/Seldaek/monolog.git">モノローグ</a>
    </td>
    <td>ライブラリ</td>
    <td>ログをファイル、ソケット、受信ボックス、データベース、および様々な Web サービスに送信します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jmespath/jmespath.php.git">mtdowling/jmespath.php</a>
    </td>
    <td>ライブラリ</td>
    <td>JSON ドキュメントから要素を抽出する方法を宣言的に指定する</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/constant_time_encoding.git">paragonie/constant_time_encoding</a>
    </td>
    <td>ライブラリ</td>
    <td>RFC 4648 エンコーディングの定時実装 (Base-64、Base-32、Base-16)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/random_compat.git">paragonie/random_compat</a>
    </td>
    <td>ライブラリ</td>
    <td>PHP 7 の random_bytes() と random_int() の PHP 5.x のポリフィル</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/emogrifier.git">pelago/emogrifier</a>
    </td>
    <td>ライブラリ</td>
    <td>CSS スタイルをHTMLコード内のインラインスタイル属性に変換</td>
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
    <td>PHP プロジェクト用の最新の DOM API です。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/mcrypt_compat.git">phpseclib/mcrypt_compat</a>
    </td>
    <td>ライブラリ</td>
    <td>mcrypt 拡張の PHP 5.x-8.x polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/phpseclib.git">phpseclib/phpseclib</a>
    </td>
    <td>ライブラリ</td>
    <td>PHP セキュア通信ライブラリ — RSA、AES、SSH2、SFTP、X.509 などの Pure-PHP 実装</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/container.git">psr/container</a>
    </td>
    <td>ライブラリ</td>
    <td>共通コンテナインタフェース (PHP FIG PSR-11)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/event-dispatcher.git">psr/event-dispatcher</a>
    </td>
    <td>ライブラリ</td>
    <td>イベント処理用の標準インターフェイス。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-client.git">psr/http-client</a>
    </td>
    <td>ライブラリ</td>
    <td>HTTP クライアント用の共通インターフェイス</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-factory.git">psr/http-factory</a>
    </td>
    <td>ライブラリ</td>
    <td>PSR-7 HTTP メッセージファクトリ用の共通インターフェイス</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-message.git">psr/http-message</a>
    </td>
    <td>ライブラリ</td>
    <td>HTTP メッセージ用の共通インターフェイス</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/log.git">psr/log</a>
    </td>
    <td>ライブラリ</td>
    <td>ログライブラリ用の共通インターフェイス</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ralouphie/getallheaders.git">ralouphie/getallheaders</a>
    </td>
    <td>ライブラリ</td>
    <td>getallheaders のポリフィルです。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/collection.git">ラムジー/コレクション</a>
    </td>
    <td>ライブラリ</td>
    <td>コレクションを表示および操作するための PHP ライブラリ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/uuid.git">ramsey/uuid</a>
    </td>
    <td>ライブラリ</td>
    <td>UUID(Universally Unique Identifier) を生成し、使用するための PHP ライブラリ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/reactphp/promise.git">react/promise</a>
    </td>
    <td>ライブラリ</td>
    <td>PHP 用の CommonJS Promise/A の軽量実装</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/sabberworm/PHP-CSS-Parser.git">sabberworm/php-css-parser</a>
    </td>
    <td>ライブラリ</td>
    <td>PHP で書き込まれた CSS ファイルのパーサー</td>
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
    <td>PHAR ファイル形式のユーティリティ。PHP が</td>
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
      <a href="https://github.com/Spomky-Labs/base64url.git">spomky-labs/base64url</a>
    </td>
    <td>ライブラリ</td>
    <td>Base 64 URL の安全なエンコード/デコード PHP ライブラリ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/otphp.git">spomky-labs/otphp</a>
    </td>
    <td>ライブラリ</td>
    <td>RFC 4226(HOTP Algorithm) および RFC 6238(TOTP Algorithm) に従って 1 回限りのパスワードを生成し、Google Authenticator と互換性を持つ PHP ライブラリ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/config.git">symfony/config</a>
    </td>
    <td>ライブラリ</td>
    <td>あらゆる種類の設定値を検索、読み込み、組み合わせ、自動入力および検証できます</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/console.git">symfony/console</a>
    </td>
    <td>ライブラリ</td>
    <td>美しくテスト可能なコマンドラインインターフェイスの作成を容易にします。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/css-selector.git">symfony/css-selector</a>
    </td>
    <td>ライブラリ</td>
    <td>CSS セレクターを XPath 式に変換します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/debug.git">symfony/debug</a>
    </td>
    <td>ライブラリ</td>
    <td>PHP コードのデバッグを容易にするツールを提供します。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/dependency-injection.git">symfony/dependency-injection</a>
    </td>
    <td>ライブラリ</td>
    <td>アプリケーションでのオブジェクトの構築方法を標準化および一元化できます。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/deprecation-contracts.git">symfony/deprecation-contracts</a>
    </td>
    <td>ライブラリ</td>
    <td>廃止の通知をトリガーする汎用関数と規則</td>
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
    <td>イベントをディスパッチし、それらをリッスンすることで、アプリケーションコンポーネントが相互に通信できるツールを提供します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher-contracts.git">symfonity/event-dispatcher-contracts</a>
    </td>
    <td>ライブラリ</td>
    <td>イベントのディスパッチに関連する一般的な抽象概念</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/filesystem.git">symfony/filesystem</a>
    </td>
    <td>ライブラリ</td>
    <td>ファイル・システムの基本的なユーティリティを提供</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/finder.git">symfony/finder</a>
    </td>
    <td>ライブラリ</td>
    <td>直感的な流暢なインターフェイスでファイルとディレクトリを検索</td>
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
    <td>HTTP 仕様用のオブジェクト指向レイヤーを定義します。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-kernel.git">symfony/http-kernel</a>
    </td>
    <td>ライブラリ</td>
    <td>リクエストを応答に変換する構造化されたプロセスを提供します。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-ctype.git">symfony/polyfill-ctype</a>
    </td>
    <td>ライブラリ</td>
    <td>ctype 関数の Symfony ポリフィル</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-idn.git">symfony/polyfill-intl-idn</a>
    </td>
    <td>ライブラリ</td>
    <td>intl の idn_to_ascii 関数と idn_to_utf8 関数の Symfony ポリフィル</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-normalizer.git">symfony/polyfill-intl-normalizer</a>
    </td>
    <td>ライブラリ</td>
    <td>intl の Normalizer クラスと関連関数の Symfony ポリフィル</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-mbstring.git">symfony/polyfill-mbstring</a>
    </td>
    <td>ライブラリ</td>
    <td>Mbstring 拡張機能の Symfony ポリフィル</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php72.git">symfony/polyfill-php72</a>
    </td>
    <td>ライブラリ</td>
    <td>Symfony のポリフィルは、PHP 7.2 以降の機能をバックポートし、PHP のバージョンを下げる</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php73.git">symfony/polyfill-php73</a>
    </td>
    <td>ライブラリ</td>
    <td>Symfony のポリフィルは、PHP 7.3 以降の機能をバックポートし、PHP のバージョンを下げる</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php80.git">symfony/polyfill-php80</a>
    </td>
    <td>ライブラリ</td>
    <td>Symfony のポリフィルは、PHP 8.0 以降の機能をバックポートし、PHP のバージョンを下げる</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php81.git">symfony/polyfill-php81</a>
    </td>
    <td>ライブラリ</td>
    <td>Symfony のポリフィルは、PHP 8.1 以降の機能をバックポートし、PHP のバージョンを下げる</td>
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
    <td>書き込みサービスに関連する一般的な抽象概念</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-dumper.git">symfony/var-dumper</a>
    </td>
    <td>ライブラリ</td>
    <td>任意の PHP 変数を介して歩くためのメカニズムを提供します。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thecodingmachine/safe.git">tecodingmachine/safe</a>
    </td>
    <td>ライブラリ</td>
    <td>エラー時に FALSE を返す代わりに例外をスローする PHP のコア関数</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/web-token/jwt-framework.git">web-token/jwt-framework</a>
    </td>
    <td>symfony-bundle</td>
    <td>PHP および Symfony バンドル用の JSON オブジェクト署名および暗号化ライブラリ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webmozarts/assert.git">webmozart/assert</a>
    </td>
    <td>ライブラリ</td>
    <td>メソッドの入出力を検証するアサーションで、優れたエラーメッセージが表示されます。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webonyx/graphql-php.git">webonyx/graphql-php</a>
    </td>
    <td>ライブラリ</td>
    <td>GraphQL 参照実装の PHP ポート</td>
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
      paypal/module-braintree-graph-ql
    </td>
    <td>magento2-module</td>
    <td>該当なし</td>
  </tr>
  <tr>
    <td>
      temando/module-shipping-remover
    </td>
    <td>magento2-module</td>
    <td>Temando のマルチキャリア配送の延長をMagento2 から削除</td>
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
  <tr>
    <td>
      temando/module-shipping
    </td>
    <td>メタパッケージ</td>
    <td>Magento2 の Temando マルチキャリア配送拡張</td>
  </tr>
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
    <td>PHP 用の CBOR エンコーダ</td>
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
  </tbody>
</table>

### 独自の

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
    <td>Gene Commerce for PayPal によるMagentoBraintree2.2.0 モジュールからのフォーク。</td>
  </tr>
  </tbody>
</table>
