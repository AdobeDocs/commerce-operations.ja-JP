---
title: オンプレミスでのインストールの前提条件
description: Adobe Commerceのオンプレミスインストールに必要なソフトウェア依存関係について詳しく説明します。
exl-id: dd4694e7-5437-440c-bb67-804ae36149de
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 1%

---

# オンプレミスでのインストールの前提条件

Adobe CommerceまたはMagento Open Sourceをインストールする前に、次の作業を行う必要があります。

* を満たす 1 つ以上のホストの設定 [必要システム構成](../system-requirements.md).
* ロードバランシングを使用して複数の web ノードを設定する場合は、システムのその部分を設定してテストします _次の前_ アプリケーションをインストールします。
* 問題が発生した場合にロールバックできるように、インストール中の様々な時点でシステム全体をバックアップできることを確認してください。

>[!NOTE]
>
>ここでは、にAdobe CommerceまたはMagento Open Sourceをインストールすることを前提としています。 **開発環境**&#x200B;マシンに対するルートユーザーのアクセス権があること。 **および** マシンのセキュリティが高い必要がないこと。 より安全なマシンを設定する場合は、ネットワーク管理者に問い合わせてサポートを依頼することを強くお勧めします。

オペレーティングシステムのソフトウェアを更新およびアップグレードすることを強くお勧めします。 これらのアップグレードにより、将来の問題を防ぐためのセキュリティとソフトウェアの修正が提供される場合があります。 これは何を意味するのか分からない？ こちらをご覧ください [インストールの概要ページ](../overview.md).

を使用して、ユーザーとして次のコマンドを入力します `root` 権限：

* Ubuntu

  ```bash
  apt-get update
  ```

  ```bash
  apt-get upgrade
  ```

* CentOS

  ```bash
  yum -y update
  ```

  ```bash
  yum -y upgrade
  ```

## 前提条件の確認

システムの前提条件を確認するには、次のコマンドを入力します。

### Apache

CentOS: `httpd -v`

Ubuntu: `apache2 -v`

次の結果が示すように、Adobe Commerceは Apache バージョン 2.4 をサポートしています。

```terminal
Server version: Apache/2.4.0 (Unix)
Server built:   Jul 23 2017 14:17:29
```

Apache をインストールまたはアップグレードするには、を参照してください [Apache](web-server/apache.md).

### PHP

参照： [必要システム構成](../system-requirements.md) サポートされている PHP のバージョンおよび [PHP](../system-requirements.md#php-settings) （PHP の要件）。

### MySQL

インストールしているAdobe CommerceまたはMagento Open Sourceのバージョンと互換性のある MySQL のバージョンがあることを確認します。 参照： [必要システム構成](../system-requirements.md) （サポートされているバージョンの場合）

```bash
mysql -u <database root user or database owner name> -p
```

例：

```bash
mysql -u magento -p
```

次の結果は、実行しているバージョンを示しています。

```terminal
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 871
Server version: 5.7.9 MySQL Community Server (GPL)

Copyright (c) 2000, 2019, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.
```

タイプ `help` または `\h` ヘルプを参照してください。 タイプ `\c` 現在の input 文をクリアします。

Enter `exit` 時刻 `mysql>` 終了を確認する。

MySQL をインストールまたはアップグレードするには、次を参照してください。 [MySQL](database/mysql.md).

### 検索エンジン

OpenSearch のインストールを確認するには：

```bash
curl -XGET '<opensearch-hostname>:<opensearch-port>'
```

Elasticsearchのインストールを確認するには：

```bash
curl -XGET '<elasticsearch-hostname>:<elasticsearch-port>'
```

例：

```bash
curl -XGET 'localhost:9200'
```

```terminal
{
  "name" : "Z0S2B05",
  "cluster_name" : "elasticsearch_myname",
  "cluster_uuid" : "V-kpikRJQHudN-Wzdt-IrQ",
  "version" : {
    "number" : "6.8.7",
    "build_flavor" : "oss",
    "build_type" : "tar",
    "build_hash" : "c63e621",
    "build_date" : "2020-02-26T14:38:01.193138Z",
    "build_snapshot" : false,
    "lucene_version" : "7.7.2",
    "minimum_wire_compatibility_version" : "5.6.0",
    "minimum_index_compatibility_version" : "5.0.0"
  },
  "tagline" : "You Know, for Search"
```
