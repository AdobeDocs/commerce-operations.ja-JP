---
title: リファレンスアーキテクチャ
description: Adobe CommerceおよびMagento Open Sourceのデプロイメントで推奨されるリファレンスアーキテクチャの図を確認します。
exl-id: 85a6d3d6-f47f-4806-97bd-fa7a73605f4c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# リファレンスアーキテクチャ

このトピックでは、リソースが他のユーザーと共有されないデータセンター（仮想化されていない）で物理的にホストされるプレーンサーバーを使用する、Adobe CommerceおよびMagento Open Sourceインスタンスの一般的な推奨設定について説明します。 ホスティングプロバイダー、特に Commerce の高パフォーマンスホスティングを専門としている場合は、要件に応じて同様に、またはより効果的な別の設定をお勧めします。

クラウドインフラストラクチャ環境のAdobe Commerceについては、 [スターターアーキテクチャ](https://devdocs.magento.com/cloud/architecture/starter-architecture.html).

## [!DNL Commerce] 参照アーキテクチャの図

The [!DNL Commerce] リファレンスアーキテクチャの図は、拡張性の高いを設定するためのベストプラクティスアプローチを表しています [!DNL Commerce] サイト。

図の各要素の色は、その要素がMagento Open Sourceの一部かAdobe Commerceかを示し、必要に応じて示します。

* Magento Open Sourceにはオレンジ色の要素が必要です
* グレーの要素はMagento Open Sourceのオプションです
* 青い要素はAdobe Commerceのオプションです

![コマースリファレンスのアーキテクチャ図](../assets/performance/images/ref-architecture-2.3.png)

次の節では、コマースリファレンスアーキテクチャ図の各セクションの推奨事項と考慮事項を示します。

### [!DNL Varnish]

* A [!DNL Varnish] クラスターは、サイトのトラフィックに合わせて拡大/縮小できます
* 必要なキャッシュページの数に基づいてインスタンスサイズを調整する
* トラフィックの多いサイトでは、 [!DNL Varnish] キャッシュ上で Web 層ごとに 1 つのリクエスト（最大）を確実にフラッシュするマスター

### Web

* トラフィックと冗長性に対するノードの規模の有効化
* 1 つのノードがマスターで、cron を実行します。
* または、専用の管理者ノードとワーカーノードを使用します。

### キャッシュ

* セッションに別の Redis インスタンスを実装することを検討します。
* キャッシュごとに Redis インスタンスを持つことができます
* 予想される最大のキャッシュサイズを含むようにインスタンスをサイズ設定

### データベースとキュー

* 高トラフィックサイトは、スレーブ DB で DB のパフォーマンスを調整し、注文/買い物かごで DB を分割できます (Adobe Commerce)
* スレーブ DB を使用して迅速なリカバリを可能にし、データのバックアップを行うことを検討します。
* 低トラフィックのサイトでは、DB に画像を保存できます。

### 検索 {#search-heading}

* 検索トラフィックに基づいてインスタンス数を調整する

### ストレージ

* pub/media ストレージに GFS または GlusterFS を使用することを検討
* または、低トラフィックのサイトに DB ストレージを使用します。

### 推奨 [!DNL Varnish] 参照アーキテクチャ

Magentoは、複数のフルページキャッシュエンジン（ファイル、Memcache、Redis）をサポートしています。 [!DNL Varnish]) を追加せずに、拡張機能を介して拡張されたカバレッジと共に使用できます。 [!DNL Varnish] は、推奨されるフルページキャッシュエンジンです。  [!DNL Commerce] 多くの異なる [!DNL Varnish] 設定。

高可用性を必要としないサイトでは、シンプルな [!DNL Varnish] Nginx SSL を終了して設定します。

![シンプル [!DNL Varnish] SSL 終了を使用した設定](../assets/performance/images/single-varnish-with-ssl-termination.png)

高可用性が必要なサイトでは、2 層を使用することをお勧めします [!DNL Varnish] SSL による終了ロードバランサーの設定

![高可用性の 2 層 [!DNL Varnish] SSL によるロードバランサーの終了を使用した設定](../assets/performance/images/ha-2-tier-varnish-with-ssl-term-load-balancer.png)
