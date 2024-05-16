---
title: Ubuntu での memcached の設定
description: Ubuntu に memcached をインストールして設定します。
feature: Configuration, Cache, Storage
exl-id: 831193d2-3e81-472c-9b87-78a8d52959b4
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# Ubuntu での memcached の設定

このセクションでは、Ubuntu に memcached をインストールする手順を説明します。

>[!INFO]
>
>Adobeでは、memcached バージョン 3.0.5 以降を使用することをお勧めします。

PHP は memcache をネイティブでサポートしていないので、それを使用するには PHP 用の拡張モジュールをインストールする必要があります。 PHP には 2 つの拡張モジュールがあり、どちらを使用するかをデコードすることが重要です。

- `memcache` （_いいえ d_） – 定期的にメンテナンスされていない、古いが一般的な拡張機能。
この `memcache` 現在の拡張機能 _次を含まない_ php 7 で動作します。 参照： [memcache に関する PHP ドキュメント](https://www.php.net/manual/en/book.memcache.php).

  正確な名前は、 `php5-memcache` Ubuntu の場合。

- `memcached` （_（を使用）`d`_） – PHP 7 と互換性のある、新しくメンテナンスされた拡張モジュールです。 参照： [memcached の PHP ドキュメント](https://www.php.net/manual/en/book.memcached.php).

  正確な名前は、 `php5-memcached` Ubuntu の場合。

## Ubuntu での memcached のインストールと設定

**Ubuntu に memcached をインストールして設定するには**:

1. を使用した As a ユーザー `root` privileges。次のコマンドを入力します。

   ```bash
   apt-get -y update
   ```

   ```bash
   apt-get -y install php5-memcached memcached
   ```

1. の memcached 設定の変更 `CACHESIZE` および `-l`:

   1. 開く `/etc/memcached.conf` テキストエディター。
   1. を見つけます。 `-m` パラメーター。
   1. その値を「少なくとも」に変更します `1GB`
   1. を見つけます。 `-l` パラメーター。
   1. 値をに変更します `127.0.0.1` または `localhost`
   1. 変更をに保存します。 `memcached.conf` をクリックして、テキストエディターを終了します。
   1. memcached を再起動します。

      ```bash
      service memcached restart
      ```

1. Web サーバーを再起動します。

   Apache の場合、 `service apache2 restart`

1. 次の節に進みます。

## Magentoをインストールする前に memcached が動作することを確認します。

Adobeでは、Commerceをインストールする前に、memcached をテストして機能することを確認することをお勧めします。 この操作には数分しかかかりません。また、後でトラブルシューティングを簡略化することもできます。

### memcached が Web サーバで認識されることを確認します。

memcached が Web サーバで認識されることを確認するには、次の手順に従います。

1. を作成 `phpinfo.php` web サーバーの docroot にあるファイル：

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. Web ブラウザーでそのページに移動します。 例：

   ```http
   http://192.0.2.1/phpinfo.php
   ```

1. memcached が次のように表示されていることを確認します。

   ![Memcached が Web サーバーで認識されることを確認します。](../../assets/configuration/memcache.png)

   memcached バージョン 3.0.5 以降を使用していることを確認します。

   memcached が表示されない場合は、web サーバーを再起動してブラウザーページを更新します。 それでも表示されない場合は、をインストールしたことを確認します `php-pecl-memcached` 拡張機能。

### memcached がデータをキャッシュできることを検証

このテストでは、PHP スクリプトを使用して、memcached がキャッシュデータを格納および取得できることを検証します。

このテストについて詳しくは、 [Ubuntu で Memcache をインストールして使用する方法チュートリアル](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-14-04).

作成 `cache-test.php` web サーバーの docroot に次の内容を入力します。

```php
$meminstance = new Memcached();

$meminstance->addServer("<memcached hostname or ip>", <memcached port>);

$result = $meminstance->get("test");

if ($result) {
    echo $result;
} else {
    echo "No matching key found. Refresh the browser to add it!";
    $meminstance->set("test", "Successfully retrieved the data!") or die("Could not save anything to memcached...");
}
```

ここで、 `<memcached hostname or ip>` 次のいずれか `localhost`, `127.0.0.1`、または memcache ホスト名もしくは IP アドレス。 この `<memcached port>` はリッスンポートです（デフォルトでは、 `11211`.

Web ブラウザーでそのページに移動します。 例：

```http
http://192.0.2.1/cache-test.php
```

ページに初めて移動すると、次の情報が表示されます。 `No matching key found. Refresh the browser to add it!`

ブラウザーを更新します。 メッセージが次のように変更されます。 `Successfully retrieved the data!`

最後に、Telnet を使用して memcache キーを確認できます。

```bash
telnet localhost <memcache port>
```

プロンプトに対して、と入力します。

```shell
stats items
```

結果は次のようになります。

```terminal
STAT items:2:number 1
STAT items:2:age 106
STAT items:2:evicted 0
STAT items:2:evicted_nonzero 0
STAT items:2:evicted_time 0
STAT items:2:outofmemory 0
STAT items:2:tailrepairs 0
STAT items:2:reclaimed 0
STAT items:2:expired_unfetched 0
STAT items:2:evicted_unfetched 0
```

memcached ストレージをフラッシュし、Telnet を終了します。

```shell
flush_all
```

```shell
quit
```

[Telnet テストに関する追加情報](https://darkcoding.net/software/memcached-list-all-keys/)
