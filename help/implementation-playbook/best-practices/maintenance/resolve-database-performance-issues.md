---
title: データベースのパフォーマンスの問題を解決するベストプラクティス
description: クラウドインフラストラクチャにデプロイされたAdobe Commerce サイトで、パフォーマンスが低下するデータベースの問題を修正する方法を説明します。
role: Developer, Admin
feature: Best Practices
exl-id: e40e0564-a4eb-43a8-89dd-9f6c5cedb4a7
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

<!--Consider moving this topic to the Maintenance section-->

# データベースのパフォーマンスの問題を解決するベストプラクティス

この記事では、クラウドインフラストラクチャサイト上のAdobe Commerceでデータベースのパフォーマンスに悪影響を与えるデータベースの問題を修正する方法について説明します。

## 影響を受けるバージョン

クラウドインフラストラクチャー上のAdobe Commerce

## 長時間実行中のクエリの特定と解決

MySQL クエリの実行が遅いかどうかを確認します。 クラウドインフラストラクチャプランのAdobe Commerceとその利用可能なツールに応じて、次の操作を実行できます。

### MySQL でのデータベースクエリの分析

MySQL を使用すると、クラウドインフラストラクチャプロジェクト上のAdobe Commerceに対して長時間実行中のクエリを特定して解決できます。

1. [`SHOW \[FULL\] PROCESSLIST`](https://dev.mysql.com/doc/refman/8.0/en/show-processlist.html) ステートメントを実行します。
1. クエリの実行時間が長い場合は、クエリごとに [MySQL `EXPLAIN` と `EXPLAIN ANALYZE`](https://mysqlserverteam.com/mysql-explain-analyze/) を実行して、クエリが長時間実行される原因を調べます。
1. 見つかった問題に基づいて、クエリがより迅速に実行されるように、クエリを修正する手順を実行します。

### Percona Toolkit を使用したクエリの分析（Pro アーキテクチャのみ）

Adobe Commerce プロジェクトが Pro アーキテクチャにデプロイされている場合は、Percona Toolkit を使用してクエリを分析できます。

1. MySQL の低速クエリログに対して `pt-query-digest --type=slowlog` コマンドを実行します。
   * 処理に時間のかかるクエリログの場所については、開発者向けドキュメントの **[!UICONTROL Log locations > Service Logs]** （https://experienceleague.adobe.com/ja/docs/commerce-cloud-service/user-guide/develop/test/log-locations#service-logs）を参照してください。
   * [Percona Toolkit > pt-query-digest](https://www.percona.com/doc/percona-toolkit/LATEST/pt-query-digest.html#pt-query-digest) ドキュメントを参照してください。
1. 見つかった問題に基づいて、クエリがより迅速に実行されるように、クエリを修正する手順を実行します。

## すべてのテーブルにプライマリ・キーがあることを確認します。

プライマリキーの定義は、データベースとテーブルを適切に設計するための要件です。 プライマリキーを使用すると、任意のテーブル内の 1 つの行を一意に識別できます。

主キーのないテーブルがある場合、Adobe Commerceのデフォルトのデータベースエンジン（InnoDB）では、最初の一意の not null キーが主キーとして使用されます。 一意のキーがない場合、InnoDB は隠されたプライマリキー（6 バイト）を作成します。 暗黙的に定義されたプライマリキーの問題は、プライマリキーを制御できないことです。 さらに、暗黙の値は、プライマリキーのないすべてのテーブルに対してグローバルに割り当てられます。 この構成では、これらのテーブルに同時書き込みを実行すると、競合の問題が発生する可能性があります。 テーブルはグローバルな非表示プライマリ・キー・インデックス増分も共有するため、パフォーマンスの問題が発生する可能性があります。

テーブルにプライマリキーがない場合は、プライマリキーを定義することで、これらの問題を防ぐことができます。

### プライマリキーのないテーブルの識別と更新

1. 次の SQL クエリを使用して、プライマリキーのないテーブルを識別します。

   ```sql
   SELECT table_catalog, table_schema, table_name, engine FROM information_schema.tables        WHERE (table_catalog, table_schema, table_name) NOT IN (SELECT table_catalog, table_schema, table_name FROM information_schema.table_constraints  WHERE constraint_type = 'PRIMARY KEY') AND table_schema NOT IN ('information_schema', 'pg_catalog');    
   ```

1. プライマリキーがないテーブルの場合は、`db_schema.xml` （宣言型スキーマ）を次のようなノードで更新して、プライマリキーを追加します。

   ```html
   <constraint xsi:type="primary" referenceId="PRIMARY">         <column name="id_column"/>     </constraint>    
   ```

   ノードを追加する際は、`referenceID` 変数と `column name` 変数をカスタムのカスタム値に置き換えます。

詳しくは、開発者向けドキュメントの [ 宣言型スキーマの設定 ](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) を参照してください。

## 重複するインデックスの特定と削除

データベース内の重複するインデックスを特定して削除します。

### 重複するインデックスのチェック

Pro または Starter クラウドアーキテクチャで重複したインデックスをチェックするには、次の SQL クエリを実行します。

```sql
SELECT s.INDEXED_COL,GROUP_CONCAT(INDEX_NAME) FROM (SELECT INDEX_NAME,GROUP_CONCAT(CONCAT(TABLE_NAME,'.',COLUMN_NAME) ORDER BY CONCAT(SEQ_IN_INDEX,COLUMN_NAME)) 'INDEXED_COL' FROM INFORMATION_SCHEMA.STATISTICS WHERE TABLE_SCHEMA = 'db?' GROUP BY INDEX_NAME)as s GROUP BY INDEXED_COL HAVING COUNT(1)>1
```

クエリを実行すると、列名と、重複するインデックスの名前が返されます。

Pro アーキテクチャマーチャントは、Percona Toolkit `[pt-duplicate-key checker](https://www.percona.com/doc/percona-toolkit/LATEST/pt-duplicate-key-checker.html%C2%A0)` コマンドを使用してチェックを実行することもできます。

### 重複するインデックスの削除

SQL [DROP INDEX ステートメント ](https://dev.mysql.com/doc/refman/8.0/en/drop-index.html) を使用して、重複するインデックスを削除します。

```SQL
DROP INDEX
```

## 追加情報

[クラウドデプロイメントにおけるデータベース設定のベストプラクティス](../planning/database-on-cloud.md)
