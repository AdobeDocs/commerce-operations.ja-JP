---
title: ストアの設定
description: 次の手順に従って、Adobe Commerce ストアを設定します。
exl-id: ab5e9c43-d914-4de9-98a9-b60d3984b23c
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ストアの設定

このコマンドを実行する前に、次の操作を行う必要があります *または* アプリケーションをインストールする必要があります [](../advanced.md)。

* [デプロイメント設定の作成または更新](deployment.md)
* [データベーススキーマの作成](database.md)

## 安全なインストール

{{$include /help/_includes/secure-install.md}}

## ストアの設定

コマンドの使用法：

```bash
bin/magento setup:store-config:set [--<parameter_name>=<value>, ...]
```

次の表に、パラメーターと値を示します。

| 名前 | 値 | 必須？ |
|--- |--- |--- |
| `--base-url` | 次のいずれかの形式で管理者およびストアフロントにアクセスするために使用するベース URL:<br><br>- `http[s]://<host or ip>/<your install dir>/`。<br><br>**注意：** スキーム（`http://` または `https://`）と末尾のスラッシュは両方とも必須です。 `<your install dir>` は、アプリケーションをインストールするドキュメントルート相対パスです。 Web サーバーと仮想ホストの設定方法に応じて、パスは magento2 になるか、空になります。<br><br>localhost 上のアプリケーションにアクセスするには、`http://127.0.0.1/<your install dir>/` を使用できます。<br><br> – 仮想ホスト設定または Docker などの仮想化環境によって定義されたベース URL を表す `{{base_url}}`。 例えば、ホスト名がcommerce.example.comの仮想ホストを設定した場合、`--base-url={{base_url}}` を使用してアプリケーションをインストールし、`http://commerce.example.com/admin` のような URL を使用して管理者にアクセスできます。 | 不可 |
| `--language` | 管理およびストアフロントで使用する言語コード。<br><br> （まだ実行していない場合は、`bin` ディレクトリから `magento info:language:list` と入力して言語コードのリストを表示できます。） | 不可 |
| `--currency` | ストアフロントで使用するデフォルト通貨。 <br><br> （まだ行っていない場合は、`bin` ディレクトリから `magento info:currency:list` と入力して通貨のリストを表示できます。） | 不可 |
| `--timezone` | 管理およびストアフロントで使用するデフォルトのタイムゾーン。 （タイムゾーンリストをまだ表示していない場合は、`bin` ディレクトリから `magento info:timezone:list` と入力して表示できます）。 | 不可 |
| `--use-rewrites` | つま `1`、ストアフロントおよび管理者で生成されたリンクに対して、web サーバーの書き換えを使用します。<br><br>`0` は、web サーバーの書き換えの使用を無効にします。 これがデフォルトです。 | 不可 |
| `--use-secure` | `1` を使用すると、ストアフロント URL で Secure Sockets Layer （SSL）を使用できます。 このオプションを選択する前に、web サーバーで SSL がサポートされていることを確認してください。<br><br>`0` は SSL の使用を無効にします。 この場合、他のすべてのセキュア URL オプションも 0 と見なされます。 これがデフォルトです。 | 不可 |
| `--base-url-secure` | 管理者およびストアフロントにアクセスするために使用するセキュアなベース URL を次の形式で指定します：`http[s]://<host or ip>/<your install dir>/` | 不可 |
| `--use-secure-admin` | `1` まり、SSL を使用して管理者にアクセスします。 このオプションを選択する前に、web サーバーで SSL がサポートされていることを確認してください。<br><br>`0` れは、管理者で SSL を使用しないことを意味します。 これがデフォルトです。 | 不可 |
| `--admin-use-security-key` | `1` を使用すると、アプリケーションはランダムに生成されたキー値を使用して、管理およびフォームのページにアクセスします。 これらのキー値は、クロスサイトスクリプトフォージェリー攻撃を防ぐのに役立ちます。 これがデフォルトです。<br/><br/>`0` はキーの使用を無効にします。 | 不可 |
| `--magento-init-params` | を任意のコマンドに追加して、アプリケーション初期化パラメーターをカスタマイズ <br/><br/> ます。例：`MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | 不可 |
