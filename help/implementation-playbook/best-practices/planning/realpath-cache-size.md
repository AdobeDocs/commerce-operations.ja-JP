---
title: リアルパスキャッシュサイズ
description: PHPのreadlpath キャッシュ設定を更新して、推奨設定を使用するようにAdobe Commerceのパフォーマンスを最適化する方法を説明します。
role: Developer
feature: Best Practices, Cache
exl-id: 1cd48155-5d60-48b2-b07b-9b5784b81681
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
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
- [インデクサーの「スケジュールに従って更新」により、Magento パフォーマンスが最適化されます](../maintenance/indexer-configuration.md)
