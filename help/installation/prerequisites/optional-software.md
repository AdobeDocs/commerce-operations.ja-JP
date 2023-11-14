---
title: オプションのソフトウェア
description: Adobe CommerceとMagento Open Sourceのオンプレミスインストールをサポートするためにインストールできるオプションのソフトウェアの詳細を説明します。
exl-id: 533ff52b-3301-4624-b691-3dfddde6ce0b
source-git-commit: 40d850add2ef8c51e9192758135768306b163780
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 0%

---

# オプションのソフトウェア

CRON 関連のタスクが正しく実行されるように、NTP をインストールすることを強くお勧めします。 （サーバーの日付は、過去の日付と未来の日付のどちらにするかなどです）。

このトピックで説明する他のオプションのユーティリティは、インストールに役立つ場合がありますが、Adobe CommerceまたはMagento Open Sourceをインストールまたは使用するために必要なユーティリティではありません。

## NTP(Network Time Protocol) のインストールと構成

[NTP](https://www.ntp.org/) を使用して、サーバーがシステムクロックを同期できるようにします。 [グローバルに使用可能なプールサーバ](https://www.ntppool.org/en/). 信頼できる NTP サーバを使用することをお勧めします。NTP サーバは、内部ネットワークと外部、パブリックサーバのどちらの専用ハードウェアソリューションであるかに関わらずです。

複数のホストにAdobe CommerceまたはMagento Open Sourceをデプロイする場合、NTP は、サーバのタイムゾーンに関係なく、すべてのクロックが同期されることを保証する簡単な方法です。 また、cron 関連のタスク（インデックス作成やトランザクション E メールなど）は、正確なサーバークロックに依存します。

### Ubuntu での NTP のインストールと構成

次のコマンドを入力して、NTP をインストールします。

```bash
apt-get install ntp
```

次で続行 [NTP プールサーバを使用する](#use-ntp-pool-servers).

### CentOS での NTP のインストールと設定

NTP をインストールして構成するには、次の手順に従います。

1. 次のコマンドを入力して、適切な NTP ソフトウェアを検索します。

   ```bash
   yum search ntp
   ```

1. インストールするパッケージを選択します。 例： `ntp.x86_64`.

1. パッケージをインストールします。

   ```bash
   yum -y install ntp.x86_64
   ```

1. 次のコマンドを入力して、サーバが起動したときに NTP が起動するようにします。

   ```bash
   chkconfig ntpd on
   ```

1. 次の節に進みます。

### NTP プールサーバを使用する

プールサーバの選択は自由に行えます。 NTP プールサーバを使用する場合、 ntp.orgでは、 [プールサーバ](https://www.ntppool.org/en/) これは、サーバーのタイムゾーンに近いものです。 [NTP プールプロジェクトページ](https://www.ntppool.org/en/use.html). 展開中のすべてのホストで使用可能なプライベート NTP サーバがある場合は、代わりにそのサーバを使用できます。

1. 開く `/etc/ntp.conf` をクリックします。

1. 次のような行を探します。

   ```conf
   server 0.centos.pool.ntp.org
   server 1.centos.pool.ntp.org
   server 2.centos.pool.ntp.org
   ```

1. これらの行を置き換えるか、NTP プールサーバまたは他の NTP サーバを指定する行を追加します。 複数のを指定することをお勧めします。

1. 米国ベースの 3 台の NTP サーバの使用例を次に示します。

   ```conf
   server 0.us.pool.ntp.org
   server 1.us.pool.ntp.org
   server 2.us.pool.ntp.org
   ```

1. 変更をに保存します。 `/etc/ntp.conf` をクリックし、テキストエディタを終了します。

1. サービスを再起動します。

   * Ubuntu: `service ntp restart`

   * CentOS: `service ntpd restart`

1. 入力 `date` サーバーの日付を確認します。

   日付が正しくない場合は、NTP クライアントポート（通常は UDP 123）がファイアウォールで開いていることを確認します。

   所要時間： `ntpdate _[pool server hostname]_` コマンドを使用します。 失敗した場合は、返されるエラーを検索します。

   それ以外の場合は、サーバを再起動してみてください。

## phpinfo.php を作成します。

The [`phpinfo.php`](https://www.php.net/manual/en/function.phpinfo.php) ファイルは、PHP とその拡張に関する多くの情報を表示します。

>[!NOTE]
>
>用途 `phpinfo.php` 開発システムで _のみ_. 実稼動環境でのセキュリティ上の問題になる場合があります。

Web サーバーのドキュメントルートの任意の場所に次のコードを追加します。

```php
<?php
// Show all information, defaults to INFO_ALL
phpinfo();
```

詳しくは、 [phpinfo マニュアルページ](https://www.php.net/manual/en/function.phpinfo.php).

結果を表示するには、ブラウザーの場所またはアドレスフィールドに次の URL を入力します。

```http
http://<web server host or IP>/phpinfo.php
```

404（見つかりません）エラーが表示される場合は、次の点を確認してください。

* 必要に応じて、Web サーバーを起動します。
* ファイアウォールで、ポート 80 でのトラフィックが許可されていることを確認します。

  [Ubuntu のヘルプ](https://help.ubuntu.com/community/UFW)

  [CentOS のヘルプ](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html)

## phpMyAdmin

phpMyAdmin アプリケーションは、使いやすく、無料のデータベース管理ユーティリティです。 これを使用して、データベースの内容を確認および操作できます。 phpMyAdmin に MySQL データベース管理ユーザーとしてログインする必要があります。

phpMyAdmin の詳細については、 [phpMyAdmin ホームページ](https://www.phpmyadmin.net/).

インストールの詳細については、 [phpMyAdmin のインストールドキュメント](https://docs.phpmyadmin.net/en/latest/setup.html#quick-install).

>[!NOTE]
>
>開発システムで phpMyAdmin を使用する _のみ_. 実稼動環境でのセキュリティ上の問題になる場合があります。

1. phpMyAdmin を使用するには、ブラウザのアドレスまたは場所フィールドに次のコマンドを入力します。

   ```http
   http://<web server host or IP>/phpmyadmin
   ```

1. プロンプトが表示されたら、MySQL データベースを使用してログインします `root` または管理ユーザーのユーザー名とパスワード。
