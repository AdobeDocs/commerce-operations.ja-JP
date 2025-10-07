---
title: Ubuntu での memcached の設定
description: Adobe Commerceのキャッシュ用に Ubuntu に memcached をインストールして設定する方法を説明します。 設定手順と最適化のヒントを確認します。
feature: Configuration, Cache, Storage
exl-id: 831193d2-3e81-472c-9b87-78a8d52959b4
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# Ubuntu での memcached の設定

このセクションでは、Ubuntu に memcached をインストールする手順を説明します。

>[!INFO]
>
>Adobeでは、memcached バージョン 3.0.5 以降を使用することをお勧めします。

PHP は memcache をネイティブでサポートしていないので、それを使用するには PHP 用の拡張モジュールをインストールする必要があります。 PHP には 2 つの拡張モジュールがあり、どちらを使用するかをデコードすることが重要です。

- `memcache` （_no d_） – 定期的にメンテナンスされていない、古いが一般的な拡張機能。
`memcache` 拡張モジュールは現在 PHP 7 で動作します _動作しません_。 [memcache に関する PHP のドキュメント ](https://www.php.net/manual/en/book.memcache.php) を参照してください。

  Ubuntu の正確な名前は `php5-memcache` です。

- `memcached` （_と`d`_） – PHP 7 と互換性のある、新しくメンテナンスされた拡張機能です。 [memcached に関する PHP のドキュメント ](https://www.php.net/manual/en/book.memcached.php) を参照してください。

  Ubuntu の正確な名前は `php5-memcached` です。

## Ubuntu での memcached のインストールと設定

**Ubuntu に memcached をインストールして設定するには**:

1. `root` 権限を持つユーザーとして、次のコマンドを入力します。

   ```bash
   apt-get -y update
   ```

   ```bash
   apt-get -y install php5-memcached memcached
   ```

1. `CACHESIZE` および `-l` の memcached 設定を変更します。

   1. `/etc/memcached.conf` をテキストエディターで開きます。
   1. `-m` パラメーターを見つけます。
   1. その値を少なくとも `1GB` に変更します
   1. `-l` パラメーターを見つけます。
   1. 値を `127.0.0.1` または `localhost` に変更します
   1. `memcached.conf` への変更を保存し、テキストエディターを終了します。
   1. memcached を再起動します。

      ```bash
      service memcached restart
      ```

1. Web サーバーを再起動します。

   Apache の場合、`service apache2 restart`

1. 次の節に進みます。

## Magentoをインストールする前に、memcached が機能することを確認

Adobeでは、Commerceをインストールする前に、memcached が機能することをテストすることをお勧めします。 この操作には数分しかかかりません。また、後でトラブルシューティングを簡略化することもできます。

### memcached が Web サーバで認識されることを確認します。

memcached が Web サーバで認識されることを確認するには、次の手順に従います。

1. Web サーバーの docroot に `phpinfo.php` ファイルを作成します。

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

   ![Web サーバーで memcached が認識されていることを確認する ](../../assets/configuration/memcache.png)

   memcached バージョン 3.0.5 以降を使用していることを確認します。

   memcached が表示されない場合は、web サーバーを再起動してブラウザーページを更新します。 それでも表示されない場合は、`php-pecl-memcached` 拡張機能をインストールしたことを確認します。

### memcached がデータをキャッシュできることを検証

このテストでは、PHP スクリプトを使用して、memcached がキャッシュデータを格納および取得できることを検証します。

このテストについて詳しくは、[Ubuntu で Memcache をインストールして使用する方法 ](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-14-04) チュートリアルを参照してください。

Web サーバーの docroot に、次の内容の `cache-test.php` を作成します。

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

ここで、`<memcached hostname or ip>` は `localhost`、`127.0.0.1`、memcache ホスト名または IP アドレスのいずれかです。 `<memcached port>` はリッスンポートです（デフォルトは `11211`）。

Web ブラウザーでそのページに移動します。 例：

```http
http://192.0.2.1/cache-test.php
```

ページに初めて移動すると、次の内容が表示されます。`No matching key found. Refresh the browser to add it!`

ブラウザーを更新します。 メッセージが「`Successfully retrieved the data!`」に変わります

最後に、Telnet を使用して memcache キーを確認できます。

```bash
telnet localhost <memcache port>
```

プロンプトに対して、と入力します。

```shell
stats items
```

結果は次のようになります。

```
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

[Telnet テストに関する追加情報 ](https://darkcoding.net/software/memcached-list-all-keys/)
