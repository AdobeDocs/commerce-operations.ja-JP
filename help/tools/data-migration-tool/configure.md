---
title: の設定 [!DNL Data Migration Tool]
description: 2 つの方法で [!DNL Data Migration Tool] Magento1 とMagento2 の間でデータを転送する。
exl-id: 273be997-8085-4488-a455-f6005a85b406
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 0%

---

# の設定 [!DNL Data Migration Tool]

インストール後、 [!DNL Data Migration Tool]の場合、次のディレクトリにはマッピングファイルと設定ファイルが含まれます。

* Magento Open Source:
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-opensource`:Magento Open Source1 からMagento Open Source2 への移行のための設定とスクリプト

* Adobe Commerce:
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-commerce`:Magento Open Source1 からAdobe Commerce 2 への移行の設定とスクリプト
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/commerce-to-commerce`:Adobe Commerce 1 からAdobe Commerce 2 への移行の設定とスクリプト

上記のディレクトリには、サポートされている各バージョン用のサブディレクトリが含まれています。

## 移行の設定

次の 2 つの方法で [!DNL Data Migration Tool]:

* の設定 [!DNL Data Migration Tool] 別のモジュール内（推奨）
* を [!DNL Data Migration Tool] 設定 `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/` ディレクトリ。

ソース管理を使用して移行設定を管理し、導入に使用するには、別のモジュールを作成する必要があります。
を実行する予定がある場合、 [!DNL Data Migration Tool] ローカルのみ、 `<your Magento 2 install dir>/vendor/magento/data-migration-tool/` ディレクトリを直接使用します。

### 別のモジュールでの移行の設定

データを移行する前に、Magento2 モジュールを作成する必要があります。

1. Magento2 モジュールを作成します。

   * `<your Magento 2 install dir>/app/code/Vendor/Migration/composer.json`

   ```json
   {
       "name": "vendor/migration",
       "description": "Providing config for migration",
       "config": {
           "sort-packages": true
       },
       "require": {
           "magento/framework": "*",
           "magento/data-migration-tool": "*"
       },
       "type": "magento2-module",
       "autoload": {
           "files": [
               "registration.php"
           ],
           "psr-4": {
               "Vendor\\Migration\\": ""
           }
       },
       "version": "1.0.0"
   }
   ```

   * `<your Magento 2 install dir>/app/code/Vendor/Migration/registration.php`

   ```php
   <?php
   
   \Magento\Framework\Component\ComponentRegistrar::register(
       \Magento\Framework\Component\ComponentRegistrar::MODULE,
       'Vendor_Migration',
       __DIR__
   );
   ```

   * `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/module.xml`

   ```xml
   <?xml version="1.0"?>
   
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           xsi:noNamespaceSchemaLocation="urn:magento:framework:Module/etc/module.xsd">
       <module name="Vendor_Migration" setup_version="1.0.0">
           <sequence>
               <module name="Magento_DataMigrationTool"/>
           </sequence>
       </module>
   </config>
   ```

1. を `config.xml.dist` 設定ファイルを [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>`) を `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/config.xml` ファイル。

   例えば、 `Magento 1.9.3.6 Community Edition` から `Magento 2 Open Source`:

   ```bash
   cd <your Magento 2 install dir>
   ```

   ```bash
   cp vendor/magento/data-migration-tool/etc/opensource-to-opensource/1.9.3.6/config.xml.dist app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.3.6/config.xml
   ```

1. 内 `config.xml` ファイルにアクセスする場合は、M1 および M2 データベースと暗号化キーにアクセスの詳細を設定する必要があります。

