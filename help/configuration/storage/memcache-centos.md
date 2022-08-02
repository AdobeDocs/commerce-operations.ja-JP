---
title: CentOS での memcached の設定
description: CentOS に memcached をインストールして設定します。
source-git-commit: 65060d067bbbfe139736df3800688ce897cb17be
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%

---


# CentOS での memcached の設定

この節では、CentOS で memcached をインストールする手順を説明します。 詳しくは、 [memcached wiki](https://github.com/memcached/old-wiki).

>[!INFO]
>
>Adobeは、最新の安定した memcached バージョン（現在は memcached の場合は 3.1.3）を使用することをお勧めします。

PHP は memcache をネイティブでサポートしていないので、PHP で使用するには拡張をインストールする必要があります。 PHP には 2 つの拡張機能があり、どの拡張機能を使用するかをデコードすることが重要です。

- `memcache` (_no d_) — 定期的に維持されない、古いが一般的な拡張機能。
この `memcache` 現在、拡張機能 _次の値と等しくない_ は PHP 7 で動作します。 詳しくは、 [memcache の PHP ドキュメント](https://www.php.net/manual/en/book.memcache.php).

   正確な名前は `php-pecl-memcache` （CentOS 用）

- `memcached` (_と`d`_)—PHP 7 と互換性のある、より新しく、維持された拡張。 詳しくは、 [memcached に関する PHP ドキュメント](https://www.php.net/manual/en/book.memcached.php).

   正確な名前は `php-pecl-memcached` （CentOS 用）

## CentOS で memcached をインストールして設定します。

CentOS に memcached をインストールするには、以下のタスクを `root` 権限：

1. memcached とその依存関係をインストールします。

   ```bash
   yum -y update
   ```

   ```bash
   yum install -y libevent libevent-devel
   ```

   ```bash
   yum install -y memcached
   ```

   ```bash
   yum install -y php-pecl-memcache
   ```

   >[!INFO]
   >
   >前述のコマンドの構文は、使用するパッケージリポジトリによって異なる場合があります。 例えば、webtatic と PHP 5.6 を使用する場合、 `yum install -y php56w-pecl-memcache`. 用途 `yum search memcache|grep php` 適切なパッケージ名を検索します。


1. 次の memcached 構成設定を変更します。 `CACHESIZE` および `OPTIONS`:

   1. 開く `/etc/sysconfig/memcached` をクリックします。
   1. 次の値を探します。 `CACHESIZE` を 1 GB 以上に変更します。 例：

      ```config
      CACHESIZE="1GB"
      ```

   1. 次の値を探します。 `OPTIONS` を変更します。 `localhost` または `127.0.0.1`

1. 変更をに保存します。 `memcached` をクリックし、テキストエディタを終了します。
1. memcached を再起動します。

   ```bash
   service memcached restart
   ```

1. Web サーバーを再起動します。

   Apache の場合：

   ```bash
   service httpd restart
   ```

1. 次の節に進みます。

## コマースをインストールする前に memcached の動作を確認

Adobeでは、Commerce をインストールする前に、memcached が機能することを確認することをお勧めします。 これをおこなうのに数分かかり、後で簡単にトラブルシューティングできます。

### Web サーバーが memcached を認識したことを確認します

Web サーバーが memcached を認識することを確認するには、次の手順を実行します。

1. の作成 `phpinfo.php` ファイルを web サーバーの docroot に配置します。

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. Web ブラウザーでそのページに移動します。

   例：`http://192.0.2.1/phpinfo.php`

1. memcache が次のように表示されていることを確認します。

![Web サーバーが memcache を認識したことを確認](../../assets/configuration/memcache.png)

memcached バージョン 3.0.5 以降を使用していることを確認します。

memcache が表示されない場合は、Web サーバーを再起動し、ブラウザページを更新します。 それでも表示されない場合は、 `php-pecl-memcache` 拡張子。

### MySQL データベースと PHP スクリプトから成る memcache テストを作成する

このテストでは、MySQL データベース、テーブル、およびデータを使用して、データベースデータを取得して memcache に保存できることを確認します。 PHP スクリプトは、最初に [キャッシュ](https://glossary.magento.com/cache). 結果が存在しない場合は、スクリプトはデータベースに対してクエリを実行します。 元のデータベースでクエリが処理された後、スクリプトは、 `set` コマンドを使用します。

[このテストの詳細](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-12-04)

MySQL データベースを作成します。

```bash
mysql -u root -p
```

次の場合： `mysql` プロンプトで、次のコマンドを入力します。

```sql
create database memcache_test;
GRANT ALL ON memcache_test.* TO memcache_test@localhost IDENTIFIED BY 'memcache_test';
use memcache_test;
create table example (id int, name varchar(30));
insert into example values (1, "new_data");
exit
```

作成 `cache-test.php` を web サーバーの docroot に設定します。

```php
$meminstance = new Memcached();

$meminstance->addServer('<memcached hostname or ip>', <memcached port>);

$query = "select id from example where name = 'new_data'";
$querykey = "KEY" . md5($query);

$result = $meminstance->get($querykey);

if (!$result) {
   try {
        $dbh = new PDO('mysql:host=localhost;dbname=memcache_test','memcache_test','memcache_test');
        $dbh->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
        $result = $dbh->query("select id from example where name = 'new_data'")->fetch();
        $meminstance->set($querykey, $result, 0, 600);
        print "got result from mysql\n";
        return 0;
    } catch (PDOException $e) {
        die($e->getMessage());
    }
}
print "got result from memcached\n";
return 0;
```

ここで、 `<memcached hostname or ip>` 次のいずれか `localhost`, `127.0.0.1`または memcache のホスト名または IP アドレス。 この `<memcached port>` はリッスンポートです。デフォルトでは `11211`.

コマンドラインからスクリプトを実行します。

```bash
cd <web server docroot>
```

```bash
php cache-test.php
```

最初の結果は次のようになります。 `got result from mysql`. つまり、キーは memcached には存在しなかったが、MySQL から取得されたということです。

2 つ目の結果は、 `got result from memcached`：値が memcached に正常に保存されたことを確認します。

最後に、Telnet を使用して memcache キーを表示できます。

```bash
telnet localhost <memcache port>
```

プロンプトに対して、と入力します。

```bash
stats items
```

結果は次のようになります。

```terminal
STAT items:3:number 1
STAT items:3:age 1075
STAT items:3:evicted 0
STAT items:3:evicted_nonzero 0
STAT items:3:evicted_time 0
STAT items:3:outofmemory 0
STAT items:3:tailrepairs 0
```

memcache ストレージをフラッシュし、Telnet を終了します。

```bash
flush_all
```

```bash
quit
```

[Telnet テストの追加情報](https://darkcoding.net/software/memcached-list-all-keys/)
