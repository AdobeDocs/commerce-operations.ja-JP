---
title: Valkeyのインストールと設定
description: Adobe Commerceを使用して、キャッシュとセッションストレージ用にValkeyをインストールして設定する方法について説明します。 最適化とパフォーマンス調整のためのオプションをご紹介します。
feature: Configuration, Cache
exl-id: 12dbc171-3df6-4413-869b-a3450b5647b4
source-git-commit: de613310ad701dd594a6ee8fcd973aa2c3769870
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# Valkeyのインストールと設定

Valkeyは、Redis互換のオープンソースのメモリ内データストアで、キャッシュバックエンドおよびセッションストレージとして使用できます。 主な機能は次のとおりです。

- PHP セッションストレージ
- `foreach` ループを使用しないタグベースのキャッシュのクリーンアップ
- ディスク上の保存とマスター/スレーブ・レプリケーション

## Valkeyのインストール

Valkey ソフトウェアをインストールして設定するには、次のリソースを参照してください。

- [Valkeyのページをダウンロード](https://valkey.io/download/){target="_blank"}
- [Valkey クイックスタート](https://valkey.io/topics/quickstart/){target="_blank"}
- [Valkey ドキュメントページ](https://valkey.io/docs){target="_blank"}

## Valkey設定の設定

インストールに応じて、Valkey設定は通常、`/etc/valkey/valkey.conf` ファイルまたは`/etc/valkey/<port>.conf` ファイルで見つけることができます。

要件に合わせてValkey インスタンスを最適化するには、各セッション、Commerce キャッシュ、FPCに専用のインスタンスを使用することで、最適な結果を得ることができます。

Adobeでは、Valkey データをディスクにコピーするセッションの永続性を有効にすることをお勧めします。 Valkey Database Backup （RDB）スナップショットまたはAppend Only File （AOF）永続ログを使用できます。

- **RDB** （Valkey Database） スナップショットは、前回の保存以降にキーの最小数が変更された場合、指定された時間の後に完全なデータベースをダンプファイルに保存します。 この設定を構成するには、`valkey.conf` ファイル内の`save`設定を使用します。

- **ファイルのみを追加** （AOF）は、Valkeyに送信された各書き込み操作をジャーナルファイルに保存します。 Valkeyは、このファイルを再起動時にのみ読み取り、それを使用して元のデータセットを復元します。

RDB オプションとAOF オプションの両方を同時に有効にすることもできます。 永続性オプションの利点と欠点を含む詳細については、[Valkey Persistence ドキュメント &#x200B;](https://valkey.io/topics/persistence/)を参照してください。

キャッシュインスタンスの場合は、Commerce キャッシュ全体を格納するのに十分な大きさになるようにインスタンスを設定します。 サイズの要件は、商品数やストアビューなどの要因によって異なります。 出発点として、ファイルシステム上のキャッシュフォルダーのサイズを使用できます。 例えば、ファイルシステム上の`var/cache` フォルダーが5 GBの場合、Valkey インスタンスを5 GB以上で設定して開始します。 Commerce キャッシュを復元できるため、キャッシュインスタンスに永続性は必要ありません。

パフォーマンス調整の場合は、非同期削除に対して次の設定を有効にできます。 これらの設定は、Valkeyの動作を変更しません。

```ini
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
lazyfree-lazy-user-del yes
```
