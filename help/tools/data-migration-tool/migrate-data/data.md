---
title: データの移行
description: を使用してMagento1 からMagento2 へのデータ移行を開始する方法を説明します。 [!DNL Data Migration Tool].
source-git-commit: b5a2c362b09de993e1dc196bdda90e74cf4a8ba2
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---


# データの移行

開始する前に、次の手順に従って準備を行います。

1. アプリケーションサーバーに次のようにログインします。 [ファイルシステムの所有者](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. アプリケーションのインストールディレクトリに移動するか、システムに追加されていることを確認します。 `PATH`.

詳しくは、 [最初の手順](overview.md#first-steps) 」の節を参照してください。

## データ移行コマンドを実行します。

データの移行を開始するには、次のコマンドを実行します。

```bash
bin/magento migrate:data [-r|--reset] [-a|--auto] {<path to config.xml>}
```

ここで、

* `[-a|--auto]` は、整合性チェックエラーが発生した場合に移行を停止しないようにする、オプションの引数です。

* `[-r|--reset]` は、最初から移行を開始するオプションの引数です。 この引数は、移行のテストに使用できます。

* `{<path to config.xml>}` は、 `config.xml`;この引数は必須です

この手順では、 [!DNL Data Migration Tool] は、移行テーブル用の追加のテーブルとトリガーをMagento1 データベースに作成します。 これらは、 [増分/差分](delta.md) 移行手順です。 追加のテーブルには、最終的な移行実行後の変更済みレコードに関する情報が含まれます。 データベーストリガーは、これらの追加テーブルにデータを入力するために使用されます。したがって、特定のテーブルに対して新しい操作（レコードの追加、変更、削除）が実行されている場合、この操作に関する情報を追加のテーブルに保存します。 差分移行プロセスを実行すると、 [!DNL Data Migration Tool] これらのテーブルで未処理のレコードを確認し、必要なコンテンツをMagento2 データベースに移行します。

新しい各テーブルには、次の内容が含まれます。

* `m2_cl` prefix
* `INSERT`, `UPDATE`, `DELETE` イベントトリガー。

例えば、 `sales_flat_order` の [!DNL Data Migration Tool] 作成：

* `m2_cl_sales_flat_order` テーブル：

   ```sql
   CREATE TABLE `m2_cl_sales_flat_order` (
     `entity_id` int(11) NOT NULL COMMENT 'Entity_id',
     `operation` text COMMENT 'Operation',
     `processed` tinyint(1) NOT NULL DEFAULT '0' COMMENT 'Processed',
     PRIMARY KEY (`entity_id`)
   ) COMMENT='m2_cl_sales_flat_order';
   ```

* `trg_sales_flat_order_after_insert`, `trg_sales_flat_order_after_update`, `trg_sales_flat_order_after_delete` トリガー:

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
>この [!DNL Data Migration Tool] 実行中に現在の進行状況を保存します。 エラーまたはユーザーが操作を行った場合に、正常な最後の状態で進行が再開されます。 強制的に [!DNL Data Migration Tool] 最初から実行する場合は、 `--reset` 引数。 その場合は、以前に移行したデータの重複を防ぐために、Magento2 のデータベースダンプを復元することをお勧めします。


## 一貫性エラーの可能性

実行中は、 [!DNL Data Migration Tool] は、Magento1 とMagento2 データベースの間で不整合を報告し、次のようなメッセージを表示する場合があります。

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

詳しくは、 [トラブルシューティング](https://support.magento.com/hc/en-us/articles/360033020451) の節を参照してください。

## 次の移行手順

[変更を移行](delta.md)
