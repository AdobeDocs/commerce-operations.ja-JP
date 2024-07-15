---
title: 実装計画フェーズ
description: Adobe Commerce プロジェクトの計画段階における実装のベストプラクティスについて説明します。
role: Developer, Admin, User
feature: Best Practices
exl-id: 6baeac79-8dc3-45b4-bb25-8f2add8b3443
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 1%

---

# 計画フェーズ

計画フェーズには、次のアクティビティが含まれます。

- アーキテクチャ設計
- カタログデザイン
- 拡張機能の購入
- プロジェクトのスコープ
- 要件の収集
- 販売およびマーケティング

以下の節には、計画段階に関するベストプラクティス情報が含まれています。

## 要件の収集

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
    <td>サイト、ストア、ストア表示を設定して、サイトのパフォーマンスを最大化します。</td>
  </tr>
  <tr>
    <td><a href="https://business.adobe.com/blog/how-to/the-usual-suspects-5-configuration-issues-to-maximize-your-peak-sales">設定に関する一般的な問題</a></td>
    <td>Adobe Commerce Sites で最も一般的な 5 つの設定の問題を修正して防止します。</td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cache-management.html">キャッシュ</a></td>
    <td>キャッシュ管理ツールを使用して、サイトのパフォーマンスを向上させます。</td>
  </tr>
  <tr>
    <td><a href="https://developer.adobe.com/commerce/php/development/cache/page/public-content/">フルページキャッシュ</a></td>
    <td>Adobe Commerce拡張機能でキャッシュを実装する際に、パブリックデータを操作する方法を説明します。</td>
  </tr>
  <tr>
    <td><a href="opcache-memory-size.md">OPcache のメモリー・サイズ</a></td>
    <td>OPcache メモリー消費の特定の設定でパフォーマンスの低下を回避します。</td>
  </tr>
  <tr>
    <td><a href="reporting-configuration.md">レポートの設定</a></td>
    <td>使用していない場合は、レポートモジュールを削除してサイトのパフォーマンスを最適化します。</td>
  </tr>
  <tr>
    <td colspan="2"><em>データベース設定</em></td>
  </tr>
  <tr>
    <td><a href="database-on-cloud.md">クラウドデプロイメント用のデータベースの設定</a></td>
    <td>クラウドインフラストラクチャプロジェクトにAdobe Commerceをデプロイする場合は、データベースとアプリケーションを設定してパフォーマンスを向上させます。</td>
  </tr>
  <tr>
    <td><a href="mysql-configuration.md">MySQL の設定</a></td>
    <td>MySQL トリガーとスレーブ接続がサイトのパフォーマンスに与える影響と、それらを効果的に使用する方法について説明します。</td>
  </tr>
  <tr>
    <td colspan="2"><em>サービス設定</em></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html">Fastly の設定</a></td>
    <td>クラウドインフラストラクチャプロジェクト上のAdobe Commerce用に Fastly サービスを設定します。</td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic.html">New Relicの通知チャネルの設定</a></td>
    <td>New Relic ダッシュボードにアクセスし、クラウドインフラストラクチャプロジェクト上のAdobe Commerceからデータを分析します。</td>
  </tr>
  <tr>
    <td><a href="redis-service-configuration.md">Redis の設定</a></td>
    <td>Adobe Commerceの拡張 Redis キャッシュ実装を使用して、キャッシュパフォーマンスを向上させます。</td>
  </tr>
  <tr>
    <td><a href="realpath-cache-size.md">Realpath のキャッシュ・サイズ</a></td>
    <td>推奨される設定を使用するように PHP の'readlpath'のキャッシュ設定を更新することで、パフォーマンスを最適化します。</td>
  </tr>
</tbody>
</table>

## アーキテクチャ設計

| ベストプラクティス | 説明 |
|----------------------------------------------------------------------------------------|----------------------------------------------------------|
| [ グローバル・リファレンス・アーキテクチャ（GRA） ](../../architecture/global-reference/examples.md) | GRA コードベースを構成する一般的な方法を理解します。 |

## カタログデザイン

| ベストプラクティス | 説明 |
|---------------------------------------------------------------------------------------------------|---------------------------------------------------------------|
| [ カテゴリ設定 ](catalog-management.md#category-limits) | 最適なパフォーマンスが得られるように製品カテゴリを設定します。 |
| [ 製品設定&#x200B;](catalog-management.md#product-sku-limits) | 最適なパフォーマンスが得られるように製品 SKU を設定します。 |
| [ 製品バリエーションの設定 ](catalog-management.md#product-variations) | 最適なパフォーマンスを得るために、製品のバリエーションを設定する。 |
| [ 製品オプションの設定 ](catalog-management.md#product-options) | 最適なパフォーマンスを得るために、製品オプションを設定します。 |
| [ 製品属性の設定&#x200B;](catalog-management.md#product-attributes) | 最適なパフォーマンスを得るために製品の属性を設定する。 |
| [ 製品リストのページネーション設定 ](catalog-management.md#product-listing-pagination) | 最適なパフォーマンスを得るために、製品リストのページネーションを設定する。 |

## 拡張機能

| ベストプラクティス | 説明 |
|-----------------------------------------------------------------|----------------------------------------------------------------------------------------|
| [Adobe Commerceでのサードパーティ拡張機能の使用 ](extensions.md) | サードパーティのAdobe Commerce拡張機能によって発生するパフォーマンスの問題を回避する方法について説明します。 |

## プロジェクトのスコープ

| ベストプラクティス | 説明 |
|--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| [ パートナー・エスカレーション ](partner-escalation.md) | Adobeアカウントチームとパートナーの問題のエスカレーションに備えるか、エスカレーションを回避する方法を学びます。 |
| [ 支払保管事務 ](payment-processing-storage.md) | 支払いの詳細を安全に処理し、保存します。 |

## 販売およびマーケティング

| ベストプラクティス | 説明 |
|------------------------------------------------------------|--------------------------------------------------------------|
| [ 製品カートの制限 ](catalog-management.md#cart-limits) | 最適なパフォーマンスを得るために、買い物かごの制限を管理する。 |
| [ プロモーションの設定 ](catalog-management.md#promotions) | 買い物かご内の品目の販売とプロモーションを設定します。 |
