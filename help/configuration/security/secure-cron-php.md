---
title: セキュア cron PHP
description: ブラウザーで cron.php ファイルを実行できるユーザーを制限します。
feature: Configuration, Security
exl-id: c81fcab2-1ee3-4ec7-a300-0a416db98614
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '938'
ht-degree: 1%

---

# セキュア cron PHP

このトピックでは、セキュリティ保護について説明します。 `pub/cron.php` 悪意のある攻撃に使われるのを防ぐために。 cron を保護しない場合、任意のユーザーが cron を実行してコマースアプリケーションを攻撃する可能性があります。

cron ジョブは、スケジュールされた複数のタスクを実行し、コマース設定の重要な要素です。 予定タスクには次のものが含まれますが、これらに限定されません。

- インデックス再作成
- 電子メールの生成
- ニュースレターの生成
- サイトマップの生成

>[!INFO]
>
>参照： [cron の設定と実行](../cli/configure-cron-jobs.md#run-cron-from-the-command-line) cron グループの詳細を参照してください。

cron ジョブは、次の方法で実行できます。

- の使用 [`magento cron:run`](../cli/configure-cron-jobs.md#run-cron-from-the-command-line) コマンドは、コマンドラインまたは crontab で
- へのアクセス `pub/cron.php?[group=<name>]` Web ブラウザー内

>[!INFO]
>
>を使用する場合は、何もする必要はありません。 [`magento cron:run`](../cli/configure-cron-jobs.md#run-cron-from-the-command-line) コマンドを使用して cron を実行する必要があります。既にセキュリティで保護されている別のプロセスを使用しているからです。

## Apache との cron のセキュリティ保護

この節では、Apache で HTTP 基本認証を使用して cron を保護する方法について説明します。 これらの手順は、CentOS 6 の Apache 2.2 に基づいています。 詳しくは、次のリソースの 1 つを参照してください。

- [Apache 2.2 認証および承認チュートリアル](https://httpd.apache.org/docs/2.2/howto/auth.html)
- [Apache 2.4 の認証と承認に関するチュートリアル](https://httpd.apache.org/docs/2.4/howto/auth.html)

### パスワードファイルの作成

セキュリティ上の理由から、Web サーバーの docroot 以外の場所でも、パスワードファイルを見つけることができます。 この例では、パスワードファイルを新しいディレクトリに保存します。

を使用して、次のコマンドをユーザーとして入力します。 `root` 権限：

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/passwords <username>
```

ここで、 `<username>` は、Web サーバーユーザーまたは別のユーザーです。 この例では、Web サーバーユーザーを使用しますが、ユーザーの選択はユーザー次第です。

画面の指示に従って、ユーザーのパスワードを作成します。

別のユーザーをパスワードファイルに追加するには、次のコマンドを `root` 権限：

```bash
htpasswd /usr/local/apache/password/passwords <username>
```

### ユーザーを追加して、認証済みの cron グループを作成する（オプション）

グループファイルを含むパスワードファイルに複数のユーザーを追加することで、cron を実行できるようにすることができます。

別のユーザーをパスワードファイルに追加するには、次の手順に従います。

```bash
htpasswd /usr/local/apache/password/passwords <username>
```

承認済みのグループを作成するには、Web サーバーのドキュメントルートの外側にある任意の場所にグループファイルを作成します。 グループファイルは、グループの名前とグループ内のユーザーを指定します。 この例では、グループ名は `MagentoCronGroup`.

```bash
vim /usr/local/apache/password/group
```

ファイルの内容：

```text
MagentoCronGroup: <username1> ... <usernameN>
```

### での cron の保護 `.htaccess`

で cron を保護するには `.htaccess` ファイル：

1. コマースサーバーに、ファイルシステムの所有者としてログインするか、ファイルシステムの所有者に切り替えます。
1. 開く `<magento_root>/pub/.htaccess` をクリックします。

   ( 理由 `cron.php` は、 `pub` ディレクトリ、編集 `.htaccess` のみ )

1. _1 人以上のユーザーに対する Cron アクセス。_ 既存の `<Files cron.php>` 次のようなディレクティブが含まれます。

   ```conf
   <Files cron.php>
      AuthType Basic
      AuthName "Cron Authentication"
      AuthUserFile /usr/local/apache/password/passwords
      Require valid-user
   </Files>
   ```

1. _グループの Cron アクセス。_ 既存の `<Files cron.php>` 次のようなディレクティブが含まれます。

   ```conf
   <Files cron.php>
      AuthType Basic
      AuthName "Cron Authentication"
      AuthUserFile /usr/local/apache/password/passwords
      AuthGroupFile <path to optional group file>
      Require group <name>
   </Files>
   ```

1. 変更をに保存します。 `.htaccess` をクリックし、テキストエディタを終了します。
1. 次で続行 [cron がセキュリティで保護されていることを確認します。](#verify-cron-is-secure).

## Nginx で cron を保護

このセクションでは、Nginx Web サーバを使用して cron を保護する方法について説明します。 次のタスクを実行する必要があります。

1. Nginx 用の暗号化されたパスワードファイルの設定
1. にアクセスする際にパスワードファイルを参照するように nginx 設定を変更します `pub/cron.php`

### パスワードファイルの作成

続行する前に、次のいずれかのリソースを参照してパスワードファイルを作成します。

- [Ubuntu 14.04(DigitalOcean) で Nginx を使用したパスワード認証を設定する方法](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-nginx-on-ubuntu-14-04)
- [Nginx を使用した基本 HTTP 認証 (howtoforge)](https://www.howtoforge.com/basic-http-authentication-with-nginx)

### での cron の保護 `nginx.conf.sample`

Commerce には、標準で最適化されたサンプルの nginx 設定ファイルが用意されています。 cron を保護するために変更することをお勧めします。

1. 以下を [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) ファイル：

   ```conf
   #Securing cron
   location ~ cron\.php$ {
      auth_basic "Cron Authentication";
      auth_basic_user_file /etc/nginx/.htpasswd;
   
      try_files $uri =404;
      fastcgi_pass   fastcgi_backend;
      fastcgi_buffers 1024 4k;
   
      fastcgi_read_timeout 600s;
      fastcgi_connect_timeout 600s;
   
      fastcgi_index  index.php;
      fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
      include        fastcgi_params;
   }
   ```

1.nginx を再起動します。

```bash
systemctl restart nginx
```

1. 次で続行 [cron がセキュリティで保護されていることを確認します。](#verify-cron-is-secure).

## cron がセキュリティで保護されていることを確認します。

確かめる最も簡単な方法は `pub/cron.php` が安全なのは、 `cron_schedule` データベーステーブルに保存されます。 この例では、SQL コマンドを使用してデータベースをチェックしますが、好きなツールを使用できます。

>[!INFO]
>
>The `default` この例で実行している cron は、 `crontab.xml`. cron ジョブの中には、1 日に 1 回だけ実行されるものもあります。 ブラウザーから cron を初めて実行したとき、 `cron_schedule` テーブルは更新されますが、後続は更新されません `pub/cron.php` リクエストは、設定されたスケジュールで実行されます。

**cron がセキュアであることを確認するには**:

1. データベースに、Commerce データベースユーザーまたは `root`.

   以下に例を挙げます。

   ```bash
   mysql -u magento -p
   ```

1. コマースデータベースを使用します。

   ```shell
   use <database-name>;
   ```

   以下に例を挙げます。

   ```shell
   use magento;
   ```

1. すべての行を `cron_schedule` データベーステーブル：

   ```shell
   TRUNCATE TABLE cron_schedule;
   ```

1. ブラウザーから cron を実行します。

   ```shell
   http[s]://<Commerce hostname or ip>/cron.php?group=default
   ```

   例：

   ```shell
   http://magento.example.com/cron.php?group=default
   ```

1. プロンプトが表示されたら、認証済みユーザーの名前とパスワードを入力します。 次の図に例を示します。

   ![HTTP Basic を使用した cron の認証](../../assets/configuration/cron-auth.png)

1. テーブルに行が追加されたことを確認します。

   ```shell
   SELECT * from cron_schedule;
   
   mysql> SELECT * from cron_schedule;
   +-------------+-----------------------------------------------+---------+----------+---------------------+---------------------+-------------+-------------+
   | schedule_id | job_code                             | status  | messages | created_at        | scheduled_at      | executed_at | finished_at |
   +-------------+-----------------------------------------------+---------+----------+---------------------+---------------------+-------------+-------------+
   |         1 | catalog_product_outdated_price_values_cleanup | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         2 | sales_grid_order_async_insert             | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         3 | sales_grid_order_invoice_async_insert       | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         4 | sales_grid_order_shipment_async_insert      | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         5 | sales_grid_order_creditmemo_async_insert     | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         6 | sales_send_order_emails                  | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         7 | sales_send_order_invoice_emails            | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         8 | sales_send_order_shipment_emails           | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         9 | sales_send_order_creditmemo_emails         | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |        10 | newsletter_send_all                     | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:25:00 | NULL      | NULL      |
   |        11 | captcha_delete_old_attempts               | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:30:00 | NULL      | NULL      |
   |        12 | captcha_delete_expired_images             | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:30:00 | NULL      | NULL      |
   |        13 | outdated_authentication_failures_cleanup     | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |        14 | magento_newrelicreporting_cron            | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   +-------------+-----------------------------------------------+---------+----------+---------------------+---------------------+-------------+-------------+
   14 rows in set (0.00 sec)
   ```

## Web ブラウザーから cron を実行する

cron は、開発時など、Web ブラウザーを使用していつでも実行できます。

>[!WARNING]
>
>実行 _not_ 最初に cron を保護せずに、ブラウザーで cron を実行します。

Apache Web サーバーを使用している場合は、 `.htaccess` ファイルを使用して、ブラウザーで cron を実行する前に、次の手順を実行します。

1. Commerce ファイルシステムに書き込む権限を持つユーザーとして Commerce サーバーにログインします。
1. テキストエディターで次のいずれかを開きます (Magentoへのエントリポイントに応じて異なります )。

   ```text
   <magento_root>/pub/.htaccess
   <magento_root>/.htaccess
   ```

1. 以下を削除またはコメントアウトします。

   ```conf
   ## Deny access to cron.php
     <Files cron.php>
        order allow,deny
        deny from all
     </Files>
   ```

   以下に例を挙げます。

   ```conf
   ## Deny access to cron.php
      #<Files cron.php>
         # order allow,deny
         # deny from all
      #</Files>
   ```

1. 変更を保存し、テキストエディターを終了します。

   その後、次のように、Web ブラウザーで cron を実行できます。

   ```text
   <your hostname or IP>/<Commerce root>/pub/cron.php[?group=<group name>]
   ```

次の場合：

- `<your hostname or IP>` は、コマースインストールのホスト名または IP アドレスです
- `<Commerce root>` は、Commerce ソフトウェアをインストールした Web サーバーの docroot-relative ディレクトリです。

  コマースアプリケーションを実行するために使用する正確な URL は、Web サーバーと仮想ホストの設定方法によって異なります。

- `<group name>` は任意の有効な cron グループ名です（オプション）

以下に例を挙げます。

```http
https://magento.example.com/magento2/pub/cron.php?group=index
```

>[!INFO]
>
>cron を 2 回実行する必要があります。最初に実行するタスクを検出し、再び自分でタスクを実行します。 参照： [cron の設定と実行](../cli/configure-cron-jobs.md) cron グループの詳細を参照してください。
