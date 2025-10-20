---
source-git-commit: c71367c553dce66c146540389461f36eaa529bfc
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---
# 2025 年 6 月のセキュリティパッチのハイライト

このリリースには、次のハイライトが含まれています。

* **API パフォーマンスの強化** – 以前のセキュリティパッチの後に導入された一括非同期 web API エンドポイントのパフォーマンス低下を解決します。<!-- AC-14078 -->

* **CMS ブロックのアクセス修正** – 権限が制限された管理者ユーザー（マーチャンダイジングのみのアクセスなど）が [!UICONTROL CMS Blocks] リストページを表示できない問題を解決します。

  以前は、以前のセキュリティパッチをインストールした後に設定パラメーターが見つからないために、これらのユーザーにエラーが発生していました。<!-- AC-14087 -->

* **Cookie 制限互換性** - フレームワーク内の `MAX_NUM_COOKIES` 定数に関する後方互換性のない変更を解決します。 この更新により、期待される動作が復元され、cookie の制限とやり取りする拡張機能やカスタマイズの互換性が確保されます。<!-- AC-14475 -->

* **非同期操作** – 以前の顧客の注文を上書きするための制限付きの非同期操作。<!-- AC-13917 -->

* **CVE-2025-47110** の修正 – メールテンプレートの脆弱性を解決 <!-- AC-14695 -->

>[!BEGINSHADEBOX]

CVE-2025-47110 の修正は、独立したパッチとしても使用できます。 詳しくは、[&#x200B; ナレッジベースの記事 &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-50) を参照してください。

>[!ENDSHADEBOX]