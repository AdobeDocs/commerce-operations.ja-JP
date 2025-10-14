---
title: メンテナンスモードの有効化または無効化
description: 次の手順に従って、Adobe Commerceのデプロイメントがメンテナンスのために停止した場合に顧客に表示される内容をカスタマイズします。
exl-id: 5d9f1493-e771-47b4-b906-3771026cf07a
source-git-commit: a5dbefda6b77d993756143ef0e7270425f824c44
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 0%

---

# メンテナンスモードの有効化または無効化

次のガイドでは、標準メンテナンスモードのページについて説明しています。 カスタムメンテナンスページを使用する必要がある場合は、[&#x200B; カスタムメンテナンスページの作成 &#x200B;](../../upgrade/troubleshooting/maintenance-mode-options.md) を参照してください。

Adobe Commerceは [&#x200B; メンテナンスモード &#x200B;](../../configuration/bootstrap/application-modes.md#maintenance-mode) を使用して、ブートストラップを無効にします。 サイトのメンテナンス、アップグレードまたは再構成中は、ブートストラップの無効化が役立ちます。

アプリケーションは、次のようにメンテナンスモードを検出します。

* `var/.maintenance.flag` が存在する場合、メンテナンスモードはオンになり、アプリケーションは 503 メンテナンスページを返します。
* `var/.maintenance.ip` が存在し、クライアント IP がこのファイル内の IP アドレスエントリのいずれかに対応する場合、メンテナンスページはそのリクエストに対して無視されます。

## アプリケーションのインストール

このコマンドを使用してメンテナンスモードを有効または無効にする前に、[&#x200B; アプリケーションをインストールする &#x200B;](../advanced.md) 必要があります。

## メンテナンスモードの有効化または無効化

`magento maintenance` CLI コマンドを使用して、メンテナンス・モードを有効または無効にします。

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

`--ip=<ip address>` オプションは、メンテナンスモードから除外する IP アドレスです（例：メンテナンスを行う開発者）。 同じコマンドで複数の IP アドレスを除外するには、オプションを複数回使用します。

>[!NOTE]
>
>`--ip=<ip address>` で `magento maintenance:disable` を使用すると、後で使用するために IP のリストが保存されます。 除外 IP の一覧をクリアするには、`magento maintenance:enable --ip=none` を使用するか、[&#x200B; 除外 IP アドレスの一覧の管理 &#x200B;](#maintain-the-list-of-exempt-ip-addresses) を参照してください。

`bin/magento maintenance:status` コマンドは、メンテナンス モードの状態を表示します。

例えば、IP アドレスを除外せずにメンテナンスモードを有効にするには、次の手順を実行します。

```bash
bin/magento maintenance:enable
```

192.0.2.10 と 192.0.2.11 を除くすべてのクライアントのメンテナンス・モードを有効にするには、次の手順に従います。

```bash
bin/magento maintenance:enable --ip=192.0.2.10 --ip=192.0.2.11
```

アプリケーションをメンテナンスモードにした後、メッセージキューコンシューマープロセスをすべて停止する必要があります。
これらのプロセスを見つける 1 つの方法は、`ps -ef | grep queue:consumers:start` コマンドを実行してから、各消費者に対して `kill <process_id>` コマンドを実行することです。 複数ノード環境では、各ノードでこのタスクを繰り返します。

## 除外 IP アドレスの一覧を管理します

除外 IP アドレスの一覧を管理するには、前のコマンドの `[--ip=<ip list>]` オプションを使用するか、次のコマンドを使用します。

```bash
bin/magento maintenance:allow-ips <ip address> .. <ip address> [--none]
```

`<ip address> .. <ip address>` の構文は、除外する IP アドレスのリストをスペースで区切ってオプションで指定します。

`--none` のオプションを選択すると、リストがクリアされます。

## マルチストアの設定

<!-- To set up multiple stores, each with a different layout and localized content, create a skin for each and put it into `pub/errors/{name}` where `{name}` is the store code. To distinguish between stores and websites with the same instance, use `pub/errors/{type}-{name}` where `{type}` is either `store` or `website` and matches the `MAGE_RUN_TYPE` in your server configuration. Another option is to pass the `$_GET['skin']` parameter to the intended processor. This method requires a specific configuration on your server. -->
<!-- Replace the line below with the commented text after https://github.com/magento/magento2/pull/35095 is merged. -->

それぞれ異なるレイアウトとローカライズされたコンテンツを持つ複数のストアを設定する場合は、`$_GET['skin']` パラメーターを目的のプロセッサーに渡します。

次の例では、`503` タイプのエラーテンプレートファイルを使用します。このファイルにはローカライズされたコンテンツが必要です。

`Error_Processor` クラスのコンストラクターは、`skin` のGET パラメーターを受け入れて、レイアウトを変更します。

```php
if (isset($_GET['skin'])) {
    $this->_setSkin($_GET['skin']);
}
```

これは、URL に `.htaccess` パラメーターを追加する `skin` ファイルの書き換えルールに追加することもできます。

### $_GET[&#39;skin&#39;] パラメータ

`skin` パラメーターを使用するには：

1. `.maintenance.flag` が存在するかどうかを確認します。
1. `HTTP_HOST` を参照するホストアドレスや、ENV 変数などのその他の変数に注意してください。
1. `skin` パラメーターが存在するかどうかを確認します。
1. 以下の書き換えルールを使用して、パラメーターを設定します。

   次に、書き換えルールの例を示します。

   * RewriteCond `%{DOCUMENT_ROOT}/var/.maintenance.flag -f`
   * RewriteCond `%{HTTP_HOST} ^sub.example.com$`
   * RewriteCond `%{QUERY_STRING} !(^|&)skin=sub(&|$)` [NC]
   * RewriteRule `^ %{REQUEST_URI}?skin=sub` [L]

1. 次のファイルをコピーします。

   * `pub/errors/default/503.phtml` ～ `pub/errors/sub/503.phtml`
   * `pub/errors/default/css/styles.css` ～ `pub/errors/sub/styles.css`

1. これらのファイルを編集して、`503.phtml` ファイルのコンテンツをローカライズし、`styles.css` ファイルにカスタムスタイルを設定します。

   パスが `errors` ディレクトリを指していることを確認します。 ディレクトリ名は、`RewriteRule` に示されている URL パラメーターと一致する必要があります。 前の例では、`sub` ディレクトリが使用され、`RewriteRule` でパラメーターとして指定されています（`skin=sub`）。

>[!NOTE]
>
>マルチストアを設定するには、[nginx](../../configuration/multi-sites/ms-nginx.md) 設定を追加する必要があります。
