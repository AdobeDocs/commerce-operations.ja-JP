---
title: データを移行
description: ' [!DNL Data Migration Tool] を使用して、Magento 1 からMagento 2 へのデータの移行を開始する方法を説明します。'
exl-id: f4ea8f6a-21f8-4db6-b598-c5efecec254f
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# データを移行

開始する前に、次の手順に従って準備を行います。

1. アプリケーションサーバーに [ ファイルシステムの所有者 ](../../../installation/prerequisites/file-system/overview.md) としてログインします。
1. アプリケーションのインストールディレクトリに移動するか、システムデ `PATH` クトリに追加されていることを確認します。

詳しくは、[ 最初の手順 ](overview.md#first-steps) の節を参照してください。

## データ移行コマンドの実行

データの移行を開始するには、次を実行します。

```bash
bin/magento migrate:data [-r|--reset] [-a|--auto] {<path to config.xml>}
```

ここで、

* `[-a|--auto]` は、整合性チェックエラーが発生した場合に移行が停止するのを防ぐオプション引数です。

* `[-r|--reset]` は、最初から移行を開始するオプションの引数です。 この引数を使用して、移行をテストできます。

* `{<path to config.xml>}` は `config.xml` への絶対ファイルシステムパスです。この引数は必須です

この手順では、Magento1[!DNL Data Migration Tool] ータベースのマイグレーション・テーブル用に、追加のテーブルとトリガーが作成されます。 これらは、[ 増分/差分 ](delta.md) 移行手順で使用されます。 追加のテーブルには、最終的な移行の実行後に変更されたレコードに関する情報が含まれます。 データベーストリガーは、これらの追加テーブルへの入力に使用します。したがって、特定のテーブルに対して新しい処理が実行されている（レコードが追加/変更/削除されている）場合、これらのデータベーストリガーによって、この処理に関する情報が追加のテーブルに保存されます。 差分マイグレーションプロセスを実行すると、[!DNL Data Migration Tool] はこれらのテーブルをチェックして未処理のレコードを探し、必要なコンテンツをMagento2 データベースにマイグレートします。

それぞれの新しいテーブルには、次の内容が含まれます。

* `m2_cl` プレフィックス
* `INSERT`、`UPDATE`、`DELETE` イベントトリガー。

例えば、`sales_flat_order` の場合、[!DNL Data Migration Tool] は次を作成します。

* `m2_cl_sales_flat_order` テーブル：

  ```sql
  CREATE TABLE `m2_cl_sales_flat_order` (
    `entity_id` int(11) NOT NULL COMMENT 'Entity_id',
    `operation` text COMMENT 'Operation',
    `processed` tinyint(1) NOT NULL DEFAULT '0' COMMENT 'Processed',
    PRIMARY KEY (`entity_id`)
  ) COMMENT='m2_cl_sales_flat_order';
  ```

* `trg_sales_flat_order_after_insert`、`trg_sales_flat_order_after_update`、`trg_sales_flat_order_after_delete` のトリガー:

  ```sql
  DELIMITER ;;
  CREATE TRIGGER `trg_sales_flat_order_after_insert` AFTER INSERT ON `sales_flat_order`
    FOR EACH ROW
    BEGIN
     INSERT INTO m2_cl_sales_flat_order (`entity_id`, `operation`) VALUES (NEW.entity_id, 'INSERT')ON DUPLICATE KEY UPDATE operation = 'INSERT';
    END
  ;;
  
  DELIMITER ;;
  CREATE TRIGGER `trg_sales_flat_order_after_update` AFTER UPDATE ON `sales_flat_order`
    FOR EACH ROW
    BEGIN
     INSERT INTO m2_cl_sales_flat_order (`entity_id`, `operation`) VALUES (NEW.entity_id, 'UPDATE') ON DUPLICATE KEY UPDATE operation = 'UPDATE';
    END
  ;;
  
  DELIMITER ;;
  CREATE TRIGGER `trg_sales_flat_order_after_delete` AFTER DELETE ON `sales_flat_order`
    FOR EACH ROW
    BEGIN
     INSERT INTO m2_cl_sales_flat_order (`entity_id`, `operation`) VALUES (OLD.entity_id, 'DELETE')ON DUPLICATE KEY UPDATE operation = 'DELETE';
    END
  ;;
  ```

>[!NOTE]
>
>[!DNL Data Migration Tool] は、実行時に現在の進行状況を保存します。 エラーまたはユーザーの介入によって実行が停止した場合、ツールは前回正常起動時の状態から進捗を再開します。 [!DNL Data Migration Tool] を最初から強制的に実行するには、`--reset` 引数を使用します。 この場合、以前に移行したデータが重複しないように、Magento2 のデータベースダンプを復元することをお勧めします。


## 一貫性エラーの可能性

実行中に、[!DNL Data Migration Tool] はMagento1 とMagento2 のデータベース間の不整合を報告し、次のようなメッセージが表示される場合があります。

* `Source documents are missing: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Destination documents are missing: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Source documents are not mapped: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Destination documents are not mapped: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Source fields are missing. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Destination fields are missing. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Source fields are not mapped. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Destination fields are not mapped. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Mismatch of data types. Source document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Mismatch of data types. Destination document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Incompatibility in data. Source document: <EXTENSION_TABLE>. Field: <FIELD>. Error: <ERROR_MESSAGE>`
* `Incompatibility in data. Destination document: <EXTENSION_TABLE>. Field: <FIELD>. Error: <ERROR_MESSAGE>`

詳細と推奨事項については、このガイドの [ トラブルシューティング ](https://support.magento.com/hc/en-us/articles/360033020451) の節を参照してください。

## 次の移行手順

[変更を移行](delta.md)
