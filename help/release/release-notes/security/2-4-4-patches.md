---
title: Adobe Commerce 2.4.4 セキュリティパッチリリースノート
description: Adobe Commerce バージョン 2.4.4のセキュリティパッチリリースに含まれているセキュリティバグの修正、セキュリティの強化、およびその他のセキュリティ関連アップデートについて説明します。
exl-id: 136d7090-6bf2-41e3-8445-b07bdc67f12b
source-git-commit: c297996273c42481fe9d3ee20ec3b9256e27fb5f
workflow-type: tm+mt
source-wordcount: '1914'
ht-degree: 0%

---


# Adobe Commerce 2.4.4 セキュリティパッチのリリースノート

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.4-p17

{{extended-support}}

Adobe Commerce 2.4.4-p17は、2.4.4の以前のリリースで特定された脆弱性に対するセキュリティバグ修正を提供する拡張サポートセキュリティリリースです。Adobe Commerceのお客様のみが利用できます。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB26-05](https://helpx.adobe.com/jp/security/products/magento/apsb26-05.html)を参照してください。

{{b2b-patches}}

## 2.4.4-p16

{{extended-support}}

Adobe Commerce 2.4.4-p16は、2.4.4の以前のリリースで特定された脆弱性に対するセキュリティバグ修正を提供する拡張サポートセキュリティリリースです。Adobe Commerceのお客様のみが利用できます。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB25-94](https://helpx.adobe.com/jp/security/products/magento/apsb25-94.html)を参照してください。

{{b2b-patches}}

### ハイライト

{{$include /help/_includes/release-notes/highlights/security-2025-10.md}}

>[!NOTE]
>
>2.4.4の拡張サポートセキュリティパッチは、Adobe Commerceのお客様のみが利用できます。 これらのパッチは、Magento Open Source コードベースでは使用できません。 [拡張サポート &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/release/planning/lifecycle-policy#extended-support)を参照してください。

### 既知の問題

#### チェックアウトページでstatic.min.jsとmixins.min.jsの読み込みに失敗する

{{checkout-page-fails-to-load-static-min-js-and-mixins-min-js}}

## 2.4.4-p15

{{extended-support}}

Adobe Commerce 2.4.4-p15は、以前のリリースの2.4.4で特定された脆弱性に対するセキュリティバグ修正を提供する拡張サポートセキュリティリリースです。Adobe Commerceのお客様のみが利用できます。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB25-71](https://helpx.adobe.com/jp/security/products/magento/apsb25-71.html)を参照してください。

{{b2b-patches}}

## 2.4.4-p14

{{extended-support}}

Adobe Commerce 2.4.4-p14は、以前のリリースの2.4.4で特定された脆弱性に対するセキュリティバグ修正を提供する拡張サポートセキュリティリリースです。Adobe Commerceのお客様のみが利用できます。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB25-50](https://helpx.adobe.com/jp/security/products/magento/apsb25-50.html)を参照してください。

{{b2b-patches}}

### ハイライト

このリリースには、次のハイライトが含まれています。

* **API パフォーマンスの向上** – 以前のセキュリティ パッチの後に導入された一括非同期web API エンドポイントのパフォーマンス低下を解決します。<!-- AC-14078 -->

* **CMS ブロック アクセス修正** – 制限された権限（マーチャンダイジング専用アクセスなど）を持つ管理者ユーザーが[!UICONTROL CMS Blocks]の一覧ページを表示できなかった問題を解決します。

  以前は、以前のセキュリティ パッチをインストールした後、構成パラメーターが欠落しているため、これらのユーザーでエラーが発生していました。<!-- AC-14087 -->

* **Cookie制限の互換性** - フレームワークの`MAX_NUM_COOKIES`定数に関する後方互換性のない変更を解決します。 この更新プログラムは、期待される動作を復元し、cookieの制限と相互作用する拡張機能またはカスタマイズの互換性を確保します。<!-- AC-14475 -->

* **非同期操作** – 以前の顧客の注文を上書きするための非同期操作が制限されています。<!-- AC-13917 -->

## 2.4.4-p13

{{extended-support}}

Adobe Commerce 2.4.4-p13のセキュリティリリースには、以前のリリースの2.4.4で特定された脆弱性に対するセキュリティバグの修正が含まれています。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB25-26](https://helpx.adobe.com/jp/security/products/magento/apsb25-26.html)を参照してください。

{{b2b-patches}}

### ハイライト

{{$include /help/_includes/release-notes/highlights/security-2025-04.md}}

## 2.4.4-p12

Adobe Commerce 2.4.4-p12 セキュリティリリースでは、以前のリリース 2.4.4で特定された脆弱性に対するセキュリティバグの修正が行われています。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB25-08](https://helpx.adobe.com/jp/security/products/magento/apsb25-08.html)を参照してください。

{{b2b-patches}}

### ハイライト

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.4-p11

Adobe Commerce 2.4.4-p11 セキュリティリリースには、以前のリリース 2.4.4で特定された脆弱性に対するセキュリティバグの修正が含まれています。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB24-73](https://helpx.adobe.com/jp/security/products/magento/apsb24-73.html)を参照してください。

{{b2b-patches}}

### ハイライト

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

## 2.4.4-p10

Adobe Commerce 2.4.4-p10 セキュリティリリースには、以前のリリース 2.4.4で特定された脆弱性に対するセキュリティバグの修正が含まれています。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB24-61](https://helpx.adobe.com/jp/security/products/magento/apsb24-61.html)を参照してください。

### ハイライト

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### このリリースに含まれるホットフィックス

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.4-p9

Adobe Commerce 2.4.4-p9のセキュリティリリースには、以前のリリースの2.4.4で特定された脆弱性に対するセキュリティバグの修正が含まれています。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB24-40](https://helpx.adobe.com/jp/security/products/magento/apsb24-40.html)を参照してください。

### CVE-2024-34102のホットフィックスを適用する

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

### プラットフォームのアップグレード

* **MariaDB 10.5 サポート**。 このパッチリリースでは、MariaDB バージョン 10.5との互換性が導入されています。Adobe Commerceは引き続きMariaDB バージョン 10.4と互換性がありますが、2024年6月18日にMariaDB 10.4 メンテナンスが終了するため、AdobeではAdobe Commerce 2.4.4-p9とすべての今後の2.4.4のセキュリティ専用パッチリリースをMariaDB バージョン 10.5でのみ使用することをお勧めします。<!--AC-11530-->

### ハイライト

{{$include /help/_includes/release-notes/highlights/2-4-7-security.md}}

## 2.4.4-p8

Adobe Commerce 2.4.4-p8 セキュリティリリースには、Adobe Commerce 2.4.4のデプロイメントに関するセキュリティバグ修正が含まれています。 これらのアップデートは、以前のリリースで特定された脆弱性を修正します。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB24-18](https://helpx.adobe.com/jp/security/products/magento/apsb24-18.html)を参照してください。

## 2.4.4-p7

Adobe Commerce 2.4.4-p7 セキュリティリリースには、以前のリリースで特定された脆弱性に対するセキュリティバグの修正が含まれています。 このリリースには、最新のセキュリティのベストプラクティスへのコンプライアンスを向上させるセキュリティの機能強化も含まれています。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB24-03](https://helpx.adobe.com/jp/security/products/magento/apsb24-03.html)を参照してください。

### ハイライト

このリリースでは、次の2つの重要なセキュリティ機能強化が導入されています。

* **生成されていないキャッシュキーの動作に変更が加えられました**:

   * ブロックの非生成キャッシュキーに、自動生成されるキーのプレフィックスとは異なるプレフィックスが含まれるようになりました。 （生成されないキャッシュキーは、テンプレートディレクティブ構文または`setCacheKey`または`setData` メソッドを使用して設定されるキーです）。
   * ブロックの生成されないキャッシュキーには、文字、数字、ハイフン（ – ）、アンダースコア（_）のみを含める必要があります。<!-- AC-9831 -->

* **自動生成されるクーポンコード数の制限**。 Commerceでは、自動生成されるクーポンコードの数が制限されるようになりました。 デフォルトの最大値は250,000です。 マーチャントは、新しい&#x200B;**[!UICONTROL Code Quantity Limit]**&#x200B;設定オプション（**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**）を使用して、この新しい制限を制御できます。<!-- AC-8753 -->

## 2.4.4-p6

Adobe Commerce 2.4.4-p6 セキュリティリリースには、以前のリリースで特定された脆弱性に対するセキュリティバグの修正が含まれています。 このリリースには、最新のセキュリティのベストプラクティスへのコンプライアンスを向上させるセキュリティの機能強化も含まれています。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB23-50](https://helpx.adobe.com/jp/security/products/magento/apsb23-50.html)を参照してください。

このリリースには、最新のセキュリティのベストプラクティスへのコンプライアンスを向上させるセキュリティの機能強化も含まれています。

### ハイライト

このリリースでは、`{BASE-URL}/page_cache/block/esi HTTP` エンドポイントに関連するリスクを軽減するのに役立つ、新しいフルページキャッシュ設定設定が導入されました。 このエンドポイントは、Commerceのレイアウトハンドルとブロック構造から無制限に動的に読み込まれるコンテンツフラグメントをサポートしています。 新しい&#x200B;**[!UICONTROL Handles Param]**&#x200B;構成設定では、このエンドポイントの`handles` パラメーターの値が設定され、APIごとに許可されるハンドルの最大数が決定されます。 このプロパティのデフォルト値は100です。 この値は、管理者（**[!UICONTROL Stores]** > **[!UICONTROL Settings: Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**）から変更できます。<!-- AC-9113 -->

### 既知の問題

**問題**: Composerによる&#x200B;**からのダウンロード中に**&#x200B;間違ったチェックサム `repo.magento.com` エラーがAdobe Commerceに表示され、パッケージのダウンロードが中断されます。 この問題は、プレリリース中に利用可能になったリリースパッケージのダウンロード中に発生する可能性があり、`magento/module-page-cache` パッケージの再パッケージによって発生します。

**回避策**：ダウンロード中にこのエラーが表示されるマーチャントは、次の手順を実行できます。

1) プロジェクト内の`/vendor` ディレクトリが存在する場合は、そのディレクトリを削除します。
2) `bin/magento composer update magento/module-page-cache` コマンドを実行します。 このコマンドは、`page cache` パッケージのみを更新します。

