---
source-git-commit: 4ed23e2a8319ff97f8206f752cf1cbe2e73ea5c5
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---
# 2.4.7 セキュリティの強化

* **サブリソースの整合性（SRI）のサポートを追加** 支払いページ上のスクリプトの整合性の検証に関する PCI 4.0 要件に準拠する。 サブリソースの整合性（SRI）のサポートは、ローカルファイルシステムに存在するすべての JavaScript アセットの整合性ハッシュを提供します。 デフォルトの SRI 機能は、管理エリアとストアフロントエリアの支払いページにのみ実装されています。 ただし、マーチャントは、デフォルトの設定を他のページに拡張できます。 参照： [サブリソースの整合性](https://developer.adobe.com/commerce/php/development/security/subresource-integrity/) が含まれる _Commerce PHP デベロッパーガイド_.<!--AC-1153-->

* **コンテンツセキュリティポリシー（CSP）の変更**—PCI 4.0 要件に準拠するためのAdobe Commerce コンテンツセキュリティポリシー（CSP）の設定の更新と機能強化。 詳しくは、を参照してください [コンテンツセキュリティポリシー](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) が含まれる _Commerce PHP デベロッパーガイド_. <!--AC-11513-->

   * Commerce管理エリアとストアフロントエリアの支払いページ用のデフォルトの CSP 設定が、以下になりました `restrict` モード。 その他のすべてのページでは、デフォルトの設定はです。 `report-only` モード。  2.4.7 より前のリリースでは、CSP はで設定されていました `report-only` すべてのページのモード。

   * CSP でインラインスクリプトの実行を許可する nonce プロバイダーを追加しました。 nonce プロバイダーは、各リクエストに対して一意の nonce 文字列を容易に生成できるようにします。 その後、文字列が CSP ヘッダーにアタッチされます。

   * 管理の注文を作成ページとストアフロントのチェックアウトページの CSP 違反をレポートするカスタム URI を設定するオプションを追加しました。 設定を追加するには、管理者から、または URI をに追加します `config.xml` ファイル。

     >[!NOTE]
     >
     >CSP 設定をに更新しています `restrict` モードでは、管理およびストアフロントの支払いページで既存のインラインスクリプトがブロックされる可能性があり、ページを読み込む際に次のブラウザーエラーが発生します。 `Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`. 許可リスト設定を更新して、必要なスクリプトを許可することで、これらのエラーを修正します。 参照： [トラブルシューティング](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#troubleshooting) が含まれる _Commerce PHP デベロッパーガイド_.
