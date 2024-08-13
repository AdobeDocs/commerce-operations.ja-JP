---
title: Adobe Commerce 2.4.4 セキュリティパッチのリリースノート
description: Adobe Commerce バージョン 2.4.4 のセキュリティパッチリリースに含まれている、セキュリティバグ修正、セキュリティ機能強化、その他のセキュリティ関連アップデートについて説明します。
exl-id: 136d7090-6bf2-41e3-8445-b07bdc67f12b
source-git-commit: 3a2d104f0a689ac3715af302d470a1660857543c
workflow-type: tm+mt
source-wordcount: '1461'
ht-degree: 0%

---


# Adobe Commerce 2.4.4 セキュリティパッチのリリースノート

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## 2.4.4-p10

Adobe Commerce 2.4.4-p10 セキュリティリリースは、2.4.4 の以前のリリースで特定された脆弱性に対するセキュリティバグ修正を提供します。

セキュリティのバグ修正の最新情報については、[Adobeセキュリティ速報 APSB24-61](https://helpx.adobe.com/security/products/magento/apsb24-61.html) を参照してください。

### ハイライト

{{$include /help/_includes/release-notes/2024-08/security.md}}

### このリリースに含まれるホットフィックス

{{$include /help/_includes/release-notes/2024-08/hotfixes-included.md}}

## 2.4.4-p9

Adobe Commerce 2.4.4-p9 セキュリティリリースは、以前のリリースの 2.4.4 で特定された脆弱性に対するセキュリティバグ修正を提供します。

セキュリティのバグ修正の最新情報については、[Adobeセキュリティ速報 APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html) を参照してください。

### CVE-2024-34102 のホットフィックスを適用する

{{$include /help/_includes/release-notes/2024-06/hotfixes-not-included.md}}

### Platform のアップグレード

* **MariaDB 10.5 のサポート**。 このパッチリリースでは、MariaDB バージョン 10.5 との互換性が導入されています。Adobe Commerceは MariaDB バージョン 10.4 と引き続き互換性がありますが、MariaDB 10.4 のメンテナンスは 2024 年 6 月 18 日（PT）に終了するため、Adobeでは、Adobe Commerce 2.4.4-p9 および今後のすべての 2.4.4 のセキュリティ専用パッチリリースは MariaDB バージョン 10.5 でのみ使用することをお勧めします。<!--AC-11530-->

### ハイライト

{{$include /help/_includes/release-notes/2-4-7-security.md}}

## 2.4.4-p8

Adobe Commerce 2.4.4-p8 セキュリティリリースは、Adobe Commerce 2.4.4 デプロイメントのセキュリティバグを修正します。 これらのアップデートにより、以前のリリースで特定された脆弱性が修正されます。

セキュリティのバグ修正の最新情報については、[Adobeセキュリティ速報 APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html) を参照してください。

## 2.4.4-p7

Adobe Commerce 2.4.4-p7 セキュリティリリースは、以前のリリースで特定された脆弱性に対するセキュリティバグ修正を提供します。 このリリースには、最新のセキュリティのベストプラクティスへのコンプライアンスを向上させるセキュリティの機能強化も含まれています。

セキュリティのバグ修正の最新情報については、[Adobeセキュリティ速報 APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html) を参照してください。

### ハイライト

このリリースでは、次の 2 つの重要なセキュリティ機能強化が導入されています。

* **生成されないキャッシュキーの動作の変更**:

   * ブロックの生成されないキャッシュキーに、自動的に生成されるキーのプレフィックスとは異なるプレフィックスが含まれるようになりました。 （生成されないキャッシュキーは、テンプレートディレクティブ構文または `setCacheKey` または `setData` メソッドで設定されるキーです）。
   * ブロックの生成されないキャッシュキーには、文字、数字、ハイフン（–）、アンダースコア（_）のみを含める必要があります。<!-- AC-9831 -->

* **自動生成されたクーポンコード数の制限**。 Commerceでは、自動生成されるクーポンコードの数を制限するようになりました。 デフォルトの最大値は 250,000 です。 マーチャントは、新しい **[!UICONTROL Code Quantity Limit]** 設定オプション（**[!UICONTROL Stores]**/**[!UICONTROL Settings:Configuration]**/**[!UICONTROL Customers]**/**[!UICONTROL Promotions]**）を使用して、この新しい制限を制御できます。<!-- AC-8753 -->

## 2.4.4-p6

Adobe Commerce 2.4.4-p6 セキュリティリリースは、以前のリリースで特定された脆弱性に対するセキュリティバグ修正を提供します。 このリリースには、最新のセキュリティのベストプラクティスへのコンプライアンスを向上させるセキュリティの機能強化も含まれています。

セキュリティのバグ修正の最新情報については、[Adobeセキュリティ速報 APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html) を参照してください。

このリリースには、最新のセキュリティのベストプラクティスへのコンプライアンスを向上させるセキュリティの機能強化も含まれています。

### ハイライト

このリリースでは、`{BASE-URL}/page_cache/block/esi HTTP` エンドポイントに伴うリスクを軽減するのに役立つ、新しいフルページキャッシュ設定が導入されています。 このエンドポイントは、Commerceのレイアウトハンドルおよびブロック構造から無制限で動的に読み込まれるコンテンツフラグメントをサポートしています。 新しい **[!UICONTROL Handles Param]** 設定では、このエンドポイントの `handles` パラメーターの値を設定します。このパラメーターによって、API あたりの最大ハンドル数が決定されます。 このプロパティのデフォルト値は 100 です。 マーチャントは、管理者（**[!UICONTROL Stores]**/**[!UICONTROL Settings: Configuration]**/**[!UICONTROL System]**/**[!UICONTROL Full Page Cache]**/**[!UICONTROL Handles Param]**）からこの値を変更できます。<!-- AC-9113 -->

### 既知の問題

**問題**:`repo.magento.com` から Composer によるダウンロード中にAdobe Commerceで **wrong checksum** エラーが表示され、パッケージのダウンロードが中断される。 この問題は、プレリリース時に使用可能になったリリースパッケージのダウンロード中に発生する可能性があります。これは、`magento/module-page-cache` パッケージの再パッケージ化が原因です。

**回避策**：ダウンロード中にこのエラーが表示されたマーチャントは、次の手順を実行できます。

1) プロジェクト内に `/vendor` ディレクトリが存在する場合は、削除します。
2) `bin/magento composer update magento/module-page-cache` コマンドを実行します。 このコマンドは、`page cache` パッケージのみを更新します。

チェックサムの問題が解決しない場合は、`bin/magento composer update` コマンドを再実行する前に `composer.lock` ファイルを削除し、すべてのパッケージを更新します。

## 2.4.4-p5

Adobe Commerce 2.4.4-p5 セキュリティリリースは、以前のリリースで特定された脆弱性に対するセキュリティバグ修正を提供します。

セキュリティのバグ修正の最新情報については、[Adobeセキュリティ速報 APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html) を参照してください。

### CVE-2022-31160 のホットフィックスを適用する

`jQuery-UI` library バージョン 1.13.1 には、複数のバージョンのAdobe CommerceおよびMagento Open Sourceに影響する既知のセキュリティ脆弱性（CVE-2022-31160）があります。 このライブラリは、Adobe CommerceとMagento Open Source 2.4.4、2.4.5、2.4.6 の依存関係です。影響を受けるデプロイメントを実行しているマーチャントは、ナレッジベース記事の 2.4.4、2.4.5、2.4.6 リリースの [jQuery UI のセキュリティ脆弱性 CVE-2022-31160 の修正で指定されたパッチを適用する必要 ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) あります。

## 2.4.4-p4

Adobe Commerce 2.4.4-p4 セキュリティリリースは、以前のリリースで特定された脆弱性に対するセキュリティバグ修正を提供します。 このリリースには、最新のセキュリティのベストプラクティスへのコンプライアンスを向上させるためのセキュリティ機能強化とプラットフォームアップグレードも含まれています。

セキュリティのバグ修正の最新情報については、[Adobeセキュリティ速報 APSB23-35](https://helpx.adobe.com/security/products/magento/apsb23-35.html) を参照してください。

### CVE-2022-31160 のホットフィックスを適用する

`jQuery-UI` library バージョン 1.13.1 には、複数のバージョンのAdobe CommerceおよびMagento Open Sourceに影響する既知のセキュリティ脆弱性（CVE-2022-31160）があります。 このライブラリは、Adobe CommerceとMagento Open Source 2.4.4、2.4.5、2.4.6 の依存関係です。影響を受けるデプロイメントを実行しているマーチャントは、ナレッジベース記事の 2.4.4、2.4.5、2.4.6 リリースの [jQuery UI のセキュリティ脆弱性 CVE-2022-31160 の修正で指定されたパッチを適用する必要 ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) あります。

### ハイライト

[`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL クエリと（[`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)） REST エンドポイントのデフォルトの動作が変更されました。 デフォルトでは、API は常に `true` を返すようになりました。 マーチャントは、元の動作を有効にすることができます。これは、メールがデータベースに存在しない場合は `true` を返し、存在する場合は `false` を返します。<!-- AC-6695 -->

### Platform のアップグレード

このリリースのプラットフォームのアップグレードにより、最新のセキュリティのベストプラクティスへのコンプライアンスが向上します。

* **Varnish cache 7.3 のサポート**。 このリリースは、最新バージョンの Varnish Cache 7.3 と互換性があります。6.0.x および 7u.2.x バージョンとの互換性は維持されますが、Adobeでは、Adobe Commerce 2.4.4-p4 を Varnish Cache バージョン 7.3 またはバージョン 6.0 LTS でのみ使用することをお勧めします。

* **RabbitMQ 3.11 サポート**。 このリリースは最新バージョンのRabbitMQ 3.11 と互換性があります。互換性はRabbitMQ 3.9 に残っています。このバージョンは 2023 年 8 月までサポートされます。ただし、Adobeでは、Adobe Commerce 2.4.4-p4 をRabbitMQ 3.11 でのみ使用することをお勧めします。

* **JavaScript ライブラリ**。 古いJavaScript ライブラリは、`moment.js` ライブラリ（v2.29.4）、`jQuery UI` ライブラリ（v1.13.2）、`jQuery` validation プラグインライブラリ（v1.19.5）など、最新のマイナーバージョンまたはパッチバージョンにアップグレードされています。

## 2.4.4-p3

Adobe Commerce 2.4.4-p3 セキュリティリリースは、以前のリリースで特定された脆弱性に対するセキュリティバグ修正を提供します。

セキュリティのバグ修正の最新情報については、[Adobeセキュリティ速報 APSB23-17](https://helpx.adobe.com/security/products/magento/apsb23-17.html) を参照してください。

## 2.4.4-p2

Adobe Commerce 2.4.4-p2 セキュリティリリースは、以前のリリースで特定された脆弱性の修正を提供します。 1 つの修正には、新しい設定の作成が含まれます。 「**メールが変更された場合、メールによる確認を要求する**」設定を使用すると、管理者ユーザーがメールアドレスを変更したときに、管理者がメールによる確認を要求できます。<!-- AC-6292-->

セキュリティのバグ修正の最新情報については、[Adobeセキュリティ速報 APSB22-48](https://helpx.adobe.com/security/products/magento/apsb22-48.html) を参照してください。

### AC-3022.patch を適用して、引き続き配送業者として DHL を提供します

DHL ではスキーマバージョン 6.2 を導入しており、近い将来、スキーマバージョン 6.0 を廃止する予定です。 DHL 統合をサポートするAdobe Commerce 2.4.4 以前のバージョンは、バージョン 6.0 のみをサポートしています。これらのリリースをデプロイするマーチャントは、DHL を配送業者として引き続き提供するために、できるだけ早い時期に `AC-3022.patch` を適用する必要があります。 パッチのダウンロードとインストールについては、ナレッジベースの記事 [DHL を引き続き配送業者として提供するためのパッチを適用する ](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier?_ga=2.201689433.994140970.1661546561-1218319047.1534347481) を参照してください。

## 2.4.4-p1

Adobe Commerce 2.4.4-p1 セキュリティリリースは、以前のリリースで特定された脆弱性の修正を提供します。 このリリースには、最新のセキュリティのベストプラクティスへのコンプライアンスを向上させるためのセキュリティの機能強化も含まれています。

セキュリティのバグ修正の最新情報については、[Adobe セキュリティ速報 ](https://helpx.adobe.com/security/products/magento/apsb22-38.html).t を参照してください

### 配送業者として DHL を引き続き提供するには、`AC-3022.patch` を適用してください

DHL ではスキーマバージョン 6.2 を導入しており、近い将来、スキーマバージョン 6.0 を廃止する予定です。 DHL 統合をサポートするAdobe Commerce 2.4.4 以前のバージョンは、バージョン 6.0 のみをサポートしています。これらのリリースをデプロイするマーチャントは、DHL を配送業者として引き続き提供するために、できるだけ早い時期に `AC-3022.patch` を適用する必要があります。 パッチのダウンロードとインストールについては、ナレッジベースの記事 [DHL を引き続き配送業者として提供するためのパッチを適用する ](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) を参照してください。

### ハイライト

このリリースのセキュリティの強化により、次のような最新のセキュリティのベストプラクティスへのコンプライアンスが向上しています。

* ACL リソースがインベントリに追加されました。
* 在庫テンプレートのセキュリティが強化されました。

### 既知の問題

**問題**:2.4.4-p1 パッケージ（`[2022-06-14T16:58:23.694Z] PHP Fatal error:  Declaration of Magento\TestFramework\ErrorLog\Logger::addRecord(int $level, string $message, array $context = []): bool must be compatible with Monolog\Logger::addRecord(int $level, string $message, array $context = [], ?Monolog\DateTimeImmutable $datetime = null): bool in /var/www/html/dev/tests/integration/framework/Magento/TestFramework/ErrorLog/Logger.php on line 69`）で web API および統合テストを実行すると、次のエラーが表示されます。 **回避策**:`require monolog/monolog:2.6.0` コマンドを実行して、以前のバージョンの Monolog をインストールします。<!-- AC-3651-->

**問題**:Adobe Commerce 2.4.4 からAdobe Commerce 2.4.4-p1 にアップグレードする際に、マーチャントがパッケージのバージョンのダウングレードに関する通知に気付く場合があります。 これらのメッセージは無視できます。 パッケージバージョンの不一致は、パッケージ生成時の異常値が原因で発生します。 製品の機能に影響はありません。 影響を受けるシナリオと回避策の説明については、ナレッジベースの記事 [2.4.4 から 2.4.4-p1 へのアップグレード後にダウングレードされたパッケージ ](https://support.magento.com/hc/en-us/articles/8214752983949) を参照してください。
