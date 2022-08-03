---
title: 分割データベースの検証
description: コマース分割データベースの構成が正しく機能していることを確認する方法を説明します。
source-git-commit: 52f92ef79586d618fd4ac51c00eaa1446a2dc98f
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---


# 分割データベースの検証

{{ee-only}}

{{deprecate-split-db}}

設定後、マスター・データベースは次のように構成されます。

- メインコマースデータベース：369 テーブル
- コマース [見積もり](https://glossary.magento.com/quote) データベース：11 テーブル
- コマース販売データベース：55 テーブル

分割データベースが正しく動作していることを確認するには、次のタスクを実行し、データがデータベーステーブルに追加されていることを、 [phmyadmin](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/optional.html#install-optional-phpmyadmin):

| 検証内容 | 検証方法 |
| -------------- | ------------- |
| 見積もりデータベースが機能しています | 買い物かごに項目を追加します。 行が見積データベースのに追加されたことを確認します。 `quote`, `quote_address`、および `quote_item` テーブル。 |
| セールスデータベースが動作しています | 注文を完了します（小切手/送金注文を含む任意の支払い方法）。 行がセールスデータベースのに追加されたことを確認します。 `sales_order_address`, `sales_order_item`、および `sales_order_payment` テーブル。 |

>[!WARNING]
>
>2 つの追加のデータベースインスタンスを手動でバックアップする必要があります。 Commerce は、メインデータベースインスタンスのみをバックアップします。 この [`magento setup:backup --db`](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-backup.html) コマンドおよび管理オプションでは、追加のテーブルはバックアップされません。
