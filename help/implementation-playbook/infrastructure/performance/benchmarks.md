---
title: パフォーマンスベンチマーク
description: AdobeクラウドインフラストラクチャでホストされるAdobe Commerce実装のパフォーマンスベンチマーク結果を確認します。
exl-id: cc9b090a-a504-4df3-aa32-81882f431dd9
source-git-commit: 09a42dc68836b34eab2c9d90879b897729cd1b09
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 0%

---

# ベンチマークの概要

Adobe Commerce 2.4.5 のパフォーマンスベンチマーク結果は、以下のインフラストラクチャと追加のコンポーネントを使用してデプロイされたAdobe Commerceインスタンスで測定されたパフォーマンスを反映しています。
- [Pro クラウド環境](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html) と [スケールアーキテクチャ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html)
- [Adobe Commerce用 B2B](https://experienceleague.adobe.com/docs/commerce-admin/b2b/introduction.html)
- [Adobe Commerce Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/introduction.html)
- [Adobe Stock](https://experienceleague.adobe.com/docs/commerce-admin/content-design/media/adobe-stock/adobe-stock.html)

追加のカスタマイズはありません。

次の情報は、ベンチマーク結果の概要を示し、テスト中に使用された環境とデータに関する情報を提供します。

## 主要なパフォーマンス指標

次の図は、パフォーマンスベンチマークのコマースストアの設定と、テスト結果から得られる主要なパフォーマンス指標を示しています。

![パフォーマンスベンチマーク JMeter と実稼動インフラストラクチャ](../../../assets/performance/images/performance-benchmark-kpis-245-cloud.png){width="700" zoomable="yes"}

企業の B2C 組織を模倣したテスト条件に基づき、標準の負荷フローで、ピーク時に要求されたトラフィックと注文番号を処理できます。

### パフォーマンスのハイライト

- **注文** — 第 99 百分位の応答時間を 2 秒未満に保ちながら、1 分あたり 3,481 の注文を処理しました（要求の 99%が応答時間 2 秒未満で処理されました）。
- **ページビュー数** — 第 99 百分位の応答時間は 2 秒未満で維持しながら、1 時間あたり 200 万件を超えるページビューが処理されます。
- **有効な SKU** — 顧客プロファイルには 2 億 4200 万の異なる価格変動 (<a href="https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/product-sku-limits.html">eSKU</a>) 250,000 個の製品に対して使用できます。
- **GraphQL Requests** — システムは、99 番目のパーセンタイル値に対して 2 秒未満の応答時間を維持しながら、1 分あたり 10,500 個のGraphQLのキャッシュされていない要求に拡張されました。
- **同時管理者ユーザー** — システムは、第 99 百分位で 2 秒未満の応答時間を維持しながら、500 人の同時管理者ユーザーをサポートするように拡張されました。

## テスト環境

パフォーマンスのベンチマーク結果は、拡張されたアーキテクチャを使用して、Pro クラウド環境にデプロイされたAdobe Commerce 2.4.5 インスタンスに対してテストを実施した結果です。 また、このインスタンスには、Adobe Commerce B2B、Inventory management、Adobe Stock統合モジュールもインストール、設定および有効化されていました。

テストプロファイルのパフォーマンステストデータは、 <a href="https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/generate-data.html">Performance Toolkit</a>.

パフォーマンスの測定は、顧客およびビジネスユーザーに対する日々の店舗活動のシミュレーションに基づいておこなわれます。 これらの値は、各ケースでの最大スループットに近い値を反映していますが、個人向け販売やフラッシュ販売などの独自のビジネスモデルは反映していません。

- **LUMA ストアフロント**
   - ストアフロントでの 3,000 人の同時ユーザー
   - 30% CDN キャッシュヒット率に設定

      キャッシュレイヤーを有効に使用すると、1 時間あたりのページビュー数が増加します。

- **GraphQL API**
   - 250 個の同時スレッド
   - 0% CDN キャッシュヒット率に設定

      GraphQLの前面にあるキャッシュレイヤーを使用すると、応答時間が大幅に短縮されます。

- **管理 Web**
   - 500 人の同時ユーザー
   - 0% CDN キャッシュヒット率に設定

## テスト環境の仕様

Adobe Commerceインスタンスに対して実行する JMeter 読み込みプロファイルを使用して、読み込みテストが完了しました。 テスト中に 3 つの Web ノードと 3 つのサービスノードが使用されました。 次の図は、JMeter および実稼動インフラストラクチャのエントリポイントの詳細を示しています。

![パフォーマンスベンチマーク JMeter と実稼動インフラストラクチャ](https://git.corp.adobe.com/storage/user/43354/files/4d801e3e-96b7-4193-b94f-12571263b495){width="700" zoomable="yes"}

### アプリ

<a href="https://experienceleague.adobe.com/docs/commerce-operations/release/notes/adobe-commerce/2-4-5.html">Adobe Commerce 2.4.5</a> Pro アーキテクチャを備えたクラウドインフラストラクチャ上にデプロイされます。

### インフラ

パフォーマンスベンチマークに関しては、Adobe Commerce 2.4.5 は、 [スケーラブルインフラ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html) 以下の容量を使用します。

- **Web ノードの仕様**
   - vCPU 216 （72 x 3 ノード）
   - メモリ 432 GiB （144 x 3 ノード）
   - ネットワーク帯域幅 768 Gbps （256 x 3 ノード）
   - プロビジョニング済みストレージ 100 GB

- **サービスノードの仕様**
   - vCPU 192（64 x 3 ノード）
   - メモリ 768 GiB （256 x 3 ノード）
   - ネットワーク帯域幅 60 Gbps （20 x 3 ノード）
   - EBS 帯域幅40800 Mbps (13600 x 3 ノード )
   - プロビジョニング済みストレージ 1100 GB