1. M1 ストアにカスタムの変更がある場合は、残りの設定ファイルをMagento1 ストアのカスタマイズにマッピングする必要があります。 詳しくは、 [設定ファイルとマッピングファイルの操作](#migration-config).

### での移行の設定 `vendor` フォルダー

データを移行する前に、 `config.xml` 指定したサンプルの設定ファイル。

次の手順で [!DNL Data Migration Tool] 移行の場合：

1. アプリケーションサーバーに、 [ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md).

1. 次のディレクトリに移動します。

   ```bash
   <your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>
   ```

1. 次のコマンドを入力して、 `config.xml` 用意されているサンプルから：

   ```bash
   cp config.xml.dist config.xml
   ```

1. 開く `config.xml` をクリックします。

1. 少なくとも、config.xml ファイルには、M1 および M2 データベースへのアクセスの詳細と暗号化キーが含まれている必要があります。

   ```xml
   <source>
      <database host="127.0.0.1" name="magento1" user="root"/>
   </source>
   <destination>
      <database host="127.0.0.1" name="magento2" user="root"/>
   </destination>
   <options>
      <crypt_key />
   </options>
   ```

   この &lt;crypt_key> タグに値を含める必要があります。 これは、 `<key>` タグに含める必要があります。このタグは、Magento1 インスタンスのapp/etc/local.xmlファイルにあります。

   オプションのパラメーター：

   * データベースユーザーのパスワード： `password=<password>`
   * データベースのカスタムポート： `port=<port>`
   * テーブルのプレフィックス： `<source_prefix>`, `<dest_prefix>`

   例えば、データベース所有者のユーザー名が `root` パスワード `pass` また、 `magento1` Magento1 データベースで、次のを使用します。 `config.xml`:

   ```xml
   <source>
      <database host="127.0.0.1" name="magento1" user="root" password="pass"/>
   </source>
   <destination>
      <database host="127.0.0.1" name="magento2" user="root" password="pass"/>
   </destination>
   <options>
      <source_prefix>magento1</source_prefix>
      <crypt_key>f3e25abe619dae2387df9fs594f01985</crypt_key>
   </options>
   ```

終了したら、変更を `config.xml` をクリックし、テキストエディタを終了します。

### TLS プロトコルを使用した接続

TLS プロトコルを使用して（つまり、公開/秘密鍵を使用して）データベースに接続することもできます。 次のオプション属性を `database` 要素：

* `ssl_ca`
* `ssl_cert`
* `ssl_key`

例：

```xml
<source>
    <database host="localhost" name="magento1" user="root" ssl_ca="/path/to/file" ssl_cert="/path/to/file" ssl_key="/path/to/file"/>
</source>
<destination>
    <database host="localhost" name="magento2" user="root" ssl_ca="/path/to/file" ssl_cert="/path/to/file" ssl_key="/path/to/file"/>
</destination>
```

## 設定ファイルとマッピングファイルの操作

この [!DNL Data Migration Tool] uses *マッピングファイル* Magento1 とMagento2 の間でカスタム・データベース・マッピングを実行するには、次の手順を実行します。

* テーブル名の変更

* フィールド名の変更

* テーブルまたはフィールドを無視する

* フィールドのデータ転送をMagento2 形式に適応させる

サポートされるMagentoバージョンのマッピングファイルは、 `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc`

マッピング・ファイルを使用する手順は、次のとおりです。

1. コピー元 `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>/` から `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/` をクリックし、 `.dist` 拡張子。

1. で新しくコピーしたファイルのパスを更新します。 `<options>` のノード `config.xml`. 更新されたパスは、次のいずれかである必要があります。

   1. 絶対ファイルパス、e.g. `/var/www/html/app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. magento/data-migration-tool モジュールの相対ファイルパス： `etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. Magentoのルート相対ファイルパス： `app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`

この `<Magento 2 dir>/vendor/magento/data-migration-tool/etc` および `<Magento 2 dir>/vendor/magento/data-migration-tool/etc/<ce version>` ディレクトリには、次の設定ファイルが含まれます。

ただし、 `map.xml.dist` ファイルほとんどの場合、次の表は各マッピングと他のファイルについて説明します。

| マッピングファイル名 | 説明 |
| --- | --- |
| `class-map.xml.dist` | Magento1 とMagento2 間のクラスマッピングの辞書 |
| `config.xml.dist` | Magento1 とMagento2 のデータベース設定、ステップ設定、およびマッピングファイルへのリンクを指定するメイン設定ファイル |
| *Adobe Commerceのみ*. `customer-attr-document-groups.xml.dist` | カスタム顧客属性ステップで使用されるテーブルのリスト。 |
| *Adobe Commerceのみ*. `customer-attr-map.xml.dist` | カスタム顧客属性ステップで使用されるマップファイル。 |
| `deltalog.xml.dist` | データベースルーチンの設定に必要なテーブルのリストが含まれます。 |
| `eav-attribute-groups.xml.dist` | EAV ステップで使用される属性のリストが含まれます。 |
| `eav-document-groups.xml.dist` | EAV ステップで使用されるテーブルのリストが含まれます。 |
| `log-document-groups.xml.dist` | 「ログステップ」で使用されるテーブルのリストが含まれます。 |
| `map-eav.xml.dist` | EAV ステップで使用されるマップファイル。 |
| `map-log.xml.dist` | ログマッピングファイル。 |
| *Adobe Commerceのみ*. `map-sales.xml.dist` | SalesOrder ステップで使用されるマップファイル。 |
| `map.xml.dist` | マップ手順に必要なマッピングファイル。 |
| `settings.xml.dist` | 移行に必要なルールを指定する移行設定ファイルを設定しています `core_config_data` 表。 |
| `customer-attribute-groups.xml.dist` | 顧客属性ステップで使用される属性のリストが含まれます。 |
| `customer-document-groups.xml.dist` | 顧客属性ステップで使用されるテーブルのリストが含まれます。 |
| `map-customer.xml.dist` | 顧客属性ステップで使用されるマップファイル。 |
| `order-grids-document-groups.xml.dist` | OrderGrids ステップで使用されるテーブルのリストが含まれます。 |
| `map-document-groups.xml.dist` | データ挿入時に重複が発生した場合に更新するフィールドを定義します |
| `map-stores.xml.dist` | ストアステップで使用されるマップファイル。 |
| `map-tier-price.xml.dist` | 階層価格ステップで使用されるマップファイル。 |
| *Adobe Commerceのみ*. `visual_merchandiser_map.xml.dist` | VisualMerchandiser ステップで使用されるマップファイル。 |
| *Adobe Commerceのみ*. `visual_merchandiser_attribute_groups.xml.dist` | VisualMerchandiser ステップで使用される属性のリストが含まれます。 |
| *Adobe Commerceのみ*. `visual_merchandiser_document_groups.xml.dist` | VisualMerchandiser ステップで使用されるテーブルのリストが含まれます。 |

以下を参照してください。 [[!DNL Data Migration Tool] 技術仕様](technical-specification.md) を参照してください。
