---
title: データベーステーブルを変更する際のベストプラクティス
description: Adobe Commerceおよびサードパーティのデータベーステーブルを変更する方法とタイミングについて説明します。
role: Developer, Architect
feature: Best Practices
feature-set: Commerce
last-substantial-update: 2022-11-15T00:00:00Z
source-git-commit: 570fa4877f578f636736f0404169ed215fd06b24
workflow-type: tm+mt
source-wordcount: '1469'
ht-degree: 0%

---

# データベーステーブルを変更する際のベストプラクティス

この記事では、 [!DNL Adobe Commerce] またはサードパーティモジュール テーブルを効果的に変更するタイミングと方法を理解することで、コマースプラットフォームの長期的な存続性と安定性を確保できます。

移行元 [!DNL Magento 1] 他の e コマースプラットフォーム、または [!DNL Adobe Commerce] Marketplace では、追加のデータの追加と保存が必要になる場合があります。 最初に、データベーステーブルに列を追加したり、既存の列を調整したりします。 ただし、コアのみを変更する必要があります [!DNL Adobe Commerce] 限られた状況でのテーブル（またはサードパーティベンダーテーブル）。

## Adobeが変更を避けることを推奨する理由

コアテーブルを変更しない主な理由は、生の SQL クエリを含む基礎となるロジックがAdobe Commerceに含まれていることです。 テーブルの構造を変更すると、予期しない副作用が発生し、トラブルシューティングが困難になる場合があります。 この変更は、DDL（データ定義言語）操作に影響を与え、パフォーマンスに予期しない予期しない影響を与える場合もあります。

