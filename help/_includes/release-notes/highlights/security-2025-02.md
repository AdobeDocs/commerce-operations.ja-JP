---
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---
# 2025年2月のセキュリティパッチのハイライト

このリリースには、次のハイライトが含まれています。

* **暗号化キーの管理とデータの再暗号化** – 暗号化キーの管理を再設計して、使いやすさを向上させ、以前の制限やバグを排除しました。<!-- AC-12679 -->

  新しいCLI コマンドが、[変更](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/encryption-key) キーと[再暗号化](https://developer.adobe.com/commerce/php/development/security/data-encryption)特定のシステム設定、支払い、およびカスタムフィールドデータに対して使用できるようになりました。 このリリースでは、Admin UIでのキーの変更はサポートされなくなりました。 CLI コマンドを使用する必要があります。

* **CVE-2025-24434](https://nvd.nist.gov/vuln/detail/CVE-2025-24434)**&#x200B;の修正 – 認証の脆弱性を解決します。[

  この修正プログラムは、独立したパッチとしても利用できます。 詳しくは、[ ナレッジベース記事](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27149)を参照してください。<!-- AC-12755 -->

* **TinyMCE バージョンのダウングレード** - ライセンスの互換性の問題に対処するために、TinyMCE依存関係がバージョン 7から6.8.5にダウングレードされました。

  この変更により、Adobeは別のオープンソースのWYSIWYG エディターを評価する間、継続的なコンプライアンスが保証されます。
