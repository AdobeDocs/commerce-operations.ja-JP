---
source-git-commit: 10a6329502bc63ec06bac0652301770bd8e2935a
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 0%

---
# 2.4.7 セキュリティの強化

これらの問題に関連する確認された攻撃は、今日まで行われていません。 ただし、特定の脆弱性が悪用されて、顧客情報にアクセスしたり、管理者のセッションを引き継いだりする可能性があります。 これらの問題のほとんどは、攻撃者が最初に管理者へのアクセス権を取得する必要があります。 そのため、管理者を保護するために必要なすべての措置をとることをお勧めします。これには、以下の取り組みが含まれますが、これらに限定されません。

* IP許可リストに加える
* [二要素認証](https://developer.adobe.com/commerce/testing/functional-testing-framework/two-factor-authentication/)
* VPN の使用
* 代わりに一意の場所を使用 `/admin`
* 適切なパスワードハイジーン

このリリースのセキュリティの強化により、最新のセキュリティのベストプラクティスへのコンプライアンスが向上します。

* **生成されないキャッシュキーの動作の変更**:

   * ブロックの生成されないキャッシュキーに、自動的に生成されるキーのプレフィックスとは異なるプレフィックスが含まれるようになりました。 （生成されていないキャッシュキーは、テンプレートディレクティブ構文で設定されるキーです。 `setCacheKey` または `setData` メソッド）
   * ブロックの生成されないキャッシュキーに含める文字は、文字、数字、ハイフン（–）、アンダースコア（_）に限られるようになりました。  <!-- AC-9831 -->

* **自動生成されたクーポンコード数の制限**. Commerceでは、自動生成されるクーポンコードの数を制限するようになりました。 デフォルトの最大値は 250,000 です。 マーチャントは、新しいを使用することができます **[!UICONTROL Code Quantity Limit]** 設定オプション （**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**）を使用して、システムが多数のクーポンで圧倒されるのを防ぎます。 <!-- AC-8753 -->

* **デフォルトの管理者 URL 生成プロセスの最適化**. デフォルトの管理者 URL の生成は、ランダム性の向上に合わせて最適化されており、生成された URL を予測しにくくなります。 <!-- AC-9028 -->

* **サブリソースの整合性（SRI）のサポートを追加** 支払いページ上のスクリプトの整合性の検証に関する PCI 4.0 要件に準拠する。 サブリソースの整合性（SRI）のサポートは、ローカルファイルシステムに存在するすべての JavaScript アセットの整合性ハッシュを提供します。 デフォルトの SRI 機能は、管理エリアとストアフロントエリアの支払いページにのみ実装されています。 ただし、マーチャントは、デフォルトの設定を他のページに拡張できます。 参照： [サブリソースの整合性](https://developer.adobe.com/commerce/php/development/security/subresource-integrity/) が含まれる _Commerce PHP デベロッパーガイド_.<!--AC-1153-->

* **コンテンツセキュリティポリシー（CSP）の変更**—PCI 4.0 要件に準拠するためのAdobe Commerce コンテンツセキュリティポリシー（CSP）の設定の更新と機能強化。 詳しくは、を参照してください [コンテンツセキュリティポリシー](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) が含まれる _Commerce PHP デベロッパーガイド_. <!--AC-11513-->

   * Commerce管理エリアとストアフロントエリアの支払いページ用のデフォルトの CSP 設定が、以下になりました `restrict` モード。 その他のすべてのページでは、デフォルトの設定はです。 `report-only` モード。  2.4.7 より前のリリースでは、CSP はで設定されていました `report-only` すべてのページのモード。

   * CSP でインラインスクリプトの実行を許可する nonce プロバイダーを追加しました。 nonce プロバイダーは、各リクエストに対して一意の nonce 文字列を容易に生成できるようにします。 その後、文字列が CSP ヘッダーにアタッチされます。

   * 管理の注文を作成ページとストアフロントのチェックアウトページの CSP 違反をレポートするカスタム URI を設定するオプションを追加しました。 設定を追加するには、管理者から、または URI をに追加します `config.xml` ファイル。

     >[!NOTE]
     >
     >CSP 設定をに更新しています `restrict` モードでは、管理およびストアフロントの支払いページで既存のインラインスクリプトがブロックされる可能性があり、ページを読み込む際に次のブラウザーエラーが発生します。 `Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`. 許可リスト設定を更新して、必要なスクリプトを許可することで、これらのエラーを修正します。 参照： [トラブルシューティング](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#troubleshooting) が含まれる _Commerce PHP デベロッパーガイド_.

* 新しいフルページキャッシュ設定は、HTTP に関連するリスクを軽減するのに役立ちます `{BASE-URL}/page_cache/block/esi` エンドポイント。 このエンドポイントは、Commerceのレイアウトハンドルおよびブロック構造から無制限で動的に読み込まれるコンテンツフラグメントをサポートしています。 新しい **[!UICONTROL Handles params size]** 構成設定は、このエンドポイントの値を設定します `handles` パラメーター。API ごとに許可される最大ハンドル数を決定します。 このプロパティのデフォルト値は 100 です。 マーチャントは、この値を管理者（**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles params size]**）に設定します。 参照： [Varnish を使用するようにCommerce アプリケーションを設定します。](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/configure-varnish-commerce.html). <!-- AC-9113 -->

* **REST およびGraphQL API を通じて送信される支払い情報のネイティブレート制限**. マーチャントは、次のことができるようになりました [レート制限の設定](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/sales#rate-limiting) REST およびGraphQLを使用して送信される支払い情報。 この保護レイヤーの追加により、カード攻撃の防止がサポートされ、多くのクレジットカード番号を一度にテストするカード攻撃の量が減少する可能性があります。 これは、既存の REST エンドポイントのデフォルト動作の変更です。 参照： [レート制限](https://developer.adobe.com/commerce/webapi/get-started/rate-limiting/).

* のデフォルトの動作 [isEmailAvailable](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQLでクエリを実行し、[V1/customers/isEmailAvailable](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)） REST エンドポイントが変更されました。 デフォルトでは、API は常にを返すようになりました `true`. マーチャントは、を設定することで元の動作を有効にできます。 *[ゲスト チェックアウト ログインを有効にする](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/checkout)* 管理画面の「」オプションを使用して、 `yes`ただし、そうすることで、顧客情報が未認証のユーザーに公開される可能性があります。
