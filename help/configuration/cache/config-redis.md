---
title: Redisのインストールとセットアップ
description: Adobe Commerceを使用して、キャッシュとセッションストレージ用にRedisをインストールおよび設定する方法について説明します。 最適化とパフォーマンス調整のためのオプションをご紹介します。
feature: Configuration, Cache
exl-id: e037c382-334a-4096-a417-a25fdb61a9ce
source-git-commit: de613310ad701dd594a6ee8fcd973aa2c3769870
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# Redisのインストールとセットアップ

Redisは、キャッシュバックエンドおよびセッションストレージとして使用できるメモリ内データストアです。 主な機能は次のとおりです。

- PHP セッションストレージ
- `foreach` ループを使用しないタグベースのキャッシュのクリーンアップ
- ディスク上の保存とマスター/スレーブ・レプリケーション

## Redisのインストール

Redis ソフトウェアのインストールと設定は、このガイドの範囲を超えています。 次のようなリソースを参照してください。

- [Redis ページをダウンロード](https://redis.io/download)
- [Redis クイックスタート](https://redis.io/docs/latest/)
- [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-redis)
- [Redis ドキュメントページ](https://redis.io/docs)

## Redis設定の設定

インストールに応じて、Redis設定は通常、`/etc/redis/redis.conf`または`/etc/redis/<port>.conf`のいずれかのファイルで見つけることができます

要件に合わせてRedis インスタンスを最適化するには、各セッション、Commerce キャッシュ、FPCに専用のインスタンスを使用することで、最適な結果を得ることができます。

セッションの場合、Adobeでは、永続性を有効にして、通常のRedis Database Backup （RDB）スナップショットまたはAppend Only File （AOF）永続ログのいずれかを使用して、Redis データをディスクにコピーすることをお勧めします。

- **Redis Database Backup** （RDB） スナップショットは、前回の保存以降にキーの最小数が変更された場合、指定された時間が経過すると、完全なデータベースをダンプファイルに保存します。 この設定を構成するには、`redis.conf` ファイル内の`save`設定を使用します。

- **ファイルのみを追加** （AOF）は、Redisに送信された各書き込み操作をジャーナルファイルに保存します。 Redisは、このファイルを再起動時にのみ読み取り、それを使用して元のデータセットを復元します。

RDB オプションとAOF オプションの両方を同時に有効にすることもできます。 永続性オプションの利点と欠点を含む詳細については、[Redis永続性ドキュメント &#x200B;](https://redis.io/topics/persistence)を参照してください。

キャッシュインスタンスの場合は、Commerce キャッシュ全体を格納するのに十分な大きさになるようにインスタンスを設定します。 サイズの要件は、商品数やストアビューなどの要因によって異なります。 出発点として、ファイルシステム上のキャッシュフォルダーのサイズを使用できます。 例えば、ファイルシステム上の`var/cache` フォルダーが5 GBの場合は、少なくとも5 GBのRedis インスタンスを設定して開始します。 Commerce キャッシュを復元できるため、キャッシュインスタンスに永続性は必要ありません。 [Redis キャッシュガイド &#x200B;](https://redis.io/docs/latest/develop/use/)を参照してください。

パフォーマンス調整の場合は、非同期削除に対して次の設定を有効にできます。 これらの設定は、Redisの動作を変更しません。

```ini
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
```

Redis 6.x以降では、次の値を追加することもできます。

```ini
lazyfree-lazy-user-del yes
```
