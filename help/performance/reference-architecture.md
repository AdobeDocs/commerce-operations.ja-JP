---
title: 参照アーキテクチャ
description: Adobe Commerceのデプロイメントに推奨されるリファレンスアーキテクチャの図を確認します。
exl-id: 85a6d3d6-f47f-4806-97bd-fa7a73605f4c
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# 参照アーキテクチャ

ここでは、データセンター（仮想化されていない）で物理的にホストされているプレーンサーバーを使用し、リソースが他のユーザーと共有されていないAdobe Commerce インスタンスの一般的な推奨設定について説明します。 ホスティングプロバイダーは、特にCommerceのハイパフォーマンスホスティングを専門としている場合、要件に対して同等または効果的な別の設定を推奨する場合があります。

クラウドインフラストラクチャ環境でのAdobe Commerceについては、を参照してください。 [スターターアーキテクチャ](https://devdocs.magento.com/cloud/architecture/starter-architecture.html).

## [!DNL Commerce] リファレンスアーキテクチャ図

この [!DNL Commerce] リファレンスアーキテクチャの図は、スケーラブルな環境を設定するためのベストプラクティスアプローチを表しています [!DNL Commerce] サイト。

図中の各要素の色は、その要素がMagento Open Sourceの一部であるかAdobe Commerceの一部であるか、また必要かどうかを示しています。

* Magento Open Sourceにはオレンジ色が必要です
* グレーの要素はMagento Open Sourceのオプションです
* Adobe Commerceでは、青い要素はオプションです

![Commerceのリファレンスアーキテクチャ図](../assets/performance/images/ref-architecture-2.3.png)

次の節では、Commerce リファレンスアーキテクチャの図の各セクションに関する推奨事項と考慮事項を示します。

### [!DNL Varnish]

* A [!DNL Varnish] クラスターは、サイトのトラフィックに合わせて拡張可能
* 必要なキャッシュページの数に基づいてインスタンスサイズを調整します
* トラフィック量の多いサイトでは、 [!DNL Varnish] オンキャッシュで web 層ごとにリクエストを（最大で） 1 つフラッシュするためのマスター

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

### 推奨 [!DNL Varnish] 参照アーキテクチャ

Magentoは、複数のフルページキャッシュエンジン（File、Memcache、Redis、 [!DNL Varnish]）が標準で搭載されており、拡張機能による適用範囲が拡大されています。 [!DNL Varnish] は、推奨されるフルページキャッシュエンジンです。  [!DNL Commerce] は様々な種類のをサポートしています [!DNL Varnish] 設定。

高可用性を必要としないサイトの場合は、シンプルなを使用することをお勧めします [!DNL Varnish] nginx SSL ターミネーションを使用した設定。

![シンプル [!DNL Varnish] SSL ターミネーションを使用した設定](../assets/performance/images/single-varnish-with-ssl-termination.png)

高可用性が必要なサイトの場合は、2 層の使用をお勧めします [!DNL Varnish] ssl ターミネーションロードバランサーを使用した設定。

![2 層の高可用性 [!DNL Varnish] ssl ターミネータリングロードバランサーを使用した設定](../assets/performance/images/ha-2-tier-varnish-with-ssl-term-load-balancer.png)
