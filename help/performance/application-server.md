---
title: GraphQL Application Server
description: Adobe CommerceのデプロイメントでGraphQL Application Server を有効にするには、次の手順に従います。
exl-id: 9b223d92-0040-4196-893b-2cf52245ec33
source-git-commit: 70d86569bef5c656fff3a8c6b4af142c81c81f10
workflow-type: tm+mt
source-wordcount: '2079'
ht-degree: 0%

---


# GraphQL Application Server

Commerce GraphQL Application Server は、Adobe Commerceが Commerce GraphQL API リクエストの状態を管理できるようにします。 Swoole 拡張機能に基づいて構築されたGraphQL Application Server は、リクエスト処理を処理するワーカースレッドを使用したプロセスとして動作します。 GraphQL Application Server は、GraphQL API リクエストの間でブートストラップされたアプリケーションの状態を保持することで、リクエスト処理と製品全体のパフォーマンスを向上させます。 API リクエストが大幅に効率的になります。

GraphQL Application Server は、Adobe Commerceでのみ使用できます。 Magento Open Sourceには使用できません。 あなたは必要があります [Adobe Commerce サポートの送信](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) GraphQL Application Server を Pro プロジェクトで有効にするためのチケット。

>[!NOTE]
>
>現在、GraphQL Application Server には互換性がありません [[!DNL Amazon Simple Storage Service (AWS S3)]](https://aws.amazon.com/s3/). 現在を使用しているクラウドインフラストラクチャー上のAdobe Commerce [!DNL AWS S3] （用） [リモートストレージ](../configuration/remote-storage/cloud-support.md) Adobeが 2024 年末にホットフィックスをリリースするまで、GraphQL Application Server を使用できません。

## アーキテクチャ

GraphQL Application Server は、Commerce GraphQL API リクエストの間のステータスを維持し、ブートストラップを行う必要をなくします。 複数のプロセスでアプリケーションのステータスを共有することで、GraphQL リクエストの効率が大幅に向上し、応答時間が最大 30% 短縮します。

共有なし PHP 実行モデルは、要求ごとにフレームワークのブートストラップが必要なため、待ち時間の観点から問題があります。 このブートストラッププロセスには、設定の読み取り、ブートストラッププロセスの設定、サービスクラスオブジェクトの作成など、時間のかかるタスクが含まれます。

リクエスト処理ロジックをアプリケーションレベルのイベントループに移行することは、エンタープライズレベルでリクエスト処理を効率化するという課題に対処するように見えます。 このアプローチにより、リクエスト実行のライフサイクル中にブートストラップを行う必要がなくなります。

## メリット

GraphQL Application Server を使用すると、Adobe Commerceは、連続する Commerce GraphQL API リクエストの間にステートを維持できます。 リクエスト間でアプリケーション状態を共有すると、処理オーバーヘッドが最小限に抑えられ、リクエスト処理が最適化されるので、API リクエストの効率が向上します。 その結果、GraphQLのリクエストの応答時間を最大 30% 短縮できます。

## 必要システム構成

GraphQL Application Server を実行するには、以下が必要です。

* PHP 8.2 以降
* Swoole PHP 拡張機能 v5 以降がインストールされている
* 予想される負荷に応じた十分な RAM と CPU

## クラウドインフラストラクチャでの有効化とデプロイ

この `ApplicationServer` モジュール （`Magento/ApplicationServer/`）を指定すると、GraphQL Application Server が有効になります。

### Pro プロジェクトの有効化

>[!NOTE]
>
>アプリケーションサーバーは、Cloud Pro インスタンスのオプトイン機能です。 有効にするには、サポートリクエストを送信します。

Pro プロジェクトで Application Server 機能を有効にした後、GraphQL Application Server をデプロイする前に次の手順を実行します。

1. のクラウドテンプレートを使用して、クラウドインフラストラクチャにAdobe Commerceをデプロイします。 [2.4.7-appserver ブランチ](https://github.com/magento/magento-cloud/tree/2.4.7-appserver).
1. すべての Commerce のカスタマイズと拡張機能が次のようになっていることを確認します [互換性](https://developer.adobe.com/commerce/php/development/components/app-server/) （GraphQL Application Server を使用）。
1. Commerce Cloudプロジェクトのクローンを作成します。
1. 必要に応じて、「application-server/nginx.conf.sample」ファイルの設定を調整します。
1. のアクティブな「web」セクションをコメントアウト `project_root/.magento.app.yaml` ファイルを完全に。
1. で次の「web」セクション設定をコメント解除 `project_root/.magento.app.yaml` GraphQL Application Server を含むファイル `start` コマンド。

   ```yaml
   web:
       upstream:
           socket_family: tcp
           protocol: http
       commands:
           start: ./application-server/start.sh > var/log/application-server-status.log 2>&1
   ```

1. 更新したファイルを次のコマンドで Git インデックスに追加します。

   ```bash
   git add -f .magento.app.yaml application-server/*
   ```

1. 次のコマンドを使用して変更をコミットします。

   ```bash
   git commit -m "AppServer Enabled"
   ```

### Pro プロジェクトのデプロイ

イネーブルメント手順を完了したら、変更を Git リポジトリーにプッシュして、GraphQL アプリケーションサーバーをデプロイします。

```bash
git push
```

### スタータープロジェクトの有効化

スタータープロジェクトにGraphQL アプリケーションサーバーをデプロイする前に、次の手順を実行します。

1. のクラウドテンプレートを使用して、クラウドインフラストラクチャにAdobe Commerceをデプロイします。 [2.4.7-appserver ブランチ](https://github.com/magento/magento-cloud/tree/2.4.7-appserver).
1. すべての Commerce のカスタマイズと拡張機能に、GraphQL Application Server との互換性があることを確認します。
1. を確認します `CRYPT_KEY` お使いのインスタンスに環境変数が設定されています。 この変数のステータスは、クラウドプロジェクトポータル（オンボーディング UI）で確認できます。
1. Commerce Cloudプロジェクトのクローンを作成します。
1. 名前を変更 `application-server/.magento/.magento.app.yaml.sample` 対象： `application-server/.magento/.magento.app.yaml` 必要に応じて、.magento.app.yaml の設定を調整します。
1. で次のルートの設定をコメント解除します `project_root/.magento/routes.yaml` リダイレクトするファイル `/graphql` GraphQL Application Server にトラフィックします。

   ```yaml
   "http://{all}/graphql":
       type: upstream
       upstream: "application-server:http"
   ```

1. 更新したファイルを Git インデックスに追加します。

   ```bash
   git add -f .magento/routes.yaml application-server/.magento/*
   ```

1. 変更内容をコミットします。

   ```bash
   git commit -m "AppServer Enabled"
   ```

>[!NOTE]
>
>ルートにすべてのカスタム設定があることを確認します `.magento.app.yaml` ファイルは、に適切に移行されます。 `application-server/.magento/.magento.app.yaml` ファイル。 後 `application-server/.magento/.magento.app.yaml` ファイルがプロジェクトに追加されました。ルートに加えて、ファイルを保持する必要があります `.magento.app.yaml` ファイル。 例えば、次の場合です [rabbitmq の設定](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/rabbitmq) または [web プロパティの管理](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/properties/web-property) 同じ設定をに追加する必要があります `application-server/.magento/.magento.app.yaml` また。

### スタータープロジェクトのデプロイ

イネーブルメント完了後 [手順](#before-you-begin-a-cloud-starter-deployment)変更を Git リポジトリーにプッシュして、GraphQL アプリケーションサーバーをデプロイします。

```bash
git push
```

### クラウドプロジェクトでのイネーブルメントの検証

1. インスタンスに対してGraphQL クエリまたはミューテーションを実行し、 `graphql` エンドポイントにアクセスできます。 例：

   ```
   mutation {  
    createEmptyCart
   }
   ```

   期待される応答は次の例のようになります。

   ```terminal
   {    
    "data": {        
        "createEmptyCart": "HLATPzcLw5ylDf76IC92nxdO2hXSXOrv"    
        }
    }
   ```

1. SSH を使用してクラウドインスタンスにアクセスします。 この `project_root/var/log/application-server.log` は、GraphQL リクエストごとに新しいログレコードを含む必要があります。

1. また、次のコマンドを実行して、GraphQL Application Server が実行中かどうかを確認することもできます。

   ```bash
   ps aux|grep php
   ```

   「」が表示されます。 `bin/magento server:run` 複数のスレッドで処理します。

これらの検証手順が正常に完了した場合は、GraphQL Application Server が動作しており、 `/graphql` リクエスト。

## オンプレミスプロジェクトの有効化

この `ApplicationServer` モジュール （`Magento/ApplicationServer/`）を使用すると、GraphQL API 用のGraphQL Application Server を有効にできます。

GraphQL Application Server をローカルで実行するには、Swoole 拡張機能をインストールし、デプロイメントの Nginx 設定ファイルに小さな変更を加える必要があります。

### 前提条件

を有効にする前に、次の手順を実行します `ApplicationServer` モジュール：

* Nginx の設定
* Swoole v5+拡張機能のインストールと設定

#### Nginx の設定

特定の Commerce デプロイメントによって、Nginx の設定方法が決まります。 一般に、Nginx 設定ファイルは、デフォルトではという名前になっています。 `nginx.conf` およびは、次のディレクトリのいずれかに配置されます。 `/usr/local/nginx/conf`, `/etc/nginx`、または `/usr/local/etc/nginx`. 参照： [初心者向けガイド](https://nginx.org/en/docs/beginners_guide.html) nginx の設定の詳細については、を参照してください。

Nginx 設定の例：

```conf
location /graphql {
    proxy_set_header Host $http_host;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

    proxy_pass http://127.0.0.1:9501/graphql;
}
```

#### Swoole のインストールと設定

GraphQL Application Server をローカルで実行するには、Swoole 拡張機能（v5.0 以降）をインストールします。 この拡張機能をインストールする方法は複数あります。

次の手順では、OSX ベースのシステムに Swoole extension for PHP 8.2 をインストールする方法について説明します。 これは、Swoole 拡張機能をインストールする方法の 1 つです。

```bash
pecl install swoole
```

インストール時に、Adobe Commerceは以下のサポートを有効にするよう求めます `openssl`, `mysqlnd`, `sockets`, `http2`、および `postgres`. Enter `yes` を除くすべてのオプション `postgres`.

### Swoole のインストールの確認

拡張機能が正常に有効になったことを確認します。

```bash
php -m | grep swoole
```

### Swoole のインストールに関するよくあるエラー

Swoole のインストール中に発生するエラーは、通常、 `pecl` インストール段階。 典型的なエラーとしては、 `openssl.h` および `pcre2.h` ファイル。 これらのエラーを解決するには、ローカルシステムにこれらの 2 つのパッケージがインストールされていることを確認します。

* の場所を確認する `openssl` 実行方法：

```bash
openssl version -d
```

このコマンドは、次のパスを表示します `openssl` がインストールされました。

* の場所を確認する `pcre2` 実行方法：

```bash
pcre2-config --prefix 
```

コマンド出力にファイルが見つからないことが示されている場合は、Homebrew を使用して見つからないパッケージをインストールします。

```bash
brew install openssl
```

```bash
brew install pcre2
```

#### openssl の問題を解決

に関連した問題を解決するには `openssl`、実行：

```bash
export LDFLAGS="-L/opt/homebrew/etc/openssl@3/lib" export CPPFLAGS="-I/opt/homebrew/etc/openssl@3/include"
```

ローカルのパスを使用していることを確認します `dev` 環境。

#### Openssl 関連の問題の解決の確認

次のコマンドを再度実行すると、openssl 関連の問題が解決されたかどうかを確認できます。

```bash
pecl install swoole
```

#### pcre2.h の問題を解決

に関連した問題を解決するには `pcre2.h`、シンボリックリンク `pcre2.h` インストールした PHP 拡張ディレクトリへのパス。 特定のインストール済みバージョンの PHP `pcr2.h` 使用するコマンドの特定のバージョンを決定します。

### GraphQL Application Server の実行

GraphQL Application Server を起動します。

```bash
bin/magento server:run
```

このコマンドは、9501 で HTTP ポートを開始します。 GraphQL Application Server が起動すると、ポート 9501 はすべてのGraphQL クエリの HTTP プロキシサーバーになります。

デプロイメントでGraphQL Application Server が実行中であることを確認するには：

```bash
ps aux | grep php
```

GraphQL Application Server が実行中であることを確認するその他の方法を次に示します。

* を確認します `/var/log/application-server.log` 処理されたGraphQL リクエストに関連するエントリのファイル。
* GraphQL Application Server を実行している HTTP ポートに接続してみます。 例： `curl -g 'http://localhost:9501/graph`.

### GraphQL リクエストが処理中であることを確認します

GraphQL Application Server は、 `X-Backend` 応答ヘッダー（値：） `graphql_server` を処理する各リクエストに対して実行します。 リクエストがGraphQL Application Server によって処理されたかどうかを確認するには、この応答ヘッダーを確認します。

### 拡張機能とカスタマイズの互換性の確認

拡張機能の開発者とマーチャントは、まず、拡張機能とカスタマイズコードがに記載されている技術的なガイドラインに準拠していることを確認する必要があります。 [技術ガイドライン](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/).

コード評価時には、次のガイドラインを考慮してください。

* サービスクラス（動作を提供するがデータを提供しないクラス。以下に例を示します） `EventManager`）に可変状態を指定しないでください。
* 時間結合を避けます。

## GraphQL Application Server の無効化

GraphQL Application Server を無効にする手順は、サーバーがオンプレミスとクラウドのどちらのデプロイメントで実行されているかによって異なります。

### GraphQL Application Server （Cloud）を無効にする

1. に含まれていた新しいファイルとその他のコード変更を削除します `AppServer Enabled` デプロイメントの準備中にコミットします。

1. 次のコマンドを使用して変更をコミットします。

   ```bash
   git commit -m "AppServer Disabled"
   ```

1. 次のコマンドを使用して、これらの変更をデプロイします。

   ```bash
   git push
   ```

### GraphQL Application Server を無効にする（オンプレミス）

1. をコメントアウトします `/graphql` セクション `nginx.conf` GraphQL Application Server を有効にする際に追加したファイル。
1. nginx を再起動します。

GraphQL Application Server を無効にするこの方法は、パフォーマンスをすばやくテストまたは比較するのに役立ちます。

### GraphQL Application Server が無効になっていることを確認します。

GraphQL リクエストがによって処理されていることを確認するには `php-fpm` GraphQL Application Server の代わりに、次のコマンドを入力します。 `ps aux | grep php`.

GraphQL Application Server が無効になった後：

* `bin/magento server:run` 非アクティブです。
* `var/log/application-server.log` GraphQL リクエストの後にエントリが含まれていません。

## GraphQL Application Server の統合および機能テスト

拡張機能の開発者は、2 つの統合テストを実行して、GraphQL Application Server との拡張機能の互換性を確認できます。 `GraphQlStateTest` および `ResetAfterRequestTest`.

### GraphQlStateTest

`GraphQlStateTest` 複数のリクエストで再利用してはいけない共有オブジェクトの状態を検出します。

このテストは、によって生成されるサービスオブジェクトの状態変化を検出するように設計されています。 `ObjectManager`. このテストでは、同一のGraphQL クエリを 2 回実行し、2 回目のクエリの前後でサービスオブジェクトのステートを比較します。

#### GraphQlStateTest の失敗と潜在的な修正

* **リストを追加、スキップ、フィルタリングできない**. リストの追加、スキップ、またはフィルタリングが安全ではないことが示唆されるエラーが発生した場合は、可変状態のサービスクラスのファクトリを使用するために、下位互換性のある方法でクラスをリファクタリングできるかどうかを検討します。

* **クラスは可変状態を示します**. クラス自体が可変状態を示す場合は、この状態を回避するようにコードを書き換えてみてください。 パフォーマンス上の理由から可変状態が必要な場合は、を実装します。 `ResetAfterRequestInterface` および使用 `_resetState()` オブジェクトを初期構築状態にリセットします。

* **型指定されたプロパティ $x は初期化メッセージの前にアクセスできません**. このタイプのメッセージでエラーが発生した場合は、指定されたプロパティがコンストラクターによって初期化されていないことを示します。 これは、オブジェクトが最初に作成された後で使用できないために発生する時間的結合の一種です。 プロパティからデータを取得するコレクタが PHP のリフレクション機能を使用しているため、プロパティがプライベートであっても、この結合が発生します。 この場合、クラスをリファクタリングして、時間結合を避け、可変状態を避けるようにしてください。 そのリファクタリングでエラーが解決されない場合は、プロパティタイプを nullable 型に変更して、null に初期化できるようにします。  プロパティが配列の場合は、プロパティを空の配列として初期化してみてください。

実行 `GraphQlStateTest` 実行による `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/GraphQl/App/GraphQlStateTest.php`.

### ResetAfterRequestTest

`ResetAfterRequestTest` は、を実装するすべてのクラスを検索します `ResetAfterRequestInterface` を実行して、 `_resetState()` メソッドは、オブジェクトの状態を、で構築された後に保持したのと同じ状態に返します。 `ObjectManager`.  このテストでは、次のサービス オブジェクトを作成します `ObjectManager`その後、オブジェクトを複製し、を呼び出します `_resetState()`を選択し、両方のオブジェクトを比較します。 このテストでは、オブジェクトのインスタンス化との間でメソッドは呼び出されません。 `_resetState()`そのため、可変状態のリセットは確認されません。 バグやタイプミスが発生した問題を見つけます `_resetState()` 元の状態とは異なる状態に設定される場合があります。

#### ResetAfterRequestTest エラーと修復の可能性

* **クラスに一貫性のないプロパティ値があります**. このテストが失敗した場合は、構築後のオブジェクトのプロパティ値が、構築後のオブジェクトのプロパティ値と異なるという結果で、クラスが変更されたかどうかを確認します `_resetState()` メソッドが呼び出されます。 作業中のクラスにが含まれていない場合 `_resetState()` 次に、メソッド自体を実装しているスーパークラスのクラス階層を確認します。

* **型指定されたプロパティ $x は初期化メッセージの前にアクセスできません**. この問題は、でも発生します。 `GraphQlStateTest`.

  実行 `ResetAfterRequestTest` 次を実行します。 `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/Framework/ObjectManager/ResetAfterRequestTest.php`.

### 機能テスト

拡張機能の開発者は、GraphQL Application Server のデプロイ中に、GraphQLの WebAPI 機能テストと、GraphQLのカスタム自動または手動の機能テストを実行する必要があります。 これらの機能テストは、開発者が潜在的なエラーや互換性の問題を特定するのに役立ちます。

#### 状態監視モード

機能テスト（または手動テスト）の実行中、アプリケーションサーバーはで実行できます `--state-monitor mode` 状態が意図せずに再利用されているクラスを見つけるのに役立ちます。 アプリケーションサーバーを通常どおり起動します（を追加する以外） `--state-monitor` パラメーター。

```
bin/magento server:run --state-monitor
```

各リクエストが処理されると、新しいファイルがに追加されます。 `tmp` ディレクトリ（例：） `var/tmp/StateMonitor-thread-output-50-6nmxiK`. テストが完了したら、これらのファイルは `bin/magento server:state-monitor:aggregate-output` コマンド。結合された 2 つのファイルを作成します。1 つは `XML` さらに 1: `JSON`.

例：

```
/var/workspace/var/tmp/StateMonitor-json-2024-04-10T18:50:39Z-hW0ucN.json
/var/workspace/var/tmp/StateMonitor-junit-2024-04-10T18:50:39Z-oreUco.xml
```

これらのファイルは、XML または JSON の表示に使用する任意のツールを使用して調べることができます。これにより、GraphQlStateTest などのサービスオブジェクトの変更されたプロパティが表示されます。 この `--state-monitor` モードでは、GraphQlStateTest と同じスキップリストとフィルターリストを使用します。

>[!NOTE]
>
>を使用しないでください。 `--state-monitor` モードは実稼動環境にあります。 開発およびテストのみを目的として設計されています。 多くの出力ファイルが作成され、通常よりも実行速度が低下します。

>[!NOTE]
>
>`--state-monitor` は、PHP バージョンと互換性がありません。 `8.3.0` - `8.3.4` php のガベージコレクタのバグが原因です。 PHP 8.3 を使用している場合は、以下にアップグレードする必要があります。 `8.3.5` この機能を使用するには、以降のバージョンを使用します。
