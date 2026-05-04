---
title: メンテナンスモードを有効または無効にする
description: 次の手順に従って、Adobe Commerceの導入がメンテナンスに失敗した場合に表示される内容をカスタマイズします。
exl-id: 5d9f1493-e771-47b4-b906-3771026cf07a
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# メンテナンスモードを有効または無効にする

次のガイドでは、標準メンテナンスモードページについて説明します。 カスタムメンテナンスページを使用する必要がある場合は、[&#x200B; カスタムメンテナンスページの作成](../../upgrade/troubleshooting/maintenance-mode-options.md) トピックを参照してください。

Adobe Commerceでは、[&#x200B; メンテナンスモード &#x200B;](../../configuration/bootstrap/application-modes.md#maintenance-mode)を使用してブートストラップを無効にします。 ブートストラップを無効にすると、サイトの保守、アップグレード、再設定を行う際に役立ちます。

アプリケーションは、次のようにメンテナンスモードを検出します。

* `var/.maintenance.flag`が存在する場合、メンテナンスモードは有効になっており、アプリケーションは503 メンテナンスページを返します。
* `var/.maintenance.ip`が存在し、クライアント IPがこのファイル内のIP アドレスエントリのいずれかに対応する場合、メンテナンスページはリクエストに対して無視されます。

## アプリケーションのインストール

このコマンドを使用してメンテナンスモードを有効または無効にする前に、[&#x200B; アプリケーションをインストールする必要があります](../advanced.md)。

## メンテナンスモードを有効または無効にする

メンテナンスモードを有効または無効にするには、`magento maintenance` CLI コマンドを使用します。

コマンドの使用状況：

```shell
bin/magento maintenance:enable [--ip=<ip address> ... --ip=<ip address>] | [ip=none]
```

```shell
bin/magento maintenance:disable [--ip=<ip address> ... --ip=<ip address>] | [ip=none]
```

```shell
bin/magento maintenance:status
```

`--ip=<ip address>` オプションは、メンテナンスモードから除外するIP アドレスです（例えば、メンテナンスを行う開発者）。 同じコマンドで複数のIP アドレスを除外するには、オプションを複数回使用します。

>[!NOTE]
>
>`--ip=<ip address>`を`magento maintenance:disable`と共に使用すると、後で使用するためにIPのリストが保存されます。 除外IPのリストをクリアするには、`magento maintenance:enable --ip=none`を使用するか、[除外IP アドレスのリストを維持](#maintain-the-list-of-exempt-ip-addresses)を参照してください。

`bin/magento maintenance:status` コマンドは、メンテナンスモードのステータスを表示します。

例えば、IP アドレスの除外なしでメンテナンスモードを有効にするには、次のようにします。

```shell
bin/magento maintenance:enable
```

192.0.2.10と192.0.2.11を除くすべてのクライアントでメンテナンスモードを有効にするには：

```shell
bin/magento maintenance:enable --ip=192.0.2.10 --ip=192.0.2.11
```

アプリケーションをメンテナンスモードにした後、すべてのメッセージキューコンシューマープロセスを停止する必要があります。
これらのプロセスを見つける方法の1つは、`ps -ef | grep queue:consumers:start` コマンドを実行してから、各コンシューマーに対して`kill <process_id>` コマンドを実行することです。 複数ノード環境で、各ノードでこのタスクを繰り返します。

## 除外IP アドレスのリストの管理

除外IP アドレスのリストを管理するには、上記のコマンドで`[--ip=<ip list>]` オプションを使用するか、次のいずれかを使用できます。

```shell
bin/magento maintenance:allow-ips <ip address> .. <ip address> [--none]
```

`<ip address> .. <ip address>`構文は、除外するIP アドレスのスペース区切りリストです（オプション）。

`--none` オプションはリストをクリアします。

## 複数店舗の設定

<!-- To set up multiple stores, each with a different layout and localized content, create a skin for each and put it into `pub/errors/{name}` where `{name}` is the store code. To distinguish between stores and websites with the same instance, use `pub/errors/{type}-{name}` where `{type}` is either `store` or `website` and matches the `MAGE_RUN_TYPE` in your server configuration. Another option is to pass the `$_GET['skin']` parameter to the intended processor. This method requires a specific configuration on your server. -->
<!-- Replace the line below with the commented text after https://github.com/magento/magento2/pull/35095 is merged. -->

複数のストアを設定し、それぞれのストアに異なるレイアウトとローカライズされたコンテンツを設定する場合は、`$_GET['skin']` パラメーターを目的のプロセッサーに渡します。

次の例では、ローカライズされたコンテンツを必要とする`503` タイプのエラーテンプレートファイルを使用しています。

`Error_Processor` クラスのコンストラクターは、レイアウトを変更するために`skin` GET パラメーターを受け入れます。

```php
if (isset($_GET['skin'])) {
    $this->_setSkin($_GET['skin']);
}
```

これは、`skin` パラメーターをURLに追加する`.htaccess` ファイルの書き換えルールに追加することもできます。

### $_GET[&#39;skin&#39;] パラメーター

`skin` パラメーターを使用するには：

1. `.maintenance.flag`が存在するかどうかを確認します。
1. `HTTP_HOST`、またはENV変数などの他の変数を参照するホストアドレスに注意してください。
1. `skin` パラメーターが存在するかどうかを確認します。
1. 以下の書き換えルールを使用して、パラメーターを設定します。

   書き換えルールの例を次に示します。

   * RewriteCond `%{DOCUMENT_ROOT}/var/.maintenance.flag -f`
   * RewriteCond `%{HTTP_HOST} ^sub.example.com$`
   * RewriteCond `%{QUERY_STRING} !(^|&)skin=sub(&|$)` [NC]
   * RewriteRule `^ %{REQUEST_URI}?skin=sub` [L]

1. 次のファイルをコピーします。

   * `pub/errors/default/503.phtml` ～ `pub/errors/sub/503.phtml`
   * `pub/errors/default/css/styles.css` ～ `pub/errors/sub/styles.css`

1. これらのファイルを編集して、`503.phtml` ファイルのローカライズされたコンテンツと`styles.css` ファイルのカスタム スタイル設定を提供します。

   パスが`errors` ディレクトリを指していることを確認します。 ディレクトリ名は、`RewriteRule`に示されているURL パラメーターと一致する必要があります。 前の例では、`RewriteRule` （`skin=sub`）のパラメーターとして指定されている`sub` ディレクトリが使用されています

>[!NOTE]
>
>マルチストア設定の場合は、[nginx](../../configuration/multi-sites/ms-nginx.md)設定を追加する必要があります。
