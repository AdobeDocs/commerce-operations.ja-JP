---
title: Adobe Commerce 2.4.7 セキュリティパッチのリリースノート
description: Adobe Commerce バージョン 2.4.7 のセキュリティパッチリリースに含まれている、セキュリティバグ修正、セキュリティ機能強化、その他のセキュリティ関連アップデートについて説明します。
source-git-commit: 59a5306c8329ddc3ca2a2e086f5ebe81b49eab3a
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 0%

---


# Adobe Commerce 2.4.7 セキュリティパッチのリリースノート

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.7-p1

Adobe Commerce 2.4.7-p1 セキュリティリリースは、以前のリリースの 2.4.7 で特定された脆弱性に対するセキュリティバグ修正を提供します。

セキュリティ バグ修正の最新情報については、を参照してください。 [Adobeセキュリティ速報 APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### セキュリティ ハイライト

このリリースでは、 [ワンタイムパスワード（OTP）設定](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google) （Google Authenticator で） [後方互換性のない変化](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value) （2.4.7 でサポート）。の説明 **[!UICONTROL OTP Window]** フィールドで設定の正確な説明が提供されるようになり、デフォルト値は次のように変更されました `1` 対象： `29`.

### その他のセキュリティ機能強化

{{$include /help/_includes/release-notes/2-4-7-security.md}}

### このリリースに含まれるホットフィックス

Adobe Commerce 2.4.7-p1 では、UPS 統合の SOAP から REST API への移行の範囲で発生していた問題が修正されました。 この問題は、米国外に出荷するお客様に影響を与え、UPS を使用した出荷を作成するために、パッケージにキログラムとセンチメートルのメートル法/SI 測定を使用することを妨げました。 を参照してください。 [SOAP から RESTful API への UPS 出荷メソッド統合の移行](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/ups-shipping-method-integration-migration-from-soap-to-restful-api) ナレッジベース記事を参照してください。
