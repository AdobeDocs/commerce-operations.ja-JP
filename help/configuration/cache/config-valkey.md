---
title: Valkey の設定
description: Valkey の機能の概要を説明し、Valkey の設定を開始します。
feature: Configuration, Cache
exl-id: 12dbc171-3df6-4413-869b-a3450b5647b4
source-git-commit: b2cf71bfda3e5db8e27eb28d764cf99216454e33
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# Valkey の設定

主な機能は次のとおりです。

- PHP セッションストレージ
- `foreach` ループを使用しないタグベースのキャッシュクリーンアップ
- ディスク上のセーブとマスター/スレーブレプリケーション

## Valkey のインストール

Valkey ソフトウェアをインストールして設定するには、次のリソースを参照してください。

- [Valkey ページをダウンロード ](https://valkey.io/download/)
- [Valkey クイックスタート ](https://valkey.io/topics/quickstart/)
- [Valkey ドキュメントページ ](https://valkey.io/docs)

## Valkey 設定のセットアップ

インストール環境によっては、通常 `/etc/valkey/valkey.conf` ファイルまたは `/etc/valkey/<port>.conf` ファイルで Valkey 設定を見つけることができます。

要件に合わせて Valkey インスタンスを最適化するには、各セッション、Commerce キャッシュ、FPC に専用のインスタンスを使用することで、最良の結果を得ることができます。

Adobeでは、セッションの永続性を有効にして、有効なデータをディスクにコピーすることをお勧めします。 有効なデータベースバックアップ（RDB）スナップショットまたはファイルのみ追加（AOF）永続性ログを使用できます。

- **RDB** （Valkey Database）スナップショットは、最後の保存以降に最小数のキーが変更された場合、所定の時間後にデータベース全体をダンプファイルに保存します。 `save` ファイル内の `valkey.conf` 設定を使用して、この設定を構成します。

- **ファイルのみ追加** （AOF）は、Valkey に送信された各書き込み操作をジャーナルファイルに保存します。 Valkey は、再起動時にのみこのファイルを読み取り、元のデータセットの復元に使用します。

また、RDB オプションと AOF オプションの両方を同時に有効にすることもできます。 永続性オプションの長所と短所など、詳細については、[Valkey Persistence ドキュメント ](https://valkey.io/topics/persistence/) を参照してください。

キャッシュインスタンスには、Commerce キャッシュ全体を格納するのに十分な大きさになるようにインスタンスを設定します。 サイズ要件は、商品の数やストアの表示など、様々な要因によって異なります。 出発点として、ファイルシステム上のキャッシュフォルダーのサイズを使用できます。 例えば、ファイルシステムの `var/cache` フォルダーが 5 GB の場合、起動するには少なくとも 5 GB の Valkey インスタンスを設定します。 Commerce キャッシュは復元できるので、キャッシュインスタンスには永続性は必要ありません。

パフォーマンスを調整する場合は、非同期削除について次の設定を有効にできます。 これらの設定によって、Valkey の動作が変わることはありません。

```ini
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
lazyfree-lazy-user-del yes
```
