---
title: ストアを設定
description: 次の手順に従って、Adobe CommerceまたはMagento Open Sourceストアを設定します。
exl-id: ab5e9c43-d914-4de9-98a9-b60d3984b23c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# ストアを設定

このコマンドを実行する前に、次の操作を行う必要があります *または* 必ず [アプリケーションのインストール](../advanced.md):

* [デプロイメント設定を作成または更新する](deployment.md)
* [データベーススキーマの作成](database.md)

## 安全なインストール

{{$include /help/_includes/secure-install.md}}

## ストアを設定

コマンドの使用：

```bash
bin/magento setup:store-config:set [--<parameter_name>=<value>, ...]
```

次の表に、パラメータと値の定義を示します。

| 名前 | 値 | 必須？ |
|--- |--- |--- |
| `--base-url` | 次のいずれかの形式で管理者およびストアフロントにアクセスするために使用するベース URL。<br><br>- `http[s]://<host or ip>/<your install dir>/`.<br><br>**注意：** スキーム (`http://` または `https://`) と末尾のスラッシュは両方とも必要です。 `<your install dir>` は、アプリケーションをインストールする docroot 相対パスです。 Web サーバーと仮想ホストの設定方法に応じて、パスは magento2 になる場合と空になる場合があります。<br><br>localhost 上のアプリケーションにアクセスするには、 `http://127.0.0.1/<your install dir>/`.<br><br>- `{{base_url}}` これは、仮想ホスト設定または Docker のような仮想化環境で定義されるベース URL を表します。 例えば、ホスト名commerce.example.comを使用して仮想ホストを設定した場合、 `--base-url={{base_url}}` また、のような URL を使用して管理者にアクセスします。 `http://commerce.example.com/admin`. | いいえ |
| `--language` | 管理およびストアフロントで使用する言語コード。<br><br>( まだ行っていない場合は、 `magento info:language:list` から `bin` ディレクトリ ) | いいえ |
| `--currency` | ストアフロントで使用するデフォルトの通貨。 <br><br>( まだ通貨リストを表示していない場合は、「 `magento info:currency:list` から `bin` ディレクトリ ) | いいえ |
| `--timezone` | Admin およびストアフロントで使用するデフォルトのタイムゾーン。 ( まだタイムゾーンを表示していない場合は、 `magento info:timezone:list` から `bin` ディレクトリ ) | いいえ |
| `--use-rewrites` | `1` とは、生成されたリンクに対して、ストアフロントと管理で web サーバーの書き換えを使用することを意味します。<br><br>`0` web サーバーの書き換えを使用できなくします。 これがデフォルトです。 | いいえ |
| `--use-secure` | `1` ストアフロント URL での Secure Sockets Layer(SSL) の使用を有効にします。 このオプションを選択する前に、Web サーバーが SSL をサポートしていることを確認してください。<br><br>`0` は SSL の使用を無効にします。 この場合、他のセキュア URL オプションもすべて 0 と見なされます。 これがデフォルトです。 | いいえ |
| `--base-url-secure` | 管理者およびストアフロントへのアクセスに使用するセキュアベース URL は、次の形式です。 `http[s]://<host or ip>/<your install dir>/` | いいえ |
| `--use-secure-admin` | `1` は、SSL を使用して管理者にアクセスすることを意味します。 このオプションを選択する前に、Web サーバーが SSL をサポートしていることを確認してください。<br><br>`0` は、管理者と共に SSL を使用していないことを意味します。 これがデフォルトです。 | いいえ |
| `--admin-use-security-key` | `1` を指定すると、アプリケーションは、ランダムに生成されたキー値を使用して、管理者およびフォームのページにアクセスします。 これらのキー値は、クロスサイトスクリプトフォージェリ攻撃を防ぐのに役立ちます。 これがデフォルトです。<br/><br/>`0` キーの使用を無効にします。 | いいえ |
| `--magento-init-params` | 任意のコマンドに追加して、アプリケーション初期化パラメータをカスタマイズ<br/><br/>例： `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | いいえ |
