---
title: オプションソフトウェア
description: Adobe Commerceのオンプレミスインストールをサポートするためにインストールできるオプションソフトウェアの詳細について説明します。
exl-id: 533ff52b-3301-4624-b691-3dfddde6ce0b
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 0%

---

# オプションソフトウェア

cron 関連のタスクが適切に実行されるように、NTP をインストールすることを強くお勧めします。 （サーバーの日付は、過去や将来の日付などが考えられます）。

このトピックで取り上げるその他のオプションユーティリティは、インストールに役立つ場合がありますが、Adobe Commerceのインストールや使用には必要ありません。

## ネットワークタイムプロトコル（NTP）のインストールと設定

[NTP](https://www.ntp.org/) を使用すると、サーバーは [ グローバルに利用可能なプールサーバー ](https://www.ntppool.org/en/) を使用してシステムクロックを同期できます。 社内ネットワークまたは外部のパブリック サーバーの専用ハードウェア ソリューションであるかどうかにかかわらず、信頼できる NTP サーバーを使用することをお勧めします。

Adobe Commerceを複数のホストに導入する場合、NTP を使用すると、サーバーのタイムゾーンに関係なく、すべてのクロックが同期していることを簡単に保証できます。 また、cron 関連のタスク（インデックス作成やメールのトランザクション処理など）は、サーバーの時計が正確かどうかに依存します。

### Ubuntu での NTP のインストールと設定

次のコマンドを入力して NTP をインストールします。

```bash
apt-get install ntp
```

[NTP プール サーバーを使用する ](#use-ntp-pool-servers) を参照してください。

### CentOS での NTP のインストールと設定

NTP をインストールして構成するには、次の手順に従います。

1. 次のコマンドを入力して、適切な NTP ソフトウェアを検索します。

   ```bash
   yum search ntp
   ```

1. インストールするパッケージを選択します。 例：`ntp.x86_64`。

1. パッケージをインストール。

   ```bash
   yum -y install ntp.x86_64
   ```

1. サーバの起動時に NTP が起動するように、次のコマンドを入力します。

   ```bash
   chkconfig ntpd on
   ```

1. 次の節に進みます。

### NTP プール サーバーを使用する

プール・サーバの選択はユーザー次第です。 NTP プールサーバーを使用する場合、ntp.orgでは、[NTP プールプロジェクトページ ](https://www.ntppool.org/en/) で説明されているように、サーバーのタイムゾーンに近い [ プールサーバー ](https://www.ntppool.org/en/use.html) を使用することをお勧めします。 展開環境のすべてのホストが使用できるプライベート NTP サーバーがある場合は、代わりにそのサーバーを使用できます。

1. `/etc/ntp.conf` をテキストエディターで開きます。

1. 次のような行を探します。

   ```conf
   server 0.centos.pool.ntp.org
   server 1.centos.pool.ntp.org
   server 2.centos.pool.ntp.org
   ```

1. これらの行を置き換えるか、NTP プール サーバーまたは他の NTP サーバーを指定する行を追加します。 複数を指定することをお勧めします。

1. 米国ベースの 3 台の NTP サーバの使用例を次に示します。

   ```conf
   server 0.us.pool.ntp.org
   server 1.us.pool.ntp.org
   server 2.us.pool.ntp.org
   ```

1. `/etc/ntp.conf` への変更を保存し、テキストエディターを終了します。

1. サービスを再起動します。

   * Ubuntu: `service ntp restart`

   * CentOS: `service ntpd restart`

1. `date` を入力して、サーバーの日付を確認します。

   日付が正しくない場合は、ファイアウォールで NTP クライアントポート（通常は UDP 123）が開いていることを確認します。

   `ntpdate _[pool server hostname]_` コマンドを試します。 失敗した場合は、返されるエラーを検索します。

   他のすべてが失敗した場合は、サーバーを再起動してみてください。

## phpinfo.php の作成

[`phpinfo.php`](https://www.php.net/manual/en/function.phpinfo.php) ファイルには、PHP とその拡張機能に関する大量の情報が表示されます。

>[!NOTE]
>
>開発システムで `phpinfo.php` を使用します _のみ_。 実稼動環境では、セキュリティの問題になる場合があります。

Web サーバーの docroot の任意の場所に、次のコードを追加します。

```php
<?php
// Show all information, defaults to INFO_ALL
phpinfo();
```

詳しくは、[phpinfo マニュアルページ ](https://www.php.net/manual/en/function.phpinfo.php) を参照してください。

結果を表示するには、ブラウザーの場所または住所フィールドに次の URL を入力します。

```http
http://<web server host or IP>/phpinfo.php
```

404 （見つかりません）エラーが表示された場合は、次の点を確認してください。

* 必要に応じて、web サーバーを起動します。
* ファイアウォールでポート 80 でのトラフィックが許可されていることを確認します。

  [Ubuntu のヘルプ ](https://help.ubuntu.com/community/UFW)

  [CentOS のヘルプ ](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html)

## phpMyAdmin

phpMyAdmin アプリケーションは、使いやすく、無料のデータベース管理ユーティリティです。 データベースのコンテンツを確認および操作するために使用できます。 phpMyAdmin に MySQL データベース管理ユーザーとしてログインする必要があります。

phpMyAdmin の詳細については、[phpMyAdmin ホームページ ](https://www.phpmyadmin.net/) を参照してください。

インストールについて詳しくは、[phpMyAdmin インストールドキュメント ](https://docs.phpmyadmin.net/en/latest/setup.html#quick-install) を参照してください。

>[!NOTE]
>
>開発システムで phpMyAdmin を使用します _のみ_。 実稼動環境では、セキュリティの問題になる場合があります。

1. phpMyAdmin を使用するには、ブラウザのアドレスまたは場所フィールドに次のコマンドを入力します。

   ```http
   http://<web server host or IP>/phpmyadmin
   ```

1. プロンプトが表示されたら、MySQL データベース `root` または管理者ユーザーのユーザー名とパスワードを使用してログインします。
