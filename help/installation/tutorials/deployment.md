---
title: デプロイメント設定の作成または更新
description: Adobe CommerceまたはMagento Open Sourceのデプロイメント設定を管理するには、次の手順に従います。
feature: Install, Deploy, Configuration
exl-id: 2cdde735-0c70-44e8-b2ee-ffb874c1c443
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '680'
ht-degree: 0%

---

# デプロイメント設定の作成または更新

このコマンドを使用するための前提条件はありません。

## デプロイメント設定の作成または更新

[デプロイメント設定](../../configuration/reference/deployment-files.md) アプリケーションの初期化とブートストラップに必要な情報を提供します。

このコマンドは、次の場合に使用できます。

* 以前にアプリケーションをインストールしており、配置設定を変更する場合
* デプロイメント設定のみを作成し、別の方法でインストールを続行する場合
* 他に影響を与えずにデプロイメント設定を更新するには

コマンドオプション：

```bash
bin/magento setup:config:set [--<parameter>=<value>, ...]
```

次の表に、インストール パラメータと値の意味を示します。

| パラメーター | 値 | 必須？ |
|--- |--- |--- |
| `--backend-frontname` | Uniform Resource Identifier （[URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)）を選択して、管理者にアクセスします。<br><br>悪用を防ぐために、admin, backend のような一般的な単語は使用しないことをお勧めします。 管理 URI には、英数字とアンダースコア文字（`_`）のみ。 | 不可 |
| `--db-host` | 次のいずれかを使用します。<br><br>- データベースサーバーの完全修飾ホスト名または IP アドレス。<br><br>- `localhost` （デフォルト）または `127.0.0.1` データベースサーバーが web サーバーと同じホスト上にある場合。 localhost は、MySQL クライアントライブラリが UNIX ソケットを使用してデータベースに接続することを意味します。 `127.0.0.1` クライアントライブラリで TCP プロトコルを使用します。 ソケットの詳細については、 [PHP PDO_MYSQL ドキュメント](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**注意：** オプションで、次のようなホスト名でデータベースサーバーポートを指定できます。 `www.example.com:9000` | 不可 |
| `--db-name` | データベーステーブルをインストールするデータベースインスタンスの名前。<br><br>デフォルトは `magento2`. | 不可 |
| `--db-user` | データベース・インスタンス所有者のユーザー名。<br><br>デフォルトは `root`. | 不可 |
| `--db-password` | データベースインスタンス所有者のパスワード。 | 不可 |
| `--db-prefix` | 既にAdobe Commerce テーブルが含まれているデータベースインスタンスにデータベーステーブルをインストールしている場合にのみ、を使用します。<br><br>その場合は、プレフィックスを使用して、このインストールのテーブルを識別します。 一部のお客様は、1 台のサーバーで複数のAdobe CommerceまたはMagento Open Sourceインスタンスが実行されており、そのサーバー内のすべてのテーブルが同じデータベース内にある場合があります。<br><br>プレフィックスの長さは最大 5 文字です。 文字で始まる必要があり、文字、数字、アンダースコア文字のみを含めることができます。<br><br>このオプションを選択すると、複数のAdobe CommerceまたはMagento Open Sourceのインストールでデータベースサーバーを共有できます。 | 不可 |
| `--session-save` | 次のいずれかを使用します。<br><br>- `db` セッションデータをに保存する [データベース](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/). クラスター化されたデータベースがある場合は、データベースストレージを選択します。そうしないと、ファイルベースのストレージに比べて大きなメリットがない可能性があります。<br><br>- `files` セッションデータをファイルシステムに格納する。 ファイルベースのセッションストレージは、ファイルシステムアクセスが遅い場合、クラスター化されたデータベースがある場合、または Redis にセッションデータを保存する場合を除いて、適切です。<br><br>- `redis` セッションデータを次に保存します [セッションストレージに Redis を使用](../../configuration/cache/config-redis.md). デフォルトまたはページキャッシュに Redis を使用している場合は、Redis がインストールされている必要があります。 | 不可 |
| `--key` | 暗号化するキーがある場合は、指定します [機密データ](#sensitive-data) データベース内にあります。 ユーザーが定義されていない場合は、自動的に定義されます。 | 不可 |
| `--db-init-statements` | MySQL の詳細設定パラメーター。 データベース初期化文を使用して、MySQL データベースへの接続時に実行します。<br><br>デフォルトは `SET NAMES utf8;`.<br><br>～に類似した参考文献を参照する [この 1](https://dev.mysql.com/doc/refman/5.6/en/server-options.html) 値を設定する前に行います。 | 不可 |
| `--http-cache-hosts` | パージリクエストの送信先の HTTP キャッシュゲートウェイホストのコンマ区切りリスト。 （例：Varnish サーバー）。 このパラメーターを使用して、同じリクエストでパージする 1 つ以上のホストを指定します。 （ホストが 1 つだけの場合でも、多数のホストがある場合でも関係ありません）。<br><br>形式はでなければなりません `<hostname or ip>:<listen port>`。を省略できます `<listen port>` ポート 80 の場合。 例： `--http-cache-hosts=192.0.2.100,192.0.2.155:6081`. ホストをスペース文字で区切らないでください。 | 不可 |

## 設定データの読み込み

実稼動システムを設定する場合は、次の場所から設定を読み込むことをお勧めします `config.php` および `env.php` をデータベースに追加します。
これらの設定には、設定パスと値、web サイト、ストア、ストアビュー、テーマが含まれます。

Web サイト、ストア、ストアビュー、テーマを読み込んだ後、製品属性を作成して、実稼動システムの web サイト、ストア、ストアビューに適用できます。

実稼動システムで、次のコマンドを実行して設定ファイル（`config.php` および `env.php`）を選択します。

```bash
bin/magento app:config:import [-n, --no-interaction]
```

オプション `[-n, --no-interaction]` フラグを使用すると、確認を追加せずにコマンドを実行できます。

詳しくは、 [設定ファイルからのデータの読み込み](../../configuration/cli/import-configuration.md)

### 機密データ

{{$include /help/_includes/sensitive-data.md}}
