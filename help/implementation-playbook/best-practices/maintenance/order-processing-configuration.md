---
title: オーダー処理の設定のベストプラクティス
description: チェックアウトと注文の処理パフォーマンスを向上させるための設定のベストプラクティスについて説明します。
role: Admin, User
feature: Best Practices
exl-id: d15fe845-670f-4f7e-9645-7e111e6e809f
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# オーダー処理の設定のベストプラクティス

Commerce サイトで注文量が増えるにつれ、次のストア設定オプションを有効にして、チェックアウトのパフォーマンスと注文処理を最適化できます。

- **[!UICONTROL Asynchronous indexing]** – このオプションを有効にすると、大量の注文が同時に行われたときに発生する可能性のあるデータベースのロックや処理の遅れを防ぐことができます。
- **[!UICONTROL Asynchronous email notifications]** – このオプションを有効にすると、チェックアウトおよび注文処理のメール通知を、直ちに送信するのではなく、指定された間隔で送信することで、チェックアウトのパフォーマンスを向上できます。
- **[!UICONTROL Enable Archiving]** – このオプションを有効にすると、注文、請求書、出荷、クレジット・メモのパフォーマンスが向上し、ワークスペースに不要な情報が含まれないため、現在のビジネスに集中できます。 参照： [アーカイブを有効にする](https://docs.magento.com/user-guide/sales/order-archive.html#to-enable-archiving).

## 影響を受ける製品とバージョン

[サポートされているすべてのバージョン](../../../release/versions.md) （件中）:

- クラウドインフラストラクチャー上のAdobe Commerce
- Adobe Commerce オンプレミス

## 非同期注文処理を有効にする

非同期注文処理を有効にする手順は、デプロイメントモードによって異なります。

- クラウドインフラストラクチャー上のAdobe Commerceおよび実稼動モードのオンプレミスサイトの場合は、次のMagento CLI コマンドを使用して非同期インデックス作成を有効にします。

  ```php
  php bin/magento config:set dev/grid/async_indexing 1
  ```

- デフォルトモードまたは実稼動モードのAdobe Commerce オンプレミスサイトの場合は、管理者の Grid Settings 設定を更新して、非同期インデックス作成を有効にします。

  参照： [スケジュールされたグリッドの更新とインデックス再作成を有効にする](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-scheduled-operations.html#enable-scheduled-grid-updates-and-reindexing)

  >[!WARNING]
  >
  >実稼動環境を更新する前に、必ずステージング環境で設定変更をテストしてください。

## 追加情報

- [設定のベストプラクティス](../../../performance/configuration.md)
- [一般設定パスおよび詳細設定パスのリファレンス](../../../configuration/reference/config-reference-general.md)
- [高スループットのオーダー処理](../../../performance/high-throughput-order-processing.md)
