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

Commerce アプリケーションを実行するには、次のアクションを [pub/index.php][index] に実装します。

- エラー処理、オートローダーの初期化、プロファイル オプションの設定、および既定のタイムゾーンの設定などの基本的な初期化ルーチンを実行する [0&rbrace;app/bootstrap.php&rbrace; を含めます。][bootinitial]
- [\Magento\Framework\App\Bootstrap.php][bootstrap] <!-- It requires initialization parameters to be specified in constructor. Normally, the $_SERVER super-global variable is supposed to be passed there. --> のインスタンスを作成します
- Commerce アプリケーションインスタンスを作成します：[\Magento\Framework\AppInterface][app-face]
- Commerceの実行

## Bootstrap実行ロジック

[Bootstrap オブジェクト ][bootinitial] は、次のアルゴリズムを使用してCommerce アプリケーションを実行します。

1. エラーハンドラーを初期化します。
1. すべての場所で使用され、環境の影響を受ける [ オブジェクト マネージャ ][object] と基本的な共有サービスを作成します。 環境パラメーターは、これらのオブジェクトに適切に挿入されます。
1. メンテナンスモードが有効 _ではない_ とアサートし、有効でない場合は終了します。
1. Commerce アプリケーションがインストールされていることをアサートします。インストールされていない場合は終了します。
1. Commerce アプリケーションを起動します。

   アプリケーションの起動中にキャッチされなかった例外は、例外の処理に使用できる `catchException()` メソッドでCommerceに自動的に返されます。 後者は、`true` または `false` のいずれかを返す必要があります。

   - `true` の場合：Commerceが正常に例外を処理しました。 他に何もする必要はありません。
   - `false`: （またはその他の空の結果）Commerceが例外を処理しなかった場合。 Bootstrap オブジェクトは、デフォルトの例外処理サブルーチンを実行します。

1. アプリケーションオブジェクトによって提供された応答を送信します。

   >[!INFO]
   >
   >Commerce アプリケーションがインストールされており、メンテナンスモードではないというアサーションが、`\Magento\Framework\App\Bootstrap` クラスのデフォルトの動作です。 Bootstrap オブジェクトの作成時に、エントリポイントスクリプトを使用して変更できます。

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

- [&#x200B; 開発者モード &#x200B;](../bootstrap/application-modes.md#developer-mode) では、は例外をそのまま表示します。
- その他のモードでは、は例外をログに記録し、一般的なエラーメッセージを表示しようとします。
- エラーコード `1` でCommerceを終了します

## エントリポイントアプリケーション

次のエントリポイントアプリケーション（Web サーバーでディレクトリインデックスとして使用される、Commerceで定義されたアプリケーション）があります。

### HTTP エントリポイント

[\Magento\Framework\App\Http][http] は次のように動作します。

1. [&#x200B; アプリケーション領域 &#x200B;](https://developer.adobe.com/commerce/php/architecture/modules/areas/) を決定します。
1. コントローラ アクションを検索して実行するために、フロント コントローラとルーティング システムを開始します。
1. HTTP 応答オブジェクトを使用して、コントローラアクションから取得した結果を返します。
1. エラー処理（優先順位が次の順）:

   1. [&#x200B; 開発者モード &#x200B;](../bootstrap/application-modes.md#developer-mode) を使用している場合：
      - Commerce アプリケーションがインストールされていない場合は、セットアップウィザードにリダイレクトします。
      - Commerce アプリケーションがインストールされている場合は、エラーと HTTP ステータスコード 500 （内部サーバーエラー）を表示します。
   1. Commerce アプリケーションがメンテナンスモードの場合は、HTTP ステータスコード 503 （サービス利用不可）の、使いやすい「サービス利用不可」ランディングページを表示します。
   1. Commerce アプリケーションがインストールされて _ない_ 場合は、セットアップウィザードにリダイレクトします。
   1. セッションが無効な場合は、ホームページにリダイレクトします。
   1. その他のアプリケーション初期化エラーがある場合は、HTTP ステータスコード 404 （見つかりません）を含む、ユーザーにわかりやすい「ページが見つかりません」ページを表示します。
   1. その他のエラーでは、HTTP 応答 503 を使用してユーザーにわかりやすい「サービス利用不可」ページを表示し、エラーレポートを生成して、その ID をページに表示します。

### 静的リソースエントリポイント

[\Magento\Framework\App\StaticResource][static-resource] は、静的リソース （CSS、JavaScript、画像など）を取得するためのアプリケーションです。 リソースがリクエストされるまで、静的リソースを使用したすべてのアクションが延期されます。

>[!INFO]
>
>静的ビューファイルのエントリポイントは、サーバーでの潜在的な攻撃を回避するために [&#x200B; 実稼動モード &#x200B;](application-modes.md#production-mode) では使用されません。 実稼動モードでは、Commerce アプリケーションは、必要なすべてのリソースが `<your Commerce install dir>/pub/static` ディレクトリに存在することを想定します。

デフォルトまたは開発者モードでは、存在しない静的リソースに対するリクエストは、適切な `.htaccess` で指定された書き換えルールに従って静的エントリポイントにリダイレクトされます。
リクエストがエントリポイントにリダイレクトされると、Commerce アプリケーションは、取得されたパラメーターに基づいてリクエストされた URL を解析し、リクエストされたリソースを見つけます。

- [&#x200B; 開発者 &#x200B;](application-modes.md#developer-mode) モードでは、リソースがリクエストされるたびに返されるコンテンツが最新の状態になるように、ファイルのコンテンツが返されます。
- [&#x200B; デフォルト &#x200B;](application-modes.md#default-mode) モードでは、取得したリソースは公開され、以前にリクエストした URL からアクセスできるようになります。

  静的リソースに対する今後のリクエストはすべて、静的ファイルと同じようにサーバーによって処理されます。つまり、エントリポイントが関係なくなります。 公開済みのファイルを元のファイルと同期する必要がある場合は、`pub/static` ディレクトリを削除する必要があります。その結果、ファイルは次のリクエストで自動的に再公開されます。

### メディアリソースのエントリポイント

[Magento\MediaStorage\App\Media][media] メディア リソース （メディア ストレージにアップロードされたファイル）をデータベースから取得します。 これは、データベースがメディアストレージとして設定されている場合は常に使用されます。

`\Magento\Core\App\Media` は、構成されたデータベース・ストレージ内でメディア・ファイルを検索し、`pub/static` ディレクトリに書き込んでから、その内容を返します。 エラーの場合、内容を含まない HTTP 404 （見つかりません）ステータスコードがヘッダーに返されます。

<!-- Link Definitions -->

[app-face]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/AppInterface.php
[bootinitial]: https://github.com/magento/magento2/tree/2.4/app/bootstrap.php
[bootstrap]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Bootstrap.php
[http]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Http
[index]: https://github.com/magento/magento2/tree/2.4/pub/index.php
[media]: https://github.com/magento/magento2/tree/2.4/app/code/Magento/MediaStorage/App/Media.php
[object]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/ObjectManager
[static-resource]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/StaticResource.php
