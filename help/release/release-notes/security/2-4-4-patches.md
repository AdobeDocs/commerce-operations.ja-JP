---
title: Adobe Commerce 2.4.4 セキュリティパッチのリリースノート
description: Adobe Commerce バージョン 2.4.4 のセキュリティパッチリリースに含まれている、セキュリティバグ修正、セキュリティ機能強化、その他のセキュリティ関連アップデートについて説明します。
exl-id: 136d7090-6bf2-41e3-8445-b07bdc67f12b
source-git-commit: e1c5b5e5c1a8800aa5aa2657060f61c16743cbda
workflow-type: tm+mt
source-wordcount: '1337'
ht-degree: 0%

---

# Adobe Commerce 2.4.4 セキュリティパッチのリリースノート

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## 2.4.4-p8

Adobe Commerce 2.4.4-p8 セキュリティリリースは、Adobe Commerce 2.4.4 デプロイメントのセキュリティバグを修正します。 これらのアップデートにより、以前のリリースで特定された脆弱性が修正されます。

セキュリティ バグ修正の最新情報については、を参照してください。 [Adobeセキュリティ速報 APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html).

## 2.4.4-p7

Adobe Commerce 2.4.4-p7 セキュリティリリースは、以前のリリースで特定された脆弱性に対するセキュリティバグ修正を提供します。 このリリースには、最新のセキュリティのベストプラクティスへのコンプライアンスを向上させるセキュリティの機能強化も含まれています。

セキュリティ バグ修正の最新情報については、を参照してください。 [Adobeセキュリティ速報 APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html).

### セキュリティのハイライト

このリリースでは、次の 2 つの重要なセキュリティ機能強化が導入されています。

* **生成されないキャッシュキーの動作の変更**:

   * ブロックの生成されないキャッシュキーに、自動的に生成されるキーのプレフィックスとは異なるプレフィックスが含まれるようになりました。 （生成されていないキャッシュキーは、テンプレートディレクティブ構文で設定されるキーです。 `setCacheKey` または `setData` メソッド）
   * ブロックの生成されないキャッシュキーに含める文字は、文字、数字、ハイフン（–）、アンダースコア（_）に限られるようになりました。 <!-- AC-9831 -->

* **自動生成されたクーポンコード数の制限**. Commerceでは、自動生成されるクーポンコードの数を制限するようになりました。 デフォルトの最大値は 250,000 です。 マーチャントは、新しいを使用することができます **[!UICONTROL Code Quantity Limit]** 設定オプション （**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**）に設定して、この新しい制限を制御します。 <!-- AC-8753 -->

## 2.4.4-p6

Adobe Commerce 2.4.4-p6 セキュリティリリースは、以前のリリースで特定された脆弱性に対するセキュリティバグ修正を提供します。 このリリースには、最新のセキュリティのベストプラクティスへのコンプライアンスを向上させるセキュリティの機能強化も含まれています。

セキュリティ バグ修正の最新情報については、を参照してください。 [Adobeセキュリティ速報 APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html).

このリリースには、最新のセキュリティのベストプラクティスへのコンプライアンスを向上させるセキュリティの機能強化も含まれています。

### セキュリティ ハイライト

このリリースでは、に関連するリスクの軽減に役立つ、新しいフルページキャッシュ設定が導入されています `{BASE-URL}/page_cache/block/esi HTTP` エンドポイント。 このエンドポイントは、Commerce レイアウトハンドルおよびブロック構造から無制限で動的に読み込まれるコンテンツフラグメントをサポートします。 新しい **[!UICONTROL Handles Param]** 構成設定は、このエンドポイントの値を設定します `handles` パラメーター。API ごとに許可される最大ハンドル数を決定します。 このプロパティのデフォルト値は 100 です。 マーチャントは、この値を管理者（**[!UICONTROL Stores]** > **[!UICONTROL Settings: Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**）に設定します。 <!-- AC-9113 -->

### 既知の問題

**問題**:Adobe Commerceにが表示されます **誤ったチェックサム** composer からのダウンロード中にエラーが発生しました `repo.magento.com`、およびパッケージのダウンロードが中断される。 この問題は、プレリリース時に使用可能になったリリースパッケージのダウンロード中に発生する可能性があり、の再パッケージ化が原因です `magento/module-page-cache` パッケージ。

**回避策**：ダウンロード中にこのエラーが表示されたマーチャントは、次の手順を実行できます。

1) を削除 `/vendor` プロジェクト内にディレクトリが存在する場合は、そのディレクトリに移動します。
2) を実行 `bin/magento composer update magento/module-page-cache` コマンド。 このコマンドは、 `page cache` パッケージ。

