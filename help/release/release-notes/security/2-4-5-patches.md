---
title: Adobe Commerce 2.4.5 セキュリティパッチのリリースノート
description: Adobe Commerce バージョン 2.4.5 のセキュリティパッチリリースに含まれている、セキュリティバグ修正、セキュリティ機能強化、その他のセキュリティ関連アップデートについて説明します。
exl-id: 1b5f6d84-877a-45ea-8ff5-db83e3d360dd
source-git-commit: 2269c99908c0f8292ad62bd5837b1b8cebd50cb3
workflow-type: tm+mt
source-wordcount: '1101'
ht-degree: 0%

---


# Adobe Commerce 2.4.5 セキュリティパッチのリリースノート

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.5-p8

Adobe Commerce 2.4.5-p7 セキュリティリリースは、以前のリリースの 2.4.5 で特定された脆弱性に対するセキュリティバグ修正を提供します。

セキュリティのバグ修正の最新情報については、[Adobeセキュリティ速報 APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html) を参照してください。

### CVE-2024-34102 のホットフィックスを適用する

{{$include /help/_includes/release-notes/2024-06/hotfixes-not-included.md}}

### Platform のアップグレード

* **MariaDB 10.5 のサポート**。 このパッチリリースでは、MariaDB バージョン 10.5 との互換性が導入されています。Adobe Commerceは MariaDB バージョン 10.4 と引き続き互換性がありますが、MariaDB 10.4 のメンテナンスは 2024 年 6 月 18 日（PT）に終了するため、Adobeでは、Adobe Commerce 2.4.5-p8 および今後のすべての 2.4.5 のセキュリティ専用パッチリリースは MariaDB バージョン 10.5 でのみ使用することをお勧めします。<!--AC-11530-->

### その他のセキュリティ機能強化

{{$include /help/_includes/release-notes/2-4-7-security.md}}

## Adobe Commerce 2.4.5-p7

Adobe Commerce 2.4.5-p7 セキュリティリリースは、以前のリリースで特定された脆弱性に対するセキュリティバグ修正を提供します。

セキュリティのバグ修正の最新情報については、[Adobeセキュリティ速報 APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html) を参照してください。

## Adobe Commerce 2.4.5-p6

Adobe Commerce 2.4.5-p6 セキュリティリリースは、以前のリリースで特定された脆弱性に対するセキュリティバグ修正を提供します。 このリリースには、最新のセキュリティのベストプラクティスへのコンプライアンスを向上させるためのセキュリティの機能強化も含まれています。

セキュリティのバグ修正の最新情報については、[Adobeセキュリティ速報 APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html) を参照してください。

### セキュリティのハイライト

このリリースでは、次の 2 つの重要なセキュリティ機能強化が導入されています。

* **生成されないキャッシュキーの動作の変更**:

   * ブロックの生成されないキャッシュキーに、自動的に生成されるキーのプレフィックスとは異なるプレフィックスが含まれるようになりました。 （生成されないキャッシュキーは、テンプレートディレクティブ構文または `setCacheKey` または `setData` メソッドで設定されるキーです）。
   * ブロックの生成されないキャッシュキーには、文字、数字、ハイフン（–）、アンダースコア（_）のみを含める必要があります。<!-- AC-9831 -->

