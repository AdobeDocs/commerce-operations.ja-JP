---
title: データ移行のフォローアップ
description: Magento 1からMagento 2へのデータ移行が成功し、すべての機能が期待どおりに動作していることを検証する方法について説明します。
exl-id: a55f357b-6c95-49d6-b2f1-c2e403a8c85f
topic: Commerce, Migration
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
source-wordcount: '315'
ht-degree: 0%
---
# データ移行のフォローアップ

Magento 1の一部の動作とロジックは、Magento 2では異なる方法で実装されています。 [!DNL Data Migration Tool]が処理します。 移行に関して知っておくべき側面がいくつかあり、一部の機能が移行後にスムーズに動作するために、一部の手順を実行する必要がある場合があります。

## Information

### 分割データベースはサポートされていません

[!DNL Data Migration Tool]は分割データベースをサポートしていません。

### グループ価格を階層価格に変換

移行時にすべてのグループ価格が自動的に階層の価格に変換されます。

### 販売エンティティの新しい番号

注文、請求書、出荷、クレジットメモ、RMAの参照番号はそのまま移行されます。 移行後、新しいMagento 2番号割り当てルールが適用されます。 新しい販売エンティティの数値が異なります。

## 手順

### 顧客セグメントの再保存[Adobe Commerceのみ]

移行後、顧客セグメントを起動して実行するには、管理パネルから顧客セグメントを再保存する必要があります。

### タイムゾーンの設定

このツールはタイムゾーン設定を移行しないので、**ストア** > **設定** > **ロケールオプション** > **タイムゾーン**&#x200B;で、移行後にタイムゾーンを手動で設定する必要があります。

デフォルトでは、MagentoはタイムデータをUTC-0 ゾーンにデータベースに保存し、現在のタイムゾーン設定に従って表示します。 時間データが既にUTC-0以外のゾーンのデータベースに保存されている場合は、[!DNL Data Migration Tool]の`\Migration\Handler\Timezone` ハンドラーを使用して、既存の時間をUTC-0に変換する必要があります。

次の例では、Magento 1が誤ってデータベースのUTC-7 ゾーンで時間を節約しています（例えば、サードパーティの拡張機能の欠陥が原因）。 移行時に顧客アカウントの作成時間をUTC-0 ゾーンに適切に変換するには、次の手順に従います。

1. `map-customer.xml.dist`設定ファイルを[!DNL Data Migration Tool] （`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>`）の適切なディレクトリから`<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/map-customer.xml` ファイルにコピーします。

1. `config.xml`の`<customer_map_file>` ノードを更新し、`map-customer.xml.dist`から`.dist`拡張機能を削除します

1. 次のルールを`map-customer.xml` ファイルに追加します。

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
