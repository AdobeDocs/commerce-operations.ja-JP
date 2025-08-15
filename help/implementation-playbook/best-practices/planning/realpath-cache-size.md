---
title: Realpath のキャッシュ・サイズ
description: PHP の readlpath キャッシュ設定を更新し、推奨設定を使用してAdobe Commerceのパフォーマンスを最適化する方法を説明します。
role: Developer
feature: Best Practices, Cache
exl-id: 1cd48155-5d60-48b2-b07b-9b5784b81681
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 1%

---

# Realpath キャッシュ構成のベスト・プラクティス

Realpath キャッシュは、参照されるファイル名の実際のファイルシステムパスを、毎回検索する代わりにキャッシュします。 様々なファイル関数が実行されたり、ファイルを要求したり、相対パスを使用したりするたびに、PHP はそのファイルが実際に存在する場所を探す必要があります。

Commerceのパフォーマンスを向上させるには、次の推奨設定を使用して、`realpath_cache` ファイルの `php.ini` の設定を行います。

- キャッシュサイズを 10 MB に設定します（`realpath cache_size=10M`）。
- 有効期間（ttl）を 7200 秒（`realpath_cache_ttl=7200`）に設定します

設定手順については、[PHP オプションの設定方法 ](../../../installation/prerequisites/php-settings.md#how-to-set-php-options) を参照してください。

## 影響を受ける製品とバージョン

- Adobe Commerce オンプレミス、すべてのバージョン 2.3.x 以降
- クラウドインフラストラクチャー上のAdobe Commerce、すべてのバージョン 2.3.x 以降

## パフォーマンスへの潜在的な影響

Realpath のキャッシュ設定値が低すぎる、または高すぎる場合は、キャッシュ生成中にオーバーヘッドが増加し、パフォーマンスが低下します。

## 追加情報

- [オンプレミス：PHP 設定](../../../performance/software.md#php-settings)
- クラウドインフラストラクチャー上：
   - [データベースのベストプラクティス](database-on-cloud.md)
   - [Magento Commerce Cloud で最も一般的なデータベースの問題](../maintenance/resolve-database-performance-issues.md)
- [インデクサーの「スケジュールに従った更新」により、Magentoのパフォーマンスが最適化されます](../maintenance/indexer-configuration.md)
