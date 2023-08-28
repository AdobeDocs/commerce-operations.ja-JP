---
title: 実装計画段階
description: Adobe Commerceプロジェクトの計画段階に関する実装のベストプラクティスについて説明します。
role: Developer, Admin, User
feature: Best Practices
exl-id: 6baeac79-8dc3-45b4-bb25-8f2add8b3443
source-git-commit: 9cda88a4aeb4cc58d8ec9c4417e3107885a6cdb8
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# 計画段階

計画段階には、次のアクティビティが含まれます。

- 要件収集
- アーキテクチャ設計
- カタログデザイン
- プロジェクト範囲
- アカウントのプロビジョニング
- ユーザーアクセス
- 拡張機能の購入

次のセクションでは、計画段階のベストプラクティス情報について説明します。

## 要件収集

- **アプリケーション設定**
   - [サイト、ストア、ストアの表示（クラウドインフラストラクチャ）を設定する際のベストプラクティス](sites-stores-store-views.md)
   - [Adobe Commerceサイトで最もよく発生する 5 つの設定上の問題の回避方法および修正方法](https://business.adobe.com/blog/how-to/usual-suspects-five-configuration-fixes-maximize-your-peak-sales)
   - [キャッシュのベストプラクティス](https://docs.magento.com/user-guide/system/cache-management.html#best-practices-for-caching)
   - [フルページキャッシュ](https://developer.adobe.com/commerce/php/development/cache/page/public-content/)
   - [OPcache メモリサイズ](opcache-memory-size.md)
   - [レポート設定](reporting-configuration.md)

- **データベース設定**
   - [クラウドデプロイメントのデータベース設定のベストプラクティス&#x200B;](database-on-cloud.md)
   - [MySQL 設&#x200B;定](mysql-configuration.md)

- **サービス設定**
   - [Fastly の設定](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)
   - [New Relic — 通知チャネルの設定](https://devdocs.magento.com/cloud/project/new-relic.html#configure-notification-channels)
   - [Redis サービス設定のベストプラクティス&#x200B;](redis-service-configuration.md)
   - [再パスキャッシュサイズのベストプラクティス](realpath-cache-size.md)

## **アーキテクチャ設計**

<!--Asset not yet integrated
- [GRA Architecture examples](https://wiki.corp.adobe.com/x/kD4ykw)
-->
- [グローバルリファレンスアーキテクチャについて](../../../implementation-playbook/architecture/global-reference/overview.md)

## **カタログデザイン**

次のトピックでは、カテゴリ数、製品に対する効果的な SKU、製品のバリエーション、製品の属性とオプションなど、Adobe Commerceカタログを設定する際のパフォーマンス最適化のベストプラクティスについて説明します。

- [カテゴリ設定](catalog-management.md#category-limits)
- [製品設&#x200B;定](catalog-management.md#product-sku-limits)
- [製品バリエーションの設定](catalog-management.md#product-variations)
- [製品オプションの設定](catalog-management.md#product-options)
- [製品属性の設&#x200B;定](catalog-management.md#product-attributes)
- [製品リストのページネーション設定](catalog-management.md#product-listing-pagination)

## **セールスとマーケティング**

- [製品買い物かごの上限に関するベストプラクティス](catalog-management.md#cart-limits)
- [プロモーション設定のベストプラクティス](catalog-management.md#promotions)

## **プロジェクト範囲**

- [パートナーのエスカレーション](partner-escalation.md)
- [支払ストレージ処理](payment-processing-storage.md)

## **購入拡張機能**

- [Adobe Commerceでサードパーティの拡張機能を使用する際のベストプラクティス](extensions.md)
