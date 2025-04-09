---
title: Adobe Systems Commerce 2.4.7 セキュリティパッチリリースノート
description: Adobe Systems Commerce バージョン 2.4.7 のセキュリティパッチリリースに含まれるセキュリティバグの修正、セキュリティ拡張機能、およびその他のセキュリティ関連の更新について説明します。
exl-id: 38e5632b-c795-47d8-89dd-26bbaeb34e67
source-git-commit: 9bf1c539220d70a8e7fe449e4d91199f23cc23b2
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# Adobe Systems Commerce 2.4.7 セキュリティパッチのリリースノート

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.7-p5

The Adobe Commerce 2.4.7-p5 security release provides security bug fixes for vulnerabilities identified in previous releases of 2.4.7.

セキュリティのバグ修正の最新情報については、[Adobe セキュリティ速報 APSB25-26](https://helpx.adobe.com/security/products/magento/apsb25-26.html) を参照してください。

{{b2b-patches}}

### ハイライト

このリリースでは、Adobe Systems Commerce [HIPAA 対応拡張機能](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/hipaa-ready-service/overview)のサポートが導入されています。

## 2.4.7-p4

Adobe Systems Commerce 2.4.7-p4 セキュリティリリースでは、以前のリリースの 2.4.7 で特定された脆弱性に対するセキュリティバグの修正が提供されています。

セキュリティバグの修正に関する最新情報については、 [Adobe Systems セキュリティ情報 APSB25-08](https://helpx.adobe.com/security/products/magento/apsb25-08.html) を参照してください。

{{b2b-patches}}

### ハイライト

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.7-p3

Adobe Systems Commerce 2.4.7-p3 セキュリティリリースでは、以前のリリースの 2.4.7 で特定された脆弱性に対するセキュリティバグ修正が提供されています。

セキュリティのバグ修正の最新情報については、[Adobe セキュリティ速報 APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html) を参照してください。

{{b2b-patches}}

### ハイライト

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

### このリリースに含まれるホットフィックス

{{$include /help/_includes/release-notes/hotfixes/included-2024-10.md}}

## 2.4.7-p2

Adobe Systems Commerce 2.4.7-p2 セキュリティリリースでは、以前のリリースの 2.4.7 で特定された脆弱性に対するセキュリティバグ修正が提供されています。

セキュリティバグの修正に関する最新情報については、 [Adobe Systems セキュリティ情報 APSB24-61](https://helpx.adobe.com/security/products/magento/apsb24-61.html) を参照してください。

### ハイライト

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### このリリースに含まれるホットフィックス

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.7-p1

Adobe Systems Commerce 2.4.7-p1 セキュリティリリースでは、以前のリリースの 2.4.7 で特定された脆弱性に対するセキュリティバグ修正が提供されています。

セキュリティのバグ修正の最新情報については、[Adobe セキュリティ速報 APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html) を参照してください。

### CVE-2024-34102 のホットフィックスを適用する

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

### ハイライト

This release includes the following highlights:

* **Google 認証システムの [ワンタイムパスワード(OTP)設定](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google) を更新する** - この更新は、2.4.7 の [後方互換性のない変更](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value) によって発生したエラーを解決するために必要です。 **[!UICONTROL OTP Window]** フィールドの説明で設定の正確な説明が提供され、デフォルト値が `1` から `29` に変更されました。

* **B2Bバージョンの互換性** - Commerce バージョン 2.4.7-p1 との互換性のために、Adobe Systems Commerce B2B 拡張機能を持つマーチャントは [B2B バージョン 1.4.2-p1](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1) にアップグレードする必要があります。

### このリリースに含まれるホットフィックス

Adobe Systems Commerce 2.4.7-p1 は、SOAP から REST API への UPS 統合の移行の範囲で発生した問題を解決します。 この問題は、米国外に出荷するお客様に影響を及ぼし、UPSで出荷を作成するためにパッケージにキログラムとセンチメートルのメートル法/ SI測定値を使用できなくなりました。 詳細については、SOAP から RESTful API への [UPS 配送方法統合の移行](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/ups-shipping-method-integration-migration-from-soap-to-restful-api) ナレッジベース記事を参照してください。
