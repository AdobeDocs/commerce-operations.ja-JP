---
title: 設定タイプ
description: Adobe Commerceで設定タイプを作成および拡張する方法について説明します。 モジュールの設定とカスタマイズの手法について説明します。
exl-id: 4390c310-b35a-431a-859f-3fd46d8ba6bf
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 0%

---

# 設定タイプ

## 設定タイプの拡張

既存の設定タイプを拡張する場合は、モジュールに設定ファイルを作成するだけで済みます。

例えば、イベントオブザーバーを追加するには、`app/code/{VendorName}/{ModuleName}/etc/events.xml` を作成し、新しいオブザーバーを宣言します。

イベント設定タイプはCommerceに存在するので、ローダーと `events.xsd` 検証スキーマは既に存在し、機能しています。

新しい `events.xml` は、モジュールから自動的に収集され、他のモジュール用に他の `events.xml` ファイルと結合されます。

## 設定タイプの作成

設定タイプを作成するには、少なくとも次を追加する必要があります。

- 積込人
- XSD 検証スキーマ
- XML 設定ファイル

たとえば、新しい検索サーバーにアダプタを導入して、拡張機能がそのサーバーでエンティティのインデックスを作成する方法を構成できるようにするには、次のように作成します。

- 積込人
- XSD スキーマファイル
- 適切な名前の設定ファイル。 例：`search.xml`。 このファイルは、スキーマに対して読み取られ、検証されます。
- 作業に必要なその他のクラス。

>[!INFO]
>
>新しいモジュールに `search.xml` ファイルがある場合、そのモジュールは読み込み時にファイルと結合されます。

### 使用例

設定タイプを作成するには、次の手順を実行します。

1. XSD ファイルを作成します。
1. XML ファイルを作成します。
1. `di.xml` で設定オブジェクトを定義します。

   次のMagento_Sales モジュールの [di.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/di.xml) の例は、設定オブジェクトがどのように表示されるかを示しています。

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

   - 最初のタイプノードでは、Readerのファイル名、関連付けられた `Converter` および `SchemaLocator` クラスを設定します。
   - 次に、`pdfConfigDataStorage` 仮想タイプノードは、リーダークラスを [Magento\Framework\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Data.php) のインスタンスにアタッチします。
   - 最後に、設定データの仮想タイプを最後のタイプノードで [Magento\Sales\Model\Order\Pdf\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config.php) クラスに添付します。このクラスは、これらの [pdf.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/pdf.xml) ファイルから実際にの値を読み取るために使用されます。

1. [Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) クラスを拡張してリーダーを定義し、次のパラメーターを書き換えます：

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
>独自のバージョンのリーダーを作成する場合は、`\Magento\Framework\Config\ReaderInterface` を実装します。 [Magento_Analytics 設定リーダーを参照してください &#x200B;](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config/Reader.php)

リーダーを定義した後、それを使用して、設定ファイルを収集、結合、検証および内部配列表現に変換します。

## 設定タイプの検証

各設定ファイルは、その設定タイプに固有のスキーマに対して検証されます。 例：以前のCommerce バージョンで `config.xml` で設定されたイベントが、`events.xml` で設定されるようになりました。

設定ファイルは、同じ設定タイプに影響を与える複数のファイルを結合する前（オプション）と後の両方で検証できます。 個々のファイルと結合ファイルの検証ルールが同じでない限り、設定ファイルを検証するには、次の 2 つのスキーマを指定する必要があります。

- 個人を検証するためのスキーマ
- 結合ファイルを検証するスキーマ

新しい設定ファイルには、XSD 検証スキーマを伴う必要があります。 XML 設定ファイルと XSD 検証ファイルには、同じ名前を付ける必要があります。

1 つの XML ファイルに 2 つの XSD ファイルを使用する必要がある場合、スキーマの名前は認識でき、XML ファイルに関連付けられている必要があります。
`events.xml` ファイルと最初の `events.xsd` ファイルがある場合、結合された `events.xml` ファイルの XSD ファイルの名前は `events_merged.xsd` になります。
適切な XSD ファイルで XML ファイルを確実に検証するには、XML ファイル内の XSD ファイルに URN （Uniform Resource Name）を追加する必要があります。 例：

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager:etc/config.xsd">
```

IDE は、実行時と開発時の両方で構成ファイルを検証できます。
