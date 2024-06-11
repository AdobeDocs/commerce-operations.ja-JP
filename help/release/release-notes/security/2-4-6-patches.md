---
title: Adobe Commerce 2.4.6 セキュリティパッチのリリースノート
description: Adobe Commerce バージョン 2.4.6 のセキュリティパッチリリースに含まれている、セキュリティバグ修正、セキュリティ機能強化、その他のセキュリティ関連アップデートについて説明します。
exl-id: cde096ac-d192-490d-873a-475996c474ff
source-git-commit: 7705e750a466ab134ae2616a40a32880ee0c45de
workflow-type: tm+mt
source-wordcount: '1134'
ht-degree: 0%

---


# Adobe Commerce 2.4.6 セキュリティパッチのリリースノート

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.6-p6

Adobe Commerce 2.4.6-p6 セキュリティリリースは、以前のリリースの 2.4.6 で特定された脆弱性に対するセキュリティバグ修正を提供します。

セキュリティ バグ修正の最新情報については、を参照してください。 [Adobeセキュリティ速報 APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

## Adobe Commerce 2.4.6-p5

Adobe Commerce 2.4.6-p5 セキュリティリリースは、以前のリリースの 2.4.6 で特定された脆弱性に対するセキュリティバグ修正を提供します。

これらの修正の最新情報については、を参照してください。 [Adobeセキュリティ速報 APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html).

## Adobe Commerce 2.4.6-p4

Adobe Commerce 2.4.6-p4 セキュリティリリースは、以前のリリースで特定された脆弱性に対するセキュリティバグ修正を提供します。 このリリースには、最新のセキュリティのベストプラクティスへのコンプライアンスを向上させるセキュリティの機能強化も含まれています。

セキュリティ バグ修正の最新情報については、を参照してください。 [Adobeセキュリティ速報 APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html).

### セキュリティのハイライト

このリリースでは、次の 2 つの重要なセキュリティ機能強化が導入されています。

* **生成されないキャッシュキーの動作の変更**:

   * ブロックの生成されないキャッシュキーに、自動的に生成されるキーのプレフィックスとは異なるプレフィックスが含まれるようになりました。 （生成されていないキャッシュキーは、テンプレートディレクティブ構文で設定されるキーです。 `setCacheKey` または `setData` メソッド）
   * ブロックの生成されないキャッシュキーに含める文字は、文字、数字、ハイフン（–）、アンダースコア（_）に限られるようになりました。  <!-- AC-9831 -->

* **自動生成されたクーポンコード数の制限**. Commerceでは、自動生成されるクーポンコードの数を制限するようになりました。 デフォルトの最大値は 250,000 です。 マーチャントは、新しいを使用することができます **[!UICONTROL Code Quantity Limit]** 設定オプション （**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**）に設定して、この新しい制限を制御します。 <!-- AC-8753 -->

## Adobe Commerce 2.4.6-p3

Adobe Commerce 2.4.6-p3 セキュリティリリースは、以前のリリースで特定された脆弱性に対するセキュリティバグ修正を提供します。 このリリースには、最新のセキュリティのベストプラクティスへのコンプライアンスを向上させるためのセキュリティの機能強化も含まれています。

セキュリティ修正の最新情報については、を参照してください。 [Adobeセキュリティ速報 APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html).

### セキュリティのハイライト

このリリースでは、に関連するリスクの軽減に役立つ、新しいフルページキャッシュ設定が導入されています `{BASE-URL}/page_cache/block/esi HTTP` エンドポイント。 このエンドポイントは、Commerceのレイアウトハンドルおよびブロック構造から無制限で動的に読み込まれるコンテンツフラグメントをサポートしています。 新しい **[!UICONTROL Handles Param]** 構成設定は、このエンドポイントの値を設定します `handles` パラメーター。API ごとに許可される最大ハンドル数を決定します。 このプロパティのデフォルト値は 100 です。 マーチャントは、この値を管理者（**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**. <!-- AC-9113 -->

### このリリースに含まれるホットフィックス

Adobe Commerce 2.4.6-p3 には、パッチ ACSD-51892 によって修正された、パフォーマンスの低下の解決策が含まれています。 マーチャントは、で説明されるこのパッチによって対処される問題の影響を受けません。 [ACSD-51892：設定ファイルが複数回読み込まれるパフォーマンスの問題](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html) ナレッジベースの記事

### 既知の問題

**問題**:Adobe Commerceにが表示されます `wrong checksum` composer からのダウンロード中にエラーが発生しました `repo.magento.com`、およびパッケージのダウンロードが中断される。 この問題は、プレリリース期間中に使用可能になったリリースパッケージのダウンロード中に発生する可能性があり、の再パッケージ化が原因です `magento/module-page-cache` パッケージ。

**回避策**：ダウンロード中にこのエラーが表示されたマーチャントは、次の手順を実行できます。

1) を削除 `/vendor` プロジェクト内にディレクトリが存在する場合は、そのディレクトリに移動します。
2) を実行 `bin/magento composer update magento/module-page-cache` コマンド。 このコマンドは、 `page cache` パッケージ。

チェックサムの問題が解決しない場合は、 `composer.lock` ファイルを開いてから、 `bin/magento composer update` すべてのパッケージを更新するコマンド。

## 2.4.6-p2

Adobe Commerce 2.4.6-p2 セキュリティリリースは、以前のリリースで特定された脆弱性に対するセキュリティバグ修正を提供します。 また、このリリースでは、最新のセキュリティのベストプラクティスへの準拠を強化するためのセキュリティの機能強化も行っています。

