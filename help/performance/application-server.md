---
title: GraphQL API 用アプリケーションサーバー
description: Adobe CommerceデプロイメントでGraphQL API 用のアプリケーションサーバーを有効にするには、以下の手順に従います。
badgeCoreBeta: label="2.4.7-beta" type="informative"
exl-id: 9b223d92-0040-4196-893b-2cf52245ec33
source-git-commit: 9d5795400880a65947b1b90c8806b9dcb14aba23
workflow-type: tm+mt
source-wordcount: '1897'
ht-degree: 0%

---

# GraphQL API 用アプリケーションサーバー

GraphQL API 用の Commerce Application Server を使用すると、Adobe Commerceは Commerce GraphQL API リクエストの間で状態を維持できます。 Swoole 拡張機能上に構築された Application Server は、リクエスト処理を処理するワーカースレッドを持つプロセスとして動作します。 GraphQL API リクエストでアプリケーションのブートストラップ状態を保持することで、Application Server はリクエスト処理と製品の全体的なパフォーマンスを強化します。 API リクエストの効率が大幅に向上しました。

Application Server は、クラウドインフラストラクチャの Starter および Pro プロジェクト上のAdobe Commerceでのみサポートされています。 Magento Open Sourceプロジェクトでは使用できません。 Adobeは、Application Server のオンプレミスデプロイメントをサポートしていません。

## Application Server のアーキテクチャの概要

Application Server は、Commerce GraphQL API リクエスト間の状態を維持し、ブートストラップをおこなう必要がなくなりました。 複数のプロセスでアプリケーション状態を共有することで、GraphQLリクエストの効率が大幅に向上し、応答時間が最大 30%短縮されます。

共有なしの PHP 実行モデルは、待ち時間の観点から問題を提供します。各要求はフレームワークのブートストラップを必要とするからです。 このブートストラッププロセスには、設定の読み取り、ブートストラッププロセスの設定、サービスクラスオブジェクトの作成など、時間のかかるタスクが含まれます。

リクエスト処理ロジックをアプリケーションレベルのイベントループに移行すると、リクエスト処理をエンタープライズレベルで合理化するという課題に対処できるようになります。 このアプローチにより、リクエストの実行ライフサイクル中にブートストラップをおこなう必要がなくなります。

## アプリケーションサーバーを使用する利点

Application Server を使用すると、Adobe Commerceは連続する Commerce GraphQL API リクエストの間で状態を維持できます。 リクエスト間でアプリケーション状態を共有すると、処理のオーバーヘッドを最小限に抑え、リクエスト処理を最適化することで、API リクエストの効率が向上します。 その結果、GraphQLリクエストの応答時間を最大 30%短縮できます。

## 必要システム構成

アプリケーションサーバーを実行するには、次が必要です。

* PHP 8.2 以降
* Swoole PHP 拡張機能 v5+がインストールされています
* 予想される負荷に基づく適切な RAM と CPU

## アプリケーションサーバーを有効にする

The `ApplicationServer` モジュール (`Magento/ApplicationServer/`) は、GraphQL API 用の Application Server を有効にします。 Application Server は、オンプレミスおよびクラウドでの展開でサポートされます。

## Cloud Pro での Application Server の有効化

Cloud Pro に Application Server をデプロイする前に、次の作業を実行します。

