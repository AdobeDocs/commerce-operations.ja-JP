---
title: CentOS での memcached の設定
description: CentOS に memcached をインストールして設定します。
feature: Configuration, Cache, Storage
exl-id: fc4ad18b-7e99-496e-aebc-1d7640d8716c
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 0%

---

# CentOS での memcached の設定

この節では、CentOS に memcached をインストールする手順を示します。 詳しくは、を参照してください [memcached wiki](https://github.com/memcached/old-wiki).

>[!INFO]
>
>Adobeでは、最新の安定した memcached バージョン（memcached の場合は現在 3.1.3）を使用することをお勧めします。

PHP は memcache をネイティブでサポートしていないので、それを使用するには PHP 用の拡張モジュールをインストールする必要があります。 PHP には 2 つの拡張モジュールがあり、どちらを使用するかをデコードすることが重要です。

- `memcache` （_いいえ d_） – 定期的にメンテナンスされていない、古いが一般的な拡張機能。
この `memcache` 現在の拡張機能 _次を含まない_ php 7 で動作します。 参照： [memcache に関する PHP ドキュメント](https://www.php.net/manual/en/book.memcache.php).

  正確な名前は、 `php-pecl-memcache` CentOS の場合。

- `memcached` （_（を使用）`d`_） – PHP 7 と互換性のある、新しくメンテナンスされた拡張モジュールです。 参照： [memcached の PHP ドキュメント](https://www.php.net/manual/en/book.memcached.php).

  正確な名前は、 `php-pecl-memcached` CentOS の場合。

## CentOS での memcached のインストールと設定

CentOS 上で memcached をインストールするには、次のタスクをユーザーとして実行します。 `root` 権限：

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
   >上記のコマンドの構文は、使用するパッケージリポジトリによって異なる場合があります。 例えば、webtatic と PHP 5.6 を使用する場合、 `yum install -y php56w-pecl-memcache`. 使用方法 `yum search memcache|grep php` をクリックして、適切なパッケージ名を検索します。


1. の memcached 設定の変更 `CACHESIZE` および `OPTIONS`:

   1. 開く `/etc/sysconfig/memcached` テキストエディター。
   1. の値を見つけます。 `CACHESIZE` そして、それを少なくとも 1 GB に変更します。 例：

      ```config
      CACHESIZE="1GB"
      ```

   1. の値を見つけます。 `OPTIONS` に変更します。 `localhost` または `127.0.0.1`

1. 変更をに保存します。 `memcached` をクリックして、テキストエディターを終了します。
1. memcached を再起動します。

   ```bash
   service memcached restart
   ```

1. Web サーバーを再起動します。

   Apache の場合

   ```bash
   service httpd restart
   ```

1. 次の節に進みます。

## Commerceをインストールする前に、memcached が機能することを確認

Adobeでは、Commerceをインストールする前に、memcached をテストして機能することを確認することをお勧めします。 この操作には数分しかかかりません。また、後でトラブルシューティングを簡略化することもできます。

### memcached が Web サーバで認識されることを確認します。

memcached が Web サーバで認識されることを確認するには、次の手順に従います。

1. を作成 `phpinfo.php` web サーバーの docroot にあるファイル：

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. Web ブラウザーでそのページに移動します。

   例：`http://192.0.2.1/phpinfo.php`

1. memcache が次のように表示されていることを確認します。

![Web サーバーが memcache を認識していることを確認](../../assets/configuration/memcache.png)

memcached バージョン 3.0.5 以降を使用していることを確認します。

memcache が表示されない場合は、web サーバーを再起動してブラウザーページを更新します。 それでも表示されない場合は、をインストールしたことを確認します `php-pecl-memcache` 拡張機能。

### MySQL データベースと PHP スクリプトで構成される memcache テストを作成します。

このテストでは、MySQL データベース、テーブル、およびデータを使用して、データベースデータを取得して memcache に保存できることを確認します。 PHP スクリプトはまずキャッシュを検索します。 結果が存在しない場合、スクリプトはデータベースにクエリを実行します。 クエリが元のデータベースで実行された後、スクリプトは次を使用して結果を memcache に保存します `set` コマンド。

[このテストの詳細](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-12-04)

MySQL データベースを作成します。

```bash
mysql -u root -p
```

時刻 `mysql` プロンプトで、次のコマンドを入力します。

```sql
create database memcache_test;
GRANT ALL ON memcache_test.* TO memcache_test@localhost IDENTIFIED BY 'memcache_test';
use memcache_test;
create table example (id int, name varchar(30));
insert into example values (1, "new_data");
exit
```

作成 `cache-test.php` web サーバーの docroot で、次の操作を行います。

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

ここで、 `<memcached hostname or ip>` 次のいずれか `localhost`, `127.0.0.1`、または memcache ホスト名もしくは IP アドレス。 この `<memcached port>` はリッスンポートです（デフォルトでは、 `11211`.

コマンドラインからスクリプトを実行します。

```bash
cd <web server docroot>
```

```bash
php cache-test.php
```

最初の結果は次のとおりです。 `got result from mysql`. つまり、キーは memcached には存在しませんが、MySQL から取得されたものです。

2 つ目の結果は次のとおりです `got result from memcached`：値が memcached に正常に格納されていることを確認します。

最後に、Telnet を使用して memcache キーを確認できます。

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

[Telnet テストに関する追加情報](https://darkcoding.net/software/memcached-list-all-keys/)
