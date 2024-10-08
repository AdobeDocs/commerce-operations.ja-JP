---
source-git-commit: cb4f388c90902c2fe1df4a5d84841280fa740104
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---
# 2024 年 10 月セキュリティパッチのハイライト

このリリースには、次のハイライトが含まれています。

* **TinyMCE のアップグレード** - Admin の [WYSIWYG Editor](https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/wysiwyg/editor) は、最新バージョンの TinyMCE 依存関係（7.3&#x200B;）を使用するようになりました。

   * TinyMCE 7.3 は、ユーザーエクスペリエンスの向上、コラボレーションの強化、効率の向上を実現します。 TinyMCE 5 は 2.4.8 リリース行で削除されました&#x200B;

   * TinyMCE 5.10 ではセキュリティ上の脆弱性（[CVE-2024-38357](https://nvd.nist.gov/vuln/detail/CVE-2024-38357)）が報告されたため、現在サポートされているすべてのリリースラインに対しても依存関係がアップグレードされ、2024 年 10 月のすべてのセキュリティパッチに含まれるようになりました。

      * 2.4.7-p3
      * 2.4.6-p8
      * 2.4.5-p10
      * 2.4.4-p11

* **Require.js のアップグレード** - Adobe Commerceで最新バージョンの Require.js （2.3.7）が使用されるようになりました。

   * Require.js 2.3.6 でセキュリティの脆弱性（[CVE-2024-38999](https://nvd.nist.gov/vuln/detail/CVE-2024-38999)）が報告されたため、依存関係も、現在サポートされているすべてのリリースラインでアップグレードされ、2024 年 10 月のすべてのセキュリティパッチに含まれるようになりました。

      * 2.4.7-p3
      * 2.4.6-p8
      * 2.4.5-p10
      * 2.4.4-p11

>[!NOTE]
>
>これらのアップデートは後方互換性があるため、カスタマイズや拡張機能には影響しません&#x200B;