セキュリティ バグ修正の最新情報については、を参照してください。 [Adobeセキュリティ速報 APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html).

### jQuery-UI ライブラリのセキュリティ脆弱性 CVE-2022-31160 を解決するためのパッチを適用する

`jQuery-UI` ライブラリバージョン 1.13.1 には、複数のバージョンのAdobe CommerceおよびMagento Open Sourceに影響する既知のセキュリティ脆弱性（CVE-2022-31160）があります。 このライブラリは、Adobe CommerceとMagento Open Source 2.4.4、2.4.5、2.4.6 の依存関係です。影響を受けるデプロイメントを実行しているマーチャントは、で指定されたパッチを適用する必要があります [2.4.4、2.4.5、2.4.6 リリースの jQuery UI セキュリティ脆弱性 CVE-2022-31160 の修正](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) ナレッジベースの記事

### セキュリティ ハイライト

次の値 `fastcgi_pass` が含まれる `nginx.sample` ファイルは、その前（2.4.6-p1 以前）の値に返されました。 `fastcgi_backend`. この値が誤ってに変更されました `php-fpm:9000` Adobe Commerce 2.4.6-p1 では、

### このリリースに含まれるホットフィックス

Adobe Commerce 2.4.6-p2 には、パッチ ACSD-51892 によって対処されたパフォーマンスの低下の解決が含まれています。 マーチャントは、で説明されるこのパッチによって対処される問題の影響を受けません。 [ACSD-51892：設定ファイルが複数回読み込まれるパフォーマンスの問題](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html) ナレッジベースの記事

## Adobe Commerce 2.4.6-p1

Adobe Commerce 2.4.6-p1 セキュリティリリースは、以前のリリースで特定された脆弱性に対するセキュリティバグ修正を提供します。 このリリースには、最新のセキュリティのベストプラクティスへのコンプライアンスを向上させるためのセキュリティ機能強化とプラットフォームアップグレードも含まれています。

セキュリティ バグ修正の最新情報については、を参照してください。 [Adobeセキュリティ速報 APSB23-35](https://helpx.adobe.com/security/products/magento/apsb23-35.html).

### jQuery-UI ライブラリのセキュリティ脆弱性 CVE-2022-31160 を解決するためのパッチを適用する

`jQuery-UI` ライブラリバージョン 1.13.1 には、複数のバージョンのAdobe CommerceおよびMagento Open Sourceに影響する既知のセキュリティ脆弱性（CVE-2022-31160）があります。 このライブラリは、Adobe CommerceとMagento Open Source 2.4.4、2.4.5、2.4.6 の依存関係です。影響を受けるデプロイメントを実行しているマーチャントは、で指定されたパッチを適用する必要があります [2.4.4、2.4.5、2.4.6 リリースの Query UI セキュリティ脆弱性 CVE-2022-31160 の修正](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) ナレッジベースの記事

#### セキュリティ ハイライト

のデフォルトの動作 [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQLのクエリと（[`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)） REST エンドポイントが変更されました。 デフォルトでは、API は常にを返すようになりました。 `true`. マーチャントは、元の動作（の戻り値）を有効にできます `true` メールがデータベースに存在しない場合。 `false` 存在する場合。 <!-- AC-6695 -->

### Platform のアップグレード

このリリースのプラットフォームのアップグレードにより、最新のセキュリティのベストプラクティスへのコンプライアンスが向上します。

* **Varnish cache 7.3 のサポート**. このリリースは、最新バージョンの Varnish Cache 7.3 と互換性があります。6.0.x および 7.2.x バージョンとの互換性は維持されますが、Adobeでは、Adobe Commerce 2.4.6-p1 を使用して、Varnish Cache バージョン 7.3 またはバージョン 6.0 LTS のみを使用することをお勧めします。

* **RabbitMQ 3.11 サポート**. このリリースは最新バージョンのRabbitMQ 3.11 と互換性があります。互換性はRabbitMQ 3.9 に残っています。このバージョンは 2023 年 8 月までサポートされますが、Adobeでは、Adobe Commerce 2.4.6-p1 をRabbitMQ 3.11 でのみ使用することをお勧めします。

* **JavaScript ライブラリ**. 古い JavaScript ライブラリは、次のような最新のマイナーバージョンまたはパッチバージョンにアップグレードされました `moment.js` ライブラリ（v2.29.4）、 `jQuery UI` ライブラリ（v1.13.2）、 `jQuery` 検証プラグインライブラリ（v1.19.5）。

### 既知の問題

* この `nginx.sample` ファイルが誤って、の値を変更する変更で更新されました `fastcgi_pass` から `fastcgi_backend` 対象： `php-fpm:9000`. この変更は、元に戻しても無視しても問題ありません。 <!-- AC-8992 -->

* B2B セキュリティパッケージの依存関係が見つからない場合、B2B 拡張機能をインストールまたは 1.4.0 にアップグレードする際に、次のインストールエラーが発生します。

  ```terminal
  Your requirements could not be resolved to an installable set of packages.
  
    Problem 1
      - Root composer.json requires magento/extension-b2b 1.4.0 -> satisfiable by magento/extension-b2b[1.4.0].
      - magento/extension-b2b 1.4.0 requires magento/security-package-b2b 1.0.4-beta1 -> found magento/security-package-b2b[1.0.4-beta1] but it does not match your minimum-stability.
  
  Installation failed, reverting ./composer.json and ./composer.lock to their original content.
  ```

  この問題は、 [安定性タグ](https://getcomposer.org/doc/04-schema.md#package-links). 詳しくは、を参照してください [B2B リリースノート](https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html#known-issue).
