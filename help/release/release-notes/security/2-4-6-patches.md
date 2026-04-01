---
title: Adobe Commerce 2.4.6 セキュリティパッチリリースノート
description: Adobe Commerce バージョン 2.4.6のセキュリティパッチリリースに含まれているセキュリティバグの修正、セキュリティの強化、およびその他のセキュリティ関連アップデートについて説明します。
exl-id: cde096ac-d192-490d-873a-475996c474ff
source-git-commit: 2657c83d5467e603a681521886e80592e3b335aa
workflow-type: tm+mt
source-wordcount: '1835'
ht-degree: 0%

---


# Adobe Commerce 2.4.6 セキュリティパッチのリリースノート

{{$include /help/_includes/release-notes/security-patch-intro.md}}

>[!IMPORTANT]
>
>MySQL 8.0は、2026年4月30日からサポート終了（EOS）に到達します。
>
>この日付に続いて、Adobe Commerce 2.4.6では互換性が提供されません。または
>mysql 8.0以降にリリースされたMySQL バージョンをサポートします。Adobeでは
>このAdobeの新しいMySQL メジャーバージョンの検証またはサポートの提供
>Commerce リリースライン。
>
>バージョン 2.4.6を実行しているすべてのAdobe Commerce オンプレミスのお客様は、以下の点に強く同意します。
>データベースサーバーを互換性のあるMariaDB バージョンに移行することをお勧めします。

## 2.4.6-p14

Adobe Commerce 2.4.6-p14のセキュリティリリースには、以前のリリースの2.4.6で特定された脆弱性に対するセキュリティバグの修正が含まれています。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB26-05](https://helpx.adobe.com/security/products/magento/apsb26-05.html)を参照してください。

{{b2b-patches}}

### ハイライト

このリリースには、次のハイライトが含まれています。

#### 2.4.7からの修正をバックポートするためのPHPUnit アップグレードサポート

Adobe Commerce 2.4.6は、セキュア PHPUnit リリースで必要な`sebastian/comparator` ライブラリの新しいバージョンで実行できることが検証されました。 このレビューの一環として、Adobeでは、以前はパッチを適用したPHPUnit バージョンへのアップグレードを制限していた依存関係の制約を評価しました。

お客様は、コンポーザーの要件を調整して、安全なリリースにPHPUnitを安全に更新できるようになりました（例：`sebastian/comparator:^4.0`）。 このアップデートは、Adobe Commerce 2.4.6の機能や想定される動作には影響しません。

#### DHL配送の統合のためのMyDHL REST API サポート

DHL出荷統合では、既存のDHL Express XML統合に加えて、MyDHL REST APIがサポートされるようになりました。 このアップデートはDHLの現在のAPI スタックに合っており、古いXML APIの廃止に備えています。

## 2.4.6-p13

Adobe Commerce 2.4.6-p13のセキュリティリリースには、以前のリリースの2.4.6で特定された脆弱性に対するセキュリティバグの修正が含まれています。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB25-94](https://helpx.adobe.com/security/products/magento/apsb25-94.html)を参照してください。

{{b2b-patches}}

### ハイライト

このリリースには、次のハイライトが含まれています。

{{$include /help/_includes/release-notes/highlights/security-2025-10.md}}

{{oct-2025-backports}}

### 既知の問題

#### Inventory Composer インストーラーパッケージがありません

このバージョンには、`magento/inventory-composer-installer` パッケージは含まれていません。これは、後方互換性のない変更を加えた古いマイナーバージョンからスムーズにアップグレードするために必要です。

2.3から2.4.6-p13にアップグレードする場合は、アップグレードする前に次のコマンドを実行して`magento/inventory-composer-installer` パッケージをインストールします。

```bash
composer require magento/inventory-composer-installer
```

#### チェックアウトページでstatic.min.jsとmixins.min.jsの読み込みに失敗する

{{checkout-page-fails-to-load-static-min-js-and-mixins-min-js}}

## 2.4.6-p12

Adobe Commerce 2.4.6-p12のセキュリティリリースには、以前のリリースの2.4.6で特定された脆弱性に対するセキュリティバグの修正が含まれています。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB25-71](https://helpx.adobe.com/security/products/magento/apsb25-71.html)を参照してください。

{{b2b-patches}}

## 2.4.6-p11

Adobe Commerce 2.4.6-p11 セキュリティリリースでは、以前のリリース 2.4.6で特定された脆弱性に対するセキュリティバグの修正が行われています。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB25-50](https://helpx.adobe.com/security/products/magento/apsb25-50.html)を参照してください。

{{b2b-patches}}

### ハイライト

このリリースには、次のハイライトが含まれています。

* **MariaDB サポート** - MariaDB 10.11のサポートを追加しました。

* **API パフォーマンスの向上** – 以前のセキュリティ パッチの後に導入された一括非同期web API エンドポイントのパフォーマンス低下を解決します。<!-- AC-14078 -->

* **CMS ブロック アクセス修正** – 制限された権限（マーチャンダイジング専用アクセスなど）を持つ管理者ユーザーが[!UICONTROL CMS Blocks]の一覧ページを表示できなかった問題を解決します。

  以前は、以前のセキュリティ パッチをインストールした後、構成パラメーターが欠落しているため、これらのユーザーでエラーが発生していました。<!-- AC-14087 -->

* **Cookie制限の互換性** - フレームワークの`MAX_NUM_COOKIES`定数に関する後方互換性のない変更を解決します。 この更新プログラムは、期待される動作を復元し、cookieの制限と相互作用する拡張機能またはカスタマイズの互換性を確保します。<!-- AC-14475 -->

* **非同期操作** – 以前の顧客の注文を上書きするための非同期操作が制限されています。<!-- AC-13917 -->

## 2.4.6-p10

Adobe Commerce 2.4.6-p10のセキュリティリリースには、以前のリリースの2.4.6で特定された脆弱性に対するセキュリティバグの修正が含まれています。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB25-26](https://helpx.adobe.com/security/products/magento/apsb25-26.html)を参照してください。

{{b2b-patches}}

### ハイライト

{{$include /help/_includes/release-notes/highlights/security-2025-04.md}}

## 2.4.6-p9

Adobe Commerce 2.4.6-p9のセキュリティリリースには、以前のリリースの2.4.6で特定された脆弱性に対するセキュリティバグ修正が含まれています。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB25-08](https://helpx.adobe.com/security/products/magento/apsb25-08.html)を参照してください。

{{b2b-patches}}

### ハイライト

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.6-p8

Adobe Commerce 2.4.6-p8 セキュリティリリースには、以前のリリース 2.4.6で特定された脆弱性に対するセキュリティバグの修正が含まれています。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html)を参照してください。

