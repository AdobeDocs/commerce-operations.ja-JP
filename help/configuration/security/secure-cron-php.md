---
title: Cron PHP を保護する
description: ブラウザーで cron.php ファイルを実行できるユーザーを制限します。
feature: Configuration, Security
exl-id: c81fcab2-1ee3-4ec7-a300-0a416db98614
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '924'
ht-degree: 1%

---

# Cron PHP を保護する

このトピックでは、`pub/cron.php` をセキュリティで保護して、悪意のある攻撃で使用されないようにする方法について説明します。 Cron を保護しないと、任意のユーザーが cron を実行してCommerce アプリケーションを攻撃する可能性があります。

cron ジョブは、スケジュールされた複数のタスクを実行します。このジョブは、Commerce設定の重要な要素です。 スケジュールされたタスクには以下が含まれますが、これらに限定されません。

- 再インデックス
- メールの生成
- ニュースレターの生成
- サイトマップの生成

>[!INFO]
>
>cron グループについて詳しくは、[cron の設定と実行 ](../cli/configure-cron-jobs.md#run-cron-from-the-command-line) を参照してください。

次の方法で cron ジョブを実行できます。

- コマンドラインまたは crontab で [`magento cron:run`](../cli/configure-cron-jobs.md#run-cron-from-the-command-line) コマンドを使用する
- Web ブラウザーでの `pub/cron.php?[group=<name>]` へのアクセス

>[!INFO]
>
>[`magento cron:run`](../cli/configure-cron-jobs.md#run-cron-from-the-command-line) コマンドを使用して cron を実行する場合は、すでに保護されている別のプロセスを使用するので、何もする必要はありません。

## Apache で cron を保護

この節では、Apache で HTTP 基本認証を使用して cron を保護する方法について説明します。 これらの手順は、Apache 2.2 と CentOS 6 に基づいています。 詳しくは、次のいずれかのリソースを参照してください。

- [Apache 2.2 認証と承認のチュートリアル ](https://httpd.apache.org/docs/2.2/howto/auth.html)
- [Apache 2.4 認証と承認のチュートリアル ](https://httpd.apache.org/docs/2.4/howto/auth.html)

### パスワードファイルの作成

セキュリティ上の理由から、web サーバーの docroot を除く任意の場所にパスワードファイルを配置できます。 この例では、パスワードファイルを新しいディレクトリに保存しています。

`root` 権限を持つユーザーとして、次のコマンドを入力します。

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/passwords <username>
```

`<username>` の Web サーバーユーザーまたは別のユーザーを指定できます。 この例では web サーバーユーザーを使用しますが、ユーザーの選択はユーザー次第です。

画面の指示に従って、ユーザーのパスワードを作成します。

パスワード・ファイルに別のユーザーを追加するには、`root` 権限を持つユーザーとして次のコマンドを入力します。

```bash
htpasswd /usr/local/apache/password/passwords <username>
```

### ユーザーを追加して、承認済み cron グループを作成（オプション）

複数のユーザーを有効にするには、これらのユーザーを、グループファイルを含むパスワードファイルに追加します。

パスワード ファイルに別のユーザーを追加するには：

```bash
htpasswd /usr/local/apache/password/passwords <username>
```

承認済みグループを作成するには、web サーバーの docroot 外の任意の場所にグループファイルを作成します。 グループファイルは、グループの名前とグループ内のユーザーを指定します。 この例では、グループ名は `MagentoCronGroup` です。

```bash
vim /usr/local/apache/password/group
```

ファイルの内容：

```text
MagentoCronGroup: <username1> ... <usernameN>
```

### `.htaccess` で cron を保護

ファイルで cron を保護するには、次 `.htaccess` 手順に従います。

1. ファイルシステムの所有者としてCommerce サーバーにログインするか、に切り替えます。
1. `<magento_root>/pub/.htaccess` をテキストエディターで開きます。

   （`cron.php` は `pub` ディレクトリにあるので、この `.htaccess` のみを編集します）。

1. _1 人以上のユーザーの Cron アクセス。_ 既存の `<Files cron.php>` ディレクティブを次のように置き換えます。

   ```conf
   <Files cron.php>
      AuthType Basic
      AuthName "Cron Authentication"
      AuthUserFile /usr/local/apache/password/passwords
      Require valid-user
   </Files>
   ```

1. _グループの Cron アクセス。_ 既存の `<Files cron.php>` ディレクティブを次のように置き換えます。

   ```conf
   <Files cron.php>
      AuthType Basic
      AuthName "Cron Authentication"
      AuthUserFile /usr/local/apache/password/passwords
      AuthGroupFile <path to optional group file>
      Require group <name>
   </Files>
   ```

1. `.htaccess` への変更を保存し、テキストエディターを終了します。
1. [cron が安全であることを確認する ](#verify-cron-is-secure) を続行します。

## Nginx で cron を保護

この節では、Nginx web サーバーを使用して cron を保護する方法について説明します。 次のタスクを実行する必要があります。

1. Nginx の暗号化されたパスワード ファイルを設定する
1. `pub/cron.php` にアクセスするときにパスワードファイルを参照するように、nginx 設定を変更します

### パスワードファイルの作成

続行する前に、次のいずれかのリソースを参照してパスワードファイルを作成してください。

- [Ubuntu 14.04 （DigitalOcean）で Nginx を使用してパスワード認証を設定する方法 ](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-nginx-on-ubuntu-14-04)
- [Nginx による基本的な HTTP 認証（howtoforge） ](https://www.howtoforge.com/basic-http-authentication-with-nginx)

### `nginx.conf.sample` で cron を保護

Commerceには、最適化されたサンプルの nginx 設定ファイルが標準搭載されています。 cron を保護するために変更することをお勧めします。

1. [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) ファイルに次の内容を追加します。

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

1. nginx を再起動します。

```bash
systemctl restart nginx
```

1. [cron が安全であることを確認する ](#verify-cron-is-secure) を続行します。

## Cron が安全であることを確認

`pub/cron.php` が安全であることを確認する最も簡単な方法は、パスワード認証を設定した後で、`cron_schedule` のデータベーステーブルに行が作成されていることを確認することです。 この例では、SQL コマンドを使用してデータベースをチェックしますが、好きなツールを使用できます。

>[!INFO]
>
>この例で実行している `default` cron は、`crontab.xml` で定義されたスケジュールに従って実行されています。 一部の cron ジョブは 1 日に 1 回だけ実行されます。 ブラウザーから cron を初めて実行すると、`cron_schedule` テーブルは更新されますが、それ以降の `pub/cron.php` リクエストは設定したスケジュールで実行されます。

**cron が安全であることを確認するには**:

1. Commerce データベースユーザーまたは `root` としてデータベースにログインします。

   以下に例を挙げます。

   ```bash
   mysql -u magento -p
   ```

1. Commerce データベースを使用します。

   ```shell
   use <database-name>;
   ```

   以下に例を挙げます。

   ```shell
   use magento;
   ```

1. `cron_schedule` データベース テーブルからすべての行を削除します。

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

1. プロンプトが表示されたら、承認済みユーザーの名前とパスワードを入力します。 次の図に例を示します。

   ![HTTP Basic を使用した cron の認証 ](../../assets/configuration/cron-auth.png)

1. 行がテーブルに追加されたことを確認します。

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

## Web ブラウザーからの cron の実行

Web ブラウザーを使用して、開発中など、いつでも cron を実行できます。

>[!WARNING]
>
>最初にセキュリティを確保 _ずに_ ブラウザーで cron を実行しないでください。

Apache web サーバーを使用している場合、ブラウザーで cron を実行するには、まず `.htaccess` ファイルから制限を削除する必要があります。

1. Commerce ファイルシステムへの書き込み権限を持つユーザーとして、Commerce サーバーにログインします。
1. （Magentoへのエントリポイントに応じて）次のいずれかをテキストエディターで開きます。

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

   その後、次のように、web ブラウザーで cron を実行できます。

   ```text
   <your hostname or IP>/<Commerce root>/pub/cron.php[?group=<group name>]
   ```

ここで、

- `<your hostname or IP>` は、Commerce インストールのホスト名または IP アドレスです。
- `<Commerce root>` は、Commerce ソフトウェアをインストールした web サーバーの docroot 相対ディレクトリです。

  Commerce アプリケーションの実行に使用する正確な URL は、web サーバーとバーチャルホストの設定方法によって異なります。

- `<group name>` は有効な cron グループ名です（オプション）

以下に例を挙げます。

```http
https://magento.example.com/magento2/pub/cron.php?group=index
```

>[!INFO]
>
>cron を 2 回実行する必要があります。最初に実行するタスクを見つけ、もう一度タスク自体を実行します。 cron グループについて詳しくは、[cron の設定と実行 ](../cli/configure-cron-jobs.md) を参照してください。
