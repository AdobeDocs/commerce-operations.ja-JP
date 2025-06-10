---
source-git-commit: 6899eec0d30acd39f8b4f8a0310096e7770feed1
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---
# 2025 年 2 月セキュリティパッチのハイライト

このリリースには、次のハイライトが含まれています。

* **暗号化キーの管理とデータの再暗号化**：操作性を向上させ、以前の制限やバグを排除するために設計し直された暗号化キーの管理 <!-- AC-12679 -->

  新しい CLI コマンドが、キーと [ 再暗号化 ](https://experienceleague.adobe.com/ja/docs/commerce-admin/systems/security/encryption-key)、特定のシステム構成、支払い [&#128279;](https://developer.adobe.com/commerce/php/development/security/data-encryption/) カスタムフィールドのデータに対して  変更」、「」で使用できるようになりました。 管理 UI でのキーの変更は、このリリースではサポートされなくなりました。 CLI コマンドを使用する必要があります。

* **CVE-2025-24434[&#128279;](https://nvd.nist.gov/vuln/detail/CVE-2025-24434)** の修正  認証の脆弱性を解決します。

  この修正は、独立したパッチとしても使用できます。 詳しくは、[ ナレッジベースの記事 ](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-08) を参照してください。<!-- AC-12755 -->
