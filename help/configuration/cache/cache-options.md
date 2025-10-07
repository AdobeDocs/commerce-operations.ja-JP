---
title: キャッシュオプション
description: Adobe Commerceの低レベルのキャッシュオプションとストレージ設定について説明します。 Redis とデータベースのフロントエンド、バックエンド、ストレージの設定を確認します。
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '112'
ht-degree: 0%

---

# 低レベルのキャッシュオプション

Commerce アプリケーションは、低レベルのキャッシュフロントエンドとバックエンドを使用して、キャッシュストレージへのアクセスを提供します。

## 低レベルのフロントエンドキャッシュ

Commerceは、[Magento\Framework\Cache\Core](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html) フロントエンドキャッシュを実装することで [Zend_Cache_Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) を拡張しています。

## 低レベルのバックエンド・キャッシュ

一般に、Commerce アプリケーションは、[Zend_Cache Backends](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html) がサポートする任意のバックエンドキャッシュで動作します。 ただし、このガイドでは、次の低レベルのバックエンドキャッシュのみを扱っています。

- [Redis](config-redis.md)
- [ データベース ](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
- ファイルシステム（デフォルト）：ファイルシステムのキャッシュを使用するための設定は不要です。

[Varnish](config-varnish.md) では、低レベルのキャッシュバックエンドを設定する必要はありません。
