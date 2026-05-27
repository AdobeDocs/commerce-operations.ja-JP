---
title: オプションのソフトウェア
description: オンプレミスでのAdobe Commerceのインストールをサポートするためにインストールできるオプションのソフトウェアについて詳しく説明します。
exl-id: 533ff52b-3301-4624-b691-3dfddde6ce0b
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '634'
ht-degree: 0%

---

# オプションのソフトウェア

クローン関連のタスクが適切に実行されるように、NTPをインストールすることを強くお勧めします。 （サーバーの日付は、例えば、過去または将来の日付である可能性があります）。

このトピックで説明するその他のオプションのユーティリティは、インストールに役立つ場合がありますが、Adobe Commerceのインストールや使用には必要ありません。

## Network Time Protocol （NTP）のインストールと設定

[NTP](https://www.ntp.org/)を使用すると、サーバーは[&#x200B; グローバルに利用可能なプールサーバー](https://www.ntppool.org/en/)を使用してシステムクロックを同期できます。 信頼できるNTP サーバーは、専用のハードウェアソリューションであるか、内部ネットワークまたは外部のパブリックサーバーであるかを問わず、使用することをお勧めします。

複数のホストにAdobe Commerceをデプロイする場合、NTPは、サーバーがどのタイムゾーンにあっても、すべてのクロックが同期されていることを保証する簡単な方法です。 また、cron関連のタスク（インデックス作成やトランザクションメールなど）は、サーバークロックの精度に依存します。

### UbuntuでのNTPのインストールと設定

次のコマンドを入力して、NTPをインストールします。

```shell
apt-get install ntp
```

[NTP プールサーバーを使用](#use-ntp-pool-servers)で続行します。

### CentOSでのNTPのインストールと設定

NTPをインストールして設定するには：

1. 次のコマンドを入力して、適切なNTP ソフトウェアを見つけます。

   ```shell
   yum search ntp
   ```

1. インストールするパッケージを選択します。 例：`ntp.x86_64`。

1. パッケージをインストールします。

   ```shell
   yum -y install ntp.x86_64
   ```

1. 次のコマンドを入力して、サーバーの起動時にNTPが開始されるようにします。

   ```shell
   chkconfig ntpd on
   ```

1. 次のセクションに進みます。

### NTP プールサーバーの使用

プールサーバーの選択は自分の責任です。 NTP プールサーバーを使用する場合、ntp.orgでは、[NTP プールプロジェクトページ &#x200B;](https://www.ntppool.org/en/use.html)で説明されているように、サーバーのタイムゾーンに近い[&#x200B; プールサーバー](https://www.ntppool.org/en/)を使用することをお勧めします。 デプロイメント内のすべてのホストで利用可能なプライベート NTP サーバーがある場合は、代わりにそのサーバーを使用できます。

1. `/etc/ntp.conf`をテキストエディターで開きます。

1. 次のような行を探します。

   ```conf
   server 0.centos.pool.ntp.org
   server 1.centos.pool.ntp.org
   server 2.centos.pool.ntp.org
   ```

1. これらの行を置き換えるか、NTP プールサーバーまたは他のNTP サーバーを指定する行を追加します。 複数を指定することをお勧めします。

1. 米国に拠点を置く3つのNTP サーバーを使用する例を次に示します。

   ```conf
   server 0.us.pool.ntp.org
   server 1.us.pool.ntp.org
   server 2.us.pool.ntp.org
   ```

1. 変更を`/etc/ntp.conf`に保存して、テキストエディターを終了します。

1. サービスを再起動します。

   * Ubuntu: `service ntp restart`

   * CentOS: `service ntpd restart`

1. サーバーの日付を確認するには、`date`と入力します。

   日付が正しくない場合は、NTP クライアントポート（通常はUDP 123）がファイアウォールで開いていることを確認します。

   `ntpdate _[pool server hostname]_` コマンドを試してください。 失敗した場合は、返されるエラーを検索します。

   他のすべてが失敗した場合は、サーバーを再起動してみてください。

## phpinfo.phpの作成

[`phpinfo.php`](https://www.php.net/manual/en/function.phpinfo.php) ファイルには、PHPとその拡張機能に関する大量の情報が表示されます。

>[!NOTE]
>
>開発システム _のみ_&#x200B;で`phpinfo.php`を使用します。 これは本番環境のセキュリティの問題かもしれません。

Web サーバーのdocroot内の任意の場所に次のコードを追加します。

```php
<?php
// Show all information, defaults to INFO_ALL
phpinfo();
```

詳しくは、[phpinfoのマニュアルページ &#x200B;](https://www.php.net/manual/en/function.phpinfo.php)を参照してください。

結果を表示するには、ブラウザーの場所または住所フィールドに次のURLを入力します。

```http
http://<web server host or IP>/phpinfo.php
```

404 （Not Found）エラーが表示される場合は、次の点を確認してください。

* 必要に応じてWeb サーバーを起動します。
* ファイアウォールでポート 80のトラフィックが許可されていることを確認します。

  [Ubuntuのヘルプ](https://help.ubuntu.com/community/UFW)

  [CentOSのヘルプ](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html)

## phpMyAdmin

phpMyAdmin アプリケーションは、使いやすい無料のデータベース管理ユーティリティです。 データベースの内容を確認および操作するために使用できます。 phpMyAdminにMySQL データベース管理ユーザーとしてログインする必要があります。

phpMyAdminについて詳しくは、[phpMyAdmin ホームページ &#x200B;](https://www.phpmyadmin.net/)を参照してください。

インストールについて詳しくは、[phpMyAdmin インストールドキュメント &#x200B;](https://docs.phpmyadmin.net/en/latest/setup.html#quick-install)を参照してください。

>[!NOTE]
>
>開発システム _only_&#x200B;でphpMyAdminを使用します。 これは本番環境のセキュリティの問題かもしれません。

1. phpMyAdminを使用するには、ブラウザーのアドレスまたは場所フィールドに次のコマンドを入力します。

   ```http
   http://<web server host or IP>/phpmyadmin
   ```

1. プロンプトが表示されたら、MySQL データベース `root`または管理ユーザーのユーザー名とパスワードを使用してログインします。
