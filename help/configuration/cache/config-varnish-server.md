---
title: Web サーバーの設定
description: Varnish と連携するように web サーバーを設定する方法を説明します。
feature: Configuration, Cache, Install, Logs
exl-id: b31179ef-3c0e-4a6b-a118-d3be1830ba4e
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 0%

---

# Web サーバーの設定

Web サーバーは Web サーバーではなく、受信 HTTP リクエストに Varnish が直接応答するため、デフォルトのポート 80 以外のポートでリッスンするように web サーバーを設定します。

次のセクションでは、例としてポート 8080 を使用します。

**Apache 2.4 リッスンポートを変更するには**:

1. 開く `/etc/httpd/conf/httpd.conf` テキストエディター。
1. を見つけます。 `Listen` ディレクティブ。
1. リッスンポートの値をに変更します。 `8080`. （利用可能な任意のリッスンポートを使用できます）。
1. 変更をに保存します。 `httpd.conf` をクリックして、テキストエディターを終了します。

## Varnish システムの設定を変更します。

Varnish システムの設定を変更するには：

1. を使用した As a ユーザー `root` 権限を持つ場合は、Vanish 設定ファイルをテキストエディターで開きます。

   - CentOS 6: `/etc/sysconfig/varnish`
   - CentOS 7: `/etc/varnish/varnish.params`
   - Debian: `/etc/default/varnish`
   - Ubuntu: `/etc/default/varnish`

1. Varnish listen ポートを 80 に設定します。

   ```conf
   VARNISH_LISTEN_PORT=80
   ```

   Varnish 4.x の場合は、DAEMON_OPTS に以下に対する正しいリスニングポートが含まれていることを確認してください。 `-a` パラメータ（VARNISH_LISTEN_PORT が正しい値に設定されている場合も含む）:

   ```conf
   DAEMON_OPTS="-a :80 \
      -T localhost:6082 \
      -f /etc/varnish/default.vcl \
      -S /etc/varnish/secret \
      -s malloc,256m"
   ```

1. 変更内容を Varnish 設定ファイルに保存し、テキストエディタを終了します。

### デフォルトの VCL の修正

この節では、Varnish が HTTP 応答ヘッダーを返すための最小限の設定を提供する方法について説明します。 これにより、設定する前に、Varnish が機能することを確認できます [!DNL Commerce] ワニスを使用するアプリケーション。

ワニスを最小限に設定するには：

