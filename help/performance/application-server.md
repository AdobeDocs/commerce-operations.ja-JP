---
title: GraphQL API 用アプリケーションサーバー
description: Adobe CommerceデプロイメントでGraphQL API 用のアプリケーションサーバーを有効にするには、以下の手順に従います。
badgeCoreBeta: label="2.4.7-beta1" type="informative"
exl-id: 346cc722-131e-4ed0-bc8c-23c3a1e58258
source-git-commit: f085c0a77fe59ff3b2d76abbd6965b6bc8ee69db
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# GraphQL API 用アプリケーションサーバー

GraphQL API 用 Commerce Application Server を使用すると、Adobe Commerceは Commerce GraphQL API リクエスト間の状態を維持でき、各リクエストのブートストラップ時間を短縮できます。 プロセス間でアプリケーション状態を共有することで、API リクエストの効率が大幅に向上します。

このベータ版の Application Server は、PHP 8.1 または 8.2 を実行するオンプレミスのデプロイメントにのみ使用できます。 クラウドベースのデプロイメントはサポートされていません。 B2B GraphQL機能はまだサポートされていません。 このバージョンの PHP アプリケーションサーバーが設定されている場合、オンプレミスデプロイメントでGraphQLの要求が期待どおりに動作しないことがあります。

## アプリケーションサーバーを使用できるユーザー

Application Server は、オンプレミスの Commerce の展開にのみ使用できます。

## GraphQL API 用のアプリケーションサーバーの有効化

The `ApplicationServer` モジュール (`Magento/ApplicationServer/`) は、GraphQL API 用の Application Server を有効にします。

Application Server を実行するには、Open Swoole 拡張機能をインストールする必要があります。また、このアプリケーションサーバーをローカルで実行するには、デプロイメントの Nginx 設定ファイルに若干の変更が必要です。

### 始める前に

次の 2 つの作業を完了してから、 `ApplicationServer` モジュール：

* Nginx の設定

* Open Swoole v22 拡張機能のインストールと設定

### Nginx の設定

特定のコマースデプロイメントによって、Nginx の設定方法が決まります。 一般に、Nginx 設定ファイルはデフォルトで、 `nginx.conf` は、次のいずれかのディレクトリに配置されます。 `/usr/local/nginx/conf`, `/etc/nginx`または `/usr/local/etc/nginx`. 詳しくは、 [初心者向けガイド](http://nginx.org/en/docs/beginners_guide.html) を参照してください。

Nginx 設定の例：

```conf
location /graphql {
    proxy_set_header Host $http_host;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

    proxy_pass http://127.0.0.1:9501/graphql;
}
```

### Open Swoole のインストールと設定

Application Server をローカルで実行するには、Open Swoole v22 拡張機能をインストールします。 この拡張機能は、複数の方法でインストールできます。

## アプリケーションサーバーを実行

アプリケーションサーバーを起動します。

```bash
bin/magento server:run
```

このコマンドは、9501 で HTTP ポートを開始します。 アプリケーションサーバーが起動すると、ポート 9501 は、すべてのGraphQLクエリの HTTP プロキシサーバーになります。

## 例：Open Swoole (OSX) のインストール

この手順は、OSX ベースのシステム用の PHP 8.2 に Open Swoole 拡張をインストールする方法を示します。 これは、Open Swoole 拡張機能をインストールするいくつかの方法の 1 つです。

Open Swoole extension for PHP (v22) と、この拡張機能が必要とする Composer パッケージの両方を 1 つのコマンドでインストールできます。

### Open Swoole のインストール

入力：

```bash
pecl install openswoole-22.0.0 | composer require openswoole/core:22.1.1
```

インストール中に、Adobe Commerceに、のサポートを有効にするプロンプトが表示されます。 `openssl`, `mysqlnd`, `sockets`, `http2`、および `postgres`. 入力 `yes` を除くすべてのオプション `postgres`.

### Open Swoole のインストールを確認

実行 `php -m | grep openswoole` 拡張機能が正常に有効化されたことを確認する。

### Open Swoole のインストールに関する一般的なエラー

Open Swoole のインストール中に発生したエラーは、通常、 `pecl` インストールフェーズ。 一般的なエラーには、が見つからないものが含まれます `openssl.h` および `pcre2.h` ファイル。 これらのエラーを解決するには、ローカルシステムにこれら 2 つのパッケージがインストールされていることを確認します。

* 次の場所を確認 `openssl` 実行別：

```bash
openssl version -d
```

このコマンドは、次の場所にあるパスを表示します。 `openssl` がインストールされている。

* 次の場所を確認 `pcre2` 実行別：

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
pecl install openswoole-22.0.0
```

#### pcre2.h の問題の解決

関連する問題を解決するには `pcre2.h`、symlink をクリックします。 `pcre2.h` インストールした PHP 拡張ディレクトリのパス。 PHP の特定のインストールバージョンと `pcr2.h` 使用する必要のあるコマンドの特定のバージョンを決定します。
