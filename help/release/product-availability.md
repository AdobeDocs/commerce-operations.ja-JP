---
title: 製品の可用性
description: 現在サポートされているAdobe Commerceの機能について説明し、特定のAdobe Commerceリリースとの互換性を確認します。
exl-id: 7e8e8ac2-a0b9-4023-a813-c0f1293e54c2
source-git-commit: 9b09cd4d4934735a6fb06e4193dc652d65098f66
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 15%

---

# 製品の可用性

次の表に、Adobe Commerceソフトウェアの可用性のステータスと、その入手先を示します。特に、従来のAdobe Commerce Composer パッケージ以外で使用可能なソフトウェアについては、このステータスを示します。

サービスと拡張機能は、製品リリース時に、最新リリースの Commerce でテストされます。

サポート対象バージョンは、Adobeで完全にテスト済みです。 カスタマーサポートを通じて、サポート対象のバージョンを利用できます。 古いバージョンは正しく機能する可能性がありますが、正式にはサポートされていません。

## Adobeが作成した拡張機能

これらのAdobe Commerce拡張機能は、コアAdobe Commerceコードベースから切り離されます。 これにより、Adobeは、より柔軟な期間でこれらの拡張機能を繰り返しリリースし、新機能に初めてアクセスできるようになります。


次の表に、Adobe Commerceバージョンを基準とした各拡張機能でのバージョンサポートを示します。

| **Adobe Commerceバージョン** | 2.4.7-beta1 | 2.4.6 | 2.4.5 | 2.4.4 | 2.4.3 |                                                                                                                                                                                                                                          |
|----------------------------------------|-------------|--------|--------|--------|--------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| _Adobe CommerceのAdobe I/Oイベント_ | 1.2.2 | 1.2.2 | 1.2.2 | 1.2.2 | - | [コンポーザー](https://developer.adobe.com/commerce/events/get-started/installation/) <br/>[リリースノート](https://developer.adobe.com/commerce/events/get-started/release-notes/) |
| _B2B_ | 1.4.0+ | 1.3.5+ | 1.3.4 | 1.3.3 | 1.3.2 | [コンポーザー](https://experienceleague.adobe.com/docs/commerce-admin/b2b/install.html) <br/> [リリースノート](https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html) |
| _Experience Platformコネクタ_ | 3.0.0-beta1 | 1.0.0+ | 1.0.0+ | 1.0.0+ | 1.0.0+ | [Marketplace](https://commercemarketplace.adobe.com/magento-experience-platform-connector.html)<br/>[リリースノート](https://experienceleague.adobe.com/docs/commerce-merchant-services/experience-platform-connector/release-notes.html) |
| _Page Builder_ | - | - | 1.7.2 | 1.7.1 | - | [ユーザーガイド](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/guide-overview.html)<br/> [リリースノート](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/release-notes.html) |

## コマースサービス

[コマースサービス](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/home.html) は、コマースインスタンスと組み合わせて、堅牢な機能と高速な応答時間を提供する、Adobeでホストされる機能のスイートです。

最高の安定性と機能を確保するために、マーチャントは最新バージョンのサービスを使用することをお勧めします。 ドキュメントでは、現在リリースされているバージョンについて説明します。

* Adobe Commerce Services は、現在、Commerce 2.4.4 以降と互換性があります。 商人には最新バージョンのサービスを使用することをお勧めします。
* サービスは、以前のバージョンの Commerce 2.4.x との互換性があると見なされますが、正式にはサポートされていません。
* サービスは、Product Recommendations 3.3.7 以前を除き、Commerce 2.3.x と互換性がありません。

次の表に、Adobe Commerceバージョンを基準とした各サービスでサポートされるバージョンを示します。

| **Adobe Commerce Versions** | 2.4.7-beta1 | 2.4.6 | 2.4.5 | 2.4.4 | 2.4.3 |                                                                                                                                                                                                                                                |
|--------------------------------------|-------------|--------|--------|--------|--------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| _AmazonSales Channel_ | - | 4.1.0+ | 4.3.0+ | 4.3.0+ | 4.3.0+ | [Marketplace](https://commercemarketplace.adobe.com/magento-module-amazon.html)<br/> [リリースノート](https://experienceleague.adobe.com/docs/commerce-channels/amazon/release-notes.html) |
| _Adobe Commerceのカタログサービス_ | 1.1.2 | 1.1.2 | 1.1.2 | 1.1.2 | - | [概要](https://experienceleague.adobe.com/docs/commerce-merchant-services/catalog-service/guide-overview.html)<br/> [リリースノート](https://experienceleague.adobe.com/docs/commerce-merchant-services/catalog-service/release-notes.html) |
| _チャネルマネージャ_ | - | 2.0.0 | 1.0.0+ | 1.0.0+ | 1.0.0+ | [Marketplace](https://commercemarketplace.adobe.com/magento-channel-manager.html)<br/> [リリースノート](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/release-notes.html) |
| _ライブ検索_ | 3.0.2 | 3.0.2 | 3.0.2 | 3.0.2 | - | [Marketplace](https://commercemarketplace.adobe.com/magento-live-search.html)<br/>[リリースノート](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/release-notes.html) |
| _支払いサービス_ | 2.2.0 | 2.2.0 | 2.2.0 (PHP 8.1) | 2.2.0 (PHP 8.1) | - | [Marketplace](https://commercemarketplace.adobe.com/magento-payment-services.html)<br/> [リリースノート](https://commercemarketplace.adobe.com/magento-payment-services.html) |
| _製品Recommendations_ | 5.0 | 5.0 | 5.0 | 5.0 | - | [Marketplace](https://commercemarketplace.adobe.com/magento-product-recommendations.html)<br/> [リリースノート](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/release-notes.html) |
| _クイックチェックアウト_ | - | 1.0.0+ | 1.2.0+ | 1.0.0+ | 1.2.0+ | [Marketplace](https://commercemarketplace.adobe.com/magento-quick-checkout.html)<br/> [リリースノート](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/release-notes.html) |
| _Adobe Commerce のストアフルフィルメント_ | - | 1.5.0 | 1.2.0+ | 1.2.0+ | 1.2.0+ | [Marketplace](https://commercemarketplace.adobe.com/store-fulfillment-magento-walmart.html)<br/> [リリースノート](https://experienceleague.adobe.com/docs/commerce-merchant-services/store-fulfillment/release-notes.html) |
