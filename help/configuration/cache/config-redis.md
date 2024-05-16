---
title: Redis の設定
description: Redis の機能の概要を説明し、Redis 設定を開始します。
feature: Configuration, Cache
exl-id: e037c382-334a-4096-a417-a25fdb61a9ce
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Redis の設定

Redis の機能は次のとおりです。

- PHP セッションストレージ
- を使用しないタグベースのキャッシュクリーンアップ `foreach` ループ
- ディスク上のセーブとマスター/スレーブレプリケーション

## Redis のインストール

Redis ソフトウェアのインストールと設定はこのガイドの範囲外です。 次のようなリソースを参照します。

- [Redis ページのダウンロード](https://redis.io/download)
- [Redis クイックスタート](https://redis.io/docs/getting-started/)
- [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-redis)
- [Redis ドキュメントページ](https://redis.io/docs)

## Redis 設定のセットアップ

インストール環境に応じて、通常、Redis 設定は次のいずれかのファイルで見つけることができます。 `/etc/redis/redis.conf` または `/etc/redis/<port>.conf`

要件に合わせて Redis インスタンスを最適化するには、各セッション、Commerce キャッシュ、FPC 専用のインスタンスを使用すると最良の結果が得られます。

Adobe セッションの場合、通常の Redis データベースバックアップ（RDB）スナップショットまたはファイルのみを追加（AOF）永続性ログのいずれかの永続性オプションを使用して、Redis データをディスクにコピーする永続性を有効にすることをお勧めします。

- **Redis データベース バックアップ** （RDB）スナップショットは、最後の保存以降に最小数のキーが変更された場合、指定された時間の後にデータベース全体をダンプファイルに保存します。 の使用 `save` 内での設定 `redis.conf` この設定を構成するファイルです。

- **ファイルのみを追加** （AOF）は、Redis に送信された各書き込み操作をジャーナルファイルに保存します。 Redis はこのファイルを再起動時にのみ読み取り、元のデータセットの復元に使用します。

また、RDB オプションと AOF オプションの両方を同時に有効にすることもできます。 永続性オプションの長所と短所など、追加の詳細については、を参照してください。 [Redis 永続性ドキュメント](https://redis.io/topics/persistence).

キャッシュインスタンスには、Commerce キャッシュ全体を格納するのに十分な大きさになるようにインスタンスを設定します。 サイズ要件は、商品の数やストアの表示など、様々な要因によって異なります。 出発点として、ファイルシステム上のキャッシュフォルダーのサイズを使用できます。 例えば、 `var/cache` お使いのファイルシステムのフォルダーは 5 GB です。開始するには少なくとも 5 GB で Redis インスタンスを設定します。 Commerce キャッシュは復元できるので、キャッシュインスタンスには永続性は必要ありません。 参照： [Redis キャッシュガイド](https://redis.io/docs/manual/eviction/).

パフォーマンスを調整する場合は、非同期削除について次の設定を有効にできます。 これらの設定は、Redis の動作を変更しません。

```ini
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
```

Redis 6.x 以降では、次の値も追加できます。

```ini
lazyfree-lazy-user-del yes
```
