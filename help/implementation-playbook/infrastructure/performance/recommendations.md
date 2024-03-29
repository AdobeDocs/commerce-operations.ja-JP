---
title: パフォーマンス最適化の推奨事項
description: 次の推奨事項に従って、Adobe Commerce実装のパフォーマンスを最適化します。
exl-id: c5d62e23-be43-4eea-afdb-bb1b156848f9
feature: Cloud
topic: Performance
source-git-commit: 8b09d734d8ac4490cd88af5673acd0a41b6cdf66
workflow-type: tm+mt
source-wordcount: '1282'
ht-degree: 0%

---


# パフォーマンス最適化のレビュー

パフォーマンスの最適化は多くの側面から得られる場合でも、ほとんどのシナリオで考慮する必要がある一般的な推奨事項があります。 一般的な推奨事項としては、インフラストラクチャ要素の設定の最適化、Adobe Commerceのバックエンド設定、アーキテクチャ拡張性の計画などがあります。

>[!TIP]
>
>詳しくは、 [_パフォーマンスのベストプラクティスガイド_](../../../performance/overview.md) パフォーマンスの最適化の詳細については、を参照してください。

## インフラ

次の節では、インフラストラクチャの最適化に関する推奨事項を説明します。

### DNS 参照

DNS ルックアップは、ドメイン名が属する IP アドレスを見つけるプロセスです。 ブラウザーは、DNS 参照が完了するのを待ってから、各リクエストの内容をダウンロードする必要があります。 DNS 参照の削減は、ページ全体の読み込み時間を改善するために重要です。

### コンテンツ配信ネットワーク (CDN)

CDN を使用して、アセットのダウンロードパフォーマンスを最適化する。 Adobe Commerceは Fastly を使用します。 Adobe Commerceのオンプレミス実装がある場合は、CDN レイヤーを追加することも検討してください。

### Web 遅延

データセンターの場所は、フロントエンドユーザーの Web 遅延に影響します。

### ネットワーク帯域幅

十分なネットワーク帯域幅は、Web ノード、データベース、キャッシュ/セッションサーバー、その他のサービス間でのデータ交換に関する主要な要件の 1 つです。

Adobe Commerceは高いパフォーマンスを実現するためにキャッシュを効果的に使用するので、システムは Redis などのキャッシュサーバーと積極的にデータを交換できます。 Redis がリモートサーバーにインストールされている場合は、読み取り/書き込み操作のボトルネックを防ぐために、Web ノードとキャッシュサーバー間に十分なネットワークチャネルを提供する必要があります。

### オペレーティングシステム (OS)

オペレーティングシステムの設定と最適化は、他の高負荷 Web アプリケーションと比較して、Adobe Commerceに似ています。 サーバーが処理する同時接続の数が増えると、使用可能なソケットの数が完全に割り当てられる場合があります。

### Web ノードの CPU

1 つの CPU コアで、キャッシュを効果的に行わずに約 2 ～ 4Adobe Commerceリクエストを処理できます。 すべての受信リクエストをキューに入れずに処理するために必要な Web ノード/コアの数を判断するには、次の式を使用します。

```
N[Cores] = (N [Expected Requests] / 2) + N [Expected Cron Processes])
```

### PHP-FPM 設定

これらの設定を最適化するかどうかは、様々なプロジェクトのパフォーマンステスト結果によって異なります。

- **ByteCode**—PHP 7 でAdobe Commerceを最大速度で出すには、 `opcache` モジュールを構築し、適切に設定してください。

- **APCU**—Adobeでは、PHP APCu 拡張を有効にし、Composer を設定して最大のパフォーマンスを得ることを推奨します。 この拡張機能は、開いたファイルのファイルの場所をキャッシュします。これにより、ページ、Ajax 呼び出し、エンドポイントを含む、Adobe Commerceのサーバー呼び出しのパフォーマンスが向上します。

- **Realpath_cacheconfiguration** — 最適化中 `realpath_cache` PHP プロセスは、ページを読み込むたびにファイルを検索するのではなく、ファイルへのパスをキャッシュできます。

### Web サーバー

