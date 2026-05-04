---
title: オンプレミスのインストールの前提条件
description: Adobe Commerceのオンプレミスインストールに必要なソフトウェアの依存関係について詳しくは、こちらを参照してください。
exl-id: dd4694e7-5437-440c-bb67-804ae36149de
source-git-commit: 319f3232d1ba5f5ed7cdd10ce85b9d7ffbeec89a
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 1%

---

# オンプレミスのインストールの前提条件

Adobe Commerceをインストールする前に、次の操作を行う必要があります。

* 「*Commerce オンプレミス*」タブに記載されている[ システム要件](../system-requirements.md)を満たす1つ以上のホストを設定します。
* 負荷分散を使用して複数のweb ノードを設定する場合は、アプリケーションをインストールする&#x200B;_前_&#x200B;に、システムのその部分を設定してテストします。
* インストール中のさまざまな時点でシステム全体をバックアップして、問題が発生した場合にロールバックできるようにします。

>[!NOTE]
>
>マシンへのルートユーザーアクセス権を持つ&#x200B;**開発環境**&#x200B;にAdobe Commerceをインストールし、マシンのセキュリティを高く確保する必要がないことを&#x200B;**および**&#x200B;と仮定します。 より安全なマシンを設定する場合は、追加のサポートを得るためにネットワーク管理者に相談することを強くお勧めします。

オペレーティングシステムのソフトウェアを更新してアップグレードすることを強くお勧めします。 これらのアップグレードは、将来の問題を防ぐ可能性のあるセキュリティとソフトウェアの修正を提供します。 どういうことか分からない？ [ インストールの概要ページ ](../overview.md)をご覧ください。

`root`権限を持つユーザーとして次のコマンドを入力します。

* Ubuntu

  ```shell
  apt-get update
  ```

  ```shell
  apt-get upgrade
  ```

* CentOS

  ```shell
  yum -y update
  ```

  ```shell
  yum -y upgrade
  ```

## 前提条件チェック

システムに前提条件がないか確認するには、次のコマンドを入力します。

### Apache

CentOS: `httpd -v`

Ubuntu: `apache2 -v`

次の結果が示すように、Adobe CommerceはApache バージョン 2.4をサポートしています。

```text
Server version: Apache/2.4.0 (Unix)
Server built:   Jul 23 2017 14:17:29
```

Apacheをインストールまたはアップグレードするには、[Apache](web-server/apache.md)を参照してください。

### PHP

サポートされているバージョンのPHPについては[ システム要件](../system-requirements.md)の「*Commerce オンプレミス*」タブを、PHP要件については[PHP](../system-requirements.md#php-settings)を参照してください。

### MySQL

インストールするAdobe Commerceのバージョンと互換性のあるバージョンのMySQLがあることを確認します。 サポートされているバージョンについては、[ システム要件](../system-requirements.md)の「*Commerce オンプレミス*」タブを参照してください。

```shell
mysql -u <database root user or database owner name> -p
```

例：

```shell
mysql -u magento -p
```

コマンド出力では、`Server version`行は、実行中のバージョンを示します。 インストールするAdobe Commerce リリースでサポートされているバージョンと一致することを確認します。

```text
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 871
Server version: <supported MySQL version> MySQL Community Server (GPL)

Copyright (c) 2000, 2019, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.
```

`help`または`\h`を入力してヘルプを表示します。 現在の入力ステートメントをクリアするには、`\c`と入力します。

`mysql>` プロンプトに`exit`と入力して終了します。

MySQLをインストールまたはアップグレードするには、[MySQL](database/mysql.md)を参照してください。

### 検索エンジン

OpenSearchのインストールを確認するには：

```shell
curl -XGET '<opensearch-hostname>:<opensearch-port>'
```

Elasticsearchのインストールを確認するには：

```shell
curl -XGET '<elasticsearch-hostname>:<elasticsearch-port>'
```

例：

```shell
curl -XGET 'localhost:9200'
```

```json
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
