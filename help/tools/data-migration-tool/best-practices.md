---
title: データ移行のベストプラクティス
description: データ移行のベストプラクティスに従って、Magento 1 からMagento 2 に正常にアップグレードします。
exl-id: 0cd51987-a514-434d-b21e-2739ada2ce85
feature: Best Practices, Configuration
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 0%

---

# データ移行のベストプラクティス

このセクションでは、移行を加速し、シンプル化するための最適な推奨事項と、移行にかかる時間に関するガイダンスを示します。

* 移行テストを実行する際は、**Magento 1 インスタンスのデータベースのコピーを使用** ます。 Magento 1 ストアデータベースの実稼動インスタンスは使用しないでください。

* 移行前に、Magento 1 データベースから **古くなった冗長なデータを削除** します。

このようなデータには、ログ、注文見積、最近表示または比較された製品、訪問者、イベント固有のカテゴリ、プロモーションルールなどが含まれる場合があります。

* **移行を成功させるための一般的なルール [&#x200B; に従い](migrate-data/overview.md#migration-overview)** す。

* パフォーマンスを向上させるには、**ファイルで `direct_document_copy`** オプションを有効にする `config.xml` ことができます。

  ```xml
  <direct_document_copy>1</direct_document_copy>
  ```

>[!NOTE]
>
>Magento 1 とMagento 2 の両方のデータベースが同じ MySQL サーバー上にある必要があり、データベースアカウントが両方のデータベースにアクセスできる必要があります。

## ベンチマークの推定

Adobeは、次のシステムでのデータ移行をテストしました。

* Virtual Box VM、CentOS 6、2.5 GB RAM、CPU 1 コア 2.6 GHz
* 177,000 の製品、355,000 の注文、214,000 の顧客を含むデータベース

## パフォーマンス結果

* 設定の移行時間：約 10 分
* データ移行時間：約 9 時間（URL の書き換えを除くすべてのデータ、合計データの約 85%）
* サイトのダウンタイムの見積もり：DNS 設定の再インデックスおよび変更に数分かかります。 ページキャッシュのウォームアップに必要な追加時間。
