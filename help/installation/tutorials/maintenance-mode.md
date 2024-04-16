---
title: メンテナンスモードの有効化または無効化
description: 次の手順に従って、Adobe CommerceまたはMagento Open Sourceのデプロイメントがメンテナンスのためにダウンした場合に表示される内容をカスタマイズします。
exl-id: 5d9f1493-e771-47b4-b906-3771026cf07a
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---

# メンテナンスモードの有効化または無効化

次のガイドでは、標準メンテナンスモードのページについて説明しています。 カスタムメンテナンスページを使用する必要がある場合は、を参照してください。 [カスタムメンテナンスページの作成](../../upgrade/troubleshooting/maintenance-mode-options.md) トピック。

Adobe Commerceが使用する [メンテナンスモード](../../configuration/bootstrap/application-modes.md#maintenance-mode) ブートストラップを無効にします。 サイトのメンテナンス、アップグレードまたは再構成中は、ブートストラップの無効化が役立ちます。

アプリケーションは、次のようにメンテナンスモードを検出します。

* 次の場合 `var/.maintenance.flag` が存在しない。メンテナンスモードがオフであり、アプリケーションが正常に動作します。
* それ以外の場合、以下に該当しない限り、メンテナンスモードはオンになります。 `var/.maintenance.ip` が存在する。

  `var/.maintenance.ip` ip アドレスのリストを含めることができます。 HTTP を使用してエントリ ポイントにアクセスし、クライアントの IP アドレスがそのリスト内のいずれかのエントリに対応する場合、メンテナンス モードはオフになります。

## アプリケーションのインストール

このコマンドを使用してメンテナンスモードを有効または無効にする前に、以下を行う必要があります [アプリケーションのインストール](../advanced.md).

## メンテナンスモードの有効化または無効化

の使用 `magento maintenance` メンテナンス・モードを有効または無効にする CLI コマンド。

コマンドの使用法：

```bash
bin/magento maintenance:enable [--ip=<ip address> ... --ip=<ip address>] | [ip=none]
```

```bash
bin/magento maintenance:disable [--ip=<ip address> ... --ip=<ip address>] | [ip=none]
```

```bash
bin/magento maintenance:status
```

この `--ip=<ip address>` option は、メンテナンスモードから除外する IP アドレスです（例：メンテナンスを行う開発者）。 同じコマンドで複数の IP アドレスを除外するには、オプションを複数回使用します。

>[!NOTE]
>
>使用 `--ip=<ip address>` （を使用） `magento maintenance:disable` 後で使用するために IP のリストを保存します。 除外 IP のリストをクリアするには、を使用します `magento maintenance:enable --ip=none` または参照： [除外 IP アドレスの一覧を管理します](#maintain-the-list-of-exempt-ip-addresses).

この `bin/magento maintenance:status` コマンドは、メンテナンス モードの状態を表示します。

例えば、IP アドレスを除外せずにメンテナンスモードを有効にするには、次の手順を実行します。

```bash
bin/magento maintenance:enable
```

192.0.2.10 および 192.0.2.11 を除くすべてのクライアントのメンテナンス モードを有効にするには、次の手順に従います。

```bash
bin/magento maintenance:enable --ip=192.0.2.10 --ip=192.0.2.11
```

アプリケーションをメンテナンスモードにした後、メッセージキューコンシューマープロセスをすべて停止する必要があります。
これらのプロセスを見つける 1 つの方法は、 `ps -ef | grep queue:consumers:start` コマンドを実行してから、 `kill <process_id>` 各消費者に対するコマンド。 複数ノード環境では、各ノードでこのタスクを繰り返します。

## 除外 IP アドレスの一覧を管理します

除外 IP アドレスのリストを管理するには、次のいずれかを使用します `[--ip=<ip list>]` 上記のコマンドのオプションを使用するか、次のオプションを使用できます。

```bash
bin/magento maintenance:allow-ips <ip address> .. <ip address> [--none]
```

この `<ip address> .. <ip address>` 構文は、除外する IP アドレスのスペース区切りリスト（オプション）です。

この `--none` 「」オプションを選択すると、リストがクリアされます。

## マルチストアの設定

<!-- To set up multiple stores, each with a different layout and localized content, create a skin for each and put it into `pub/errors/{name}` where `{name}` is the store code. To distinguish between stores and websites with the same instance, use `pub/errors/{type}-{name}` where `{type}` is either `store` or `website` and matches the `MAGE_RUN_TYPE` in your server configuration. Another option is to pass the `$_GET['skin']` parameter to the intended processor. This method requires a specific configuration on your server. -->
<!-- Replace the line below with the commented text after https://github.com/magento/magento2/pull/35095 is merged. -->

複数のストアを設定する場合は、それぞれに異なるレイアウトとローカライズされたコンテンツを指定し、 `$_GET['skin']` 対象のプロセッサーへのパラメーター。

次の例では、を使用しています。 `503` ローカライズされたコンテンツが必要なエラーテンプレートファイルを入力します。

のコンストラクター `Error_Processor` クラスはを受け入れます `skin` レイアウトを変更するためのGETパラメーター：

```php
if (isset($_GET['skin'])) {
    $this->_setSkin($_GET['skin']);
}
```

これは、の書き換えルールに追加することもできます。 `.htaccess` を追加するファイル `skin` パラメーターを URL に追加します。

### $_GET[『スキン 』] パラメーター

を使用するには `skin` パラメーター：

1. 次の場合を確認します `.maintenance.flag` が存在する。
1. を参照するホストアドレスを書き留めます `HTTP_HOST`、または環境変数などのその他の変数。
1. 次の場合を確認します `skin` パラメーターが存在します。
1. 以下の書き換えルールを使用して、パラメーターを設定します。

   次に、書き換えルールの例を示します。

   * RewriteCond `%{DOCUMENT_ROOT}/var/.maintenance.flag -f`
   * RewriteCond `%{HTTP_HOST} ^sub.example.com$`
   * RewriteCond `%{QUERY_STRING} !(^|&)skin=sub(&|$)` [NC]
   * RewriteRule `^ %{REQUEST_URI}?skin=sub` [L]

1. 次のファイルをコピーします。

   * `pub/errors/default/503.phtml` 対象： `pub/errors/sub/503.phtml`
   * `pub/errors/default/css/styles.css` 対象： `pub/errors/sub/styles.css`

1. これらのファイルを編集して、ローカライズされたコンテンツを `503.phtml` でのファイルとカスタムスタイル設定 `styles.css` ファイル。

   パスがを指していることを確認します `errors` ディレクトリ。 ディレクトリ名は、に示されている URL パラメーターと一致する必要があります。 `RewriteRule`. 前の例では、 `sub` ディレクトリが使用されます。これは、 `RewriteRule` （`skin=sub`）

>[!NOTE]
>
>この [nginx](../../configuration/multi-sites/ms-nginx.md) マルチストアを設定するには、設定を追加する必要があります。
