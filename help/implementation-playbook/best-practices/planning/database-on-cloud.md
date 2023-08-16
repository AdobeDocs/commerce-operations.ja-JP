---
title: クラウドデプロイメントのデータベース設定のベストプラクティス
description: クラウドインフラストラクチャにAdobe Commerceをデプロイする際のパフォーマンスを向上させるために、データベースとアプリケーションの設定を構成する方法について説明します。
role: Developer, Admin
feature: Best Practices
exl-id: ca377dc8-c8bd-4f77-a24b-22a298e2bba4
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '687'
ht-degree: 0%

---

# データベース設定のベストプラクティス

クラウドインフラストラクチャにAdobe Commerceをデプロイする際に、データベースのパフォーマンスを向上し、データベースを効率的に操作するためのベストプラクティスについて説明します。

## 影響を受ける製品

Adobe Commerce an cloud infrastructure

## すべての MyISAM テーブルを InnoDB に変換

Adobeでは、InnoDB データベースエンジンの使用をお勧めします。 デフォルトのAdobe Commerceインストールでは、データベース内のすべてのテーブルは InnoDB エンジンを使用して格納されます。 ただし、一部のサードパーティモジュール（拡張）では、MyISAM 形式のテーブルを導入できます。 サードパーティ製モジュールをインストールした後、データベースをチェックして、 `myisam` 形式を設定して、 `innodb` 形式を使用します。

### モジュールに MyISAM テーブルが含まれているかどうかを確認します

インストール前にサードパーティのモジュールコードを分析し、MyISAM テーブルを使用しているかどうかを判断できます。

拡張機能が既にインストールされている場合は、次のクエリを実行して、データベースに MyISAM テーブルが存在するかどうかを判断します。

```sql
SELECT table_schema, CONCAT(ROUND((index_length+data_length)/1024/1024),'MB')
    AS total_size FROM information_schema. TABLES WHERE engine='myisam' AND table_schema
    NOT IN ('mysql', 'information_schema', 'performance_schema', 'sys');
```

### ストレージエンジンを InnoDB に変更

Adobe Analytics の `db_schema.xml` テーブルを宣言するファイル、 `engine` 対応する `table` ノードから `innodb`. 参照： [宣言スキーマ/テーブルノードの設定](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) （開発者向けドキュメント）。

この宣言スキームは、クラウドインフラストラクチャバージョン 2.3 のAdobe Commerceで導入されました。

## ネイティブ MySQL 検索に推奨される検索エンジンを設定する

Adobe Commerceアプリケーションにサードパーティの検索ツールを設定する予定がある場合でも、クラウドインフラストラクチャプロジェクト上でAdobe CommerceのElasticsearchまたは OpenSearch を常に設定することをお勧めします。 この設定は、サードパーティの検索ツールが失敗した場合に備えたフォールバックオプションを提供します。

使用する検索エンジンは、インストールされているクラウドバージョンに応じて、Adobe Commerceによって異なります。

- Adobe Commerce 2.4.4 以降では、ネイティブの MySQL 検索に OpenSearch サービスを使用します。

- 以前のバージョンのAdobe Commerceでは、Elasticsearchを使用します。

現在使用中の検索エンジンを判断するには、次のコマンドを実行します。

```bash
./bin/magento config:show catalog/search/engine
```

設定手順については、クラウド上のAdobe Commerceの開発者ガイドを参照してください。

- [OpenSearch サービスを設定する](https://devdocs.magento.com/cloud/project/services-opensearch.html)

- [Elasticsearchサービスの設定](https://devdocs.magento.com/cloud/project/services-elastic.html)

## カスタムトリガーの回避

可能な限り、カスタムトリガーを使用しないでください。

トリガーは、変更を監査テーブルに記録するために使用されます。 Adobeでは、次の理由により、アプリケーション機能を使用する代わりに、監査テーブルに直接書き込むようにトリガーを設定することをお勧めします。

- トリガーはコードとして解釈され、MySQL は事前にコンパイルしません。 クエリのトランザクションスペースに接続すると、テーブルで実行される各クエリに対して、パーサとインタプリタにオーバーヘッドが追加されます。
- トリガーは、元のクエリと同じトランザクション領域を共有し、これらのクエリがテーブルのロックを競合しますが、トリガーは別のテーブルのロックを個別に競合します。

カスタムトリガーの使用に代わる方法については、 [MySQLトリガーを効果的に使用](mysql-triggers-usage.md) をサポートナレッジベースに追加しました。

## アップグレード [!DNL ECE-Tools] をバージョン 2002.0.21 以降に変更 {#ece-tools-version}

cron デッドロックの潜在的な問題を回避するには、ECE-Tools をバージョン 2002.0.21 以降にアップグレードします。 手順については、 [更新 `ece-tools` version](https://devdocs.magento.com/cloud/project/ece-tools-update.html) （開発者向けドキュメント）。

## インデクサーモードを安全に切り替える

<!--This best practice might belong in the Maintenance phase. Database lock prevention might be consolidated under a single heading-->

インデクサーを切り替えると、 [!DNL data definition language] (DDL) ステートメントを使用して、データベース・ロックを引き起こすトリガーを作成します。 この問題を回避するには、Web サイトをメンテナンスモードにし、設定を変更する前に cron ジョブを無効にします。
手順については、 [インデクサーの設定](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html#configure-indexers-1) （内） *Adobe Commerce設定ガイド*.

## 実稼動環境で DDL ステートメントを実行しない

実稼動環境で DDL ステートメントを実行して、競合（テーブルの変更や作成など）を防ぎます。 The `setup:upgrade` プロセスは例外です。

DDL 文を実行する必要がある場合は、Web サイトをメンテナンスモードにし、cron を無効にします（前の節でインデックスを安全に切り替える手順を参照）。

## 注文のアーカイブを有効にする

管理者からの注文のアーカイブを有効にして、注文データが増えるにつれ、販売テーブルに必要な容量を削減します。 アーカイブは、MySQL のディスク領域を節約し、チェックアウトパフォーマンスを向上させます。

詳しくは、 [アーカイブを有効にする](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-archive.html) ( Adobe Commerce Merchant ドキュメント ) を参照してください。

## 追加情報

- [MySQL ストレージエンジン](https://dev.mysql.com/doc/refman/8.0/en/storage-engines.html)
- [Adobe Commerce 2.3.5 MariaDB のアップグレードの前提条件](../maintenance/commerce-235-upgrade-prerequisites-mariadb.md)
- [データベースのパフォーマンスの問題を解決するためのベストプラクティス](../maintenance/resolve-database-performance-issues.md)
