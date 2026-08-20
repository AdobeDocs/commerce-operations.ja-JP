---
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---
# 2024年8月のセキュリティパッチのハイライト

このリリースには、次のハイライトが含まれています。

* **[!DNL one-time passwords]**&#x200B;のレート制限 – [!DNL two-factor authentication (2FA)] [!DNL one-time password (OTP)]検証でレート制限を有効にするために、次の新しいシステム設定オプションが使用できるようになりました。

  * [!UICONTROL **二段階認証の再試行回数**]
  * [!UICONTROL **二段階認証のロックアウト時間（秒）**]

  Adobeでは、2FA OTP検証のしきい値を設定して、ブルートフォース攻撃を軽減するための再試行回数を制限することをお勧めします。 詳しくは、_設定リファレンスガイド_&#x200B;の[&#x200B; セキュリティ > 2FA](https://experienceleague.adobe.com/en/docs/commerce-admin/config/security/2fa)を参照してください。<!-- AC-12095 -->

* **暗号化キーのローテーション** – 暗号化キーを変更するための新しいCLI コマンドが利用可能になりました。 詳しくは、「[暗号化キーのローテーションのトラブルシューティング：CVE-2024-34102](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27134) ナレッジベース」の記事を参照してください。

* **CVE-2020-27511&rbrack;(https://nvd.nist.gov/vuln/detail/CVE-2020-27511)**&#x200B;の修正 – [!DNL Prototype.js]のセキュリティ脆弱性を解決します。<!-- AC-11936 -->&lbrack;

* **CVE-2024-39397[&#128279;](https://nvd.nist.gov/vuln/detail/CVE-2024-39397)**&#x200B;の修正 – リモート コード実行のセキュリティの脆弱性を解決します。 この脆弱性は、オンプレミスまたはセルフホスト型のデプロイメントにApache web サーバーを使用するマーチャントに影響します。 この修正プログラムは、独立したパッチとしても利用できます。 詳しくは、「[Adobe Commerceに関するセキュリティアップデート - APSB24-61](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27133) Knowledge Base記事」を参照してください。<!-- ACSD-60551 -->
