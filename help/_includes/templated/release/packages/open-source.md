---
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '3444'
ht-degree: 0%

---
# Magento Open Source パッケージ

<!-- The 'packages' variable contains the 'packages' node of the '_data/codebase/open-source/composer_lock.json' file -->

<!-- The 'packages-dev' variable contains the 'packages-dev' node of the '_data/codebase/open-source/composer_lock.json' file -->

<!-- The 'product' variable contains data of the 'magento/product-community-edition' package -->

<!-- The edition variable contains `open-source` value from the _data/names.yml file -->

Magento Open Sourceでは、Composerを使用してPHP パッケージを管理します。

`composer.json` ファイルはパッケージのリストを宣言しますが、`composer.lock` ファイルには、Magento Open Sourceのインストールの構築に使用されたパッケージの完全なリスト（各パッケージとその依存関係の完全なバージョン）が格納されます。

次のリファレンスドキュメントは`composer.lock` ファイルから生成され、Magento Open Source 2.4.8に含まれる必要なパッケージを説明しています。

## 依存関係

`magento/product-community-edition 2.4.8`には次の依存関係があります：

- adobe-commerce/os-extensions-metapackage: 1.0.1
- colinmollenhour/cache-backend-file: ^1.4
- colinmollenhour/cache-backend-redis: ^1.16
- colinmollenhour/credis: ^1.15
- colinmollenhour/php-redis-session-abstract: ^2.0
- コンポーザー/コンポーザー：^2.0、!=2.2.16
- duosecurity/duo_api_php: ^1.1
- duosecurity/duo_universal_php: ^1.0
- elasticsearch/elasticsearch: ^8.15
- ext-bcmath: *
- ext-ctype: *
- ext-curl: *
- ext-dom: *
- ext-ftp: *
- ext-gd: *
- ext-hash: *
- ext-iconv: *
- ext-intl: *
- ext-mbstring: *
- ext-openssl: *
- ext-pdo_mysql: *
- ext-simplexml: *
- ext-soap: *
- ext-sodium: *
- ext-xsl: *
- ext-zip: *
- ezyang/htmlpurifier: ^4.17
- guzzlehttp/guzzle: ^7.5
- laminas/laminas-captcha: ^2.18
- laminas/laminas-code: ^4.13
- laminas/laminas-di: ^3.15
- laminas/laminas-escaper: ^2.13
- laminas/laminas-eventmanager: ^3.11
- laminas/laminas-feed: ^2.22
- laminas/laminas-filter: ^2.33
- laminas/laminas-http: ^2.15
- laminas/laminas-i18n: ^2.17
- laminas/laminas-modulemanager: ^2.11
- laminas/laminas-mvc: ^3.6
- laminas/laminas-permissions-acl: ^2.10
- laminas/laminas-servicemanager: ^3.16
- laminas/laminas-soap: ^2.10
- laminas/laminas-stdlib: ^3.11
- laminas/laminas-uri: ^2.9
- laminas/laminas-validator: ^2.23
- リーグ/フライシステム：^3.0
- league/flysystem-aws-s3-v3: ^3.0
- lib-libxml: *
- magento/composer: ^1.10.1-beta1
- magento/composer-dependency-version-audit-plugin: ^0.1
- magento/framework: 103.0.8
- magento/framework-amqp: 100.4.6
- magento/framework-bulk: 101.0.4
- magento/framework-message-queue: 100.4.8
- magento/inventory-metapackage:1.2.8
- magento/language-de_de: 100.4.0
- magento/language-en_us: 100.4.0
- magento/language-es_es: 100.4.0
- magento/language-fr_fr: 100.4.0
- magento/language-nl_nl: 100.4.0
- magento/language-pt_br: 100.4.0
- magento/language-zh_hans_cn: 100.4.0
- magento/magento-composer-installer: >=0.4.0
- magento/magento-zf-db: ^3.21.0
- magento/magento2-base:2.4.8
- [magento/module-admin-analytics](https://developer.adobe.com/commerce/php/module-reference/module-admin-analytics/): 100.4.7
- [magento/module-admin-notification](https://developer.adobe.com/commerce/php/module-reference/module-admin-notification/): 100.4.7
- [magento/module-advanced-pricing-import-export](https://developer.adobe.com/commerce/php/module-reference/module-advanced-pricing-import-export/): 100.4.8
- [magento/module-advanced-search](https://developer.adobe.com/commerce/php/module-reference/module-advanced-search/): 100.4.6
- [magento/module-amqp](https://developer.adobe.com/commerce/php/module-reference/module-amqp/): 100.4.5
- [magento/module-analytics](https://developer.adobe.com/commerce/php/module-reference/module-analytics/): 100.4.8
- [magento/module-application-performance-monitor](https://developer.adobe.com/commerce/php/module-reference/module-application-performance-monitor/): 100.4.1
- [magento/module-application-performance-monitor-new-relic](https://developer.adobe.com/commerce/php/module-reference/module-application-performance-monitor-new-relic/): 100.4.1
- [magento/module-async-config](https://developer.adobe.com/commerce/php/module-reference/module-async-config/): 100.4.1
- [magento/module-asynchronous-operations](https://developer.adobe.com/commerce/php/module-reference/module-asynchronous-operations/): 100.4.8
- [magento/module-authorization](https://developer.adobe.com/commerce/php/module-reference/module-authorization/): 100.4.8
- [magento/module-aws-s3](https://developer.adobe.com/commerce/php/module-reference/module-aws-s3/): 100.4.6
- [magento/module-backend](https://developer.adobe.com/commerce/php/module-reference/module-backend/): 102.0.8
- [magento/module-backup](https://developer.adobe.com/commerce/php/module-reference/module-backup/): 100.4.8
- [magento/module-bundle](https://developer.adobe.com/commerce/php/module-reference/module-bundle/): 101.0.8
- [magento/module-bundle-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-bundle-graph-ql/): 100.4.8
- [magento/module-bundle-import-export](https://developer.adobe.com/commerce/php/module-reference/module-bundle-import-export/): 100.4.7
- [magento/module-cache-invalidate](https://developer.adobe.com/commerce/php/module-reference/module-cache-invalidate/): 100.4.6
- [magento/module-captcha](https://developer.adobe.com/commerce/php/module-reference/module-captcha/): 100.4.8
- [magento/module-cardinal-commerce](https://developer.adobe.com/commerce/php/module-reference/module-cardinal-commerce/): 100.4.6
- [magento/module-catalog](https://developer.adobe.com/commerce/php/module-reference/module-catalog/): 104.0.8
- [magento/module-catalog-analytics](https://developer.adobe.com/commerce/php/module-reference/module-catalog-analytics/): 100.4.5
- [magento/module-catalog-cms-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-catalog-cms-graph-ql/): 100.4.4
- [magento/module-catalog-customer-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-catalog-customer-graph-ql/): 100.4.7
- [magento/module-catalog-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-catalog-graph-ql/): 100.4.8
- [magento/module-catalog-import-export](https://developer.adobe.com/commerce/php/module-reference/module-catalog-import-export/): 101.1.8
- [magento/module-catalog-inventory](https://developer.adobe.com/commerce/php/module-reference/module-catalog-inventory/): 100.4.8
- [magento/module-catalog-inventory-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-catalog-inventory-graph-ql/): 100.4.5
- [magento/module-catalog-rule](https://developer.adobe.com/commerce/php/module-reference/module-catalog-rule/): 101.2.8
- [magento/module-catalog-rule-configurable](https://developer.adobe.com/commerce/php/module-reference/module-catalog-rule-configurable/): 100.4.7
- [magento/module-catalog-rule-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-catalog-rule-graph-ql/): 100.4.5
- [magento/module-catalog-search](https://developer.adobe.com/commerce/php/module-reference/module-catalog-search/): 102.0.8
- [magento/module-catalog-url-rewrite](https://developer.adobe.com/commerce/php/module-reference/module-catalog-url-rewrite/): 100.4.8
- [magento/module-catalog-url-rewrite-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-catalog-url-rewrite-graph-ql/): 100.4.6
- [magento/module-catalog-widget](https://developer.adobe.com/commerce/php/module-reference/module-catalog-widget/): 100.4.8
- [magento/module-checkout](https://developer.adobe.com/commerce/php/module-reference/module-checkout/): 100.4.8
- [magento/module-checkout-agreements](https://developer.adobe.com/commerce/php/module-reference/module-checkout-agreements/): 100.4.7
- [magento/module-checkout-agreements-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-checkout-agreements-graph-ql/): 100.4.4
- [magento/module-cms](https://developer.adobe.com/commerce/php/module-reference/module-cms/): 104.0.8
- [magento/module-cms-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-cms-graph-ql/): 100.4.5
- [magento/module-cms-url-rewrite](https://developer.adobe.com/commerce/php/module-reference/module-cms-url-rewrite/): 100.4.7
- [magento/module-cms-url-rewrite-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-cms-url-rewrite-graph-ql/): 100.4.6
- [magento/module-compare-list-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-compare-list-graph-ql/): 100.4.4
- [magento/module-config](https://developer.adobe.com/commerce/php/module-reference/module-config/): 101.2.8
- [magento/module-configurable-import-export](https://developer.adobe.com/commerce/php/module-reference/module-configurable-import-export/): 100.4.6
- [magento/module-configurable-product](https://developer.adobe.com/commerce/php/module-reference/module-configurable-product/): 100.4.8
- [magento/module-configurable-product-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-configurable-product-graph-ql/): 100.4.8
- [magento/module-configurable-product-sales](https://developer.adobe.com/commerce/php/module-reference/module-configurable-product-sales/): 100.4.5
- [magento/module-contact](https://developer.adobe.com/commerce/php/module-reference/module-contact/): 100.4.7
- [magento/module-contact-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-contact-graph-ql/): 100.4.1
- [magento/module-cookie](https://developer.adobe.com/commerce/php/module-reference/module-cookie/): 100.4.8
- [magento/module-cron](https://developer.adobe.com/commerce/php/module-reference/module-cron/): 100.4.8
- [magento/module-csp](https://developer.adobe.com/commerce/php/module-reference/module-csp/): 100.4.7
- [magento/module-currency-symbol](https://developer.adobe.com/commerce/php/module-reference/module-currency-symbol/): 100.4.6
- [magento/module-customer](https://developer.adobe.com/commerce/php/module-reference/module-customer/): 103.0.8
- [magento/module-customer-analytics](https://developer.adobe.com/commerce/php/module-reference/module-customer-analytics/): 100.4.5
- [magento/module-customer-downloadable-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-customer-downloadable-graph-ql/): 100.4.4
- [magento/module-customer-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-customer-graph-ql/): 100.4.8
- [magento/module-customer-import-export](https://developer.adobe.com/commerce/php/module-reference/module-customer-import-export/): 100.4.8
- [magento/module-deploy](https://developer.adobe.com/commerce/php/module-reference/module-deploy/): 100.4.8
- [magento/module-developer](https://developer.adobe.com/commerce/php/module-reference/module-developer/): 100.4.8
- [magento/module-dhl](https://developer.adobe.com/commerce/php/module-reference/module-dhl/): 100.4.7
- [magento/module-directory](https://developer.adobe.com/commerce/php/module-reference/module-directory/): 100.4.8
- [magento/module-directory-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-directory-graph-ql/): 100.4.6
- [magento/module-downloadable](https://developer.adobe.com/commerce/php/module-reference/module-downloadable/): 100.4.8
- [magento/module-downloadable-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-downloadable-graph-ql/): 100.4.8
- [magento/module-downloadable-import-export](https://developer.adobe.com/commerce/php/module-reference/module-downloadable-import-export/): 100.4.7
- [magento/module-eav](https://developer.adobe.com/commerce/php/module-reference/module-eav/): 102.1.8
- [magento/module-eav-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-eav-graph-ql/): 100.4.5
- [magento/module-elasticsearch](https://developer.adobe.com/commerce/php/module-reference/module-elasticsearch/): 101.0.8
- [magento/module-elasticsearch-8](https://developer.adobe.com/commerce/php/module-reference/module-elasticsearch-8/): 101.0.0
- [magento/module-email](https://developer.adobe.com/commerce/php/module-reference/module-email/): 101.1.8
- [magento/module-encryption-key](https://developer.adobe.com/commerce/php/module-reference/module-encryption-key/): 100.4.6
- [magento/module-fedex](https://developer.adobe.com/commerce/php/module-reference/module-fedex/): 100.4.6
- [magento/module-gift-message](https://developer.adobe.com/commerce/php/module-reference/module-gift-message/): 100.4.7
- [magento/module-gift-message-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-gift-message-graph-ql/): 100.4.6
- [magento/module-google-adwords](https://developer.adobe.com/commerce/php/module-reference/module-google-adwords/): 100.4.5
- [magento/module-google-analytics](https://developer.adobe.com/commerce/php/module-reference/module-google-analytics/): 100.4.4
- [magento/module-google-gtag](https://developer.adobe.com/commerce/php/module-reference/module-google-gtag/): 100.4.3
- [magento/module-google-optimizer](https://developer.adobe.com/commerce/php/module-reference/module-google-optimizer/): 100.4.7
- [magento/module-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-graph-ql/): 100.4.8
- [magento/module-graph-ql-cache](https://developer.adobe.com/commerce/php/module-reference/module-graph-ql-cache/): 100.4.5
- [magento/module-graph-ql-new-relic](https://developer.adobe.com/commerce/php/module-reference/module-graph-ql-new-relic/): 100.4.1
- [magento/module-graph-ql-resolver-cache](https://developer.adobe.com/commerce/php/module-reference/module-graph-ql-resolver-cache/): 100.4.1
- [magento/module-grouped-catalog-inventory](https://developer.adobe.com/commerce/php/module-reference/module-grouped-catalog-inventory/): 100.4.5
- [magento/module-grouped-import-export](https://developer.adobe.com/commerce/php/module-reference/module-grouped-import-export/): 100.4.6
- [magento/module-grouped-product](https://developer.adobe.com/commerce/php/module-reference/module-grouped-product/): 100.4.8
- [magento/module-grouped-product-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-grouped-product-graph-ql/): 100.4.8
- [magento/module-import-export](https://developer.adobe.com/commerce/php/module-reference/module-import-export/): 101.0.8
- [magento/module-indexer](https://developer.adobe.com/commerce/php/module-reference/module-indexer/): 100.4.8
- [magento/module-instant-purchase](https://developer.adobe.com/commerce/php/module-reference/module-instant-purchase/): 100.4.7
- [magento/module-integration](https://developer.adobe.com/commerce/php/module-reference/module-integration/): 100.4.8
- [magento/module-integration-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-integration-graph-ql/): 100.4.1
- [magento/module-jwt-framework-adapter](https://developer.adobe.com/commerce/php/module-reference/module-jwt-framework-adapter/): 100.4.4
- [magento/module-jwt-user-token](https://developer.adobe.com/commerce/php/module-reference/module-jwt-user-token/): 100.4.3
- [magento/module-layered-navigation](https://developer.adobe.com/commerce/php/module-reference/module-layered-navigation/): 100.4.8
- [magento/module-login-as-customer](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer/): 100.4.8
- [magento/module-login-as-customer-admin-ui](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-admin-ui/): 100.4.8
- [magento/module-login-as-customer-api](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-api/): 100.4.7
- [magento/module-login-as-customer-assistance](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-assistance/): 100.4.7
- [magento/module-login-as-customer-frontend-ui](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-frontend-ui/): 100.4.7
- [magento/module-login-as-customer-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-graph-ql/): 100.4.5
- [magento/module-login-as-customer-log](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-log/): 100.4.6
- [magento/module-login-as-customer-page-cache](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-page-cache/): 100.4.7
- [magento/module-login-as-customer-quote](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-quote/): 100.4.6
- [magento/module-login-as-customer-sales](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-sales/): 100.4.7
- [magento/module-marketplace](https://developer.adobe.com/commerce/php/module-reference/module-marketplace/): 100.4.6
- [magento/module-media-content](https://developer.adobe.com/commerce/php/module-reference/module-media-content/): 100.4.6
- [magento/module-media-content-api](https://developer.adobe.com/commerce/php/module-reference/module-media-content-api/): 100.4.7
- [magento/module-media-content-catalog](https://developer.adobe.com/commerce/php/module-reference/module-media-content-catalog/): 100.4.6
- [magento/module-media-content-cms](https://developer.adobe.com/commerce/php/module-reference/module-media-content-cms/): 100.4.6
- [magento/module-media-content-synchronization](https://developer.adobe.com/commerce/php/module-reference/module-media-content-synchronization/): 100.4.7
- [magento/module-media-content-synchronization-api](https://developer.adobe.com/commerce/php/module-reference/module-media-content-synchronization-api/): 100.4.6
- [magento/module-media-content-synchronization-catalog](https://developer.adobe.com/commerce/php/module-reference/module-media-content-synchronization-catalog/): 100.4.5
- [magento/module-media-content-synchronization-cms](https://developer.adobe.com/commerce/php/module-reference/module-media-content-synchronization-cms/): 100.4.5
- [magento/module-media-gallery](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery/): 100.4.7
- [magento/module-media-gallery-api](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-api/): 101.0.7
- [magento/module-media-gallery-catalog](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-catalog/): 100.4.5
- [magento/module-media-gallery-catalog-integration](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-catalog-integration/): 100.4.5
- [magento/module-media-gallery-catalog-ui](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-catalog-ui/): 100.4.5
- [magento/module-media-gallery-cms-ui](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-cms-ui/): 100.4.5
- [magento/module-media-gallery-integration](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-integration/): 100.4.7
- [magento/module-media-gallery-metadata](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-metadata/): 100.4.6
- [magento/module-media-gallery-metadata-api](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-metadata-api/): 100.4.5
- [magento/module-media-gallery-renditions](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-renditions/): 100.4.6
- [magento/module-media-gallery-renditions-api](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-renditions-api/): 100.4.5
- [magento/module-media-gallery-synchronization](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-synchronization/): 100.4.7
- [magento/module-media-gallery-synchronization-api](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-synchronization-api/): 100.4.6
- [magento/module-media-gallery-synchronization-metadata](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-synchronization-metadata/): 100.4.4
- [magento/module-media-gallery-ui](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-ui/): 100.4.7
- [magento/module-media-gallery-ui-api](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-ui-api/): 100.4.6
- [magento/module-media-storage](https://developer.adobe.com/commerce/php/module-reference/module-media-storage/): 100.4.7
- [magento/module-message-queue](https://developer.adobe.com/commerce/php/module-reference/module-message-queue/): 100.4.8
- [magento/module-msrp](https://developer.adobe.com/commerce/php/module-reference/module-msrp/): 100.4.7
- [magento/module-msrp-configurable-product](https://developer.adobe.com/commerce/php/module-reference/module-msrp-configurable-product/): 100.4.5
- [magento/module-msrp-grouped-product](https://developer.adobe.com/commerce/php/module-reference/module-msrp-grouped-product/): 100.4.5
- [magento/module-multishipping](https://developer.adobe.com/commerce/php/module-reference/module-multishipping/): 100.4.8
- [magento/module-mysql-mq](https://developer.adobe.com/commerce/php/module-reference/module-mysql-mq/): 100.4.6
- [magento/module-new-relic-reporting](https://developer.adobe.com/commerce/php/module-reference/module-new-relic-reporting/): 100.4.6
- [magento/module-newsletter](https://developer.adobe.com/commerce/php/module-reference/module-newsletter/): 100.4.8
- [magento/module-newsletter-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-newsletter-graph-ql/): 100.4.5
- [magento/module-offline-payments](https://developer.adobe.com/commerce/php/module-reference/module-offline-payments/): 100.4.6
- [magento/module-offline-shipping](https://developer.adobe.com/commerce/php/module-reference/module-offline-shipping/): 100.4.7
- [magento/module-open-search](https://developer.adobe.com/commerce/php/module-reference/module-open-search/): 100.4.2
- [magento/module-order-cancel](https://developer.adobe.com/commerce/php/module-reference/module-order-cancellation/): 100.4.1
- [magento/module-order-cancelation-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-order-cancellation-graph-ql/): 100.4.1
- [magento/module-order-cancel-ui](https://developer.adobe.com/commerce/php/module-reference/module-order-cancellation-ui/): 100.4.1
- [magento/module-page-cache](https://developer.adobe.com/commerce/php/module-reference/module-page-cache/): 100.4.8
- [magento/module-payment](https://developer.adobe.com/commerce/php/module-reference/module-payment/): 100.4.8
- [magento/module-payment-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-payment-graph-ql/): 100.4.3
- [magento/module-paypal](https://developer.adobe.com/commerce/php/module-reference/module-paypal/): 101.0.8
- [magento/module-paypal-captcha](https://developer.adobe.com/commerce/php/module-reference/module-paypal-captcha/): 100.4.5
- [magento/module-paypal-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-paypal-graph-ql/): 100.4.6
- [magento/module-persistent](https://developer.adobe.com/commerce/php/module-reference/module-persistent/): 100.4.8
- [magento/module-product-alert](https://developer.adobe.com/commerce/php/module-reference/module-product-alert/): 100.4.7
- [magento/module-product-video](https://developer.adobe.com/commerce/php/module-reference/module-product-video/): 100.4.8
- [magento/module-quote](https://developer.adobe.com/commerce/php/module-reference/module-quote/): 101.2.8
- [magento/module-quote-analytics](https://developer.adobe.com/commerce/php/module-reference/module-quote-analytics/): 100.4.7
- [magento/module-quote-bundle-options](https://developer.adobe.com/commerce/php/module-reference/module-quote-bundle-options/): 100.4.4
- [magento/module-quote-configurable-options](https://developer.adobe.com/commerce/php/module-reference/module-quote-configurable-options/): 100.4.4
- [magento/module-quote-downloadable-links](https://developer.adobe.com/commerce/php/module-reference/module-quote-downloadable-links/): 100.4.4
- [magento/module-quote-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-quote-graph-ql/): 100.4.8
- [magento/module-related-product-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-related-product-graph-ql/): 100.4.5
- [magento/module-release-notification](https://developer.adobe.com/commerce/php/module-reference/module-release-notification/): 100.4.6
- [magento/module-remote-storage](https://developer.adobe.com/commerce/php/module-reference/module-remote-storage/): 100.4.6
- [magento/module-reports](https://developer.adobe.com/commerce/php/module-reference/module-reports/): 100.4.8
- [magento/module-require-js](https://developer.adobe.com/commerce/php/module-reference/module-require-js/): 100.4.4
- [magento/module-review](https://developer.adobe.com/commerce/php/module-reference/module-review/): 100.4.8
- [magento/module-review-analytics](https://developer.adobe.com/commerce/php/module-reference/module-review-analytics/): 100.4.5
- [magento/module-review-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-review-graph-ql/): 100.4.4
- [magento/module-robots](https://developer.adobe.com/commerce/php/module-reference/module-robots/): 101.1.4
- [magento/module-rss](https://developer.adobe.com/commerce/php/module-reference/module-rss/): 100.4.6
- [magento/module-rule](https://developer.adobe.com/commerce/php/module-reference/module-rule/): 100.4.7
- [magento/module-sales](https://developer.adobe.com/commerce/php/module-reference/module-sales/): 103.0.8
- [magento/module-sales-analytics](https://developer.adobe.com/commerce/php/module-reference/module-sales-analytics/): 100.4.5
- [magento/module-sales-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-sales-graph-ql/): 100.4.8
- [magento/module-sales-inventory](https://developer.adobe.com/commerce/php/module-reference/module-sales-inventory/): 100.4.5
- [magento/module-sales-rule](https://developer.adobe.com/commerce/php/module-reference/module-sales-rule/): 101.2.8
- [magento/module-sales-rule-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-sales-rule-graph-ql/): 100.4.1
- [magento/module-sales-sequence](https://developer.adobe.com/commerce/php/module-reference/module-sales-sequence/): 100.4.5
- [magento/module-sample-data](https://developer.adobe.com/commerce/php/module-reference/module-sample-data/): 100.4.6
- [magento/module-search](https://developer.adobe.com/commerce/php/module-reference/module-search/): 101.1.8
- [magento/module-security](https://developer.adobe.com/commerce/php/module-reference/module-security/): 100.4.8
- [magento/module-send-friend](https://developer.adobe.com/commerce/php/module-reference/module-send-friend/): 100.4.6
- [magento/module-send-friend-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-send-friend-graph-ql/): 100.4.4
- [magento/module-shipping](https://developer.adobe.com/commerce/php/module-reference/module-shipping/): 100.4.8
- [magento/module-sitemap](https://developer.adobe.com/commerce/php/module-reference/module-sitemap/): 100.4.7
- [magento/module-store](https://developer.adobe.com/commerce/php/module-reference/module-store/): 101.1.8
- [magento/module-store-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-store-graph-ql/): 100.4.6
- [magento/module-swagger](https://developer.adobe.com/commerce/php/module-reference/module-swagger/): 100.4.7
- [magento/module-swagger-webapi](https://developer.adobe.com/commerce/php/module-reference/module-swagger-webapi/): 100.4.4
- [magento/module-swagger-webapi-async](https://developer.adobe.com/commerce/php/module-reference/module-swagger-webapi-async/): 100.4.4
- [magento/module-swatches](https://developer.adobe.com/commerce/php/module-reference/module-swatches/): 100.4.8
- [magento/module-swatches-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-swatches-graph-ql/): 100.4.6
- [magento/module-swatches-layered-navigation](https://developer.adobe.com/commerce/php/module-reference/module-swatches-layered-navigation/): 100.4.4
- [magento/module-tax](https://developer.adobe.com/commerce/php/module-reference/module-tax/): 100.4.8
- [magento/module-tax-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-tax-graph-ql/): 100.4.4
- [magento/module-tax-import-export](https://developer.adobe.com/commerce/php/module-reference/module-tax-import-export/): 100.4.7
- [magento/module-theme](https://developer.adobe.com/commerce/php/module-reference/module-theme/): 101.1.8
- [magento/module-theme-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-theme-graph-ql/): 100.4.5
- [magento/module-translation](https://developer.adobe.com/commerce/php/module-reference/module-translation/): 100.4.8
- [magento/module-ui](https://developer.adobe.com/commerce/php/module-reference/module-ui/): 101.2.8
- [magento/module-ups](https://developer.adobe.com/commerce/php/module-reference/module-ups/): 100.4.8
- [magento/module-url-rewrite](https://developer.adobe.com/commerce/php/module-reference/module-url-rewrite/): 102.0.7
- [magento/module-url-rewrite-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-url-rewrite-graph-ql/): 100.4.7
- [magento/module-user](https://developer.adobe.com/commerce/php/module-reference/module-user/): 101.2.8
- [magento/module-usps](https://developer.adobe.com/commerce/php/module-reference/module-usps/): 100.4.7
- [magento/module-variable](https://developer.adobe.com/commerce/php/module-reference/module-variable/): 100.4.6
- [magento/module-vault](https://developer.adobe.com/commerce/php/module-reference/module-vault/): 101.2.8
- [magento/module-vault-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-vault-graph-ql/): 100.4.4
- [magento/module-version](https://developer.adobe.com/commerce/php/module-reference/module-version/): 100.4.5
- [magento/module-webapi](https://developer.adobe.com/commerce/php/module-reference/module-webapi/): 100.4.7
- [magento/module-webapi-async](https://developer.adobe.com/commerce/php/module-reference/module-webapi-async/): 100.4.6
- [magento/module-webapi-security](https://developer.adobe.com/commerce/php/module-reference/module-webapi-security/): 100.4.5
- [magento/module-weee](https://developer.adobe.com/commerce/php/module-reference/module-weee/): 100.4.8
- [magento/module-weee-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-weee-graph-ql/): 100.4.5
- [magento/module-widget](https://developer.adobe.com/commerce/php/module-reference/module-widget/): 101.2.8
- [magento/module-wishlist](https://developer.adobe.com/commerce/php/module-reference/module-wishlist/): 101.2.8
- [magento/module-wishlist-analytics](https://developer.adobe.com/commerce/php/module-reference/module-wishlist-analytics/): 100.4.6
- [magento/module-wishlist-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-wishlist-graph-ql/): 100.4.8
- magento/page-builder:1.7.5
- magento/security-package: 1.1.7
- magento/theme-adminhtml-backend: 100.4.8
- magento/theme-frontend-blank: 100.4.8
- magento/theme-frontend-luma: 100.4.8
- magento/zend-cache: ^1.16
- magento/zend-db: ^1.16
- magento/zend-pdf: ^1.16
- monolog/monolog: ^3.6
- opensearch-project/opensearch-php: ^2.3
- pelago/emogrifier: ^7.0
- php: ～8.2.0||～8.3.0||～8.4.0
- php-amqplib/php-amqplib: ^3.2
- phpseclib/mcrypt_compat: ^2.0
- phpseclib/phpseclib: ^3.0
- psr/log: ^2 || ^3
- ramsey/uuid: ^4.2
- symfony/console: ^6.4
- symfony/intl: ^6.4
- symfony/mailer: ^6.4
- symfony/mime: ^6.4
- symfony/process: ^6.4
- symfony/string: ^6.4
- tedivm/jshrink: ^1.4
- tubalmartin/cssmin: ^4.1
- web-token/jwt-framework: ^3.4
- webonyx/graphql-php: ^15.0
- wikimedia/less.php: ^5.0

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
      <a href="https://github.com/opensearch-project/opensearch-php">opensearch-project/opensearch-php</a>
    </td>
    <td>Library</td>
    <td>OpenSearch用PHP クライアント</td>
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
      <a href="https://github.com/adobe/stock-api-libphp">astock/stock-api-libphp</a>
    </td>
    <td>Library</td>
    <td>Adobe Stock API ライブラリ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/awslabs/aws-crt-php">aws/aws-crt-php</a>
    </td>
    <td>Library</td>
    <td>PHP用AWS Common Runtime</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/aws/aws-sdk-php">aws/aws-sdk-php</a>
    </td>
    <td>Library</td>
    <td>PHP用AWS SDK - PHP プロジェクトでのAmazon Web Servicesの使用</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/opentelemetry-php/api">open-telemetry/api</a>
    </td>
    <td>Library</td>
    <td>OpenTelemetry PHP用のAPI。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/opentelemetry-php/context">open-telemetry/context</a>
    </td>
    <td>Library</td>
    <td>OpenTelemetry PHPのコンテキスト実装。</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree
    </td>
    <td>メタパッケージ</td>
    <td>Braintree Magento</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/wikimedia/less.php">wikimedia/less.php</a>
    </td>
    <td>Library</td>
    <td>LESS プロセッサーのPHP ポート</td>
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
      <a href="https://github.com/Bacon/BaconQrCode">bacon/bacon-qr-code</a>
    </td>
    <td>Library</td>
    <td>BaconQrCodeは、PHP用のQR コードジェネレーターです。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/DASPRiD/Enum">dasprid/enum</a>
    </td>
    <td>Library</td>
    <td>PHP 7.1 enumの実装</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webimpress/safe-writer">webimpress/safe-writer</a>
    </td>
    <td>Library</td>
    <td>レース条件を避けるために、安全にファイルを書き込むためのツール</td>
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
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_File">colinmollenhour/cache-backend-file</a>
    </td>
    <td>Magento-module</td>
    <td>在庫のZend_Cache_Backend_File バックエンドは、タグによるクリーニングのパフォーマンスが非常に低いため、キャッシュされたアイテム数が増えると使用できなくなります。 このバックエンドでは、多くの変更が行われ、特にタグクリーニングの場合、パフォーマンスが大幅に向上します。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/php-redis-session-abstract">colinmollenhour/php-redis-session-abstract</a>
    </td>
    <td>Library</td>
    <td>楽観的ロックを備えたRedis ベースのセッションハンドラー</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/duosecurity/duo_universal_php">duosecurity/duo_universal_php</a>
    </td>
    <td>Library</td>
    <td>Duo Universal SDKのPHP実装。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/firebase/php-jwt">firebase/php-jwt</a>
    </td>
    <td>Library</td>
    <td>PHPでJSON Web Tokens （JWT）をエンコードおよびデコードするためのシンプルなライブラリ。 現在の仕様に準拠する必要があります。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-captcha">laminas/laminas-captcha</a>
    </td>
    <td>Library</td>
    <td>フィレット、画像、ReCaptchaなどを使用してCAPTCHAを生成し、検証します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-code">laminas/laminas-code</a>
    </td>
    <td>Library</td>
    <td>PHP Reflection API、静的コードスキャン、コード生成の拡張機能</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-config">laminas/laminas-config</a>
    </td>
    <td>Library</td>
    <td>アプリケーション コード内でこの設定データにアクセスするための、ネストされたオブジェクト プロパティ ベースのユーザーインターフェイスを提供します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-di">laminas/laminas-di</a>
    </td>
    <td>Library</td>
    <td>PSR-11 コンテナの依存関係の自動挿入</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-escaper">laminas/laminas-escaper</a>
    </td>
    <td>Library</td>
    <td>HTML、HTMLの属性、JavaScript、CSS、URLを安全にエスケープできます</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-eventmanager">laminas/laminas-eventmanager</a>
    </td>
    <td>Library</td>
    <td>PHP アプリケーション内のイベントのトリガーとリッスン</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-feed">laminas/laminas-feed</a>
    </td>
    <td>Library</td>
    <td>は、RSSおよびAtom フィードを作成および使用するための機能を提供します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-filter">laminas/laminas-filter</a>
    </td>
    <td>Library</td>
    <td>データとファイルをプログラムでフィルタリングおよび正規化する</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-http">laminas/laminas-http</a>
    </td>
    <td>Library</td>
    <td>HTTP （Hyper-Text Transfer Protocol）リクエストを実行するための簡単なインターフェイスを提供</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-i18n">laminas/laminas-i18n</a>
    </td>
    <td>Library</td>
    <td>アプリケーションの翻訳を提供し、国際化された値をフィルタリングおよび検証します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-json">laminas/laminas-json</a>
    </td>
    <td>Library</td>
    <td>ネイティブ PHPをJSONにシリアル化し、JSONをネイティブ PHPにデコードするための便利なメソッドを提供します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-loader">laminas/laminas-loader</a>
    </td>
    <td>Library</td>
    <td>自動ロードとプラグインのロード戦略</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-modulemanager">laminas/laminas-modulemanager</a>
    </td>
    <td>Library</td>
    <td>laminas-mvc アプリケーション向けモジュラーアプリケーションシステム</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mvc">laminas/laminas-mvc</a>
    </td>
    <td>Library</td>
    <td>MVC アプリケーション、コントローラ、プラグインを含むLaminasのイベント駆動型MVC レイヤー</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-permissions-acl">laminas/laminas-permissions-acl</a>
    </td>
    <td>Library</td>
    <td>権限管理のための軽量で柔軟なアクセス制御リスト（ACL）実装を提供</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-recaptcha">laminas/laminas-recaptcha</a>
    </td>
    <td>Library</td>
    <td>ReCaptcha web サービスのOOP ラッパー</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-router">laminas/laminas-router</a>
    </td>
    <td>Library</td>
    <td>HTTPおよびコンソールアプリケーション向けの柔軟なルーティングシステム</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-server">laminas/laminas-server</a>
    </td>
    <td>Library</td>
    <td>リフレクションベースのRPC サーバーの作成</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-servicemanager">laminas/laminas-servicemanager</a>
    </td>
    <td>Library</td>
    <td>工場駆動依存性注入コンテナ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-session">laminas/laminas-session</a>
    </td>
    <td>Library</td>
    <td>PHP セッションとストレージへのオブジェクト指向インターフェイス</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-soap">laminas/laminas-soap</a>
    </td>
    <td>Library</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-stdlib">laminas/laminas-stdlib</a>
    </td>
    <td>Library</td>
    <td>SPL拡張機能、配列ユーティリティ、エラーハンドラーなど</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-text">laminas/laminas-text</a>
    </td>
    <td>Library</td>
    <td>FIGletとテキストベースのテーブルの作成</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-translator">laminas/laminas-translator</a>
    </td>
    <td>Library</td>
    <td>laminas-i18nのTranslator コンポーネントのインターフェイス</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-uri">laminas/laminas-uri</a>
    </td>
    <td>Library</td>
    <td>» Uniform Resource Identifiers （URI）の操作と検証を支援するコンポーネント</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-validator">laminas/laminas-validator</a>
    </td>
    <td>Library</td>
    <td>幅広いドメインの検証クラスと、複雑な検証条件を作成するチェーンバリデータの機能</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-view">laminas/laminas-view</a>
    </td>
    <td>Library</td>
    <td>複数のビューレイヤー、ヘルパーなどをサポートする柔軟なビューレイヤー</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/marc-mabe/php-enum">marc-mabe/php-enum</a>
    </td>
    <td>Library</td>
    <td>ネイティブ PHPによる列挙のシンプルかつ迅速な実装</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/nikic/PHP-Parser">nikic/php-parser</a>
    </td>
    <td>Library</td>
    <td>PHPで書かれたPHP パーサー</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpfui/recaptcha">phpfui/recaptcha</a>
    </td>
    <td>Library</td>
    <td>PHP 8.4以降のreCAPTCHA Google用クライアントライブラリ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tedious/JShrink">tedivm/jshrink</a>
    </td>
    <td>Library</td>
    <td>PHPで構築されたJavascript ミニファイア</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tubalmartin/YUI-CSS-compressor-PHP-port">tubalmartin/cssmin</a>
    </td>
    <td>Library</td>
    <td>YUI CSS コンプレッサーのPHP ポート</td>
  </tr>
  </tbody>
</table>

### BSD-3-Clause-Modification

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
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_Redis">colinmollenhour/cache-backend-redis</a>
    </td>
    <td>Magento-module</td>
    <td>タグを完全にサポートするRedisを使用したZend_Cache バックエンド。</td>
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
      <a href="https://github.com/paragonie/sodium_compat"> パラゴニー/ナトリウム_コンパット </a>
    </td>
    <td>Library</td>
    <td>libsodiumの純粋なPHP実装。存在する場合はPHP拡張機能を使用します。</td>
  </tr>
  </tbody>
</table>

### LGPL-2.1以降

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
      <a href="https://github.com/ezyang/htmlpurifier">ezyang/htmlpurifier</a>
    </td>
    <td>Library</td>
    <td>PHPで記述された標準準拠のHTML フィルター</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-amqplib/php-amqplib">php-amqplib/php-amqplib</a>
    </td>
    <td>Library</td>
    <td>以前はvidelalvaro/php-amqplibでした。  このライブラリは、AMQP プロトコルの純粋なPHP実装です。 RabbitMQに対してテストされています。</td>
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
      <a href="https://github.com/braintree/braintree_php">braintree/braintree_php</a>
    </td>
    <td>Library</td>
    <td>Braintree PHP クライアントライブラリ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/math"> レンガ/計算</a>
    </td>
    <td>Library</td>
    <td>任意精度演算ライブラリ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/varexporter">brick/varexporter</a>
    </td>
    <td>Library</td>
    <td>var_export （）に代わる強力な方法。__set_state （）なしでクロージャやオブジェクトを書き出すことができます。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ChristianRiesen/base32">christian-riesen/base32</a>
    </td>
    <td>Library</td>
    <td>RFC 4648に準拠したBase32 エンコーダ/デコーダ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/credis">colinmollenhour/credis</a>
    </td>
    <td>Library</td>
    <td>Credisは、Redis キー値ストアの軽量インターフェイスで、パフォーマンスを向上させるために利用可能な場合にphpredis ライブラリをラップします。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/ca-bundle"> コンポーザー/ca バンドル </a>
    </td>
    <td>Library</td>
    <td>システム CA バンドルへのパスを見つけることができ、Mozilla CA バンドルへのフォールバックが含まれます。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/class-map-generator">composer/class-map-generator</a>
    </td>
    <td>Library</td>
    <td>PHP コードをスキャンしてクラスマップを生成するユーティリティ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/composer"> コンポーザー/コンポーザー</a>
    </td>
    <td>Library</td>
    <td>Composerは、PHP プロジェクトの依存関係を宣言、管理、インストールするのに役立ちます。 これにより、あらゆる場所に適切なスタックを構築できます。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/metadata-minifier">composer/metadata-minifier</a>
    </td>
    <td>Library</td>
    <td>メタデータの縮小と拡張を扱う小規模なユーティリティライブラリ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/pcre"> コンポーザー/pcre</a>
    </td>
    <td>Library</td>
    <td>タイプ セーフのpreg_*置換を提供するPCRE ラッピングライブラリ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/semver"> コンポーザー/サーバー</a>
    </td>
    <td>Library</td>
    <td>ユーティリティ、バージョン制約の解析および検証を提供するSemver ライブラリ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/spdx-licenses"> コンポーザー/spdx-licenses</a>
    </td>
    <td>Library</td>
    <td>SPDX ライセンスのリストと検証ライブラリ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/xdebug-handler">composer/xdebug-handler</a>
    </td>
    <td>Library</td>
    <td>Xdebugを使用せずにプロセスを再起動します。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/doctrine/lexer">doctrine/lexer</a>
    </td>
    <td>Library</td>
    <td>トップダウン、再帰的な降順パーサーで使用できるPHP Doctrine Lexer パーサーライブラリ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/egulias/EmailValidator">egulias/email-validator</a>
    </td>
    <td>Library</td>
    <td>複数のRFCに対して電子メールを検証するためのライブラリ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/elastic/elastic-transport-php">弾性/輸送</a>
    </td>
    <td>Library</td>
    <td>Elastic製品用のHTTP トランスポート PHP ライブラリ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/elastic/elasticsearch-php">elasticsearch/elasticsearch</a>
    </td>
    <td>Library</td>
    <td>ELASTICSEARCH用PHP クライアント</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/endroid/qr-code">endroid/qr-code</a>
    </td>
    <td>Library</td>
    <td>Endroid QR コード</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/guzzlestreams">ezimuel/guzzlestreams</a>
    </td>
    <td>Library</td>
    <td>elasticsearch-phpで使用するguzzle/streams （abandoned）のフォーク</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/ringphp">ezimuel/ringphp</a>
    </td>
    <td>Library</td>
    <td>elasticsearch-phpで使用するguzzle/RingPHPのフォーク（放棄）</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/guzzle">guzzlehttp/guzzle</a>
    </td>
    <td>Library</td>
    <td>GuzzleはPHP HTTP クライアントライブラリです</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/promises">guzzlehttp/promises</a>
    </td>
    <td>Library</td>
    <td>ガズル・プロミス・ライブラリー</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/psr7">guzzlehttp/psr7</a>
    </td>
    <td>Library</td>
    <td>PSR-7 メッセージの実装。共通のユーティリティメソッドも提供</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jsonrainbow/json-schema">justinrainbow/json-schema</a>
    </td>
    <td>Library</td>
    <td>Json スキーマを検証するライブラリ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem"> リーグ/フライシステム </a>
    </td>
    <td>Library</td>
    <td>PHPのファイルストレージの抽象化</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-aws-s3-v3">league/flysystem-aws-s3-v3</a>
    </td>
    <td>Library</td>
    <td>Flysystem用AWS S3 ファイルシステムアダプタ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-local">league/flysystem-local</a>
    </td>
    <td>Library</td>
    <td>Flysystem用のローカル・ファイルシステム・アダプタ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/mime-type-detection">league/mime-type-detection</a>
    </td>
    <td>Library</td>
    <td>FlysystemのMime タイプ検出</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/monolog">monolog/monolog</a>
    </td>
    <td>Library</td>
    <td>ログをファイル、ソケット、受信トレイ、データベース、各種web サービスに送信します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jmespath/jmespath.php">mtdowling/jmespath.php</a>
    </td>
    <td>Library</td>
    <td>JSON ドキュメントから要素を抽出する方法を宣言的に指定します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/constant_time_encoding">paragonie/constant_time_encoding</a>
    </td>
    <td>Library</td>
    <td>RFC 4648 エンコーディングの定時実装（Base-64、Base-32、Base-16）</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/random_compat">paragonie/random_compat</a>
    </td>
    <td>Library</td>
    <td>PHP 5.x polyfill for random_bytes （） and random_int （） from PHP 7</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/emogrifier">pelago/emogrifier</a>
    </td>
    <td>Library</td>
    <td>HTML コードでCSS スタイルをインラインスタイル属性に変換します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/discovery">php-http/discovery</a>
    </td>
    <td>Composer-plugin</td>
    <td>PSR-7、PSR-17、PSR-18およびHTTPlug実装を検索してインストールします</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/httplug">php-http/httplug</a>
    </td>
    <td>Library</td>
    <td>HTTPlug:PHP用のHTTP クライアント抽象化</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/promise">php-http/promise</a>
    </td>
    <td>Library</td>
    <td>非同期HTTP リクエストに使用されるPromise</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/CssXPath">phpgt/cssxpath</a>
    </td>
    <td>Library</td>
    <td>CSS セレクターをXPath クエリに変換します。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/Dom">phpgt/dom</a>
    </td>
    <td>Library</td>
    <td>最新のDOM API:</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/PropFunc">phpgt/propfunc</a>
    </td>
    <td>Library</td>
    <td>プロパティアクセサー関数とミューテーター関数。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/mcrypt_compat">phpseclib/mcrypt_compat</a>
    </td>
    <td>Library</td>
    <td>mcrypt拡張機能のためのPHP 5.x-8.x polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/phpseclib">phpseclib/phpseclib</a>
    </td>
    <td>Library</td>
    <td>PHP Secure Communications Library - RSA、AES、SSH2、SFTP、X.509などの純粋なPHP実装。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/cache">psr/cache</a>
    </td>
    <td>Library</td>
    <td>ライブラリをキャッシュするための共通インターフェイス</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/clock">psr/clock</a>
    </td>
    <td>Library</td>
    <td>時計を読むための一般的なインターフェイス。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/container">psr/container</a>
    </td>
    <td>Library</td>
    <td>共通コンテナインターフェイス（PHP FIG PSR-11）</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/event-dispatcher">psr/event-dispatcher</a>
    </td>
    <td>Library</td>
    <td>イベント処理用の標準インターフェイス。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-client">psr/http-client</a>
    </td>
    <td>Library</td>
    <td>HTTP クライアント用の共通インターフェイス</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-factory">psr/http-factory</a>
    </td>
    <td>Library</td>
    <td>PSR-17: PSR-7 HTTP メッセージ ファクトリの共通インターフェイス</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-message">psr/http-message</a>
    </td>
    <td>Library</td>
    <td>HTTP メッセージの共通インターフェイス</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/log">psr/log</a>
    </td>
    <td>Library</td>
    <td>ライブラリをログ記録するための共通インターフェイス</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ralouphie/getallheaders">ralouphie/getallheaders</a>
    </td>
    <td>Library</td>
    <td>getallheaders用のpolyfill。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/collection"> ラムジー/コレクション </a>
    </td>
    <td>Library</td>
    <td>コレクションを表現および操作するためのPHP ライブラリ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/uuid"> ラムジー/uuid</a>
    </td>
    <td>Library</td>
    <td>ユニバーサル固有識別子（UUID）を生成して使用するためのPHP ライブラリ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/reactphp/promise">react/promise</a>
    </td>
    <td>Library</td>
    <td>CommonJS Promises/A for PHPの軽量な実装</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/PHP-CSS-Parser">sabberworm/php-css-parser</a>
    </td>
    <td>Library</td>
    <td>PHPで書かれたCSS ファイルのパーサー</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/jsonlint">seld/jsonlint</a>
    </td>
    <td>Library</td>
    <td>JSON Linter</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/phar-utils">seld/phar-utils</a>
    </td>
    <td>Library</td>
    <td>PHAR ファイル形式ユーティリティ（PHPが起動したときに使用）</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/signal-handler">seld/signal-handler</a>
    </td>
    <td>Library</td>
    <td>簡単なクロスプラットフォーム開発のために、シグナルがサポートされていない場合にサイレントで失敗するシンプルなunix シグナルハンドラー</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/aes-key-wrap">spomky-labs/aes-key-wrap</a>
    </td>
    <td>Library</td>
    <td>AES Key Wrap for PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/otphp">spomky-labs/otphp</a>
    </td>
    <td>Library</td>
    <td>RFC 4226 （HOTP アルゴリズム）およびRFC 6238 （TOTP アルゴリズム）に準拠し、Google Authenticatorと互換性のある1回限りのパスワードを生成するためのPHP ライブラリ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/pki-framework">spomky-labs/pki-framework</a>
    </td>
    <td>Library</td>
    <td>公開鍵インフラストラクチャを管理するためのPHP フレームワーク。 これは、X.509公開鍵証明書、属性証明書、証明要求、および証明書パス検証で構成されます。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/config">symfony/config</a>
    </td>
    <td>Library</td>
    <td>あらゆる種類の設定値を検索、読み込み、結合、自動入力、検証できます</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/console">symfony/console</a>
    </td>
    <td>Library</td>
    <td>美しくテスト可能なコマンドラインインターフェイスの作成を容易にする</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/css-selector">symfony/css-selector</a>
    </td>
    <td>Library</td>
    <td>CSS セレクターをXPath式に変換します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/dependency-injection">symfony/dependency-injection</a>
    </td>
    <td>Library</td>
    <td>アプリケーションでのオブジェクトの構築方法を標準化および一元化できます</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/deprecation-contracts">symfony/deprecation-contracts</a>
    </td>
    <td>Library</td>
    <td>トリガーの非推奨化に関する一般的な関数と規則</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/error-handler">symfony/error-handler</a>
    </td>
    <td>Library</td>
    <td>エラーを管理し、PHP コードのデバッグを容易にするツールを提供します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher">symfony/event-dispatcher</a>
    </td>
    <td>Library</td>
    <td>イベントをディスパッチしてリッスンすることで、アプリケーションコンポーネントが互いに通信できるようにするツールを提供します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher-contracts">symfony/event-dispatcher-contracts</a>
    </td>
    <td>Library</td>
    <td>イベントのディスパッチに関連する一般的な抽象化</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/filesystem">symfony/filesystem</a>
    </td>
    <td>Library</td>
    <td>ファイルシステムの基本的なユーティリティを提供します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/finder">symfony/finder</a>
    </td>
    <td>Library</td>
    <td>直感的な流暢なインターフェイスを介してファイルとディレクトリを検索します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client">symfony/http-client</a>
    </td>
    <td>Library</td>
    <td>HTTP リソースを同期または非同期で取得するための強力なメソッドを提供します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client-contracts">symfony/http-client-contracts</a>
    </td>
    <td>Library</td>
    <td>HTTP クライアントに関連する汎用的な抽象化</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-foundation">symfony/http-foundation</a>
    </td>
    <td>Library</td>
    <td>HTTP仕様のオブジェクト指向レイヤーを定義します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-kernel">symfony/http-kernel</a>
    </td>
    <td>Library</td>
    <td>リクエストをレスポンスに変換するための構造化プロセスを提供します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/intl">symfony/intl</a>
    </td>
    <td>Library</td>
    <td>ICU ライブラリのローカライゼーションデータへのアクセスを提供</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/mailer">symfony/mailer</a>
    </td>
    <td>Library</td>
    <td>メール送信を支援</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/mime">symfony/mime</a>
    </td>
    <td>Library</td>
    <td>MIME メッセージの操作を許可します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-ctype">symfony/polyfill-ctype</a>
    </td>
    <td>Library</td>
    <td>Ctype関数のSymfony polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-grapheme">symfony/polyfill-intl-grapheme</a>
    </td>
    <td>Library</td>
    <td>インテルのgrapheme_*関数のためのSymfony polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-idn">symfony/polyfill-intl-idn</a>
    </td>
    <td>Library</td>
    <td>インテルのidn_to_ascii関数およびidn_to_utf8関数のSymfony polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-normalizer">symfony/polyfill-intl-normalizer</a>
    </td>
    <td>Library</td>
    <td>InlのNormalizer クラスおよび関連関数のSymfony polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-mbstring">symfony/polyfill-mbstring</a>
    </td>
    <td>Library</td>
    <td>Mbstring拡張機能のSymfony polyfill</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php73">symfony/polyfill-php73</a>
    </td>
    <td>Library</td>
    <td>Symfony polyfill backporting some PHP 7.3+ features to lower PHP versions</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php80">symfony/polyfill-php80</a>
    </td>
    <td>Library</td>
    <td>Symfony polyfill backporting some PHP 8.0+ features to lower PHP versions</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php81">symfony/polyfill-php81</a>
    </td>
    <td>Library</td>
    <td>Symfony polyfill backporting some PHP 8.1+ features to lower PHP versions</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php82">symfony/polyfill-php82</a>
    </td>
    <td>Library</td>
    <td>Symfony polyfill backporting some PHP 8.2+ features to lower PHP versions</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php83">symfony/polyfill-php83</a>
    </td>
    <td>Library</td>
    <td>Symfony polyfill backporting some PHP 8.3+ features to lower PHP versions</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/process">symfony/process</a>
    </td>
    <td>Library</td>
    <td>サブプロセス内でコマンドを実行</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/service-contracts">symfony/service-contracts</a>
    </td>
    <td>Library</td>
    <td>ライティングサービスに関連する一般的な抽象化</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/string">symfony/string</a>
    </td>
    <td>Library</td>
    <td>文字列にオブジェクト指向APIを提供し、バイト、UTF-8 コードポイント、およびgrapheme クラスターを統一された方法で処理します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-dumper">symfony/var-dumper</a>
    </td>
    <td>Library</td>
    <td>任意のPHP変数を実行するためのメカニズムを提供します</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-exporter">symfony/var-exporter</a>
    </td>
    <td>Library</td>
    <td>シリアル化可能なPHP データ構造をプレーン PHP コードに書き出すことができます</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/yaml">symfony/yaml</a>
    </td>
    <td>Library</td>
    <td>YAML ファイルの読み込みとダンプ</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/web-token/jwt-framework">web-token/jwt-framework</a>
    </td>
    <td>Symfony-bundle</td>
    <td>PHPおよびSymfony バンドル用のJSON オブジェクト署名および暗号化ライブラリ。</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webonyx/graphql-php">webonyx/graphql-php</a>
    </td>
    <td>Library</td>
    <td>GraphQL参照実装のPHP ポート</td>
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
    <td>Magento2-module</td>
    <td>該当なし</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-gift-card
    </td>
    <td>Magento2-module</td>
    <td>該当なし</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-gift-card-account
    </td>
    <td>Magento2-module</td>
    <td>該当なし</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-gift-wrapping
    </td>
    <td>Magento2-module</td>
    <td>該当なし</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-graph-ql
    </td>
    <td>Magento2-module</td>
    <td>該当なし</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-reward
    </td>
    <td>Magento2-module</td>
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
      <a href="https://github.com/2tvenom/CBOREncode">2tvenom/cborencode</a>
    </td>
    <td>Library</td>
    <td>PHP用CBOR エンコーダー</td>
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
    <td>Magento2-module</td>
    <td>Gene Commerce for PayPalによるMagento Braintree 2.2.0 モジュールからのフォーク。</td>
  </tr>
  </tbody>
</table>
