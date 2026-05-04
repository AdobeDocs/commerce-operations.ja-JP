---
title: ストアの設定
description: セキュアインストールオプションを含む、デプロイメント設定とデータベーススキーマの設定後に、コマンドラインからAdobe Commerce ストアを設定する方法について説明します。
exl-id: ab5e9c43-d914-4de9-98a9-b60d3984b23c
source-git-commit: 41b8d77793f1c24f08ff7e6a2d35826a62477534
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# ストアの設定

このコマンドを実行する前に、次の&#x200B;*または*&#x200B;を実行する必要があります。アプリケーションを[&#x200B; インストールする必要があります](../advanced.md):

* [デプロイメント設定の作成または更新](deployment.md)
* [データベーススキーマの作成](database.md)

## 安全なインストール

{{$include /help/_includes/secure-install.md}}

## ストアの設定

コマンドの使用状況：

```shell
bin/magento setup:store-config:set [--<parameter_name>=<value>, ...]
```

次の表でパラメーターと値を定義します。

| 名前 | 値 | 必要ですか？ |
|--- |--- |--- |
| `--base-url` | 次のいずれかの形式で管理者およびストアフロントにアクセスするために使用するベース URL:<br><br>- `http[s]://<host or ip>/<your install dir>/`.<br><br>**注：** スキーム （`http://`または`https://`）と末尾のスラッシュの両方が必要です。 `<your install dir>`は、アプリケーションをインストールするdocroot相対パスです。 Web サーバーと仮想ホストの設定方法によっては、パスがmagento2であるか、空白である可能性があります。<br><br>localhost上のアプリケーションにアクセスするには、`http://127.0.0.1/<your install dir>/`.<br><br>- `{{base_url}}`を使用できます。これは、仮想ホスト設定またはDockerなどの仮想化環境で定義されたベース URLを表します。 例えば、ホスト名commerce.example.comで仮想ホストを設定した場合、`--base-url={{base_url}}`でアプリケーションをインストールし、`http://commerce.example.com/admin`のようなURLで管理者にアクセスできます。 | いいえ |
| `--language` | 管理者およびストアフロントで使用する言語コード。<br><br> （まだ行っていない場合は、`bin` ディレクトリから`magento info:language:list`を入力すると、言語コードのリストを表示できます）。 | いいえ |
| `--currency` | ストアフロントで使用するデフォルト通貨。 <br><br> （まだ行っていない場合は、`bin` ディレクトリから`magento info:currency:list`を入力して、通貨のリストを表示できます）。 | いいえ |
| `--timezone` | 管理者とストアフロントで使用するデフォルトのタイムゾーン。 （まだ実行していない場合は、`bin` ディレクトリから`magento info:timezone:list`を入力して、タイムゾーンのリストを表示できます）。 | いいえ |
| `--use-rewrites` | `1`とは、ストアフロントおよび管理者で生成されたリンクにweb サーバーの書き換えを使用することを意味します。<br><br>`0` web サーバーの書き換えの使用を無効にします。 これがデフォルトです。 | いいえ |
| `--use-secure` | `1`では、ストアフロント URLでSSL （Secure Sockets Layer）を使用できます。 このオプションを選択する前に、Web サーバーがSSLをサポートしていることを確認してください。<br><br>`0` sslの使用を無効にします。 この場合、その他のすべてのセキュア URL オプションも0と見なされます。 これがデフォルトです。 | いいえ |
| `--base-url-secure` | 管理者およびストアフロントへのアクセスに使用するセキュアなベース URL: `http[s]://<host or ip>/<your install dir>/` | いいえ |
| `--use-secure-admin` | `1`とは、SSLを使用して管理者にアクセスすることを意味します。 このオプションを選択する前に、Web サーバーがSSLをサポートしていることを確認してください。<br><br>`0` つまり、管理者と一緒にSSLを使用しません。 これがデフォルトです。 | いいえ |
| `--admin-use-security-key` | `1`により、アプリケーションはランダムに生成されたキー値を使用して、管理者およびフォームのページにアクセスできます。 これらのキー値は、クロスサイトスクリプトフォージェリー攻撃を防ぐのに役立ちます。 これは既定値です。<br/><br/>`0` キーの使用を無効にします。 | いいえ |
| `--magento-init-params` | 任意のコマンドに追加して、アプリケーションの初期化パラメーターをカスタマイズします<br/><br/>例：`MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | いいえ |

<!-- Last updated from includes: 2022-09-08 11:33:05 -->
