---
title: 設定タイプ
description: 設定タイプを作成または拡張します。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 0%

---


# 設定タイプ

## 設定タイプの拡張

既存の設定タイプを拡張するには、 [モジュール](https://glossary.magento.com/module).

例えば、イベント監視者を追加するには、 `app/code/{VendorName}/{ModuleName}/etc/events.xml` そして新しい監視者を宣言する

イベント設定タイプは Commerce に存在するので、ローダと `events.xsd` 検証スキーマは既に存在し、機能しています。

新規 `events.xml` は自動的にモジュールから収集され、他のと統合されます。 `events.xml` 他のモジュール用のファイル

## 設定タイプの作成

設定タイプを作成するには、少なくとも次を追加する必要があります。

- ローダ
- XSD 検証スキーマ
- XML 設定ファイル

例えば、 [アダプタ](https://glossary.magento.com/adapter) 拡張機能を有効にして、そのサーバーでエンティティのインデックスを作成する方法を設定する新しい検索サーバーの場合は、次を作成します。

- ローダ
- XSD スキーマファイル
- 適切な名前の設定ファイル。 例： `search.xml`. このファイルは、スキーマに対して読み取られ、検証されます。
- 作業に必要なその他のクラス。

>[!INFO]
>
>新しいモジュールに `search.xml` ファイルを読み込むと、ファイルとマージされます。

### 使用例

設定タイプを作成するには：

1. XSD ファイルを作成します。
1. XML ファイルを作成します。
1. 設定オブジェクトを `di.xml`.

   次の例は、Magento_Sales モジュールの [di.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/di.xml) は、設定オブジェクトがどのように表示されるかを示します。

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

   - 1 つ目のタイプのノードは、Readerのファイル名を設定し、 `Converter` および `SchemaLocator` クラス。
   - 次に、 `pdfConfigDataStorage` 仮想タイプノードは、リーダークラスをのインスタンスに接続します。 [Magento\Framework\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Data.php).
   - 最後に、最後のタイプのノードは、その設定データ仮想型を [Magento\Sales\Model\Order\Pdf\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config.php) クラス。これらのクラスからの値を実際に読み取るのに使用されます。 [pdf.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/pdf.xml) ファイル。

1. を拡張して読み取り装置を定義する [Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) クラスで次のパラメーターを書き換えます。

   ```php
   $_idAttributes // Array of node attribute IDs.
   ```

**例：**

```php
<?php
/**
 * Copyright © Magento, Inc. All rights reserved.
 * See COPYING.txt for license details.
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
>独自のバージョンのリーダーを作成する場合は、 `\Magento\Framework\Config\ReaderInterface`. 詳しくは、 [Magento_Analytics 設定リーダー](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config/Reader.php)

リーダーを定義したら、それを使用して、設定ファイルを収集、マージ、検証し、内部配列表現に変換します。

## 設定タイプの検証

各設定ファイルは、その設定タイプに固有のスキーマに対して検証されます。 例：イベント ( 以前のバージョンのコマースでは、 `config.xml`、で設定されました。 `events.xml`.

設定ファイルは、同じ設定タイプに影響する複数のファイルを結合する前（オプション）と後の両方で検証できます。 個々のファイルと結合されたファイルの検証ルールが同じでない限り、設定ファイルを検証する 2 つのスキーマを指定する必要があります。

- 個人を検証するスキーマ
- 結合ファイルを検証するスキーマ

新しい設定ファイルには、XSD 検証スキーマが付属している必要があります。 XML 設定ファイルとその XSD 検証ファイルの名前は同じにする必要があります。

1 つの XML ファイルに 2 つの XSD ファイルを使用する必要がある場合、スキーマの名前が認識可能で、XML ファイルに関連付けられている必要があります。
次の場合、 `events.xml` ファイルと最初の `events.xsd` ファイル、結合後の XSD ファイル `events.xml` ファイル名を指定できます `events_merged.xsd`.
適切な XSD ファイルによる XML ファイルの検証を確実におこなうには、XML ファイル内の XSD ファイルに URN (Uniform Resource Name) を追加する必要があります。 例：

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager:etc/config.xsd">
```

IDE では、実行時と開発時の両方で構成ファイルを検証できます。
