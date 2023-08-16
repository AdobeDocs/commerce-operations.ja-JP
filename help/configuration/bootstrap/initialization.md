---
title: アプリケーションの初期化とブートストラップ
description: コマースアプリケーションの初期化とブートストラップのロジックについてお読みください。
feature: Configuration, Install, Media
exl-id: 46d1ffc0-7870-4dd1-beec-0a9ff858ab62
source-git-commit: 403a5937561d82b02fd126c95af3f70b0ded0747
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%

---

# 初期化とブートストラップの概要

Commerce アプリケーションを実行するには、次のアクションが [pub/index.php][index]:

- 次を含む [app/bootstrap.php][bootinitial]：エラー処理、オートローダの初期化、プロファイルオプションの設定、デフォルトタイムゾーンの設定など、基本的な初期化ルーチンを実行します。
- のインスタンスを作成 [\Magento\Framework\App\Bootstrap.php][bootstrap] <!-- It requires initialization parameters to be specified in constructor. Normally, the $_SERVER super-global variable is supposed to be passed there. -->
- コマースアプリケーションインスタンスを作成します。 [\Magento\Framework\AppInterface][app-face]
- コマースを実行

## Bootstrap実行ロジック

[ブートストラップオブジェクト][bootinitial] は、次のアルゴリズムを使用して Commerce アプリケーションを実行します。

1. エラーハンドラーを初期化します。
1. を作成します。 [オブジェクトマネージャ][object] およびすべての場所で使用され、環境の影響を受ける基本的な共有サービス。 環境パラメーターは、これらのオブジェクトに適切に挿入されます。
1. メンテナンスモードが _not_ enabled。それ以外の場合は終了します。
1. Commerce アプリケーションがインストールされていることをアサートし、それ以外の場合は、が終了します。
1. Commerce アプリケーションを起動します。

   アプリケーションの起動中にキャッチされなかった例外は、自動的に `catchException()` メソッドを使用して例外を処理できます。 後者は、 `true` または `false`:

   - 次の場合 `true`：コマースで例外が正常に処理されました。 他に何もする必要はありません。
   - 次の場合 `false`:（またはその他の空の結果）Commerce は例外を処理しませんでした。 ブートストラップオブジェクトは、デフォルトの例外処理サブルーチンを実行します。

1. アプリケーションオブジェクトによって提供された応答を送信します。

   >[!INFO]
   >
   >Commerce アプリケーションがインストールされ、メンテナンスモードではないという主張が、 `\Magento\Framework\App\Bootstrap` クラス。 ブートストラップオブジェクトを作成する際に、エントリポイントスクリプトを使用して変更できます。

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

bootstrap オブジェクトは、Commerce アプリケーションがキャッチできない例外を次のように処理する方法を指定します。

- In [開発者モード](../bootstrap/application-modes.md#developer-mode)「 」の場合は、例外がそのまま表示されます。
- その他のモードでは、は例外をログに記録し、一般的なエラーメッセージを表示しようとします。
- コマースをエラーコードで終了します `1`

## エントリポイントアプリケーション

次のエントリポイントアプリケーションがあります（つまり、Web サーバーがディレクトリインデックスとして使用する Commerce で定義されたアプリケーション）。

### HTTP エントリポイント

[\Magento\Framework\App\Http][http] は、次のように動作します。

1. を決定します。 [応用領域](https://developer.adobe.com/commerce/php/architecture/modules/areas/).
1. コントローラの操作を検索して実行するために、フロントコントローラとルーティングシステムを起動します。
1. HTTP 応答オブジェクトを使用して、コントローラアクションから取得した結果を返します。
1. エラー処理（次の優先順位）:

   1. を使用している場合、 [開発者モード](../bootstrap/application-modes.md#developer-mode):
      - Commerce アプリケーションがインストールされていない場合は、セットアップウィザードにリダイレクトします。
      - コマースアプリケーションがインストールされている場合は、エラーと HTTP ステータスコード 500（内部サーバーエラー）を表示します。
   1. コマースアプリケーションがメンテナンスモードの場合は、HTTP ステータスコード 503（サービスを使用できません）を含む、使いやすい「サービスを使用できません」ランディングページを表示します。
   1. Commerce アプリケーションが _not_ インストール済みの場合は、セットアップウィザードにリダイレクトします。
   1. セッションが無効な場合は、ホームページにリダイレクトします。
   1. その他のアプリケーション初期化エラーが発生した場合は、HTTP ステータスコード 404(Not Found) のわかりやすい「Page Not Found」ページを表示します。
   1. その他のエラーが発生した場合は、HTTP 応答 503 で、使いやすい「サービスを利用できません」ページを表示し、エラーレポートを生成して、その ID をページに表示します。

### 静的リソースエントリポイント

[\Magento\Framework\App\StaticResource][static-resource] は、静的リソース（CSS、JavaScript、画像など）を取得するためのアプリケーションです。 静的リソースを使用したアクションは、リソースがリクエストされるまで延期されます。

>[!INFO]
>
>静的ビューファイルのエントリポイントは、 [実稼動モード](application-modes.md#production-mode) サーバー上の潜在的な悪用を回避するため。 実稼働モードでは、コマースアプリケーションは、必要なリソースがすべて `<your Commerce install dir>/pub/static` ディレクトリ。

デフォルトまたは開発者モードでは、存在しない静的リソースのリクエストは、適切な `.htaccess`.
リクエストがエントリポイントにリダイレクトされると、Commerce アプリケーションは、取得されたパラメーターに基づいてリクエストされた URL を解析し、リクエストされたリソースを見つけます。

- In [開発者](application-modes.md#developer-mode) mode の場合は、リソースがリクエストされるたびに、返されるコンテンツが最新の状態になるように、ファイルのコンテンツが返されます。
- In [デフォルト](application-modes.md#default-mode) モードの場合、取得したリソースは公開され、以前に要求した URL からアクセスできるようになります。

  静的リソースに対する以降の要求は、すべて静的ファイルと同じようにサーバーによって処理されます。つまり、エントリポイントを含みません。 公開したファイルを元のファイルと同期する必要がある場合は、 `pub/static` ディレクトリは削除する必要があります。その結果、ファイルは次のリクエストで自動的に再公開されます。

### メディアリソースのエントリポイント

[Magento\MediaStorage\App\Media][media] は、データベースからメディアリソース（つまり、メディアストレージにアップロードされたファイル）を取得します。 データベースがメディアストレージとして設定される際に使用されます。

`\Magento\Core\App\Media` は、構成済みのデータベースストレージ内のメディアファイルを検索し、次の場所に書き込みます。 `pub/static` ディレクトリにコピーし、その内容を返します。 エラーの場合は、ヘッダーにステータスコード (HTTP 404（見つかりません）) が返され、コンテンツは返されません。

<!-- Link Definitions -->

[app-face]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/AppInterface.php
[bootinitial]: https://github.com/magento/magento2/tree/2.4/app/bootstrap.php
[bootstrap]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Bootstrap.php
[http]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Http
[index]: https://github.com/magento/magento2/tree/2.4/pub/index.php
[media]: https://github.com/magento/magento2/tree/2.4/app/code/Magento/MediaStorage/App/Media.php
[object]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/ObjectManager
[static-resource]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/StaticResource.php
