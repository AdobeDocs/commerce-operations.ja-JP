---
title: 分割データベースの検証
description: Commerceの分割データベース設定が正しく動作していることを確認する方法について説明します。
recommendations: noCatalog
exl-id: 36295240-6521-4f3e-9ea3-f35b73de672d
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# 分割データベースの検証

{{ee-only}}

{{deprecate-split-db}}

構成後、マスター・データベースは次のように構成されます。

- メインのCommerce データベース：369 テーブル
- Commerce見積データベース：11 個のテーブル
- Commerce sales database: 55 テーブル

分割データベースが正しく動作していることを確認するには、次のタスクを実行し、[phpmyadmin](../../installation/prerequisites/optional-software.md#phpmyadmin) などのデータベース・ツールを使用してデータがデータベース・テーブルに追加されていることを確認します。

| 検証対象 | 検証方法 |
| -------------- | ------------- |
| 見積もりデータベースが動作しています | 買い物かごに商品を追加します。 見積もりデータベースの `quote`、`quote_address`、および `quote_item` テーブルに行が追加されていることを確認します。 |
| 営業データベースが動作しています | 注文を完了します（小切手/マネーオーダーを含む支払い方法）。 sales データベースの `sales_order_address`、`sales_order_item`、`sales_order_payment` の各テーブルに行が追加されていることを確認します。 |

>[!WARNING]
>
>2 つの追加のデータベース・インスタンスを手動でバックアップする必要があります。 Commerceは、メインデータベースインスタンスのみをバックアップします。 [`magento setup:backup --db`](../../installation/tutorials/backup.md) コマンドおよび管理オプションでは、追加のテーブルはバックアップされません。