チェックサムの問題が解決しない場合は、 `composer.lock` ファイルを開いてから、 `bin/magento composer update` すべてのパッケージを更新するコマンド。

## 2.4.4-p5

Adobe Commerce 2.4.4-p5 セキュリティリリースは、以前のリリースで特定された脆弱性に対するセキュリティバグ修正を提供します。

セキュリティ バグ修正の最新情報については、を参照してください。 [Adobeセキュリティ速報 APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html).

### jQuery-UI ライブラリのセキュリティ脆弱性 CVE-2022-31160 を解決するためのパッチを適用する

`jQuery-UI` ライブラリバージョン 1.13.1 には、複数のバージョンのAdobe CommerceおよびMagento Open Sourceに影響する既知のセキュリティ脆弱性（CVE-2022-31160）があります。 このライブラリは、Adobe CommerceとMagento Open Source 2.4.4、2.4.5、2.4.6 の依存関係です。影響を受けるデプロイメントを実行しているマーチャントは、で指定されたパッチを適用する必要があります [2.4.4、2.4.5、2.4.6 リリースの jQuery UI セキュリティ脆弱性 CVE-2022-31160 の修正](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) ナレッジベースの記事

## 2.4.4-p4

Adobe Commerce 2.4.4-p4 セキュリティリリースは、以前のリリースで特定された脆弱性に対するセキュリティバグ修正を提供します。 このリリースには、最新のセキュリティのベストプラクティスへのコンプライアンスを向上させるためのセキュリティ機能強化とプラットフォームアップグレードも含まれています。