チェックサムの問題が解決しない場合は、`composer.lock` コマンドを再実行してすべてのパッケージを更新する前に、`bin/magento composer update` ファイルを削除してください。

## 2.4.4-p5

Adobe Commerce 2.4.4-p5 セキュリティリリースには、以前のリリースで特定された脆弱性に対するセキュリティバグの修正が含まれています。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB23-42](https://helpx.adobe.com/jp/security/products/magento/apsb23-42.html)を参照してください。

### CVE-2022-31160のホットフィックスを適用する

`jQuery-UI` ライブラリ バージョン 1.13.1には、Adobe CommerceとMagento Open Sourceの複数のバージョンに影響する既知のセキュリティ脆弱性（CVE-2022-31160）があります。 このライブラリは、Adobe CommerceおよびMagento Open Source 2.4.4、2.4.5、および2.4.6の依存関係です。影響を受けるデプロイメントを実行しているマーチャントは、ナレッジベース記事「[jQuery UI セキュリティ脆弱性CVE-2022-31160修正プログラム（2.4.4、2.4.5、2.4.6 リリース &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html?lang=ja)）を適用する必要があります。

## 2.4.4-p4

Adobe Commerce 2.4.4-p4 セキュリティリリースには、以前のリリースで特定された脆弱性に対するセキュリティバグ修正が含まれています。 このリリースには、最新のセキュリティのベストプラクティスに準拠するために、セキュリティの強化とプラットフォームのアップグレードも含まれています。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB23-35](https://helpx.adobe.com/jp/security/products/magento/apsb23-35.html)を参照してください。

### CVE-2022-31160のホットフィックスを適用する

`jQuery-UI` ライブラリ バージョン 1.13.1には、Adobe CommerceとMagento Open Sourceの複数のバージョンに影響する既知のセキュリティ脆弱性（CVE-2022-31160）があります。 このライブラリは、Adobe CommerceおよびMagento Open Source 2.4.4、2.4.5、および2.4.6の依存関係です。影響を受けるデプロイメントを実行しているマーチャントは、ナレッジベース記事「[jQuery UI セキュリティ脆弱性CVE-2022-31160修正プログラム（2.4.4、2.4.5、2.4.6 リリース &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html?lang=ja)）を適用する必要があります。

### ハイライト

[`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL クエリと（[`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)） REST エンドポイントの既定の動作が変更されました。 デフォルトでは、APIは常に`true`を返すようになりました。 マーチャントは元の動作を有効にできます。つまり、メールがデータベースに存在しない場合は`true`、存在する場合は`false`を返します。<!-- AC-6695 -->

### プラットフォームのアップグレード

このリリースのプラットフォームのアップグレードは、最新のセキュリティのベストプラクティスへのコンプライアンスを向上させます。

* **Varnish キャッシュ 7.3 サポート**。 このリリースは、最新バージョンのVarnish Cache 7.3と互換性があります。互換性は6.0.xおよび7u.2.x バージョンで維持されますが、Adobeでは、Varnish Cache バージョン 7.3またはバージョン 6.0 LTSでのみAdobe Commerce 2.4.4-p4を使用することをお勧めします。

* **RabbitMQ 3.11 サポート**。 このリリースは、最新バージョンのRabbitMQ 3.11と互換性があります。互換性は2023年8月までサポートされているRabbitMQ 3.9で維持されますが、AdobeではAdobe Commerce 2.4.4-p4をRabbitMQ 3.11でのみ使用することをお勧めします。

* **JavaScript ライブラリ**。 古いJavaScript ライブラリは、`moment.js` ライブラリ （v2.29.4）、`jQuery UI` ライブラリ （v1.13.2）、`jQuery`検証プラグインライブラリ （v1.19.5）など、最新のマイナーバージョンまたはパッチバージョンにアップグレードされました。

## 2.4.4-p3

Adobe Commerce 2.4.4-p3 セキュリティリリースには、以前のリリースで特定された脆弱性に対するセキュリティバグの修正が含まれています。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB23-17](https://helpx.adobe.com/jp/security/products/magento/apsb23-17.html)を参照してください。

## 2.4.4-p2

Adobe Commerce 2.4.4-p2のセキュリティリリースでは、以前のリリースで特定された脆弱性に対する修正が提供されています。 1つの修正には、新しい設定設定の作成が含まれます。 [!UICONTROL **電子メールが変更された場合は電子メールの確認を必要とする**]&#x200B;の設定設定により、管理者ユーザーが電子メールアドレスを変更したときに管理者が電子メールの確認を必要とすることができます。<!-- AC-6292-->

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB22-48](https://helpx.adobe.com/jp/security/products/magento/apsb22-48.html)を参照してください。

### 配送業者としてDHLを提供し続けるには、AC-3022.patchを適用します

DHLはスキーマバージョン 6.2を導入しており、近い将来スキーマバージョン 6.0を廃止する予定です。 DHL統合をサポートするAdobe Commerce 2.4.4以前のバージョンは、バージョン 6.0のみをサポートします。これらのリリースを展開する販売者は、DHLを配送業者として提供し続けるために、最も早い都合で`AC-3022.patch`を適用する必要があります。 パッチのダウンロードとインストールについて詳しくは、[配送業者としてDHLを提供し続けるためのパッチの適用](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier?_ga=2.201689433.994140970.1661546561-1218319047.1534347481) ナレッジベースの記事を参照してください。

## 2.4.4-p1

Adobe Commerce 2.4.4-p1 セキュリティリリースには、以前のリリースで特定された脆弱性に対する修正が含まれています。 このリリースには、最新のセキュリティのベストプラクティスに準拠するためのセキュリティの強化も含まれています。

セキュリティのバグ修正に関する最新情報については、[Adobe セキュリティ情報](https://helpx.adobe.com/jp/security/products/magento/apsb22-38.html)tを参照してください。

### 配送業者としてDHLを提供し続けるには、AC-3022.patchを適用します

DHLはスキーマバージョン 6.2を導入しており、近い将来スキーマバージョン 6.0を廃止する予定です。 DHL統合をサポートするAdobe Commerce 2.4.4以前のバージョンは、バージョン 6.0のみをサポートします。これらのリリースを展開する販売者は、DHLを配送業者として提供し続けるために、最も早い都合で`AC-3022.patch`を適用する必要があります。 パッチのダウンロードとインストールについて詳しくは、[配送業者としてDHLを提供し続けるためのパッチの適用](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) ナレッジベースの記事を参照してください。

### ハイライト

このリリースのセキュリティの改善点は、次のような最新のセキュリティのベストプラクティスに準拠することです。

* ACL リソースがインベントリに追加されました。
* インベントリテンプレートのセキュリティが強化されました。

### 既知の問題

**問題**: 2.4.4-p1 パッケージ `[2022-06-14T16:58:23.694Z] PHP Fatal error:  Declaration of Magento\TestFramework\ErrorLog\Logger::addRecord(int $level, string $message, array $context = []): bool must be compatible with Monolog\Logger::addRecord(int $level, string $message, array $context = [], ?Monolog\DateTimeImmutable $datetime = null): bool in /var/www/html/dev/tests/integration/framework/Magento/TestFramework/ErrorLog/Logger.php on line 69`で実行すると、Web APIと統合テストにこのエラーが表示されます。 **回避策**: `require monolog/monolog:2.6.0` コマンドを実行して、以前のバージョンのMonologをインストールします。<!-- AC-3651-->

**問題**:Adobe Commerce 2.4.4からAdobe Commerce 2.4.4-p1へのアップグレード中に、パッケージ バージョンのダウングレードに関する通知が表示される場合があります。 これらのメッセージは無視できます。 パッケージバージョンの相違は、パッケージ生成時の異常に起因します。 製品機能には影響はありません。 影響を受けるシナリオと回避策について詳しくは、ナレッジベースの記事「2.4.4から2.4.4-p1[」にアップグレードした後にダウングレードされた](https://support.magento.com/hc/en-us/articles/8214752983949) パッケージを参照してください。

<!-- Last updated from includes: 2026-03-19 11:29:47 -->
