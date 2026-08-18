---
title: データ移行のベストプラクティス
description: Magento 1からMagento 2へのアップグレードを成功させるには、次のデータ移行のベストプラクティスに従ってください。
exl-id: 0cd51987-a514-434d-b21e-2739ada2ce85
feature: Best Practices, Configuration
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---

# データ移行のベストプラクティス

このセクションでは、移行を迅速化および簡素化するための推奨事項と、移行にかかる時間に関するガイダンスを提供します。

* **移行テストを実行する際に、Magento 1 インスタンス**&#x200B;のデータベースのコピーを使用します。 Magento 1 ストアデータベースの実稼動インスタンスは使用しないでください。

* **移行する前に、Magento 1 データベースから古い冗長なデータ**&#x200B;を削除します。

そのようなデータには、ログ、注文見積もり、最近閲覧または比較された商品、訪問者、イベント固有のカテゴリー、プロモーションルールなどが含まれます。

* **移行を成功させるには、[一般的なルール](migrate-data/overview.md#migration-overview)**&#x200B;に従ってください。

* パフォーマンスを向上させるには、`config.xml` ファイルで`direct_document_copy` オプション **を有効にします。**

  ```xml
  <direct_document_copy>1</direct_document_copy>
  ```

>[!NOTE]
>
>Magento 1とMagento 2の両方のデータベースは、同じMySQL サーバー上に配置する必要があり、データベースアカウントは両方のデータベースにアクセスできる必要があります。

## ベンチマーク推定

Adobeでは、次のシステムでのデータ移行をテストしました。

* Virtual Box VM、CentOS 6、2.5 GB RAM、CPU 1 コア 2.6 GHz
* 製品が177,000件、注文が355,000件、顧客が214,000人のデータベース

## パフォーマンス結果

* 設定の移行時間：約10分
* データ移行時間：約9時間（URL書き換えを除くすべてのデータ、合計データの約85%）
* サイトのダウンタイムの見積もり：DNS設定のインデックスを再作成して変更するには数分かかります。 ページキャッシュのウォームアップに必要な追加時間。
