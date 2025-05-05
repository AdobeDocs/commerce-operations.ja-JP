---
title: オーダー処理の設定のベストプラクティス
description: チェックアウトと注文の処理パフォーマンスを向上させるための設定のベストプラクティスについて説明します。
role: Admin, User
feature: Best Practices
exl-id: d15fe845-670f-4f7e-9645-7e111e6e809f
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# オーダー処理の設定のベストプラクティス

Commerce サイトで注文量が増えるにつれ、次のストア設定オプションを有効にして、チェックアウトのパフォーマンスと注文処理を最適化できます。

- **[!UICONTROL Asynchronous indexing]** – このオプションを有効にすると、多数のオーダーが同時に配置された場合に発生する可能性のあるデータベースのロックおよび処理の遅延を防止できます。
- **[!UICONTROL Asynchronous email notifications]** – このオプションを有効にすると、チェックアウトおよび注文処理の E メール通知を即時に送信するのではなく、指定した間隔で送信することで、チェックアウトのパフォーマンスを向上できます。
- **[!UICONTROL Enable Archiving]**：このオプションを有効にすると、受注、請求書、出荷およびクレジット・メモのパフォーマンスが向上し、ワークスペースに不要な情報が含まれないため、現在のビジネスに集中できます。 [ アーカイブの有効化 ](https://experienceleague.adobe.com/ja/docs/commerce-admin/stores-sales/order-management/orders/order-archive) を参照してください。

## 影響を受ける製品とバージョン

[ サポートされているすべてのバージョン ](../../../release/versions.md):

- クラウドインフラストラクチャー上のAdobe Commerce
- Adobe Commerce オンプレミス

## 非同期注文処理を有効にする

非同期注文処理を有効にする手順は、デプロイメントモードによって異なります。

- クラウドインフラストラクチャー上のAdobe Commerceおよび実稼動モードのオンプレミスサイトの場合は、次のMagento CLI コマンドを使用して非同期インデックス作成を有効にします。

  ```php
  php bin/magento config:set dev/grid/async_indexing 1
  ```

- デフォルトモードまたは実稼動モードのAdobe Commerce オンプレミスサイトの場合は、管理者の Grid Settings 設定を更新して、非同期インデックス作成を有効にします。

  [ スケジュールされたグリッドの更新とインデックス再作成の有効化 ](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-scheduled-operations.html?lang=ja#enable-scheduled-grid-updates-and-reindexing) を参照してください。

  >[!WARNING]
  >
  >実稼動環境を更新する前に、必ずステージング環境で設定変更をテストしてください。

## 追加情報

- [設定のベストプラクティス](../../../performance/configuration.md)
- [一般設定パスおよび詳細設定パスのリファレンス](../../../configuration/reference/config-reference-general.md)
- [高スループットのオーダー処理](../../../performance/high-throughput-order-processing.md)
