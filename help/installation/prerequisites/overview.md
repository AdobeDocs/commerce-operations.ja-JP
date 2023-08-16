---
title: オンプレミスインストールの前提条件
description: Adobe CommerceとMagento Open Sourceのオンプレミスインストールに必要なソフトウェアの依存関係について詳しく説明します。
exl-id: dd4694e7-5437-440c-bb67-804ae36149de
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 1%

---

# オンプレミスインストールの前提条件

Adobe CommerceまたはMagento Open Sourceをインストールする前に、次の手順を実行する必要があります。

* 次の条件を満たす 1 つ以上のホストを設定します。 [システム要件](../system-requirements.md).
* ロードバランシングを使用して複数の Web ノードを設定する場合は、システムのその部分を設定してテストします _前_ アプリケーションをインストールします。
* 問題が発生した場合は、システム全体をロールバックできるように、インストール中の様々な時点でシステム全体をバックアップできることを確認します。

>[!NOTE]
>
>Adobe CommerceまたはMagento Open Sourceを **開発環境**（マシンへの root ユーザーアクセス権を持っている） **および** マシンを高度に安全にする必要はありません。 より安全なマシンを設定する場合は、ネットワーク管理者に問い合わせて、さらにサポートが必要な場合は、

オペレーティングシステムソフトウェアの更新とアップグレードを強くお勧めします。 これらのアップグレードにより、セキュリティとソフトウェアの修正が行われ、今後の問題を回避できる可能性があります。 これが何を意味するか分からない？ 以下をご確認ください。 [インストールの概要ページ](../overview.md).

を使用して、次のコマンドをユーザーとして入力します。 `root` 権限：

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

Adobe CommerceとMagento Open Sourceは Apache バージョン 2.4 をサポートしています。サポートの結果は次のようになります。

```terminal
Server version: Apache/2.4.0 (Unix)
Server built:   Jul 23 2017 14:17:29
```

Apache をインストールまたはアップグレードするには、 [Apache](web-server/apache.md).

### PHP

詳しくは、 [システム要件](../system-requirements.md) （PHP およびのサポート対象バージョンの場合） [PHP] PHP の要件に関する情報。

### MySQL

```bash
mysql -u <database root user or database owner name> -p
```

例：

```bash
mysql -u magento -p
```

インストールするAdobe CommerceまたはMagento Open Source([サポートされているバージョンについては、こちらを参照してください。](../system-requirements.md). 次の結果は、実行中のバージョンを示します )。

```terminal
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 871
Server version: 5.7.9 MySQL Community Server (GPL)

Copyright (c) 2000, 2019, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.
```

タイプ `help` または `\h` を参照してください。 タイプ `\c` 現在の入力文をクリアするには、をクリックします。

入力 `exit` 時刻： `mysql>` 終了するプロンプトが表示されます。

MySQL をインストールまたはアップグレードするには、 [MySQL](database/mysql.md).

### 検索エンジン

OpenSearch のインストールを確認するには、次の手順に従います。

```bash
curl -XGET '<opensearch-hostname>:<opensearch-port>'
```

インストールをElasticsearchするには：

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
