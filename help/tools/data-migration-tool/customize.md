---
title: のカスタマイズ [!DNL Data Migration Tool]
description: をカスタマイズする方法を説明します [!DNL Data Migration Tool] Magento1 とMagento2 の間で拡張機能によって作成されたデータを転送する。
exl-id: a5c1575f-9d77-416e-91fe-a82905ef2e1c
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%

---

# の設定 [!DNL Data Migration Tool]

によって作成されるデータ形式と構造 [拡張機能](https://marketplace.magento.com/extensions.html) または、Magento 1 とMagento 2 でカスタムコードが異なります。 内での拡張ポイントの使用 [!DNL Data Migration Tool] このデータを移行します。 データの形式と構造が同じ場合、ユーザーの操作なしでツールを使用して自動的にデータを移行できます。

移行中、 [マップ ステップ](technical-specification.md#map-step) 拡張機能で作成されたテーブルを含む、すべてのMagento1 およびMagento2 のテーブルをスキャンして比較します。 テーブルが同じ場合、ツールは自動的にデータを移行します。 テーブルが異なる場合、ツールは終了し、ユーザーに通知します。

>[!NOTE]
>
>を読み取る [技術仕様](technical-specification.md) を拡張する前に [!DNL Data Migration Tool]. また、を確認します [移行ガイド](../overview.md) を参照してください。


## データ形式と構造のマイナーな変更

ほとんどの場合、 [マップ ステップ](technical-specification.md#map-step) で次のメソッドを使用すると、マイナーなデータ形式および構造の変更を十分に解決できます `map.xml` ファイル：

- マッピングルールを使用したテーブル名またはフィールド名の変更
- 既存のハンドラーまたはカスタムハンドラーを使用してデータ形式を変換

マッピングルールとハンドラーの両方を使用する例を以下に示します。 この例では、Magento 2 用に改善された「GreatBlog」という架空のMagento 1 拡張機能を使用します。

```xml
<source>
    <document_rules>
        <ignore>
            <document>great_blog_index</document>
        </ignore>
        <rename>
            <document>great_blog_publication</document>
            <to>great_blog_post</to>
        </rename>
    </document_rules>
    <field_rules>
        <move>
            <field>great_blog_publication.summary</field>
            <to>great_blog_post.title</to>
        </move>
        <ignore>
            <field>great_blog_publication.priority</field>
        </ignore>
        <transform>
            <field>great_blog_publication.body</field>
            <handler class="\Migration\Handler\GreatBlog\NewFormat">
                <param name="switch" value="yes" />
            </handler>
        </transform>
    </field_rules>
</source>
<destination>
    <document_rules>
        <ignore>
            <document>great_blog_rating</document>
        </ignore>
    </document_rules>
    <field_rules>
        <ignore>
            <field>great_blog_post.rating</field>
        </ignore>
    </field_rules>
</destination>
```

- から不要なデータを移行しない `great_blog_index` インデックステーブル。
- テーブル `great_blog_publication` の名前はに変更されました `great_blog_post` Magento 2 では、データは新しいテーブルに移行されます。
   - この `summary` フィールド名をに変更しました `title`そのため、データは新しいフィールドに移行されます。
   - この `priority` フィールドが削除され、Magento 2 には存在しません。
   - のデータ `body` フィールドの形式が変更されました。カスタムハンドラーで処理する必要があります。 `\Migration\Handler\GreatBlog\NewFormat`.
- Magento 2 の「GreatBlog」拡張機能用に新しい評価機能が開発されました。
   - 新品 `great_blog_rating` テーブルが作成されました。
   - 新品 `great_blog_post.rating` フィールドが作成されました。

### 他の手順でのマッピングの拡張

その他の手順は、次のようなマッピングをサポートします [EAV ステップ](technical-specification.md#eav-step) および顧客属性ステップ 次の手順では、Magentoテーブルの定義済みリストを移行します。 例えば、「GreatBlog」拡張機能のに追加のフィールドがあるとします `eav_attribute` Magento2 で変更されたテーブルと名前。 テーブルはによって処理されるので、 [EAV ステップ](technical-specification.md#eav-step)、マッピングルールはに対して記述する必要があります `map-eav.xml` ファイル。 この `map.xml` および `map-eav.xml` ファイルは同じ値を使用 `map.xsd` スキーマなので、マッピングルールは同じままです。

## データ形式および構造の大幅な変更

マップ ステップに加えて、には他のステップがあります。 `config.xml` 次のような主要な形式および構造の変更によりデータを移行するファイル。

- [Url 書き換え手順](technical-specification.md#url-rewrite-step)
- OrderGrids ステップ
- [EAV ステップ](technical-specification.md#eav-step)

と異なります。 [マップ ステップ](technical-specification.md#map-step)の場合、これらの手順では、すべてのテーブルではなく、事前に定義されたテーブルのリストをスキャンします。

データの形式および構造を大幅に変更する場合は、カスタムステップを作成します。

### カスタムステップの作成

同じ「GreatBlog」の例を使用して、Magento1 に 1 つのテーブルがあるものの、Magento2 に 2 つのテーブルを持つように再設計したとします。

Magento 1 には、 `greatblog_post` テーブル：

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
| tags      | TEXT     |
```

Magento 2 のタグ用の新しいテーブル `greatblog_post_tags` が導入されました：

```text
| Field      | Type     |
|------------|----------|
| post_id    | INT      |
| tag        | VARCHAR  |
| sort_order | SMALLINT |
```

MAGENTO 2 `greatblog_post` テーブルは次のようになります。

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
```

古いテーブル構造から新しいテーブル構造にすべてのデータを移行するには、でカスタムステップを作成できます。 `config.xml` ファイル。 例：

```xml
<steps mode="data">
    ...
    <step title="GreatBlog Step">
        <integrity>Vendor\Migration\Step\GreatBlog\Integrity</integrity>
        <data>Vendor\Migration\Step\GreatBlog\Data</data>
        <volume>Vendor\Migration\Step\GreatBlog\Volume</volume>
    </step>
</steps>
<steps mode="delta">
    ...
    <step title="GreatBlog Step">
        <delta>Vendor\Migration\Step\GreatBlog\Delta</delta>
        <volume>Vendor\Migration\Step\GreatBlog\Volume</volume>
    </step>
</steps>
```

ツールは、 `config.xml` ファイル。上から下へ。 この例では、 `GreatBlog Step` 前回の実行。

手順には、次の 4 種類のクラスが含まれます。

- 整合性チェック
- データ配信
- ボリュームチェック
- Delta 配信

>[!NOTE]
>
>こちらを参照してください [設定](technical-specification.md#configuration), [ステップ内部](technical-specification.md#step-internals), [ステージ](technical-specification.md#step-stages)、および [実行モード](technical-specification.md#running-modes) を参照してください。


複雑な SQL クエリは、これらのクラス内で組み合わせて、データを取得および移行できます。 また、これらのテーブルはで「無視」される必要があります。 [マップ ステップ](technical-specification.md#map-step) これは、既存のすべてのテーブルをスキャンし、データがに存在しない限りデータの移行を試みるからです `<ignore>` のタグ `map.xml` ファイル。

整合性チェックの場合は、に追加のマップファイルを定義します。 `config.xml` ファイルを作成して、テーブル構造が期待どおりであることを確認します。

```xml
<config xmlns:xs="http://www.w3.org/2001/XMLSchema-instance"
        xs:noNamespaceSchemaLocation="urn:magento:module:Magento_DataMigrationTool:etc/config.xsd">
    ...
    <options>
        ...
        <greatblog_map_file>app/code/Vendor/Migration/etc/opensource-to-opensource/map-greatblog.xml</greatblog_map_file>
        ...
    </options>
</config>
```

マップファイル `map-greatblog.xml`:

```xml
<map xmlns:xs="http://www.w3.org/2001/XMLSchema-instance"
     xs:noNamespaceSchemaLocation="urn:magento:module:Magento_DataMigrationTool:etc/map.xsd">
    <source>
        <field_rules>
            <ignore>
                <field>greatblog_post.tags</field>
            </ignore>
        </field_rules>
    </source>
    <destination>
        <document_rules>
            <ignore>
                <document>greatblog_post_tags</document>
            </ignore>
        </document_rules>
    </destination>
</map>
```

整合性チェック クラス `Vendor\Migration\Step\GreatBlog\Integrity` を拡張 `Migration\App\Step\AbstractIntegrity` およびは、を含みます `perform` テーブル構造を検証する方法：

```php
class Integrity extends \Migration\App\Step\AbstractIntegrity
{
    ...
    /**
     * Integrity constructor.
     * @param ProgressBar\LogLevelProcessor $progress
     * @param Logger $logger
     * @param Config $config
     * @param ResourceModel\Source $source
     * @param ResourceModel\Destination $destination
     * @param MapFactory $mapFactory
     * @param string $mapConfigOption
     */
    public function __construct(
        ProgressBar\LogLevelProcessor $progress,
        Logger $logger,
        Config $config,
        ResourceModel\Source $source,
        ResourceModel\Destination $destination,
        MapFactory $mapFactory,
        $mapConfigOption = 'greatblog_map_file'
    ) {
        parent::__construct($progress, $logger, $config, $source, $destination, $mapFactory, $mapConfigOption);
    }

    /**
     * @inheritDoc
     */
    public function perform()
    {
        $this->progress->start($this->getIterationsCount());
        $this->check(['greatblog_post'], MapInterface::TYPE_SOURCE);
        $this->check(['greatblog_post', 'greatblog_post_tags'], MapInterface::TYPE_DEST);
        $this->progress->finish();
        return $this->checkForErrors();
    }
    ...
}
```

次に、Magento2 データベースにデータを処理および保存するためのクラスを作成する必要があります `Vendor\Migration\Step\GreatBlog\Data`:

```php
class Data implements \Migration\App\Step\StageInterface
{
    ...
    /**
     * Data constructor.
     *
     * @param ProgressBar\LogLevelProcessor $progress
     * @param ResourceModel\Source $source
     * @param ResourceModel\Destination $destination
     * @param ResourceModel\RecordFactory $recordFactory
     * @param RecordTransformerFactory $recordTransformerFactory
     * @param MapFactory $mapFactory
     */
    public function __construct(
        ProgressBar\LogLevelProcessor $progress,
        ResourceModel\Source $source,
        ResourceModel\Destination $destination,
        ResourceModel\RecordFactory $recordFactory,
        RecordTransformerFactory $recordTransformerFactory,
        MapFactory $mapFactory
    ) {
        $this->progress = $progress;
        $this->destination = $destination;
        $this->recordFactory = $recordFactory;
        $this->source = $source;
        $this->recordTransformerFactory = $recordTransformerFactory;
        $this->map = $mapFactory->create('greatblog_map_file');
    }

    /**
     * @inheritDoc
     */
    public function perform()
    {
        $sourceDocName = 'greatblog_post';
        $sourceDocument = $this->source->getDocument($sourceDocName);
        $destinationDocName = 'greatblog_post';
        $destinationDocument = $this->destination->getDocument($destinationDocName);
        /** @var \Migration\RecordTransformer $recordTransformer */
        $recordTransformer = $this->recordTransformerFactory->create(
            [
                'sourceDocument' => $sourceDocument,
                'destDocument'   => $destinationDocument,
                'mapReader'      => $this->map
            ]
        );
        $recordTransformer->init();

        $this->progress->start($this->source->getRecordsCount($sourceDocName));
        $pageNumber = 0;
        while (!empty($items = $this->source->getRecords($sourceDocName, $pageNumber))) {
            $pageNumber++;
            $recordsToSave = $destinationDocument->getRecords();
            foreach ($items as $item) {
                $sourceRecord = $this->recordFactory->create(
                    ['document' => $sourceDocument, 'data' => $item]
                );
                $destinationRecord = $this->recordFactory->create(['document' => $destinationDocument]);
                $recordTransformer->transform($sourceRecord, $destinationRecord);
                $recordsToSave->addRecord($destinationRecord);
            }
            $this->destination->saveRecords($destinationDocName, $recordsToSave);

            $tags = $this->getTags($items);
            $this->destination->saveRecords('greatblog_post_tags', $tags);
            $this->progress->advance();
        }

        $this->progress->finish();
        return true;
    }
    ...
}
```

Volume クラス内 `Vendor\Migration\Step\GreatBlog\Volume`データが完全に移行されたかどうかを確認します。

```php
class Volume extends \Migration\App\Step\AbstractVolume
{
    ...
    /**
     * @inheritdoc
     */
    public function perform()
    {
        $documentName = 'greatblog_post';
        $sourceCount = $this->source->getRecordsCount($documentName);
        $destinationCount = $this->destination->getRecordsCount($documentName);
        if ($sourceCount != $destinationCount) {
            $this->errors[] = sprintf(
                'Mismatch of entities in the document: %s Source: %s Destination: %s',
                $documentName,
                $sourceCount,
                $destinationCount
            );
        }

        return $this->checkForErrors(Logger::ERROR);
    }
    ...
}
```

差分移行機能を追加するには、新しいグループをに追加します `deltalog.xml` ファイル。 対象： `group`で、変更をチェックする必要があるテーブルの名前を指定します。

```xml
<groups>
    ...
    <group name="delta_greatblog">
        <document key="post_id">greatblog_post</document>
    </group>
</groups>
```

次に、を作成します `Delta` クラス `Vendor\Migration\Step\GreatBlog\Delta` それが広がる `Migration\App\Step\AbstractDelta`:

```php
class Delta extends \Migration\App\Step\AbstractDelta
{
    /**
     * @var string
     */
    protected $mapConfigOption = 'greatblog_map_file';

    /**
     * @var string
     */
    protected $groupName = 'delta_greatblog';

    /**
     * @inheritDoc
     */
    public function perform()
    {
        $sourceDocumentName = 'greatblog_post';
        $idKeys = ['post_id'];
        $page = 0;
        while (!empty($items = $this->source->getChangedRecords($sourceDocumentName, $idKeys, $page++))) {
            $this->destination->deleteRecords(
                'greatblog_post_tags',
                $idKeys,
                $items
            );

            $tags = $this->getTags($items);
            $this->destination->saveRecords('greatblog_post_tags', $tags);
        }

        //parent class takes care of greatblog_post records automatically
        return parent::perform();
    }
}
```

例に示したカスタムステップの実装が完了すると、システムはシングルMagento1 テーブルからデータを取得し、次を使用して処理します `Vendor\Migration\Step\GreatBlog\Data` データをクラス化し、2 つのMagento 2 テーブルに格納します。 新しいレコードと変更されたレコードは、 `Vendor\Migration\Step\GreatBlog\Delta` クラス。

## 禁止される拡張方法

以降 [!DNL Data Migration Tool] また、Magento 2 は常に進化しており、既存の手順やハンドラーは変更される可能性があります。 のようなステップの動作を上書きしないことを強くお勧めします。 [マップ ステップ](technical-specification.md#map-step), [URL 書き換え手順](technical-specification.md#url-rewrite-step)、およびハンドラーのクラスを拡張して追加できます。

一部の手順は、マッピングをサポートしておらず、変更するにはコードを変更する必要があります。 移行終了時にデータを変更する追加の手順を記述するか、 [GitHub の問題](https://github.com/magento/data-migration-tool/issues) 既存のステップで新しい拡張ポイントを要求します。
