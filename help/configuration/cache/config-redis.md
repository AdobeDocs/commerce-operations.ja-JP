---
title: Redis の設定
description: Redis の機能の概要を説明し、Redis 設定を開始します。
feature: Configuration, Cache
exl-id: e037c382-334a-4096-a417-a25fdb61a9ce
source-git-commit: 95ea96a566b0579a22b2ba738bd4a4bceef8cd9c
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Redis の設定

Redis の機能は次のとおりです。

- PHP セッションストレージ
- `foreach` ループを使用しないタグベースのキャッシュクリーンアップ
- ディスク上のセーブとマスター/スレーブレプリケーション

## Redis のインストール

Redis ソフトウェアのインストールと設定はこのガイドの範囲外です。 次のようなリソースを参照します。

- [Redis ページをダウンロード ](https://redis.io/download)
- [Redis クイックスタート ](https://redis.io/docs/getting-started/)
- [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-redis)
- [Redis ドキュメントページ ](https://redis.io/docs)

## Redis 設定のセットアップ

インストール環境に応じて、通常、Redis 設定は `/etc/redis/redis.conf` または `/etc/redis/<port>.conf` のいずれかのファイルで見つけることができます

要件に合わせて Redis インスタンスを最適化するには、各セッション、Commerce キャッシュ、FPC 専用のインスタンスを使用すると最良の結果が得られます。

セッションの場合、Adobeでは、通常の Redis データベースバックアップ（RDB）スナップショットまたはファイルのみを追加（AOF）永続性ログのいずれかの永続性オプションを使用して、Redis データをディスクにコピーする永続性を有効にすることをお勧めします。

- **Redis データベースバックアップ** （RDB）スナップショットは、最後の保存以降に最小数のキーが変更された場合、所定の時間後にデータベース全体をダンプファイルに保存します。 `save` ファイル内の `redis.conf` 設定を使用して、この設定を構成します。

- **ファイルのみ追加** （AOF）は、Redis に送信された各書き込み操作をジャーナルファイルに保存します。 Redis はこのファイルを再起動時にのみ読み取り、元のデータセットの復元に使用します。

また、RDB オプションと AOF オプションの両方を同時に有効にすることもできます。 永続性オプションのメリットとデメリットなど、詳しくは、[Redis 永続性ドキュメント ](https://redis.io/topics/persistence) を参照してください。

キャッシュインスタンスには、Commerce キャッシュ全体を格納するのに十分な大きさになるようにインスタンスを設定します。 サイズ要件は、商品の数やストアの表示など、様々な要因によって異なります。 出発点として、ファイルシステム上のキャッシュフォルダーのサイズを使用できます。 例えば、ファイルシステムの `var/cache` フォルダーが 5 GB の場合、起動するには少なくとも 5 GB の Redis インスタンスを設定します。 Commerce キャッシュは復元できるので、キャッシュインスタンスには永続性は必要ありません。 [Redis キャッシュガイド ](https://redis.io/docs/latest/develop/use/) を参照してください。

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
