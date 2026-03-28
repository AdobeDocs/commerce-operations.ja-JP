---
title: データベーステーブルの修正に関するベストプラクティス
description: Adobe Commerceおよびサードパーティのデータベーステーブルを変更する方法とタイミングについて説明します。
role: Developer
feature: Best Practices
last-substantial-update: 2022-11-15T00:00:00Z
exl-id: 9e7adaaa-b165-4293-aa98-5dc4b8c23022
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '1509'
ht-degree: 0%

---

# データベーステーブルの修正に関するベストプラクティス

この記事では、[!DNL Adobe Commerce]またはサードパーティのモジュールによって作成されたデータベース テーブルを修正するためのベストプラクティスについて説明します。 テーブルを効果的に変更するタイミングと方法を把握することは、コマースプラットフォームの長期的な存続可能性と安定性を確保するのに役立ちます。

[!DNL Magento 1]やその他のe コマース プラットフォームから移行する場合、または[!DNL Adobe Commerce] Marketplaceからモジュールを操作する場合は、追加のデータを追加して保存する必要があります。 最初の感覚としては、データベースのテーブルに列を追加することや、既存のテーブルを調整することなどが考えられます。 ただし、コア [!DNL Adobe Commerce] テーブル（またはサードパーティのベンダーテーブル）は、限られた状況でのみ変更する必要があります。

## Adobeで修正を避けることをお勧めします

コアテーブルの変更を避ける主な理由は、Adobe Commerceに生のSQL クエリを含む基になるロジックが含まれていることです。 テーブルの構造を変更すると、予期しない副作用が発生する可能性があり、トラブルシューティングが困難です。 この変更は、DDL （Data Definition Language）操作にも影響し、パフォーマンスに予期しない影響を与える可能性があります。

