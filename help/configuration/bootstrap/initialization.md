---
title: アプリケーションの初期化とブートストラップ
description: Commerce アプリケーションの初期化とブートストラップロジックについて説明します。
feature: Configuration, Install, Media
exl-id: 46d1ffc0-7870-4dd1-beec-0a9ff858ab62
source-git-commit: 403a5937561d82b02fd126c95af3f70b0ded0747
workflow-type: tm+mt
source-wordcount: '792'
ht-degree: 0%

---

# 初期化とブートストラップの概要

Commerce アプリケーションを実行するために、次のアクションが実装されています。 [pub/index.php][index]:

- 次を含める [app/bootstrap.php][bootinitial]エラー処理、オートローダーの初期化、プロファイルオプションの設定、デフォルトのタイムゾーンの設定などの基本的な初期化ルーチンを実行します。
- のインスタンスを作成 [\Magento\Framework\App\Bootstrap.php][bootstrap] <!-- It requires initialization parameters to be specified in constructor. Normally, the $_SERVER super-global variable is supposed to be passed there. -->
- Commerce アプリケーションインスタンスを作成します。 [\Magento\Framework\AppInterface][app-face]
- Commerceの実行

## Bootstrap実行ロジック

[Bootstrap オブジェクト][bootinitial] では、次のアルゴリズムを使用してCommerce アプリケーションを実行します。

1. エラーハンドラーを初期化します。
1. を作成 [オブジェクト マネージャ][object] すべての場所で使用され、環境の影響を受ける基本的な shared services 環境パラメーターは、これらのオブジェクトに適切に挿入されます。
1. メンテナンスモードがであるとアサートします _ではない_ 有効。有効でない場合は終了します。
1. Commerce アプリケーションがインストールされていることをアサートします。インストールされていない場合は終了します。
1. Commerce アプリケーションを起動します。

   アプリケーションの起動中にキャッチされなかった例外は、でCommerceに自動的に返されます `catchException()` 例外の処理に使用できるメソッド。 後者はどちらかを返す必要があります `true` または `false`:

   - 次の場合 `true`:Commerceが例外を正常に処理しました。 他に何もする必要はありません。
   - 次の場合 `false`: （または他の空の結果）Commerceが例外を処理しませんでした。 Bootstrap オブジェクトは、デフォルトの例外処理サブルーチンを実行します。

1. アプリケーションオブジェクトによって提供された応答を送信します。

   >[!INFO]
   >
   >Commerce アプリケーションがインストールされており、メンテナンスモードではないというアサーションが、のデフォルトの動作です。 `\Magento\Framework\App\Bootstrap` クラス。 Bootstrap オブジェクトの作成時に、エントリポイントスクリプトを使用して変更できます。

   Bootstrap オブジェクトを変更するエントリ ポイント スクリプトの例：

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

ブートストラップオブジェクトは、Commerce アプリケーションがキャッチされなかった例外を処理する方法を次のように指定します。

- 対象： [開発者モード](../bootstrap/application-modes.md#developer-mode)は、例外をそのまま表示します。
- その他のモードでは、は例外をログに記録し、一般的なエラーメッセージを表示しようとします。
- エラーコードでCommerceを終了します `1`

## エントリポイントアプリケーション

次のエントリポイントアプリケーション（Web サーバーでディレクトリインデックスとして使用される、Commerceで定義されたアプリケーション）があります。

### HTTP エントリポイント

[\Magento\Framework\App\Http][http] は次のように動作します。

1. は [適用領域](https://developer.adobe.com/commerce/php/architecture/modules/areas/).
1. コントローラ アクションを検索して実行するために、フロント コントローラとルーティング システムを開始します。
1. HTTP 応答オブジェクトを使用して、コントローラアクションから取得した結果を返します。
1. エラー処理（優先順位が次の順）:

   1. を使用している場合 [開発者モード](../bootstrap/application-modes.md#developer-mode):
      - Commerce アプリケーションがインストールされていない場合は、セットアップウィザードにリダイレクトします。
      - Commerce アプリケーションがインストールされている場合は、エラーと HTTP ステータスコード 500 （内部サーバーエラー）を表示します。
   1. Commerce アプリケーションがメンテナンスモードの場合は、HTTP ステータスコード 503 （サービス利用不可）の、使いやすい「サービス利用不可」ランディングページを表示します。
   1. Commerce アプリケーションが _ではない_ インストール済み。セットアップウィザードにリダイレクトします。
   1. セッションが無効な場合は、ホームページにリダイレクトします。
   1. その他のアプリケーション初期化エラーがある場合は、HTTP ステータスコード 404 （見つかりません）を含む、ユーザーにわかりやすい「ページが見つかりません」ページを表示します。
   1. その他のエラーでは、HTTP 応答 503 を使用してユーザーにわかりやすい「サービス利用不可」ページを表示し、エラーレポートを生成して、その ID をページに表示します。

### 静的リソースエントリポイント

[\Magento\Framework\App\StaticResource][static-resource] は、静的リソース（CSS、JavaScript、画像など）を取得するためのアプリケーションです。 リソースがリクエストされるまで、静的リソースを使用したすべてのアクションが延期されます。

>[!INFO]
>
>静的ビューファイルのエントリポイントは、では使用されません [実稼動モード](application-modes.md#production-mode) サーバー上での潜在的な悪用を回避します。 実稼動モードでは、Commerce アプリケーションは、必要なすべてのリソースがに存在することを想定しています `<your Commerce install dir>/pub/static` ディレクトリ。

デフォルトまたは開発者モードでは、存在しない静的リソースに対するリクエストは、適切ので指定された書き換えルールに従って静的エントリポイントにリダイレクトされます `.htaccess`.
リクエストがエントリポイントにリダイレクトされると、Commerce アプリケーションは、取得されたパラメーターに基づいてリクエストされた URL を解析し、リクエストされたリソースを見つけます。

- 対象： [開発者](application-modes.md#developer-mode) モードの場合、リソースがリクエストされるたびに返されるコンテンツが最新の状態になるように、ファイルのコンテンツが返されます。
- 対象： [default](application-modes.md#default-mode) モードの場合、取得したリソースは公開され、以前にリクエストした URL からアクセスできるようになります。

  静的リソースに対する今後のリクエストはすべて、静的ファイルと同じようにサーバーによって処理されます。つまり、エントリポイントが関係なくなります。 公開済みのファイルを元のファイルと同期する必要がある場合、 `pub/static` ディレクトリを削除する必要があります。その結果、次のリクエストでファイルが自動的に再公開されます。

### メディアリソースのエントリポイント

[Magento\MediaStorage\App\Media][media] データベースからメディア リソース（メディア ストレージにアップロードされたすべてのファイル）を取得します。 これは、データベースがメディアストレージとして設定されている場合は常に使用されます。

`\Magento\Core\App\Media` 構成されたデータベース・ストレージ内でメディア・ファイルを検索し、そのメディア・ファイルをに書き込みます `pub/static` ディレクトリに移動してから、その内容を返します。 エラーの場合、内容を含まない HTTP 404 （見つかりません）ステータスコードがヘッダーに返されます。

<!-- Link Definitions -->

[app-face]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/AppInterface.php
[bootinitial]: https://github.com/magento/magento2/tree/2.4/app/bootstrap.php
[bootstrap]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Bootstrap.php
[http]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Http
[index]: https://github.com/magento/magento2/tree/2.4/pub/index.php
[media]: https://github.com/magento/magento2/tree/2.4/app/code/Magento/MediaStorage/App/Media.php
[object]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/ObjectManager
[static-resource]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/StaticResource.php
