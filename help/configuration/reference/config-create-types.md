---
title: 設定タイプ
description: Adobe Commerceで設定タイプを作成および拡張する方法について説明します。 モジュールの設定とカスタマイズの手法について説明します。
exl-id: 4390c310-b35a-431a-859f-3fd46d8ba6bf
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
source-wordcount: '603'
ht-degree: 0%
---
# 設定タイプ

## 設定タイプの拡張

既存の設定タイプを拡張するには、モジュールに設定ファイルを作成するだけで済みます。

例えば、イベントオブザーバーを追加するには、`app/code/{VendorName}/{ModuleName}/etc/events.xml`を作成し、新しいオブザーバーを宣言します。

イベント設定タイプはCommerceに存在するため、ローダーと`events.xsd`検証用スキーマは既に存在し、機能しています。

新しい`events.xml`は、モジュールから自動的に収集され、他のモジュール用に他の`events.xml` ファイルと結合されます。

## 設定タイプの作成

設定タイプを作成するには、少なくとも次を追加する必要があります。

- ローダー
- XSD検証スキーマ
- XML設定ファイル

例えば、拡張機能がそのサーバー内でのエンティティのインデックス作成方法を設定できるようにする新しい検索サーバー用のアダプタを導入するには、次のように作成します。

- ローダー
- XSD スキーマファイル
- 適切な名前の設定ファイル。 例：`search.xml`。 このファイルは、スキーマに対して読み取られ、検証されます。
- あなたの仕事に必要なその他のクラス。

>[!INFO]
>
>新しいモジュールに`search.xml` ファイルがある場合、読み込み時にファイルと結合されます。

### 使用例

設定タイプを作成するには：

1. XSD ファイルを作成します。
1. XML ファイルを作成します。
1. `di.xml`で設定オブジェクトを定義します。

   Magento_Sales モジュールの[di.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/di.xml)の次の例は、設定オブジェクトがどのように表示されるかを示しています。

   ```xml
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
   
       <type name="Magento\Sales\Model\Order\Pdf\Config\Reader">
           <arguments>
               <argument name="fileName" xsi:type="string">pdf.xml</argument>
               <argument name="converter" xsi:type="object">Magento\Sales\Model\Order\Pdf\Config\Converter</argument>
               <argument name="schemaLocator" xsi:type="object">Magento\Sales\Model\Order\Pdf\Config\SchemaLocator</argument>
           </arguments>
       </type>
   
       <virtualType name="pdfConfigDataStorage" type="Magento\Framework\Config\Data">
           <arguments>
               <argument name="reader" xsi:type="object">Magento\Sales\Model\Order\Pdf\Config\Reader</argument>
               <argument name="cacheId" xsi:type="string">sales_pdf_config</argument>
           </arguments>
       </virtualType>
   
       <type name="Magento\Sales\Model\Order\Pdf\Config">
           <arguments>
               <argument name="dataStorage" xsi:type="object">pdfConfigDataStorage</argument>
           </arguments>
       </type>
   </config>
   ```

   - 最初の型ノードは、`Converter`および`SchemaLocator`個のクラスに関連付けられたReaderのファイル名を設定します。
   - 次に、`pdfConfigDataStorage`仮想タイプノードは、[Magento\Framework\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Data.php)のインスタンスにリーダークラスをアタッチします。
   - 最後に、最後のtype ノードは、設定データの仮想タイプを[Magento\Sales\Model\Order\Pdf\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config.php) クラスに添付します。このクラスは、これらの[pdf.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/pdf.xml) ファイルから実際に値を読み取るために使用されます。

1. [Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) クラスを拡張してリーダーを定義し、次のパラメーターを書き換えます。

   ```php
   $_idAttributes // Array of node attribute IDs.
   ```

**例：**

```php
<?php
/**
 * Copyright [first year code created] Adobe
 * All Rights Reserved.
 */

namespace Vendor\ModuleName\Model\Config;

use Magento\Framework\Config\Reader\Filesystem;

class Reader extends Filesystem
{
    /**
     * List of identifier attributes for merging
     *
     * @var array
     */
    protected $_idAttributes = [
         '</path/to/node_in_your_xml_file>'        => '<identifierAttributeName>',
         '</path/to/other/node_in_your_xml_file>'  => '<identifierAttributeName>',
    ];
}
```

>[!INFO]
>
>独自のバージョンのリーダーを作成する場合は、`\Magento\Framework\Config\ReaderInterface`を実装することで作成できます。 [Magento_Analytics設定リーダー](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config/Reader.php)を参照してください

リーダーを定義した後、これを使用して設定ファイルを収集、結合、検証し、内部配列表現に変換します。

## 設定タイプの検証

各設定ファイルは、その設定タイプに固有のスキーマに対して検証されます。 例：以前のCommerce バージョンで`config.xml`に設定されていたイベントが、`events.xml`に設定されるようになりました。

設定ファイルは、同じ設定タイプに影響を与える複数のファイルを結合する前（オプション）と後の両方で検証できます。 個々のファイルと結合されたファイルの検証ルールが同じでない限り、設定ファイルを検証するための2つのスキーマを指定する必要があります。

- 個人を検証するスキーマ
- 結合されたファイルを検証するスキーマ

新しい設定ファイルには、XSD検証スキーマを添付する必要があります。 XML設定ファイルとそのXSD検証ファイルの名前は同じである必要があります。

1つのXML ファイルに2つのXSD ファイルを使用する必要がある場合、スキーマの名前は認識でき、XML ファイルに関連付けられている必要があります。
`events.xml` ファイルと最初の`events.xsd` ファイルがある場合、結合された`events.xml` ファイルのXSD ファイルの名前は`events_merged.xsd`になる可能性があります。
適切なXSD ファイルによるXML ファイルの検証を確実に行うには、XML ファイル内のXSD ファイルにUniform Resource Name （URN）を追加する必要があります。 例：

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager:etc/config.xsd">
```

IDEでは、実行時と開発時の両方で設定ファイルを検証できます。
