---
title: キャッシュオプション
description: 低レベルのキャッシュストレージへのアクセスを設定します。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# 低レベルキャッシュオプション

Commerce アプリケーションは、低レベルのキャッシュフロントエンドとバックエンドを使用して、キャッシュストレージへのアクセスを提供します。

## 低レベルのフロントエンドキャッシュ

コマースの拡張 [Zend_Cache_Core](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html) 実装する [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) フロントエンドキャッシュ

## 低レベルのバックエンドキャッシュ

一般に、コマースアプリケーションは、 [Zend_Cache バックエンド](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html) サポート。 ただし、このガイドで扱うのは、次の低レベルのバックエンドキャッシュのみです。

- [レディス](config-redis.md)
- [データベース](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
- ファイルシステム（デフォルト）:ファイル・システムのキャッシュを使用するための設定は必要ありません。

[ワニス](config-varnish.md) では、低レベルのキャッシュバックエンドを設定する必要はありません。
