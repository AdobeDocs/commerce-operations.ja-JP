---
title: CentOS での memcached の設定
description: Adobe Commerceのキャッシュ用に CentOS に memcached をインストールして設定する方法を説明します。 設定手順と最適化のヒントを確認します。
feature: Configuration, Cache, Storage
exl-id: fc4ad18b-7e99-496e-aebc-1d7640d8716c
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 0%

---

# CentOS での memcached の設定

この節では、CentOS に memcached をインストールする手順を示します。 詳細については、[memcached wiki](https://github.com/memcached/old-wiki) を参照してください。

>[!INFO]
>
>Adobeでは、最新の安定した memcached バージョン（memcached の場合は現在 3.1.3）を使用することをお勧めします。

PHP は memcache をネイティブでサポートしていないので、それを使用するには PHP 用の拡張モジュールをインストールする必要があります。 PHP には 2 つの拡張モジュールがあり、どちらを使用するかをデコードすることが重要です。

- `memcache` （_no d_） – 定期的にメンテナンスされていない、古いが一般的な拡張機能。
`memcache` 拡張モジュールは現在 PHP 7 で動作します _動作しません_。 [memcache に関する PHP のドキュメント &#x200B;](https://www.php.net/manual/en/book.memcache.php) を参照してください。

  CentOS の正確な名前は `php-pecl-memcache` です。

- `memcached` （_と`d`_） – PHP 7 と互換性のある、新しくメンテナンスされた拡張機能です。 [memcached に関する PHP のドキュメント &#x200B;](https://www.php.net/manual/en/book.memcached.php) を参照してください。

  CentOS の正確な名前は `php-pecl-memcached` です。

## CentOS での memcached のインストールと設定

CentOS に memcached をインストールするには、`root` 権限を持つユーザーとして次のタスクを実行します。

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
   >上記のコマンドの構文は、使用するパッケージリポジトリによって異なる場合があります。 例えば、webtatic と PHP 5.6 を使用する場合、`yum install -y php56w-pecl-memcache` と入力します。 `yum search memcache|grep php` を使用して、適切なパッケージ名を見つけます。


1. `CACHESIZE` および `OPTIONS` の memcached 設定を変更します。

   1. `/etc/sysconfig/memcached` をテキストエディターで開きます。
   1. `CACHESIZE` の値を見つけて、1 GB 以上に変更します。 例：

      ```config
      CACHESIZE="1GB"
      ```

   1. `OPTIONS` の値を見つけて、`localhost` または `127.0.0.1` に変更します

1. `memcached` への変更を保存し、テキストエディターを終了します。
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

Adobeでは、Commerceをインストールする前に、memcached が機能することをテストすることをお勧めします。 この操作には数分しかかかりません。また、後でトラブルシューティングを簡略化することもできます。

### memcached が Web サーバで認識されることを確認します。

memcached が Web サーバで認識されることを確認するには、次の手順に従います。

1. Web サーバーの docroot に `phpinfo.php` ファイルを作成します。

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. Web ブラウザーでそのページに移動します。

   例：`http://192.0.2.1/phpinfo.php`

1. memcache が次のように表示されていることを確認します。

![Web サーバーが memcache を認識していることを確認します &#x200B;](../../assets/configuration/memcache.png)

memcached バージョン 3.0.5 以降を使用していることを確認します。

memcache が表示されない場合は、web サーバーを再起動してブラウザーページを更新します。 それでも表示されない場合は、`php-pecl-memcache` 拡張機能をインストールしたことを確認します。

### MySQL データベースと PHP スクリプトで構成される memcache テストを作成します。

このテストでは、MySQL データベース、テーブル、およびデータを使用して、データベースデータを取得して memcache に保存できることを確認します。 PHP スクリプトはまずキャッシュを検索します。 結果が存在しない場合、スクリプトはデータベースにクエリを実行します。 クエリが元のデータベースで実行された後、スクリプトは `set` コマンドを使用して結果を memcache に保存します。

[&#x200B; このテストの詳細 &#x200B;](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-12-04)

MySQL データベースを作成します。

```bash
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

Web サーバーの docroot に `cache-test.php` を作成します。

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

ここで、`<memcached hostname or ip>` は `localhost`、`127.0.0.1`、memcache ホスト名または IP アドレスのいずれかです。 `<memcached port>` はリッスンポートです（デフォルトは `11211`）。

コマンドラインからスクリプトを実行します。

```bash
cd <web server docroot>
```

```bash
php cache-test.php
```

最初の結果は `got result from mysql` です。 つまり、キーは memcached には存在しませんが、MySQL から取得されたものです。

2 つ目の結果は `got result from memcached` で、値が memcached に正常に格納されていることを確認します。

最後に、Telnet を使用して memcache キーを確認できます。

```bash
telnet localhost <memcache port>
```

プロンプトに対して、と入力します。

```bash
stats items
```

結果は次のようになります。

```
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

[Telnet テストに関する追加情報 &#x200B;](https://darkcoding.net/software/memcached-list-all-keys/)
