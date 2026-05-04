---
title: ' [!DNL Data Migration Tool]を設定'
description: Magento 1とMagento 2間でデータを転送するように [!DNL Data Migration Tool] を設定する2つの方法について説明します。
exl-id: 273be997-8085-4488-a455-f6005a85b406
topic: Commerce, Migration
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '811'
ht-degree: 0%

---

# [!DNL Data Migration Tool]の設定

[!DNL Data Migration Tool]をインストールすると、次のディレクトリにマッピングファイルと設定ファイルが含まれます。

* Magento Open Source:
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-opensource`: Magento Open Source 1からMagento Open Source 2への移行用の設定とスクリプト

* Adobe Commerce:
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-commerce`: Magento Open Source 1からAdobe Commerce 2への移行用の設定とスクリプト
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/commerce-to-commerce`: Adobe Commerce 1からAdobe Commerce 2への移行用の設定とスクリプト

前述のディレクトリには、サポートされている各バージョンのサブディレクトリが含まれています。

## 移行の設定

[!DNL Data Migration Tool]を設定するには、次の2つの方法があります。

* 別のモジュールで[!DNL Data Migration Tool]を設定します（推奨）
* `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/` ディレクトリの[!DNL Data Migration Tool]設定を変更します。

ソース管理を使用して移行設定を管理し、デプロイメントに使用するには、別のモジュールを作成する必要があります。
[!DNL Data Migration Tool]をローカルでのみ実行する場合は、`<your Magento 2 install dir>/vendor/magento/data-migration-tool/` ディレクトリ内のファイルを直接編集できます。

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

1. `config.xml.dist`設定ファイルを[!DNL Data Migration Tool] （`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>`）の適切なディレクトリから`<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/config.xml` ファイルにコピーします。

   例えば、`Magento 1.9.3.6 Community Edition`を`Magento 2 Open Source`に移行する場合は次のようになります。

   ```shell
   cd <your Magento 2 install dir>
   ```

   ```shell
   cp vendor/magento/data-migration-tool/etc/opensource-to-opensource/1.9.3.6/config.xml.dist app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.3.6/config.xml
   ```

1. `config.xml` ファイルでは、アクセスの詳細をM1およびM2 データベースと暗号化キーに設定する必要があります。

1. M1 ストアにカスタム変更がある場合は、残りのコンフィギュレーションファイルをMagento 1 ストアのカスタマイズにマッピングする必要があります。 [設定ファイルとマッピングファイルの操作](#migration-config)を参照してください。

### `vendor` フォルダーでの移行の設定

データを移行する前に、提供されたサンプルから`config.xml`設定ファイルを作成する必要があります。

移行用に[!DNL Data Migration Tool]を設定するには：

1. [&#x200B; ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md)としてアプリケーションサーバーにログインするか、切り替えます。

1. 次のディレクトリに移動します。

   ```shell
   <your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>
   ```

1. 次のコマンドを入力して、提供されたサンプルから`config.xml`を作成します。

   ```shell
   cp config.xml.dist config.xml
   ```

1. `config.xml`をテキストエディターで開きます。

1. 少なくとも、config.xml ファイルには、M1およびM2 データベースへのアクセスの詳細と暗号化キーが含まれている必要があります。

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

   &lt;crypt_key> タグには値を含める必要があります。 Magento 1 インスタンスのapp/etc/local.xml ファイルにある`<key>` タグ内で見つけることができます。

   オプションのパラメーター：

   * データベース ユーザーのパスワード：`password=<password>`
   * データベース カスタム ポート：`port=<port>`
   * テーブルのプレフィックス：`<source_prefix>`、`<dest_prefix>`

   例えば、データベース所有者のユーザー名がパスワード `pass`の`root`で、Magento 1 データベースでプレフィックス `magento1`を使用している場合は、`config.xml`で次のように使用します。

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

完了したら、変更内容を`config.xml`に保存し、テキストエディターを終了します。

### TLS プロトコルを使用した接続

TLS プロトコルを使用してデータベースに接続することもできます（つまり、公開鍵と秘密鍵を使用します）。 次のオプション属性を`database`要素に追加します。

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

[!DNL Data Migration Tool]では、*マッピングファイル*&#x200B;を使用して、Magento 1とMagento 2のデータベース間でカスタムデータベースマッピングを実行できます。次の機能があります。

* テーブル名の変更

* フィールド名の変更

* テーブルまたはフィールドの無視

* フィールドのデータ転送をMagento 2形式に適応させる

サポートされているMagento バージョンのマッピングファイルは、`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc`のサブディレクトリにあります

マッピングファイルを使用するには：

1. `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>/`から`<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/`にコピーし、`.dist`拡張機能を削除します。

1. `config.xml`の`<options>` ノードで、新しくコピーしたファイルへのパスを更新します。 更新されたパスは、次のいずれかである必要があります。

   1. 絶対ファイルパス e. g. `/var/www/html/app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. magento/data-migration-tool モジュールの相対ファイルパス：`etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. Magentoのルート相対ファイルパス：`app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`

`<Magento 2 dir>/vendor/magento/data-migration-tool/etc`および`<Magento 2 dir>/vendor/magento/data-migration-tool/etc/<ce version>` ディレクトリには、次の設定ファイルが含まれています。

ほとんどの場合、`map.xml.dist` ファイルを使用していますが、各マッピングとその他のファイルについては、次の表で説明します。

| マッピングファイル名 | 説明 |
| --- | --- |
| `class-map.xml.dist` | Magento 1とMagento 2のクラスマッピングの辞書 |
| `config.xml.dist` | Magento 1およびMagento 2のデータベース設定、ステップ設定、およびマッピングファイルへのリンクを指定するメイン設定ファイル |
| *Adobe Commerceのみ*。`customer-attr-document-groups.xml.dist` | カスタム顧客属性ステップで使用されるテーブルのリスト。 |
| *Adobe Commerceのみ*。`customer-attr-map.xml.dist` | カスタム顧客属性ステップで使用されるマップファイル。 |
| `deltalog.xml.dist` | データベースルーチンの設定に必要なテーブルのリストが含まれます。 |
| `eav-attribute-groups.xml.dist` | Eav ステップで使用される属性のリストが含まれます。 |
| `eav-document-groups.xml.dist` | Eav ステップで使用されるテーブルのリストが含まれます。 |
| `log-document-groups.xml.dist` | ログステップで使用されるテーブルのリストが含まれます。 |
| `map-eav.xml.dist` | EAV ステップで使用されるマップファイル。 |
| `map-log.xml.dist` | ログマッピングファイル。 |
| *Adobe Commerceのみ*。`map-sales.xml.dist` | SalesOrder ステップで使用されるマップファイル。 |
| `map.xml.dist` | マップステップに必要なマッピングファイル。 |
| `settings.xml.dist` | `core_config_data` テーブルの移行に必要なルールを指定する移行設定ファイルを設定しています。 |
| `customer-attribute-groups.xml.dist` | 顧客属性ステップで使用される属性のリストが含まれます。 |
| `customer-document-groups.xml.dist` | 顧客属性ステップで使用されるテーブルのリストが含まれます。 |
| `map-customer.xml.dist` | 顧客属性ステップで使用されるマップファイル。 |
| `order-grids-document-groups.xml.dist` | OrderGrids ステップで使用されるテーブルのリストが含まれます。 |
| `map-document-groups.xml.dist` | データ挿入時に重複が発生したときに更新されるフィールドを定義します |
| `map-stores.xml.dist` | ストアステップで使用されるマップファイル。 |
| `map-tier-price.xml.dist` | 階層価格ステップで使用されるマップファイル。 |
| *Adobe Commerceのみ*。`visual_merchandiser_map.xml.dist` | VisualMerchandiser ステップで使用されるマップファイル。 |
| *Adobe Commerceのみ*。`visual_merchandiser_attribute_groups.xml.dist` | VisualMerchandiser ステップで使用される属性のリストが含まれます。 |
| *Adobe Commerceのみ*。`visual_merchandiser_document_groups.xml.dist` | VisualMerchandiser ステップで使用されるテーブルのリストが含まれます。 |

詳しくは、[[!DNL Data Migration Tool] 技術仕様](technical-specification.md)を参照してください。