{{b2b-patches}}

### ハイライト

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

### このリリースに含まれるホットフィックス

{{$include /help/_includes/release-notes/hotfixes/included-2024-10.md}}

## 2.4.6-p7

Adobe Commerce 2.4.6-p7 セキュリティリリースには、以前のリリース 2.4.6で特定された脆弱性に対するセキュリティバグの修正が含まれています。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB24-61](https://helpx.adobe.com/security/products/magento/apsb24-61.html)を参照してください。

### ハイライト

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### このリリースに含まれるホットフィックス

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.6-p6

Adobe Commerce 2.4.6-p6のセキュリティリリースには、以前のリリースの2.4.6で特定された脆弱性に対するセキュリティバグの修正が含まれています。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html)を参照してください。

Commerce バージョン 2.4.6-p6との互換性を保つために、Adobe Commerce B2B拡張機能を持つマーチャントは[B2B バージョン 1.4.2-p1](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1)にアップグレードする必要があります。

### CVE-2024-34102のホットフィックスを適用する

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

Commerce バージョン 2.4.6-p6との互換性を保つために、Adobe Commerce B2B拡張機能を持つマーチャントは[B2B バージョン 1.4.2-p1](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1)にアップグレードする必要があります。

### ハイライト

{{$include /help/_includes/release-notes/highlights/2-4-7-security.md}}

## 2.4.6-p5

Adobe Commerce 2.4.6-p5 セキュリティリリースでは、以前のリリースの2.4.6で特定された脆弱性に対するセキュリティバグ修正が提供されています。

これらの修正に関する最新情報については、[Adobe セキュリティ情報APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html)を参照してください。

## 2.4.6-p4

Adobe Commerce 2.4.6-p4 セキュリティリリースには、以前のリリースで特定された脆弱性に対するセキュリティバグ修正が含まれています。 このリリースには、最新のセキュリティのベストプラクティスへのコンプライアンスを向上させるセキュリティの機能強化も含まれています。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html)を参照してください。

### ハイライト

このリリースでは、次の2つの重要なセキュリティ機能強化が導入されています。

