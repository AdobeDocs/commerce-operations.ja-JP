---
title: キャッシュオプション
description: 低レベルのキャッシュストレージへのアクセスを設定します。
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
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
