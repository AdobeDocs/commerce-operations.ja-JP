---
title: プラットフォームツール
description: Platform Commerce 実装に推奨されるAdobeツールを選択します。
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 0%

---


# プラットフォームツール

e コマースサイトを干渉なしに実行し続けるために十分に考慮し、厳格にテストする必要がある側面の不足はありません。 Not only must you identify the right solutions to tackle every aspect of the site—from data storage and programming to caching and security—but you need the right process to ensure the delivery of a platform that both runs smoothly and can be built and optimized efficiently.

このセクションでは、多数のAdobe・コマースの実装でテストおよび実行されたツール、ソリューション、プロセス、方法論について説明するだけでなく、特定のビジネス・ニーズと目標に最も適したソリューションに関する推奨事項についても説明します。

次の表に、プラットフォーム上でのパフォーマンスを向上させるためにAdobeコマース内で使用できる、推奨されるソリューションを示します。

| Purpose | Tool |
|------------------------------------------|-------------------------|
| Database | MySQL、MariaDB、Percona |
| プログラミング言語 | PHP, JS, HTML, LESS CSS |
| 統合開発環境 (IDE) | Eclipse、PHPStorm |
| Web サーバー | Nginx、Apache |
| キャッシュサービス | ワニス・レディス |
| 検索サービス | Elasticsearch |
| メッセージキューサービス | RabbitMQ |
| セキュリティスキャンツール | SonarQube、ZAP |

## データベース

There are three different tools that we use depending on the needs of the brand. MySQL は、ストアが極端な負荷を処理することを期待していない場合、Adobeコマースデータベースとして優れたベースラインソリューションです。

MariaDB はコミュニティに焦点を当て、純粋なパフォーマンスよりも機能に関心を持つユーザーに適しています。 MariaDB supports a large array of database engines, disk encryption, complex horizontal interconnectivity, and scaling features, which could be interesting for large Adobe Commerce stores.

Percona は、パフォーマンスとピーク負荷の処理を中心とした MySQL のフォークです。 Choose MariaDB if you need more quality of life and DevOps features. Go for Percona if your goal is to gain high-load performance in large-scale datasets.

## プログラミング言語

Adobeコマースは PHP ベースのアプリケーションで、最新のリリースは常に最新の安定した PHP バージョンと互換性があります ( 例えば、Adobeコマースバージョン 2.4 では PHP 7.4 を使用することを推奨します )。 より高いセキュリティとパフォーマンスを得るために、PHP を設定して要求処理の速度と効率を最大限に高める際には、いくつかの要因を考慮する必要があります。 Adobeコマース Web ストアフロントは、HTML、JavaScript、LESS CSS プリプロセッサーを使用して構築されています。

## Web サーバー

Adobeコマースは、Nginx および Apache Web サーバーを完全にサポートします。 Adobeコマースには、次の両方の推奨設定ファイルのサンプルが用意されています。

- **Nginx**—`<magento_home>/nginx.conf.sample`
- **Apache** —`<magento_home>.htaccess.sample`

Nginx サンプルには、パフォーマンスを向上させるための設定が含まれ、再構成が必要ないように設計されています。

## キャッシュサービス

Adobeコマースは、Redis、Memcache、filesystem、データベースなど、キャッシュとセッションデータを保存する多数のオプションを提供します。 複数の Web ノードを持つ設定では、Redis が最適なオプションです。

ストアのフルページキャッシュサーバーとして Vanrish を使用することを強くお勧めします。 Adobeコマースは、パフォーマンスに関する推奨設定をすべて含む、Vanrish 用のサンプル設定ファイルを配布しています。

## Search services

Adobeコマースバージョン 2.4 以降の場合、カタログ検索ソリューションとしてElasticsearchを使用するように、すべてのインストールを設定する必要があります。 Elasticsearchは、カタログ内の製品をすばやく詳細検索できます。 Elasticsearch is optional for releases prior to 2.4, but it’s recommended.

## メッセージキューサービス

メッセージキューは、メッセージの送信者と受信者が互いに接触しない非同期通信メカニズムを提供する。 RabbitMQ is an open-source message broker that offers a reliable, highly available, scalable, and portable messaging system.

## セキュリティツール

[Adobe・コマース・セキュリティ・スキャン・ツール ](https://docs.magento.com/user-guide/magento/security-scan.html) を使用すると、ストア Web サイトを定期的に監視し、セキュリティ上の既知のリスク、マルウェア、最新でないソフトウェアの更新を受け取ることができます。 通常、このツールの使用は、ユーザー受け入れテスト (UAT) を開始する際に開始します。 Commerce Security Scan Tool は、無料ですべての実装とAdobeCommerce のバージョンで利用できますが、AdobeCommerce の他に、CI/CD プロセス中および各リリース前に使用できる選択肢があります。

SonarQube は、コードの技術品質を分析および測定するために設計された、オープンソースの品質管理プラットフォームです。 SonarQube は、コードのバグ、構文エラー、脆弱性に関する完全なレポートを提供するだけでなく、コードの修正方法や例も提供しています。 SonarQube は、CI/CD 環境で、デプロイ前にコードを分析できるツールとして使用するのに最適です。

Zed Attack Proxy(ZAP) は、世界中の何千ものペンテスターが使用する無料のセキュリティテストツールです。 ZAP は OWASP によって開発され、手動セキュリティテストに最も優れたツールの 1 つです。