* **生成されていないキャッシュキーの動作に変更が加えられました**:

   * ブロックの非生成キャッシュキーに、自動生成されるキーのプレフィックスとは異なるプレフィックスが含まれるようになりました。 （生成されないキャッシュキーは、テンプレートディレクティブ構文または`setCacheKey`または`setData` メソッドを使用して設定されるキーです）。
   * ブロックの生成されないキャッシュキーには、文字、数字、ハイフン（ – ）、アンダースコア（_）のみを含める必要があります。<!-- AC-9831 -->

* **自動生成されるクーポンコード数の制限**。 Commerceでは、自動生成されるクーポンコードの数が制限されるようになりました。 デフォルトの最大値は250,000です。 マーチャントは、新しい&#x200B;**[!UICONTROL Code Quantity Limit]**&#x200B;設定オプション（**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**）を使用して、この新しい制限を制御できます。<!-- AC-8753 -->

## 2.4.6-p3

Adobe Commerce 2.4.6-p3 セキュリティリリースには、以前のリリースで特定された脆弱性に対するセキュリティバグの修正が含まれています。 このリリースには、最新のセキュリティのベストプラクティスに準拠するためのセキュリティの強化も含まれています。

セキュリティ修正に関する最新情報については、[Adobe セキュリティ情報APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html)を参照してください。

### ハイライト

このリリースでは、`{BASE-URL}/page_cache/block/esi HTTP` エンドポイントに関連するリスクを軽減するのに役立つ、新しいフルページキャッシュ設定設定が導入されました。 このエンドポイントは、Commerceのレイアウトハンドルとブロック構造から無制限に動的に読み込まれるコンテンツフラグメントをサポートしています。 新しい&#x200B;**[!UICONTROL Handles Param]**&#x200B;構成設定では、このエンドポイントの`handles` パラメーターの値が設定され、APIごとに許可されるハンドルの最大数が決定されます。 このプロパティのデフォルト値は100です。 マーチャントは、管理者（**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**）からこの値を変更できます。<!-- AC-9113 -->

### このリリースに含まれるホットフィックス

Adobe Commerce 2.4.6-p3には、パッチ ACSD-51892で修正されたパフォーマンス低下の解決策が含まれています。 このパッチで解決された問題は、マーチャントには影響しません。詳しくは、[ACSD-51892：設定ファイルが複数回ロードされるパフォーマンスの問題](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html) ナレッジベース記事を参照してください。

### 既知の問題

**問題**: Composerによる`wrong checksum`からのダウンロード中に`repo.magento.com` エラーがAdobe Commerceに表示され、パッケージのダウンロードが中断されます。 この問題は、プレリリース期間中に利用可能になったリリースパッケージのダウンロード中に発生する可能性があり、`magento/module-page-cache` パッケージの再パッケージが原因で発生します。

**回避策**：ダウンロード中にこのエラーが表示されるマーチャントは、次の手順を実行できます。

1) プロジェクト内の`/vendor` ディレクトリが存在する場合は、そのディレクトリを削除します。
2) `bin/magento composer update magento/module-page-cache` コマンドを実行します。 このコマンドは、`page cache` パッケージのみを更新します。

チェックサムの問題が解決しない場合は、`composer.lock` コマンドを再実行してすべてのパッケージを更新する前に、`bin/magento composer update` ファイルを削除してください。

## 2.4.6-p2

Adobe Commerce 2.4.6-p2 セキュリティリリースには、以前のリリースで特定された脆弱性に対するセキュリティバグ修正が含まれています。 このリリースでは、最新のセキュリティのベストプラクティスに準拠するためのセキュリティの機能強化も提供されます。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html)を参照してください。

### CVE-2022-31160のホットフィックスを適用する

`jQuery-UI` ライブラリ バージョン 1.13.1には、Adobe CommerceとMagento Open Sourceの複数のバージョンに影響する既知のセキュリティ脆弱性（CVE-2022-31160）があります。 このライブラリは、Adobe CommerceおよびMagento Open Source 2.4.4、2.4.5、および2.4.6の依存関係です。影響を受けるデプロイメントを実行しているマーチャントは、ナレッジベース記事「[jQuery UI セキュリティ脆弱性CVE-2022-31160修正プログラム（2.4.4、2.4.5、2.4.6 リリース ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html)）を適用する必要があります。

### ハイライト

