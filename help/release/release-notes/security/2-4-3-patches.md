---
title: Adobe Commerce 2.4.3 セキュリティパッチのリリースノート
description: Adobe Commerce バージョン 2.4.3のセキュリティパッチリリースに含まれているセキュリティバグの修正、セキュリティの強化、およびその他のセキュリティ関連アップデートについて説明します。
exl-id: 72d343cd-83d7-48ce-976a-e26ba1b8db27
source-git-commit: f9a135fc63574ccbecd3f564a87fc5c4ac03f009
workflow-type: tm+mt
source-wordcount: '1106'
ht-degree: 0%

---


# Adobe Commerce 2.4.3 セキュリティパッチのリリースノート

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## Adobe Commerce 2.4.3-p3

Adobe Commerce 2.4.3-p3 セキュリティリリースでは、以前のリリースの2.4.3で特定された脆弱性に対するセキュリティ修正が提供されています。 このリリースには、最新のセキュリティのベストプラクティスへのコンプライアンスを向上させるセキュリティの機能強化も含まれています。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB22-38](https://helpx.adobe.com/security/products/magento/apsb22-38.html)を参照してください。

### 配送業者としてDHLを提供し続けるには、AC-3022.patchを適用します

DHLはスキーマバージョン 6.2を導入しており、近い将来スキーマバージョン 6.0を廃止する予定です。 DHL統合をサポートするAdobe Commerce 2.4.4以前のバージョンは、バージョン 6.0のみをサポートします。 これらのリリースを展開する販売者は、DHLを配送業者として提供し続けるために、最も早い都合で`AC-3022.patch`を適用する必要があります。 パッチのダウンロードとインストールについて詳しくは、[配送業者としてDHLを提供し続けるためのパッチの適用](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) ナレッジベースの記事を参照してください。

### セキュリティのハイライト

* ACL リソースがインベントリに追加されました。
* インベントリテンプレートのセキュリティが強化されました。



## Adobe Commerce 2.4.3-p2

Adobe Commerce 2.4.3-p2 セキュリティリリースには、以前のリリースで特定された脆弱性に対するセキュリティバグ修正が含まれています。 このリリースには、最新のセキュリティのベストプラクティスへのコンプライアンスを向上させるセキュリティの機能強化も含まれています。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB22-13](https://helpx.adobe.com/security/products/magento/apsb22-13.html)を参照してください。  パッチリリースでは、`MDVA-43395_EE_2.4.3-p1_COMPOSER_v1.patch.zip`、`MDVA-43443_EE_2.4.3-p1_COMPOSER_v1.patch.zip`、`MDVA-43395_EE_2.4.3-p1_COMPOSER_v1.patch`、`MDVA-43443_EE_2.4.3-p1_COMPOSER_v1.patch`が解決した脆弱性も解決されます。


### 配送業者としてDHLを提供し続けるには、AC-3022.patchを適用します

DHLはスキーマバージョン 6.2を導入しており、近い将来スキーマバージョン 6.0を廃止する予定です。 DHL統合をサポートするAdobe Commerce 2.4.4以前のバージョンは、バージョン 6.0のみをサポートします。 これらのリリースを展開する販売者は、DHLを配送業者として提供し続けるために、最も早い都合で`AC-3022.patch`を適用する必要があります。 パッチのダウンロードとインストールについて詳しくは、[配送業者としてDHLを提供し続けるためのパッチの適用](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) ナレッジベースの記事を参照してください。

### セキュリティのハイライト

* メール変数の使用は、より厳格な変数の構文を優先するセキュリティリスク軽減の一環として、2.3.4で廃止されました。 このレガシー動作は、そのセキュリティリスク軽減の継続として、このリリースで完全に削除されました。

  その結果、以前のバージョンで動作していた電子メールやニュースレターのテンプレートが、Adobe Commerce 2.4.3-p2にアップグレードした後で正しく動作しない場合があります。 影響を受けるテンプレートには、管理者の上書き、テーマ、子テーマ、カスタムモジュールまたはサードパーティの拡張機能のテンプレートが含まれます。 非推奨の使用を修正するために[ アップグレード互換性ツール ](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/overview.html)を使用した後でも、デプロイメントが影響を受ける可能性があります。 影響を受けるテンプレートを移行する際の潜在的な影響とガイドラインについては、[ カスタムメールテンプレートの移行](https://developer.adobe.com/commerce/frontend-core/guide/templates/email-migration)を参照してください。

* OAuth アクセストークンとパスワードリセットトークンは、データベースに保存されたときに暗号化されるようになりました。<!-- AC-520 1323-->

* 非英数字のファイル拡張子のアップロードを防ぐため、検証が強化されました。<!-- AC-479-->

* Adobe Commerceが実稼動モードの場合、Swaggerはデフォルトで無効になりました。<!-- AC-1450-->

* 開発者は、エンドポイントごとに、Adobe Commerce RESTful エンドポイントで受け入れられる配列のサイズ制限を設定できるようになりました。 [API セキュリティ ](https://developer.adobe.com/commerce/webapi/get-started/api-security/)を参照してください。<!-- AC-465-->

* ユーザーがweb APIを通じてシステム全体でリクエストできるリソースのサイズと数を制限し、個々のモジュールのデフォルトを上書きするためのメカニズムを追加しました。 この機能強化により、`MC-43048__set_rate_limits__2.4.3.patch`が対処した問題が解決されます。 [API セキュリティ ](https://developer.adobe.com/commerce/webapi/get-started/api-security/)を参照してください。<!-- AC-1120-->


## 2.4.3-p1

Adobe Commerce 2.4.3-p1 セキュリティリリースには、以前のリリース（Adobe Commerce 2.4.3およびMagento Open Source 2.4.3）で特定された脆弱性に対するセキュリティバグ修正が含まれています。 このリリースには、最新のセキュリティのベストプラクティスへのコンプライアンスを向上させるセキュリティの機能強化も含まれています。


セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB21-86](https://helpx.adobe.com/security/products/magento/apsb21-86.html)を参照してください。 このパッチリリースでは、[Braintree](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/payments/braintree.html)、[Klarna](https://commercemarketplace.adobe.com//klarna-m2-klarna.html)、[Vertex](https://commercemarketplace.adobe.com//vertexinc-vertex-tax-module.html)のベンダーが開発した拡張機能のバグ修正も提供されています。

### 配送業者としてDHLを提供し続けるには、AC-3022.patchを適用します

DHLはスキーマバージョン 6.2を導入しており、近い将来スキーマバージョン 6.0を廃止する予定です。 DHL統合をサポートするAdobe Commerce 2.4.4以前のバージョンは、バージョン 6.0のみをサポートします。 これらのリリースを展開する販売者は、DHLを配送業者として提供し続けるために、最も早い都合で`AC-3022.patch`を適用する必要があります。 パッチのダウンロードとインストールについて詳しくは、[配送業者としてDHLを提供し続けるためのパッチの適用](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) ナレッジベースの記事を参照してください。

### ホットフィックス

このリリースには、次のホットフィックスと、以前のパッチリリースでリリースされたすべてのホットフィックスが含まれています。

* `AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch to address PHP fatal error on upgrade`にパッチを適用します。 パッチと問題の両方について詳しくは、[Adobe Commerce アップグレード 2.4.3、2.3.7-p1 PHP Fatal error Hotfix](https://support.magento.com/hc/en-us/articles/4408021533069-Adobe-Commerce-upgrade-2-4-3-2-3-7-p1-PHP-Fatal-error-Hotfix) ナレッジベースの記事を参照してください。

### セキュリティのハイライト

**セッション IDがデータベース**&#x200B;から削除されました。 このコードの変更により、マーチャントがカスタマイズを行ったり、データベースに保存されている生のセッション IDを使用する拡張機能をインストールしたりすると、破損する可能性があります。<!-- MC-40976-->

**Media Gallery フォルダー**&#x200B;への管理者アクセスが制限されています。 デフォルトのメディアギャラリー権限で、設定で明示的に許可されているディレクトリ操作（表示、アップロード、削除、作成）のみが許可されるようになりました。 管理者ユーザーは、`catalog/category`または`wysiwyg` ディレクトリ以外にアップロードされたメディアギャラリーを通じてメディアアセットにアクセスできなくなります。 メディアアセットにアクセスする管理者は、明示的に許可されたフォルダーに移動するか、設定を調整する必要があります。 [ メディアライブラリフォルダーの権限の変更](https://developer.adobe.com/commerce/php/tutorials/backend/modify-image-library-permissions/)を参照してください。<!-- B2B-1897-->

**GraphQL クエリの複雑さの制限を下げました**。 サービス拒否（DOS）攻撃を防ぐために、GraphQLで許可される最大クエリの複雑さが軽減されました。 [GraphQL セキュリティ設定](https://developer.adobe.com/commerce/webapi/graphql/usage/security-configuration/)を参照してください。<!-- PWA-1700-->

**最近の侵入テストの脆弱性**&#x200B;は、このリリースで修正されました。<!-- MC-42431-->

サポートされていないソース式`unsafe-inline`がコンテンツセキュリティポリシー`frame-ancestors` ディレクティブから削除されました。 [GitHub-33101](https://github.com/magento/magento2/issues/33101)<!-- MC-42632-->

<!-- Last updated from includes: 2025-05-28 17:01:56 -->
