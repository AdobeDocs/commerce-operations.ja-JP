---
title: クラウド デプロイメントのデータベース設定のベストプラクティス
description: Adobe Commerceをクラウドインフラストラクチャにデプロイする際のパフォーマンスを向上させるために、データベースとアプリケーションの設定を行う方法について説明します。
role: Developer, Admin
feature: Best Practices
exl-id: ca377dc8-c8bd-4f77-a24b-22a298e2bba4
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 0%

---

# データベース設定のベストプラクティス

Adobe Commerceをクラウドインフラストラクチャにデプロイする際に、データベースのパフォーマンスを向上させ、データベースを効率的に操作するためのベストプラクティスについて説明します。

## 影響を受ける製品

Adobe Commerce on cloud infrastructure

## すべてのMyISAM テーブルをInnoDBに変換

Adobeでは、InnoDB データベースエンジンを使用することをお勧めします。 デフォルトのAdobe Commerce インストールでは、データベース内のすべてのテーブルがInnoDB エンジンを使用して保存されます。 ただし、一部のサードパーティモジュール（拡張機能）では、MyISAM形式のテーブルを導入できます。 サードパーティ製モジュールをインストールした後、データベースを確認して、`myisam`形式のテーブルを特定し、`innodb`形式に変換します。

### モジュールにMyISAM テーブルが含まれているかどうかを確認します

サードパーティ製モジュールコードをインストールする前に分析し、MyISAM テーブルを使用しているかどうかを判断できます。

拡張機能を既にインストールしている場合は、次のクエリを実行して、データベースにMyISAM テーブルがあるかどうかを判断します。

```sql
SELECT table_schema, CONCAT(ROUND((index_length+data_length)/1024/1024),'MB')
    AS total_size FROM information_schema. TABLES WHERE engine='myisam' AND table_schema
    NOT IN ('mysql', 'information_schema', 'performance_schema', 'sys');
```

### ストレージ エンジンをInnoDBに変更する

テーブルを宣言する`db_schema.xml` ファイルで、対応する`table` ノードの`engine`属性値を`innodb`に設定します。 参照については、開発者ドキュメントの[宣言スキーマの設定/テーブルノード ](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/)を参照してください。

宣言型スキームは、Adobe Commerce on cloud infrastructure バージョン 2.3で導入されました。

## ネイティブ MySQL検索用に推奨される検索エンジンを設定する

Adobeでは、Adobe Commerce アプリケーションのサードパーティ検索ツールを設定する予定がある場合でも、Adobe Commerce on cloud infrastructure プロジェクトに対して常にElasticsearchまたはOpenSearchを設定することをお勧めします。 この設定では、サードパーティ検索ツールが失敗した場合に備えて、フォールバックオプションを提供します。

使用する検索エンジンは、インストールされているAdobe Commerce on cloud バージョンによって異なります。

- Adobe Commerce 2.4.4以降では、ネイティブ MySQL検索にOpenSearch サービスを使用します。

- 以前のAdobe Commerce バージョンの場合は、Elasticsearchを使用します。

現在使用されている検索エンジンを特定するには、次のコマンドを実行します。

```shell
./bin/magento config:show catalog/search/engine
```

設定手順については、Adobe Commerce on cloudの開発者向けガイドを参照してください。

- [OpenSearch サービスの設定](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/opensearch)

- [Elasticsearch サービスの設定](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch)

## カスタムトリガーを避ける

可能であれば、カスタムトリガーの使用は避けます。

トリガーは、監査テーブルに変更を記録するために使用されます。 Adobeでは、次の理由から、トリガー機能を使用するのではなく、監査テーブルに直接書き込むようにアプリケーションを設定することをお勧めします。

- トリガーはコードとして解釈され、MySQLはそれらをプリコンパイルしません。 クエリのトランザクションスペースに接続すると、テーブルで実行された各クエリのオーバーヘッドがパーサーとインタープリターに追加されます。
- トリガーは、元のクエリと同じトランザクションスペースを共有し、それらのクエリがテーブル上のロックを競う一方で、トリガーは別のテーブルのロックを競います。

カスタムトリガーの使用に代わる方法については、[MySQL トリガー](mysql-configuration.md#triggers)を参照してください。

## [!DNL ECE-Tools]をバージョン 2002.0.21以降にアップグレード {#ece-tools-version}

クローンのデッドロックに関する潜在的な問題を回避するには、ECE-Toolsをバージョン 2002.0.21以降にアップグレードします。 手順については、開発者ドキュメントの「[ アップデート `ece-tools` バージョン ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package)」を参照してください。

## インデクサーモードを安全に切り替える

<!--This best practice might belong in the Maintenance phase. Database lock prevention might be consolidated under a single heading-->

インデックスを切り替えると、[!DNL data definition language] （DDL）ステートメントが生成され、データベースのロックの原因となるトリガーが作成されます。 この問題を回避するには、web サイトをメンテナンスモードにし、設定を変更する前にcron ジョブを無効にします。
手順については、*Adobe Commerce設定ガイド*&#x200B;の「[ インデックスを設定](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html#configure-indexers-1)」を参照してください。

## 実稼動環境でDDL ステートメントを実行しない

実稼動環境でDDL ステートメントを実行して、競合（テーブルの変更や作成など）を防ぐことは避けてください。 `setup:upgrade` プロセスは例外です。

DDL ステートメントを実行する必要がある場合は、web サイトをメンテナンスモードにし、cronを無効にします（前の節のインデックスを安全に切り替える手順を参照）。

## 注文アーカイブの有効化

管理者からの注文アーカイブを有効にして、注文データの増加に合わせてセールステーブルに必要なスペースを削減します。 アーカイブは、MySQL ディスク容量を節約し、チェックアウトのパフォーマンスを向上させます。

Adobe Commerce Merchant ドキュメントの[ アーカイブを有効にする](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-archive.html)を参照してください。

## 追加情報

- [MySQL ストレージエンジン](https://dev.mysql.com/doc/refman/8.0/en/storage-engines.html)
- [MariaDBのAdobe Commerce 2.3.5 アップグレードの前提条件](../maintenance/mariadb-upgrade.md)
- [データベースのパフォーマンスの問題を解決するためのベストプラクティス](../maintenance/resolve-database-performance-issues.md)
