---
title: パフォーマンスベンチマーク
description: AdobeのクラウドインフラストラクチャでホストされるAdobe Commerce実装のパフォーマンスベンチマーク結果を確認します。
exl-id: cc9b090a-a504-4df3-aa32-81882f431dd9
feature: Cloud
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---

# ベンチマークサマリ

Adobe Commerce 2.4.5 のパフォーマンスベンチマークの結果には、次のインフラストラクチャおよび追加のコンポーネントを使用してデプロイされたAdobe Commerce インスタンスで測定されたパフォーマンスが反映されています。
- [Pro クラウド環境 ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html)[ 拡張アーキテクチャ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html)
- Adobe Commerceの [B2B](https://experienceleague.adobe.com/docs/commerce-admin/b2b/introduction.html)
- [Adobe CommerceInventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/introduction.html)
- [Adobe Stock](https://experienceleague.adobe.com/docs/commerce-admin/content-design/media/adobe-stock/adobe-stock.html)

追加のカスタマイズはありません。

次の情報は、ベンチマーク結果の概要と、テスト中に使用した環境とデータに関する情報を示しています。

## 主要業績評価指標

次の図は、パフォーマンスベンチマークのCommerce ストア設定と、テスト結果の主要パフォーマンス指標を示しています。

![ パフォーマンスベンチマーク JMeter と実稼動インフラストラクチャ ](../../../assets/performance/images/performance-benchmark-kpis-245-cloud.png){width="700" zoomable="yes"}

企業 B2C 組織を模したテスト基準に基づいて、システムは、標準的な負荷フローで、ピーク時に要求されたトラフィックと注文番号を処理できます。

### パフォーマンスのハイライト

- **注文件数** - 99 百分位数に対して、応答時間を 2 秒未満に維持しながら、1 分あたり 3,481 件の注文を処理しました（リクエストの 99% は 2 秒未満の応答時間で処理されました）。
- **ページビュー** - 99 パーセンタイルの応答時間を 2 秒未満に維持しながら、1 時間あたり 200 万回を超えるページビューを処理しました。
- **有効な SKU** – 顧客プロファイルには、250,000 製品で 2 億 4,200 万個の異なる価格バリエーション（<a href="https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/product-sku-limits.html">eSKU</a>）が含まれていました。
- **GraphQL リクエスト** - 99 パーセンタイルの応答時間を 2 秒未満に保ちながら、1 分あたり 10,500 件のGraphQL キャッシュされていないリクエストに拡張されました。
- **同時管理者ユーザー** - 99 パーセンタイルの応答時間を 2 秒未満に維持しながら、500 人の同時管理者ユーザーをサポートするようにシステムを拡張しました。

## テスト環境

パフォーマンスベンチマークの結果は、拡張アーキテクチャを使用して Pro クラウド環境にデプロイされたAdobe Commerce 2.4.5 インスタンスに対するテストによって得られました。 また、このインスタンスには、Adobe Commerce B2B、Inventory management、Adobe Stock Integration モジュールもインストール、設定、有効化されています。

テストプロファイルのパフォーマンステストデータは、<a href="https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/generate-data.html">Performance Toolkit</a> を使用して生成されました。

パフォーマンスの測定は、顧客およびビジネスユーザー向けにシミュレートされた日々のストアアクティビティに基づいています。 値は、各ケースで最大スループットに近いものを反映していますが、プライベート販売やフラッシュ販売などの独自のビジネスモデルは反映していません。

- **LUMA ストアフロント**
   - ストアフロントの 3,000 人の同時ユーザー
   - CDN キャッシュヒット率を 30% に設定

     キャッシュレイヤーを効果的に使用すると、1 時間あたりのページビュー数が増加します。

- **GraphQL API**
   - 250 個の同時スレッド
   - CDN キャッシュヒット率を 0% に設定

     GraphQLの前にキャッシュレイヤーを配置することで、応答時間が大幅に短縮します。

- **管理 Web**
   - 500 人の同時ユーザー
   - CDN キャッシュヒット率を 0% に設定

## テスト環境仕様

Adobe Commerce インスタンスに対して実行される JMeter 負荷プロファイルを使用して、負荷テストを完了しました。 テスト中に 3 つの web ノードと 3 つのサービスノードが使用されました。 次の画像は、JMeter のエントリポイントと実稼動インフラストラクチャの詳細を示しています。

![ パフォーマンスベンチマーク JMeter と実稼動インフラストラクチャ ](https://git.corp.adobe.com/storage/user/43354/files/4d801e3e-96b7-4193-b94f-12571263b495){width="700" zoomable="yes"}

### 用途

<a href="https://experienceleague.adobe.com/docs/commerce-operations/release/notes/adobe-commerce/2-4-5.html">Adobe Commerce 2.4.5</a> は、Pro アーキテクチャを使用してクラウドインフラストラクチャにデプロイされます。

### インフラストラクチャ

パフォーマンスベンチマークでは、Adobe Commerce 2.4.5 を次の処理能力を持つ [ スケーラブルなインフラストラクチャ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html) にデプロイしました。

- **Web ノードの仕様**
   - vCPU 216 （72 x 3 ノード）
   - メモリ 432 GiB （144 x 3 ノード）
   - ネットワーク帯域幅 768 Gbps （256 x 3 ノード）
   - EBS 帯域幅 57000 Mbps （19000 x 3 ノード）
   - プロビジョニングされたストレージ：100 GB

- **サービスノードの仕様**
   - vCPU 192 （64 x 3 ノード）
   - メモリ 768 GiB （256 x 3 ノード）
   - ネットワーク帯域幅 60 Gbps （20 x 3 ノード）
   - EBS 帯域幅 40800 Mbps （13600 x 3 ノード）
   - プロビジョニングされたストレージ：1100 GB
