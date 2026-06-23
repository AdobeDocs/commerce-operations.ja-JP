---
title: Varnish キャッシュ用にnginxを設定する
description: Adobe CommerceのVarnish キャッシュを使用するようにweb サーバーを設定する方法について説明します。 ポートの設定と設定の要件について説明します。
feature: Configuration, Cache, Install, Logs
exl-id: b31179ef-3c0e-4a6b-a118-d3be1830ba4e
badgePaas: label="オンプレミス" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce オンプレミス プロジェクトにのみ適用されます。"
autotag-review: '2026-06-22T21:49:41.837Z'
TQID: 'https://experienceleague.adobe.com/0vOg86gRkST8CZGhdIESzhld63HQ5IUlO4go-Hgw9Xs'
product_v2: id: b974b164-8a4e-43b8-a9e2-8e67ec131677id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: c8faa589c9e9d1dbc01863d90aad5f91b11c0140
workflow-type: tm+mt
source-wordcount: 806
ht-degree: 0%

---

# Varnish キャッシュ用のnginxの設定 {#configure-web-server-for-varnish-caching}

VarnishがAdobe Commerceのフルページキャッシュとして使用される場合、Varnishは通常、パブリック HTTP ポートでリッスンし、8080などのデフォルト以外のバックエンドポートでnginxにリクエストを転送します。 Varnishが使用するバックエンドポートをリッスンするように、Commerce オリジンサーバーのnginx サイト設定を更新します。

{{varnish-config-cloud}}

次の節では、ポート 8080を例として使用します。

**Commerce origin サーバー**&#x200B;のnginx リッスン ポートを変更します。

1. Adobe Commerce origin サーバーのnginx サイト設定をテキストエディターで開きます。

場所は、オペレーティングシステムとnginx レイアウトによって異なります。 例えば、Ubuntuでは、`/etc/nginx/sites-available/`の下のファイルを使用することがよくあります。

1. Commerce サイトの`server` ブロックで、`listen` ディレクティブをパブリック HTTP ポートから、Varnishがnginxへのアクセスに使用するバックエンドポートに変更します。

   例えば、変更します

   ```conf
   server {
       listen 80;
       server_name example.com;
       root /var/www/html/magento2;
       include /var/www/html/magento2/nginx.conf.sample;
   }
   ```

   宛先：

   ```conf
   server {
       listen 8080;
       server_name example.com;
       root /var/www/html/magento2;
       include /var/www/html/magento2/nginx.conf.sample;
   }
   ```

1. ファイルを保存します。

1. nginx設定を確認します。

   ```shell
   nginx -t
   ```

1. nginxを再起動します。

   ```shell
   systemctl restart nginx
   ```

## Varnish システム設定の変更

バックエンドポートでリッスンするようにnginxを更新した後、そのホストとポートにリクエストを転送するようにVarnishを設定します。 例：

```conf
backend default {
    .host = "192.0.2.55";
    .port = "8080";
}
```

### デフォルトのVCLの変更

この節では、VarnishがHTTP応答ヘッダーを返すように、最小限の設定を提供する方法について説明します。 これにより、Varnishを使用するように[!DNL Commerce] アプリケーションを設定する前に、Varnishが機能することを確認できます。

Varnishを最小限に設定するには：

1. `default.vcl`をバックアップ：

   ```shell
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak
   ```

1. `/etc/varnish/default.vcl`をテキストエディターで開きます。
1. 次のスタンザを探します。

   ```conf
   backend default {
       .host = "127.0.0.1";
       .port = "80";
   }
   ```

1. `.host`の値を、Varnish _バックエンド_&#x200B;または&#x200B;_オリジン サーバー_&#x200B;の完全修飾ホスト名またはIP アドレスとリッスン ポートに置き換えます。つまり、コンテンツ Varnishを提供するサーバーが高速化します。

   通常、これはあなたのweb サーバーです。 _Varnish ガイド_&#x200B;の「[ バックエンドサーバー](https://varnish-cache.org/docs/trunk/users-guide/vcl-backends.html)」を参照してください。

1. `.port`の値をWeb サーバーのリッスン ポート （この例では8080）に置き換えます。

   例：nginxはホスト 192.0.2.55にインストールされ、ポート 8080でリッスンしています。

   ```conf
   backend default {
       .host = "192.0.2.55";
       .port = "8080";
   }
   ```

   >[!INFO]
   >
   >Varnishとnginxが同じホストで実行されている場合、Adobeでは、`localhost`ではなくIP アドレスまたはホスト名を使用することをお勧めします。

1. 変更を`default.vcl`に保存して、テキストエディターを終了します。

1. Varnishを再起動します。

   ```shell
   service varnish restart
   ```

Varnishの起動に失敗した場合は、次のようにコマンドラインから実行してみてください。

```shell
varnishd -d -f /etc/varnish/default.vcl
```

エラーメッセージが表示されるはずです。


>[!INFO]
>
>Varnishがサービスとして開始しない場合は、実行できるようにSELinux ルールを設定する必要があります。

