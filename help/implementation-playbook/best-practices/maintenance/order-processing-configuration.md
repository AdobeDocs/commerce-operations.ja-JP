---
title: 注文処理の設定のベストプラクティス
description: チェックアウトと注文処理のパフォーマンスを向上させるための設定のベストプラクティスについて説明します。
role: Admin, User
feature: Best Practices
exl-id: d15fe845-670f-4f7e-9645-7e111e6e809f
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# 注文処理の設定のベストプラクティス

Commerce サイトでの注文量が増加すると、次のストア設定オプションを有効にすることで、チェックアウトのパフォーマンスと注文処理を最適化できます。

- **[!UICONTROL Asynchronous indexing]** – このオプションを有効にすると、多数の注文が同時に行われる場合に発生する可能性のある、データベースのロックと処理速度の低下を防ぐことができます。
- **[!UICONTROL Asynchronous email notifications]** – このオプションを有効にすると、チェックアウトと注文処理のメール通知をすぐに送信するのではなく、指定された間隔で送信して、チェックアウトのパフォーマンスを高速化できます。
- **[!UICONTROL Enable Archiving]** – このオプションを有効にすると、注文、請求書、出荷、およびクレジット メモのパフォーマンスが向上し、ワークスペースに不要な情報がなくなるため、現在のビジネスに集中できるようになります。 「[ アーカイブを有効にする](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-archive)」を参照してください。

## 影響を受ける製品とバージョン

[ サポートされているすべてのバージョン ](../../../release/versions.md) /:

- Adobe Commerce on cloud infrastructure
- Adobe Commerce オンプレミス

## 非同期注文処理を有効にする

非同期注文処理を有効にする手順は、デプロイメントモードによって異なります。

- クラウドインフラストラクチャ上のAdobe Commerceと実稼動モードのオンプレミスサイトの場合は、次のMagento CLI コマンドを使用して非同期インデックス作成を有効にします。

  ```php
  php bin/magento config:set dev/grid/async_indexing 1
  ```

- デフォルトモードまたは実稼動モードのAdobe Commerce オンプレミスサイトの場合は、AdminでGrid Settings設定を更新して非同期インデックス作成を有効にします。

  [ スケジュールされたグリッドの更新とインデックス再作成の有効化](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-scheduled-operations.html#enable-scheduled-grid-updates-and-reindexing)を参照してください

  >[!WARNING]
  >
  >実稼動環境を更新する前に、必ずステージング環境の設定変更をテストしてください。

## 追加情報

- [設定のベストプラクティス](../../../performance/configuration.md)
- [一般および詳細設定パスのリファレンス](../../../configuration/reference/config-reference-general.md)
- [高スループットの注文処理](../../../performance/high-throughput-order-processing.md)
