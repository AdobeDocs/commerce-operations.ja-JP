---
title: GraphQL Application Server
description: Adobe Commerceのgraphql アプリケーションサーバーについて説明します。 導入に関するガイダンスと最適化戦略。
exl-id: 9b223d92-0040-4196-893b-2cf52245ec33
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '2464'
ht-degree: 0%

---


# GraphQL Application Server

Commerce GraphQL Application Serverを使用すると、Adobe CommerceはCommerce GraphQL API リクエスト間のステートを維持できます。 Swoole拡張機能で構築されているGraphQL Application Serverは、リクエスト処理を処理するワーカースレッドを持つプロセスとして動作します。 GraphQL API リクエスト間でブートストラップされたアプリケーションのステートを保持することで、GraphQL Application Serverはリクエスト処理と全体的な製品パフォーマンスを向上させます。 API リクエストが大幅に効率化されます。

GraphQL Application Serverは、Adobe Commerceでのみ使用できます。 Magento Open Sourceでは使用できません。 Cloud Pro プロジェクトの場合、GraphQL Application Serverを有効にするには、[Adobe Commerce サポート &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) チケットを送信する必要があります。

>[!NOTE]
>
>GraphQL Application Serverは現在[[!DNL Amazon Simple Storage Service (AWS S3)]](https://aws.amazon.com/s3/)と互換性がありません。 [&#x200B; リモートストレージ &#x200B;](../configuration/remote-storage/cloud-support.md)で[!DNL AWS S3]を現在使用しているクラウドインフラストラクチャ上のAdobe Commerceのお客様は、GraphQL Application Serverを使用できません。

## デザイン

GraphQL Application Serverは、Commerce GraphQL API リクエスト間のステートを維持し、ブートストラップを不要にします。 プロセス全体でアプリケーションの状態を共有することで、GraphQLリクエストの効率が大幅に向上し、応答時間が最大30%短縮されました。

共有なしPHP実行モデルは、各リクエストにフレームワークのブートストラップが必要なため、レイテンシの観点から課題を提供します。 このブートストラッププロセスには、設定の読み取り、ブートストラッププロセスの設定、サービスクラスオブジェクトの作成など、時間のかかるタスクが含まれます。

リクエスト処理ロジックをアプリケーションレベルのイベントループに移行すると、エンタープライズレベルでリクエスト処理を合理化するという課題に対処するようです。 このアプローチにより、リクエスト実行ライフサイクル中にブートストラップを実行する必要がなくなります。

## 利点

GraphQL Application Serverを使用すると、Adobe Commerceは連続したCommerce GraphQL API リクエスト間のステートを維持できます。 リクエスト間でアプリケーションの状態を共有することで、処理のオーバーヘッドを最小限に抑え、リクエスト処理を最適化することで、API リクエストの効率を高めます。 その結果、GraphQLのリクエストへの対応時間を最大30%短縮できます。

## 必要システム構成

GraphQL Application Serverを実行するには、次の操作が必要です。

* Commerce バージョン 2.4.7以降
* PHP 8.2以降
* 予想される負荷に基づく適切なRAMとCPU
* Swoole PHP拡張機能v5+（以下のプロジェクト固有の要件を参照）

### クラウドプロジェクト

Adobe Commerce オンクラウドインフラストラクチャプロジェクトには、デフォルトでSwoole拡張機能が含まれています。 `.magento.app.yaml` ファイルの`runtime` プロパティで[有効にする](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/php-settings#enable-extensions)ことができます。 例：

```yaml
runtime:
    extensions:
        - swoole
```

### オンプレミスプロジェクト

オンプレミス プロジェクトのSwoole PHP拡張機能を手動で[&#x200B; インストールして設定](#install-and-configure-swoole)する必要があります。

## クラウドインフラストラクチャの有効化とデプロイ

`ApplicationServer` モジュール （`Magento/ApplicationServer/`）は、GraphQL Application Serverを有効にします。

### Pro プロジェクトを有効にする

>[!NOTE]
>
>Application Serverは、Cloud Pro インスタンスのオプトイン機能です。 これを有効にするには、サポートリクエストを送信します。

Pro プロジェクトでApplication Server機能を有効にした後、GraphQL Application Serverをデプロイする前に次の手順を実行します。

1. [2.4.7-appserver ブランチ &#x200B;](https://github.com/magento/magento-cloud/tree/2.4.7-appserver)のクラウドテンプレートを使用して、Adobe Commerceをクラウドインフラストラクチャにデプロイします。
1. すべてのCommerce カスタマイズと拡張機能が[GraphQL Application Serverと互換性があることを確認してください。](https://developer.adobe.com/commerce/php/development/components/app-server/)
1. Commerce Cloud プロジェクトを複製します。
1. 必要に応じて、「application-server/nginx.conf.sample」ファイルの設定を調整します。
1. `project_root/.magento.app.yaml` ファイル内のアクティブな「web」セクションを完全にコメントします。
1. GraphQL Application Server `start` コマンドを含む`project_root/.magento.app.yaml` ファイルで、次の「web」セクション設定のコメントを解除します。

   ```yaml
   web:
       upstream:
           socket_family: tcp
           protocol: http
       commands:
           start: ./application-server/start.sh > var/log/application-server-status.log 2>&1
   ```

1. 次のコマンドを実行して、`/application-server/start.sh`が実行可能であることを確認します。

   ```shell
   chmod +x application-server/start.sh
   ```

1. 次のコマンドを使用して、更新されたファイルをGit インデックスに追加します。

   ```shell
   git add -f .magento.app.yaml application-server/*
   ```

1. 次のコマンドで変更をコミットします。

   ```shell
   git commit -m "AppServer Enabled"
   ```

### Pro プロジェクトのデプロイ

イネーブルメント手順が完了したら、Git リポジトリに変更をプッシュして、GraphQL Application Serverをデプロイします。

```shell
git push
```

### スタータープロジェクトの有効化

スタータープロジェクトにGraphQL Application Serverをデプロイする前に、次の手順を実行します。

1. [2.4.7-appserver ブランチ &#x200B;](https://github.com/magento/magento-cloud/tree/2.4.7-appserver)のクラウドテンプレートを使用して、Adobe Commerceをクラウドインフラストラクチャにデプロイします。
1. Commerceのすべてのカスタマイズと拡張機能がGraphQL Application Serverと互換性があることを確認します。
1. インスタンスに`CRYPT_KEY`環境変数が設定されていることを確認します。 この変数のステータスは、Cloud Consoleで確認できます。
1. Commerce Cloud プロジェクトを複製します。
1. `application-server/.magento/.magento.app.yaml.sample`の名前を`application-server/.magento/.magento.app.yaml`に変更し、必要に応じて.magento.app.yamlの設定を調整します。
1. `/graphql` トラフィックをGraphQL Application Serverにリダイレクトするには、`project_root/.magento/routes.yaml` ファイルで次のルートの設定のコメントを解除します。

   ```yaml
   "http://{all}/graphql":
       type: upstream
       upstream: "application-server:http"
   ```

1. `.magento/services.yaml` ファイルの`files` セクションのコメントを解除します。

   ```yaml
   files:
       type: network-storage:2.0
       disk: 5120
   ```

1. `.magento.app.yaml` ファイルのマウント設定の`TEMPORARY SHARED MOUNTS`部分のコメントを解除します。

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

1. 更新されたファイルをGit インデックスに追加します。

   ```shell
   git add -f .magento.app.yaml .magento/routes.yaml .magento/services.yaml application-server/.magento/*
   ```

1. 変更を確定し、デプロイメントのトリガーにプッシュします。

   ```shell
   git commit -m "Enabling AppServer: initial changes"
   git push
   ```

1. SSHを使用してリモートクラウド環境にログインします（`application-server` アプリの&#x200B;_not_）。

   ```shell
   magento-cloud ssh -p <project-ID> -e <environment-ID>
   ```

1. ローカルマウントから共有マウントにデータを同期します。

   ```shell
   rsync -avz var/* var_shared/
   rsync -avz app/etc/* app/etc_shared/
   rsync -avz pub/media/* pub/media_shared/
   rsync -avz pub/static/* pub/static_shared/
   ```

1. `DEFAULT MOUNTS`とマウント設定の`TEMPORARY SHARED MOUNTS`部分を`.magento.app.yaml` ファイルにコメントアウトします。

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

1. `.magento.app.yaml` ファイルのマウント設定の`OLD LOCAL MOUNTS`と`SHARED MOUNTS`部分のコメントを解除します。

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

1. 更新されたファイルをGit インデックスに追加し、変更をコミットして、デプロイメントをトリガーにプッシュします。

   ```shell
   git add -f .magento.app.yaml
   git commit -m "Enabling AppServer: switch mounts"
   git push
   ```

1. `*_old` ディレクトリのファイルが実際のディレクトリに存在することを確認します。

1. 古いローカルマウントのクリーンアップ：

   ```shell
   rm -rf var_old/*
   rm -rf app/etc_old/*
   rm -rf pub/media_old/*
   rm -rf pub/static_old/*
   ```

1. マウント設定の`OLD LOCAL MOUNTS`部分を`.magento.app.yaml` ファイルにコメントします。

   ```yaml
   #"var_old": "shared:files/var"
   #"app/etc_old": "shared:files/etc"
   #"pub/media_old": "shared:files/media"
   #"pub/static_old": "shared:files/static"
   ```

1. 更新されたファイルをGit インデックスに追加し、変更をコミットして、デプロイメントをトリガーにプッシュします。

   ```shell
   git add -f .magento.app.yaml
   git commit -m "Enabling AppServer: finish"
   git push
   ```

>[!NOTE]
>
>ルート `.magento.app.yaml` ファイルのすべてのカスタム設定が`application-server/.magento/.magento.app.yaml` ファイルに適切に移行されていることを確認します。 `application-server/.magento/.magento.app.yaml` ファイルをプロジェクトに追加した後、ルート `.magento.app.yaml` ファイルに加えてファイルを管理する必要があります。 例えば、[RabbitMQ サービス &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/rabbitmq)または[web プロパティを管理](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/properties/web-property)する必要がある場合は、`application-server/.magento/.magento.app.yaml`にも同じ設定を追加する必要があります。

### クラウドプロジェクトでのイネーブルメントの確認

1. インスタンスに対してGraphQL クエリまたはミューテーションを実行し、`graphql` エンドポイントにアクセスできることを確認します。 例：

   ```graphql
   mutation {  
    createEmptyCart
   }
   ```

   期待される応答は、次の例のようになります。

   ```json
   {    
    "data": {        
        "createEmptyCart": "HLATPzcLw5ylDf76IC92nxdO2hXSXOrv"    
        }
    }
   ```

1. クラウドインスタンスにアクセスするには、SSHを使用します。 `project_root/var/log/application-server.log`には、GraphQL リクエストごとに新しいログレコードを含める必要があります。

1. また、次のコマンドを実行して、GraphQL Application Serverが実行されているかどうかを確認することもできます。

   ```shell
   ps aux|grep php
   ```

   複数のスレッドを持つ`bin/magento server:run` プロセスが表示されます。

これらの検証手順が正常に実行された場合、GraphQL Application Serverは実行中で、`/graphql`件のリクエストを処理しています。

## オンプレミスプロジェクトの有効化

`ApplicationServer` モジュール （`Magento/ApplicationServer/`）は、GraphQL API用のGraphQL Application Serverを有効にします。

GraphQL Application Serverをローカルで実行するには、Swoole拡張機能のインストールと、デプロイメントのNginx設定ファイルのマイナーな変更が必要です。

### 前提条件

`ApplicationServer` モジュールを有効にする前に、次の手順を実行します。

* Nginxの設定
* Swoole v5+拡張機能のインストールと設定

#### Nginxの設定

Commerceのデプロイメントによって、Nginxの設定方法が決まります。 一般に、Nginx設定ファイルはデフォルトで`nginx.conf`という名前で、次のいずれかのディレクトリ（`/usr/local/nginx/conf`、`/etc/nginx`、または`/usr/local/etc/nginx`）に配置されます。 Nginxの設定について詳しくは、_[初心者向けガイド &#x200B;](https://nginx.org/en/docs/beginners_guide.html)_&#x200B;を参照してください。

Nginx設定の例：

```conf
location /graphql {
    proxy_set_header Host $http_host;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

    proxy_pass http://127.0.0.1:9501/graphql;
}
```

#### Swooleのインストールと設定

GraphQL Application Serverをローカルで実行するには、Swoole拡張機能（v5.0以降）をインストールします。 この拡張機能をインストールするには、複数の方法があります。

次の手順では、OSX ベースのシステムにPHP 8.2用のSwoole拡張機能をインストールする方法について説明します。 Swoole拡張機能をインストールするいくつかの方法の1つです。

```shell
pecl install swoole
```

インストール中に、Adobe Commerceに、`openssl`、`mysqlnd`、`sockets`、`http2`、および`postgres`のサポートを有効にするためのプロンプトが表示されます。 `postgres`を除くすべてのオプションに対して`yes`と入力します。

### Swoole インストールの確認

拡張機能が正常に有効になっていることを確認します。

```shell
php -m | grep swoole
```

### Swoole インストールの一般的なエラー

Swooleのインストール中に発生するエラーは、通常、`pecl` インストール フェーズで発生します。 一般的なエラーには、`openssl.h`と`pcre2.h`個のファイルがありません。 これらのエラーを解決するには、これらの2つのパッケージがローカルシステムにインストールされていることを確認します。

* 次を実行して、`openssl`の場所を確認します：

```shell
openssl version -d
```

このコマンドは、`openssl`がインストールされているパスを示します。

* 次を実行して、`pcre2`の場所を確認します：

```shell
pcre2-config --prefix 
```

コマンド出力でファイルが見つからないことが示された場合は、Homebrewを使用して見つからないパッケージをインストールします。

```shell
brew install openssl
```

```shell
brew install pcre2
```

#### opensslの問題を解決する

`openssl`に関連する問題を解決するには、次を実行します。

```shell
export LDFLAGS="-L/opt/homebrew/etc/openssl@3/lib" export CPPFLAGS="-I/opt/homebrew/etc/openssl@3/include"
```

ローカル `dev`環境のパスを使用していることを確認してください。

#### openssl関連の問題の解決を確認する

次のコマンドを再度実行して、openssl関連の問題が解決されたかどうかを確認できます。

```shell
pecl install swoole
```

#### pcre2.hの問題を解決する

`pcre2.h`に関する問題を解決するには、インストールされているPHP拡張ディレクトリに`pcre2.h` パスをシンボリックリンクします。 インストールされている特定のバージョンのPHPと`pcr2.h`によって、使用するコマンドの特定のバージョンが決まります。

### GraphQL Application Serverの実行

GraphQL Application Serverを起動します。

```shell
bin/magento server:run
```

このコマンドは、9501でHTTP ポートを開始します。 GraphQL Application Serverが起動すると、ポート 9501はすべてのGraphQL クエリのHTTP プロキシサーバーになります。

GraphQL Application Serverがデプロイメントで実行されていることを確認するには、次の手順を実行します。

```shell
ps aux | grep php
```

GraphQL Application Serverが実行中であることを確認する追加の方法は次のとおりです。

* 処理済みのGraphQL リクエストに関連するエントリについては、`/var/log/application-server.log` ファイルを確認してください。
* GraphQL Application Serverが実行するHTTP ポートへの接続を試みます。 例：`curl -g 'http://localhost:9501/graph`。

### GraphQL リクエストが処理中であることを確認します

GraphQL Application Serverは、処理する各リクエストに、値`graphql_server`の`X-Backend`応答ヘッダーを追加します。 GraphQL Application Serverがリクエストを処理したかどうかを確認するには、この応答ヘッダーを確認します。

### 拡張機能とカスタマイズの互換性を確認

拡張機能の開発者と販売者は、最初に、拡張機能とカスタマイズ コードが&#x200B;_[テクニカル ガイドライン &#x200B;](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/)_&#x200B;に記載されているガイドラインに準拠していることを確認する必要があります。

コードの評価時に、次のガイドラインを検討します。

* サービス クラス （つまり、`EventManager`など、動作を提供するがデータを提供しないクラス）には、可変ステートを設定しないでください。
* 一時的な結合を避ける。

## GraphQL Application Serverを無効にする

GraphQL Application Serverを無効にする手順は、サーバーがオンプレミスまたはクラウドのデプロイメントで実行されているかどうかによって異なります。

### GraphQL Application Server （cloud）を無効にする

1. デプロイメントの準備中に`AppServer Enabled` コミットに含まれていた新しいファイルやその他のコード変更を削除します。

1. 次のコマンドを使用して変更をコミットします。

   ```shell
   git commit -m "AppServer Disabled"
   ```

1. 次のコマンドを使用して、これらの変更をデプロイします。

   ```shell
   git push
   ```

### GraphQL Application Serverを無効にする（オンプレミス）

1. GraphQL Application Serverを有効にする際に追加した`nginx.conf` ファイルの`/graphql` セクションをコメントアウトします。
1. nginxを再起動します。

GraphQL Application Serverを無効にするこの方法は、パフォーマンスを迅速にテストまたは比較するのに便利です。

### GraphQL Application Serverが無効になっていることを確認します

`php-fpm`がGraphQL Application ServerではなくGraphQL リクエストを処理していることを確認するには、次のコマンドを入力します：`ps aux | grep php`。

GraphQL Application Serverを無効にした後：

* `bin/magento server:run`は非アクティブです。
* `var/log/application-server.log`には、GraphQL リクエストの後にエントリが含まれていません。

## GraphQL Application Serverの統合テストと機能テスト

拡張機能の開発者は、2つの統合テストを実行して、GraphQL Application Serverとの拡張機能の互換性を検証できます：`GraphQlStateTest`と`ResetAfterRequestTest`。

### GraphQlStateTest

`GraphQlStateTest`は、複数の要求に再利用できない共有オブジェクトの状態を検出します。

このテストは、`ObjectManager`が生成するサービス オブジェクトの状態の変更を検出するように設計されています。 テストでは、同じGraphQL クエリを2回実行し、2回目のクエリの前後でサービスオブジェクトの状態を比較します。

#### GraphQlStateTestのエラーと潜在的な修正

* **リストを追加、スキップ、またはフィルターできません**。 このエラーが発生した場合は、可変ステートのサービスクラスにファクトリを使用するようにクラスをリファクタリングしてみてください。

* **クラスに可変ステートが表示されます**。 クラス自体が可変ステートを示す場合は、このステートを回避するためにコードを書き換えてみてください。 パフォーマンス上の理由から可変ステートが必要な場合は、`ResetAfterRequestInterface`を実装し、`_resetState()`を使用して、オブジェクトを最初に構築されたステートにリセットします。

* **初期化メッセージ**&#x200B;の前に、入力されたプロパティ $xにアクセスすることはできません。 このタイプのメッセージでエラーが発生した場合は、指定したプロパティがコンストラクターによって初期化されていないことが示されます。 これは、オブジェクトが最初に構築された後に使用できないため、時間的な結合の一形態です。 プロパティからデータを取得するCollectorがPHP リフレクション機能を使用しているため、プロパティがプライベートである場合でも、この結合が発生します。 この場合は、時間的な結合を避け、可変状態を避けるために、クラスをリファクタリングしてみてください。 リファクタリングで失敗が解決しない場合は、プロパティタイプをnull可能なタイプに変更して、nullに初期化できます。  プロパティが配列の場合は、プロパティを空の配列として初期化してみてください。

`vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/GraphQl/App/GraphQlStateTest.php`を実行して`GraphQlStateTest`を実行します。

### ResetAfterRequestTest

`ResetAfterRequestTest`は、`ResetAfterRequestInterface`を実装するすべてのクラスを検索し、`_resetState()` メソッドが、`ObjectManager`によって構築された後に保持した状態と同じ状態にオブジェクトの状態を返すことを確認します。  このテストでは、`ObjectManager`を含むサービスオブジェクトを作成し、そのオブジェクトを複製して`_resetState()`を呼び出し、両方のオブジェクトを比較します。 このテストでは、オブジェクトのインスタンス化と`_resetState()`の間のメソッドは呼び出されないので、変更可能な状態のリセットは確認されません。 `_resetState()`のバグまたはタイプミスが元の状態とは異なる状態に設定される可能性がある問題が見つかります。

#### ResetAfterRequestTestのエラーと潜在的な修正

* **クラスに一貫しないプロパティ値**&#x200B;があります。 このテストが失敗した場合は、クラスが変更されたかどうかを確認し、`_resetState()` メソッドが呼び出された後のオブジェクトのプロパティ値と、コンストラクション後のオブジェクトのプロパティ値が異なることを確認します。 作業中のクラスに`_resetState()` メソッド自体が含まれていない場合は、それを実装するスーパークラスのクラス階層を確認してください。

* **初期化メッセージ**&#x200B;の前に、入力されたプロパティ $xにアクセスすることはできません。 この問題は`GraphQlStateTest`でも発生します。

  実行して`ResetAfterRequestTest`を実行：`vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/Framework/ObjectManager/ResetAfterRequestTest.php`。

### 機能テスト

GraphQL Application Serverのデプロイ時に、拡張機能の開発者はWebAPI機能テストと、GraphQLのカスタム機能テストの自動または手動テストを実行する必要があります。 これらの機能テストは、開発者が潜在的なエラーや互換性の問題を特定するのに役立ちます。

#### 状態モニターモード

機能テスト （または手動テスト）の実行中に、GraphQL Application Serverは`--state-monitor mode`を有効にして実行し、ステートが意図せず再利用されているクラスを見つけるのに役立てることができます。 `--state-monitor` パラメーターを追加する場合を除き、通常どおりアプリケーションサーバーを起動します。

```shell
bin/magento server:run --state-monitor
```

各リクエストが処理されると、新しいファイルが`tmp` ディレクトリに追加されます（例：`var/tmp/StateMonitor-thread-output-50-6nmxiK`）。 テストが完了すると、これらのファイルを`bin/magento server:state-monitor:aggregate-output` コマンドと結合して、`XML`と`JSON`の2つの結合ファイルを作成できます。

例：

```text
/var/workspace/var/tmp/StateMonitor-json-2024-04-10T18:50:39Z-hW0ucN.json
/var/workspace/var/tmp/StateMonitor-junit-2024-04-10T18:50:39Z-oreUco.xml
```

これらのファイルは、`GraphQlStateTest`のようにサービスオブジェクトの変更されたプロパティを示すXMLまたはJSONを表示するために使用する任意のツールで検査できます。 `--state-monitor` モードでは、GraphQlStateTestと同じスキップリストとフィルターリストが使用されます。

>[!NOTE]
>
>実稼動環境では`--state-monitor` モードを使用しないでください。 開発とテスト専用に設計されています。 多くの出力ファイルを作成し、通常よりも動作が遅くなります。

>[!NOTE]
>
>`--state-monitor`は、PHP ガベージコレクターのバグにより、PHP バージョン `8.3.0` ～ `8.3.4`と互換性がありません。 PHP 8.3を使用している場合、この機能を使用するには`8.3.5`以降にアップグレードする必要があります。

## クライアント IP検出のための代替ヘッダーの設定

デフォルトでは、GraphQL Application Serverは`app/etc/di.xml` ファイルで定義された`x-forwarded-for` ヘッダーの標準設定をサポートしており、一般的なプロキシ環境およびCDN環境でクライアント IP アドレスを正確に取得できます。

追加ヘッダーまたはカスタムヘッダー（`x-client-ip`、`fastly-client-ip`、`x-real-ip`など）をサポートする必要がある場合は、`app/etc/di.xml` ファイルの`alternativeHeaders`引数を拡張または上書きできます。 これは、環境で`x-forwarded-for`以外のヘッダーを使用してクライアント IP アドレスを渡す場合にのみ必要です。

例えば、他のヘッダーのサポートを追加するには、次のように`app/etc/di.xml`を更新します。

```xml
<type name="Magento\Framework\HTTP\PhpEnvironment\RemoteAddress">
    <arguments>
        <argument name="alternativeHeaders" xsi:type="array">
            <item name="x-client-ip" xsi:type="string">HTTP_X_CLIENT_IP</item>
            <item name="fastly-client-ip" xsi:type="string">HTTP_FASTLY_CLIENT_IP</item>
            <item name="x-real-ip" xsi:type="string">HTTP_X_REAL_IP</item>
            <item name="x-forwarded-for" xsi:type="string">HTTP_X_FORWARDED_FOR</item>
        </argument>
    </arguments>
</type>
```

必要に応じてヘッダーを追加、削除、または並べ替えることで、設定の正しいソースからクライアント IPを取得できます。

>[!NOTE]
>
>Fastly CDN モジュールでAdobe Commerce Cloudを使用している場合、この設定は自動的に処理され、手動での変更は必要ありません。 手動による設定は、カスタム CDN、プロキシ、または非標準ヘッダーの設定に対してのみ必要です。
