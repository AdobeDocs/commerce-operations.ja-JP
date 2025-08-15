---
title: データ移行のフォローアップ
description: Magento 1 からMagento 2 へのデータ移行が成功し、すべての機能が期待どおりに動作していることを検証する方法について説明します。
exl-id: a55f357b-6c95-49d6-b2f1-c2e403a8c85f
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# データ移行のフォローアップ

Magento 2 では、Magento 1 の一部の動作とロジックの実装が異なります。 [!DNL Data Migration Tool] が処理します。 移行後にスムーズに動作させるために、いくつかの機能に対して多少の手順を実行する必要が生じる場合があります。

## 情報

### 分割データベースはサポートされていません

[!DNL Data Migration Tool] は分割データベースをサポートしていません。

### 階層価格に換算したグループ価格

すべてのグループ価格は、移行中に自動的に階層価格に変換されます。

### 営業エンティティの新しい番号付け

受注、請求書、出荷、クレジット・メモおよび RMA の参照番号は、そのまま移行されます。 移行後は、新しいMagento 2 の数値割り当てルールが適用されます。 新しい営業エンティティの数字が異なります。

## 手順

### 顧客セグメントの再保存 [Adobe Commerceのみ ]

移行後、顧客セグメントを稼働させるには、管理パネルから再度保存する必要があります。

### タイムゾーンの設定

このツールではタイムゾーン設定が移行されないので、移行後に **ストア**/**設定**/**ロケールオプション**/**タイムゾーン** でタイムゾーンを手動で設定する必要があります。

デフォルトでは、Magentoは時間データをデータベースの UTC-0 ゾーンに格納し、現在のタイムゾーン設定に従って表示します。 時刻データが既にデータベースの UTC-0 以外のゾーンに保存されている場合は、[!DNL Data Migration Tool] の `\Migration\Handler\Timezone` ハンドラーを使用して既存の時刻を UTC-0 に変換する必要があります。

次の例では、Magento 1 がデータベースの UTC-7 ゾーンで誤って時間を節約していました（例えば、サードパーティの拡張子の不具合が原因など）。 移行時に顧客アカウントの作成時間を UTC-0 ゾーンに適切に変換するには、次の手順に従います。

1. `map-customer.xml.dist` （[!DNL Data Migration Tool]）の適切なディレクトリから `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>` ファイルに `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/map-customer.xml` 設定ファイルをコピーします。

1. `<customer_map_file>` の `config.xml` ノードを更新し、`.dist` から `map-customer.xml.dist` 拡張機能を削除します

1. `map-customer.xml` ファイルに次のルールを追加します。

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
