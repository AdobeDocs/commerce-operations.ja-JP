---
title: Redis を設定
description: Redis の機能の概要を把握し、Redis の設定を開始します。
source-git-commit: 5c0d285717a79d654af769cb734ec385d2d4046f
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# Redis を設定

Redis の機能には次のものが含まれます。

- PHP セッションストレージ
- タグベースのキャッシュクリーンアップ ( `foreach` ループ
- ディスク上での保存とマスター/スレーブ・レプリケーション

## Redis をインストール

Redis ソフトウェアのインストールと設定は、このガイドの範囲外です。 次のようなリソースを参照してください。

- [Redis ページをダウンロード](https://redis.io/download)
- [Redis クイックスタート](https://redis.io/docs/getting-started/)
- [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-redis)
- [Redis ドキュメントページ](https://redis.io/docs)

## Redis 設定のセットアップ

インストールに応じて、通常、Redis の設定は次のファイルのいずれかで確認できます。 `/etc/redis/redis.conf` または `/etc/redis/<port>.conf`

Redis インスタンスを要件に合わせて最適化するには、各セッション用の専用インスタンス、Commerce キャッシュ、FPC を使用して最適な結果を得ます。

セッションの場合、Adobeでは、次の永続性オプションのいずれかを使用して、永続性を有効にして Redis データをディスクにコピーすることをお勧めします。通常の Redis Database Backup(RDB) スナップショット、または Append Only File(AOF) 永続性ログ。

- **Redis データベースのバックアップ** (RDB) スナップショットは、最後の保存以降に最小数のキーが変更された場合、ダンプファイルに完全なデータベースを保存します。 以下を使用： `save` 設定を `redis.conf` ファイルを参照してください。

- **追加専用ファイル** (AOF)Redis に送信された各書き込み操作をジャーナルファイルに保存します。 Redis は、再起動時にのみこのファイルを読み取り、元のデータセットを復元するために使用します。

また、RDB と AOF の両方のオプションを同時に有効にすることもできます。 永続性オプションのメリットとデメリットなど、その他の詳細については、 [Redis の永続性に関するドキュメント](https://redis.io/topics/persistence).

キャッシュインスタンスの場合は、コマースキャッシュ全体を保存するのに十分な大きさになるようにインスタンスを設定します。 サイズの要件は、製品数や店舗表示数など、様々な要因によって異なります。 開始点として、ファイルシステム上のキャッシュフォルダーのサイズを使用できます。 例えば、 `var/cache` ファイルシステム上のフォルダーは 5 GB です。少なくとも 5 GB の Redis インスタンスを設定して起動します。 コマースキャッシュを復元できるので、キャッシュインスタンスに永続性は必要ありません。 詳しくは、 [Redis キャッシュガイド](https://redis.io/docs/manual/eviction/).

パフォーマンスチューニングの場合、非同期削除に対して次の設定を有効にすることもできます。 これらの設定は、Redis の動作を変更しません。 関連トピック [レディアスニュース](http://antirez.com/news/93) ：非同期削除の詳細を参照してください。

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
