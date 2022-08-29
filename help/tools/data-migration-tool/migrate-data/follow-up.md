---
title: データ移行のフォローアップ
description: Magento1 からMagento2 へのデータ移行が成功したこと、およびすべての機能が期待どおりに動作していることを検証する方法について説明します。
source-git-commit: d609c497fdf00c5e5f975a5679b1d072cec4f8a2
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---


# データ移行のフォローアップ

Magento1 の一部の動作とロジックは、Magento2 では実装が異なっています。 この [!DNL Data Migration Tool] それを処理する。 移行に関しては、いくつかの側面を知っておく必要があり、移行後にスムーズに動作するためには、いくつかの機能について小さな手順を踏む必要がある場合があります。

## 情報

### 分割データベースはサポートされていません

この [!DNL Data Migration Tool] は、分割データベースをサポートしていません。

### グループ価格を階層価格に変換

移行中に、すべてのグループ価格が自動的に階層価格に変換されます。

### 販売エンティティの新しい番号付け

受注、請求書、出荷、クレジット・メモおよび RMA の移行に関する参照番号は、そのままです。 移行後、新しいMagento2 番の割り当てルールが適用されます。 新しい販売エンティティの数値が異なります。

## 手順

### 顧客セグメントの再保存 [Adobe Commerceのみ]

移行後、顧客セグメントは [管理者](https://glossary.magento.com/admin) パネルを使用して操作を開始します。

### タイムゾーンの設定

このツールではタイムゾーン設定は移行されないので、移行後にタイムゾーンを手動で設定する必要があります ( )。 **ストア** > **設定** > **ロケールオプション** > **タイムゾーン**.

デフォルトでは、Magentoは時刻データをデータベースの UTC-0 ゾーンに保存し、現在のタイムゾーン設定に従って表示します。 時刻データが既に UTC-0 以外のゾーンでデータベースに保存されている場合は、 [!DNL Data Migration Tool]&#39;s `\Migration\Handler\Timezone` ハンドラ

次の例では、Magento1 が誤ってデータベースの UTC-7 ゾーンの時間を節約しています（例えば、サードパーティの拡張機能の誤りが原因です）。 移行時に顧客アカウントの作成時刻を UTC-0 ゾーンに適切に変換するには、次の手順に従います。

1. を `map-customer.xml.dist` 設定ファイルを [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>`) を `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/map-customer.xml` ファイル。

1. を更新します。 `<customer_map_file>` ノード内 `config.xml` をクリックし、 `.dist` からの拡張 `map-customer.xml.dist`

1. 次のルールを `map-customer.xml` ファイル：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<map xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="../map.xsd">
  <!--...-->
  <destination>
      <field_rules>
          <!--...-->
          <transform>
              <field>customer_entity.created_at</field>
              <handler class="\Migration\Handler\Timezone">
                  <param name="offset" value="-7" />
              </handler>
          </transform>
      </field_rules>
  </destination>
</map>
```