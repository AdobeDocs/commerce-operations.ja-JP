---
title: Web サーバーの設定
description: Vanrish と連携するように Web サーバーを設定する方法を説明します。
feature: Configuration, Cache, Install, Logs
exl-id: b31179ef-3c0e-4a6b-a118-d3be1830ba4e
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 0%

---

# Web サーバーの設定

Wanish は Web サーバーではなく受信 HTTP 要求に直接応答するので、Web サーバーをデフォルトポート 80 以外のポートでリッスンするように設定します。

次の節では、例としてポート 8080 を使用します。

**Apache 2.4 リスンポートを変更するには**:

1. 開く `/etc/httpd/conf/httpd.conf` をクリックします。
1. を `Listen` ディレクティブ。
1. リッスンポートの値をに変更します。 `8080`. （使用可能な任意のリスンポートを使用できます）。
1. 変更をに保存します。 `httpd.conf` をクリックし、テキストエディタを終了します。

## Vanish システムの構成を変更する

Vanish システムの構成を変更するには、次の手順に従います。

1. を使用して `root` 権限を持つ場合は、テキストエディターで Vanish 設定ファイルを開きます。

   - CentOS 6: `/etc/sysconfig/varnish`
   - CentOS 7: `/etc/varnish/varnish.params`
   - Debian: `/etc/default/varnish`
   - Ubuntu: `/etc/default/varnish`

1. Vanish リッスンポートを 80 に設定します。

   ```conf
   VARNISH_LISTEN_PORT=80
   ```

   Vanish 4.x の場合、DAEMON_OPTS に `-a` パラメータ（VANISH_LISTEN_PORT が正しい値に設定されている場合でも）:

   ```conf
   DAEMON_OPTS="-a :80 \
      -T localhost:6082 \
      -f /etc/varnish/default.vcl \
      -S /etc/varnish/secret \
      -s malloc,256m"
   ```

1. 変更内容を Vanish 設定ファイルに保存し、テキストエディタを終了します。

### デフォルトの VCL を修正する

このセクションでは、Vanrish が HTTP 応答ヘッダーを返すように、最小限の設定を提供する方法について説明します。 これにより、Vanish が機能することを確認してから、 [!DNL Commerce] ワニスを使用する場合の適用。

Vanish を最小限に設定するには：

1. バックアップ `default.vcl`:

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak
   ```

1. 開く `/etc/varnish/default.vcl` をクリックします。
1. 次の規格を探します。

   ```conf
   backend default {
       .host = "127.0.0.1";
       .port = "80";
   }
   ```

1. 次の値を `.host` 完全修飾ホスト名または IP アドレスと Vanish のリッスンポート _バックエンド_ または _接触元サーバー_;つまり、コンテンツ Vanrish を提供するサーバは、高速化します。

   通常、これは Web サーバーです。 詳しくは、 [バックエンドサーバー](https://varnish-cache.org/docs/trunk/users-guide/vcl-backends.html) 内 _ワニスガイド_.

1. 次の値を `.port` Web サーバーのリスンポート（この例では 8080）を使用している。

   例：Apache がホスト 192.0.2.55 にインストールされ、Apache がポート 8080 でリッスンしています。

   ```conf
   backend default {
       .host = "192.0.2.55";
       .port = "8080";
   }
   ```

   >[!INFO]
   >
   >Vanish と Apache が同じホスト上で実行されている場合、Adobeでは IP アドレスまたはホスト名を使用し、 `localhost`.

1. 変更をに保存します。 `default.vcl` をクリックし、テキストエディタを終了します。

1. ワニスを再起動：

   ```bash
   service varnish restart
   ```

Vanish が起動しない場合は、次のようにコマンドラインから実行してみてください。

```bash
varnishd -d -f /etc/varnish/default.vcl
```

これにより、エラーメッセージが表示されます。


>[!INFO]
>
>Vanish がサービスとして起動しない場合は、SELinux ルールを設定して実行できるようにする必要があります。

## ワニスが機能していることを確認

次のセクションでは、Vanish が機能していることを確認する方法を説明します。 _なし_ 使用する Commerce を設定しています。 コマースを設定する前に、この操作を試す必要があります。

次のセクションで説明したタスクを、次の順に実行します。

- [ワニスを起動](#start-varnish)
- [&#39;netstat&#39;](#netstat)

### ワニスを起動

入力： `service varnish start`

Vanrish がサービスとして起動しない場合は、次のようにコマンドラインから起動します。

1. Vanish CLI を起動します。

   ```bash
   varnishd -d -f /etc/varnish/default.vcl
   ```

1. Vanish 子プロセスを開始します。

   プロンプトが表示されたら、次のように入力します。 `start`

   開始が成功したことを確認する次のメッセージが表示されます。

   ```terminal
   child (29805) Started
   200 0
   
   Child (29805) said
   Child (29805) said Child starts
   ```

### netstat

Vanish サーバにログインし、次のコマンドを入力します。

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

上記の図は、ポート 80 で Vanish を実行し、ポート 8080 で Apache を実行していることを示しています。

の出力が表示されない場合 `varnishd`、Vanrish が実行中であることを確認します。

詳しくは、 [`netstat` options](https://tldp.org/LDP/nag2/x-087-2-iface.netstat.html).

## Commerce ソフトウェアのインストール

コマースソフトウェアをインストールしていない場合は、インストールします。 Base URL の入力を求められたら、Vanish はすべての受信 HTTP 要求を受け取るので、Vanish ホストとポート 80（Vanish 用）を使用します。

コマースのインストール中にエラーが発生した可能性があります：

```terminal
Error 503 Service Unavailable
Service Unavailable
XID: 303394517
Varnish cache server
```

このエラーが発生した場合は、 `default.vcl` タイムアウトを `backend` stanza は次のようになります。

```conf
backend default {
   .host = "127.0.0.1";
   .port = "8080";
   .first_byte_timeout = 600s;
}
```

## HTTP 応答ヘッダーの検証

これで、Vanrish がページを提供していることを確認するには、任意のページから返されたHTML応答ヘッダーを調べます。

ヘッダーを確認する前に、開発者モードに Commerce を設定する必要があります。 その方法はいくつかあり、最も簡単な方法は次のとおりです。 `.htaccess` （コマースアプリケーションのルート）をクリックします。 また、 [`magento deploy:mode:set`](../cli/set-mode.md) コマンドを使用します。

### 開発者モード用にコマースを設定

開発者モード用にコマースを設定するには、 [`magento deploy:mode:set`](../cli/set-mode.md#change-to-developer-mode) コマンドを使用します。

### ワニスのログを見る

Vanish が実行中であることを確認し、Vanish サーバで次のコマンドを入力します。

```bash
varnishlog
```

Web ブラウザーで、任意のコマースページに移動します。

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

このようなヘッダーでは _not_ 表示、ワニスを停止、確認 `default.vcl`を再度お試しください。

### HTML応答ヘッダーを見る

ブラウザープラグインやブラウザーインスペクターの使用など、応答ヘッダーを見る方法はいくつかあります。

次の例では、 `curl`. このコマンドは、HTTP を使用して Commerce サーバーにアクセスできる任意のマシンから入力できます。

```bash
curl -I -v --location-trusted '<your Commerce base URL>'
```

例：

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