`fastcgi_pass` ファイルの`nginx.sample`の値が、以前の（2.4.6-p1以前）値`fastcgi_backend`に戻されました。 この値は、Adobe Commerce 2.4.6-p1で誤って`php-fpm:9000`に変更されました。

### このリリースに含まれるホットフィックス

Adobe Commerce 2.4.6-p2には、ACSD-51892 パッチで解決されたパフォーマンス低下の解決策が含まれています。 このパッチで解決された問題は、マーチャントには影響しません。詳しくは、[ACSD-51892：設定ファイルが複数回ロードされるパフォーマンスの問題](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html) ナレッジベース記事を参照してください。

## 2.4.6-p1

Adobe Commerce 2.4.6-p1 セキュリティリリースには、以前のリリースで特定された脆弱性に対するセキュリティバグの修正が含まれています。 このリリースには、最新のセキュリティのベストプラクティスに準拠するために、セキュリティの強化とプラットフォームのアップグレードも含まれています。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB23-35](https://helpx.adobe.com/security/products/magento/apsb23-35.html)を参照してください。

### CVE-2022-31160のホットフィックスを適用する

`jQuery-UI` ライブラリ バージョン 1.13.1には、Adobe CommerceとMagento Open Sourceの複数のバージョンに影響する既知のセキュリティ脆弱性（CVE-2022-31160）があります。 このライブラリは、Adobe CommerceおよびMagento Open Source 2.4.4、2.4.5、および2.4.6の依存関係です。影響を受けるデプロイメントを実行している販売者は、ナレッジベース記事[Query UI セキュリティ脆弱性CVE-2022-31160で指定されたパッチを、2.4.4、2.4.5、および2.4.6 リリース ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html)に適用する必要があります。

#### ハイライト

[`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL クエリと（[`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)） REST エンドポイントの既定の動作が変更されました。 デフォルトでは、APIは常に`true`を返すようになりました。 マーチャントは元の動作を有効にできます。つまり、メールがデータベースに存在しない場合は`true`、存在する場合は`false`を返します。<!-- AC-6695 -->

### プラットフォームのアップグレード

このリリースのプラットフォームのアップグレードは、最新のセキュリティのベストプラクティスへのコンプライアンスを向上させます。

* **Varnish キャッシュ 7.3 サポート**。 このリリースは、最新バージョンのVarnish Cache 7.3と互換性があります。互換性は6.0.xおよび7.2.x バージョンで維持されますが、Adobeでは、Varnish Cache バージョン 7.3またはバージョン 6.0 LTSでのみAdobe Commerce 2.4.6-p1を使用することをお勧めします。

* **RabbitMQ 3.11 サポート**。 このリリースは、最新バージョンのRabbitMQ 3.11と互換性があります。互換性は2023年8月までサポートされているRabbitMQ 3.9で維持されますが、AdobeではRabbitMQ 3.11でのみAdobe Commerce 2.4.6-p1を使用することをお勧めします。

* **JavaScript ライブラリ**。 古いJavaScript ライブラリは、`moment.js` ライブラリ （v2.29.4）、`jQuery UI` ライブラリ （v1.13.2）、`jQuery`検証プラグインライブラリ （v1.19.5）など、最新のマイナーバージョンまたはパッチバージョンにアップグレードされました。

### 既知の問題

* `nginx.sample` ファイルが誤って更新され、`fastcgi_pass`の値が`fastcgi_backend`から`php-fpm:9000`に変更されました。 この変更は安全に元に戻されるか、無視されます。<!-- AC-8992 -->

* B2B セキュリティパッケージの依存関係が見つからない場合、B2B拡張機能を1.4.0にインストールまたはアップグレードする際に、次のインストールエラーが発生します。

  ```
  Your requirements could not be resolved to an installable set of packages.
  
    Problem 1
      - Root composer.json requires magento/extension-b2b 1.4.0 -> satisfiable by magento/extension-b2b[1.4.0].
      - magento/extension-b2b 1.4.0 requires magento/security-package-b2b 1.0.4-beta1 -> found magento/security-package-b2b[1.0.4-beta1] but it does not match your minimum-stability.
  
  Installation failed, reverting ./composer.json and ./composer.lock to their original content.
  ```

  この問題は、[安定性タグ ](https://getcomposer.org/doc/04-schema.md#package-links)を持つB2B セキュリティパッケージの手動の依存関係を追加することで解決できます。 詳しくは、[B2B リリースノート ](https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html#known-issue)を参照してください。

<!-- Last updated from includes: 2026-03-19 11:29:47 -->
