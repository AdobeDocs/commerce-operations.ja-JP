---
title: 実行計画フェーズ
description: Adobe Commerce プロジェクトの計画段階での実装のベストプラクティスについて説明します。
role: Developer, Admin, User
feature: Best Practices
exl-id: 6baeac79-8dc3-45b4-bb25-8f2add8b3443
source-git-commit: 28ca422543728123edcaa41dedca6e3cc53536b6
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 1%

---

# 計画段階

計画段階では、次のアクティビティを実行します。

- 建築デザイン
- カタログデザイン
- 拡張機能の購入
- プロジェクト範囲
- 要件収集
- セールス部門とマーケティング部門

次の節では、計画段階のベストプラクティス情報を示します。

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
    <td><a href="sites-stores-store-views.md">サイト、ストア、ストアビューの設定</a></td>
    <td>サイト、ストア、ストアビューを設定して、サイトパフォーマンスを最大化します。</td>
  </tr>
  <tr>
    <td><a href="https://business.adobe.com/blog/how-to/the-usual-suspects-5-configuration-issues-to-maximize-your-peak-sales">一般的な設定の問題</a></td>
    <td>Adobe Commerce サイトの最も一般的な5つの設定問題を修正して防止します。</td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cache-management.html?lang=ja">キャッシュ</a></td>
    <td>キャッシュ管理ツールを使用して、サイトのパフォーマンスを向上させます。</td>
  </tr>
  <tr>
    <td><a href="https://developer.adobe.com/commerce/php/development/cache/page/public-content/">ページ全体のキャッシュ</a></td>
    <td>Adobe Commerce拡張機能にキャッシュを実装する際に、公開データを操作する方法について説明します。</td>
  </tr>
  <tr>
    <td><a href="opcache-memory-size.md">OPcacheのメモリサイズ</a></td>
    <td>OPcache メモリ消費の特定の設定でパフォーマンスの低下を回避します。</td>
  </tr>
  <tr>
    <td><a href="reporting-configuration.md">レポートの設定</a></td>
    <td>使用していない場合は、レポートモジュールを削除して、サイトパフォーマンスを最適化します。</td>
  </tr>
  <tr>
    <td colspan="2"><em>データベース設定</em></td>
  </tr>
  <tr>
    <td><a href="database-on-cloud.md">クラウド デプロイメント用のデータベースの設定</a></td>
    <td>クラウドインフラストラクチャプロジェクトにAdobe Commerceをデプロイする際のパフォーマンスを向上させるために、データベースとアプリケーションの設定を行います。</td>
  </tr>
  <tr>
    <td><a href="mysql-configuration.md">MySQLの設定</a></td>
    <td>MySQL トリガーとスレーブ接続がサイトパフォーマンスに与える影響と、それらを効果的に使用する方法について説明します。</td>
  </tr>
  <tr>
    <td colspan="2"><em>サービス設定</em></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=ja">Fastlyの設定</a></td>
    <td>Adobe Commerce on cloud インフラプロジェクト用にFastly サービスを設定します。</td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic.html?lang=ja">New Relicの通知チャネルの設定</a></td>
    <td>New Relicダッシュボードにアクセスし、Adobe Commerce on cloud インフラプロジェクトのデータを分析します。</td>
  </tr>
  <tr>
    <td><a href="redis-valkey-service-configuration.md">Redis/Valkeyの設定</a></td>
    <td>Adobe Commerce用の拡張Redis キャッシュ実装を使用して、キャッシュのパフォーマンスを向上させます。</td>
  </tr>
  <tr>
    <td><a href="realpath-cache-size.md">リアルパスキャッシュサイズ</a></td>
    <td>PHPの「readlpath」キャッシュ設定を更新して、推奨設定を使用することで、パフォーマンスを最適化します。</td>
  </tr>
</tbody>
</table>

## カタログデザイン

| ベストプラクティス | 説明 |
|---------------------------------------------------------------------------------------------------|---------------------------------------------------------------|
| [&#x200B; カテゴリ設定](catalog-management.md#category-limits) | 最適なパフォーマンスを得るために商品カテゴリを設定します。 |
| [製品設定&#x200B;](catalog-management.md#product-sku-limits) | 最適なパフォーマンスを実現するための製品SKUの設定。 |
| [製品バリエーション設定](catalog-management.md#product-variations) | 最適なパフォーマンスを得るために製品バリエーションを設定します。 |
| [製品オプション設定](catalog-management.md#product-options) | 最適なパフォーマンスを実現するための製品オプションを設定する。 |
| [製品属性設定&#x200B;](catalog-management.md#product-attributes) | 最適なパフォーマンスを得るために製品属性を設定します。 |
| [製品リストのページ設定](catalog-management.md#product-listing-pagination) | 最適なパフォーマンスを得るために、製品リストのページネーションを設定します。 |

## 拡張機能

| ベストプラクティス | 説明 |
|-----------------------------------------------------------------|----------------------------------------------------------------------------------------|
| [Adobe Commerceでのサードパーティの拡張機能の使用](extensions.md) | サードパーティのAdobe Commerce拡張機能に起因するパフォーマンスの問題を回避する方法について説明します。 |

## プロジェクト範囲

| ベストプラクティス | 説明 |
|--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| [&#x200B; パートナーのエスカレーション &#x200B;](partner-escalation.md) | Adobe アカウントチームでパートナーの問題をエスカレーションする準備をするか、エスカレーションを回避する方法について説明します。 |
| [支払いストレージ処理](payment-processing-storage.md) | 支払いの詳細を安全に処理して保存。 |

## セールス部門とマーケティング部門

| ベストプラクティス | 説明 |
|------------------------------------------------------------|--------------------------------------------------------------|
| [製品カート制限](catalog-management.md#cart-limits) | 最適なパフォーマンスのためにカート制限を管理します。 |
| [&#x200B; プロモーションの設定](catalog-management.md#promotions) | ショッピングカート内の商品の販売とプロモーションを設定します。 |
