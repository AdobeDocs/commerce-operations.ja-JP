---
title: セッション ストレージにmemcachedを使用
description: env.phpのセッションストレージにmemcachedを使用するようにAdobe Commerceを設定する方法と、他のキャッシュレイヤーにRedisまたはVarnishを優先する場合について説明します。
feature: Configuration, Cache, Storage
exl-id: 24077929-e732-4579-8d7d-717a4902fc64
source-git-commit: 41b8d77793f1c24f08ff7e6a2d35826a62477534
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# セッション ストレージにmemcachedを使用

Memcachedは、汎用の分散型メモリキャッシングシステムです。 多くの場合、RAMにデータとオブジェクトをキャッシュすることで、外部データソース（データベースやAPIなど）を読み取る必要がある回数を減らし、動的なデータベース駆動型のweb サイトを高速化するために使用されます。

Memcachedは、複数のマシンに分散できる大規模なハッシュテーブルを提供します。 テーブルがいっぱいになると、後続の挿入によって、古いデータが最も最近使用されていない（LRU）順序で消去されます。 このハッシュテーブルのサイズは非常に大きいことがよくあります。 （Source: [memcached.org](https://www.memcached.org/)）

Commerceでは、セッションの保存にmemcachedを使用しますが、ページキャッシュには使用しません。 ページキャッシュについては、[Redis](../cache/redis-pg-cache.md)または[Varnish](../cache/config-varnish.md)をお勧めします。

**Commerceでmemcached**&#x200B;を使用するように設定するには：

1. `<your install dir>/app/etc/env.php`をテキストエディターで開きます。
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

   memcachedには、このガイドの範囲を超えるオプションの起動パラメーターがあります。 詳細については、[memcached](https://www.php.net/manual/en/memcached.sessions.php) ドキュメント、ソースコード、および変更履歴を参照してください。

1. 次のセクションに進みます。

**MemcachedがCommerceで動作することを確認するには**:

1. Commerce インストールディレクトリの下にある次のディレクトリの内容を削除します。

   ```shell
   rm -rf var/cache/* var/page_cache/* var/session/*
   ```

1. ストアフロントの任意のページに移動します。

1. 管理者にログインし、複数のページを参照します。

   エラーが表示されない場合は、おめでとうございます。 memcachedが動作しています。 オプションとして、次の手順で説明するように、memcached ストレージを調べることができます。

   エラーが表示された場合（HTTP 500 （内部サーバーエラー）は、開発者モードを有効にして問題を診断します。 memcachedが実行され、適切に設定され、`env.php`に構文エラーがないことを確認してください。

1. （オプション） Telnetを使用してmemcached ストレージを調べます。

   ```shell
   telnet <memcached host or ip> <memcached port>
   ```

   ```shell
   stats items
   ```

   結果は次のように表示されます。

   ```text
   STAT items:3:number 1
   STAT items:3:age 7714
   STAT items:3:evicted 0
   STAT items:3:evicted_nonzero 0
   STAT items:3:evicted_time 0
   STAT items:3:outofmemory 0
   STAT items:3:tailrepairs 0
   
   [Look at the keys in more detail](https://darkcoding.net/software/memcached-list-all-keys/)
   ```
