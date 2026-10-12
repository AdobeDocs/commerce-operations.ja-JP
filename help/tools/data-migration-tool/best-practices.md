---
title: データ移行のベストプラクティス
description: Magento 1からMagento 2へのアップグレードを成功させるには、次のデータ移行のベストプラクティスに従ってください。
exl-id: 0cd51987-a514-434d-b21e-2739ada2ce85
feature: Best Practices, Configuration
topic: Commerce, Migration
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
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
source-wordcount: '219'
ht-degree: 0%
---
# データ移行のベストプラクティス

このセクションでは、移行を迅速化および簡素化するための推奨事項と、移行にかかる時間に関するガイダンスを提供します。

* **移行テストの実行時に、Magento 1 インスタンス**&#x200B;のデータベースのコピーを使用します。 Magento 1 ストアデータベースの実稼動インスタンスは使用しないでください。

* 移行前に、Magento 1 データベースから&#x200B;**古い冗長なデータ**&#x200B;を削除します。

そのようなデータには、ログ、注文見積もり、最近閲覧または比較された商品、訪問者、イベント固有のカテゴリー、プロモーションルールなどが含まれます。

* **移行を成功させるには、[一般的なルール](migrate-data/overview.md#migration-overview)**&#x200B;に従ってください。

* パフォーマンスを向上させるには、`config.xml` ファイルで`direct_document_copy` オプション **を有効にします。**

  ```xml
  <direct_document_copy>1</direct_document_copy>
  ```

>[!NOTE]
>
>Magento 1とMagento 2の両方のデータベースを同じMySQL サーバーに配置し、データベースアカウントが両方のデータベースにアクセスできるようにする必要があります。

## ベンチマーク推定

Adobeでは、次のシステムでのデータ移行をテストしました。

* Virtual Box VM、CentOS 6、2.5 GB RAM、CPU 1 コア 2.6 GHz
* 製品が177,000件、注文が355,000件、顧客が214,000人のデータベース

## パフォーマンス結果

* 設定の移行時間：約10分
* データ移行時間：約9時間（URL書き換えを除くすべてのデータ、合計データの約85%）
* サイトのダウンタイムの見積もり：DNS設定のインデックスを再作成して変更するには数分かかります。 ページキャッシュのウォームアップに必要な追加時間。
