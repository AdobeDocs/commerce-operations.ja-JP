---
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---
# 2.4.7 セキュリティの強化

* **支払いページでのスクリプトの整合性の検証に関するPCI 4.0要件に準拠するため、サブリソース整合性（SRI）サポート**&#x200B;を追加しました。 Subresource Integrity （SRI）のサポートは、ローカルファイルシステムにあるすべてのJavaScript アセットに対して整合性ハッシュを提供します。 デフォルトのSRI機能は、管理領域とストアフロント領域の支払いページにのみ実装されます。 ただし、マーチャントはデフォルト設定を他のページに拡張できます。 _Commerce PHP開発者ガイド_&#x200B;の[Subresource Integrity](https://developer.adobe.com/commerce/php/development/security/subresource-integrity/)を参照してください。<!--AC-1153-->

* **コンテンツセキュリティポリシー（CSP）の変更** - PCI 4.0要件に準拠するため、Adobe Commerce コンテンツセキュリティポリシー（CSP）の設定の更新と機能強化。 詳しくは、_Commerce PHP開発者ガイド_&#x200B;の[&#x200B; コンテンツセキュリティポリシー](https://developer.adobe.com/commerce/php/development/security/content-security-policies/)を参照してください。<!--AC-11513-->

  * Commerce管理領域とストアフロント領域の支払いページのデフォルト CSP設定が`restrict` モードになりました。 その他のすべてのページでは、デフォルト設定は`report-only` モードです。  2.4.7より前のリリースでは、すべてのページに対して`report-only` モードでCSPが設定されていました。

  * CSPでインラインスクリプトの実行を許可するnonce プロバイダーを追加しました。 nonce プロバイダーは、各リクエストに対して一意のnonce文字列を生成しやすくします。 その後、文字列がCSP ヘッダーに添付されます。

  * 管理者の注文を作成ページとストアフロントのチェックアウトページのCSP違反をレポートするためのカスタム URIを設定するオプションを追加しました。 管理者から、または`config.xml` ファイルにURIを追加することで、設定を追加できます。

    >[!NOTE]
    >
    >CSP設定を`restrict` モードに更新すると、Adminおよびストアフロントの支払いページ上の既存のインラインスクリプトがブロックされる可能性があり、ページの読み込み時に次のブラウザーエラーが発生します：`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`。 これらのエラーを修正するには、ホワイトリスト設定を更新して、必要なスクリプトを許可します。 _Commerce PHP開発者ガイド_&#x200B;の[&#x200B; トラブルシューティング &#x200B;](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#troubleshooting)を参照してください。
