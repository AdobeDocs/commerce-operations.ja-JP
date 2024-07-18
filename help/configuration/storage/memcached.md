---
title: セッションストレージに memcached を使用
description: Commerce セッションストレージに memcached を使用する方法について説明します。
feature: Configuration, Cache, Storage
exl-id: 24077929-e732-4579-8d7d-717a4902fc64
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# セッションストレージに memcached を使用

Memcached は、汎用の分散メモリキャッシュシステムです。 多くの場合、外部データソース（データベースや API など）の読み取り回数を減らすために、データやオブジェクトを RAM にキャッシュして、動的なデータベース駆動 web サイトを高速化するために使用されます。

Memcached は、複数のマシンに分散できる大きなハッシュテーブルを提供します。 テーブルがいっぱいになると、後続の挿入により、古いデータが LRU （Least Recently Used）の順序でパージされます。 このハッシュテーブルのサイズは、多くの場合、非常に大きくなります。 （Source: [memcached.org](https://www.memcached.org/)）

Commerceでは、セッションストレージには memcached を使用しますが、ページキャッシュには使用しません。 ページキャッシュの場合は、[Redis](../cache/redis-pg-cache.md) または [Varnish](../cache/config-varnish.md) をお勧めします。

**memcached を使用するようにCommerceを設定するには**:

1. `<your install dir>/app/etc/env.php` をテキストエディターで開きます。
1. 次の場所を探します。

   ```php
   'session' =>
       array (
       'save' => 'files',
   ),
   ```

1. 次のように変更します。

   ```php
   'session' =>
       array (
         'save' => 'memcached',
         'save_path' => '<memcache ip or host>:<memcache port>'
   ),
   ```

   memcached には、このガイドの範囲外のオプションの起動パラメーターがあります。 詳細については、[memcached](https://www.php.net/manual/en/memcached.sessions.php) のドキュメント、ソースコード、changelogs を参照してください。

1. 次の節に進みます。

**memcached がCommerceで動作することを確認するには**:

1. Commerce インストールディレクトリの下にある次のディレクトリの内容を削除します。

   ```bash
   rm -rf var/cache/* var/page_cache/* var/session/*
   ```

1. ストアフロントのページに移動します。

1. 管理者にログインし、複数のページを参照します。

   エラーが表示されない場合は、ここで完了です。 memcached は動作しています。 オプションで、次の手順で説明する memcached ストレージを参照できます。

   エラー（HTTP 500 （内部サーバーエラー）など）が表示された場合は、開発者モードを有効にして問題を診断します。 memcached が実行中で、適切に設定されており、構文エラーが `env.php` いことを確認します。

1. （オプション。） Telnet を使用して、memcached ストレージを調べます。

   ```bash
   telnet <memcached host or ip> <memcached port>
   ```

   ```bash
   stats items
   ```

   結果は次のように表示されます。

   ```
   STAT items:3:number 1
   STAT items:3:age 7714
   STAT items:3:evicted 0
   STAT items:3:evicted_nonzero 0
   STAT items:3:evicted_time 0
   STAT items:3:outofmemory 0
   STAT items:3:tailrepairs 0
   
   [Look at the keys in more detail](https://darkcoding.net/software/memcached-list-all-keys/)
   ```
