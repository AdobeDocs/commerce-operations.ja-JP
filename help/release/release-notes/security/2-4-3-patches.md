---
title: Adobe Commerce 2.4.3 セキュリティパッチのリリースノート
description: Adobe Commerce バージョン 2.4.3 のセキュリティパッチリリースに含まれている、セキュリティバグ修正、セキュリティ機能強化、その他のセキュリティ関連アップデートについて説明します。
exl-id: 72d343cd-83d7-48ce-976a-e26ba1b8db27
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '931'
ht-degree: 0%

---


# Adobe Commerce 2.4.3 セキュリティパッチのリリースノート

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## Adobe Commerce 2.4.3-p3

Adobe Commerce 2.4.3-p3 セキュリティリリースは、以前のリリースの 2.4.3 で特定された脆弱性に対するセキュリティ修正を提供します。このリリースには、最新のセキュリティのベストプラクティスへのコンプライアンスを向上させるセキュリティの機能強化も含まれています。

セキュリティのバグ修正の最新情報については、[Adobe セキュリティ速報 APSB22-38](https://helpx.adobe.com/jp/security/products/magento/apsb22-38.html) を参照してください。

### 配送業者として DHL を引き続き提供するには、`AC-3022.patch` を適用してください

DHL ではスキーマバージョン 6.2 を導入しており、近い将来、スキーマバージョン 6.0 を廃止する予定です。 DHL 統合をサポートするAdobe Commerce 2.4.4 以前のバージョンは、バージョン 6.0 のみをサポートしています。これらのリリースをデプロイするマーチャントは、DHL を配送業者として引き続き提供するために、できるだけ早い時期に `AC-3022.patch` を適用する必要があります。 パッチのダウンロードとインストールについては、ナレッジベースの記事 [DHL を引き続き配送業者として提供するためのパッチを適用する &#x200B;](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) を参照してください。

### セキュリティのハイライト

* ACL リソースがインベントリに追加されました。
* 在庫テンプレートのセキュリティが強化されました。

## Adobe Commerce 2.4.3-p2

Adobe Commerce 2.4.3-p2 セキュリティリリースは、以前のリリースで特定された脆弱性に対するセキュリティバグ修正を提供します。 このリリースには、最新のセキュリティのベストプラクティスへのコンプライアンスを向上させるセキュリティの機能強化も含まれています。

セキュリティのバグ修正の最新情報については、[Adobe セキュリティ速報 APSB22-13](https://helpx.adobe.com/jp/security/products/magento/apsb22-13.html) を参照してください。  また、このパッチリリースでは、`MDVA-43395_EE_2.4.3-p1_COMPOSER_v1.patch.zip`、`MDVA-43443_EE_2.4.3-p1_COMPOSER_v1.patch.zip`、`MDVA-43395_EE_2.4.3-p1_COMPOSER_v1.patch` および `MDVA-43443_EE_2.4.3-p1_COMPOSER_v1.patch` によって対処された脆弱性も解決されています。


### 配送業者として DHL を引き続き提供するには、`AC-3022.patch` を適用してください

DHL ではスキーマバージョン 6.2 を導入しており、近い将来、スキーマバージョン 6.0 を廃止する予定です。 DHL 統合をサポートするAdobe Commerce 2.4.4 以前のバージョンは、バージョン 6.0 のみをサポートしています。これらのリリースをデプロイするマーチャントは、DHL を配送業者として引き続き提供するために、できるだけ早い時期に `AC-3022.patch` を適用する必要があります。 パッチのダウンロードとインストールについては、ナレッジベースの記事 [DHL を引き続き配送業者として提供するためのパッチを適用する &#x200B;](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) を参照してください。

### セキュリティのハイライト

* メール変数の使用は、セキュリティリスク軽減の一環として 2.3.4 に廃止され、より厳密な変数構文に置き換わりました。 このレガシー動作は、そのセキュリティリスク軽減の続きとして、このリリースでは完全に削除されています。

  その結果、Adobe Commerce 2.4.3-p2 にアップグレードすると、以前のバージョンで機能していたメールまたはニュースレターのテンプレートが正しく機能しなくなる場合があります。 影響を受けるテンプレートには、管理者の上書き、テーマ、子テーマ、カスタムモジュールまたはサードパーティの拡張機能のテンプレートが含まれます。 [&#x200B; 互換性アップグレードツール &#x200B;](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/overview.html?lang=ja) を使用して非推奨（廃止予定）の使用状況を修正した後でも、デプロイメントに影響が及ぶ場合があります。 考えられる影響と影響を受けるテンプレートの移行に関するガイドラインについて詳しくは、[&#x200B; カスタムメールテンプレートの移行 &#x200B;](https://developer.adobe.com/commerce/frontend-core/guide/templates/email-migration/) を参照してください。

* OAuth アクセストークンとパスワードリセットトークンが、データベースに保存される際に暗号化されるようになりました。<!-- AC-520 1323-->

* 英数字ではないファイル拡張子のアップロードを防ぐために、検証が強化されました。<!-- AC-479-->

* Adobe Commerceが実稼動モードの場合、Swagger がデフォルトで無効になりました。<!-- AC-1450-->

* 開発者は、Adobe Commerce RESTful エンドポイントで受け入れられる配列のサイズ制限を、エンドポイントごとに設定できるようになりました。 [API セキュリティ &#x200B;](https://developer.adobe.com/commerce/webapi/get-started/api-security/) を参照してください。<!-- AC-465-->

* ユーザーが web API を使用してシステム全体でリクエストできるリソースのサイズと数を制限し、個々のモジュールのデフォルトを上書きするメカニズムを追加しました。 この機能強化により、`MC-43048__set_rate_limits__2.4.3.patch` で対処された問題が解決します。 [API セキュリティ &#x200B;](https://developer.adobe.com/commerce/webapi/get-started/api-security/) を参照してください。<!-- AC-1120-->


## 2.4.3-p1

Adobe Commerce 2.4.3-p1 セキュリティリリースでは、前のリリース（Adobe Commerce 2.4.3 およびMagento Open Source 2.4.3）で特定された脆弱性のセキュリティバグが修正されています。 このリリースには、最新のセキュリティのベストプラクティスへのコンプライアンスを向上させるセキュリティの機能強化も含まれています。


セキュリティのバグ修正の最新情報については、[Adobe セキュリティ速報 APSB21-86](https://helpx.adobe.com/jp/security/products/magento/apsb21-86.html) を参照してください。 また、このパッチリリースでは、ベンダーが開発した [Braintree](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/payments/braintree.html?lang=ja)、[Klarna](https://marketplace.magento.com/klarna-m2-klarna.html) および [Vertex](https://marketplace.magento.com/vertexinc-vertex-tax-module.html) 拡張機能のバグ修正も提供しています。

### 配送業者として DHL を引き続き提供するには、`AC-3022.patch` を適用してください

DHL ではスキーマバージョン 6.2 を導入しており、近い将来、スキーマバージョン 6.0 を廃止する予定です。 DHL 統合をサポートするAdobe Commerce 2.4.4 以前のバージョンは、バージョン 6.0 のみをサポートしています。これらのリリースをデプロイするマーチャントは、DHL を配送業者として引き続き提供するために、できるだけ早い時期に `AC-3022.patch` を適用する必要があります。 パッチのダウンロードとインストールについては、ナレッジベースの記事 [DHL を引き続き配送業者として提供するためのパッチを適用する &#x200B;](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) を参照してください。

### ホットフィックス

このリリースには、次のホットフィックスと、前のパッチリリース用にリリースされたすべてのホットフィックスが含まれています。

* パッチ `AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch to address PHP fatal error on upgrade`。 パッチと問題の両方について詳しくは、[Adobe Commerceのアップグレード 2.4.3、2.3.7-p1 PHP の致命的なエラーに関するホットフィックス &#x200B;](https://support.magento.com/hc/en-us/articles/4408021533069-Adobe-Commerce-upgrade-2-4-3-2-3-7-p1-PHP-Fatal-error-Hotfix) ナレッジベースの記事を参照してください。

### セキュリティのハイライト

**セッション ID がデータベースから削除されました**。 このコードの変更により、マーチャントがデータベースに保存されている生のセッション ID を使用するカスタマイズまたはインストールされた拡張機能を持っている場合、重大な変更が発生する可能性があります。<!-- MC-40976-->

**メディアギャラリーフォルダーへの制限付き管理者アクセス**。 Media Gallery のデフォルトの権限では、設定で明示的に許可されているディレクトリ操作（表示、アップロード、削除、作成）のみが許可されるようになりました。 管理者ユーザーは、`catalog/category` または `wysiwyg` ディレクトリの外部でアップロードされたメディアギャラリーを介してメディアアセットにアクセスできなくなりました。 メディアアセットにアクセスする管理者は、明示的に許可されたフォルダーに移動するか、設定を調整する必要があります。 [Media Library フォルダー権限の変更 &#x200B;](https://developer.adobe.com/commerce/php/tutorials/backend/modify-image-library-permissions/) を参照してください。<!-- B2B-1897-->

**GraphQL クエリの複雑さの上限を引き下げ**。 サービス拒否（DOS）攻撃を防ぐために、GraphQLで許可されるクエリの最大複雑度が低下しました。 詳しくは、[GraphQLのセキュリティ設定 &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/usage/security-configuration/) を参照してください。<!-- PWA-1700-->

**最近の侵入テストの脆弱性** は、このリリースで修正されました。<!-- MC-42431-->

サポートされていないソース式 `unsafe-inline` が、コンテンツセキュリティポリシー `frame-ancestors` ディレクティブから削除されました。 [GitHub-33101](https://github.com/magento/magento2/issues/33101)<!-- MC-42632-->

<!-- Last updated from includes: 2025-05-28 17:01:56 -->
