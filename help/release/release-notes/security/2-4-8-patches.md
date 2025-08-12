---
title: Adobe Commerce 2.4.8 セキュリティパッチのリリースノート
description: Adobe Commerce バージョン 2.4.7 のセキュリティパッチリリースに含まれている、セキュリティバグ修正、セキュリティ機能強化、その他のセキュリティ関連アップデートについて説明します。
exl-id: 5f8866ed-9215-4b2e-9c77-b2d474f6c1f9
source-git-commit: a5cdc9ee2d8c8632c40e0ced62182d5275b8b942
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# Adobe Commerce 2.4.8 セキュリティパッチのリリースノート

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.8-p2

Adobe Commerce 2.4.8-p2 セキュリティリリースは、2.4.8 の以前のリリースで特定された脆弱性に対するセキュリティバグ修正を提供します。

セキュリティのバグ修正の最新情報については、[Adobe セキュリティ速報 APSB25-71](https://helpx.adobe.com/security/products/magento/apsb25-71.html) を参照してください。

{{b2b-patches}}

## 2.4.8-p1

Adobe Commerce 2.4.8-p1 セキュリティリリースは、2.4.8 の以前のリリースで特定された脆弱性に対するセキュリティバグ修正を提供します。

セキュリティのバグ修正の最新情報については、[Adobe セキュリティ速報 APSB25-50](https://helpx.adobe.com/security/products/magento/apsb25-50.html) を参照してください。

{{b2b-patches}}

### ハイライト

このリリースには、次のハイライトが含まれています。

* **API パフォーマンスの強化** – 以前のセキュリティパッチの後に導入された一括非同期 web API エンドポイントのパフォーマンス低下を解決します。<!-- AC-14078 -->

* **CMS ブロックのアクセス修正** – 権限が制限された管理者ユーザー（マーチャンダイジングのみのアクセスなど）が [!UICONTROL CMS Blocks] リストページを表示できない問題を解決します。

  以前は、以前のセキュリティパッチをインストールした後に設定パラメーターが見つからないために、これらのユーザーにエラーが発生していました。<!-- AC-14087 -->

* **Cookie 制限互換性** - フレームワーク内の `MAX_NUM_COOKIES` 定数に関する後方互換性のない変更を解決します。 この更新により、期待される動作が復元され、cookie の制限とやり取りする拡張機能やカスタマイズの互換性が確保されます。<!-- AC-14475 -->

* **非同期操作** – 以前の顧客の注文を上書きするための制限付きの非同期操作。<!-- AC-13917 -->

* **CVE-2025-47110** の修正 – メールテンプレートの脆弱性を解決 <!-- AC-14695 -->

* **VULN-31547** の修正 – カテゴリの正規リンクの脆弱性を解決します。<!-- AC-14713 -->

>[!BEGINSHADEBOX]

CVE-2025-47110 および VULN-31547 の修正も、独立したパッチとして使用できます。 詳しくは、[ ナレッジベースの記事 ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-50) を参照してください。

>[!ENDSHADEBOX]
