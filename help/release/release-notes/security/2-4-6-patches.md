---
title: Adobe Commerce 2.4.6 セキュリティパッチのリリースノート
description: Adobe Commerce バージョン 2.4.6 のセキュリティパッチリリースに含まれている、セキュリティバグ修正、セキュリティ機能強化、その他のセキュリティ関連アップデートについて説明します。
exl-id: cde096ac-d192-490d-873a-475996c474ff
source-git-commit: cb4f388c90902c2fe1df4a5d84841280fa740104
workflow-type: tm+mt
source-wordcount: '1243'
ht-degree: 0%

---


# Adobe Commerce 2.4.6 セキュリティパッチのリリースノート

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## 2.4.6-p8

Adobe Commerce 2.4.6-p8 セキュリティリリースは、2.4.6 の以前のリリースで特定された脆弱性に対するセキュリティバグ修正を提供します。

セキュリティのバグ修正の最新情報については、[Adobeセキュリティ速報 APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html) を参照してください。

{{b2b-patches}}

### ハイライト

{{$include /help/_includes/release-notes/2024-10/security-foo.md}}

### このリリースに含まれるホットフィックス

{{$include /help/_includes/release-notes/2024-10/hotfixes-included-foo.md}}

## 2.4.6-p7

Adobe Commerce 2.4.6-p7 セキュリティリリースは、2.4.6 の以前のリリースで特定された脆弱性に対するセキュリティバグ修正を提供します。

