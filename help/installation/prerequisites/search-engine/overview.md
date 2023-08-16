---
title: 検索エンジンの前提条件
description: 次の手順に従って、Adobe CommerceとMagento Open Sourceのオンプレミスインストールで、サポートされている検索エンジンソフトウェアをインストールして設定します。
feature: Install, Search
exl-id: 44ea638a-7200-4269-be1b-b0851de2c4f4
source-git-commit: ce405a6bb548b177427e4c02640ce13149c48aff
workflow-type: tm+mt
source-wordcount: '786'
ht-degree: 0%

---

# 検索エンジンの前提条件

Adobe CommerceとMagento Open Source2.4 以降では、すべてのインストールでを使用するように設定する必要があります。 [Elasticsearch](https://www.elastic.co) または [OpenSearch](https://opensearch.org/) をカタログ検索ソリューションとして使用する。

>[!NOTE]
>
>2.4.4 で OpenSearch のサポートが追加されました。OpenSearch は互換性のあるフォークのElasticsearchです。 Elasticsearch7 を設定するすべての手順は、OpenSearch に適用されます。 [Elasticsearchから OpenSearch への移行](../../../upgrade/prepare/opensearch-migration.md) は、OpenSearch への切り替えに関するガイダンスを提供します。

## サポートされているバージョン

Adobe Commerce 2.4.4 以降をインストールする前に、Elasticsearchまたは OpenSearch をインストールして設定する必要があります。

詳しくは、 [必要システム構成](../../system-requirements.md) を参照してください。

## 推奨設定

以下をお勧めします。

* [検索エンジンに対する nginx の設定](configure-nginx.md)
* [検索エンジン用に Apache を設定する](configure-apache.md)

## インストール場所

次のタスクは、次の図に従ってシステムを設定したことを前提としています。

![検索エンジン図](../../../assets/installation/search-engine-config.svg)

前述の図は、次の内容を示しています。

* コマースアプリケーションと検索エンジンが異なるホストにインストールされている。

  別のホストで実行する場合は、プロキシが機能する必要があります。 ( 検索エンジンのクラスタリングは、このガイドの範囲外ですが、詳しくは、 [Elasticsearchクラスタリングに関するドキュメント](https://www.elastic.co/guide/en/elasticsearch/guide/current/distributed-cluster.html).)

* 各ホストには独自の Web サーバーがあり、Web サーバーを同じにする必要はありません。

  例えば、Commerce アプリケーションは Apache を実行し、検索エンジンは nginx を実行します。

* どちらの Web サーバーも、Transport Layer Security(TLS) を使用します。

  TLS の設定は、アドビのドキュメントの範囲外です。

検索リクエストは、次のように処理されます。

1. ユーザーからの検索リクエストが Commerce Web サーバーによって受信され、このリクエストが検索エンジンサーバーに転送されます。

   検索エンジンを設定して、プロキシのホストとポートに接続します。 Web サーバーの SSL ポート（デフォルトは 443）をお勧めします。

1. 検索エンジン Web サーバ（ポート 443 でリッスン）は、要求を検索エンジンサーバにプロキシします（デフォルトでは、ポート 9200 でリッスンします）。

1. 検索エンジンへのアクセスは、HTTP 基本認証によってさらに保護されます。 検索エンジンに到達するリクエストに対しては、SSL 経由で移動する必要があります *および* 有効なユーザー名とパスワードを入力します。

1. 検索エンジンがリクエストを処理します。

1. 同じルートで通信が返され、ElasticsearchWeb サーバーが安全なリバースプロキシとして機能します。

## 前提条件

この節で説明するタスクでは、次の作業が必要です。

* [ファイアウォールと SELinux](#firewall-and-selinux)
* [Java Software Development Kit(JDK) のインストール](#install-the-java-software-development-kit)
* [検索エンジンのインストール](#install-the-search-engine)
* [アップグレードElasticsearch](#upgrading-elasticsearch)

### ファイアウォールと SELinux

セキュリティ関連のソフトウェア (iptables、SELinux、AppArmor) は、サブシステム間の通信をブロックするようにデフォルトで設定できます。 問題があるかどうかを確認するのが良い考えかもしれません。

#### iptables および SELinux のルールを設定します。

ファイアウォールまたは SELinux が有効なときとの通信を許可するルールを設定するには、次のリソースを参照してください。

* [iptables ハウツー](https://help.ubuntu.com/community/IptablesHowTo)
* [iptables ルールの編集方法（fedora プロジェクト）](https://fedoraproject.org/wiki/How_to_edit_iptables_rules)
* [SELinux の概要 (CentOS.org)](https://www.centos.org)
* [SELinux ハウツー Wiki(CentOS.org)](https://wiki.centos.org/HowTos/SELinux)

### Java Software Development Kit のインストール

Java が既にインストールされているかどうかを確認するには、次のコマンドを入力します。

```bash
java -version
```

メッセージが `java: command not found` 「 」が表示されたら、次の節で説明するように Java SDK をインストールする必要があります。

次のセクションのいずれかを参照してください。

* [CentOS での最新 JDK のインストール](#install-the-jdk-on-centos)
* [Ubuntu での最新 JDK のインストール](#install-the-jdk-on-ubuntu)

#### CentOS での JDK のインストール

詳しくは、 [Digital Ocean チュートリアル](https://www.digitalocean.com/community/tutorials/how-to-install-java-on-centos-and-fedora#install-oracle-java-8).

必ず JDK とをインストールしてください。 *not* JRE。

```bash
yum -y install java-1.8.0-openjdk
```

>[!NOTE]
>
>すべてのオペレーティングシステムで Java バージョン 8 が使用できるとは限りません。 例えば、次のことが可能です。 [Ubuntu 用に利用可能なパッケージのリストを検索](https://packages.ubuntu.com/).

#### Ubuntu での JDK のインストール

Ubuntu に JDK 1.8 をインストールするには、次のコマンドををを使用してユーザーとして入力します。 `root` 権限：

```bash
apt-get -y update
```

```bash
apt-get install -y openjdk-8-jdk
```

その他のオプションについては、 [Oracle文書](https://docs.oracle.com/javase/8/docs/technotes/guides/install/install_overview.html).

### 検索エンジンのインストール

フォロー [インストールElasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html) または [OpenSearch のインストールと設定](https://opensearch.org/docs/latest/opensearch/install/index/) を参照してください。

Elasticsearchが動作していることを確認するには、実行中のサーバで次のコマンドを入力します。

```bash
curl -XGET '<host>:9200/_cat/health?v&pretty'
```

次のようなメッセージが表示されます。

```terminal
epoch      timestamp cluster       status node.total node.data shards pri relo init unassign pending_tasks
1519701563 03:19:23  elasticsearch green           1         1      0   0    0    0        0             0
```

OpenSearch が動作していることを確認するには、次のコマンドを入力します。

```bash
curl -XGET https://<host>:9200 -u 'admin:admin' --insecure
```

```bash
curl -XGET https://<host>:9200/_cat/plugins?v -u 'admin:admin' --insecure
```

## アップグレードElasticsearch

参照： [アップグレードElasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) データのバックアップ、移行に関する潜在的な問題の検出、アップグレードのテストを実稼動環境にデプロイする前に行う手順について詳しくは、 現在のバージョンのElasticsearchに応じて、完全なクラスターの再起動が必要な場合と不要な場合があります。

Elasticsearchには JDK 1.8 以降が必要です。 詳しくは、 [Java Software Development Kit のインストール](#install-the-java-software-development-kit) をクリックして、インストールされている JDK のバージョンを確認します。

## その他のリソース

詳しくは、 [Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html) または [OpenSearch](https://opensearch.org/docs/latest/) ドキュメント。