* **自動生成されたクーポンコード数の制限**。 Commerceでは、自動生成されるクーポンコードの数を制限するようになりました。 デフォルトの最大値は 250,000 です。 マーチャントは、新しい **[!UICONTROL Code Quantity Limit]** 設定オプション（**[!UICONTROL Stores]**/**[!UICONTROL Settings:Configuration]**/**[!UICONTROL Customers]**/**[!UICONTROL Promotions]**）を使用して、この新しい制限を制御できます。<!-- AC-8753 -->



## Adobe Commerce 2.4.5-p5

Adobe Commerce 2.4.5-p5 セキュリティリリースは、以前のリリースで特定された脆弱性に対するセキュリティバグ修正を提供します。 このリリースには、最新のセキュリティのベストプラクティスへのコンプライアンスを向上させるためのセキュリティの機能強化も含まれています。

セキュリティのバグ修正の最新情報については、[Adobeセキュリティ速報 APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html) を参照してください。

### セキュリティ ハイライト

このリリースでは、`{BASE-URL}/page_cache/block/esi HTTP` エンドポイントに伴うリスクを軽減するのに役立つ、新しいフルページキャッシュ設定が導入されています。 このエンドポイントは、Commerceのレイアウトハンドルおよびブロック構造から無制限で動的に読み込まれるコンテンツフラグメントをサポートしています。 新しい **[!UICONTROL Handles Param]** 設定では、このエンドポイントの `handles` パラメーターの値を設定します。このパラメーターによって、API あたりの最大ハンドル数が決定されます。 このプロパティのデフォルト値は 100 です。 マーチャントは、管理者（**[!UICONTROL Stores]**/**[!UICONTROL Settings:Configuration]**/**[!UICONTROL System]**/**[!UICONTROL Full Page Cache]**/**[!UICONTROL Handles Param]**）からこの値を変更できます。<!-- AC-9113 -->

### 既知の問題

**問題**:`repo.magento.com` から Composer によるダウンロード中にAdobe Commerceで **wrong checksum** エラーが表示され、パッケージのダウンロードが中断される。 この問題は、プレリリース時に使用可能になったリリースパッケージのダウンロード中に発生する可能性があります。これは、`magento/module-page-cache` パッケージの再パッケージ化が原因です。

**回避策**：ダウンロード中にこのエラーが表示されたマーチャントは、次の手順を実行できます。

1) プロジェクト内に `/vendor` ディレクトリが存在する場合は、削除します。
2) `bin/magento composer update magento/module-page-cache` コマンドを実行します。 このコマンドは、`page cache` パッケージのみを更新します。

チェックサムの問題が解決しない場合は、`bin/magento composer update` コマンドを再実行する前に `composer.lock` ファイルを削除し、すべてのパッケージを更新します。

## Adobe Commerce 2.4.5-p4

Adobe Commerce 2.4.5-p4 セキュリティリリースは、以前のリリースで特定された脆弱性に対するセキュリティバグ修正を提供します。

セキュリティのバグ修正の最新情報については、[Adobeセキュリティ速報 APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html) を参照してください。

### jQuery-UI ライブラリのセキュリティ脆弱性 CVE-2022-31160 を解決するためのパッチを適用する

`jQuery-UI` library バージョン 1.13.1 には、複数のバージョンのAdobe CommerceおよびMagento Open Sourceに影響する既知のセキュリティ脆弱性（CVE-2022-31160）があります。 このライブラリは、Adobe CommerceとMagento Open Source 2.4.4、2.4.5、2.4.6 の依存関係です。影響を受けるデプロイメントを実行しているマーチャントは、ナレッジベース記事の 2.4.4、2.4.5、2.4.6 リリースの [jQuery UI のセキュリティ脆弱性 CVE-2022-31160 の修正で指定されたパッチを適用する必要 ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) あります。

## Adobe Commerce 2.4.5-p3

Adobe Commerce 2.4.5-p3 セキュリティリリースは、以前のリリースで特定された脆弱性に対するセキュリティ修正を提供します。 このリリースには、最新のセキュリティのベストプラクティスへのコンプライアンスを向上させるセキュリティの機能強化も含まれています。

セキュリティのバグ修正の最新情報については、[Adobeセキュリティ速報 ](https://helpx.adobe.com/security/products/magento/apsb23-35.html) を参照してください。

### jQuery-UI ライブラリのセキュリティ脆弱性 CVE-2022-31160 を解決するためのパッチを適用する

`jQuery-UI` library バージョン 1.13.1 には、複数のバージョンのAdobe CommerceおよびMagento Open Sourceに影響する既知のセキュリティ脆弱性（CVE-2022-31160）があります。 このライブラリは、Adobe CommerceとMagento Open Source 2.4.4、2.4.5、2.4.6 の依存関係です。影響を受けるデプロイメントを実行しているマーチャントは、[Query UI セキュリティ脆弱性 CVE-2022-31160 の 2.4.4、2.4.5、2.4.6 リリースの修正 ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) ナレッジベース記事で指定されたパッチを適用する必要があります。

### セキュリティ ハイライト

[`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL クエリと（[`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)） REST エンドポイントのデフォルトの動作が変更されました。 デフォルトでは、API は常に `true` を返すようになりました。 マーチャントは、元の動作を有効にすることができます。これは、メールがデータベースに存在しない場合は `true` を返し、存在する場合は `false` を返します。<!-- AC-6695 -->

### Platform のアップグレード

このリリースのプラットフォームのアップグレードにより、最新のセキュリティのベストプラクティスへのコンプライアンスが向上します。

* **Varnish cache 7.3 のサポート**。 このリリースは、最新バージョンの Varnish Cache 7.3 と互換性があります。6.0.x および 7.2.x バージョンとの互換性は維持されますが、Adobe Commerce 2.4.5-p3 は Varnish Cache バージョン 7.3 またはバージョン 6.0 LTS でのみ使用することをお勧めします。

* **RabbitMQ 3.11 サポート**。 このリリースは最新バージョンのRabbitMQ 3.11 と互換性があります。互換性はRabbitMQ 3.9 に残っており、2023 年 8 月までサポートされますが、Adobe Commerce 2.4.5-p3 はRabbitMQ 3.11 でのみ使用することをお勧めします。

* **JavaScript ライブラリ**。 古いJavaScript ライブラリは、`moment.js` ライブラリ（v2.29.4）、`jQuery UI` ライブラリ（v1.13.2）、`jQuery` validation プラグインライブラリ（v1.19.5）など、最新のマイナーバージョンまたはパッチバージョンにアップグレードされています。

## Adobe Commerce 2.4.5-p2 リリースノート

Adobe Commerce 2.4.5-p2 セキュリティリリースは、以前のリリースで特定された脆弱性に対して 3 つのセキュリティ修正を提供します。

セキュリティのバグ修正の最新情報については、[Adobeセキュリティ速報 APSB23-17](https://helpx.adobe.com/security/products/magento/apsb23-17.html) を参照してください。

## Adobe Commerce 2.4.5-p1

Adobe Commerce 2.4.5-p1 セキュリティリリースでは、前のリリース（Adobe Commerce 2.4.5 およびMagento Open Source 2.4.5）で特定された脆弱性のセキュリティバグが修正されています。

セキュリティのバグ修正の最新情報については、[Adobeセキュリティ速報 APSB22-48](https://helpx.adobe.com/security/products/magento/apsb22-48.html) を参照してください。

セキュリティバグの修正の 1 つに、新しい設定の作成が含まれています。 「**メールが変更された場合、メールによる確認を要求する**」設定を使用すると、管理者ユーザーがメールアドレスを変更したときに、管理者がメールによる確認を要求できます。<!-- AC-6292-->
