---
title: 注文処理の設定のベストプラクティス
description: チェックアウトと注文処理のパフォーマンスを向上させる設定のベストプラクティスについて説明します。
role: Admin, User
feature: Best Practices
exl-id: d15fe845-670f-4f7e-9645-7e111e6e809f
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# 注文処理の設定のベストプラクティス

コマースサイトの注文量が増加すると、次のストア設定オプションを有効にすることで、チェックアウトのパフォーマンスと注文処理を最適化できます。

- **[!UICONTROL Asynchronous indexing]** — このオプションを有効にすると、多数の注文が同時に行われた場合に発生する可能性のあるデータベースのロックと処理の遅延を防ぐことができます。
- **[!UICONTROL Asynchronous email notifications]** — このオプションを有効にすると、チェックアウト通知と注文処理の電子メール通知を指定の間隔で送信し、即座に送信するのではなく、チェックアウトパフォーマンスを高めることができます。
- **[!UICONTROL Enable Archiving]** — このオプションを有効にすると、オーダー、請求書、出荷およびクレジット・メモのパフォーマンスが向上し、ワークスペースに不要な情報がなくなり、現在のビジネスに集中できます。 詳しくは、 [アーカイブを有効にする](https://docs.magento.com/user-guide/sales/order-archive.html#to-enable-archiving).

## 影響を受ける製品およびバージョン

[サポートされているすべてのバージョン](../../../release/versions.md) /:

- Adobe Commerce an cloud infrastructure
- Adobe Commerceオンプレミス

## 非同期の注文処理を有効にする

非同期での注文処理を有効にする手順は、デプロイメントモードによって異なります。

- クラウドインフラストラクチャ上のAdobe Commerceおよび実稼働モードのオンプレミスサイトの場合は、次のMagentoCLI コマンドを使用して、非同期インデックス作成を有効にします。

  ```php
  php bin/magento config:set dev/grid/async_indexing 1
  ```

- Default または Production モードのAdobe Commerceオンプレミスサイトの場合は、管理者の Grid Settings 構成を更新して、非同期インデックス作成を有効にします。

  詳しくは、 [スケジュールされたグリッドの更新とインデックス再作成を有効にする](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-scheduled-operations.html#enable-scheduled-grid-updates-and-reindexing)

  >[!WARNING]
  >
  >実稼動環境を更新する前に、必ずステージング環境で設定の変更をテストしてください。

## 追加情報

- [設定のベストプラクティス](../../../performance/configuration.md)
- [一般的および高度な設定パスのリファレンス](../../../configuration/reference/config-reference-general.md)
- [高スループットの注文処理](../../../performance/high-throughput-order-processing.md)
