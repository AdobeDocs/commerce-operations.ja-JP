---
title: セッションストレージに memcached を使用
description: コマースセッションストレージに memcached を使用する方法を説明します。
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---


# セッションストレージに memcached を使用

Memcached は、汎用の分散メモリキャッシュシステムです。 多くの場合、RAM 内のデータとオブジェクトをキャッシュして、動的なデータベース駆動型 Web サイトを高速化し、外部データソース（データベースや API など）を読み取る回数を減らすために使用されます。

Memcached は、複数のマシンに分散できる大きなハッシュテーブルを提供します。 テーブルがいっぱいになると、以降の挿入では、最近使用された (LRU) 順に古いデータがパージされます。 このハッシュテーブルのサイズは、多くの場合非常に大きいです。 ( 出典： [memcached.org](http://memcached.org/))

コマースは、セッションストレージに memcached を使用しますが、ページキャッシュには使用しません。 ページのキャッシュについては、 [レディス](../cache/redis-pg-cache.md) または [ワニス](../cache/config-varnish.md).

**Commerce で memcached を使用するように設定するには**:

1. 開く `<your install dir>/app/etc/env.php` をクリックします。
1. 以下を探します。

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

   memcached には、このガイドの範囲外のオプションのスタートアップパラメーターがあります。 これらに関する詳細は、 [memcached](https://php.net/manual/en/memcached.sessions.php) ドキュメント、ソースコード、および変更

1. 次の節に進みます。

**memcached が Commerce で動作することを検証するには**:

1. コマースインストールディレクトリの下にある次のディレクトリの内容を削除します。

   ```bash
   rm -rf var/cache/* var/page_cache/* var/session/*
   ```

1. ストアフロントの任意のページに移動します。

1. 管理者にログインし、複数のページを参照します。

   エラーが表示されない場合は、おめでとうございます。 memcached は動作しています！ 次の手順で説明するように、オプションで memcached ストレージを確認できます。

   エラー (HTTP 500（内部サーバーエラー）など ) が表示される場合は、開発者モードを有効にし、問題を診断します。 memcached が実行され、正しく設定されていること、および `env.php` に構文エラーはありません。

1. （オプション） Telnet を使用して、memcached ストレージを確認します。

   ```bash
   telnet <memcached host or ip> <memcached port>
   ```

   ```bash
   stats items
   ```

   結果は次のように表示されます。

   ```terminal
   STAT items:3:number 1
   STAT items:3:age 7714
   STAT items:3:evicted 0
   STAT items:3:evicted_nonzero 0
   STAT items:3:evicted_time 0
   STAT items:3:outofmemory 0
   STAT items:3:tailrepairs 0
   
   [Look at the keys in more detail](http://www.darkcoding.net/software/memcached-list-all-keys/)
   ```
