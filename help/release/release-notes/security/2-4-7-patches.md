---
title: Adobe Commerce 2.4.7 セキュリティパッチリリースノート
description: Adobe Commerce バージョン 2.4.7のセキュリティパッチリリースに含まれているセキュリティバグの修正、セキュリティの強化、およびその他のセキュリティ関連アップデートについて説明します。
exl-id: 38e5632b-c795-47d8-89dd-26bbaeb34e67
source-git-commit: 2657c83d5467e603a681521886e80592e3b335aa
workflow-type: tm+mt
source-wordcount: '954'
ht-degree: 0%

---


# Adobe Commerce 2.4.7 セキュリティパッチのリリースノート

{{$include /help/_includes/release-notes/security-patch-intro.md}}

>[!IMPORTANT]
>
>MySQL 8.0は、2026年4月30日からサポート終了（EOS）に到達します。
>
>この日付に続いて、Adobe Commerce 2.4.7では互換性が提供されません。または
>mysql 8.0以降にリリースされたMySQL バージョンをサポートします。Adobeでは
>このAdobeの新しいMySQL メジャーバージョンの検証またはサポートの提供
>Commerce リリースライン。
>
>バージョン 2.4.7を実行しているすべてのAdobe Commerce オンプレミスのお客様は、以下の点に強く同意します。
>データベースサーバーを互換性のあるMariaDB バージョンに移行することをお勧めします。

## 2.4.7-p9

Adobe Commerce 2.4.7-p9 セキュリティリリースには、以前のリリース 2.4.7で特定された脆弱性に対するセキュリティバグ修正が含まれています。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB26-05](https://helpx.adobe.com/security/products/magento/apsb26-05.html)を参照してください。

{{b2b-patches}}

### ハイライト

このリリースには、次のハイライトが含まれています。

#### DHL配送の統合のためのMyDHL REST API サポート

DHL出荷統合では、既存のDHL Express XML統合に加えて、MyDHL REST APIがサポートされるようになりました。 このアップデートはDHLの現在のAPI スタックに合っており、古いXML APIの廃止に備えています。

#### 最新バージョンのComposerとの互換性の追加

Adobe Commerce 2.4.7が更新され、Composer 2.9.xがサポートされるようになりました。ただし、Composer 2.2 LTSとの互換性は維持されます。

## 2.4.7-p8

Adobe Commerce 2.4.7-p8 セキュリティリリースには、以前のリリース 2.4.7で特定された脆弱性に対するセキュリティバグの修正が含まれています。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB25-94](https://helpx.adobe.com/security/products/magento/apsb25-94.html)を参照してください。

{{b2b-patches}}

このリリースには、次のハイライトが含まれています。

{{$include /help/_includes/release-notes/highlights/security-2025-10.md}}

{{oct-2025-backports}}

### 既知の問題

#### チェックアウトページでstatic.min.jsとmixins.min.jsの読み込みに失敗する

{{checkout-page-fails-to-load-static-min-js-and-mixins-min-js}}

## 2.4.7-p7

Adobe Commerce 2.4.7-p7 セキュリティリリースには、以前のリリース 2.4.7で特定された脆弱性に対するセキュリティバグの修正が含まれています。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB25-71](https://helpx.adobe.com/security/products/magento/apsb25-71.html)を参照してください。

{{b2b-patches}}

## 2.4.7-p6

Adobe Commerce 2.4.7-p6 セキュリティリリースには、以前のリリース 2.4.7で特定された脆弱性に対するセキュリティバグの修正が含まれています。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB25-50](https://helpx.adobe.com/security/products/magento/apsb25-50.html)を参照してください。

{{b2b-patches}}

### ハイライト

このリリースには、次のハイライトが含まれています。

* **MariaDB サポート** - MariaDB 10.11のサポートを追加しました。

* **API パフォーマンスの向上** – 以前のセキュリティ パッチの後に導入された一括非同期web API エンドポイントのパフォーマンス低下を解決します。<!-- AC-14078 -->

* **CMS ブロック アクセス修正** – 制限された権限（マーチャンダイジング専用アクセスなど）を持つ管理者ユーザーが[!UICONTROL CMS Blocks]の一覧ページを表示できなかった問題を解決します。

  以前は、以前のセキュリティ パッチをインストールした後、構成パラメーターが欠落しているため、これらのユーザーでエラーが発生していました。<!-- AC-14087 -->

* **Cookie制限の互換性** - フレームワークの`MAX_NUM_COOKIES`定数に関する後方互換性のない変更を解決します。 この更新プログラムは、期待される動作を復元し、cookieの制限と相互作用する拡張機能またはカスタマイズの互換性を確保します。<!-- AC-14475 -->

* **非同期操作** – 以前の顧客の注文を上書きするための非同期操作が制限されています。<!-- AC-13917 -->

## 2.4.7-p5

Adobe Commerce 2.4.7-p5 セキュリティリリースには、以前のリリース 2.4.7で特定された脆弱性に対するセキュリティバグの修正が含まれています。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB25-26](https://helpx.adobe.com/security/products/magento/apsb25-26.html)を参照してください。

{{b2b-patches}}

### ハイライト

{{$include /help/_includes/release-notes/highlights/security-2025-04.md}}

>[!BEGINSHADEBOX]

このリリースでは、Adobe Commerce [HIPAA対応拡張機能](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/hipaa-ready-service/overview)のサポートも導入されています。

>[!ENDSHADEBOX]

### 既知の問題

**問題**: 2.4.7-p5をPHP 8.2以降でインストールする場合、システムは`paypal/module-braintree` バージョン 4.7.0をインストールします。これは、2.4.8以降を対象としています。 PHP 8.1では、正しいBraintree バージョン 4.6.1-p5が使用されます。 この不一致は、メタパッケージの`adobe-commerce/extensions-metapackage: ~2.0`への依存関係が緩いことが原因です。 これは、PHP 8.2以降のデプロイメントの互換性とサポートされている機能セットに影響します。<!-- ACPLTSRV-6276) -->