セキュリティ バグ修正の最新情報については、を参照してください。 [Adobeセキュリティ速報 APSB23-35](https://helpx.adobe.com/security/products/magento/apsb23-35.html).

### jQuery-UI ライブラリのセキュリティ脆弱性 CVE-2022-31160 を解決するためのパッチを適用する

`jQuery-UI` ライブラリバージョン 1.13.1 には、複数のバージョンのAdobe CommerceおよびMagento Open Sourceに影響する既知のセキュリティ脆弱性（CVE-2022-31160）があります。 このライブラリは、Adobe CommerceとMagento Open Source 2.4.4、2.4.5、2.4.6 の依存関係です。影響を受けるデプロイメントを実行しているマーチャントは、で指定されたパッチを適用する必要があります [2.4.4、2.4.5、2.4.6 リリースの jQuery UI セキュリティ脆弱性 CVE-2022-31160 の修正](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) ナレッジベースの記事

### セキュリティ ハイライト

のデフォルトの動作 [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQLのクエリと（[`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)） REST エンドポイントが変更されました。 デフォルトでは、API は常にを返すようになりました。 `true`. マーチャントは、元の動作（の戻り値）を有効にできます `true` メールがデータベースに存在しない場合。 `false` 存在する場合。 <!-- AC-6695 -->

### Platform のアップグレード

このリリースのプラットフォームのアップグレードにより、最新のセキュリティのベストプラクティスへのコンプライアンスが向上します。

* **Varnish cache 7.3 のサポート**. このリリースは、最新バージョンの Varnish Cache 7.3 と互換性があります。6.0.x および 7u.2.x バージョンとの互換性は維持されますが、Adobeでは、Adobe Commerce 2.4.4-p4 を Varnish Cache バージョン 7.3 またはバージョン 6.0 LTS でのみ使用することをお勧めします。

* **RabbitMQ 3.11 サポート**. このリリースは最新バージョンのRabbitMQ 3.11 と互換性があります。互換性はRabbitMQ 3.9 に残っています。このバージョンは 2023 年 8 月までサポートされます。ただし、Adobeでは、Adobe Commerce 2.4.4-p4 をRabbitMQ 3.11 でのみ使用することをお勧めします。

* **JavaScript ライブラリ**. 古い JavaScript ライブラリは、次のような最新のマイナーバージョンまたはパッチバージョンにアップグレードされました `moment.js` ライブラリ（v2.29.4）、 `jQuery UI` ライブラリ（v1.13.2）、 `jQuery` 検証プラグインライブラリ（v1.19.5）。

## 2.4.4-p3

Adobe Commerce 2.4.4-p3 セキュリティリリースは、以前のリリースで特定された脆弱性に対するセキュリティバグ修正を提供します。

セキュリティ バグ修正の最新情報については、を参照してください。 [Adobeセキュリティ速報 APSB23-17](https://helpx.adobe.com/security/products/magento/apsb23-17.html).

## 2.4.4-p2

Adobe Commerce 2.4.4-p2 セキュリティリリースは、以前のリリースで特定された脆弱性の修正を提供します。 1 つの修正には、新しい設定の作成が含まれます。 この **E メールが変更された場合、E メールによる確認を要求する** 構成設定を使用すると、管理者ユーザーがメールアドレスを変更したときに、管理者がメールで確認を要求できます。 <!-- AC-6292-->

セキュリティ バグ修正の最新情報については、を参照してください。 [Adobeセキュリティ速報 APSB22-48](https://helpx.adobe.com/security/products/magento/apsb22-48.html).

### AC-3022.patch を適用して、引き続き配送業者として DHL を提供します

DHL ではスキーマバージョン 6.2 を導入しており、近い将来、スキーマバージョン 6.0 を廃止する予定です。 DHL 統合をサポートするAdobe Commerce 2.4.4 以前のバージョンは、バージョン 6.0 のみをサポートしています。これらのリリースをデプロイするマーチャントは、 `AC-3022.patch` 早期に DHL を配送業者として提供し続けることができます。 を参照してください。 [配送業者として DHL を引き続き提供するためのパッチを適用する](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier?_ga=2.201689433.994140970.1661546561-1218319047.1534347481) パッチのダウンロードとインストールについては、ナレッジベースの記事を参照してください。

## 2.4.4-p1

Adobe Commerce 2.4.4-p1 セキュリティリリースは、以前のリリースで特定された脆弱性の修正を提供します。 このリリースには、最新のセキュリティのベストプラクティスへのコンプライアンスを向上させるためのセキュリティの機能強化も含まれています。

セキュリティ バグ修正の最新情報については、を参照してください。 [Adobeセキュリティ速報](https://helpx.adobe.com/security/products/magento/apsb22-38.html).t

### 適用 `AC-3022.patch` 引き続き DHL を配送業者として提供するため

DHL ではスキーマバージョン 6.2 を導入しており、近い将来、スキーマバージョン 6.0 を廃止する予定です。 DHL 統合をサポートするAdobe Commerce 2.4.4 以前のバージョンは、バージョン 6.0 のみをサポートしています。これらのリリースをデプロイするマーチャントは、 `AC-3022.patch` 早期に DHL を配送業者として提供し続けることができます。 を参照してください。 [配送業者として DHL を引き続き提供するためのパッチを適用する](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) パッチのダウンロードとインストールについては、ナレッジベースの記事を参照してください。

### セキュリティのハイライト

このリリースのセキュリティの強化により、次のような最新のセキュリティのベストプラクティスへのコンプライアンスが向上しています。

* ACL リソースがインベントリに追加されました。
* 在庫テンプレートのセキュリティが強化されました。

### 既知の問題

**問題**:Web API および統合テストを 2.4.4-p1 パッケージで実行すると、次のエラーが表示されます。 `[2022-06-14T16:58:23.694Z] PHP Fatal error:  Declaration of Magento\TestFramework\ErrorLog\Logger::addRecord(int $level, string $message, array $context = []): bool must be compatible with Monolog\Logger::addRecord(int $level, string $message, array $context = [], ?Monolog\DateTimeImmutable $datetime = null): bool in /var/www/html/dev/tests/integration/framework/Magento/TestFramework/ErrorLog/Logger.php on line 69`. **回避策**：を実行して、以前のバージョンの Monolog をインストールします `require monolog/monolog:2.6.0` コマンド。 <!-- AC-3651-->

**問題**：マーチャントは、Adobe Commerce 2.4.4 からAdobe Commerce 2.4.4-p1 へのアップグレード中に、パッケージバージョンのダウングレードに関する通知に気付く場合があります。 これらのメッセージは無視できます。 パッケージバージョンの不一致は、パッケージ生成時の異常値が原因で発生します。 製品の機能に影響はありません。 を参照してください。 [2.4.4 から 2.4.4-p1 へのアップグレード後にダウングレードされたパッケージ](https://support.magento.com/hc/en-us/articles/8214752983949) 影響を受けるシナリオと回避策のディスカッションについては、ナレッジベースの記事を参照してください。

