---
title: CentOSでのmemcachedの設定
description: Adobe Commerce キャッシュ用にCentOSにmemcachedをインストールして設定する方法について説明します。 設定の手順と最適化のヒントを説明します。
feature: Configuration, Cache, Storage
exl-id: fc4ad18b-7e99-496e-aebc-1d7640d8716c
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '593'
ht-degree: 0%

---

# CentOSでのmemcachedの設定

この節では、CentOSにmemcachedをインストールする手順を説明します。 詳細については、[memcached wiki](https://github.com/memcached/old-wiki)を参照してください。

>[!INFO]
>
>Adobeでは、最新の安定したmemcached バージョン（現在はmemcached用に3.1.3）を使用することをお勧めします。

PHPはmemcacheをネイティブにサポートしていないので、PHPで使用するには拡張機能をインストールする必要があります。 利用可能なPHP拡張機能は2つあり、どの拡張機能を使用するかをデコードすることが重要です。

- `memcache` （_no d_） – 古いが人気のある拡張機能で、定期的にメンテナンスされません。
現在`memcache`拡張機能&#x200B;_はPHP 7で動作しません。_ memcache](https://www.php.net/manual/en/book.memcache.php)については、[PHP ドキュメントを参照してください。

  CentOSの正確な名前は`php-pecl-memcache`です。

- `memcached` （_と`d`_） - PHP 7と互換性のある、新しく保守された拡張機能。 memcached](https://www.php.net/manual/en/book.memcached.php)については、[PHP ドキュメントを参照してください。

  CentOSの正確な名前は`php-pecl-memcached`です。

## CentOSでのmemcachedのインストールと設定

CentOSにmemcachedをインストールするには、`root`権限を持つユーザーとして次のタスクを実行します。

1. memcachedとその依存関係をインストールします。

   ```shell
   yum -y update
   ```

   ```shell
   yum install -y libevent libevent-devel
   ```

   ```shell
   yum install -y memcached
   ```

   ```shell
   yum install -y php-pecl-memcache
   ```

   >[!INFO]
   >
   >上記のコマンドの構文は、使用するパッケージリポジトリによって異なる場合があります。 例えば、webtaticとPHP 5.6を使用する場合は、`yum install -y php56w-pecl-memcache`と入力します。 `yum search memcache|grep php`を使用して、適切なパッケージ名を見つけます。


1. `CACHESIZE`と`OPTIONS`のmemcached設定設定を変更します。

   1. `/etc/sysconfig/memcached`をテキストエディターで開きます。
   1. `CACHESIZE`の値を探し、1 GB以上に変更します。 例：

      ```config
      CACHESIZE="1GB"
      ```

   1. `OPTIONS`の値を見つけて、`localhost`または`127.0.0.1`に変更します

1. 変更を`memcached`に保存して、テキストエディターを終了します。
1. memcachedを再起動します。

   ```shell
   service memcached restart
   ```

1. Web サーバーを再起動します。

   Apacheの場合

   ```shell
   service httpd restart
   ```

1. 次のセクションに進みます。

## Commerceをインストールする前に、memcachedが機能することを確認する

Adobeでは、Commerceをインストールする前にmemcachedをテストして、動作することを確認することをお勧めします。 これには数分しかかかりませんし、後でトラブルシューティングを簡素化できます。

### memcachedがweb サーバーで認識されていることを確認します

memcachedがweb サーバーで認識されていることを確認するには：

1. Web サーバーのdocrootに`phpinfo.php` ファイルを作成します。

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. web ブラウザーでそのページに移動します。

   例：`http://192.0.2.1/phpinfo.php`

1. memcacheが次のように表示されることを確認します。

![memcacheがweb サーバーによって認識されていることを確認する](../../assets/configuration/memcache.png)

memcached バージョン 3.0.5以降を使用していることを確認します。

memcacheが表示されない場合は、web サーバーを再起動し、ブラウザーページを更新します。 それでも表示されない場合は、`php-pecl-memcache`拡張機能がインストールされていることを確認してください。

### MySQL データベースとPHP スクリプトで構成されるmemcache テストの作成

このテストでは、MySQL データベース、テーブル、およびデータを使用して、データベースデータを取得してmemcacheに保存できることを検証します。 PHP スクリプトは、まずキャッシュを検索します。 結果が存在しない場合、スクリプトはデータベースをクエリします。 クエリが元のデータベースによって満たされた後、スクリプトは`set` コマンドを使用して結果をmemcacheに保存します。

[このテストの詳細](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-12-04)

MySQL データベースを作成します。

```shell
mysql -u root -p
```

`mysql` プロンプトで、次のコマンドを入力します。

```sql
create database memcache_test;
GRANT ALL ON memcache_test.* TO memcache_test@localhost IDENTIFIED BY 'memcache_test';
use memcache_test;
create table example (id int, name varchar(30));
insert into example values (1, "new_data");
exit
```

Web サーバーのdocrootに`cache-test.php`を作成します。

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

ここで、`<memcached hostname or ip>`は`localhost`、`127.0.0.1`、またはmemcache ホスト名またはIP アドレスのいずれかです。 `<memcached port>`はリッスン ポートです。既定では`11211`。

コマンドラインからスクリプトを実行します。

```shell
cd <web server docroot>
```

```shell
php cache-test.php
```

最初の結果は`got result from mysql`です。 これは、キーがmemcachedに存在しなかったが、MySQLから取得されたことを意味します。

2つ目の結果は`got result from memcached`です。これにより、値がmemcachedに正常に保存されていることを確認します。

最後に、Telnetを使用してmemcache キーを表示できます。

```shell
telnet localhost <memcache port>
```

プロンプトに、次のように入力します

```shell
stats items
```

結果は次のようになります。

```text
STAT items:3:number 1
STAT items:3:age 1075
STAT items:3:evicted 0
STAT items:3:evicted_nonzero 0
STAT items:3:evicted_time 0
STAT items:3:outofmemory 0
STAT items:3:tailrepairs 0
```

memcache ストレージをフラッシュして、Telnetを終了します。

```shell
flush_all
```

```shell
quit
```

[Telnet テストに関する追加情報](https://darkcoding.net/software/memcached-list-all-keys/)