1. Cloud Template バージョン 2.4.7 以降を使用して、Adobe CommerceがCommerce Cloudにインストールされていることを確認します。
1. コマースのカスタマイズと拡張機能がすべて [互換](https://developer.adobe.com/commerce/php/development/components/app-server/) アプリケーションサーバーとの統合
1. Commerce Cloudプロジェクトの複製。
1. 必要に応じて、「application-server/nginx.conf.sample」ファイルの設定を調整します。
1. 次のアクティブな「Web」セクションをコメントアウトします： `project_root/.magento.app.yaml` ファイル全体を含めます。
1. 次の「Web」セクション設定を `project_root/.magento.app.yaml` アプリケーションサーバーの start コマンドを含むファイル。

   ```yaml
   web:
       upstream:
           socket_family: tcp
           protocol: http
       commands:
           start: ./application-server/start.sh > var/log/application-server-status.log 2>&1
   ```

1. 次のコマンドを使用して、更新されたファイルを git インデックスに追加します。

   ```bash
   git add -f .magento/routes.yaml application-server/.magento/*
   ```

1. 次のコマンドを使用して変更をコミットします。

   ```bash
   git commit -m "AppServer Enabled"
   ```

### Cloud Pro でのアプリケーションサーバーのデプロイ

前提条件のタスクを実行した後、次のコマンドを使用して Application Server をデプロイします。

```bash
git push
```

### Cloud Starter のデプロイメントを開始する前に

Application Server を Cloud Starter にデプロイする前に、次のタスクを実行します。

1. Cloud Template バージョン 2.4.7 以降を使用して、Adobe CommerceがCommerce Cloudにインストールされていることを確認します。
1. すべてのコマースのカスタマイズ機能と拡張機能が Application Server と互換性があることを確認します。
1. を確認します。 `CRYPT_KEY` 環境変数がインスタンスに設定されている。 この変数のステータスは、クラウドプロジェクトポータル（オンボーディング UI）で確認できます。
1. Commerce Cloudプロジェクトの複製。
1. 名前を変更 `application-server/.magento/.magento.app.yaml.sample` から `application-server/.magento/.magento.app.yaml` 必要に応じて、 .magento.app.yaml の設定を調整します。
1. 内で次のルートの設定をコメント解除します。 `project_root/.magento/routes.yaml` リダイレクトするファイル `/graphql` アプリケーションサーバーへのトラフィック。

   ```yaml
   "http://{all}/graphql":
       type: upstream
       upstream: "application-server:http"
   ```

1. 次のコマンドを使用して、更新されたファイルを git インデックスに追加します。

   ```bash
   git add -f .magento/routes.yaml application-server/.magento/*
   ```

1. 次のコマンドを使用して変更をコミットします。

   ```bash
   git commit -m "AppServer Enabled"
   ```

>[!NOTE]
>
> ルートにあるすべてのカスタム設定を確認します。 `.magento.app.yaml` ファイルは、 `application-server/.magento/.magento.app.yaml` ファイル。 1 回 `application-server/.magento/.magento.app.yaml` ファイルがプロジェクトに追加された場合は、ルートに加えてファイルを維持する必要があります `.magento.app.yaml` ファイル。
> 例えば、 [rabbitmq の設定](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/rabbitmq) または [web プロパティの管理](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/properties/web-property) 同じ設定を `application-server/.magento/.magento.app.yaml` 同様に。

### Cloud Starter にアプリケーションサーバーをデプロイ

完了後、 [前提条件](#before-you-begin-a-cloud-starter-deployment)次のコマンドを使用して、Application Server をデプロイします。

```bash
git push
```

### Cloud Starter でのアプリケーションサーバーの有効化を検証

1. インスタンスに対してGraphQLクエリまたはミューテーションを実行し、 `graphql` エンドポイントがアクセス可能です。 例：

   ```
   mutation {  
    createEmptyCart
   }
   ```

   期待される応答は、次の例のようになります。

   ```terminal
   {    
    "data": {        
        "createEmptyCart": "HLATPzcLw5ylDf76IC92nxdO2hXSXOrv"    
        }
    }
   ```

1. SSH を使用してクラウドインスタンスにアクセスします。 The `project_root/var/log/application-server.log` には、すべてのGraphQLリクエストの新しいログレコードを含める必要があります。

1. 次のコマンドを実行して、アプリケーションサーバーが実行中かどうかを確認することもできます。

   ```bash
   ps aux|grep php
   ```

   次のように表示されます。 `bin/magento server:run` 複数のスレッドで処理します。

これらの検証手順が成功した場合、アプリケーションサーバーは実行中で、サービング中です `/graphql` リクエスト。


## オンプレミスでの展開で Application Server を有効にする

The `ApplicationServer` モジュール (`Magento/ApplicationServer/`) は、GraphQL API 用の Application Server を有効にします。

Application Server をローカルで実行するには、Swoole 拡張機能をインストールし、デプロイメントの NGINX 設定ファイルに若干の変更を加える必要があります。

### オンプレミスデプロイメントを開始する前に

次の 2 つの作業を完了してから、 `ApplicationServer` モジュール：

* Nginx の設定

* Swoole v5+拡張機能のインストールと設定

### Nginx の設定

特定のコマースデプロイメントによって、Nginx の設定方法が決まります。 一般に、Nginx 設定ファイルはデフォルトで、 `nginx.conf` は、次のいずれかのディレクトリに配置されます。 `/usr/local/nginx/conf`, `/etc/nginx`または `/usr/local/etc/nginx`. 詳しくは、 [初心者向けガイド](https://nginx.org/en/docs/beginners_guide.html) を参照してください。

Nginx 設定の例：

```conf
location /graphql {
    proxy_set_header Host $http_host;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

    proxy_pass http://127.0.0.1:9501/graphql;
}
```

### Swoole のインストールと設定

Application Server をローカルで実行するには、Swoole 拡張機能（v5.0 以降）をインストールします。 この拡張機能は、複数の方法でインストールできます。

## アプリケーションサーバーを実行

アプリケーションサーバーを起動します。

```bash
bin/magento server:run
```

このコマンドは、9501 で HTTP ポートを開始します。 アプリケーションサーバーが起動すると、ポート 9501 は、すべてのGraphQLクエリの HTTP プロキシサーバーになります。

## 例： Swoole (OSX) のインストール

この手順は、OSX ベースのシステム用の PHP 8.2 に Swoole 拡張をインストールする方法を示します。 これは、Swoole 拡張機能をインストールするいくつかの方法の 1 つです。

### Swoole のインストール

入力：

```bash
pecl install swoole
```

インストール中に、Adobe Commerceに、のサポートを有効にするプロンプトが表示されます。 `openssl`, `mysqlnd`, `sockets`, `http2`、および `postgres`. 入力 `yes` を除くすべてのオプション `postgres`.

### Swoole のインストールの確認

実行 `php -m | grep swoole` 拡張機能が正常に有効化されたことを確認する。

### Swoole のインストールに関する一般的なエラー

Swoole のインストール中に発生したエラーは、通常、 `pecl` インストールフェーズ。 一般的なエラーには、が見つからないものが含まれます `openssl.h` および `pcre2.h` ファイル。 これらのエラーを解決するには、ローカルシステムにこれら 2 つのパッケージがインストールされていることを確認します。

* 次の場所を確認： `openssl` 実行別：

```bash
openssl version -d
```

このコマンドは、次の場所にあるパスを表示します。 `openssl` がインストールされている。

* 次の場所を確認： `pcre2` 実行別：

```bash
pcre2-config --prefix 
```

コマンド出力でファイルが見つからないことが示された場合は、Homebrew を使用して、見つからないパッケージをインストールします。

```bash
brew install openssl
```

```bash
brew install pcre2
```

#### OpenSSL の問題を解決

関連する問題を解決するには `openssl`、実行：

```bash
export LDFLAGS="-L/opt/homebrew/etc/openssl@3/lib" export CPPFLAGS="-I/opt/homebrew/etc/openssl@3/include"
```

ローカルからのパスを使用していることを確認してください `dev` 環境。

#### OpenSSL に関連する問題の解決を確認する

次のコマンドを再度実行して、OpenSSL 関連の問題が解決されたかどうかを確認できます。

```bash
pecl install swoole
```

#### pcre2.h の問題の解決

関連する問題を解決するには `pcre2.h`、symlink をクリックします。 `pcre2.h` インストールした PHP 拡張ディレクトリのパス。 PHP の特定のインストールバージョンと `pcr2.h` 使用する必要のあるコマンドの特定のバージョンを決定します。

### アプリケーションサーバーが実行中であることを確認します。

デプロイメントでアプリケーションサーバーが実行されていることを確認するには、次のコマンドを実行します。

```bash
ps aux | grep php
```

アプリケーションサーバーが実行されていることを確認するその他の方法を次に示します。

* 次を確認します。 `/var/log/application-server.log` ファイルを参照してください。
* アプリケーションサーバーが実行されている HTTP ポートに接続してみます。 例： `curl -g 'http://localhost:9501/graph`.

### GraphQL要求が Application Server で処理されていることを確認します。

アプリケーションサーバーが `X-Backend` 応答ヘッダーと値 `graphql_server` を、処理する各リクエストに対して設定します。 リクエストがアプリケーションサーバーによって処理されたかどうかを確認するには、この応答ヘッダーを確認します。

### 拡張機能とアプリケーションサーバーとのカスタマイズの互換性を確認する

拡張機能の開発者とマーチャントは、まず、拡張機能とカスタマイズコードが、 [技術ガイドライン](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/).

コード評価時には、次のガイドラインを考慮してください。

* サービスクラス（例：動作を提供するがデータを提供しないクラス） `EventManager`) は可変状態ではありません。
* 時間的な結合を避けます。

## アプリケーションサーバーを無効にする

アプリケーションサーバーを無効にする手順は、サーバーがオンプレミスで実行されているかクラウドで実行されているかによって異なります。

### クラウドスターターでのアプリケーションサーバーの無効化

1. 新しいファイルや、 `AppServer Enabled` 配置の準備中にコミットします。

1. 次のコマンドを使用して変更をコミットします。

   ```bash
   git commit -m "AppServer Disabled"
   ```

1. 次のコマンドを使用して、これらの変更をデプロイします。

   ```bash
   git push
   ```

### アプリケーションサーバーを無効にする

1. 次をコメントアウト： `/graphql` のセクション `nginx.conf` アプリケーションサーバーを有効にする際に追加したファイル。
1. nginx を再起動します。

この無効化方法は、パフォーマンスを迅速にテストまたは比較する場合に役立ちます。

### アプリケーションサーバーが無効になっていることを確認します

GraphQL要求が次の条件で処理されていることを確認するには、以下を実行します。 `php-fpm` アプリケーションサーバーの代わりに、次のコマンドを入力します。 `ps aux | grep php`.

アプリケーションサーバーが無効になった後：

* `bin/magento server:run` は非アクティブです。
* `var/log/application-server.log` GraphQL要求の後にはエントリが含まれません。

## PHP Application Server の統合テストと機能テスト

拡張機能の開発者は、拡張機能とアプリケーションサーバーの互換性を検証するために、次の 2 つの統合テストを実行できます。 `GraphQlStateTest` および `ResetAfterRequestTest`.

### GraphQlStateTest

`GraphQlStateTest` は、複数のリクエストで再利用すべきでない共有オブジェクトの状態を検出します。

このテストは、 `ObjectManager`. テストでは、同じGraphQLクエリを 2 回実行し、2 番目のクエリの前後のサービスオブジェクトの状態を比較します。

#### GraphQlStateTest の失敗と潜在的な修正

* **リストの追加、スキップ、フィルターを実行できません**. リストの追加、スキップ、フィルタリングが安全でないことを示すエラーが発生した場合は、可変状態のサービスクラスのファクトリを使用する後方互換性のある方法でクラスをリファクタリングできるかどうかを検討します。

* **クラスは可変状態を示します**. クラス自体が可変状態を示す場合は、この状態を回避するためにコードを書き換えてみてください。 パフォーマンス上の理由で可変状態が必要な場合は、 `ResetAfterRequestInterface` とを使用します。 `_resetState()` オブジェクトを初期の構築済み状態にリセットする。

* **入力されたプロパティ$x には、初期化メッセージの前にアクセスできません**. このタイプのメッセージでエラーが発生した場合、指定されたプロパティがコンストラクタによって初期化されていないことを示します。 これは、最初に構築された後はオブジェクトを使用できないために発生する時間的な結合の形式です。 この結合は、プロパティがプライベートの場合でも発生します。プロパティからデータを取得するコレクタは PHP リフレクション機能を使用しているからです。 この場合、時間的な結合を避け、可変状態を避けるために、クラスをリファクタリングしてみます。 このリファクタリングで失敗が解決されない場合は、プロパティ型を null 可能な型に変更して、null に初期化できるようにします。  プロパティが配列の場合、空の配列としてプロパティを初期化してみてください。

実行 `GraphQlStateTest` 実行 `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/GraphQl/App/GraphQlStateTest.php`.

### ResetAfterRequestTest

`ResetAfterRequestTest` を実装するすべてのクラスを探す `ResetAfterRequestInterface` およびは、 `_resetState()` メソッドは、オブジェクトの状態を、 `ObjectManager`.  このテストでは、 `ObjectManager`をクローンし、そのオブジェクトのを呼び出す `_resetState()`を参照し、両方のオブジェクトを比較します。 このテストでは、オブジェクトのインスタンス化との間にメソッドは呼び出されません。 `_resetState()`そのため、可変状態のリセットは確認されません。 バグやタイポが `_resetState()` は、状態を元の状態とは異なる値に設定する場合があります。

#### ResetAfterRequestTest の失敗と潜在的な修正

* **クラスに一貫性のないプロパティ値があります**. このテストが失敗した場合は、構築後のオブジェクトのプロパティ値が、構築後のオブジェクトのプロパティ値と異なるという結果でクラスが変更されたかどうかを確認します。 `_resetState()` メソッドが呼び出されます。 作業中のクラスに `_resetState()` メソッド自体を使用して、それを実装するスーパークラスのクラス階層を確認します。

* **入力されたプロパティ$x には、初期化メッセージの前にアクセスできません**. この問題は、 `GraphQlStateTest`.

  実行 `ResetAfterRequestTest` 次を実行します。 `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/Framework/ObjectManager/ResetAfterRequestTest.php`.

### 機能テスト

拡張機能開発者は、Application Server をデプロイする際に、GraphQLの WebAPI 機能テストと、GraphQLのカスタムの自動機能テストまたは手動機能テストを実行する必要があります。 これらの機能テストは、開発者が潜在的なエラーや互換性の問題を特定するのに役立ちます。
