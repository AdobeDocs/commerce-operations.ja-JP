---
title: デプロイメント設定を作成または更新する
description: 次の手順に従って、Adobe CommerceまたはMagento Open Sourceのデプロイメント設定を管理します。
feature: Install, Deploy, Configuration
exl-id: 2cdde735-0c70-44e8-b2ee-ffb874c1c443
source-git-commit: ce405a6bb548b177427e4c02640ce13149c48aff
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 0%

---

# デプロイメント設定を作成または更新する

このコマンドを使用するための前提条件はありません。

## デプロイメント設定を作成または更新する

[デプロイメント設定](../../configuration/reference/deployment-files.md) は、アプリケーションが初期化およびブートストラップに必要な情報を提供します。

次の場合に、このコマンドを使用できます。

* 以前にアプリケーションをインストールし、デプロイメント設定を変更する
* 配置設定のみを作成し、別の方法でインストールを続行する場合
* 他に影響を与えずにデプロイメント設定を更新するには

コマンドオプション：

```bash
bin/magento setup:config:set [--<parameter>=<value>, ...]
```

次の表に、インストールパラメータと値の意味を示します。

| パラメーター | 値 | 必須？ |
|--- |--- |--- |
| `--backend-frontname` | Uniform Resource Identifier ([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)) をクリックして管理者にアクセスします。<br><br>悪用を防ぐために、admin や backend などの一般的な単語は使用しないことをお勧めします。 管理 URI には、英数字とアンダースコア文字 (`_`) のみを読み込みます。 | いいえ |
| `--db-host` | 次のいずれかを使用します。<br><br> — データベース・サーバの完全修飾ホスト名または IP アドレス。<br><br>- `localhost` （デフォルト）または `127.0.0.1` データベース・サーバが web サーバと同じホスト上にある場合。 localhost は、MySQL クライアントライブラリが UNIX ソケットを使用してデータベースに接続することを意味します。 `127.0.0.1` を指定すると、クライアントライブラリは TCP プロトコルを使用します。 ソケットの詳細については、 [PHP PDO_MYSQL ドキュメント](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**注意：** 必要に応じて、データベース・サーバ・ポートをホスト名で指定できます。 `www.example.com:9000` | いいえ |
| `--db-name` | データベーステーブルをインストールするデータベースインスタンスの名前。<br><br>デフォルトはです。 `magento2`. | いいえ |
| `--db-user` | データベースインスタンスの所有者のユーザー名。<br><br>デフォルトはです。 `root`. | いいえ |
| `--db-password` | データベースインスタンスの所有者のパスワード。 | いいえ |
| `--db-prefix` | 既にデータベーステーブルとMagento Open Sourceテーブルを含むデータベースインスタンスにデータベーステーブルをインストールする場合にのみ使用してください。<br><br>この場合は、プレフィックスを使用して、このインストール用のテーブルを識別します。 1 台のサーバー上で複数のAdobe CommerceまたはMagento Open Sourceインスタンスを実行し、同じデータベース内のすべてのテーブルを含むお客様もいます。<br><br>プレフィックスの長さは最大 5 文字です。 文字で始まる必要があり、文字、数字、アンダースコア文字のみを含めることができます。<br><br>このオプションを使用すると、お客様は、複数のAdobe CommerceまたはMagento Open Sourceのインストールでデータベースサーバーを共有できます。 | いいえ |
| `--session-save` | 次のいずれかを使用します。<br><br>- `db` セッションデータを [データベース](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/). クラスタ化されたデータベースがある場合は、データベースストレージを選択します。選択しない場合は、ファイルベースのストレージよりも多くのメリットが得られない可能性があります。<br><br>- `files` を使用して、セッションデータをファイルシステムに保存します。 ファイルシステムのアクセスが遅い場合や、クラスタ化されたデータベースが存在する場合、またはセッションデータを Redis に格納する場合を除き、ファイルベースのセッションストレージが適切です。<br><br>- `redis` セッションデータをに保存する [セッションストレージに Redis を使用](../../configuration/cache/config-redis.md). Redis をデフォルトまたはページキャッシュに使用している場合は、Redis が既にインストールされている必要があります。 | いいえ |
| `--key` | 1 つのキーがある場合は、暗号化するキーを指定します [機密データ](#sensitive-data) をデータベースに追加します。 1 つもない場合は、アプリケーションによって生成されます。 | いいえ |
| `--db-init-statements` | MySQL 設定の詳細パラメーター。 MySQL データベースへの接続時に、データベース初期化文を使用して実行します。<br><br>デフォルトはです。 `SET NAMES utf8;`.<br><br>次のような参照を参照してください。 [この 1 人は](https://dev.mysql.com/doc/refman/5.6/en/server-options.html) 値を設定する前に、を設定します。 | いいえ |
| `--http-cache-hosts` | パージ要求の送信先となる HTTP キャッシュゲートウェイホストのコンマ区切りリスト。 （たとえば、Vanish サーバなど）。 同じ要求内でパージするホストを指定するには、このパラメーターを使用します。 （ホストが 1 つだけの場合や複数のホストが存在する場合は問題になりません）。<br><br>形式は次の条件を満たす必要があります `<hostname or ip>:<listen port>`を指定します。ここで、 `<listen port>` （ポート 80 の場合）。 例： `--http-cache-hosts=192.0.2.100,192.0.2.155:6081`. ホストをスペース文字で区切らないでください。 | いいえ |

## 設定データを読み込む

実稼動システムを設定する場合は、から設定を読み込むことをお勧めします。 `config.php` および `env.php` をデータベースに追加します。
これらの設定には、設定パスと値、Web サイト、ストア、ストア表示、テーマが含まれます。

Web サイト、ストア、ストアの表示、テーマを読み込んだ後、製品属性を作成し、実稼動システム上の Web サイト、ストア、ストアの表示に適用できます。

実稼動システムで、次のコマンドを実行して設定ファイル (`config.php` および `env.php`) をデータベースに追加します。

```bash
bin/magento app:config:import [-n, --no-interaction]
```

オプションの `[-n, --no-interaction]` フラグを指定すると、追加の確認を行わずにコマンドを実行できます。

詳しくは、 [設定ファイルからデータを読み込む](../../configuration/cli/import-configuration.md)

### 機密データ

{{$include /help/_includes/sensitive-data.md}}
