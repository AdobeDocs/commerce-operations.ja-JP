---
title: ' [!DNL Data Migration Tool] を設定します。'
description: Magento 1 とMagento 2 の間でデータを転送  [!DNL Data Migration Tool]  るように設定する 2 つの方法について説明します。
exl-id: 273be997-8085-4488-a455-f6005a85b406
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '808'
ht-degree: 0%

---

# [!DNL Data Migration Tool] の設定

[!DNL Data Migration Tool] をインストールすると、次のディレクトリにマッピングおよび設定ファイルが格納されます。

* Magento Open Source:
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-opensource`:Magento Open Source 1 からMagento Open Source 2 に移行するための設定とスクリプト

* Adobe Commerce:
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-commerce`:Magento Open Source 1 からAdobe Commerce 2 に移行するための設定とスクリプト
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/commerce-to-commerce`:Adobe Commerce 1 からAdobe Commerce 2 に移行するための設定とスクリプト

上記のディレクトリには、サポートされている各バージョンのサブディレクトリが含まれています。

## 移行の設定

[!DNL Data Migration Tool] を設定する方法は 2 つあります。

* [!DNL Data Migration Tool] を別のモジュールで設定する（推奨）
* [!DNL Data Migration Tool] ディレクトリの `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/` 設定を変更します。

ソース管理を使用して移行設定を管理し、デプロイメントに使用するには、別のモジュールを作成する必要があります。
[!DNL Data Migration Tool] をローカルでのみ実行する場合は、`<your Magento 2 install dir>/vendor/magento/data-migration-tool/` ディレクトリ内のファイルを直接編集できます。

### 別のモジュールでの移行の設定

データを移行する前に、Magento 2 モジュールを作成する必要があります。

1. Magento 2 モジュールを作成します。

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

1. `config.xml.dist` （[!DNL Data Migration Tool]）の適切なディレクトリから `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>` ファイルに `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/config.xml` 設定ファイルをコピーします。

   例えば、`Magento 1.9.3.6 Community Edition` を `Magento 2 Open Source` に移行する場合は、次のようになります。

   ```bash
   cd <your Magento 2 install dir>
   ```

   ```bash
   cp vendor/magento/data-migration-tool/etc/opensource-to-opensource/1.9.3.6/config.xml.dist app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.3.6/config.xml
   ```

1. `config.xml` ファイルでは、アクセスの詳細を M1 および M2 データベースと暗号化キーに設定する必要があります。

1. M1 ストアにカスタムの変更内容がある場合は、残りの設定ファイルをMagento 1 ストアのカスタマイズにマッピングする必要があります。 [&#x200B; 設定およびマッピングファイルの操作 &#x200B;](#migration-config) を参照してください。

### フォルダーでの移行 `vendor` 設定

データを移行する前に、指定されたサンプルから `config.xml` 設定ファイルを作成する必要があります。

[!DNL Data Migration Tool] を移行用に設定するには：

1. [&#x200B; ファイルシステムの所有者 &#x200B;](../../installation/prerequisites/file-system/overview.md) としてアプリケーションサーバーにログインするか、に切り替えます。

1. 次のディレクトリに変更します。

   ```bash
   <your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>
   ```

1. 次のコマンドを入力して、提供されたサンプルから `config.xml` を作成します。

   ```bash
   cp config.xml.dist config.xml
   ```

1. `config.xml` をテキストエディターで開きます。

1. 少なくとも、config.xml ファイルには、M1 および M2 データベースおよび暗号化キーへのアクセスの詳細が含まれている必要があります。

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

   &lt;crypt_key> タグには値が含まれている必要があります。 `<key>` タグ内で検索できます。このタグは、Magento 1 インスタンスのapp/etc/local.xml ファイルにあります。

   オプションのパラメーター：

   * データベース ユーザーのパスワード：`password=<password>`
   * データベースのカスタム ポート：`port=<port>`
   * テーブルのプレフィックス：`<source_prefix>`、`<dest_prefix>`

   例えば、データベース所有者のユーザー名が password `root` で `pass`、Magento 1 データベースでプレフィックス `magento1` を使用する場合は、`config.xml` で次を使用します。

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

終了したら、`config.xml` への変更を保存し、テキストエディターを終了します。

### TLS プロトコルを使用して接続

TLS プロトコルを使用して（つまり、公開/非公開暗号化キーを使用して） データベースに接続することもできます。 `database` 要素に次のオプションの属性を追加します。

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

この [!DNL Data Migration Tool] では *マッピングファイル* を使用して、Magento 1 データベースとMagento 2 データベースの間で、次のようなカスタムデータベースマッピングを実行できます。

* テーブル名の変更

* フィールド名の変更

* テーブルまたはフィールドの無視

* フィールドのデータをMagento 2 形式に変換する

サポートされているMagento バージョンのマッピングファイルは、`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc` のサブディレクトリにあります

マッピングファイルを使用するには：

1. `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>/` から `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/` にコピーし、`.dist` 拡張機能を削除します。

1. `<options>` の `config.xml` ノードにある新しくコピーしたファイルへのパスを更新します。 更新されるパスは次のいずれかである必要があります。

   1. 絶対ファイルパス（例：`/var/www/html/app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`）
   1. magento/data-migration-tool モジュールの相対ファイル パス：`etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. Magentoのルート相対ファイルパス：`app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`

