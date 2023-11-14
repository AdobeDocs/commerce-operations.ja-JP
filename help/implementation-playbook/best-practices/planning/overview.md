---
title: 実装計画段階
description: Adobe Commerceプロジェクトの計画段階に関する実装のベストプラクティスについて説明します。
role: Developer, Admin, User
feature: Best Practices
exl-id: 6baeac79-8dc3-45b4-bb25-8f2add8b3443
source-git-commit: 40d850add2ef8c51e9192758135768306b163780
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 1%

---

# 計画段階

計画段階には、次のアクティビティが含まれます。

- アーキテクチャ設計
- カタログデザイン
- 拡張機能の購入
- プロジェクト範囲
- 要件収集
- セールスとマーケティング

次のセクションでは、計画段階のベストプラクティス情報について説明します。

## 要件収集

<table>
<thead>
  <tr>
    <th>ベストプラクティス</th>
    <th>説明</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td colspan="2"><em>アプリケーション設定</em></td>
  </tr>
  <tr>
    <td><a href="sites-stores-store-views.md">サイト、ストア、ストア表示の設定</a></td>
    <td>サイト、ストア、およびストアの表示を設定して、サイトのパフォーマンスを最大化します。</td>
  </tr>
  <tr>
    <td><a href="https://business.adobe.com/blog/how-to/the-usual-suspects-5-configuration-issues-to-maximize-your-peak-sales">設定に関する一般的な問題</a></td>
    <td>Adobe Commerceサイトで最もよく発生する 5 つの設定の問題を修正し、回避します。</td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cache-management.html">キャッシュ</a></td>
    <td>キャッシュ管理ツールを使用して、サイトのパフォーマンスを向上させます。</td>
  </tr>
  <tr>
    <td><a href="https://developer.adobe.com/commerce/php/development/cache/page/public-content/">フルページキャッシュ</a></td>
    <td>Adobe CommerceまたはMagento Open Source拡張機能にキャッシュを実装する際に、パブリックデータを使用する方法について説明します。</td>
  </tr>
  <tr>
    <td><a href="opcache-memory-size.md">OPcache メモリサイズ</a></td>
    <td>OPcache のメモリ消費の特定の設定で、パフォーマンスの低下を回避します。</td>
  </tr>
  <tr>
    <td><a href="reporting-configuration.md">レポートの設定</a></td>
    <td>レポートモジュールを使用しない場合は削除して、サイトのパフォーマンスを最適化します。</td>
  </tr>
  <tr>
    <td colspan="2"><em>データベース設定</em></td>
  </tr>
  <tr>
    <td><a href="database-on-cloud.md">クラウドデプロイメント用のデータベースの設定</a></td>
    <td>クラウドインフラストラクチャプロジェクトにAdobe Commerceをデプロイする際のパフォーマンスを向上させるために、データベースとアプリケーションの設定を構成します。</td>
  </tr>
  <tr>
    <td><a href="mysql-configuration.md">MySQL の設定</a></td>
    <td>MySQLトリガーとスレーブ接続がサイトのパフォーマンスに与える影響と、それらを効果的に使用する方法について説明します。</td>
  </tr>
  <tr>
    <td colspan="2"><em>サービス設定</em></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html">Fastly の設定</a></td>
    <td>クラウドインフラストラクチャプロジェクト上のAdobe Commerceに Fastly サービスを設定します。</td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic.html">New Relicの通知チャネルの設定</a></td>
    <td>New Relicダッシュボードにアクセスし、Adobe Commerce on cloud infrastructure プロジェクトのデータを分析します。</td>
  </tr>
  <tr>
    <td><a href="redis-service-configuration.md">Redis を設定</a></td>
    <td>Adobe Commerce用の拡張 Redis キャッシュ実装を使用して、キャッシュのパフォーマンスを向上させます。</td>
  </tr>
  <tr>
    <td><a href="realpath-cache-size.md">Realpath のキャッシュサイズ</a></td>
    <td>PHP の'readlpath'キャッシュ設定を更新し、推奨設定を使用してパフォーマンスを最適化します。</td>
  </tr>
</tbody>
</table>

## アーキテクチャ設計

| ベストプラクティス | 説明 |
|----------------------------------------------------------------------------------------|----------------------------------------------------------|
| [グローバルリファレンスアーキテクチャ (GRA)](../../architecture/global-reference/examples.md) | GRA コードベースを整理する一般的な方法を理解します。 |

## カタログデザイン

| ベストプラクティス | 説明 |
|---------------------------------------------------------------------------------------------------|---------------------------------------------------------------|
| [カテゴリ設定](catalog-management.md#category-limits) | 最適なパフォーマンスを得るために製品カテゴリを設定します。 |
| [製品設&#x200B;定](catalog-management.md#product-sku-limits) | 製品 SKU を設定して、最適なパフォーマンスを実現します。 |
| [製品バリエーションの設定](catalog-management.md#product-variations) | 最適なパフォーマンスを得るために、製品のバリエーションを設定します。 |
| [製品オプションの設定](catalog-management.md#product-options) | 最適なパフォーマンスを得るために製品オプションを設定します。 |
| [製品属性の設&#x200B;定](catalog-management.md#product-attributes) | 最適なパフォーマンスを得るために製品属性を設定します。 |
| [製品リストのページネーション設定](catalog-management.md#product-listing-pagination) | 最適なパフォーマンスを得るために、製品リストのページネーションを設定します。 |

## 拡張機能

| ベストプラクティス | 説明 |
|-----------------------------------------------------------------|----------------------------------------------------------------------------------------|
| [Adobe Commerceでのサードパーティの拡張機能の使用](extensions.md) | サードパーティのAdobe Commerce拡張機能によって生じるパフォーマンスの問題を回避する方法について説明します。 |

## プロジェクト範囲

| ベストプラクティス | 説明 |
|--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| [パートナーのエスカレーション](partner-escalation.md) | パートナーの問題をAdobeアカウントチームにエスカレーションする準備をするか、エスカレーションを回避する方法を学びます。 |
| [支払ストレージ処理](payment-processing-storage.md) | 支払いの詳細を安全に処理し、保存します。 |

## セールスとマーケティング

| ベストプラクティス | 説明 |
|------------------------------------------------------------|--------------------------------------------------------------|
| [製品買い物かごの制限](catalog-management.md#cart-limits) | 最適なパフォーマンスを得るために、買い物かごの制限を管理します。 |
| [プロモーションの設定](catalog-management.md#promotions) | 買い物かごの品目の販売とプロモーションを設定します。 |
