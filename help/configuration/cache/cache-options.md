---
title: キャッシュオプション
description: 低レベルのキャッシュストレージへのアクセスを設定します。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 0%

---

# 低レベルキャッシュオプション

Commerce アプリケーションは低レベルを使用します [キャッシュ](https://glossary.magento.com/cache) [前線](https://glossary.magento.com/frontend) および [バックエンド](https://glossary.magento.com/backend) キャッシュストレージへのアクセスを提供する。

## 低レベルのフロントエンドキャッシュ

コマースの拡張 [Zend_Cache_Core](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html) 実装する [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) フロントエンドキャッシュ

## 低レベルのバックエンドキャッシュ

一般に、コマースアプリケーションは、 [Zend_Cache バックエンド](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html) サポート。 ただし、このガイドで扱うのは、次の低レベルのバックエンドキャッシュのみです。

- [レディス](config-redis.md)
- [データベース](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
- ファイルシステム（デフォルト）:ファイル・システムのキャッシュを使用するための設定は必要ありません。

[ワニス](config-varnish.md) では、低レベルのキャッシュバックエンドを設定する必要はありません。
