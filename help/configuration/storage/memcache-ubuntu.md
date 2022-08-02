---
title: Ubuntu で memcached を設定する
description: Ubuntu に memcached をインストールして設定します。
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---


# Ubuntu で memcached を設定する

この節では、Ubuntu に memcached をインストールする手順を説明します。

>[!INFO]
>
>Adobeでは、memcached バージョン 3.0.5 以降を使用することをお勧めします。

PHP は memcache をネイティブでサポートしていないので、PHP で使用するには拡張をインストールする必要があります。 PHP には 2 つの拡張機能があり、どの拡張機能を使用するかをデコードすることが重要です。

- `memcache` (_no d_) — 定期的に維持されない、古いが一般的な拡張機能。
この `memcache` 現在、拡張機能 _次の値と等しくない_ は PHP 7 で動作します。 詳しくは、 [memcache の PHP ドキュメント](https://www.php.net/manual/en/book.memcache.php).

   正確な名前は `php5-memcache` Ubuntu に対して。

- `memcached` (_と`d`_)—PHP 7 と互換性のある、より新しく、維持された拡張。 詳しくは、 [memcached に関する PHP ドキュメント](https://www.php.net/manual/en/book.memcached.php).

   正確な名前は `php5-memcached` Ubuntu に対して。

## Ubuntu で memcached をインストールして設定します。

**Ubuntu に memcached をインストールして設定するには**:

1. を使用して `root` 権限を設定するには、次のコマンドを入力します。

   ```bash
   apt-get -y update
   ```

   ```bash
   apt-get -y install php5-memcached memcached
   ```

1. 次の memcached 構成設定を変更します。 `CACHESIZE` および `-l`:

   1. 開く `/etc/memcached.conf` をクリックします。
   1. を `-m` パラメーター。
   1. 値を少なくともに変更します。 `1GB`
   1. を `-l` パラメーター。
   1. 値をに変更します。 `127.0.0.1` または `localhost`
   1. 変更をに保存します。 `memcached.conf` をクリックし、テキストエディタを終了します。
   1. memcached を再起動します。

      ```bash
      service memcached restart
      ```

1. Web サーバーを再起動します。

   Apache の場合、 `service apache2 restart`

1. 次の節に進みます。

## memcached の動作を確認してからMagento

Adobeでは、Commerce をインストールする前に、memcached が機能することを確認することをお勧めします。 これをおこなうのに数分かかり、後で簡単にトラブルシューティングできます。

### Web サーバーが memcached を認識したことを確認します

memcached が Web サーバーによって認識されることを確認するには、次の手順を実行します。

1. の作成 `phpinfo.php` ファイルを web サーバーの docroot に配置します。

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. Web ブラウザーでそのページに移動します。 例：

   ```http
   http://192.0.2.1/phpinfo.php
   ```

1. memcached が次のように表示されることを確認します。

   ![memcached が Web サーバーによって認識されたことを確認](../../assets/configuration/memcache.png)

   memcached バージョン 3.0.5 以降を使用していることを確認します。

   memcached が表示されない場合は、Web サーバーを再起動し、ブラウザーページを更新します。 それでも表示されない場合は、 `php-pecl-memcached` 拡張子。

### memcached がデータをキャッシュできることを確認します

このテストでは、PHP スクリプトを使用して、memcached が [キャッシュ](https://glossary.magento.com/cache) データ。

このテストの詳細については、 [Ubuntu での Memcache のインストールと使用の方法のチュートリアル](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-14-04).

作成 `cache-test.php` を次の内容で、web サーバーの docroot に追加します。

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

ここで、 `<memcached hostname or ip>` 次のいずれか `localhost`, `127.0.0.1`または memcache のホスト名または IP アドレス。 この `<memcached port>` はリッスンポートです。デフォルトでは `11211`.

Web ブラウザーでそのページに移動します。 例：

```http
http://192.0.2.1/cache-test.php
```

初めてこのページに移動すると、次のように表示されます。 `No matching key found. Refresh the browser to add it!`

ブラウザーを更新します。 メッセージが `Successfully retrieved the data!`

最後に、Telnet を使用して memcache キーを表示できます。

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

[Telnet テストの追加情報](https://darkcoding.net/software/memcached-list-all-keys/)