セキュリティのバグ修正の最新情報については、[Adobeセキュリティ速報 APSB24-61](https://helpx.adobe.com/security/products/magento/apsb24-61.html) を参照してください。

### ハイライト

{{$include /help/_includes/release-notes/2024-08/security.md}}

### このリリースに含まれるホットフィックス

{{$include /help/_includes/release-notes/2024-08/hotfixes-included.md}}

## 2.4.6-p6

Adobe Commerce 2.4.6-p6 セキュリティリリースは、以前のリリースの 2.4.6 で特定された脆弱性に対するセキュリティバグ修正を提供します。

セキュリティのバグ修正の最新情報については、[Adobeセキュリティ速報 APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html) を参照してください。

Commerce バージョン 2.4.6-p6 との互換性を保つには、Adobe Commerce B2B 拡張機能を持つマーチャントが、[B2B バージョン 1.4.2-p1](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1) にアップグレードする必要があります。

### CVE-2024-34102 のホットフィックスを適用する

{{$include /help/_includes/release-notes/2024-06/hotfixes-not-included.md}}

Commerce バージョン 2.4.6-p6 との互換性を保つには、Adobe Commerce B2B 拡張機能を持つマーチャントが、[B2B バージョン 1.4.2-p1](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1) にアップグレードする必要があります。

### ハイライト

{{$include /help/_includes/release-notes/2-4-7-security.md}}

## 2.4.6-p5

Adobe Commerce 2.4.6-p5 セキュリティリリースは、以前のリリースの 2.4.6 で特定された脆弱性に対するセキュリティバグ修正を提供します。

これらの修正の最新情報については、[Adobeセキュリティ速報 APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html) を参照してください。

## 2.4.6-p4

Adobe Commerce 2.4.6-p4 セキュリティリリースは、以前のリリースで特定された脆弱性に対するセキュリティバグ修正を提供します。 このリリースには、最新のセキュリティのベストプラクティスへのコンプライアンスを向上させるセキュリティの機能強化も含まれています。

セキュリティのバグ修正の最新情報については、[Adobeセキュリティ速報 APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html) を参照してください。

### ハイライト

このリリースでは、次の 2 つの重要なセキュリティ機能強化が導入されています。

* **生成されないキャッシュキーの動作の変更**:

   * ブロックの生成されないキャッシュキーに、自動的に生成されるキーのプレフィックスとは異なるプレフィックスが含まれるようになりました。 （生成されないキャッシュキーは、テンプレートディレクティブ構文または `setCacheKey` または `setData` メソッドで設定されるキーです）。
   * ブロックの生成されないキャッシュキーには、文字、数字、ハイフン（–）、アンダースコア（_）のみを含める必要があります。<!-- AC-9831 -->

* **自動生成されたクーポンコード数の制限**。 Commerceでは、自動生成されるクーポンコードの数を制限するようになりました。 デフォルトの最大値は 250,000 です。 マーチャントは、新しい **[!UICONTROL Code Quantity Limit]** 設定オプション（**[!UICONTROL Stores]**/**[!UICONTROL Settings:Configuration]**/**[!UICONTROL Customers]**/**[!UICONTROL Promotions]**）を使用して、この新しい制限を制御できます。<!-- AC-8753 -->

## 2.4.6-p3

Adobe Commerce 2.4.6-p3 セキュリティリリースは、以前のリリースで特定された脆弱性に対するセキュリティバグ修正を提供します。 このリリースには、最新のセキュリティのベストプラクティスへのコンプライアンスを向上させるためのセキュリティの機能強化も含まれています。

セキュリティの修正に関する最新情報については、[Adobeセキュリティ速報 APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html) を参照してください。

### ハイライト

このリリースでは、`{BASE-URL}/page_cache/block/esi HTTP` エンドポイントに伴うリスクを軽減するのに役立つ、新しいフルページキャッシュ設定が導入されています。 このエンドポイントは、Commerceのレイアウトハンドルおよびブロック構造から無制限で動的に読み込まれるコンテンツフラグメントをサポートしています。 新しい **[!UICONTROL Handles Param]** 設定では、このエンドポイントの `handles` パラメーターの値を設定します。このパラメーターによって、API あたりの最大ハンドル数が決定されます。 このプロパティのデフォルト値は 100 です。 マーチャントは、管理者（**[!UICONTROL Stores]**/**[!UICONTROL Settings:Configuration]**/**[!UICONTROL System]**/**[!UICONTROL Full Page Cache]**/**[!UICONTROL Handles Param]**）からこの値を変更できます。<!-- AC-9113 -->

### このリリースに含まれるホットフィックス

Adobe Commerce 2.4.6-p3 には、パッチ ACSD-51892 によって修正された、パフォーマンスの低下の解決策が含まれています。 マーチャントは、このパッチで対処される問題の影響を受けません。詳しくは、ナレッジベースの記事 [ACSD-51892：設定ファイルが複数回読み込まれるパフォーマンスの問題 ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html) を参照してください。

### 既知の問題

**問題**:`repo.magento.com` から Composer によるダウンロード中にAdobe Commerceに `wrong checksum` エラーが表示され、パッケージのダウンロードが中断される。 この問題は、プレリリース期間中に使用可能になったリリースパッケージのダウンロード中に発生する可能性があり、`magento/module-page-cache` パッケージの再パッケージ化が原因です。

**回避策**：ダウンロード中にこのエラーが表示されたマーチャントは、次の手順を実行できます。

1) プロジェクト内に `/vendor` ディレクトリが存在する場合は、削除します。
2) `bin/magento composer update magento/module-page-cache` コマンドを実行します。 このコマンドは、`page cache` パッケージのみを更新します。

チェックサムの問題が解決しない場合は、`bin/magento composer update` コマンドを再実行する前に `composer.lock` ファイルを削除し、すべてのパッケージを更新します。

## 2.4.6-p2

Adobe Commerce 2.4.6-p2 セキュリティリリースは、以前のリリースで特定された脆弱性に対するセキュリティバグ修正を提供します。 また、このリリースでは、最新のセキュリティのベストプラクティスへの準拠を強化するためのセキュリティの機能強化も行っています。

セキュリティのバグ修正の最新情報については、[Adobeセキュリティ速報 APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html) を参照してください。

### CVE-2022-31160 のホットフィックスを適用する

`jQuery-UI` library バージョン 1.13.1 には、複数のバージョンのAdobe CommerceおよびMagento Open Sourceに影響する既知のセキュリティ脆弱性（CVE-2022-31160）があります。 このライブラリは、Adobe CommerceとMagento Open Source 2.4.4、2.4.5、2.4.6 の依存関係です。影響を受けるデプロイメントを実行しているマーチャントは、ナレッジベース記事の 2.4.4、2.4.5、2.4.6 リリースの [jQuery UI のセキュリティ脆弱性 CVE-2022-31160 の修正で指定されたパッチを適用する必要 ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) あります。

### ハイライト

`nginx.sample` ファイルの `fastcgi_pass` の値は、その前（2.4.6-p1 以前）の `fastcgi_backend` の値に返されました。 Adobe Commerce 2.4.6-p1 では、この値が誤って `php-fpm:9000` に変更されていました。

### このリリースに含まれるホットフィックス

Adobe Commerce 2.4.6-p2 には、パッチ ACSD-51892 によって対処されたパフォーマンスの低下の解決が含まれています。 マーチャントは、このパッチで対処される問題の影響を受けません。詳しくは、ナレッジベースの記事 [ACSD-51892：設定ファイルが複数回読み込まれるパフォーマンスの問題 ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html) を参照してください。

## 2.4.6-p1

Adobe Commerce 2.4.6-p1 セキュリティリリースは、以前のリリースで特定された脆弱性に対するセキュリティバグ修正を提供します。 このリリースには、最新のセキュリティのベストプラクティスへのコンプライアンスを向上させるためのセキュリティ機能強化とプラットフォームアップグレードも含まれています。

セキュリティのバグ修正の最新情報については、[Adobeセキュリティ速報 APSB23-35](https://helpx.adobe.com/security/products/magento/apsb23-35.html) を参照してください。

### CVE-2022-31160 のホットフィックスを適用する

`jQuery-UI` library バージョン 1.13.1 には、複数のバージョンのAdobe CommerceおよびMagento Open Sourceに影響する既知のセキュリティ脆弱性（CVE-2022-31160）があります。 このライブラリは、Adobe CommerceとMagento Open Source 2.4.4、2.4.5、2.4.6 の依存関係です。影響を受けるデプロイメントを実行しているマーチャントは、[Query UI セキュリティ脆弱性 CVE-2022-31160 の 2.4.4、2.4.5、2.4.6 リリースの修正 ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) ナレッジベース記事で指定されたパッチを適用する必要があります。

#### ハイライト

[`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL クエリと（[`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)） REST エンドポイントのデフォルトの動作が変更されました。 デフォルトでは、API は常に `true` を返すようになりました。 マーチャントは、元の動作を有効にすることができます。これは、メールがデータベースに存在しない場合は `true` を返し、存在する場合は `false` を返します。<!-- AC-6695 -->

### Platform のアップグレード

このリリースのプラットフォームのアップグレードにより、最新のセキュリティのベストプラクティスへのコンプライアンスが向上します。

* **Varnish cache 7.3 のサポート**。 このリリースは、最新バージョンの Varnish Cache 7.3 と互換性があります。6.0.x および 7.2.x バージョンとの互換性は維持されますが、Adobeでは、Adobe Commerce 2.4.6-p1 を使用して、Varnish Cache バージョン 7.3 またはバージョン 6.0 LTS のみを使用することをお勧めします。

* **RabbitMQ 3.11 サポート**。 このリリースは最新バージョンのRabbitMQ 3.11 と互換性があります。互換性はRabbitMQ 3.9 に残っています。このバージョンは 2023 年 8 月までサポートされますが、Adobeでは、Adobe Commerce 2.4.6-p1 をRabbitMQ 3.11 でのみ使用することをお勧めします。

* **JavaScript ライブラリ**。 古いJavaScript ライブラリは、`moment.js` ライブラリ（v2.29.4）、`jQuery UI` ライブラリ（v1.13.2）、`jQuery` validation プラグインライブラリ（v1.19.5）など、最新のマイナーバージョンまたはパッチバージョンにアップグレードされています。

### 既知の問題

* `nginx.sample` ファイルが、`fastcgi_pass` の値を `fastcgi_backend` から `php-fpm:9000` に変更する変更で誤って更新されました。 この変更は、元に戻しても無視しても問題ありません。<!-- AC-8992 -->

* B2B セキュリティパッケージの依存関係が見つからない場合、B2B 拡張機能をインストールまたは 1.4.0 にアップグレードする際に、次のインストールエラーが発生します。

  ```
  Your requirements could not be resolved to an installable set of packages.
  
    Problem 1
      - Root composer.json requires magento/extension-b2b 1.4.0 -> satisfiable by magento/extension-b2b[1.4.0].
      - magento/extension-b2b 1.4.0 requires magento/security-package-b2b 1.0.4-beta1 -> found magento/security-package-b2b[1.0.4-beta1] but it does not match your minimum-stability.
  
  Installation failed, reverting ./composer.json and ./composer.lock to their original content.
  ```

  この問題は、[ 安定タグ ](https://getcomposer.org/doc/04-schema.md#package-links) を備えた B2B セキュリティパッケージの手動依存関係を追加することで解決できます。 詳しくは、[B2B リリースノート ](https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html#known-issue) を参照してください。
