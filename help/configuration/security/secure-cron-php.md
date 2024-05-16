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

このトピックでは、セキュリティ保護について説明します `pub/cron.php` 悪意のある攻撃で使用されるのを防ぐ。 Cron を保護しないと、任意のユーザーが cron を実行してCommerce アプリケーションを攻撃する可能性があります。

cron ジョブは、スケジュールされた複数のタスクを実行します。このジョブは、Commerce設定の重要な要素です。 スケジュールされたタスクには以下が含まれますが、これらに限定されません。

- 再インデックス
- メールの生成
- ニュースレターの生成
- サイトマップの生成

>[!INFO]
>
>こちらを参照してください [Cron の設定と実行](../cli/configure-cron-jobs.md#run-cron-from-the-command-line) cron グループの詳細については、を参照してください。

次の方法で cron ジョブを実行できます。

- 使用， [`magento cron:run`](../cli/configure-cron-jobs.md#run-cron-from-the-command-line) コマンドラインまたは crontab でコマンドを実行する
- へのアクセス `pub/cron.php?[group=<name>]` Web ブラウザーで

>[!INFO]
>
>を使用する場合は、何もする必要はありません [`magento cron:run`](../cli/configure-cron-jobs.md#run-cron-from-the-command-line) cron を実行するコマンド。既に安全な別のプロセスを使用します。

## Apache で cron を保護

この節では、Apache で HTTP 基本認証を使用して cron を保護する方法について説明します。 これらの手順は、Apache 2.2 と CentOS 6 に基づいています。 詳しくは、次のいずれかのリソースを参照してください。

- [Apache 2.2 認証および承認に関するチュートリアル](https://httpd.apache.org/docs/2.2/howto/auth.html)
- [Apache 2.4 認証および承認に関するチュートリアル](https://httpd.apache.org/docs/2.4/howto/auth.html)

### パスワードファイルの作成

セキュリティ上の理由から、web サーバーの docroot を除く任意の場所にパスワードファイルを配置できます。 この例では、パスワードファイルを新しいディレクトリに保存しています。

を使用して、ユーザーとして次のコマンドを入力します `root` 権限：

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/passwords <username>
```

ここで、 `<username>` Web サーバーユーザーまたは別のユーザーにすることができます。 この例では web サーバーユーザーを使用しますが、ユーザーの選択はユーザー次第です。

画面の指示に従って、ユーザーのパスワードを作成します。

パスワードファイルに別のユーザーを追加するには、ユーザーとして次のコマンドを入力します。 `root` 権限：

```bash
htpasswd /usr/local/apache/password/passwords <username>
```

### ユーザーを追加して、承認済み cron グループを作成（オプション）

複数のユーザーを有効にするには、これらのユーザーを、グループファイルを含むパスワードファイルに追加します。

パスワード ファイルに別のユーザーを追加するには：

```bash
htpasswd /usr/local/apache/password/passwords <username>
```

承認済みグループを作成するには、web サーバーの docroot 外の任意の場所にグループファイルを作成します。 グループファイルは、グループの名前とグループ内のユーザーを指定します。 この例では、グループ名は `MagentoCronGroup`.

```bash
vim /usr/local/apache/password/group
```

ファイルの内容：

```text
MagentoCronGroup: <username1> ... <usernameN>
```

### で cron を保護 `.htaccess`

Cron を保護するには `.htaccess` ファイル：

1. ファイルシステムの所有者としてCommerce サーバーにログインするか、に切り替えます。
1. 開く `<magento_root>/pub/.htaccess` テキストエディター。

   （理由： `cron.php` 次の場所にあります。 `pub` ディレクトリ、編集 `.htaccess` のみ。）

1. _1 人以上のユーザーの Cron アクセス。_ 既存のを `<Files cron.php>` ディレクティブに以下を指定します。

   ```conf
   <Files cron.php>
      AuthType Basic
      AuthName "Cron Authentication"
      AuthUserFile /usr/local/apache/password/passwords
      Require valid-user
   </Files>
   ```

1. _グループの Cron アクセス。_ 既存のを `<Files cron.php>` ディレクティブに以下を指定します。

   ```conf
   <Files cron.php>
      AuthType Basic
      AuthName "Cron Authentication"
      AuthUserFile /usr/local/apache/password/passwords
      AuthGroupFile <path to optional group file>
      Require group <name>
   </Files>
   ```

1. 変更をに保存します。 `.htaccess` をクリックして、テキストエディターを終了します。
1. 続行 [Cron が安全であることを確認](#verify-cron-is-secure).

## Nginx で cron を保護

この節では、Nginx web サーバーを使用して cron を保護する方法について説明します。 次のタスクを実行する必要があります。

1. Nginx の暗号化されたパスワード ファイルを設定する
1. にアクセスするときにパスワードファイルを参照するように、nginx 設定を変更します `pub/cron.php`

### パスワードファイルの作成

続行する前に、次のいずれかのリソースを参照してパスワードファイルを作成してください。

- [Ubuntu 14.04 （DigitalOcean）で Nginx を使用してパスワード認証を設定する方法](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-nginx-on-ubuntu-14-04)
- [Nginx を使用した基本的な HTTP 認証（howtoforge）](https://www.howtoforge.com/basic-http-authentication-with-nginx)

### で cron を保護 `nginx.conf.sample`

Commerceには、最適化されたサンプルの nginx 設定ファイルが標準搭載されています。 cron を保護するために変更することをお勧めします。

1. 以下のを [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) ファイル：

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

1. 続行 [Cron が安全であることを確認](#verify-cron-is-secure).

## Cron が安全であることを確認

を確認する最も簡単な方法 `pub/cron.php` で行が作成されていることを確認することが安全 `cron_schedule` パスワード認証を設定した後のデータベーステーブル。 この例では、SQL コマンドを使用してデータベースをチェックしますが、好きなツールを使用できます。

>[!INFO]
>
>この `default` この例で実行している cron は、で定義されたスケジュールに従って実行されます。 `crontab.xml`. 一部の cron ジョブは 1 日に 1 回だけ実行されます。 ブラウザーから cron を初めて実行する場合、 `cron_schedule` テーブルは更新されますが、後続の場合は `pub/cron.php` リクエストは設定されたスケジュールで実行されます。

**Cron が安全であることを確認するには**:

1. Commerce データベースユーザーとして、またはとしてデータベースにログインします。 `root`.

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

1. すべての行をから削除 `cron_schedule` データベース テーブル：

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

   ![HTTP Basic を使用した cron の承認](../../assets/configuration/cron-auth.png)

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
>実行 _ではない_ 最初にセキュリティ保護することなく、ブラウザーで cron を実行します。

Apache web サーバーを使用している場合は、から制限を削除する必要があります `.htaccess` ブラウザーで cron を実行する前に行うファイル：

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
- `<Commerce root>` は、Commerce ソフトウェアをインストールした web サーバーの docroot 相対ディレクトリです

  Commerce アプリケーションの実行に使用する正確な URL は、web サーバーとバーチャルホストの設定方法によって異なります。

- `<group name>` は有効な cron グループ名です（オプション）

以下に例を挙げます。

```http
https://magento.example.com/magento2/pub/cron.php?group=index
```

>[!INFO]
>
>cron を 2 回実行する必要があります。最初に実行するタスクを見つけ、もう一度タスク自体を実行します。 こちらを参照してください [Cron の設定と実行](../cli/configure-cron-jobs.md) cron グループの詳細については、を参照してください。