データベーステーブル構造を変更しないもう 1 つの理由は、コア開発チームやサードパーティの開発者がデータベーステーブルの構造を変更すると、変更が問題を引き起こす可能性があるからです。 例えば、いくつかのコアデータベーステーブルに、 `additional_data`. これは常に `text` 列のタイプ。 ただし、パフォーマンス上の理由から、コアチームは列を `longtext`. このタイプの列は JSON のエイリアスです。 この列タイプに変換すると、パフォーマンスが向上し、検索性がその列に追加されますが、これは `text` タイプ。 このトピックについて詳しくは、 [JSON データタイプ](https://mariadb.com/kb/en/json-data-type/){target=&quot;_blank&quot;}。

## データを保存または削除するタイミングを把握する

Adobeは、まず、このデータを保存する必要があるかどうかを決定することをお勧めします。 レガシーシステムからデータを移動する場合、削除できるデータにより、移行中の時間と労力を節約できます。 （後でアクセスする必要がある場合は、データをアーカイブする方法があります）。 アプリケーションとパフォーマンスの管理者になるには、追加のデータを保存するリクエストにチャレンジしても問題ありません。 目標は、データの保存が、別の方法で入力できないビジネスニーズを満たすための要件であることを確認することです。

### レガシーデータ

古い注文や顧客レコードなどのレガシーデータがプロジェクトに含まれている場合は、別の参照方法を検討してください。 例えば、ビジネスでデータへのアクセスが不定期の参照用にのみ必要な場合は、古いデータをに移行する代わりに、コマースプラットフォームの外部でホストされる古いデータベースの外部検索を実装することを検討します。 [!DNL Adobe Commerce].

この場合、データベースをサーバーに移行する必要があります。データを読み取るための Web インターフェイスを提供するか、MySQL Workbench または類似のツールを使用するトレーニングを提供する必要があります。 新しいデータベースからこのデータを除外すると、開発チームはデータ移行の問題のトラブルシューティングではなく、新しいサイトに焦点を当てることで、移行を迅速におこなえます。

データをコマースの外部に保持しながらリアルタイムで使用する別の関連オプションは、GraphQL メッシュなどの他のツールを活用することです。 このオプションは、異なるデータソースを組み合わせて、単一の応答として返します。

例えば、次のことが可能です。 `stitch` 外部データベース ( 廃止された古いMagento1 サイトなど ) からの古い注文をまとめたもの。 次に、GraphQL メッシュを使用して、顧客の注文履歴の一部として表示します。 これらの古い注文は、現在の注文と組み合わせることができます [!DNL Adobe Commerce] 環境。

GraphQL での API メッシュの使用について詳しくは、 [API メッシュとは](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/){target=&quot;_blank&quot;}) および [GraphQL メッシュゲートウェイ](https://developer.adobe.com/graphql-mesh-gateway/){target=&quot;_blank&quot;}。

## 拡張機能属性を持つレガシーデータの移行

レガシーデータを移行する必要があると判断した場合、または新しいデータを [!DNL Adobe Commerce]を使用する場合、Adobeは [拡張属性](https://developer.adobe.com/commerce/php/development/components/add-attributes/){target=&quot;_blank&quot;}。 拡張機能属性を使用して追加データを保存すると、次の利点があります。

- 保持するデータとデータベース構造を制御して、正しい列タイプと適切なインデックスでデータが保存されるようにします。
- のほとんどのエンティティ [!DNL Adobe Commerce] および [!DNL Magento Open Source] は、拡張機能属性の使用をサポートしています。
- 拡張機能属性は、ストレージに依存しないメカニズムで、データをプロジェクトに最適な場所に柔軟に保存できます。

ストレージの場所の 2 つの例は、データベーステーブルと [!DNL Redis]. 場所を選択する際に考慮すべき重要な点は、場所がより複雑になるか、パフォーマンスに影響を与えるかです。

### 他の代替策を検討する

開発者は、 [!DNL Adobe Commerce] 環境 (GraphQL メッシュやAdobeApp Builder など )。 これらのツールを使用すると、データへのアクセスを保持できますが、コアコマースアプリケーションやその基になるデータベーステーブルには影響しません。 この方法では、API を使用してデータを公開します。 次に、App Builder の設定にデータソースを追加します。 GraphQL Mesh を使用すると、これらのデータソースを組み合わせて、 [レガシーデータ](#legacy-data).

GraphQL メッシュの詳細については、 [GraphQL メッシュゲートウェイ](https://developer.adobe.com/graphql-mesh-gateway/){target=&quot;_blank&quot;}。 App Builder について詳しくは、Adobe [App Builder の概要](https://experienceleague.adobe.com/docs/adobe-developers-live-events/events/2021/oct2021/introduction-app-builder.html?lang=en){target=&quot;_blank&quot;}。

## コアテーブルまたはサードパーティテーブルの変更

コアを変更してデータを保存する場合 [!DNL Adobe Commerce] また、サードパーティモジュールのデータベーステーブルでは、次のガイドラインに従って、安定性とパフォーマンスへの影響を最小限に抑えます。

- 新しい列のみを追加します。
- 絶対に _type_ 既存の列の値。 例えば、 `integer` から `varchar` を使用して、固有のユースケースを満たすことができます。
- EAV 属性テーブルに列を追加しないでください。 これらのテーブルは、既にロジックと責任で過負荷になっています。
- テーブルを調整する前に、サイズを決定します。 大きなテーブルを変更すると、デプロイメントに影響し、変更が適用されると数分または数時間の遅延が生じる場合があります。

## 外部データベーステーブルを変更する際のベストプラクティス

Adobeでは、コアデータベーステーブルまたはサードパーティテーブルに列を追加する場合、次の手順に従うことをお勧めします。

1. 更新する内容を表す名前空間に、名前を持つモジュールを作成します。

   例： `app/code/YourCompany/Customer`

1. 適切なファイルを作成してモジュールを有効にします ( [モジュールの作成](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/create-module.html){target=&quot;_blank&quot;}。

1. という名前のファイルを作成します。 `db_schema.xml` 内 `etc` フォルダーに保存し、適切な変更を行います。

   該当する場合は、 `db_schema_whitelist.json` ファイル。 詳しくは、 [宣言スキーマ](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/){target=&quot;_blank&quot;} を参照してください。

### 潜在的な影響

外部データベースに列を追加すると、次の方法でAdobe Commerceプロジェクトに影響を与える可能性があります。

- アップグレードはより複雑になる場合があります。
- 変更するテーブルが大きい場合は、デプロイメントに影響が及びます。
- 新しいプラットフォームへの移行は、より複雑になる可能性があります。

## コアテーブルを変更しない方法

Adobe Commerceデータベーステーブルを変更する場合は、 [拡張属性](#migrate-legacy-data-with-extension-attributes). 別の方法として、特別な列 (`additional_data`) がいくつかのコアテーブルで見つかり、データを保存して JSON エンコード形式で保存できます。

### JSON エンコードされたデータ列にデータを保存する

一部のコアテーブルには、 `additional_data` JSON エンコードされたデータが格納される列。 この列を使用すると、1 つのフィールドに追加データをネイティブでマッピングできます。 この方法を使用すると、検索要件なしでデータ取得用の情報を格納する、小さくて簡単なデータ要素のテーブルを追加するのを回避できます。 この `additional_data` 通常、列は品目レベルでのみ使用でき、見積もりや注文全体では使用できません。

- を使用する利点 `additional_data` フィールド

   - 列数を最小限に抑える追加のフィールドは不要です。 これは、既に多数のテーブルが関係している販売フローで役立ちます。 この複雑なプロセスに複雑さを増やさない方が良いでしょう。 この方法は、多くの使用例を満たしますが、すべての使用例を満たすわけではありません。

- デメリット

   - この方法は、読み取り専用データの保存にのみ最適です。 この問題が発生するのは、依存関係やデータベースの関係を追加するために、オブジェクトを変更および構築するために、コードをシリアル化解除する必要があるからです。

   - データベース操作を使用してこれらのフィールドを検索するのは困難です。 この方法での検索は遅い。

   - データを `additional_data` 列を使用して、無効な JSON を作成したり、実行時に読み取りエラーが発生したりすることでコードが壊れる可能性があるシリアル化または非シリアル化操作をトリガーしないようにします。

   - 開発者が簡単に見つけられるように、これらのフィールドはコード内で明確に宣言する必要があります。

   - 診断が非常に難しい、発生する可能性のあるその他の問題。 例えば、PHP の一部の関数を使用する場合、 [!DNL Adobe Commerce] コアアプリケーションが提供するラッパーメソッド変換されたデータの最終結果は、期待される形式とは異なる場合があります。 常にラッパー関数を使用して、保存または取得するデータの一貫性と予測可能性を確保します。

次に、 `additional_data` 列。

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

バージョン 2.4.3、2.4.4、2.4.5 では、列を持つ 10 個のテーブルが存在します `additional_data`.

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
