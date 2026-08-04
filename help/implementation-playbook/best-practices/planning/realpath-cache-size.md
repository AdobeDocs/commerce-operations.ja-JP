---
title: リアルパスキャッシュサイズ
description: PHPのreadlpath キャッシュ設定を更新して、推奨設定を使用するようにAdobe Commerceのパフォーマンスを最適化する方法を説明します。
role: Developer
feature: Best Practices, Cache
exl-id: 1cd48155-5d60-48b2-b07b-9b5784b81681
source-git-commit: bdb900e81b3088ac452b7bfb975d5a68ecc44e7e
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 1%

---

# Realpath キャッシュ設定のベストプラクティス

Realpath キャッシュは、毎回参照されるファイル名の実際のファイルシステムのパスをキャッシュします。 さまざまなファイル関数が実行されるか、ファイルが必要になり、相対パスを使用するたびに、PHPはそのファイルが実際に存在する場所を検索する必要があります。

Commerceのパフォーマンスを向上させるには、次の推奨設定を使用して、`php.ini` ファイルの`realpath_cache`設定を行います。

- キャッシュ サイズを10 MB （`realpath_cache_size=10M`）に設定します
- 有効期間（ttl）を7200秒（`realpath_cache_ttl=7200`）に設定

設定手順については、[PHP オプションの設定方法](../../../installation/prerequisites/php-settings.md#how-to-set-php-options)を参照してください。

## 影響を受ける製品とバージョン

- Adobe Commerce オンプレミス、すべてのバージョン 2.3.x以降
- Adobe Commerce on cloud infrastructure （すべてのバージョン 2.3.x以降）

## 潜在的なパフォーマンスへの影響

Realpath キャッシュ設定値が低すぎたり高すぎたりすると、キャッシュ生成時に追加のオーバーヘッドが発生し、パフォーマンスが低下します。

## 追加情報

- [オンプレミス：PHP設定](../../../performance/software.md#php-settings)
- クラウド基盤：
  - [データベースのベストプラクティス](database-on-cloud.md)
  - [Magento Commerce Cloudの最も一般的なデータベースの問題](../maintenance/resolve-database-performance-issues.md)
- [インデクサーの「スケジュールに従って更新」により、Magentoのパフォーマンスが最適化される](../maintenance/indexer-configuration.md)
