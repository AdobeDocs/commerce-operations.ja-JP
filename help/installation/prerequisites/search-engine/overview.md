---
title: 検索エンジンの前提条件
description: 次の手順に従って、Adobe Commerceのオンプレミスインストールでサポートされる検索エンジンソフトウェアをインストールし設定します。
feature: Install, Search
exl-id: 44ea638a-7200-4269-be1b-b0851de2c4f4
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 0%

---

# 検索エンジンの前提条件

Adobe Commerce Elasticsearch 2.4 以降、すべてのインストールは、[User](https://www.elastic.co) または [OpenSearch](https://opensearch.org/) をカタログ検索ソリューションとして使用するように設定する必要があります。

>[!NOTE]
>
>OpenSearch のサポートは 2.4.4 で追加されました。OpenSearch は、互換性のあるElasticsearchのフォークです。 Elasticsearch 7 を設定する手順は、すべて OpenSearch に適用されます。 [Elasticsearchから OpenSearch への移行 ](../../../upgrade/prepare/opensearch-migration.md) は、OpenSearch への切り替えに関するガイダンスを提供します。

## サポートされているバージョン

Adobe Commerce 2.4.4 以降をインストールする前に、Elasticsearchまたは OpenSearch をインストールして設定する必要があります。

特定のバージョン情報については、[ システム要件 ](../../system-requirements.md) を参照してください。

## 推奨設定

以下をお勧めします。

* [検索エンジンの nginx の設定](configure-nginx.md)
* [検索エンジン用に Apache を設定する](configure-apache.md)

## インストール場所

次のタスクは、次の図に従ってシステムを設定していることを前提としています。

![ 検索エンジンの図 ](../../../assets/installation/search-engine-config.svg)

上の図は次の内容を示しています。

* Commerce アプリケーションと検索エンジンは、異なるホストにインストールされています。

  別々のホストで実行する場合は、プロキシを機能させる必要があります。 （検索エンジンのクラスタリングはこのガイドの範囲外ですが、詳細については、[Elasticsearchクラスタリングのドキュメント ](https://www.elastic.co/guide/en/elasticsearch/guide/current/distributed-cluster.html) を参照してください。）

* 各ホストには独自の web サーバーがあり、web サーバーは同じである必要はありません。

  例えば、Commerce アプリケーションで Apache を実行し、検索エンジンで nginx を実行することができます。

* どちらの Web サーバーも Transport Layer Security （TLS）を使用しています。

  TLS の設定は、アドビのドキュメントの範囲外です。

検索リクエストは次のように処理されます。

1. 利用者からの検索リクエストをCommerceウェブサーバが受信し、検索エンジンサーバに転送する。

   プロキシのホストおよびポートに接続するように検索エンジンを設定します。 Web サーバーの SSL ポート（デフォルトでは 443）を推奨します。

1. 検索エンジン web サーバ（ポート 443 をリッスン）は、検索エンジン サーバに要求をプロキシします（デフォルトでは、ポート 9200 をリッスンします）。

1. 検索エンジンへのアクセスは、HTTP 基本認証によってさらに保護されます。 検索エンジンに到達するには、リクエストが SSL を経由する必要があります *そして* 有効なユーザー名とパスワードを指定します）。

1. 検索エンジンがリクエストを処理します。

1. 通信は同じルートで返され、Elasticsearchの Web サーバーは安全なリバースプロキシとして機能します。

## 前提条件

この節で説明するタスクには、次の操作が必要です。

* [ファイアウォールと SELinux](#firewall-and-selinux)
* [Java Software Development Kit （JDK）をインストールします。](#install-the-java-software-development-kit)
* [検索エンジンのインストール](#install-the-search-engine)
* [Elasticsearchのアップグレード](#upgrading-elasticsearch)

### ファイアウォールと SELinux

セキュリティ関連のソフトウェア（iptables, SELinux, AppArmor）は、サブシステム間の通信をブロックするようにデフォルトで設定できます。 問題があるかどうか調べてみるのも良いかもしれません。

#### iptables と SELinux のルール設定

ファイアウォールまたは SELinux が有効な状態での通信を許可するルールを設定するには、次のリソースを参照してください。

* [iptables の使い方 ](https://help.ubuntu.com/community/IptablesHowTo)
* [iptables ルールの編集方法（fedora プロジェクト） ](https://fedoraproject.org/wiki/How_to_edit_iptables_rules)
* [SELinux の概要（CentOS.org） ](https://www.centos.org)
* [SELinux のハウツー Wiki （CentOS.org） ](https://wiki.centos.org/HowTos/SELinux)

### Java Software Development Kit のインストール

Java が既にインストールされているかどうかを確認するには、次のコマンドを入力します。

```bash
java -version
```

メッセージ `java: command not found` が表示された場合は、次の節で説明するように Java SDK をインストールする必要があります。

以下のセクションの 1 つを参照してください。

* [CentOS に最新の JDK をインストール](#install-the-jdk-on-centos)
* [Ubuntu に最新の JDK をインストールします。](#install-the-jdk-on-ubuntu)

#### CentOS への JDK のインストール

詳しくは、この [Digital Ocean チュートリアル ](https://www.digitalocean.com/community/tutorials/how-to-install-java-on-centos-and-fedora#install-oracle-java-8) を参照してください。

JRE ではなく JDK をインストールし *くだ* い。

```bash
yum -y install java-1.8.0-openjdk
```

>[!NOTE]
>
>Java バージョン 8 は、すべてのオペレーティングシステムで使用できるわけではありません。 例えば、[Ubuntu で利用可能なパッケージのリストを検索 ](https://packages.ubuntu.com/) できます。

#### Ubuntu への JDK のインストール

Ubuntu に JDK 1.8 をインストールするには、`root` 権限を持つユーザーとして次のコマンドを入力します。

```bash
apt-get -y update
```

```bash
apt-get install -y openjdk-8-jdk
```

その他のオプションについては、[Oracleドキュメント ](https://docs.oracle.com/javase/8/docs/technotes/guides/install/install_overview.html) を参照してください。

### 検索エンジンのインストール

プラットフォーム固有の手順については、[Elasticsearchのインストール ](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html) または [OpenSearch のインストールと設定 ](https://opensearch.org/docs/latest/opensearch/install/index/) に従ってください。

Elasticsearchが動作していることを確認するには、動作しているサーバで次のコマンドを入力します。

```bash
curl -XGET '<host>:9200/_cat/health?v&pretty'
```

次のようなメッセージが表示されます。

```
epoch      timestamp cluster       status node.total node.data shards pri relo init unassign pending_tasks
1519701563 03:19:23  elasticsearch green           1         1      0   0    0    0        0             0
```

OpenSearch が機能していることを確認するには、次のコマンドを入力します。

```bash
curl -XGET https://<host>:9200 -u 'admin:admin' --insecure
```

```bash
curl -XGET https://<host>:9200/_cat/plugins?v -u 'admin:admin' --insecure
```

## Elasticsearchのアップグレード

データのバックアップ、潜在的な移行の問題の検出、実稼動環境にデプロイする前のアップグレードのテストに関する手順について詳しくは、[Elasticsearchのアップグレード ](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) を参照してください。 現在のElasticsearchのバージョンに応じて、クラスターの完全な再起動は必要な場合と不要な場合があります。

Elasticsearchには JDK 1.8 以降が必要です。 インストールされている JDK のバージョンを確認するには、[Java Software Development Kit のインストール ](#install-the-java-software-development-kit) を参照してください。

## その他のリソース

[Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html) または [OpenSearch](https://opensearch.org/docs/latest/) ドキュメントを参照してください。
