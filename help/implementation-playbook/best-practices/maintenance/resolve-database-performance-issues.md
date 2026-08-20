---
title: データベースのパフォーマンスの問題を解決するためのベストプラクティス
description: クラウドインフラストラクチャにデプロイされたAdobe Commerce Sitesでパフォーマンスが低下するデータベースの問題を修正する方法について説明します。
role: Developer, Admin
feature: Best Practices
exl-id: e40e0564-a4eb-43a8-89dd-9f6c5cedb4a7
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 0%

---

<!--Consider moving this topic to the Maintenance section-->

# データベースのパフォーマンスの問題を解決するためのベストプラクティス

この記事では、Adobe Commerceのクラウドインフラストラクチャサイトでデータベースのパフォーマンスに悪影響を与えるデータベースの問題を修正する方法について説明します。

## 影響のあるバージョン

Adobe Commerce on cloud infrastructure

## 長時間実行中のクエリの特定と解決

MySQL クエリの実行が遅いかどうかを確認します。 Adobe Commerce on cloud インフラストラクチャのプランと利用可能なツールに応じて、次の操作を行うことができます。

### MySQLによるデータベースクエリの分析

MySQLを使用すると、任意のAdobe Commerce on cloud インフラストラクチャプロジェクトで長時間実行中のクエリを特定して解決できます。

1. [`SHOW \[FULL\] PROCESSLIST`](https://dev.mysql.com/doc/refman/8.0/en/show-processlist.html) ステートメントを実行します。
1. 実行中のクエリが長い場合は、それぞれに[MySQL `EXPLAIN`と`EXPLAIN ANALYZE`](https://mysqlserverteam.com/mysql-explain-analyze/)を実行して、クエリが長時間実行される理由を確認します。
1. 見つかった問題に基づいて、クエリをより迅速に実行できるように修正する手順を実行します。

### Percona Toolkitを使用したクエリの分析（Pro アーキテクチャのみ）

Adobe Commerce プロジェクトがPro アーキテクチャにデプロイされている場合は、Percona Toolkitを使用してクエリを分析できます。

1. MySQLの低速クエリログに対して`pt-query-digest --type=slowlog` コマンドを実行します。
   * 低速なクエリログの場所については、開発者ドキュメントの&#x200B;**[!UICONTROL Log locations > Service Logs]** （https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/test/log-locations#service-logs）を参照してください。
   * [Percona Toolkit > pt-query-digest](https://www.percona.com/doc/percona-toolkit/LATEST/pt-query-digest.html#pt-query-digest) ドキュメントを参照してください。
1. 見つかった問題に基づいて、クエリをより迅速に実行できるように修正する手順を実行します。

## すべてのテーブルにプライマリキーがあることを確認します

プライマリキーの定義は、適切なデータベースとテーブルの設計に必要です。 プライマリキーを使用すると、任意のテーブル内の1つの行を一意に識別できます。

プライマリキーのないテーブルがある場合、Adobe Commerce（InnoDB）のデフォルトのデータベースエンジンでは、最初の一意のヌルキーがプライマリキーとして使用されます。 一意のキーがない場合、InnoDBは非表示のプライマリキー（6 バイト）を作成します。 暗黙的に定義されたプライマリキーの問題は、そのキーを制御できないことです。 さらに、プライマリキーを持たないすべてのテーブルに対して、暗黙的な値がグローバルに割り当てられます。 この設定では、これらのテーブルに対して同時に書き込みを実行すると、競合の問題が発生する可能性があります。 これは、テーブルがグローバルな非表示のプライマリキーインデックスの増分も共有するため、パフォーマンスの問題につながる可能性があります。

プライマリキーを持たないテーブルに対してプライマリキーを定義することで、これらの問題を防止します。

### プライマリキーを使用せずにテーブルを識別および更新する

1. 次のSQL クエリを使用して、プライマリキーを持たないテーブルを識別します。

   ```sql
   SELECT table_catalog, table_schema, table_name, engine FROM information_schema.tables        WHERE (table_catalog, table_schema, table_name) NOT IN (SELECT table_catalog, table_schema, table_name FROM information_schema.table_constraints  WHERE constraint_type = 'PRIMARY KEY') AND table_schema NOT IN ('information_schema', 'pg_catalog');    
   ```

1. プライマリキーが見つからないテーブルの場合は、次のようなノードで`db_schema.xml` （宣言型スキーマ）を更新してプライマリキーを追加します。

   ```html
   <constraint xsi:type="primary" referenceId="PRIMARY">         <column name="id_column"/>     </constraint>    
   ```

   ノードを追加する場合は、`referenceID`変数と`column name`変数をカスタムカスタム値に置き換えます。

詳しくは、開発者ドキュメントの[宣言スキーマの設定](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration)を参照してください。

## 重複するインデックスの特定と削除

データベース内の重複するインデックスを特定して削除します。

### 重複するインデックスの確認

Proまたはスタータークラウドアーキテクチャで重複するインデックスを確認するには、次のSQL クエリを実行します。

```sql
SELECT s.INDEXED_COL,GROUP_CONCAT(INDEX_NAME) FROM (SELECT INDEX_NAME,GROUP_CONCAT(CONCAT(TABLE_NAME,'.',COLUMN_NAME) ORDER BY CONCAT(SEQ_IN_INDEX,COLUMN_NAME)) 'INDEXED_COL' FROM INFORMATION_SCHEMA.STATISTICS WHERE TABLE_SCHEMA = 'db?' GROUP BY INDEX_NAME)as s GROUP BY INDEXED_COL HAVING COUNT(1)>1
```

クエリは、重複するインデックスの列名と名前を返します。

Pro アーキテクチャのマーチャントは、Percona Toolkit `[pt-duplicate-key checker](https://www.percona.com/doc/percona-toolkit/LATEST/pt-duplicate-key-checker.html%C2%A0)` コマンドを使用してチェックを実行することもできます。

### 重複したインデックスの削除

SQL [DROP INDEX ステートメント ](https://dev.mysql.com/doc/refman/8.0/en/drop-index.html)を使用して、重複するインデックスを削除します。

```SQL
DROP INDEX
```

## 追加情報

[クラウド デプロイメントのデータベース設定のベストプラクティス](../planning/database-on-cloud.md)
