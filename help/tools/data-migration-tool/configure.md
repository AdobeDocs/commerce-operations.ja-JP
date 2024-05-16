---
title: の設定 [!DNL Data Migration Tool]
description: を設定する 2 つの方法について説明します [!DNL Data Migration Tool] Magento1 とMagento2 との間でデータを転送する。
exl-id: 273be997-8085-4488-a455-f6005a85b406
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '808'
ht-degree: 0%

---

# の設定 [!DNL Data Migration Tool]

をインストールしたら、 [!DNL Data Migration Tool]：次のディレクトリには、マッピングおよび設定ファイルが含まれています。

* Magento Open Source:
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-opensource`:Magento Open Source 1 からMagento Open Source 2 へ移行するための設定とスクリプト

* Adobe Commerce:
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-commerce`:Magento Open Source 1 からAdobe Commerce 2 に移行するための設定とスクリプト
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/commerce-to-commerce`:Adobe Commerce 1 からAdobe Commerce 2 に移行するための設定とスクリプト

上記のディレクトリには、サポートされている各バージョンのサブディレクトリが含まれています。

## 移行の設定

を設定する方法は 2 つあります [!DNL Data Migration Tool]:

* の設定 [!DNL Data Migration Tool] 別のモジュールで（推奨）
* 変更： [!DNL Data Migration Tool] での設定 `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/` ディレクトリ。

ソース管理を使用して移行設定を管理し、デプロイメントに使用するには、別のモジュールを作成する必要があります。
を実行する予定がある場合 [!DNL Data Migration Tool] ローカルでのみ、内のファイルを `<your Magento 2 install dir>/vendor/magento/data-migration-tool/` ディレクトリを直接。

### 別のモジュールでの移行の設定

データをマイグレーションする前に、Magento 2 モジュールを作成する必要があります。

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

1. をコピーします `config.xml.dist` の適切なディレクトリからの設定ファイル [!DNL Data Migration Tool] （`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>`）を追加して、 `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/config.xml` ファイル。

   例えば、を移行する場合 `Magento 1.9.3.6 Community Edition` 対象： `Magento 2 Open Source`:

   ```bash
   cd <your Magento 2 install dir>
   ```

   ```bash
   cp vendor/magento/data-migration-tool/etc/opensource-to-opensource/1.9.3.6/config.xml.dist app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.3.6/config.xml
   ```

1. が含まれる `config.xml` ファイルの場合、M1 および M2 データベースと暗号化キーへのアクセスの詳細を設定する必要があります。

1. M1 ストアにカスタムの変更がある場合は、残りの設定ファイルをMagento 1 ストアのカスタマイズにマッピングする必要があります。 参照： [設定ファイルとマッピングファイルの操作](#migration-config).

### での移行の設定 `vendor` フォルダー

データを移行する前に、を作成する必要があります `config.xml` 提供されたサンプルの設定ファイル。

を設定するには [!DNL Data Migration Tool] 移行の場合：

1. アプリケーションサーバーにとしてログインするか、 [ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md).

1. 次のディレクトリに変更します。

   ```bash
   <your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>
   ```

1. 次のコマンドを入力して、 `config.xml` 提供されたサンプルから：

   ```bash
   cp config.xml.dist config.xml
   ```

1. 開く `config.xml` テキストエディター。

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

   この &lt;crypt_key> タグには値を含める必要があります。 内で見つけることができます。 `<key>` Magento 1 インスタンスのapp/etc/local.xml ファイルにあるタグ。

   オプションのパラメーター：

   * データベース ユーザーのパスワード： `password=<password>`
   * データベースのカスタム ポート： `port=<port>`
   * テーブルのプレフィックス： `<source_prefix>`, `<dest_prefix>`

   例えば、データベース所有者のユーザー名がの場合 `root` パスワードを使用 `pass` また、プレフィックスを使用します `magento1` Magento1 データベースで、次のコマンドを使用します。 `config.xml`:

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

終了したら、変更をに保存します `config.xml` をクリックして、テキストエディターを終了します。

### TLS プロトコルを使用して接続

TLS プロトコルを使用して（つまり、公開/非公開暗号化キーを使用して） データベースに接続することもできます。 次のオプション属性をに追加します `database` 要素：

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

この [!DNL Data Migration Tool] 使用 *マッピングファイル* Magento1 とMagento2 のデータベース間でカスタム・データベース・マッピングを実行できるようにするには、次の手順に従います。

* テーブル名の変更

* フィールド名の変更

* テーブルまたはフィールドの無視

* フィールドのデータをMagento 2 形式に変換する

サポートされているMagentoバージョンのマッピングファイルは、のサブディレクトリにあります。 `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc`

マッピングファイルを使用するには：

1. コピー元 `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>/` 対象： `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/` を削除します `.dist` 拡張機能。

1. の新しくコピーしたファイルへのパスを更新します。 `<options>` ノード / `config.xml`. 更新されるパスは次のいずれかである必要があります。

   1. 絶対ファイルパス（例：） `/var/www/html/app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. magento/data-migration-tool モジュールの相対ファイルパス： `etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. Magentoのルート相対ファイルパス： `app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`

この `<Magento 2 dir>/vendor/magento/data-migration-tool/etc` および `<Magento 2 dir>/vendor/magento/data-migration-tool/etc/<ce version>` ディレクトリには、次の設定ファイルが含まれています。

を使用している場合でも、 `map.xml.dist` ファイルほとんどの場合、次の表では、各マッピングとその他のファイルについて説明します。

| マッピングファイル名 | 説明 |
| --- | --- |
| `class-map.xml.dist` | Magento 1 とMagento 2 間のクラスマッピングの辞書 |
| `config.xml.dist` | Magento1 およびMagento2 のデータベース構成、ステップ構成、およびマッピング・ファイルへのリンクを指定するメイン構成ファイル |
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
| `settings.xml.dist` | の移行に必要なルールを指定する移行設定ファイルの設定 `core_config_data` テーブル。 |
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

以下を参照してください。 [[!DNL Data Migration Tool] 技術仕様](technical-specification.md) を参照してください。
