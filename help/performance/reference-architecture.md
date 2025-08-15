---
title: 参照アーキテクチャ
description: Adobe Commerceのデプロイメントに推奨されるリファレンスアーキテクチャの図を確認します。
exl-id: 85a6d3d6-f47f-4806-97bd-fa7a73605f4c
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# 参照アーキテクチャ

ここでは、データセンター（仮想化されていない）で物理的にホストされているプレーンサーバーを使用し、リソースが他のユーザーと共有されていないAdobe Commerce インスタンスの一般的な推奨設定について説明します。 ホスティングプロバイダーは、特にCommerceのハイパフォーマンスホスティングを専門としている場合、要件に対して同等または効果的な別の設定を推奨する場合があります。

クラウドインフラストラクチャ環境でのAdobe Commerceについては、[ スターターアーキテクチャ ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/starter-architecture) を参照してください。

## [!DNL Commerce] リファレンスアーキテクチャ図

[!DNL Commerce] リファレンスアーキテクチャの図は、スケーラブルな [!DNL Commerce] サイトを設定するためのベストプラクティスアプローチを表しています。

図中の各要素の色は、その要素がMagento Open Sourceの一部であるかAdobe Commerceの一部であるか、また必要かどうかを示しています。

* Magento Open Sourceにはオレンジの要素が必要です
* Magento Open Sourceでは、グレーの要素はオプションです
* Adobe Commerceでは、青い要素はオプションです

![Commerceのリファレンスアーキテクチャ図 ](../assets/performance/images/ref-architecture-2.3.png)

次の節では、Commerce リファレンスアーキテクチャの図の各セクションに関する推奨事項と考慮事項を示します。

### [!DNL Varnish]

* [!DNL Varnish] クラスターは、サイトのトラフィックに合わせて拡張できます
* 必要なキャッシュページの数に基づいてインスタンスサイズを調整します
* 高トラフィックのサイトでは、[!DNL Varnish]マスターを使用して、オンキャッシュで web 層ごとに（最大で） 1 つのリクエストをフラッシュするようにします

### Web

* トラフィックと冗長性に対するノードの拡張を有効にする
* 1 つのノードは master で、cron を実行します。
* または、専用の Admin ノードと Worker ノードを使用します

### キャッシュ

* セッション用に別の Redis インスタンスを実装することを検討してください
* キャッシュごとに Redis インスタンスを設定できます
* 想定される最大キャッシュサイズを含むようにインスタンスのサイズを設定します

### データベースとキュー

* 高トラフィックのサイトでは、スレーブ DB および注文/買い物かごのための分割 DB を使用して DB パフォーマンスを調整できます（Adobe Commerce）
* 迅速なリカバリとデータバックアップを可能にするスレーブ DB の使用を検討してください
* 低トラフィックのサイトは画像を DB に格納できる

### 検索 {#search-heading}

* 検索トラフィックに基づいてインスタンス数を調整

### ストレージ

* pub/media ストレージには GFS または GlusterFS の使用を検討してください
* または、低トラフィックサイトには DB ストレージを使用します

### 推奨される [!DNL Varnish] 参照アーキテクチャ

Magentoでは、複数のフルページキャッシュエンジン（ファイル、Memcache、Redis、[!DNL Varnish]）が標準でサポートされているほか、拡張機能による適用範囲が広がっています。 [!DNL Varnish] は、推奨されるフルページキャッシュエンジンです。  [!DNL Commerce] は、様々な [!DNL Varnish] 設定をサポートしています。

高可用性を必要としないサイトの場合は、Nginx SSL ターミネーションを使用したシンプルな [!DNL Varnish] 設定を使用することをお勧めします。

![SSL ターミネーションを使用したシンプルな [!DNL Varnish] 設定 ](../assets/performance/images/single-varnish-with-ssl-termination.png)

高可用性が必要なサイトの場合は、SSL ターミネータ ロード バランサーを使用した 2 層 [!DNL Varnish] 構成を使用することをお勧めします。

![SSL ターミネーター付き、高可用性の 2 層 [!DNL Varnish] 構成 ](../assets/performance/images/ha-2-tier-varnish-with-ssl-term-load-balancer.png)
