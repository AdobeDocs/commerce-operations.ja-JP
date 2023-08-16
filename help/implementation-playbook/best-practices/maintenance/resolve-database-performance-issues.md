---
title: データベースのパフォーマンスの問題を解決するためのベストプラクティス
description: クラウドインフラストラクチャにデプロイされたAdobe Commerceサイトのパフォーマンスが低下するデータベースの問題を修正する方法について説明します。
role: Developer, Admin
feature: Best Practices
exl-id: e40e0564-a4eb-43a8-89dd-9f6c5cedb4a7
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---

<!--Consider moving this topic to the Maintenance section-->

# データベースのパフォーマンスの問題を解決するためのベストプラクティス

この記事では、クラウドインフラストラクチャサイト上のAdobe Commerceでのデータベースのパフォーマンスに悪影響を与えるデータベースの問題を修正する方法について説明します。

## 影響を受けるバージョン

Adobe Commerce an cloud infrastructure

## 長時間実行されるクエリを特定して解決する

MySQL クエリの実行に時間がかかっているかどうかを判断します。 クラウドインフラストラクチャのAdobe Commerceの計画とツールの可用性に応じて、次の操作を実行できます。

### MySQL でのデータベースクエリの分析

MySQL を使用して、クラウドインフラストラクチャプロジェクト上の任意のAdobe Commerceに関する長時間実行されるクエリを識別し、解決できます。

1. を実行します。 [`SHOW \[FULL\] PROCESSLIST`](https://dev.mysql.com/doc/refman/8.0/en/show-processlist.html) ステートメント。
1. 長時間実行されるクエリが表示される場合は、を実行します。 [MySQL `EXPLAIN` および `EXPLAIN ANALYZE`](https://mysqlserverteam.com/mysql-explain-analyze/) 各クエリに対して、何が長時間クエリを実行するのかを調べるために使用します。
1. 検出された問題に基づいて、クエリをより迅速に実行できるように修正する手順を実行します。

### Percona Toolkit を使用したクエリの分析（Pro アーキテクチャの場合のみ）

Adobe Commerceプロジェクトが Pro アーキテクチャにデプロイされている場合は、Percona Toolkit を使用してクエリを分析できます。

1. を実行します。 `pt-query-digest --type=slowlog` コマンドを MySQL の低速クエリログに対して実行します。
   * 処理に時間のかかるクエリログの場所については、 **[!UICONTROL Log locations > Service Logs]**(https://devdocs.magento.com/cloud/project/log-locations.html#service-logs) を開発者向けドキュメントに追加しました。
   * 詳しくは、 [Percona Toolkit > pt-query-digest](https://www.percona.com/doc/percona-toolkit/LATEST/pt-query-digest.html#pt-query-digest) ドキュメント。
1. 検出された問題に基づいて、クエリをより迅速に実行できるように修正する手順を実行します。

## すべてのテーブルにプライマリキーが設定されていることを確認します。

プライマリキーの定義は、データベースとテーブルのデザインを適切に行うための要件です。 プライマリキーを使用すると、任意のテーブル内の 1 つの行を一意に識別できます。

主キーのないテーブルがある場合、Adobe Commerce(InnoDB) のデフォルトのデータベースエンジンでは、最初の一意の null でないキーが主キーとして使用されます。 一意のキーを使用できない場合、InnoDB は隠しプライマリキー（6 バイト）を作成します。 暗黙的に定義されたプライマリキーに関する問題は、そのキーを制御できないことです。 さらに、暗黙的な値は、プライマリキーのないすべてのテーブルに対してグローバルに割り当てられます。 この設定では、これらのテーブルに対して同時書き込みを実行すると、競合の問題が発生する可能性があります。 これにより、テーブルはグローバルな非表示プライマリキーインデックスの増分も共有するので、パフォーマンスの問題が発生する可能性があります。

これらの問題を回避するには、存在しないテーブルのプライマリキーを定義します。

### 主キーを持たないテーブルの識別と更新

1. 次の SQL クエリを使用して、主キーのないテーブルを識別します。

   ```sql
   SELECT table_catalog, table_schema, table_name, engine FROM information_schema.tables        WHERE (table_catalog, table_schema, table_name) NOT IN (SELECT table_catalog, table_schema, table_name FROM information_schema.table_constraints  WHERE constraint_type = 'PRIMARY KEY') AND table_schema NOT IN ('information_schema', 'pg_catalog');    
   ```

1. プライマリキーが見つからないテーブルに対して、 `db_schema.xml` （宣言スキーマ）に次のようなノードが含まれます。

   ```html
   <constraint xsi:type="primary" referenceId="PRIMARY">         <column name="id_column"/>     </constraint>    
   ```

   ノードを追加する際に、 `referenceID` および `column name` 変数とカスタム値を組み合わせることができます。

詳しくは、 [宣言スキーマの設定](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) （開発者向けドキュメント）。

## 重複したインデックスの識別と削除

データベース内の重複インデックスを特定し、それらを削除します。

### 重複インデックスの確認

Pro または Starter クラウドアーキテクチャで重複インデックスを確認するには、次の SQL クエリを実行します。

```sql
SELECT s.INDEXED_COL,GROUP_CONCAT(INDEX_NAME) FROM (SELECT INDEX_NAME,GROUP_CONCAT(CONCAT(TABLE_NAME,'.',COLUMN_NAME) ORDER BY CONCAT(SEQ_IN_INDEX,COLUMN_NAME)) 'INDEXED_COL' FROM INFORMATION_SCHEMA.STATISTICS WHERE TABLE_SCHEMA = 'db?' GROUP BY INDEX_NAME)as s GROUP BY INDEXED_COL HAVING COUNT(1)>1
```

クエリは、列名と重複するインデックスの名前を返します。

Pro アーキテクチャのマーチャントも、Percona Toolkit を使用してチェックを実行できます。  `[pt-duplicate-key checker](https://www.percona.com/doc/percona-toolkit/LATEST/pt-duplicate-key-checker.html%C2%A0)` コマンドを使用します。

### 重複インデックスの削除

SQL を使用 [DROP INDEX 文](https://dev.mysql.com/doc/refman/8.0/en/drop-index.html) 重複インデックスを削除します。

```SQL
DROP INDEX
```

## 追加情報

[クラウドデプロイメントのデータベース設定のベストプラクティス](../planning/database-on-cloud.md)
