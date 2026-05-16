---
title: キャッシュバックエンドオプションとストレージリファレンス
description: ファイルシステム、Redis、Valkey、データベースストレージなど、Adobe Commerceのキャッシュバックエンドオプションについて説明します。 レガシーかつモダンなアプローチをご紹介します。
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
source-git-commit: 9cd0f2a84772e2d68fd15a00651216abfa9ec91c
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# キャッシュバックエンドオプションとストレージリファレンス

Commerce アプリケーションでは、低レベルのキャッシュフロントエンドとバックエンドを使用して、キャッシュストレージへのアクセスを提供します。 Commerceは、複数のキャッシングバックエンドと戦略をサポートしており、それぞれ異なるユースケースに適しています。 このページでは、使用可能なバックエンドとその違いについて説明します。

>[!NOTE]
>
>フロントエンドキャッシュ設定について詳しくは、[ キャッシュフロントエンドの設定](cache-types.md)を参照してください。

## バックエンドキャッシュオプション

次の表に、使用可能なバックエンドキャッシュの概要を示します。

| バックエンド | 説明 | 設定ガイド |
| ------- | ----------- | ------------------- |
| ファイルシステム | デフォルト： キャッシュデータを`var/cache/`の下のファイルに保存します。 設定は必要ありません。 | 該当なし |
| [Redis](config-redis.md) | 高性能なキャッシュを実現するインメモリデータストア。 | [ デフォルトのキャッシュにRedisを使用](redis-pg-cache.md) |
| [Valkey](config-valkey.md) | オープンソースのRedis互換の代替手段。 | [既定のキャッシュにValkeyを使用](valkey-pg-cache.md) |
| [ データベース ](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/) | データベースに裏打ちされたキャッシュ： | [ カスタムキャッシュエンジンの作成](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/){target="_blank"} （Adobe開発者向けドキュメント） |

>[!NOTE]
>
>[Varnish](config-varnish.md)は、HTTP レベルでページ全体キャッシュを処理し、低レベルのキャッシュバックエンドを使用しません。

## 導入アプローチ

Commerceは、バックエンドの実装アプローチを2つサポートしています。 Commerceのバージョンによって、最適なアプローチを選択できます。

>[!BEGINTABS]

>[!TAB 従来のZend ベースのキャッシュ （2.4.8以前） ]

バックエンド設定にフルクラス名を使用します。

| バックエンド | クラス名 |
| ------- | ---------- |
| Redis | `Magento\Framework\Cache\Backend\Redis` |
| バルキー | `Magento\Framework\Cache\Backend\Valkey` |

これらは`Zend_Cache_Backend` インターフェイスと互換性があります。

**設定例：**

```php?start_inline=1
'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
'backend_options' => [
    'server' => '127.0.0.1',
    'database' => '0',
    'port' => '6379',
],
```

>[!TAB 最新のSymfony キャッシュ （2.4.9以降、推奨） ]

>[!TIP]
>
>最新のSymfony Cache実装は、PSR-6 コンプライアンス、Igbinary シリアル化、gzip圧縮、Lua スクリプト、および永続的な接続を通じて、より優れたパフォーマンスを提供します。

簡略化されたバックエンドタイプ名を使用：

| バックエンド | タイプ名 |
| ------- | --------- |
| Redis | `redis` |
| バルキー | `valkey` |
| ファイルシステム | `file` |

**設定例：**

```php?start_inline=1
'backend' => 'redis',
'backend_options' => [
    'server' => '127.0.0.1',
    'database' => '0',
    'port' => '6379',
    'serializer' => 'igbinary',
    'compression_lib' => 'gzip',
],
```

>[!ENDTABS]

設定オプションの詳細については、次を参照してください。

- [デフォルトのキャッシュにRedisを使用](redis-pg-cache.md)
- [デフォルトのキャッシュにValkeyを使用](valkey-pg-cache.md)
- [L2 キャッシュ設定](level-two-cache.md)

従来のZend ベースのオプションについては、[Laminas ドキュメント ](https://docs.laminas.dev/)を参照してください。
