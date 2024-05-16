---
title: クラウドデプロイメントにおけるデータベース設定のベストプラクティス
description: Adobe Commerceをクラウドインフラストラクチャーにデプロイする際に、パフォーマンスを向上させるためにデータベースとアプリケーションを設定する方法について説明します。
role: Developer, Admin
feature: Best Practices
exl-id: ca377dc8-c8bd-4f77-a24b-22a298e2bba4
source-git-commit: fb449f0ee7d503d0c7ba60bf6bfbe3f528060606
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 0%

---

# データベース設定のベストプラクティス

クラウドインフラストラクチャーにAdobe Commerceをデプロイする際に、データベースのパフォーマンスを向上させ、データベースを効率的に操作するためのベストプラクティスについて説明します。

## 対象製品

クラウドインフラストラクチャー上のAdobe Commerce

## すべての MyISAM テーブルを InnoDB に変換する

Adobeでは、InnoDB データベースエンジンを使用することをお勧めします。 デフォルトのAdobe Commerce インストールでは、データベース内のすべてのテーブルが InnoDB エンジンを使用して格納されます。 ただし、一部のサードパーティモジュール（拡張機能）では、MyISAM 形式のテーブルを導入できます。 サードパーティ製モジュールをインストールしたら、データベースをチェックして次のテーブルを識別します `myisam` 形式を設定して次のように変換します `innodb` 形式。

### モジュールに MyISAM テーブルが含まれているかどうかの確認

インストールする前にサードパーティのモジュールコードを分析して、MyISAM テーブルを使用しているかどうかを判断できます。

すでに拡張機能をインストールしている場合は、次のクエリを実行して、データベースに MyISAM テーブルがあるかどうかを確認します。

```sql
SELECT table_schema, CONCAT(ROUND((index_length+data_length)/1024/1024),'MB')
    AS total_size FROM information_schema. TABLES WHERE engine='myisam' AND table_schema
    NOT IN ('mysql', 'information_schema', 'performance_schema', 'sys');
```

### ストレージエンジンを InnoDB に変更する

が含まれる `db_schema.xml` テーブルを宣言するファイルで、 `engine` 対応するの属性値 `table` ノード先 `innodb`. 詳しくは、を参照してください [宣言型スキーマ/テーブルノードを設定](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) 開発者向けドキュメントを参照してください。

宣言型スキームは、クラウドインフラストラクチャバージョン 2.3 上のAdobe Commerceで導入されました。

## ネイティブの MySQL 検索用に推奨される検索エンジンを設定

Adobeでは、Adobe Commerce アプリケーションにサードパーティの検索ツールを設定する予定がある場合でも、クラウドインフラストラクチャプロジェクトでAdobe Commerceに対して常にElasticsearchまたは OpenSearch を設定することをお勧めします。 この設定により、サードパーティの検索ツールでエラーが発生した場合に備えたフォールバックオプションが提供されます。

使用する検索エンジンは、インストールされているAdobe Commerce on cloud バージョンによって異なります。

- Adobe Commerce 2.4.4 以降では、ネイティブの MySQL 検索に OpenSearch サービスを使用します。

- 以前のバージョンのAdobe Commerceの場合は、Elasticsearchを使用します。

現在使用されている検索エンジンを確認するには、次のコマンドを実行します。

```bash
./bin/magento config:show catalog/search/engine
```

設定手順については、Adobe Commerce on cloud の開発者ガイドを参照してください。

- [OpenSearch サービスの設定](https://devdocs.magento.com/cloud/project/services-opensearch.html)

- [Elasticsearchサービスの設定](https://devdocs.magento.com/cloud/project/services-elastic.html)

## カスタムトリガーの回避

可能であれば、カスタムトリガーの使用は避けます。

トリガーは、変更を監査テーブルに記録するために使用されます。 Adobeは、次の理由から、トリガー機能を使用する代わりに、監査表に直接書き込むようにアプリケーションを設定することをお勧めします。

- トリガーはコードとして解釈され、MySQL は事前にコンパイルしません。 クエリのトランザクション領域にフックすると、テーブルで実行される各クエリのパーサーとインタープリターにオーバーヘッドが追加されます。
- トリガーは元の問い合わせと同じトランザクション領域を共有し、それらの問い合わせがテーブルのロックに競合する間、トリガーは別のテーブルのロックに独立して競合する。

カスタムトリガーの代替手段について詳しくは、を参照してください。 [MySQL トリガー](mysql-configuration.md#triggers).

## アップグレード [!DNL ECE-Tools] バージョン 2002.0.21 以降へ {#ece-tools-version}

Cron デッドロックの潜在的な問題を回避するには、ECE-Tools をバージョン 2002.0.21 以降にアップグレードしてください。 手順については、を参照してください [更新 `ece-tools` version](https://devdocs.magento.com/cloud/project/ece-tools-update.html) 開発者向けドキュメントを参照してください。

## インデクサーモードの安全な切り替え

<!--This best practice might belong in the Maintenance phase. Database lock prevention might be consolidated under a single heading-->

インデクサーの切り替えで生成されるもの [!DNL data definition language] （DDL）ステートメントを使用して、データベース・ロックの原因となる可能性のあるトリガーを作成します。 この問題を回避するには、web サイトをメンテナンスモードにし、設定を変更する前に cron ジョブを無効にします。
手順については、を参照してください [インデクサーの設定](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html#configure-indexers-1) が含まれる *Adobe Commerce設定ガイド*.

## 実稼動環境で DDL ステートメントを実行しない

競合（テーブルの変更や作成など）を防ぐために、実稼動環境では DDL ステートメントを実行しないでください。 この `setup:upgrade` プロセスは例外です。

DDL ステートメントを実行する必要がある場合は、web サイトをメンテナンスモードにして、cron を無効にします（前の節のインデックスを安全に切り替える手順を参照）。

## 注文のアーカイブを有効にする

管理者からの注文アーカイブを有効にして、注文データの増加に合わせてセールステーブルに必要なスペースを減らします。 アーカイブにより、MySQL のディスク領域が節約され、チェックアウトのパフォーマンスが向上します。

参照： [アーカイブを有効にする](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-archive.html) Adobe Commerce マーチャントドキュメントを参照してください。

## 追加情報

- [MySQL ストレージエンジン](https://dev.mysql.com/doc/refman/8.0/en/storage-engines.html)
- [MariaDB のAdobe Commerce 2.3.5 アップグレードの前提条件](../maintenance/mariadb-upgrade.md)
- [データベースのパフォーマンスの問題を解決するベストプラクティス](../maintenance/resolve-database-performance-issues.md)