データベーステーブル構造の変更を避けるもう1つの理由は、コア開発チームまたはサードパーティの開発者がデータベーステーブルの構造を変更した場合、変更が問題を引き起こす可能性があることです。 例えば、`additional_data`という列を持つコアデータベーステーブルがいくつかあります。 これは常に`text`列タイプです。 ただし、パフォーマンス上の理由から、コアチームは列を`longtext`に変更する場合があります。 このタイプの列は、JSONのエイリアスです。 この列タイプに変換すると、その列にパフォーマンスの向上と検索性が追加されますが、これは`text` タイプとしては存在しません。 このトピックについて詳しくは、[JSON データタイプ &#x200B;](https://mariadb.com/kb/en/json-data-type/){target="_blank"}を参照してください。

## データを保存または削除するタイミングを把握

Adobeでは、まず、このデータを保存する必要があるかどうかを判断することをお勧めします。 レガシーシステムからデータを移行する場合、削除できるデータはすべて、移行時の時間と労力を節約します。 （後でアクセスする必要がある場合は、データをアーカイブする方法があります）。 申し込みやパフォーマンスをしっかりと管理するために、追加データの保存をリクエストすることもできます。 目標は、データの保存が、他の方法では満たすことができないビジネスニーズを満たすための要件であることを確認することです。

### レガシーデータ

古い注文や顧客レコードなどの古いデータがプロジェクトに含まれている場合は、別の検索方法を検討してください。 例えば、時折参照するためだけにデータにアクセスする必要がある場合は、古いデータを[!DNL Adobe Commerce]に移行する代わりに、コマースプラットフォーム外部でホストされている古いデータベースの外部検索を実装することを検討してください。

この状況では、データベースをサーバーに移行し、データを読み取るためのweb インターフェイスを提供するか、MySQL Workbenchまたは同様のツールの使用に関するトレーニングを行う必要があります。 新しいデータベースからこのデータを除外すると、開発チームがデータ移行の問題をトラブルシューティングするのではなく、新しいサイトに集中できるようにすることで、移行を迅速化できます。

データをコマースの外部に保管し、リアルタイムで使用できるようにするもうひとつの関連する選択肢は、GraphQL meshなどの他のツールを活用することです。 このオプションは、異なるデータソースを組み合わせて、1つの応答として返します。

例えば、外部データベース（廃止予定の旧Magento 1 サイトなど）からの古い注文を`stitch`まとめることができます。 次に、GraphQL meshを使用して、お客様の注文履歴の一部として表示します。 これらの古い注文は、現在の[!DNL Adobe Commerce]環境の注文と組み合わせることができます。

GraphQLでのAPI メッシュの使用について詳しくは、[API Mesh](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/){target="_blank"}とは何か）および[GraphQL Mesh Gateway](https://developer.adobe.com/graphql-mesh-gateway/){target="_blank"}を参照してください。

## 拡張機能の属性を使用したレガシーデータの移行

従来のデータを移行する必要がある、または新しいデータを[!DNL Adobe Commerce]に保存する必要があると判断した場合、Adobeでは[拡張機能の属性](https://developer.adobe.com/commerce/php/development/components/add-attributes/){target="_blank"}を使用することをお勧めします。 拡張機能の属性を使用して追加データを保存すると、次のメリットが得られます。

- 永続化するデータとデータベース構造を制御できます。これにより、データは正しい列タイプと適切なインデックスで保存されます。
- [!DNL Adobe Commerce]のほとんどのエンティティでは、拡張機能の属性の使用がサポートされています。
- 拡張機能の属性は、プロジェクトに最適な場所にデータを保存する柔軟性を提供する、ストレージに依存しないメカニズムです。

ストレージの場所の例として、データベーステーブルと[!DNL Redis]が2つあります。 場所を選択する際に考慮すべき重要なことは、場所が余分な複雑さを引き起こすのか、パフォーマンスに影響を与えるのかということです。

### 他の選択肢を検討する

開発者は、GraphQL meshやAdobe App Builderなど、[!DNL Adobe Commerce]環境以外のツールの使用を常に検討することが重要です。 これらのツールは、データへのアクセスを維持するのに役立ちますが、コアコマースアプリケーションやその基盤となるデータベーステーブルには影響を与えません。 このアプローチでは、APIを通じてデータを公開します。 次に、App Builder設定にデータソースを追加します。 GraphQL Meshを使用すると、これらのデータソースを組み合わせて、[従来のデータ &#x200B;](#legacy-data)で説明したように1つの応答を生成できます。

GraphQL メッシュの詳細については、[GraphQL Mesh Gateway](https://developer.adobe.com/graphql-mesh-gateway/){target="_blank"}を参照してください。 Adobe App Builderについて詳しくは、[App Builderの概要](https://experienceleague.adobe.com/docs/adobe-developers-live-events/events/2021/oct2021/introduction-app-builder.html?lang=ja){target="_blank"}を参照してください。

## コアテーブルまたはサードパーティテーブルの変更

コア [!DNL Adobe Commerce]またはサードパーティ モジュール データベース テーブルを変更してデータを保存する場合は、次のガイドラインを使用して、安定性とパフォーマンスへの影響を最小限に抑えます。

- 新しい列のみを追加します。
- 既存の列の&#x200B;_type_&#x200B;値を変更しないでください。 例えば、固有のユースケースを満たすために、`integer`を`varchar`に変更しないでください。
- EAV属性テーブルに列を追加しないでください。 これらのテーブルには、既にロジックと責任がオーバーロードされています。
- 表を調整する前に、そのサイズを決定します。 大きなテーブルを変更すると、デプロイメントに影響が及び、変更が適用されるときに数分または数時間の遅延が発生する場合があります。

## 外部データベーステーブルを修正するためのベストプラクティス

コアのデータベーステーブルまたはサードパーティのテーブルに列を追加する場合、Adobeでは次の手順を実行することをお勧めします。

1. 更新内容を表す名前を名前空間内に持つモジュールを作成します。

   例：`app/code/YourCompany/Customer`

1. モジュールを有効にする適切なファイルを作成します（[&#x200B; モジュールの作成](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/create-module.html?lang=ja){target="_blank"}を参照）。

1. `db_schema.xml` フォルダーに`etc`という名前のファイルを作成し、適切な変更を行います。

   該当する場合は、`db_schema_whitelist.json` ファイルを生成します。 詳しくは、[宣言型スキーマ &#x200B;](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/){target="_blank"}を参照してください。

### 潜在的な影響

外部データベースに列を追加すると、次の点でAdobe Commerce プロジェクトに影響を与える可能性があります。

- アップグレードはより複雑になる可能性があります。
- 変更するテーブルが大きい場合、デプロイメントは影響を受けます。
- 新しいプラットフォームへの移行は、より複雑になる可能性があります。

## コアテーブルの変更を避ける方法

Adobe Commerce データベーステーブルの変更は、[拡張属性](#migrate-legacy-data-with-extension-attributes)を使用することで避けることができます。 もう1つの代替方法は、いくつかのコアテーブルにある特別な列（`additional_data`）を使用してデータを保存し、JSON エンコード形式で保存することです。

### JSON エンコードされたデータ列にデータを保存する

一部のコアテーブルには、JSON エンコードされたデータを保持する`additional_data`列があります。 この列では、1つのフィールドに追加データをマッピングするネイティブな方法を提供します。 この方法を使用すると、検索要件なしでデータ検索用の情報を格納する、小さなシンプルなデータ要素にテーブルを追加する必要がなくなります。 `additional_data`列は通常、見積もり全体または注文全体ではなく、品目レベルでのみ使用できます。

- `additional_data` フィールドを使用する利点

   - 追加のフィールドは必要ありません。これにより、列数を最小限に抑えることができます。 これは、既に多くのテーブルが含まれているセールスフローで役立ちます。 この複雑なプロセスに複雑な問題を追加しないことをお勧めします。 この方法は、多くのユースケースを満たしていますが、すべてを満たすわけではありません。

- 欠点

   - この方法は、読み取り専用データを保存する場合にのみ最適です。 この問題は、依存関係またはデータベース関係を追加するために、オブジェクトを変更および構築するためにコードをシリアル化しない必要があるため発生します。

   - データベース操作を使用してこれらのフィールドを検索するのは困難です。 この方法での検索は遅くなります。

   - 無効なJSONを作成したり、実行時に読み取りエラーを引き起こしたりしてコードが破損する可能性があるシリアル化またはシリアル化解除操作をトリガーしないように、`additional_data`列にデータを保存する場合は、細心の注意を払う必要があります。

   - これらのフィールドは、開発者が簡単に見つけられるように、コード内で明確に宣言する必要があります。

   - その他、診断が非常に難しい問題も発生する可能性があります。 例えば、一部のネイティブ PHP関数では、コアアプリケーションが提供する[!DNL Adobe Commerce] ラッパーメソッドを使用しない場合、変換データの最終結果が期待される形式と異なる可能性があります。 ラッパー関数を常に使用して、保存または取得されるデータの一貫性と予測可能性を確保します。

次に、`additional_data`列の列と構造を持つテーブルの例を示します。

```mysql
MariaDB [main]> DESCRIBE quote_item additional_data;
+-----------------+------+------+-----+---------+-------+
| Field           | Type | Null | Key | Default | Extra |
+-----------------+------+------+-----+---------+-------+
| additional_data | text | YES  |     | NULL    |       |
+-----------------+------+------+-----+---------+-------+
1 row in set (0.001 sec)


MariaDB [main]> DESCRIBE sales_order_item additional_data;
+-----------------+------+------+-----+---------+-------+
| Field           | Type | Null | Key | Default | Extra |
+-----------------+------+------+-----+---------+-------+
| additional_data | text | YES  |     | NULL    |       |
+-----------------+------+------+-----+---------+-------+
1 row in set (0.001 sec)
```

バージョン 2.4.3、2.4.4、および2.4.5には、列`additional_data`を持つ10個のテーブルがあります。

```mysql
MariaDB [magento]> SELECT DISTINCT TABLE_NAME FROM INFORMATION_SCHEMA.COLUMNS WHERE COLUMN_NAME IN ('additional_data') AND TABLE_SCHEMA='main';
+------------------------+
| TABLE_NAME             |
+------------------------+
| sales_shipment_item    |
| sales_creditmemo_item  |
| sales_invoice_item     |
| catalog_eav_attribute  |
| sales_order_payment    |
| quote_address_item     |
| quote_payment          |
| quote_item             |
| magento_reward_history |
| sales_order_item       |
+------------------------+
10 rows in set (0.020 sec)
```

## 大きなMySQL テーブルの検索

大きなテーブルを識別するには、[&#x200B; データベースへの接続](https://experienceleague.adobe.com/ja/docs/commerce-cloud-service/user-guide/configure/service/mysql#connect-to-the-database)記事の説明に従ってデータベースに接続し、次のコマンドを実行します。 実稼動環境には`project_id`を使用します。 ステージング環境の場合は、`[project_id]_stg`、`[project_id]_stg2`を使用します。

```sql
SELECT TABLE_NAME AS `Table`,
  ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM information_schema.TABLES
WHERE TABLE_SCHEMA = "<project_id>"
ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC
LIMIT 10;
```

これにより、最大10個のテーブルが表示されます。 さらにテーブルを表示する必要がある場合は、`LIMIT`を増やします。 制限なしで、コマンドは既存のすべてのテーブル（100を超える）を表示します。 また、各テーブルのサイズも表示されます。 リストを確認し、サイズに基づいて注意が必要なテーブルを特定できます。