Web サーバーとして nginx を使用する場合は、わずかな再構成のみが必要です。 nginx Web サーバーはパフォーマンスが向上し、Adobe Commerce ([`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample)) をクリックします。

- TCP を使用した PHP-FPM の設定

- HTTP/2 および Gzip を有効にする

- ワーカー接続の最適化

### データベース

各ストアと環境は異なるので、このドキュメントでは MySQL の詳細な調整手順は示しませんが、Adobeは一般的な推奨事項を提示できます。

Adobe Commerceデータベース（およびその他のデータベース）は、データとインデックスの保存に使用できるメモリ量に応じて異なります。 MySQL データのインデクス化を有効に使用するには、使用可能なメモリの量が、少なくともデータベースに格納されているデータのサイズの半分に近い値になる必要があります。

最適化： `innodb_buffer_pool_instances` を設定して、複数のスレッドが同じインスタンスにアクセスしようとする際の問題を回避します。 の値 `max_connections` パラメータは、アプリケーションサーバーで設定された PHP スレッドの総数と関連付ける必要があります。 次の数式を使用して最適な値を計算 `innodb-thread-concurrency`:

```
innodb-thread-concurrency = 2 * (NumCPUs+NumDisks)
```

### セッションキャッシュ

Redis の別のインスタンスに対しては、セッションキャッシュを設定するのが適切な候補です。 このキャッシュタイプのメモリ設定では、サイトの買い物かご放棄戦略と、セッションがキャッシュに残る期間を考慮する必要があります。

Redis は、最適なパフォーマンスを得るために、他のすべてのキャッシュをメモリに保持するのに十分なメモリを割り当てる必要があります。 ブロックキャッシュは、構成するメモリ量を決定する際の重要な要素です。 ブロックキャッシュは、サイトのページ数（SKU 数 x ストア表示数）に対して増加します。

### ページキャッシュ

Adobeでは、Adobe Commerceストアのフルページキャッシュに Varnish を使用することを強くお勧めします。 The `PageCache` モジュールはコードベース内にまだ存在しますが、開発目的でのみ使用する必要があります。

Web 層の前にある別のサーバに Varnish をインストールします。 受信するすべてのリクエストを受け入れ、キャッシュされたページコピーを提供する必要があります。 Vanish がセキュアなページで効果的に動作するように、SSL 終端プロキシを Vanrish の前に配置することができます。 Nginx はこの目的で使用できます。

Vanish のフルページキャッシュメモリの無効化は有効ですが、Adobeは、最も人気のあるページをメモリに保持するのに十分なメモリを Vanish に割り当てることを推奨します。

### メッセージキュー

Message Queue Framework（MQF；メッセージキューフレームワーク）は、モジュールがキューにメッセージを公開できるシステムです。 また、非同期でメッセージを受信するコンシューマーも定義します。 Adobe Commerceサポート [!DNL RabbitMQ] メッセージを送受信するためのスケーラブルなプラットフォームを提供するメッセージングブローカーとして。

### パフォーマンスのテストと監視

各実稼動リリース前のパフォーマンステストでは、e コマースプラットフォームの機能を推定することをお勧めします。 起動後も監視を続け、ピーク時間を処理するための拡張性とバックアップ計画を用意します。

>[!NOTE]
>
> Adobe Commerce on cloud infrastructure では、上記のインフラストラクチャとアーキテクチャの最適化が既に適用されています。ただし、この最適化は、範囲外なので、DNS ルックアップは除きます。

### 検索 {#search-heading}

Adobe Commerceバージョン 2.4 以降ではElasticsearch（または OpenSearch）が必要になりますが、2.4 以前のバージョンで有効にすることもお勧めします。

## オペレーティングモデル

前述の一般的なインフラストラクチャ最適化の推奨事項に加え、特定のビジネスモードや規模に対するパフォーマンスを向上させるアプローチもあります。 このドキュメントでは、すべてのシナリオが異なるので、詳細なAdobe手順は提供しません。ただし、シナリオでは参照用にいくつかの高レベルオプションが提供される場合があります。

### ヘッドレスアーキテクチャ

専用の別の節があります。 [頭のない](../../architecture/enterprise-blueprint.md#headless-storefront). 要約すると、ストアフロントレイヤーがプラットフォーム自体から切り離されます。 それでも同じバックエンドですが、Adobe Commerceはリクエストを直接処理しなくなり、GraphQL API を介したカスタムストアフロントのみをサポートします。

### Adobe Commerceの更新を保持

Adobe Commerceを最新バージョンで実行する場合、常にパフォーマンスが向上します。 新しいバージョンがリリースされるたびにAdobe Commerceを最新の状態に保つことができない場合でも、 [アップグレード](../../../upgrade/overview.md) Adobe Commerceでパフォーマンスが大幅に最適化された場合。

例えば、2020 年に、Adobeは Redis 層の最適化をリリースし、非効率性の多く、接続の問題、Redis とAdobe Commerce間の不要なデータ転送を修正しました。 2.3 と 2.4 の間の全体的なパフォーマンスは夜と日で行われ、Redis の最適化のために、買い物かご、チェックアウト、同時使用ユーザーの大幅な改善が提供されます。

### データモデルの最適化

データには、不正なデータモデル、正しく構造化されていないデータ、インデックスがないデータなど、多くの問題が発生します。

いくつかの接続をテストしている場合は問題なく見えますが、実稼動環境にデプロイすると、パフォーマンスが大幅に低下する場合があります。 システムインテグレーターは、データモデル（特に製品属性）の設計方法を知っており、不要な属性を追加しないで、ビジネスロジックに影響を与える必須の属性（価格設定、在庫の可用性、検索など）を保持することが重要です。

ビジネスロジックに影響を与えず、ストアフロントにまだ存在する必要がある属性の場合は、それらをいくつかの属性（JSON 形式など）に組み合わせます。

プラットフォームのパフォーマンスを最適化するために、PIM や ERP から取得したデータや属性からストアフロントでビジネスロジックが必要でない場合は、その属性をAdobe Commerceに追加する必要はありません。

### 拡張性に優れた設計

拡張性は、キャンペーンを実行し、頻繁にピークトラフィック時間に直面するビジネスにとって重要です。 拡張性の高いアーキテクチャとアプリケーション設計により、ピーク時のリソースを増やし、その後のリソースを削減できます。