`<Magento 2 dir>/vendor/magento/data-migration-tool/etc` ディレクトリと `<Magento 2 dir>/vendor/magento/data-migration-tool/etc/<ce version>` ディレクトリには、次の設定ファイルが含まれています。

ほとんどの場合は `map.xml.dist` ファイルを使用しますが、次の表では各マッピングとその他のファイルについて説明しています。

| マッピングファイル名 | 説明 |
| --- | --- |
| `class-map.xml.dist` | Magento 1 とMagento 2 間のクラスマッピングの辞書 |
| `config.xml.dist` | Magento 1 およびMagento 2 データベース設定、ステップ設定、マッピングファイルへのリンクを指定するメイン設定ファイル |
| *Adobe Commerceのみ*. `customer-attr-document-groups.xml.dist` | カスタム顧客属性ステップで使用されるテーブルのリスト。 |
| *Adobe Commerceのみ*. `customer-attr-map.xml.dist` | カスタム顧客属性手順で使用されるマップファイル。 |
| `deltalog.xml.dist` | データベース・ルーチンの設定に必要なテーブルのリストが含まれます。 |
| `eav-attribute-groups.xml.dist` | Eav ステップで使用される属性のリストが含まれます。 |
| `eav-document-groups.xml.dist` | Eav ステップで使用されるテーブルのリストが含まれます。 |
| `log-document-groups.xml.dist` | ログステップで使用されるテーブルのリストが含まれます。 |
| `map-eav.xml.dist` | EAV ステップで使用されるマップファイル。 |
| `map-log.xml.dist` | ログマッピングファイル。 |
| *Adobe Commerceのみ*. `map-sales.xml.dist` | SalesOrder ステップで使用されるマップ ファイルです。 |
| `map.xml.dist` | マップステップにマッピングファイルが必要です。 |
| `settings.xml.dist` | `core_config_data` テーブルの移行に必要なルールを指定する移行構成ファイルを設定しています。 |
| `customer-attribute-groups.xml.dist` | 顧客属性ステップで使用される属性のリストが含まれます。 |
| `customer-document-groups.xml.dist` | 顧客属性ステップで使用されるテーブルのリストが含まれます。 |
| `map-customer.xml.dist` | 顧客属性手順で使用されるマップファイル。 |
| `order-grids-document-groups.xml.dist` | OrderGrids ステップで使用されるテーブルのリストが含まれます。 |
| `map-document-groups.xml.dist` | データ挿入時に重複が発生した場合に更新するフィールドを定義します |
| `map-stores.xml.dist` | ストアステップで使用されるマップファイル。 |
| `map-tier-price.xml.dist` | 階層価格手順で使用されるマップ ファイルです。 |
| *Adobe Commerceのみ*. `visual_merchandiser_map.xml.dist` | VisualMerchandiser ステップで使用されるマップファイル。 |
| *Adobe Commerceのみ*. `visual_merchandiser_attribute_groups.xml.dist` | VisualMerchandiser ステップで使用される属性のリストが含まれます。 |
| *Adobe Commerceのみ*. `visual_merchandiser_document_groups.xml.dist` | VisualMerchandiser ステップで使用されるテーブルのリストが含まれます。 |

詳細については、「技術仕様 [[!DNL Data Migration Tool]  を参照 &#x200B;](technical-specification.md) てください。
