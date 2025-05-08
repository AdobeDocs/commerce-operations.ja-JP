---
title: Adobe Commerce 2.4.7 セキュリティパッチのリリースノート
description: Adobe Commerce バージョン 2.4.7 のセキュリティパッチリリースに含まれている、セキュリティバグ修正、セキュリティ機能強化、その他のセキュリティ関連アップデートについて説明します。
exl-id: 38e5632b-c795-47d8-89dd-26bbaeb34e67
source-git-commit: 55bba84f05042667d0de3aa053e9a52119bd2599
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---

# Adobe Commerce 2.4.7 セキュリティパッチのリリースノート

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.7-p5

Adobe Commerce 2.4.7-p5 セキュリティリリースは、2.4.7 の以前のリリースで特定された脆弱性に対するセキュリティバグ修正を提供します。

セキュリティのバグ修正の最新情報については、[Adobe セキュリティ速報 APSB25-26](https://helpx.adobe.com/security/products/magento/apsb25-26.html) を参照してください。

{{b2b-patches}}

### ハイライト

{{$include /help/_includes/release-notes/highlights/security-2025-04.md}}

>[!BEGINSHADEBOX]

このリリースでは、Adobe Commerce[HIPAA 対応の拡張機能 ](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/hipaa-ready-service/overview) のサポートも導入されています。

>[!ENDSHADEBOX]

### 既知の問題

**問題**:2.4.7-p5 を PHP 8.2 以降と共にインストールする場合、システムは 2.4.8 以降を対象 `paypal/module-braintree` したバージョン 4.7.0 をインストールします。 PHP 8.1 では、正しいBraintreeのバージョン 4.6.1-p5 が使用されます。 この不一致は、メタパッケージの `adobe-commerce/extensions-metapackage: ~2.0` への依存が緩いために発生します。 これは、PHP 8.2 以降のデプロイメントの互換性およびサポートされる機能セットに影響します。<!-- ACPLTSRV-6276) -->

また、バージョン 2.4.7-p3、2.4.7-p4、2.4.7-p5 では、Braintree拡張機能バージョン 4.6.1-p5 がインストールされる場合がありますが、以前は厳格な依存関係が緩和されてリリースライン内での拡張機能のアップグレードが可能であったことから、一部のユーザーは 4.6.1-p3 または p4 を想定しています。<!-- AC-14430 -->

**回避策**：使用している PHP バージョンに適したBraintreeのバージョンが存在することを確認するには、`composer update` を実行して、`adobe-commerce/extensions-metapackage:2.0.0` の依存関係に従って適切なバージョンをインストールします。

## 2.4.7-p4

Adobe Commerce 2.4.7-p4 セキュリティリリースは、2.4.7 の以前のリリースで特定された脆弱性に対するセキュリティバグ修正を提供します。

セキュリティのバグ修正の最新情報については、[Adobe セキュリティ速報 APSB25-08](https://helpx.adobe.com/security/products/magento/apsb25-08.html) を参照してください。

{{b2b-patches}}

### ハイライト

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.7-p3

Adobe Commerce 2.4.7-p3 セキュリティリリースは、2.4.7 の以前のリリースで特定された脆弱性に対するセキュリティバグ修正を提供します。

セキュリティのバグ修正の最新情報については、[Adobe セキュリティ速報 APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html) を参照してください。

{{b2b-patches}}

### ハイライト

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

### このリリースに含まれるホットフィックス

{{$include /help/_includes/release-notes/hotfixes/included-2024-10.md}}

## 2.4.7-p2

Adobe Commerce 2.4.7-p2 セキュリティリリースは、2.4.7 の以前のリリースで特定された脆弱性に対するセキュリティバグ修正を提供します。

セキュリティのバグ修正の最新情報については、[Adobe セキュリティ速報 APSB24-61](https://helpx.adobe.com/security/products/magento/apsb24-61.html) を参照してください。

### ハイライト

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### このリリースに含まれるホットフィックス

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.7-p1

Adobe Commerce 2.4.7-p1 セキュリティリリースは、以前のリリースの 2.4.7 で特定された脆弱性に対するセキュリティバグ修正を提供します。

セキュリティのバグ修正の最新情報については、[Adobe セキュリティ速報 APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html) を参照してください。

### CVE-2024-34102 のホットフィックスを適用する

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

### ハイライト

このリリースには、次のハイライトが含まれています。

* **Google Authenticator の [ ワンタイムパスワード （OTP）設定の更新 ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google)** – この更新は、[ 後方互換性のない変更 ](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value)2.4.7 で発生したエラーを解決するために必要です。**[!UICONTROL OTP Window]** フィールドの説明で設定の正確な説明が提供されるようになり、デフォルト値は `1` から `29` に変更されました。

* **B2B バージョンの互換性** - Commerce バージョン 2.4.7-p1 との互換性を確保するには、Adobe Commerce B2B 拡張機能を持つマーチャントが、[B2B バージョン 1.4.2-p1](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1) にアップグレードする必要があります。

### このリリースに含まれるホットフィックス

Adobe Commerce 2.4.7-p1 では、SOAPから REST API への UPS 統合の移行の範囲で発生していた問題が修正されました。 この問題は、米国外に出荷するお客様に影響を与え、UPS を使用した出荷を作成するために、パッケージにキログラムとセンチメートルのメートル法/SI 測定を使用することを妨げました。 詳しくは、[UPS 配送方法の統合によるSOAPから RESTful API への移行 ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/ups-shipping-method-integration-migration-from-soap-to-restful-api) ナレッジベースの記事を参照してください。
