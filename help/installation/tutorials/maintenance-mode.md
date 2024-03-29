---
title: メンテナンスモードを有効または無効にする
description: 次の手順に従って、メンテナンスのためにAdobe CommerceまたはMagento Open Sourceのデプロイメントが停止している場合に顧客に表示する内容をカスタマイズします。
exl-id: 5d9f1493-e771-47b4-b906-3771026cf07a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 0%

---

# メンテナンスモードを有効または無効にする

次のガイドでは、標準メンテナンスモードのページについて説明します。 カスタムメンテナンスページを使用する必要がある場合は、 [カスタムメンテナンスページの作成](../../upgrade/troubleshooting/maintenance-mode-options.md) トピック。

Adobe CommerceとMagento Open Sourceの使用 [メンテナンスモード](../../configuration/bootstrap/application-modes.md#maintenance-mode) ブートストラップを無効にする。 サイトの保守、アップグレード、再設定を行う際には、ブートストラップを無効にすると便利です。

アプリケーションは、次のようにメンテナンスモードを検出します。

* 次の場合 `var/.maintenance.flag` が存在しない場合、メンテナンスモードはオフになり、アプリケーションは正常に動作します。
* それ以外の場合は、メンテナンスモードがオンになります ( ただし、 `var/.maintenance.ip` が存在します。

  `var/.maintenance.ip` には、IP アドレスのリストを含めることができます。 HTTP を使用してエントリポイントにアクセスし、そのリストのエントリの 1 つに対応するクライアント IP アドレスがある場合、メンテナンスモードはオフになります。

## アプリケーションのインストール

このコマンドを使用してメンテナンスモードを有効または無効にする前に、 [アプリケーションのインストール](../advanced.md).

## メンテナンスモードを有効または無効にする

以下を使用します。 `magento maintenance` メンテナンスモードを有効または無効にする CLI コマンド。

コマンドの使用：

```bash
bin/magento maintenance:enable [--ip=<ip address> ... --ip=<ip address>] | [ip=none]
```

```bash
bin/magento maintenance:disable [--ip=<ip address> ... --ip=<ip address>] | [ip=none]
```

```bash
bin/magento maintenance:status
```

The `--ip=<ip address>` オプションは、メンテナンスモードを除外する IP アドレスです（例えば、メンテナンスをおこなう開発者）。 同じコマンドで複数の IP アドレスを除外するには、オプションを複数回使用します。

>[!NOTE]
>
>使用 `--ip=<ip address>` 次を使用 `magento maintenance:disable` 後で使用するために IP のリストを保存します。 免除 IP のリストをクリアするには、次を使用します。 `magento maintenance:enable --ip=none` または、 [免除 IP アドレスの一覧を管理します](#maintain-the-list-of-exempt-ip-addresses).

The `bin/magento maintenance:status` コマンドは、メンテナンスモードのステータスを表示します。

例えば、IP アドレスの除外を含まないメンテナンスモードを有効にするには、次のように指定します。

```bash
bin/magento maintenance:enable
```

192.0.2.10 および 192.0.2.11 を除くすべてのクライアントのメンテナンスモードを有効にするには：

```bash
bin/magento maintenance:enable --ip=192.0.2.10 --ip=192.0.2.11
```

アプリケーションをメンテナンスモードにした後、すべてのメッセージキューコンシューマープロセスを停止する必要があります。
これらのプロセスを見つける方法の 1 つは、 `ps -ef | grep queue:consumers:start` コマンドを実行し、次に `kill <process_id>` コマンドを使用します。 複数のノード環境で、各ノードでこのタスクを繰り返します。

## 免除 IP アドレスの一覧を管理します

免除 IP アドレスのリストを管理するには、 `[--ip=<ip list>]` オプションを使用するか、次の操作を行うことができます。

```bash
bin/magento maintenance:allow-ips <ip address> .. <ip address> [--none]
```

The `<ip address> .. <ip address>` 構文は、除外する IP アドレスのスペース区切りリスト（オプション）です。

The `--none` オプションを指定すると、リストが消去されます。

## マルチストアの設定

<!-- To set up multiple stores, each with a different layout and localized content, create a skin for each and put it into `pub/errors/{name}` where `{name}` is the store code. To distinguish between stores and websites with the same instance, use `pub/errors/{type}-{name}` where `{type}` is either `store` or `website` and matches the `MAGE_RUN_TYPE` in your server configuration. Another option is to pass the `$_GET['skin']` parameter to the intended processor. This method requires a specific configuration on your server. -->
<!-- Replace the line below with the commented text after https://github.com/magento/magento2/pull/35095 is merged. -->

複数のストアを設定する場合は、それぞれ異なるレイアウトとローカライズされたコンテンツを持つストアを設定するには、 `$_GET['skin']` パラメータを指定します。

次の例では、 `503` エラーテンプレートファイルを入力します。コンテンツのローカライズが必要です。

のコンストラクター `Error_Processor` クラスは `skin` GETパラメーターを使用してレイアウトを変更します。

```php
if (isset($_GET['skin'])) {
    $this->_setSkin($_GET['skin']);
}
```

これは、 `.htaccess` を追加するファイル `skin` パラメーターを URL に設定します。

### $_GET[&#39;スキン&#39;] パラメーター

次の手順で `skin` パラメーター：

1. をチェックします。 `.maintenance.flag` が存在します。
1. ホストアドレス ( `HTTP_HOST`、または ENV 変数などの他の変数。
1. をチェックします。 `skin` パラメーターが存在します。
1. 以下の書き換えルールを使用して、パラメーターを設定します。

   次に、書き換えルールの例を示します。

   * RewriteCond `%{DOCUMENT_ROOT}/var/.maintenance.flag -f`
   * RewriteCond `%{HTTP_HOST} ^sub.example.com$`
   * RewriteCond `%{QUERY_STRING} !(^|&)skin=sub(&|$)` [NC]
   * RewriteRule `^ %{REQUEST_URI}?skin=sub` [L]

1. 次のファイルをコピーします。

   * `pub/errors/default/503.phtml` から `pub/errors/sub/503.phtml`
   * `pub/errors/default/css/styles.css` から `pub/errors/sub/styles.css`

1. これらのファイルを編集して、 `503.phtml` でのファイルとカスタムスタイル設定 `styles.css` ファイル。

   パスが `errors` ディレクトリ。 ディレクトリ名は、 `RewriteRule`. 前の例では、 `sub` ディレクトリが使用されます。これは、 `RewriteRule` (`skin=sub`)

>[!NOTE]
>
>The [nginx](../../configuration/multi-sites/ms-nginx.md) マルチストアを設定するには、の設定を追加する必要があります。
