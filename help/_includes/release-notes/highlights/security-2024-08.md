---
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---
# 2024 年 8 月のセキュリティパッチのハイライト

このリリースには、次のハイライトが含まれています。

* **[!DNL one-time passwords]** のレート制限：[!DNL two-factor authentication (2FA)] [!DNL one-time password (OTP)] の検証でレート制限を有効にするために、次の新しいシステム構成オプションが利用可能になりました。

   * [!UICONTROL **二要素認証の再試行制限**]
   * [!UICONTROL **二要素認証ロックアウト時間（秒）**]

  Adobeでは、ブルートフォース攻撃を軽減するための再試行回数を制限するために、2FA OTP 検証のしきい値を設定することをお勧めします。 詳しくは、『 [ 設定リファレンスガイド ](https://experienceleague.adobe.com/ja/docs/commerce-admin/config/security/2fa) の _セキュリティ/2FA_ を参照してください。<!-- AC-12095 -->

* **暗号化キーのローテーション**：新しい CLI コマンドを使用して暗号化キーを変更できるようになりました。 詳しくは、[ 暗号化キーのローテーションのトラブルシューティング：CVE-2024-34102](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/troubleshooting-encryption-key-rotation-cve-2024-34102) ナレッジベースの記事を参照してください。

* **[CVE-2020-27511](https://nvd.nist.gov/vuln/detail/CVE-2020-27511)** の修正 – [!DNL Prototype.js] セキュリティの脆弱性を解決します。<!-- AC-11936 -->

* **CVE-2024-39397[&#128279;](https://nvd.nist.gov/vuln/detail/CVE-2024-39397) の修正** リモートコード実行セキュリティの脆弱性を解決します。 この脆弱性は、オンプレミスまたはセルフホスト型のデプロイメントに Apache web サーバーを使用しているマーチャントに影響します。 この修正は、独立したパッチとしても使用できます。 詳しくは、[Adobe Commerceで利用可能なセキュリティ更新 – APSB24-61](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb24-61) ナレッジベースの記事を参照してください。<!-- ACSD-60551 -->
