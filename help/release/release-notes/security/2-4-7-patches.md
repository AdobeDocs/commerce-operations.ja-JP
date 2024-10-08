---
title: Adobe Commerce 2.4.7 セキュリティパッチのリリースノート
description: Adobe Commerce バージョン 2.4.7 のセキュリティパッチリリースに含まれている、セキュリティバグ修正、セキュリティ機能強化、その他のセキュリティ関連アップデートについて説明します。
exl-id: 38e5632b-c795-47d8-89dd-26bbaeb34e67
source-git-commit: cb4f388c90902c2fe1df4a5d84841280fa740104
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# Adobe Commerce 2.4.7 セキュリティパッチのリリースノート

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## 2.4.7-p3

Adobe Commerce 2.4.7-p3 セキュリティリリースは、2.4.7 の以前のリリースで特定された脆弱性に対するセキュリティバグ修正を提供します。

セキュリティのバグ修正の最新情報については、[Adobeセキュリティ速報 APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html) を参照してください。

{{b2b-patches}}

### ハイライト

{{$include /help/_includes/release-notes/2024-10/security-foo.md}}

### このリリースに含まれるホットフィックス

{{$include /help/_includes/release-notes/2024-10/hotfixes-included-foo.md}}

## 2.4.7-p2

Adobe Commerce 2.4.7-p2 セキュリティリリースは、2.4.7 の以前のリリースで特定された脆弱性に対するセキュリティバグ修正を提供します。

セキュリティのバグ修正の最新情報については、[Adobeセキュリティ速報 APSB24-61](https://helpx.adobe.com/security/products/magento/apsb24-61.html) を参照してください。

### ハイライト

{{$include /help/_includes/release-notes/2024-08/security.md}}

### このリリースに含まれるホットフィックス

{{$include /help/_includes/release-notes/2024-08/hotfixes-included.md}}

## 2.4.7-p1

Adobe Commerce 2.4.7-p1 セキュリティリリースは、以前のリリースの 2.4.7 で特定された脆弱性に対するセキュリティバグ修正を提供します。

セキュリティのバグ修正の最新情報については、[Adobeセキュリティ速報 APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html) を参照してください。

### CVE-2024-34102 のホットフィックスを適用する

{{$include /help/_includes/release-notes/2024-06/hotfixes-not-included.md}}

### ハイライト

このリリースには、次のハイライトが含まれています。

* **Google Authenticator の [ ワンタイムパスワード （OTP）設定の更新 ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google)** – この更新は、[ 後方互換性のない変更 ](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value)2.4.7 で発生したエラーを解決するために必要です。**[!UICONTROL OTP Window]** フィールドの説明で設定の正確な説明が提供されるようになり、デフォルト値は `1` から `29` に変更されました。

* **B2B バージョンの互換性** - Commerce バージョン 2.4.7-p1 との互換性を確保するには、Adobe Commerce B2B 拡張機能を持つマーチャントが、[B2B バージョン 1.4.2-p1](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1) にアップグレードする必要があります。

### このリリースに含まれるホットフィックス

Adobe Commerce 2.4.7-p1 では、SOAPから REST API への UPS 統合の移行の範囲で発生していた問題が修正されました。 この問題は、米国外に出荷するお客様に影響を与え、UPS を使用した出荷を作成するために、パッケージにキログラムとセンチメートルのメートル法/SI 測定を使用することを妨げました。 詳しくは、SOAPから RESTful API への [UPS 発送方法の統合の移行 ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/ups-shipping-method-integration-migration-from-soap-to-restful-api) ナレッジベースの記事を参照してください。
