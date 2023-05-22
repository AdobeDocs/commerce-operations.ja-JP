---
title: 分割データベースの検証
description: コマース分割データベースの構成が正しく機能していることを確認する方法を説明します。
recommendations: noCatalog
exl-id: 36295240-6521-4f3e-9ea3-f35b73de672d
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# 分割データベースの検証

{{ee-only}}

{{deprecate-split-db}}

設定後、マスター・データベースは次のように構成されます。

- メインコマースデータベース：369 テーブル
- コマース見積もりデータベース：11 テーブル
- コマース販売データベース：55 テーブル

分割データベースが正しく動作していることを確認するには、次のタスクを実行し、データがデータベーステーブルに追加されていることを、 [phmyadmin](../../installation/prerequisites/optional-software.md#phpmyadmin):

| 検証内容 | 検証方法 |
| -------------- | ------------- |
| 見積もりデータベースが機能しています | 買い物かごに項目を追加します。 行が見積データベースのに追加されたことを確認します。 `quote`, `quote_address`、および `quote_item` テーブル。 |
| セールスデータベースが動作しています | 注文を完了します（小切手/送金注文を含む任意の支払い方法）。 行がセールスデータベースのに追加されたことを確認します。 `sales_order_address`, `sales_order_item`、および `sales_order_payment` テーブル。 |

>[!WARNING]
>
>2 つの追加のデータベースインスタンスを手動でバックアップする必要があります。 Commerce は、メインデータベースインスタンスのみをバックアップします。 この [`magento setup:backup --db`](../../installation/tutorials/backup.md) コマンドおよび管理オプションでは、追加のテーブルはバックアップされません。
