---
title: GraphQL Application Server
description: Adobe CommerceのデプロイメントでGraphQL Application Server を有効にするには、次の手順に従います。
exl-id: 9b223d92-0040-4196-893b-2cf52245ec33
source-git-commit: ed46f48472a51db17e1c3ade9bfe3ab134098548
workflow-type: tm+mt
source-wordcount: '2212'
ht-degree: 0%

---


# GraphQL Application Server

Commerce GraphQL Application Server を使用すると、Adobe CommerceはCommerce GraphQL API リクエストの状態を維持できます。 Swoole 拡張機能に基づいて構築されたGraphQL Application Server は、リクエスト処理を処理するワーカースレッドを使用したプロセスとして動作します。 GraphQL Application Server は、GraphQL API リクエストの間でブートストラップされたアプリケーションの状態を保持することで、リクエスト処理と製品全体のパフォーマンスを向上させます。 API リクエストが大幅に効率的になります。

GraphQL Application Server は、Adobe Commerceでのみ使用できます。 Magento Open Sourceでは使用できません。 Cloud Pro プロジェクトの場合、GraphQL Application Server を有効にするには、[Adobe Commerce サポートを送信 ](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) チケットが必要です。

>[!NOTE]
>
>現在、GraphQL Application Server は [[!DNL Amazon Simple Storage Service (AWS S3)]](https://aws.amazon.com/s3/) と互換性がありません。 現在、[!DNL AWS S3] for [ リモートストレージ ](../configuration/remote-storage/cloud-support.md) を使用しているクラウドインフラストラクチャー上のAdobe Commerceのお客様は、GraphQL Application Server を使用できません。

## アーキテクチャ

GraphQL Application Server は、Commerce GraphQL API リクエストの間のステータスを維持し、ブートストラップを不要にします。 複数のプロセスでアプリケーションのステータスを共有することで、GraphQL リクエストの効率が大幅に向上し、応答時間が最大 30% 短縮します。

共有なし PHP 実行モデルは、要求ごとにフレームワークのブートストラップが必要なため、待ち時間の観点から問題があります。 このブートストラッププロセスには、設定の読み取り、ブートストラッププロセスの設定、サービスクラスオブジェクトの作成など、時間のかかるタスクが含まれます。

リクエスト処理ロジックをアプリケーションレベルのイベントループに移行することは、エンタープライズレベルでリクエスト処理を効率化するという課題に対処するように見えます。 このアプローチにより、リクエスト実行のライフサイクル中にブートストラップを行う必要がなくなります。

## メリット

GraphQL Application Server を使用すると、Adobe Commerceは、連続するCommerce GraphQL API リクエストの間にステートを維持できます。 リクエスト間でアプリケーション状態を共有すると、処理オーバーヘッドが最小限に抑えられ、リクエスト処理が最適化されるので、API リクエストの効率が向上します。 その結果、GraphQLのリクエストに対する応答時間を最大 30% 短縮できます。

## 必要システム構成

GraphQL Application Server を実行するには、以下が必要です。

* Commerce バージョン 2.4.7 以降
* PHP 8.2 以降
* 予想される負荷に基づいた十分な RAM とCPU
* Swoole PHP 拡張機能 v5 以降（以下のプロジェクト固有の要件を参照）

### クラウドプロジェクト

クラウドインフラストラクチャプロジェクト上のAdobe Commerceには、デフォルトで Swoole 拡張機能が含まれています。 [ ファイルの ](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/configure/app/php-settings#enable-extensions) プロパティで `runtime` 有効 `.magento.app.yaml` することができます。 例：

```yaml
runtime:
    extensions:
        - swoole
```

### オンプレミス プロジェクト

オンプレミスのプロジェクトでは、Swoole PHP 拡張機能を手動で [ インストールして設定 ](#install-and-configure-swoole) する必要があります。

## クラウドインフラストラクチャでの有効化とデプロイ

`ApplicationServer` モジュール（`Magento/ApplicationServer/`）は、GraphQL Application Server を有効にします。

### Pro プロジェクトの有効化

>[!NOTE]
>
>アプリケーションサーバーは、Cloud Pro インスタンスのオプトイン機能です。 有効にするには、サポートリクエストを送信します。

Pro プロジェクトで Application Server 機能を有効にした後、GraphQL Application Server をデプロイする前に次の手順を実行します。

1. [2.4.7-appserver ブランチ ](https://github.com/magento/magento-cloud/tree/2.4.7-appserver) のクラウドテンプレートを使用して、クラウドインフラストラクチャにAdobe Commerceをデプロイします。
1. すべてのCommerceのカスタマイズと拡張機能がGraphQL Application Server と [ 互換性がある ](https://developer.adobe.com/commerce/php/development/components/app-server/) ことを確認します。
1. Commerce Cloud プロジェクトのクローンを作成します。
1. 必要に応じて、「application-server/nginx.conf.sample」ファイルの設定を調整します。
1. ファイル内のアクティブな「web」セクション `project_root/.magento.app.yaml` 完全にコメントアウトします。
1. GraphQL Application Server `project_root/.magento.app.yaml` コマンドを含む `start` ファイルで、次の「web」セクション設定に対してコメント解除します。

   ```yaml
   web:
       upstream:
           socket_family: tcp
           protocol: http
       commands:
           start: ./application-server/start.sh > var/log/application-server-status.log 2>&1
   ```

1. 次のコマンドを実行して、`/application-server/start.sh` が実行可能であることを確認します。

   ```bash
   chmod +x application-server/start.sh
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

1. [2.4.7-appserver ブランチ ](https://github.com/magento/magento-cloud/tree/2.4.7-appserver) のクラウドテンプレートを使用して、クラウドインフラストラクチャにAdobe Commerceをデプロイします。
1. すべてのCommerceのカスタマイズと拡張機能に、GraphQL Application Server との互換性があることを確認します。
1. `CRYPT_KEY` 環境変数がインスタンスに対して設定されていることを確認します。 この変数のステータスは、Cloud Console で確認できます。
1. Commerce Cloud プロジェクトのクローンを作成します。
1. 必要に応じて、`application-server/.magento/.magento.app.yaml.sample` の名前を `application-server/.magento/.magento.app.yaml` に変更し、.magento.app.yaml の設定を調整します。
1. GraphQL Application Server にトラフィックをリダイレクトするには、`project_root/.magento/routes.yaml` ファイルで次のルートの設定 `/graphql` コメント解除します。

   ```yaml
   "http://{all}/graphql":
       type: upstream
       upstream: "application-server:http"
   ```

1. `files` ファイルの `.magento/services.yaml` セクションをコメント解除します。

   ```yaml
   files:
       type: network-storage:2.0
       disk: 5120
   ```

1. `TEMPORARY SHARED MOUNTS` ファイルのマウント設定の `.magento.app.yaml` の部分をコメント解除します。

   ```yaml
   "var_shared":
       source: "service"
       service: "files"
       source_path: "var"
   "app/etc_shared":
       source: "service"
       service: "files"
       source_path: "etc"
   "pub/media_shared":
       source: "service"
       service: "files"
       source_path: "media"
   "pub/static_shared":
       source: "service"
       service: "files"
       source_path: "static"
   ```

1. 更新したファイルを Git インデックスに追加します。

   ```bash
   git add -f .magento.app.yaml .magento/routes.yaml .magento/services.yaml application-server/.magento/*
   ```

1. 変更内容をコミットし、トリガーデプロイメントにプッシュします。

   ```bash
   git commit -m "Enabling AppServer: initial changes"
   git push
   ```

1. SSH を使用して、リモートクラウド環境（_アプリではな_） `application-server` ログインします。

   ```bash
   magento-cloud ssh -p <project-ID> -e <environment-ID>
   ```

1. ローカルマウントから共有マウントにデータを同期します。

   ```bash
   rsync -avz var/* var_shared/
   rsync -avz app/etc/* app/etc_shared/
   rsync -avz pub/media/* pub/media_shared/
   rsync -avz pub/static/* pub/static_shared/
   ```

1. `DEFAULT MOUNTS` ファイル内のマウント設定の `TEMPORARY SHARED MOUNTS` と `.magento.app.yaml` の部分をコメントアウトします。

   ```yaml
   #"var": "shared:files/var"
   #"app/etc": "shared:files/etc"
   #"pub/media": "shared:files/media"
   #"pub/static": "shared:files/static"
   
   #"var_shared":
   #    source: "service"
   #    service: "files"
   #    source_path: "var"
   #"app/etc_shared":
   #    source: "service"
   #    service: "files"
   #    source_path: "etc"
   #"pub/media_shared":
   #    source: "service"
   #    service: "files"
   #    source_path: "media"
   #"pub/static_shared":
   #    source: "service"
   #    service: "files"
   #    source_path: "static"
   ```

1. `OLD LOCAL MOUNTS` ファイルのマウント設定の `SHARED MOUNTS` と `.magento.app.yaml` の部分のコメントを解除します。

   ```yaml
   "var_old": "shared:files/var"
   "app/etc_old": "shared:files/etc"
   "pub/media_old": "shared:files/media"
   "pub/static_old": "shared:files/static"
   
   "var":
       source: "service"
       service: "files"
       source_path: "var"
   "app/etc":
       source: "service"
       service: "files"
       source_path: "etc"
   "pub/media":
       source: "service"
       service: "files"
       source_path: "media"
   "pub/static":
       source: "service"
       service: "files"
       source_path: "static"
   ```

1. 更新したファイルを Git インデックスに追加し、変更をコミットして、デプロイメントをトリガーにプッシュします。

   ```bash
   git add -f .magento.app.yaml
   git commit -m "Enabling AppServer: switch mounts"
   git push
   ```

1. `*_old` ディレクトリのファイルが実際のディレクトリに存在することを確認します。

1. 古いローカル マウントのクリーンアップ：

   ```bash
   rm -rf var_old/*
   rm -rf app/etc_old/*
   rm -rf pub/media_old/*
   rm -rf pub/static_old/*
   ```

1. `OLD LOCAL MOUNTS` ファイルのマウント設定の `.magento.app.yaml` の部分をコメントアウトします。

   ```yaml
   #"var_old": "shared:files/var"
   #"app/etc_old": "shared:files/etc"
   #"pub/media_old": "shared:files/media"
   #"pub/static_old": "shared:files/static"
   ```

1. 更新したファイルを Git インデックスに追加し、変更をコミットして、デプロイメントをトリガーにプッシュします。

   ```bash
   git add -f .magento.app.yaml
   git commit -m "Enabling AppServer: finish"
   git push
   ```

>[!NOTE]
>
>ルート `.magento.app.yaml` ファイル内のすべてのカスタム設定が、`application-server/.magento/.magento.app.yaml` ファイルに適切に移行されていることを確認します。 `application-server/.magento/.magento.app.yaml` ファイルがプロジェクトに追加されたら、ルート `.magento.app.yaml` ファイルに加えてそのファイルを保持する必要があります。 例えば、[RabbitMQ サービスを設定する ](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/configure/service/rabbitmq) または [web プロパティを管理する ](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/configure/app/properties/web-property) 必要がある場合、同じ設定を `application-server/.magento/.magento.app.yaml` にも追加する必要があります。

### クラウドプロジェクトでのイネーブルメントの検証

1. インスタンスに対してGraphQL クエリまたはミューテーションを実行し、`graphql` エンドポイントにアクセスできることを確認します。 例：

   ```
   mutation {  
    createEmptyCart
   }
   ```

   期待される応答は次の例のようになります。

   ```json
   {    
    "data": {        
        "createEmptyCart": "HLATPzcLw5ylDf76IC92nxdO2hXSXOrv"    
        }
    }
   ```

1. SSH を使用してクラウドインスタンスにアクセスします。 `project_root/var/log/application-server.log` には、GraphQL リクエストごとに新しいログレコードを含める必要があります。

1. また、次のコマンドを実行して、GraphQL Application Server が実行中かどうかを確認することもできます。

   ```bash
   ps aux|grep php
   ```

   複数のスレッドを持つ `bin/magento server:run` プロセスが表示されます。

これらの検証手順が正常に完了した場合、GraphQL Application Server は実行中で、`/graphql` リクエストを処理します。

## オンプレミスプロジェクトの有効化

`ApplicationServer` モジュール（`Magento/ApplicationServer/`）は、GraphQL API 用のGraphQL Application Server を有効にします。

GraphQL Application Server をローカルで実行するには、Swoole 拡張機能をインストールし、デプロイメントの Nginx 設定ファイルに小さな変更を加える必要があります。

### 前提条件

`ApplicationServer` モジュールを有効にする前に、次の手順を実行します。

* Nginx の設定
* Swoole v5+拡張機能のインストールと設定

#### Nginx の設定

Commerceの具体的なデプロイメントによって、Nginx の設定方法が決まります。 一般に、Nginx 設定ファイルはデフォルトで `nginx.conf` という名前で、`/usr/local/nginx/conf`、`/etc/nginx`、`/usr/local/etc/nginx` のいずれかのディレクトリに配置されます。 Nginx の設定の詳細については、_[初心者向けガイド ](https://nginx.org/en/docs/beginners_guide.html)_ を参照してください。

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

インストール時に、Adobe Commerceで `openssl`、`mysqlnd`、`sockets`、`http2` および `postgres` のサポートを有効にするよう求められます。 `yes` を除くすべてのオプションに対して `postgres` を入力します。

### Swoole のインストールの確認

拡張機能が正常に有効になったことを確認します。

```bash
php -m | grep swoole
```

### Swoole のインストールに関するよくあるエラー

Swoole のインストール中に発生するエラーは、通常、`pecl` のインストール段階で発生します。 一般的なエラーには、`openssl.h` ファイルと `pcre2.h` ファイルの欠落があります。 これらのエラーを解決するには、ローカルシステムにこれらの 2 つのパッケージがインストールされていることを確認します。

* 次のコマンドを実行して、`openssl` の場所を確認します。

```bash
openssl version -d
```

このコマンドは、`openssl` がインストールされているパスを表示します。

* 次のコマンドを実行して、`pcre2` の場所を確認します。

```bash
pcre2-config --prefix 
```

コマンド出力にファイルが見つからないことが示されている場合は、Homebrew を使用して、見つからないパッケージをインストールします。

```bash
brew install openssl
```

```bash
brew install pcre2
```

#### openssl の問題を解決

`openssl` に関連する問題を解決するには、次を実行します。

```bash
export LDFLAGS="-L/opt/homebrew/etc/openssl@3/lib" export CPPFLAGS="-I/opt/homebrew/etc/openssl@3/include"
```

ローカル `dev` 環境からのパスを使用していることを確認します。

#### Openssl 関連の問題の解決の確認

次のコマンドを再度実行すると、openssl 関連の問題が解決されたかどうかを確認できます。

```bash
pecl install swoole
```

#### pcre2.h の問題を解決

`pcre2.h` に関連する問題を解決するには、インストールされている PHP 拡張ディレクトリに `pcre2.h` パスをシンボリックリンクします。 使用するコマンドの特定のバージョンは、PHP および `pcr2.h` の特定のインストール済みバージョンによって決まります。

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

* `/var/log/application-server.log` ファイルで、処理されたGraphQL リクエストに関連するエントリを確認します。
* GraphQL Application Server を実行している HTTP ポートに接続してみます。 例：`curl -g 'http://localhost:9501/graph`。

### GraphQL リクエストが処理中であることを確認します

GraphQL Application Server は、処理する各リクエストに `X-Backend` 値を持つ `graphql_server` 応答ヘッダーを追加します。 GraphQL Application Server がリクエストを処理したかどうかを確認するには、この応答ヘッダーを確認します。

### 拡張機能とカスタマイズの互換性の確認

拡張機能の開発者とマーチャントは、まず、拡張機能とカスタマイズコードが _[テクニカルガイドライン ](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/)_ に記載されたガイドラインに従っていることを確認する必要があります。

コード評価時には、次のガイドラインを考慮してください。

* サービスクラス（動作を提供するがデータを提供しないクラス、`EventManager` など）には可変状態を指定しないでください。
* 時間結合を避けます。

## GraphQL Application Server の無効化

GraphQL Application Server を無効にする手順は、サーバーがオンプレミスとクラウドのどちらのデプロイメントで実行されているかによって異なります。

### GraphQL Application Server （Cloud）を無効にする

1. デプロイメントの準備中に、`AppServer Enabled` コミットに含まれていた新しいファイルとその他のコード変更をすべて削除します。

1. 次のコマンドを使用して変更をコミットします。

   ```bash
   git commit -m "AppServer Disabled"
   ```

1. 次のコマンドを使用して、これらの変更をデプロイします。

   ```bash
   git push
   ```

### GraphQL Application Server を無効にする（オンプレミス）

1. GraphQL Application Server を有効にするときに追加 `/graphql` たファイルの `nginx.conf` セクションをコメントアウトします。
1. nginx を再起動します。

GraphQL Application Server を無効にするこの方法は、パフォーマンスを迅速にテストまたは比較するのに役立ちます。

### GraphQL Application Server が無効になっていることを確認します。

`php-fpm` がGraphQL Application Server ではなくGraphQL リクエストを処理していることを確認するには、コマンド `ps aux | grep php` を入力します。

GraphQL Application Server が無効になった後：

* `bin/magento server:run` は非アクティブです。
* GraphQL リクエストの後に、`var/log/application-server.log` にエントリが含まれていません。

## GraphQL Application Server の統合および機能テスト

拡張機能の開発者は、2 つの統合テスト（`GraphQlStateTest` および `ResetAfterRequestTest`）を実行して、GraphQL Application Server との拡張機能の互換性を確認できます。

### GraphQlStateTest

`GraphQlStateTest` は、複数のリクエストで再利用してはいけない共有オブジェクトの状態を検出します。

このテストの目的は、`ObjectManager` で生成されるサービスオブジェクトの状態変化を検出することです。 このテストでは、同一のGraphQL クエリを 2 回実行し、2 回目のクエリの前後でサービスオブジェクトのステートを比較します。

#### GraphQlStateTest の失敗と潜在的な修正

* **リストの追加、スキップ、フィルタリングはできません**。 このエラーが発生した場合は、クラスをリファクタリングして、可変状態のサービスクラスに対してファクトリを使用するようにしてください。

* **クラスは可変状態を示します**。 クラス自体が可変状態を示す場合は、この状態を回避するようにコードを書き換えてみてください。 パフォーマンス上の理由で可変状態が必要な場合は、`ResetAfterRequestInterface` を実装し、`_resetState()` を使用してオブジェクトを初期構築状態にリセットします。

* **型指定されたプロパティ $x は初期化メッセージの前にアクセスできません**。 このタイプのメッセージでエラーが発生した場合は、指定されたプロパティがコンストラクターによって初期化されていないことを示します。 これは、オブジェクトが最初に作成された後で使用できないために発生する時間的結合の一種です。 プロパティからデータを取得するコレクタが PHP のリフレクション機能を使用しているため、プロパティがプライベートであっても、この結合が発生します。 この場合、クラスをリファクタリングして、時間結合を避け、可変状態を避けるようにしてください。 そのリファクタリングでエラーが解決されない場合は、プロパティタイプを nullable 型に変更して、null に初期化できるようにします。  プロパティが配列の場合は、プロパティを空の配列として初期化してみてください。

`GraphQlStateTest` を実行して `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/GraphQl/App/GraphQlStateTest.php` を実行します。

### ResetAfterRequestTest

この `ResetAfterRequestTest` は、`ResetAfterRequestInterface` を実装するすべてのクラスを検索し、`_resetState()` メソッドが `ObjectManager` によって構築された後に保持したのと同じ状態にオブジェクトの状態を返すことを確認します。  このテストでは、`ObjectManager` でサービスオブジェクトを作成してから、そのオブジェクトを複製し、`_resetState()` を呼び出して、両方のオブジェクトを比較します。 このテストでは、オブジェクトのインスタンス化と `_resetState()` の間でメソッドは呼び出されないので、可変状態のリセットは確認されません。 `_resetState()` のバグやタイプミスによって元の状態とは異なる状態に設定される可能性がある問題を見つけることができます。

#### ResetAfterRequestTest エラーと修復の可能性

* **クラスに一貫性のないプロパティ値があります**。 このテストが失敗した場合は、クラスが変更され、構築後のオブジェクトのプロパティ値が、`_resetState()` メソッドが呼び出された後のオブジェクトのプロパティ値と異なるかどうかを確認します。 作業中のクラスに `_resetState()` メソッド自体が含まれていない場合は、それを実装するスーパークラスのクラス階層を確認してください。

* **型指定されたプロパティ $x は初期化メッセージの前にアクセスできません**。 この問題は `GraphQlStateTest` でも発生します。

  `ResetAfterRequestTest` を実行して `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/Framework/ObjectManager/ResetAfterRequestTest.php` を実行します。

### 機能テスト

GraphQL Application Server のデプロイ中に、拡張機能の開発者は、WebAPI 機能テストと、GraphQLのカスタム自動または手動の機能テストを実行する必要があります。 これらの機能テストは、開発者が潜在的なエラーや互換性の問題を特定するのに役立ちます。

#### 状態監視モード

機能テスト（または手動テスト）の実行中に、GraphQL Application Server を `--state-monitor mode` を有効にして実行すると、ステートが意図せずに再利用されているクラスを見つけることができます。 `--state-monitor` パラメーターの追加を除き、アプリケーションサーバーを通常どおり起動します。

```
bin/magento server:run --state-monitor
```

各リクエストが処理されると、新しいファイルが `tmp` ディレクトリに追加されます（例：`var/tmp/StateMonitor-thread-output-50-6nmxiK`）。 テストが完了したら、これらのファイルは `bin/magento server:state-monitor:aggregate-output` コマンドを使用して結合でき、`XML` と `JSON` の 2 つの結合ファイルが作成されます。

例：

```
/var/workspace/var/tmp/StateMonitor-json-2024-04-10T18:50:39Z-hW0ucN.json
/var/workspace/var/tmp/StateMonitor-junit-2024-04-10T18:50:39Z-oreUco.xml
```

これらのファイルは、`GraphQlStateTest` のようなサービスオブジェクトの変更されたプロパティを表示する XML または JSON の表示に使用する任意のツールを使用して調べることができます。 `--state-monitor` モードでは、GraphQlStateTest と同じスキップリストとフィルターリストを使用します。

>[!NOTE]
>
>実稼動環境では `--state-monitor` モードを使用しないでください。 開発およびテストのみを目的として設計されています。 多数の出力ファイルが作成され、通常よりも実行速度が低下します。

>[!NOTE]
>
>`--state-monitor` は、PHP ガベージコレクターのバグにより、PHP バージョン `8.3.0` ～ `8.3.4` と互換性がありません。 PHP 8.3 を使用している場合、この機能を使用するには `8.3.5` 以降にアップグレードする必要があります。
