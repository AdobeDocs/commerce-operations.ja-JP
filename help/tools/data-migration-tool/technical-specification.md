---
title: '"[!DNL Data Migration Tool] 技術仕様書'
description: 「 [!DNL Data Migration Tool] Magento1 とMagento2 の間でデータを転送する際に拡張する方法」
source-git-commit: c56cc6d97f69770aa718333c02514ab3cfce774c
workflow-type: tm+mt
source-wordcount: '2085'
ht-degree: 0%

---


# [!DNL Data Migration Tool] 技術仕様

ここでは、 [!DNL Data Migration Tool] 実装の詳細と、その機能の拡張方法について説明します。

## リポジトリ

次の手順で [!DNL Data Migration Tool] ソースコード（GitHub を参照） [リポジトリ](https://github.com/magento/data-migration-tool).

## 必要システム構成

この [システム要件](../../installation/system-requirements.md) の [!DNL Data Migration Tool] は、Magento2 と同じです。

## 内部構造

### ディレクトリ構造

次の図は、 [!DNL Data Migration Tool]:

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
│       ├── ResourceModel                   --- contains [adapter](https://glossary.magento.com/adapter) for connection to data storage and classes to work with structured data
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
│       ├── [Exception](https://glossary.magento.com/exception).php
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

## 入口

移行プロセスを実行するスクリプトは、次の場所にあります。 `magento-root/bin/magento`.

## 設定

設定のスキーマ `config.xsd` ファイルは `etc/` ディレクトリ。 デフォルトの設定ファイル (`config.xml.dist`) は、Magento1.x の各バージョン用に作成されます。これは、の下の別のディレクトリにあります。 `etc/`.

デフォルトの設定ファイルは、カスタムの設定ファイルに置き換えることができます ( [コマンド構文](migrate-data/overview.md#command-syntax)) をクリックします。

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

* 手順 — 移行中に処理されるすべての手順を説明します。

* source — データソースの設定。 使用可能なソースタイプ：データベース

* destination — データの宛先の設定。 使用可能な宛先のタイプ：データベース

* options — パラメーターのリスト。 必須 (map_file、settings_map_file、bulk_size) とオプション (custom_option、resource_adapter_class_name、prefix_source、prefix_dest、log_file) の両方のパラメータが含まれます

データベーステーブルにプレフィックスが付いたMagentoがインストールされた場合の「プレフィックスを変更」オプション。 Magento1 およびMagento2 データベースに設定できます。 それに応じて、「source_prefix」と「dest_prefix」の設定オプションを使用します。

設定データには、 `\Migration\Config` クラス。

## 使用可能な操作の手順

| 文書 | フィールド |
|---|---|
| `step` | ステップノード内の第 2 レベルのノード。 関連するステップの説明は、 `title` 属性。 |
| `integrity` | 整合性チェックを行う PHP クラスを指定します。 テーブルのフィールド名、タイプ、その他の情報を比較して、Magento1 と 2 のデータ構造の互換性を検証します。 |
| `data` | データチェックを行う PHP クラスを指定します。 データをテーブルごとにMagento1 からMagento2 に転送します。 |
| `volume` | ボリュームチェックを行う PHP クラスを指定します。 テーブル間のレコード数を比較し、転送が成功したことを確認します。 |
| `delta` | デルタチェックを行う PHP クラスを指定します。 完全なデータ移行後に、Magento1 からMagento2 にデルタを転送します。 |

## ソースデータベース情報の属性

| 文書 | フィールド | 必須？ |
|---|---|---|
| `name` | Magento1 サーバのデータベース名。 | はい |
| `host` | Magento1 サーバのホスト IP アドレス。 | はい |
| `port` | Magento1 サーバーのポート番号。 | いいえ |
| `user` | Magento1 データベースサーバのユーザ名。 | はい |
| `password` | Magento1 データベースサーバーのパスワード。 | はい |
| `ssl_ca` | SSL 認証局ファイルへのパス。 | いいえ |
| `ssl_cert` | SSL 証明書ファイルへのパス。 | いいえ |
| `ssl_key` | SSL キーファイルへのパス。 | いいえ |

## 宛先データベース情報の属性

| 文書 | フィールド | 必須？ |
|---|---|---|
| `name` | Magento2 サーバーのデータベース名。 | はい |
| `host` | Magento2 サーバのホスト IP アドレス。 | はい |
| `port` | Magento2 サーバーのポート番号。 | いいえ |
| `user` | Magento2 データベース・サーバのユーザ名。 | はい |
| `password` | Magento2 データベースサーバーのパスワード。 | はい |
| `ssl_ca` | SSL 認証局ファイルへのパス。 | いいえ |
| `ssl_cert` | SSL 証明書ファイルへのパス。 | いいえ |
| `ssl_key` | SSL キーファイルへのパス。 | いいえ |

## TLS プロトコルを使用した接続

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

## ステップの内部

移行プロセスは、次の手順で構成されます。

ステップは、分離されたデータの移行に必要な機能を提供する単位です。 ステップは、1 つ以上のステージ（整合性チェック、データ、ボリュームチェック、デルタ）で構成できます。

デフォルトでは、次の手順があります ([マップ](#map-step), [房室](#eav), [URL の書き換え](#url-rewrite-step)など )。 オプションで、独自の手順も追加できます。

ステップ関連のクラスは、src/Migration/Step ディレクトリにあります。

Step クラスを実行するには、config.xml ファイルでクラスを定義する必要があります。

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

すべてのステージクラスが StageInterface を実装する必要があります。

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

データステージでロールバックがサポートされている場合は、 `RollbackInterface` インターフェイス。

実行中のステップのビジュアライゼーションは、Symfony の ProgressBar コンポーネントによって提供されます ( [プログレスバー](https://symfony.com/doc/current/components/console/helpers/progressbar.html)) をクリックします。 このコンポーネントには、LogLevelProcessor としてアクセスします。

主な使用方法は次のとおりです。

```xml
$this->progress->start();
$this->progress->advance();
$this->progress->finish();
```

## ステップステージ

### 整合性チェック

各手順では、データソースの構造 ( デフォルトではMagento1) とデータ宛先の構造 (Magento2) が互換性があることを確認する必要があります。 そうでない場合 — 互換性のないエンティティが含まれるエラーが表示されます。 フィールドのデータ型が異なる場合 ( 同じフィールドのMagento1 では 10 進数データ型、Magento2 では整数 )、警告メッセージが表示されます（Map ファイルで扱われた場合を除く）。

### データ転送

整合性チェックに合格した場合、データ転送を実行しています。 エラーが発生した場合は、ロールバック実行を実行して、Magento2 の以前の状態に戻します。 step クラスが `RollbackInterface` インタフェースでは、エラーが発生した場合に rollback メソッドが実行されます。

### ボリュームチェック

データが移行された後、ボリューム・チェックでは、すべてのデータが正しく転送されたことを確認する追加のチェックが行われます。

### 差分配信

差分機能は、メイン移行後に追加された残りのデータを配信します。

## 実行モード

このツールは、次の 3 つの異なるモードで特定の順序で実行する必要があります。

1. 設定 — システム設定の移行
1. データ — データの主な移行
1. delta — メイン移行後に追加された残りのデータの移行

各モードには、実行する手順の独自のリストがあります。 config.xml を参照

### 移行モードの設定

このツールの設定移行モードは、次のエンティティを転送するために使用されます。

1. Web サイト、ストア、ストア表示。
1. ストアの設定（主に M2 でのストア —> 構成、または M1 でのシステム —> 構成）

すべてのストア設定では、データベースの core_config_data テーブルにデータが保持されます。 settings.xml ファイルには、移行プロセス中に適用されるこのテーブルの規則が含まれます。 このファイルでは、無視する、名前を変更する、または値を変更する必要がある設定について説明します。 settings.xml ファイルの構造は次のとおりです。

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

ノードの下 `<key>` 「パス」列を使用するルールが `core_config_data` 表。 `<ignore>` ルールにより、一部の設定がツールによって転送されなくなります。 このノードではワイルドカードを使用できます。 他の設定は、 `<ignore>` ノードが移行されます。 Magento2 で設定へのパスが変更された場合は、 `//key/rename` ノード ( 古いパスが `//key/rename/path` ノードと新しいパスが `//key/rename/to` ノード。

ノードの下 `<value>`の場合、 `core_config_data` 表。 これらのルールは、ハンドラ（を実装するクラス）によって設定の値を変換することを目的としています `Migration\Handler\HandlerInterface`) を参照し、Magento2 に合わせて調整します。

### データ移行モード

このモードでは、ほとんどのデータが移行されます。 データ移行の前に、各手順で整合性チェックステージが実行されます。 整合性チェックが合格すると、 [!DNL Data Migration Tool] deltalog テーブル（プレフィックス付き）をインストールします `m2_cl_*`) および対応するトリガーをMagento1 データベースに追加し、データ移行ステージを実行します。 移行がエラーなしで完了すると、ボリュームチェックはデータの整合性をチェックします。 ライブストアを移行すると、警告メッセージが表示される場合があります。 デルタ移行では、この増分データが処理されます。 最も役立つ移行手順は、マップ、URL の書き換え、EAV です。

#### マッピングステップ

マップステップは、ほとんどのデータをMagento1 からMagento2 に転送します。 この手順は、map.xml ファイル ( `etc/` ディレクトリ ) に書き込まれます。 ファイルは、ソース (Magento1) と宛先 (Magento2) のデータ構造の違いを記述しています。 Magento1 に、一部の [拡張](https://glossary.magento.com/extension) これはMagento2 に存在しないので、ここに配置して、マップステップで無視することができます。 それ以外の場合は、エラーメッセージが表示されます。

マップファイルの形式は次のとおりです。

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

* *ソース*  — ソースデータベースのルールが含まれます

* *宛先*  — 宛先データベースのルールを含みます

オプション：

* *無視*  — このオプションでマークされたドキュメント、フィールドまたはデータ型は無視されます

* *名前変更*  — 異なる名前を持つドキュメント間の名前の関係を表します。 ソースドキュメントと宛先ドキュメントの名前が異なる場合は、名前の変更オプションを使用して、ソースドキュメント名を宛先テーブル名と同じ名前に設定できます

* *移動*  — 指定したフィールドを元のドキュメントから移動先のドキュメントに移動するルールを設定します。 注意：コピー先のドキュメント名は、コピー元のドキュメント名と同じにする必要があります。 移動元と移動先のドキュメント名が異なる場合は、移動したフィールドを含むドキュメントの名前変更オプションを使用する必要があります

* *変換*  — は、ハンドラーで説明されている動作に従ってユーザーがフィールドを移行できるオプションです

* *ハンドラー*  — フィールドの変換動作を表します。 ハンドラを呼び出すには、 `<handler>` タグを使用します。 以下を使用： `<param>` タグにパラメーター名と値のデータを追加し、ハンドラーに渡します。

**ソース** 使用可能な操作：

| 文書 | フィールド |
|--- |--- |
| 名前を変更しない | 移動変換を無視 |

**宛先** 使用可能な操作：

| 文書 | フィールド |
|--- |--- |
| 無視 | 変換を無視 |

#### ワイルドカード

類似の部分を持つドキュメントを無視するには (`document_name_1`, `document_name_2`) を使用する場合は、ワイルドカード機能を使用できます。 Put `*` 繰り返し部分 (`document_name_*`) を含め、このマスクに一致するソースドキュメントまたは宛先ドキュメントがすべてこのマスクに含まれます。

#### URL の書き換え手順

この手順は複雑です。Magento1 で開発されたアルゴリズムは、Magento2 と互換性がないものが多数あるからです。 バージョン 1 の異なるMagentoでは、異なるアルゴリズムを使用できます。 したがって、Step/UrlRewrite フォルダーの下には、特定のバージョンのMagentoとMigration\Step\UrlRewrite\Version191to2000 is one of them用に開発されたクラスがあります。 URL の書き換えデータをMagento1.9.1 からMagento2 に転送できます。

#### 房室ステップ

この手順では、すべての属性（製品、顧客、RMA）をMagento1 からMagento2 に転送します。 map-eav.xml ファイルを使用します。このファイルには、データを処理する特定のケースに対して、map.xml ファイルのルールと類似したルールが含まれています。

手順で処理されるテーブルの一部：

* `eav_attribute`
* `eav_attribute_group`
* `eav_attribute_set`
* `eav_entity_attribute`
* `catalog_eav_attribute`
* `customer_eav_attribute`
* `eav_entity_type`

### 差分移行モード

メイン移行後に、追加のデータがMagento1 データベースに追加されている可能性があります（例えば、ストアフロントのお客様が追加したデータ）。 このデータを追跡するために、移行プロセスの開始時にテーブルのデータベーストリガーを設定します。 詳しくは、 [サードパーティの拡張機能で作成されたデータの移行](migrate-data/delta.md#migrate-data-created-by-third-party-extensions).

## データソース

Magento1 とMagento2 のデータソースにアクセスし、そのデータを使用して操作する（選択、更新、挿入、削除）には、Resource フォルダに多くのクラスがあります。 Migration\ResourceModel\Source と Migration\ResourceModel\Destination はメインクラスです。 すべての移行手順で、データを使用して操作します。 このデータは、Migration\ResourceModel\Document、Migration\ResourceModel\Record、Migration\ResourceModel\Structure などのクラスに含まれています。

次に、これらのクラスのクラス図を示します。

![移行ツールのデータ構造](../../assets/data-migration/MmigrationToolDataStructure.png)

## ログ

移行プロセスの出力を実装し、可能なすべてのレベルを制御するために、Magentoで使用される PSR ロガーが適用されます。 `\Migration\Logger\Logger` ログ機能を提供するために、クラスが実装されました。 ロガーを使用するには、コンストラクターを介して挿入する必要があります [依存注入](https://glossary.magento.com/dependency-injection).

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

その後、このクラスを使用して一部のイベントのログを記録できます。

```php
$this->logger->info("Some information message");
$this->logger->debug("Some debug message");
$this->logger->error("Message about error operation");
$this->logger->warning("Some warning message");
```

ログ情報の書き込み先をカスタマイズする可能性があります。 ロガーの pushHandler() メソッドを使用して、ロガーにハンドラーを追加することで、これを実行できます。 各ハンドラーは、 `\Monolog\Handler\HandlerInterface` インターフェイス。 現時点では、2 つのハンドラーがあります。

* ConsoleHandler:コンソールにメッセージを書き込みます

* FileHandler:は&quot;log_file&quot;設定オプションで設定されたログファイルにメッセージを書き込みます

また、追加のハンドラーを実装することもできます。 ハンドラーフレームワークには、一連のハンドラーがMagentoされています。 ロガーにハンドラーを追加する例：

```php
// $this->consoleHandler is the object of Migration\Logger\ConsoleHandler class
// $this->logger is the object of Migration\Logger\Logger class
$this->logger->pushHandler($this->consoleHandler);
```

ロガーの追加データ（現在のモード、テーブル名）を設定するには、ロガープロセッサを使用できます。 既存のプロセッサ (MessageProcessor) が 1 つあります。 メッセージのログに「追加」のデータを追加するために作成され、ログメソッドが実行されるたびに呼び出されます。 MessageProcessor は$extra var を保護しています。この変数には、&#39;mode&#39;、&#39;stage&#39;、&#39;step&#39;、&#39;table&#39;の空の値が含まれています。 追加のデータは、ログメソッドの第 2 のパラメータ（コンテキスト）としてプロセッサに渡すことができます。 現在、AbstractStep->runStage （現在のモード、ステージ、およびステップをプロセッサに渡す）メソッドと、logger->debug メソッド（移行するテーブル名を渡す）を使用したデータクラスに追加されています。 ロガーにプロセッサーを追加する例：

```php
// $this->processoris the object of Migration\Logger\messageProcessor class
// $this->logger is the object of Migration\Logger\Logger class
$this->logger->pushProcessor([$this->processor, 'setExtra']);
// As a second array value you need to pass method that should be executed when processor called
```

詳細のレベルを設定する可能性があります。 現時点では、次の 3 つのレベルがあります。

* `ERROR` （エラーのみをログに書き込みます）
* `INFO` （重要な情報のみがログに書き込まれます。デフォルト値）
* `DEBUG` （すべてが書かれています）

詳細ログレベルは、 `setLevel()` メソッド。 コマンドラインパラメーターを使用して詳細レベルを設定する場合は、アプリケーションの起動時に「verbose」オプションを変更する必要があります。

monolog 形式を使用して、ログメッセージを書式設定できます。 フォーマッタ機能を動作させるには、 `setFormatter()` メソッド。 現在、1 つの formatter クラス (`MessageFormatter`) を使用して、( `format()` メソッドはハンドラから実行されます )。

ロガーの操作（ハンドラーとプロセッサーの追加）および詳細モードでの処理は、 `process()` メソッド `Migration\Logger\Manager` クラス。 アプリケーションの起動時にメソッドが呼び出されます。

## 自動テスト

には 3 つのタイプのテストがあります [!DNL Data Migration Tool]:

* 静的
* 単位
* 統合

これらは、ツールの `tests/` ディレクトリ（テストのタイプと同じ）( 単体テストは `tests/unit` ディレクトリ ) に書き込まれます。 テストを開始するには、phpunit がインストールされている必要があります。 現在のディレクトリをテストディレクトリに変更し、phpunit を起動します。 例：

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
