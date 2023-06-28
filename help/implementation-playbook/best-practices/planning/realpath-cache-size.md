---
title: Realpath キャッシュサイズ
description: 推奨設定を使用するように PHP readlpath キャッシュ設定を更新し、Adobe Commerceのパフォーマンスを最適化する方法を説明します。
role: Developer
feature: Best Practices, Cache
exl-id: 1cd48155-5d60-48b2-b07b-9b5784b81681
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# Realpath キャッシュ構成のベストプラクティス

realpath キャッシュは、参照されたファイル名の実際のファイルシステムパスをキャッシュします。 様々なファイル関数が実行されたり、ファイルを必要としたり、相対パスを使用するたびに、PHP はそのファイルが実際に存在する場所を調べる必要があります。

コマースのパフォーマンスを向上させるには、次の推奨設定を使用して `realpath_cache` 設定 `php.ini` ファイル：

- キャッシュサイズを 10 MB に設定します (`realpath cache_size=10M`)
- 有効期間 (ttl) を 7200 秒に設定します (`realpath_cache_ttl=7200`)

設定手順については、 [PHP オプションの設定方法](../../../installation/prerequisites/php-settings.md#how-to-set-php-options).

## 影響を受ける製品およびバージョン

- Adobe Commerceオンプレミス、すべてのバージョン 2.3.x 以降
- Adobe Commerce on cloud infrastructure （すべてのバージョン 2.3.x 以降）

## パフォーマンスへの影響の可能性

Realpath キャッシュの設定値が小さすぎるか大きすぎる場合は、キャッシュ生成中にオーバーヘッドが追加され、パフォーマンスが低下します。

## 追加情報

- [オンプレミス：PHP 設定](../../../performance/software.md#php-settings)
- クラウドインフラストラクチャ上：
   - [データベースのベストプラクティス](database-on-cloud.md)
   - [データベースで最も一般的な問題のMagento Commerce Cloud](../maintenance/resolve-database-performance-issues.md)
- [インデクサー「スケジュールに従って更新」により、Magentoのパフォーマンスを最適化](../maintenance/indexer-configuration.md)
