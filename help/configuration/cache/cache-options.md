---
title: キャッシュオプション
description: 低レベルのキャッシュストレージへのアクセスを設定します。
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---

# 低レベルのキャッシュオプション

Commerce アプリケーションは、低レベルのキャッシュフロントエンドとバックエンドを使用して、キャッシュストレージへのアクセスを提供します。

## 低レベルのフロントエンドキャッシュ

Commerceは、[Magento\Framework\Cache\Core[ フロントエンドキャッシュを実装することで ](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html)Zend_Cache_Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) を拡張しています。

## 低レベルのバックエンド・キャッシュ

一般に、Commerce アプリケーションは、[Zend_Cache Backends](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html) がサポートする任意のバックエンドキャッシュで動作します。 ただし、このガイドでは、次の低レベルのバックエンドキャッシュのみを扱っています。

- [Redis](config-redis.md)
- [ データベース ](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
- ファイルシステム（デフォルト）：ファイルシステムのキャッシュを使用するための設定は不要です。

[Varnish](config-varnish.md) では、低レベルのキャッシュバックエンドを設定する必要はありません。
