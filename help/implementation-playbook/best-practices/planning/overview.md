---
title: 実装計画段階
description: Adobe Commerceプロジェクトの計画段階に関する実装のベストプラクティスについて説明します。
role: Developer, Admin, User
feature: Best Practices
feature-set: Commerce
source-git-commit: 78308f9cb3d2ebe8af41c42f9bb146409367ab6c
workflow-type: tm+mt
source-wordcount: '248'
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
- 内線購入

次のセクションでは、計画段階のベストプラクティス情報について説明します。

## 要件収集

- **アプリケーション設定**
   - [サイト、ストア、ストアの表示（クラウドインフラストラクチャ）の設定に関するベストプラクティス](sites-stores-store-views.md)
   - [Adobe Commerceサイトで最もよく発生する 5 つの設定上の問題の回避方法および修正方法](https://business.adobe.com/blog/how-to/usual-suspects-five-configuration-fixes-maximize-your-peak-sales)
   - [キャッシュのベストプラクティス](https://docs.magento.com/user-guide/system/cache-management.html#best-practices-for-caching)
   - [フルページキャッシュ](https://developer.adobe.com/commerce/php/development/cache/page/public-content/)
   - [OPcache メモリサイズ](opcache-memory-size.md)
   - [レポート設定](reporting-configuration.md)

- **データベース設定**
   - [クラウドデプロイメントのデータベース設定のベストプラクティス&#x200B;](database-on-cloud.md)
   - [MySQL スレーブ接続設&#x200B;定](configure-mysql-slave-connection-on-cloud.md)
   - [MySQLトリガー使用](mysql-triggers-usage.md)

- **サービス設定**
   - [Fastly の設定](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)
   - [New Relic — 通知チャネルの設定](https://devdocs.magento.com/cloud/project/new-relic.html#configure-notification-channels)
   - [Redis サービス設定のベストプラクティス&#x200B;](redis-service-configuration.md)
   - [再パスキャッシュサイズのベストプラクティス](realpath-cache-size.md)

## **アーキテクチャ設計**

<!--Asset not yet integrated
- [GRA Architecture examples](https://wiki.corp.adobe.com/x/kD4ykw)
-->
- [グローバルリファレンスアーキテクチャについて](../../../implementation-playbook/architecture/global-reference.md)

## **カタログデザイン**

次のトピックでは、カテゴリ数、製品に対する効果的な SKU、製品のバリエーション、製品の属性とオプションなど、Adobe Commerceカタログを設定する際のパフォーマンス最適化のベストプラクティスについて説明します。

- [カテゴリ設定](category-limits.md)
- [製品設&#x200B;定](product-sku-limits.md)
- [製品バリエーションの設定](product-variations.md)
- [製品オプションの設定](product-options.md)
- [製品属性の設&#x200B;定](product-attributes-and-options.md)
- [製品リストのページネーション設定](product-listing-pagination.md)

## **セールスとマーケティング**

- [製品買い物かごの上限に関するベストプラクティス](product-cart.md)
- [プロモーション設定のベストプラクティス](product-cart-promotions.md)

## **プロジェクト範囲**

- [パートナーのエスカレーション](partner-escalation.md)
- [支払ストレージ処理](payment-processing-storage.md)

## **購入拡張機能**

- [Adobe Commerceでサードパーティの拡張機能を使用する際のベストプラクティス](extensions.md)
