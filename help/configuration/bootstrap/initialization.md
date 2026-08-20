---
title: アプリケーションの初期化とブートストラップ
description: Commerce アプリケーションの初期化とブートストラップロジックについて説明します。
feature: Configuration, Install, Media
exl-id: 46d1ffc0-7870-4dd1-beec-0a9ff858ab62
source-git-commit: b378f6da50e40b1868ae759cc7f3523a7e3ced4b
workflow-type: tm+mt
source-wordcount: '901'
ht-degree: 0%

---

# 初期化とブートストラップの概要

Commerce アプリケーションを実行するには、[pub/index.php](https://github.com/magento/magento2/tree/2.4.8/pub/index.php)に次のアクションが実装されます。

- 環境にデプロイされたCommerce バージョンの[app/bootstrap.php](https://github.com/magento/magento2/blob/2.4.8/app/bootstrap.php) ファイルを含めます。 このファイルは、エラー処理、オートローダの初期化、プロファイルオプションの設定、デフォルトのタイムゾーンの設定など、重要な初期化ルーチンを実行します。
- [\Magento\Framework\App\Bootstrap.php](https://github.com/magento/magento2/tree/2.4.8/lib/internal/Magento/Framework/App/Bootstrap.php) <!-- It requires initialization parameters to be specified in constructor. Normally, the $_SERVER super-global variable is supposed to be passed there. -->のインスタンスを作成します
- Commerce アプリケーション インスタンスを作成します：[\Magento\Framework\AppInterface](https://github.com/magento/magento2/tree/2.4.8/lib/internal/Magento/Framework/AppInterface.php)
- Commerceを実行

## Bootstrap run logic

[&#x200B; ブートストラップオブジェクト &#x200B;](https://github.com/magento/magento2/tree/2.4.8/app/bootstrap.php)は、次のアルゴリズムを使用してCommerce アプリケーションを実行します。

1. エラーハンドラーを初期化します。
1. どこでも使用され、環境の影響を受ける[object manager](https://github.com/magento/magento2/tree/2.4.8/lib/internal/Magento/Framework/ObjectManager)と基本的な共有サービスを作成します。 環境パラメーターは、これらのオブジェクトに適切に挿入されます。
1. メンテナンスモードが&#x200B;_not_&#x200B;有効になっていることを確認します。有効になっていない場合は終了します。
1. Commerce アプリケーションがインストールされていることを確認します。インストールしていない場合は終了します。
1. Commerce アプリケーションを起動します。

   アプリケーションの起動中に検出されない例外は、例外を処理するために使用できる`catchException()` メソッドでCommerceに自動的に渡されます。 後者は`true`または`false`のいずれかを返す必要があります。

   - `true`の場合：Commerceは例外を正常に処理しました。 他に何もする必要はありません。
   - `false`: （またはその他の空の結果）の場合、Commerceは例外を処理しませんでした。 bootstrap オブジェクトは、デフォルトの例外処理サブルーチンを実行します。

1. アプリケーションオブジェクトが提供する応答を送信します。

   >[!INFO]
   >
   >Commerce アプリケーションがインストールされていて、メンテナンスモードになっていないというアサーションは、`\Magento\Framework\App\Bootstrap` クラスのデフォルトの動作です。 ブートストラップオブジェクトの作成時に、エントリポイントスクリプトを使用して変更できます。

   ブートストラップオブジェクトを変更するエントリポイントスクリプトの例：

   ```php
   <?php
   use Magento\Framework\App\Bootstrap;
   require __DIR__ . '/app/bootstrap.php';
   
   $params = $_SERVER;
   $params[Bootstrap::PARAM_REQUIRE_MAINTENANCE] = true; // default false
   $params[Bootstrap::PARAM_REQUIRE_IS_INSTALLED] = false; // default true
   $bootstrap = Bootstrap::create(BP, $params);
   
   /** @var \Magento\Framework\App\Http $app */
   $app = $bootstrap->createApplication('Magento\Framework\App\Http');
   $bootstrap->run($app);
   ```

## デフォルトの例外処理

bootstrap オブジェクトは、次のように、Commerce アプリケーションが捕捉されない例外を処理する方法を指定します。

- [開発者モード &#x200B;](../bootstrap/application-modes.md#developer-mode)では、例外をそのまま表示します。
- 他のモードでは、例外をログに記録し、一般的なエラーメッセージを表示しようとします。
- エラーコード `1`でCommerceを終了します

## エントリポイントアプリケーション

次のエントリポイントアプリケーション（Commerceで定義されたアプリケーションで、web サーバーがディレクトリインデックスとして使用するもの）があります。

### HTTP エントリポイント

[\Magento\Framework\App\Http](https://github.com/magento/magento2/tree/2.4.8/lib/internal/Magento/Framework/App/Http)は次のように動作します。

1. [&#x200B; アプリケーション領域](https://developer.adobe.com/commerce/php/architecture/modules/areas)を決定します。
1. コントローラのアクションを検索して実行するために、フロント コントローラとルーティング システムを開始します。
1. HTTP応答オブジェクトを使用して、コントローラーアクションから取得した結果を返します。
1. エラー処理（次の優先順位付け）:

   1. [開発者モード &#x200B;](../bootstrap/application-modes.md#developer-mode)を使用している場合：
      - Commerce アプリケーションがインストールされていない場合は、Setup Wizardにリダイレクトします。
      - Commerce アプリケーションがインストールされている場合は、エラーとHTTP ステータスコード 500 （内部サーバーエラー）が表示されます。
   1. Commerce アプリケーションがメンテナンスモードの場合は、HTTP ステータスコード 503 （サービス利用不可）のユーザーフレンドリーな「サービス利用不可」ランディングページを表示します。
   1. Commerce アプリケーションが&#x200B;_not_ インストールされている場合は、セットアップ ウィザードにリダイレクトします。
   1. セッションが無効な場合は、ホームページにリダイレクトします。
   1. 他のアプリケーション初期化エラーがある場合は、HTTP ステータスコード 404 （Not Found）のユーザーフレンドリーな「ページが見つかりません」ページを表示します。
   1. 他のエラーの場合は、HTTP応答503のユーザーフレンドリーな「サービス利用不可」ページを表示し、エラーレポートを生成して、ページにIDを表示します。

### 静的リソースエントリポイント

[\Magento\Framework\App\StaticResource](https://github.com/magento/magento2/tree/2.4.8/lib/internal/Magento/Framework/App/StaticResource.php)は、静的リソース （CSS、JavaScript、画像など）を取得するためのアプリケーションです。 リソースがリクエストされるまで、静的リソースを使用したアクションは延期されます。

>[!INFO]
>
>静的ビューファイルのエントリポイントは、[実稼動モード &#x200B;](application-modes.md#production-mode)では、サーバー上の潜在的な悪用を避けるために使用されません。 実稼動モードでは、Commerce アプリケーションは、すべての必要なリソースが`<your Commerce install dir>/pub/static` ディレクトリに存在することを想定しています。

デフォルトまたは開発者モードでは、存在しない静的リソースのリクエストは、適切な`.htaccess`によって指定された書き換えルールに従って、静的エントリポイントにリダイレクトされます。
リクエストがエントリポイントにリダイレクトされると、Commerce アプリケーションは、取得したパラメーターに基づいてリクエスト URLを解析し、リクエストされたリソースを見つけます。

- [developer](application-modes.md#developer-mode) モードでは、リソースが要求されるたびに、返されるコンテンツが最新になるように、ファイルのコンテンツが返されます。
- [default](application-modes.md#default-mode) モードでは、取得したリソースが公開され、以前に要求されたURLからアクセスできるようになります。

  静的リソースに対する今後のすべてのリクエストは、サーバーによって静的ファイルと同じように処理されます。つまり、エントリポイントは含まれません。 公開されたファイルを元のファイルと同期する必要がある場合は、`pub/static` ディレクトリを削除する必要があります。その結果、ファイルは次のリクエストで自動的に再公開されます。

### メディアリソースエントリポイント

[Magento\MediaStorage\App\Media](https://github.com/magento/magento2/tree/2.4.8/app/code/Magento/MediaStorage/App/Media.php)は、メディアリソース（つまり、メディアストレージにアップロードされたすべてのファイル）をデータベースから取得します。 データベースがメディアストレージとして設定されるたびに使用されます。

`\Magento\Core\App\Media`は、設定されたデータベースストレージ内のメディアファイルを検索して`pub/static` ディレクトリに書き込み、その内容を返そうとします。 エラーが発生すると、ヘッダーにHTTP 404 （Not Found）ステータスコードが返され、内容は返されません。