また、バージョン 2.4.7-p3、2.4.7-p4、および2.4.7-p5では、Braintree拡張機能バージョン 4.6.1-p5がインストールされる場合がありますが、一部のユーザーは、以前より厳格な依存関係が緩和され、リリースライン内で拡張機能をアップグレードできるようになったため、4.6.1-p3またはp4がインストールされることを期待しています。<!-- AC-14430 -->

**回避策**: PHPのバージョンに合った適切なBraintree バージョンを使用するには、`composer update`を実行して、`adobe-commerce/extensions-metapackage:2.0.0`依存関係に従って適切なバージョンをインストールします。

## 2.4.7-p4

Adobe Commerce 2.4.7-p4 セキュリティリリースには、以前のリリース 2.4.7で特定された脆弱性に対するセキュリティバグ修正が含まれています。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB25-08](https://helpx.adobe.com/security/products/magento/apsb25-08.html)を参照してください。

{{b2b-patches}}

### ハイライト

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.7-p3

Adobe Commerce 2.4.7-p3 セキュリティリリースには、以前のリリース 2.4.7で特定された脆弱性に対するセキュリティバグの修正が含まれています。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html)を参照してください。

{{b2b-patches}}

### ハイライト

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

### このリリースに含まれるホットフィックス

{{$include /help/_includes/release-notes/hotfixes/included-2024-10.md}}

## 2.4.7-p2

Adobe Commerce 2.4.7-p2のセキュリティリリースには、以前のリリースの2.4.7で特定された脆弱性に対するセキュリティバグ修正が含まれています。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB24-61](https://helpx.adobe.com/security/products/magento/apsb24-61.html)を参照してください。

### ハイライト

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### このリリースに含まれるホットフィックス

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.7-p1

Adobe Commerce 2.4.7-p1 セキュリティリリースでは、以前のリリースの2.4.7で特定された脆弱性に対するセキュリティバグ修正が提供されています。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html)を参照してください。

### CVE-2024-34102のホットフィックスを適用する

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

### ハイライト

このリリースには、次のハイライトが含まれています。

* **Google Authenticator[の](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google) ワンタイムパスワード（OTP）設定**&#x200B;を更新します。この更新は、2.4.7の[後方互換性のない変更](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value)によって発生したエラーを解決するために必要です。**[!UICONTROL OTP Window]** フィールドの説明で、設定の正確な説明が得られるようになり、デフォルト値が`1`から`29`に変更されました。

* **B2B バージョンの互換性** - Commerce バージョン 2.4.7-p1との互換性を保つために、Adobe Commerce B2B拡張機能を持つマーチャントは、[B2B バージョン 1.4.2-p1](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1)にアップグレードする必要があります。

### このリリースに含まれるホットフィックス

Adobe Commerce 2.4.7-p1は、SOAPからREST APIへのUPS統合の移行範囲で発生した問題を解決します。 この問題は、米国外に出荷するお客様に影響を及ぼし、UPSで出荷を作成するパッケージに対してメトリックシステム/SI測定（kgとcm）を使用できないようにしました。 詳しくは、[UPS shipping method integration migration from SOAP to RESTful API](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/ups-shipping-method-integration-migration-from-soap-to-restful-api)のナレッジベース記事を参照してください。

<!-- Last updated from includes: 2026-03-19 11:29:47 -->
