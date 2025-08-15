---
title: オンプレミスでのインストールの前提条件
description: Adobe Commerceのオンプレミスインストールに必要なソフトウェア依存関係について詳しく説明します。
exl-id: dd4694e7-5437-440c-bb67-804ae36149de
source-git-commit: db2256f5327897a4376a0d038ce697e8f93235af
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 1%

---

# オンプレミスでのインストールの前提条件

Adobe Commerceをインストールする前に、次の作業を行う必要があります。

* 「[Commerce オンプレミス ](../system-requirements.md)」タブに表示されている *システム要件* を満たす 1 つ以上のホストを設定します。
* ロードバランシングを使用して複数の web ノードを設定する場合は、システムのその部分を設定およびテストしてから _アプリケーションをインストール_ ます。
* 問題が発生した場合にロールバックできるように、インストール中の様々な時点でシステム全体をバックアップできることを確認してください。

>[!NOTE]
>
>ここでは、Adobe Commerceを **development environment** にインストールし、マシンへのルートユーザーアクセス権を持ち、マシンのセキュリティを高く保つ必要がない **ことを前提** しています。 より安全なマシンを設定する場合は、ネットワーク管理者に問い合わせてサポートを依頼することを強くお勧めします。

オペレーティングシステムのソフトウェアを更新およびアップグレードすることを強くお勧めします。 これらのアップグレードにより、将来の問題を防ぐためのセキュリティとソフトウェアの修正が提供される場合があります。 これは何を意味するのか分からない？ [ インストールの概要ページ ](../overview.md) をご覧ください。

`root` 権限を持つユーザーとして、次のコマンドを入力します。

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

```
Server version: Apache/2.4.0 (Unix)
Server built:   Jul 23 2017 14:17:29
```

Apache をインストールまたはアップグレードするには、[Apache](web-server/apache.md) を参照してください。

### PHP

PHP のサポート対象バージョンの要件については、** system requirements&rbrace; の [Commerce オンプレミス ](../system-requirements.md) タブを参照してください。また、PHP の要件については [PHP](../system-requirements.md#php-settings) を参照してください。

### MySQL

インストールしているAdobe Commerceのバージョンと互換性のある MySQL のバージョンがあることを確認します。 サポートされているバージョンについては、*システム要件* の「[Commerce オンプレミス ](../system-requirements.md)」タブを参照してください。

```bash
mysql -u <database root user or database owner name> -p
```

例：

```bash
mysql -u magento -p
```

次の結果は、実行しているバージョンを示しています。

```
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 871
Server version: 5.7.9 MySQL Community Server (GPL)

Copyright (c) 2000, 2019, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.
```

`help` または `\h` と入力してヘルプを表示します。 現在の入力文をクリアするには、`\c` と入力します。

`exit` プロンプトで `mysql>` と入力して終了します。

MySQL をインストールまたはアップグレードするには、[MySQL](database/mysql.md) を参照してください。

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

```
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
