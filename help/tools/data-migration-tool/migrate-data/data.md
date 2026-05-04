---
title: データの移行
description: ' [!DNL Data Migration Tool]を使用してMagento 1からMagento 2へのデータ移行を開始する方法を説明します。'
exl-id: f4ea8f6a-21f8-4db6-b598-c5efecec254f
topic: Commerce, Migration
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---

# データの移行

開始する前に、次の手順を実行して準備します。

1. アプリケーションサーバーに[&#x200B; ファイルシステム所有者](../../../installation/prerequisites/file-system/overview.md)としてログインします。
1. アプリケーション インストール ディレクトリに変更するか、システム `PATH`に追加されていることを確認してください。

詳しくは、[最初の手順](overview.md#first-steps) セクションを参照してください。

## データ移行コマンドの実行

データの移行を開始するには、以下を実行します。

```shell
bin/magento migrate:data [-r|--reset] [-a|--auto] {<path to config.xml>}
```

どこで：

* `[-a|--auto]`は、整合性チェック エラーが発生した場合に移行が停止するのを防ぐオプションの引数です。

* `[-r|--reset]`は、最初から移行を開始するオプションの引数です。 この引数は、移行のテストに使用できます。

* `{<path to config.xml>}`は`config.xml`への絶対ファイルシステムパスです。この引数は必須です

この手順では、[!DNL Data Migration Tool]はMagento 1 データベースの移行テーブル用に追加のテーブルとトリガーを作成します。 これらは、[増分/差分](delta.md)移行ステップで使用されます。 追加のテーブルには、最終的な移行実行後に変更されたレコードに関する情報が含まれます。 データベース・トリガーは、これらの追加テーブルにデータを入力するために使用されます。そのため、特定のテーブルに対して新しい操作が実行されている場合（レコードが追加/変更/削除されている場合）、これらのデータベース・トリガーは、この操作に関する情報を追加テーブルに保存します。 差分移行プロセスを実行すると、[!DNL Data Migration Tool]はこれらのテーブルに未処理のレコードを確認し、必要なコンテンツをMagento 2 データベースに移行します。

各新しいテーブルには次のものが含まれます。

* `m2_cl`接頭辞
* `INSERT`、`UPDATE`、`DELETE` イベントトリガー。

例えば、`sales_flat_order`の場合、[!DNL Data Migration Tool]は次のように作成します。

* `m2_cl_sales_flat_order` テーブル：

  ```sql
  CREATE TABLE `m2_cl_sales_flat_order` (
    `entity_id` int(11) NOT NULL COMMENT 'Entity_id',
    `operation` text COMMENT 'Operation',
    `processed` tinyint(1) NOT NULL DEFAULT '0' COMMENT 'Processed',
    PRIMARY KEY (`entity_id`)
  ) COMMENT='m2_cl_sales_flat_order';
  ```

* `trg_sales_flat_order_after_insert`、`trg_sales_flat_order_after_update`、`trg_sales_flat_order_after_delete`トリガー:

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
>[!DNL Data Migration Tool]は、実行中に現在の進行状況を保存します。 エラーまたはユーザーの介入によって実行が停止された場合、ツールは最後の正常な状態で進行状況を再開します。 [!DNL Data Migration Tool]を最初から強制的に実行するには、`--reset`引数を使用します。 その場合、以前に移行したデータの重複を防ぐために、Magento 2 データベースダンプを復元することをお勧めします。


## 可能性のある一貫性エラー

実行中に、[!DNL Data Migration Tool]はMagento 1とMagento 2のデータベース間の不整合を報告し、次のようなメッセージを表示する場合があります。

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

詳しい情報と推奨事項については、このガイドの[&#x200B; トラブルシューティング &#x200B;](https://support.magento.com/hc/en-us/articles/360033020451)の節を参照してください。

## 次の移行手順

[変更を移行](delta.md)
