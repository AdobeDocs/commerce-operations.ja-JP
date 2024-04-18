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

このコマンドを実行する前に、次の操作を行う必要があります *または* あなたは必要です [アプリケーションのインストール](../advanced.md):

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
| `--base-url` | 管理者およびストアフロントにアクセスするために使用するベース URL を次の形式のいずれかで指定します。<br><br>- `http[s]://<host or ip>/<your install dir>/`.<br><br>**注意：** スキーム （`http://` または `https://`）と末尾のスラッシュは両方とも必須です。 `<your install dir>` は、アプリケーションをインストールするドキュメントルートの相対パスです。 Web サーバーと仮想ホストの設定方法に応じて、パスは magento2 になるか、空になります。<br><br>localhost 上のアプリケーションにアクセスするには、を使用できます `http://127.0.0.1/<your install dir>/`.<br><br>- `{{base_url}}` これは、仮想ホスト設定または Docker などの仮想化環境で定義されたベース URL を表します。 例えば、ホスト名がcommerce.example.comの仮想ホストを設定した場合、次を使用してアプリケーションをインストールできます `--base-url={{base_url}}` 次のような URL で管理者にアクセスします。 `http://commerce.example.com/admin`. | 不可 |
| `--language` | 管理およびストアフロントで使用する言語コード。<br><br>（言語コードのリストをまだ表示していない場合は、次のように入力して表示できます。 `magento info:language:list` から `bin` ディレクトリ。） | 不可 |
| `--currency` | ストアフロントで使用するデフォルト通貨。 <br><br>（まだ行っていない場合は、次のように入力して通貨のリストを表示できます `magento info:currency:list` から `bin` ディレクトリ。） | 不可 |
| `--timezone` | 管理およびストアフロントで使用するデフォルトのタイムゾーン。 （タイムゾーンのリストをまだ表示していない場合は、次のように入力して表示できます。 `magento info:timezone:list` から `bin` ディレクトリ。） | 不可 |
| `--use-rewrites` | `1` つまり、ストアフロントおよび管理者で生成されたリンクに対して、web サーバーの書き換えを使用します。<br><br>`0` web サーバーの書き換えの使用を無効にします。 これがデフォルトです。 | 不可 |
| `--use-secure` | `1` ストアフロント URL での Secure Sockets Layer （SSL）の使用を有効にします。 このオプションを選択する前に、web サーバーで SSL がサポートされていることを確認してください。<br><br>`0` は SSL の使用を無効にします。 この場合、他のすべてのセキュア URL オプションも 0 と見なされます。 これがデフォルトです。 | 不可 |
| `--base-url-secure` | 管理者およびストアフロントにアクセスするために使用するセキュアなベース URL を次の形式で指定します。 `http[s]://<host or ip>/<your install dir>/` | 不可 |
| `--use-secure-admin` | `1` は、SSL を使用して管理者にアクセスすることを意味します。 このオプションを選択する前に、web サーバーで SSL がサポートされていることを確認してください。<br><br>`0` は、管理者で SSL を使用しないことを意味します。 これがデフォルトです。 | 不可 |
| `--admin-use-security-key` | `1` アプリケーションで、ランダムに生成されたキー値を使用して管理およびフォームのページにアクセスするようにします。 これらのキー値は、クロスサイトスクリプトフォージェリー攻撃を防ぐのに役立ちます。 これがデフォルトです。<br/><br/>`0` キーの使用を無効にします。 | 不可 |
| `--magento-init-params` | 任意のコマンドにを追加して、アプリケーション初期化パラメーターをカスタマイズ<br/><br/>例： `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | 不可 |