1. バックアップ `default.vcl`:

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak
   ```

1. 開く `/etc/varnish/default.vcl` テキストエディター。
1. 次のスタンザを探します。

   ```conf
   backend default {
       .host = "127.0.0.1";
       .port = "80";
   }
   ```

1. の値を `.host` Varnish の完全修飾ホスト名または IP アドレスとリスニングポートを使用します。 _バックエンド_ または _公開元サーバー_&#x200B;つまり、コンテンツのニスを提供するサーバーは加速します。

   通常、これは web サーバーです。 参照： [バックエンドサーバー](https://varnish-cache.org/docs/trunk/users-guide/vcl-backends.html) が含まれる _ワニスガイド_.

1. の値を `.port` を web サーバーのリッスンポートに置き換えます（この例では 8080）。

   例：Apache がホスト 192.0.2.55 にインストールされ、Apache がポート 8080 をリッスンしている

   ```conf
   backend default {
       .host = "192.0.2.55";
       .port = "8080";
   }
   ```

   >[!INFO]
   >
   >Varnish と Apache が同じホスト上で実行されている場合、Adobeでは IP アドレスまたはホスト名を使用し、を使用しないことをお勧めします `localhost`.

1. 変更をに保存します。 `default.vcl` をクリックして、テキストエディターを終了します。

1. Varnish を再起動します。

   ```bash
   service varnish restart
   ```

Varnish を起動できない場合は、次のようにコマンドラインから実行してみてください。

```bash
varnishd -d -f /etc/varnish/default.vcl
```

エラーメッセージが表示されます。


>[!INFO]
>
>Varnish がサービスとして開始しない場合は、SELinux ルールを設定して実行できるようにする必要があります。

## ワニスが機能していることを確認します

次の節では、Varnish が機能していることを確認する方法について説明しますが、 _なし_ これを使用するようにCommerceを設定します。 Commerceを設定する前に、これを試してください。

以下のセクションで説明するタスクを、示された順序で実行します。

- [ワニスを開始](#start-varnish)
- [&#39;netstat&#39;](#netstat)

### ワニスを開始

Enter: `service varnish start`

Varnish をサービスとして起動できない場合は、次のようにコマンドラインから起動します。

1. Varnish CLI を起動します。

   ```bash
   varnishd -d -f /etc/varnish/default.vcl
   ```

1. Varnish 子プロセスを開始します。

   プロンプトが表示されたら、と入力します `start`

   正常に開始されたことを確認する次のメッセージが表示されます。

   ```terminal
   child (29805) Started
   200 0
   
   Child (29805) said
   Child (29805) said Child starts
   ```

### netstat

Varnish サーバにログインし、次のコマンドを入力します。

```bash
netstat -tulpn
```

特に、次の出力を探します。

```terminal
tcp        0      0 0.0.0.0:80                  0.0.0.0:*                   LISTEN      32614/varnishd
tcp        0      0 127.0.0.1:58484             0.0.0.0:*                   LISTEN      32604/varnishd
tcp        0      0 :::8080                     :::*                        LISTEN      26822/httpd
tcp        0      0 ::1:48509                   :::*                        LISTEN      32604/varnishd
```

前述の例では、ポート 80 で動作する Varnish と、ポート 8080 で動作する Apache を示しています。

の出力が表示されない場合 `varnishd`、ワニスが実行されていることを確認してください。

参照： [`netstat` オプション](https://tldp.org/LDP/nag2/x-087-2-iface.netstat.html).

## Commerce ソフトウェアのインストール

まだインストールしていない場合は、Commerce ソフトウェアをインストールします。 ベース URL の入力を求められたら、Varnish ホストおよびポート 80 （Varnish の場合）を使用します。これは、Varnish がすべての受信 HTTP リクエストを受信するためです。

Commerceのインストール中にエラーが発生した可能性があります：

```terminal
Error 503 Service Unavailable
Service Unavailable
XID: 303394517
Varnish cache server
```

このエラーが発生した場合は、を編集します `default.vcl` にタイムアウトを追加 `backend` stanza は次のように記述します。

```conf
backend default {
   .host = "127.0.0.1";
   .port = "8080";
   .first_byte_timeout = 600s;
}
```

## HTTP 応答ヘッダーの検証

これで、任意のページから返されたHTMLレスポンスヘッダーを確認することで、Varnish がページを提供していることを確認できます。

ヘッダーを確認する前に、Commerceを開発者モードに設定する必要があります。 それを行う方法はいくつかありますが、最も簡単なのは変更することです `.htaccess` Commerce アプリケーションルートのローカルファイルに書き込みます。 を使用することもできます [`magento deploy:mode:set`](../cli/set-mode.md) コマンド。

### Commerceを開発者モードに設定

Commerceを開発者モードに設定するには、 [`magento deploy:mode:set`](../cli/set-mode.md#change-to-developer-mode) コマンド。

### Varnish ログを見る

Varnish が実行されていることを確認し、Varnish サーバで次のコマンドを入力します。

```bash
varnishlog
```

Web ブラウザーで、任意のCommerce ページに移動します。

応答ヘッダーの長いリストがコマンドプロンプトウィンドウに表示されます。 次のようなヘッダーを探します。

```terminal
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

このようなヘッダーで _ではない_ 表示、ワニスを停止、チェックしてください `default.vcl`、およびもう一度試してください。

### HTML応答ヘッダーの確認

応答ヘッダーを調べる方法はいくつかあり、ブラウザーのプラグインやブラウザーインスペクターを使用する方法などがあります。

次の例では、を使用しています `curl`. このコマンドは、HTTP を使用してCommerce サーバーにアクセスできる任意のマシンから入力できます。

```bash
curl -I -v --location-trusted '<your Commerce base URL>'
```

以下に例を挙げます。

```bash
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

次のようなヘッダーを探します。

```terminal
Content-Type: text/html; charset=iso-8859-1
X-Varnish: 15
Age: 0
Via: 1.1 varnish-v6
X-Magento-Cache-Debug: HIT
```
