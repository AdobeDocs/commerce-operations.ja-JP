---
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---
# 2.4.7 セキュリティの強化

* 支払いページでのスクリプトの整合性の検証に関する PCI 4.0 要件に準拠するために、**Subresource Integrity （SRI）のサポートを追加** しました。 サブリソースの整合性（SRI）のサポートは、ローカルファイルシステムに存在するすべてのJavaScript アセットの整合性ハッシュを提供します。 デフォルトの SRI 機能は、管理エリアとストアフロントエリアの支払いページにのみ実装されています。 ただし、マーチャントは、デフォルトの設定を他のページに拡張できます。 詳しくは、_Commerce PHP 開発者ガイドの [ サブリソースの整合性 ](https://developer.adobe.com/commerce/php/development/security/subresource-integrity/) を参照してください_.<!--AC-1153-->

* **コンテンツセキュリティポリシー（CSP）の変更** - PCI 4.0 の要件に準拠するためのAdobe Commerce コンテンツセキュリティポリシー（CSP）の設定の更新と機能強化。 詳しくは、_Commerce PHP 開発者ガイドの [ コンテンツセキュリティポリシー ](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) を参照してください。_ <!--AC-11513-->

   * Commerce管理エリアとストアフロントエリアの支払いページ用のデフォルトの CSP 設定が `restrict` モードになりました。 その他のすべてのページでは、デフォルト設定は `report-only` モードです。  2.4.7 より前のリリースでは、CSP はすべてのページに対して `report-only` モードで設定されていました。

   * CSP でインラインスクリプトの実行を許可する nonce プロバイダーを追加しました。 nonce プロバイダーは、各リクエストに対して一意の nonce 文字列を容易に生成できるようにします。 その後、文字列が CSP ヘッダーにアタッチされます。

   * 管理の注文を作成ページとストアフロントのチェックアウトページの CSP 違反をレポートするカスタム URI を設定するオプションを追加しました。 設定を追加するには、管理者から、または URI を `config.xml` ファイルに追加します。

     >[!NOTE]
     >
     >CSP 設定を `restrict` モードに更新すると、管理およびストアフロントの支払いページで既存のインラインスクリプトがブロックされる可能性があり、ページの読み込み時に次のブラウザーエラーが発生します。`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`。 許可リスト設定を更新して、必要なスクリプトを許可することで、これらのエラーを修正します。 [2&rbrace;Commerce PHP 開発者ガイド ](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#troubleshooting) トラブルシューティング _を参照してください。_