## Varnishが機能していることを確認する

次の節では、Varnishが機能しているが、_Commerceを使用するように設定していない_&#x200B;ことを確認する方法について説明します。 Commerceを設定する前に、これを試してください。

次のセクションで説明するタスクを次の順序で実行します。

- [Varnishを開始](#start-varnish)
- [`netstat`](#netstat)

### Varnishを開始

入力：`service varnish start`

Varnishがサービスとして開始できない場合は、次のようにコマンドラインから起動します。

1. Varnish CLIを起動します。

   ```shell
   varnishd -d -f /etc/varnish/default.vcl
   ```

1. Varnish子プロセスを開始します。

   プロンプトが表示されたら、`start`と入力します

   正常な開始を確認するには、次のメッセージが表示されます。

   ```text
   child (29805) Started
   200 0
   
   Child (29805) said
   Child (29805) said Child starts
   ```

### netstat

Varnish サーバーにログインし、次のコマンドを入力します。

```shell
netstat -tulpn
```

特に次の出力を探します。

```text
tcp        0      0 0.0.0.0:80                  0.0.0.0:*                   LISTEN      32614/varnishd
tcp        0      0 127.0.0.1:58484             0.0.0.0:*                   LISTEN      32604/varnishd
tcp        0      0 :::8080                     :::*                        LISTEN      26822/nginx
tcp        0      0 ::1:48509                   :::*                        LISTEN      32604/varnishd
```

前述の図は、Varnishがポート 80で動作し、nginxがポート 8080で動作していることを示しています。

`varnishd`の出力が表示されない場合は、Varnishが実行されていることを確認します。

[`netstat` オプション ](https://tldp.org/LDP/nag2/x-087-2-iface.netstat.html)を参照してください。

## Commerce ソフトウェアのインストール

まだインストールしていない場合は、Commerce ソフトウェアをインストールします。 ベース URLの入力を求められたら、Varnishがすべての受信HTTP リクエストを受信するため、Varnish ホストおよびポート 80 （Varnishの場合）を使用します。

Commerceのインストール中に発生する可能性のあるエラー：

```text
Error 503 Service Unavailable
Service Unavailable
XID: 303394517
Varnish cache server
```

このエラーが発生した場合は、次のように`default.vcl`を編集し、`backend` スタンザにタイムアウトを追加します。

```conf
backend default {
   .host = "127.0.0.1";
   .port = "8080";
   .first_byte_timeout = 600s;
}
```

## HTTP応答ヘッダーの検証

これで、どのページから返されたHTML応答ヘッダーを見て、Varnishがページを配信しているかを確認できます。

ヘッダーを確認する前に、Commerceをデベロッパーモードに設定する必要があります。 これを行うには、いくつかの方法があります。最も簡単なのは、Commerce アプリケーションルートの`.htaccess`を変更することです。 [`magento deploy:mode:set`](../cli/set-mode.md) コマンドを使用することもできます。

### Commerceを開発者向けに設定

Commerceを開発者向けモードに設定するには、[`magento deploy:mode:set`](../cli/set-mode.md#change-to-developer-mode) コマンドを使用します。

### Varnishのログを見る

Varnishが実行されていることを確認し、Varnish サーバーで次のコマンドを入力します。

```shell
varnishlog
```

Web ブラウザーで、任意のCommerce ページに移動します。

応答ヘッダーの長いリストがコマンドプロンプトウィンドウに表示されます。 次のようなヘッダーを探します。

```text
-   BereqHeader    X-Varnish: 3
-   VCL_call       BACKEND_FETCH
-   VCL_return     fetch
-   BackendOpen    17 default(10.249.151.10,,8080) 10.249.151.10 60914
-   Backend        17 default(10.249.151.10,,8080)
-   Timestamp      Bereq: 1440449534.261791 0.000618 0.000618
-   ReqHeader      Host: 10.249.151.10
-   ReqHeader      Connection: keep-alive
-   ReqHeader      Content-Length: 86
-   ReqHeader      Cache-Control: max-age=0
-   ReqHeader      Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
-   ReqHeader      Origin: http://10.249.151.10
```

これらのヘッダーが&#x200B;_not_&#x200B;表示されない場合は、Varnishを停止し、`default.vcl`を確認して、もう一度試してください。

### HTMLの応答ヘッダーの確認

応答ヘッダーを確認するには、ブラウザープラグインやブラウザーインスペクターの使用など、いくつかの方法があります。

次の例では、`curl`を使用しています。 このコマンドは、HTTPを使用してCommerce サーバーにアクセスできる任意のマシンから入力できます。

```shell
curl -I -v --location-trusted '<your Commerce base URL>'
```

以下に例を挙げます。

```shell
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

次のようなヘッダーを探します。

```text
Content-Type: text/html; charset=iso-8859-1
X-Varnish: 15
Age: 0
Via: 1.1 varnish-v6
X-Magento-Cache-Debug: HIT
```
