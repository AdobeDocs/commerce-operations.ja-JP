---
title: スプリットデータベースの検証
description: Commerceのスプリットデータベース設定が正しく機能していることを確認する方法を説明します。
recommendations: noCatalog
exl-id: 36295240-6521-4f3e-9ea3-f35b73de672d
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%
---
# スプリットデータベースの検証

{{ee-only}}

{{deprecate-split-db}}

設定後、マスターデータベースは次のように設定されます。

- メインのCommerce データベース：369 テーブル
- Commerce見積もりデータベース：11 テーブル
- Commerce販売データベース：55 テーブル

分割データベースが正常に機能していることを確認するには、次のタスクを実行し、[phpmyadmin](../../installation/prerequisites/optional-software.md#phpmyadmin)などのデータベースツールを使用して、データベーステーブルにデータが追加されていることを確認します。

| 検証すべきこと | 検証方法 |
| -------------- | ------------- |
| 見積もりデータベースが機能しています | 商品をカートに追加する： 見積書データベースの`quote`、`quote_address`、および`quote_item`のテーブルに行が追加されていることを確認します。 |
| 営業データベースは機能しています | 注文を完了します（小切手/マネーオーダーを含む任意の支払い方法）。 セールスデータベースの`sales_order_address`、`sales_order_item`、および`sales_order_payment`のテーブルに行が追加されていることを確認します。 |

>[!WARNING]
>
>2つの追加のデータベースインスタンスを手動でバックアップする必要があります。 Commerceは、メインデータベースインスタンスのみをバックアップします。 [`magento setup:backup --db`](../../installation/tutorials/backup.md) コマンドと管理者オプションでは、追加のテーブルがバックアップされません。
