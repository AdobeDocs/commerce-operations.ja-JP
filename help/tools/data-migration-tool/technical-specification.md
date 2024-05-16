---
title: '''[!DNL Data Migration Tool] 技術仕様'
description: の実装の詳細について説明します [!DNL Data Migration Tool] Magento1 とMagento2 間でデータを転送する際の拡張方法。
exl-id: fec3ac3a-dd67-4533-a29f-db917f54d606
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '2098'
ht-degree: 0%

---

# [!DNL Data Migration Tool] 技術仕様

この節では、次の内容について説明します [!DNL Data Migration Tool] 実装の詳細と機能の拡張方法。

## リポジトリ

にアクセスするには [!DNL Data Migration Tool] ソースコードについては、GitHub を参照してください。 [リポジトリ](https://github.com/magento/data-migration-tool).

## 必要システム構成

この [必要システム構成](../../installation/system-requirements.md) の場合 [!DNL Data Migration Tool] Magento 2 と同じです。

## 内部構造

### ディレクトリ構造

以下の図は、のディレクトリ構造を表しています。 [!DNL Data Migration Tool]:

```terminal
├── etc                                    --- all configuration files
│   ├── opensource-to-opensource            --- configuration files for migration from Magento Open Source 1 to Magento Open Source 2
│   │   ├── 1.9.1.1
│   │   │   ├── config.xml.dist
│   │   │   └── map.xml.dist
│   │   ├── 1.9.2.0
│   │   │   ├── config.xml.dist
│   │   │   └── map.xml.dist
│   │   ├── ........
│   │   ├── class-map.xml.dist
│   │   ├── deltalog.xml.dist
│   │   └── settings.xml.dist
│   │   ├── ........
│   ├── opensource-to-commerce              --- configuration files for migration from Magento Open Source 1 to Adobe Commerce 2
│   ├── commerce-to-commerce                --- configuration files for migration from Adobe Commerce 1 to Adobe Commerce 2
│   ├── class-map.xsd
│   ├── config.xsd
│   ├── map.xsd
│   └── settings.xsd
├── src
│   └── Migration
│       ├── App                             --- application framework
│       ├── Console
│       ├── Handler                         --- handlers are used by map files
│       │   ├── AbstractHandler.php
│       │   ├── AddPrefix.php
│       │   ├── ConvertIp.php
│       │   ├── ........
│       ├── Logger
│       ├── Reader
│       ├── Mode
│       │   ├── AbstractMode.php
│       │   ├── Data.php
│       │   ├── Delta.php
│       │   └── Settings.php
│       ├── ResourceModel                   --- contains adapter for connection to data storage and classes to work with structured data
│       │   ├── Adapter
│       │   │   └── Mysql.php
│       │   ├── AbstractCollection.php
│       │   ├── AbstractResource.php
│       │   ├── AdapterInterface.php
│       │   ├── Destination.php
│       │   ├── Document.php
│       │   ├── Record.php
│       │   ├── Source.php
│       │   └── Structure.php
│       ├── Config.php
│       ├── Exception.php
│       └── Step                            --- functionality for migrating specific data
│           ├── Eav
│           │   ├── Data.php
│           │   ├── Helper.php
│           │   ├── InitialData.php
│           │   ├── Integrity.php
│           │   └── Volume.php
│           ├── Map
│           │   ├── Data.php
│           │   ├── Delta.php
│           │   ├── Helper.php
│           │   ├── Integrity.php
│           │   └── Volume.php
│           ├── UrlRewrite
│           │   ├── Version11300to2000.php
│           │   ├── Version11410to2000.php
│           │   └── Version191to2000.php
│           ├── ..........
└── tests
    ├── integration
    ├── static
    └── unit
```

## エントリポイント

移行プロセスを実行するスクリプトは、次の場所にあります。 `magento-root/bin/magento`.

## 設定

設定用のスキーマ `config.xsd` ファイルはにあります。 `etc/` ディレクトリ。 デフォルトの設定ファイル （`config.xml.dist`）がMagento 1.x の各バージョンに対して作成されます。の下の別のディレクトリにあります `etc/`.

デフォルトの設定ファイルは、カスタムの設定ファイルに置き換えることができます（を参照） [コマンド構文](migrate-data/overview.md#command-syntax)）に設定します。

設定ファイルの構造は次のとおりです。

```xml
<config xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="config.xsd">
    <steps mode="settings">
        <step title="Settings step">
            <integrity>Migration\Step\Settings</integrity>
            <data>Migration\Step\Settings</data>
        </step>
    </steps>
    <steps mode="data">
        <step title="Map step">
            <integrity>Migration\Step\Map\Integrity</integrity>
            <data>Migration\Step\Map\Data</data>
            <volume>Migration\Step\Map\Volume</volume>
        </step>
        ...
    </steps>
    <steps mode="delta">
        <step title="Map step">
            <delta>Migration\Step\Map\Delta</delta>
            <volume>Migration\Step\Map\Volume</volume>
        </step>
        ...
    </steps>
    <source>
        <database host="localhost" name="magento1" user="root" password=""/>
    </source>
    <destination>
        <database host="localhost" name="magento2" user="root" password=""/>
    </destination>
    <options>
        <map_file>map-file.xml</map_file>
        <settings_map_file>settings-map-file.xml</settings_map_file>
        <bulk_size>100</bulk_size>
        <custom_option>custom_option_value</custom_option>
        <source_prefix />
        <dest_prefix />
        ...
    </options>
</config>
```

* 手順 – 移行中に処理されるすべての手順を説明します

* ソース – データソースの設定。 使用可能なソースの種類：データベース

* 宛先 – データ宛先の設定。 使用可能な宛先のタイプ : データベース

* options - パラメーターのリスト。 必須（map_file、settings_map_file、bulk_size）とオプション（custom_option、resource_adapter_class_name、prefix_source、prefix_dest、log_file）の両方のパラメーターが含まれる

Magentoがデータベース テーブルのプレフィックスと共にインストールされた場合にプレフィックス オプションを変更します。 Magento1 およびMagento2 のデータベースに対して設定できます。 それに応じて、「source_prefix」および「dest_prefix」設定オプションを使用します。

設定データには、を使用してアクセスできます `\Migration\Config` クラス。

## 使用可能な操作の手順

| 文書 | フィールド |
|---|---|
| `step` | Steps ノード内の第 2 レベルのノード。 関連する手順の説明を次で指定する必要があります `title` 属性。 |
| `integrity` | 整合性チェックを行う PHP クラスを指定します。 テーブルのフィールド名、型、その他の情報を比較して、Magento 1 と 2 のデータ構造の互換性を確認します。 |
| `data` | データチェックを行う PHP クラスを指定します。 Magento1 からMagento2 にテーブル単位でデータを転送します。 |
| `volume` | ボリュームチェックを行う PHP クラスを指定します。 テーブル間のレコード数を比較して、転送が成功したことを確認します。 |
| `delta` | 差分チェックを行う PHP クラスを指定します。 完全なデータ移行後に、Magento1 からMagento2 に差分を転送します。 |

## ソース・データベースの情報属性

| 文書 | フィールド | 必須？ |
|---|---|---|
| `name` | Magento1 サーバのデータベース名。 | はい |
| `host` | Magento1 サーバーのホスト IP アドレス。 | はい |
| `port` | Magento1 サーバーのポート番号。 | なし |
| `user` | Magento1 データベース・サーバのユーザ名。 | はい |
| `password` | Magento1 データベースサーバーのパスワード。 | はい |
| `ssl_ca` | SSL 認証局ファイルへのパス。 | なし |
| `ssl_cert` | SSL 証明書ファイルへのパス。 | なし |
| `ssl_key` | SSL キーファイルへのパス。 | なし |

## 宛先データベース情報属性

| 文書 | フィールド | 必須？ |
|---|---|---|
| `name` | Magento2 サーバのデータベース名。 | はい |
| `host` | Magento2 サーバーのホスト IP アドレス。 | はい |
| `port` | Magento2 サーバのポート番号。 | なし |
| `user` | Magento2 データベース・サーバのユーザ名。 | はい |
| `password` | Magento2 データベースサーバーのパスワード。 | はい |
| `ssl_ca` | SSL 認証局ファイルへのパス。 | なし |
| `ssl_cert` | SSL 証明書ファイルへのパス。 | なし |
| `ssl_key` | SSL キーファイルへのパス。 | なし |

## TLS プロトコルを使用して接続

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

## ステップ内部

移行プロセスは次の手順で構成されます。

ステップは、一部の分離されたデータの移行に必要な機能を提供する単位です。 ステップは、1 つ以上のステージ（整合性チェック、データ、ボリューム・チェック、差分）で構成できます。

デフォルトでは、いくつかの手順が存在します（[マップ](#map-step), [EAV](#eav), [URL リライト](#url-rewrite-step)など）。 オプションで、独自の手順も追加できます。

ステップ関連のクラスは、src/Migration/Step ディレクトリにあります。

Step クラスを実行するには、クラスを config.xml ファイルで定義する必要があります。

```xml
<config xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="config.xsd">
    <steps mode="mode_name">
        <step title="Step Name">
            <integrity>Migration\Step\StepName\Integrity</integrity>  <!-- integrity check stage of the step -->
            <data>Migration\Step\StepName\Data</data>
            <volume>Migration\Step\StepName\Volume</volume>
        </step>
        ...
    </steps>
    ...
</config>
```

すべてのステージクラスは、StageInterface を実装する必要があります。

```php
class StageClass implements StageInterface
{
  /**
   * Perform the stage
   *
   * @return bool
   */
  public function perform()
  {
  }
}
```

データステージがロールバックをサポートしている場合は、を実装する必要があります `RollbackInterface` インターフェイス。

実行中のステップのビジュアライゼーションは、Symfony の ProgressBar コンポーネントによって提供されます（ [プログレスバー](https://symfony.com/doc/current/components/console/helpers/progressbar.html)）に設定します。 このコンポーネントには、LogLevelProcessor として手順の中でアクセスします。

主な使用方法を次に示します。

```xml
$this->progress->start();
$this->progress->advance();
$this->progress->finish();
```

## ステップステージ

### 整合性チェック

各ステップでは、データソースの構造（デフォルトではMagento 1）とデータ送信先の構造（Magento 2）に互換性があることを確認する必要があります。 そうでない場合 – 互換性のないエンティティに関してエラーが表示されます。 フィールドのデータタイプが異なる場合（同じフィールドのMagento 1 に 10 進数データタイプがあり、Magento 2 に整数がある場合）、警告メッセージが表示されます（マップファイルで説明されている場合を除く）。

### データ転送

整合性チェックに合格した場合、データ転送は実行中です。 エラーが表示された場合は、ロールバックが実行され、Magento 2 の以前の状態に戻ります。 ステップクラスがを実装する場合 `RollbackInterface` の場合、エラーが発生すると rollback メソッドが実行されます。

### ボリュームチェック

データ移行後に、ボリュームチェックを使用すると、すべてのデータが正しく転送されたかどうかを確認できます。

### Delta 配信

メイン移行後に追加された残りのデータは、差分機能によって配信されます。

## 実行モード

ツールは、特に次の 3 つの異なるモードで実行する必要があります。

1. 設定 – システム設定の移行
1. データ – データの主な移行
1. delta - メイン移行後に追加された残りのデータの移行

各モードには、実行する独自のステップのリストがあります。 config.xml を参照

### 設定の移行モード

このツールの設定移行モードは、次のエンティティの転送に使用されます：

1. Web サイト、ストア、ストアビュー。
1. ストア設定（主に M2 でのストア/設定、または M1 でのシステム/設定）

すべてのストア設定では、データがデータベース内の core_config_data テーブルに保持されます。 settings.xml ファイルには、移行プロセス中に適用されるこのテーブルのルールが含まれています。 このファイルは、無視、名前変更、または値の変更が必要な設定を記述します。 settings.xml ファイルの構造は次のとおりです。

```xml
<?xml version="1.0" encoding="UTF-8"?>
<settings xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="settings.xsd">
    <key>
        <ignore>
            <path>path/to/ignore*</path>
        </ignore>
        <rename>
            <path>path/to/rename</path>
            <to>new/path/renamed</to>
        </rename>
    <key>
    <value>
        <transform>
            <path>some/key/to/change</path>
            <handler class="Some\Handler\Class"/>
        </transform>
    </value>
</settings>
```

ノードの下で `<key>` には、「path」列で機能するルールがあります `core_config_data` テーブル。 `<ignore>` ルールにより、ツールは一部の設定を転送できません。 このノードではワイルドカードを使用できます。 にリストされていないその他すべての設定 `<ignore>` ノードが移行されます。 設定へのパスがMagento 2 で変更された場合は、に追加する必要があります。 `//key/rename` ノード（古いパスはにあります） `//key/rename/path` ノードと新しいパスはで示されます。 `//key/rename/to` ノード。

ノードの下で `<value>`には、「値」列で機能するルールがあります `core_config_data` テーブル。 これらのルールは、ハンドラー（を実装するクラス）によって設定の値を変換することを目的としています `Migration\Handler\HandlerInterface`）を選択し、Magento 2 に適応させます。

### データ移行モード

このモードでは、ほとんどのデータが移行されます。 データを移行する前に、整合性チェックステージが各手順で実行されます。 整合性チェックに合格すると、 [!DNL Data Migration Tool] deltalog テーブル （プレフィックス付き）をインストールします `m2_cl_*`）と、Magento1 データベースへの対応するトリガーを指定し、手順のデータ移行ステージを実行します。 移行がエラーなしで完了すると、ボリュームチェックがデータの整合性をチェックします。 ライブストアを移行すると、警告メッセージが表示される場合があります。 デルタ移行では、この増分データが処理されるので、心配する必要はありません。 最も役に立つ移行手順は、マップ、URL 書き換え、EAV です。

#### マップ ステップ

マップステップは、ほとんどのデータをMagento 1 からMagento 2 に転送する役割を果たします。 この手順では、にある map.xml ファイルから手順を読み取ります `etc/` ディレクトリ）に保存します。 ファイルは、ソース（Magento 1）とデスティネーション（Magento 2）のデータ構造の違いを示します。 Magento 2 に存在しないMagentoに属するテーブルまたはフィールドが拡張機能 1 に含まれている場合、マップステップで無視するためにこれらのエンティティをここに配置できます。 それ以外の場合は、エラーメッセージが表示されます。

マップ ファイルには次の形式があります。

```xml
<?xml version="1.0" encoding="UTF-8"?>
<map xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="map.xsd">
    <source>
        <document_rules>
            <ignore>
                <document>some_document2</document>
            </ignore>
            <rename>
                <document>some_document</document>
                <to>some_dest_document</to>
            </rename>
            <log_changes>
                <document key="primary_key">some_dest_document</document>
            </log_changes>
        </document_rules>

        <field_rules>
            <move>
                <field>some_document1.field1</field>
                <to>some_document1.field2</to>
            </move>
            <ignore>
                <field>some_document3.field8</field>
            </ignore>
            <transform>
                <field>some_document1.field1</field>
                <handler class="\Migration\Handler\Convert">
                    <param name="map" value="[value1:value2;value3:value4;value5:value6;]" />
                </handler>
            </transform>
        </field_rules>
    </source>
    <destination>
        <document_rules>
            <ignore>
                <document>some_document8</document>
            </ignore>
        </document_rules>

        <field_rules>
            <transform>
                <field>some_document5.field3</field>
                <handler class="\Migration\Handler\SetValue">
                    <param name="value" value="10" />
                </handler>
            </transform>
        </field_rules>
    </destination>
</map>
```

領域：

* *ソース* - ソースデータベースのルールを含みます

* *宛先*  – 宛先データベースのルールを含む

オプション：

* *無視*  – このオプションでマークされたドキュメント、フィールドまたはデータタイプは無視されます

* *名前変更*  – 異なる名前を持つドキュメント間の名前リレーションを記述します。 宛先ドキュメント名がソースドキュメント名と異なる場合は、名前変更オプションを使用して、宛先テーブル名と同様のソースドキュメント名を設定できます

* *を移動*  – 指定したフィールドをソースドキュメントからターゲットドキュメントに移動するためのルールを設定します。 メモ：宛先ドキュメント名は、ソースドキュメント名と同じである必要があります。 移動元と移動先のドキュメントの名前が異なる場合 – 移動したフィールドを含むドキュメントには、名前の変更オプションを使用する必要があります

* *変換* - ハンドラーに記載されている動作に従ってユーザーがフィールドを移行できるオプション

* *ハンドラー* - フィールドの変換動作を記述します。 ハンドラーを呼び出すには、 `<handler>` タグ。 の使用 `<param>` ハンドラーに渡すパラメーター名と値データを指定したタグ

**ソース** 使用可能な操作：

| 文書 | フィールド |
|--- |--- |
| 名前変更を無視 | 移動変換を無視 |

**宛先** 使用可能な操作：

| 文書 | フィールド |
|--- |--- |
| 無視 | 変換を無視 |

#### ワイルドカード

類似した部品を持つドキュメントを無視するには`document_name_1`, `document_name_2`）に設定されている場合は、ワイルドカード機能を使用できます。 Put `*` 繰り返し部分の代わりにシンボル （`document_name_*`）を指定すると、このマスクを満たすすべてのソースドキュメントまたはターゲットドキュメントがマスクの対象になります。

#### URL 書き換え手順

Magento 1 で開発されたMagento 2 と互換性のないアルゴリズムが多数あるため、この手順は複雑です。 Magento 1 のバージョンが異なれば、異なるアルゴリズムを使用できます。 したがって、Step/UrlRewrite フォルダーには、特定のバージョンのMagento用に開発されたクラスがあり、Migration\Step\UrlRewrite\Version191to2000はその 1 つです。 URL 書き換えデータをMagento 1.9.1 からMagento 2 に転送できます。

#### EAV ステップ

この手順により、すべての属性（製品、顧客、RMA）がMagento1 からMagento2 に転送されます。 データの処理の特定のケースに対して、map.xml ファイルのルールと類似したルールを含む map-eav.xml ファイルを使用します。

この手順で処理されるテーブルの一部：

* `eav_attribute`
* `eav_attribute_group`
* `eav_attribute_set`
* `eav_entity_attribute`
* `catalog_eav_attribute`
* `customer_eav_attribute`
* `eav_entity_type`

### 差分移行モード

メイン移行後に、（ストアフロントのお客様などによって）Magento1 データベースにデータが追加される場合がありました。 このデータをトラッキングするために、移行プロセスの最初に、テーブルのデータベーストリガーを設定します。 詳しくは、を参照してください [サードパーティの拡張機能で作成されたデータを移行する](migrate-data/delta.md#migrate-data-created-by-third-party-extensions).

## データソース

Magento 1 とMagento 2 のデータソースにアクセスし、そのデータを使用して操作するには（select、update、insert、delete）、リソースフォルダーには多くのクラスがあります。 Migration\ResourceModel\Source および Migration\ResourceModel\Destination がメイン クラスです。 すべての移行手順でデータの操作に使用されます。 このデータは、Migration\ResourceModel\Document、Migration\ResourceModel\Record、Migration\ResourceModel\Structure などのクラスに含まれています。

次に、これらのクラスのクラス図を示します。

![移行ツールのデータ構造](../../assets/data-migration/MmigrationToolDataStructure.png)

## ログ

マイグレーションプロセスの出力を実装し、可能なすべてのレベルを制御するために、Magentoで使用される PSR ロガーが適用されます。 `\Migration\Logger\Logger` クラスは、ロギング機能を提供するために実装されました。 ロガーを使用するには、コンストラクターの依存関係の挿入を使用してロガーを挿入する必要があります。

```php
class SomeClass
{
    ...
    protected $logger;

    public function __construct(\Migration\Logger\Logger $logger)
    {
        $this->logger = $logger;
    }
    ...
}
```

その後、このクラスを使用していくつかのイベントのログを記録できます。

```php
$this->logger->info("Some information message");
$this->logger->debug("Some debug message");
$this->logger->error("Message about error operation");
$this->logger->warning("Some warning message");
```

ログ情報の書き込み先をカスタマイズできる場合があります。 これを行うには、logger の pushHandler （） メソッドを使用して logger にハンドラーを追加します。 各ハンドラーはを実装する必要があります。 `\Monolog\Handler\HandlerInterface` インターフェイス。 現時点では、次の 2 つのハンドラーがあります。

* ConsoleHandler: メッセージをコンソールに書き込む

* FileHandler:「log_file」設定オプションで指定されたログファイルにメッセージを書き込む

また、任意の追加ハンドラーを実装することもできます。 Magentoフレームワークには一連のハンドラーがあります。 ロガーにハンドラーを追加する例は次のとおりです。

```php
// $this->consoleHandler is the object of Migration\Logger\ConsoleHandler class
// $this->logger is the object of Migration\Logger\Logger class
$this->logger->pushHandler($this->consoleHandler);
```

ロガー（現在のモード、テーブル名）の追加データを設定するには、ロガープロセッサーを使用します。 既存のプロセッサ（MessageProcessor）が 1 つあります。 これは、メッセージをログに記録するための「追加」データを追加するために作成され、ログメソッドが実行されるたびに呼び出されます。 MessageProcessor が、「mode」、「stage」、「step」、「table」の空の値を含む$extra var を保護しました。 追加のデータは、ログメソッドの 2 番目のパラメーター（コンテキスト）としてプロセッサーに渡すことができます。 現在、追加のデータセットは、AbstractStep->runStage （現在のモード、ステージ、ステップをプロセッサーに渡す）メソッドおよび logger->debug メソッド（移行テーブル名を渡す）を使用するデータクラスのプロセッサーに渡されます。 ロガーにプロセッサーを追加する例：

```php
// $this->processoris the object of Migration\Logger\messageProcessor class
// $this->logger is the object of Migration\Logger\Logger class
$this->logger->pushProcessor([$this->processor, 'setExtra']);
// As a second array value you need to pass method that should be executed when processor called
```

冗長レベルを設定する可能性があります。 今のところ、次の 3 つのレベルがあります。

* `ERROR` （エラーのみをログに書き込みます）
* `INFO` （重要な情報のみがログに書き込まれます。デフォルト値）
* `DEBUG` （すべてが書かれています）

を呼び出すことで、各ハンドラーの詳細ログレベルを個別に設定できます。 `setLevel()` メソッド。 コマンドラインパラメーターを使用して詳細レベルを設定する場合は、アプリケーションの起動時に「verbose」オプションを変更する必要があります。

ログメッセージの書式は、モノログフォーマッターで設定できます。 フォーマッター機能を動作させるには、 `setFormatter()` メソッド。 現在、フォーマッタークラスが 1 つあります（`MessageFormatter`を使用して、メッセージ処理中に特定の形式（冗長レベルに依存）を設定する `format()` メソッドはハンドラーから実行されます）。

ロガーの操作（ハンドラーとプロセッサーの追加）と詳細モードでの処理は、で実行されます。 `process()` メソッド `Migration\Logger\Manager` クラス。 メソッドは、アプリケーションの起動時に呼び出されます。

## 自動テスト

には 3 種類のテストがあります。 [!DNL Data Migration Tool]:

* 静的
* 単位
* 統合

これらはツールのに配置されています `tests/` ディレクトリ。テストのタイプと同じです（単体テストは `tests/unit` ディレクトリ）に保存します。 テストを開始するには、phpunit がインストールされている必要があります。 現在のディレクトリをテストディレクトリに変更し、phpunit を起動します。 例：

```bash
[10:32 AM]-[vagrant@debian-70rc1-x64-vbox4210]-[/var/www/magento2/vendor/magento/data-migration-tool]-[git master]
$ cd tests/unit
```

```bash
[10:33 AM]-[vagrant@debian-70rc1-x64-vbox4210]-[/var/www/magento2/vendor/magento/data-migration-tool/tests/unit]-[git master]
$ phpunit
PHPUnit 8.1.0 by Sebastian Bergmann.
....
```
