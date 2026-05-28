---
title: ' [!DNL Data Migration Tool]をカスタマイズ'
description: Magento 1とMagento 2の間で拡張機能によって作成されたデータを転送するように [!DNL Data Migration Tool] をカスタマイズする方法について説明します。
exl-id: a5c1575f-9d77-416e-91fe-a82905ef2e1c
topic: Commerce, Migration
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '843'
ht-degree: 0%

---

# [!DNL Data Migration Tool]の設定

[extensions](https://commercemarketplace.adobe.com//extensions.html)またはカスタムコードで作成されたデータ形式と構造が、Magento 1とMagento 2で異なる場合があります。 このデータを移行するには、[!DNL Data Migration Tool]内の拡張ポイントを使用してください。 データの形式と構造が同じ場合は、ユーザーの介入なしでデータを自動的に移行できます。

移行中、[ マップステップ ](technical-specification.md#map-step)は、拡張機能で作成されたテーブルを含む、すべてのMagento 1とMagento 2のテーブルをスキャンして比較します。 テーブルが同じ場合、ツールはデータを自動的に移行します。 表が異なる場合、ツールは終了し、ユーザーに通知します。

>[!NOTE]
>
>[!DNL Data Migration Tool]の拡張を試みる前に、[技術仕様](technical-specification.md)をお読みください。 また、移行ツールの使用に関する一般的な情報については、[移行ガイド ](../overview.md)を参照してください。


## データ形式と構造の軽微な変更

ほとんどの場合、[ マップステップ ](technical-specification.md#map-step)は、`map.xml` ファイルの次のメソッドを使用して、データ形式と構造の変更を十分に解決します。

- マッピングルールを使用したテーブル名またはフィールド名の変更
- 既存のハンドラーまたはカスタムハンドラーを使用してデータ形式を変換する

次に、マッピングルールとハンドラーの両方を使用する例を示します。 この例では、Magento 2用に改善された「GreatBlog」と呼ばれるMagento 1拡張機能を使用しています。

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

- `great_blog_index` インデックステーブルから不要なデータを移行しないでください。
- Magento 2でテーブル `great_blog_publication`の名前が`great_blog_post`に変更されたため、データは新しいテーブルに移行されます。
   - `summary` フィールドの名前が`title`に変更されたため、データは新しいフィールドに移行されます。
   - `priority` フィールドは削除され、Magento 2には存在しなくなります。
   - `body` フィールドのデータの形式が変更されました。カスタムハンドラーで処理する必要があります：`\Migration\Handler\GreatBlog\NewFormat`。
- Magento 2の「GreatBlog」拡張機能のために、新しい評価機能が開発されました。
   - 新しい`great_blog_rating` テーブルが作成されました。
   - 新しい`great_blog_post.rating` フィールドが作成されました。

### 他の手順でマッピングを拡張

その他の手順では、[EAV ステップ ](technical-specification.md#eav-step)や顧客属性ステップなどのマッピングがサポートされています。 次の手順では、定義済みのMagento テーブルのリストを移行します。 例えば、「GreatBlog」拡張機能に`eav_attribute` テーブルに追加のフィールドがあり、名前がMagento 2で変更されているとします。 テーブルは[EAV ステップ ](technical-specification.md#eav-step)によって処理されるので、`map-eav.xml` ファイルのマッピングルールを記述する必要があります。 `map.xml` ファイルと`map-eav.xml` ファイルは同じ`map.xsd` スキーマを使用しているため、マッピングルールは同じままです。

## データ形式と構造の主な変更

マップステップに加えて、`config.xml` ファイルには、主な形式と構造の変更を含むデータを移行する他のステップがあります。

- [Url書き換えステップ](technical-specification.md#url-rewrite-step)
- OrderGrids ステップ
- [EAV ステップ](technical-specification.md#eav-step)

[ マップステップ ](technical-specification.md#map-step)とは異なり、これらのステップでは、すべてのテーブルではなく、事前に定義されたテーブルのリストをスキャンします。

データ形式や構造の変更が大きい場合は、カスタム手順を作成します。

### カスタムステップの作成

同じ「GreatBlog」の例を使用して、拡張機能がMagento 1に1つのテーブルを持つが、Magento 2に2つのテーブルを持つように再設計されたとします。

Magento 1では、1つの`greatblog_post` テーブルがありました。

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
| tags      | TEXT     |
```

Magento 2では、タグ `greatblog_post_tags`の新しいテーブルが導入されました。

```text
| Field      | Type     |
|------------|----------|
| post_id    | INT      |
| tag        | VARCHAR  |
| sort_order | SMALLINT |
```

Magento 2 `greatblog_post` テーブルは次のようになります。

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
```

古いテーブル構造からすべてのデータを新しいテーブル構造に移行するには、`config.xml` ファイルにカスタム ステップを作成します。 例：

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

ツールは、上から下まで、`config.xml` ファイル内の位置に従ってステップを実行します。 この例では、`GreatBlog Step`は最後に実行されます。

手順には、次の4種類のクラスを含めることができます。

- 整合性の確認
- データ配信
- ボリュームチェック
- 航空券の郵送

>[!NOTE]
>
>詳しくは、[設定](technical-specification.md#configuration)、[ ステップインターナル ](technical-specification.md#step-internals)、[ ステージ ](technical-specification.md#step-stages)、[実行モード ](technical-specification.md#running-modes)を参照してください。


これらのクラス内で複雑なSQL クエリを組み立てて、データを取得および移行できます。 また、既存のすべてのテーブルをスキャンし、`map.xml` ファイルの`<ignore>` タグに含まれていない限りデータを移行しようとするため、これらのテーブルは[ マップステップ ](technical-specification.md#map-step)で「無視」する必要があります。

整合性チェックの場合は、`config.xml` ファイルに追加のマップファイルを定義して、テーブルの構造が期待通りであることを確認します。

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

整合性チェック クラス `Vendor\Migration\Step\GreatBlog\Integrity`は`Migration\App\Step\AbstractIntegrity`を拡張し、テーブル構造を検証する`perform` メソッドを含んでいます：

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

次に、データを処理してMagento 2 データベース `Vendor\Migration\Step\GreatBlog\Data`に保存するためのクラスを作成する必要があります。

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

ボリューム クラス `Vendor\Migration\Step\GreatBlog\Volume`で、データが完全に移行されたかどうかを確認します。

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

差分移行機能を追加するには、新しいグループを`deltalog.xml` ファイルに追加します。 `group`で、変更を確認する必要があるテーブルの名前を指定します。

```xml
<groups>
    ...
    <group name="delta_greatblog">
        <document key="post_id">greatblog_post</document>
    </group>
</groups>
```

次に、`Migration\App\Step\AbstractDelta`を拡張する`Delta` クラス `Vendor\Migration\Step\GreatBlog\Delta`を作成します。

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

この例で提供されているカスタムステップの実装の後、システムは1つのMagento 1 テーブルからデータを取り出し、
`Vendor\Migration\Step\GreatBlog\Data` クラスを使用してデータを処理し、2つのMagento 2 テーブルに格納します。 新しいレコードと変更されたレコードは、`Vendor\Migration\Step\GreatBlog\Delta` クラスを使用して差分の移行時に配信されます。

## 禁止されている拡張方法

[!DNL Data Migration Tool]とMagento 2は常に進化しているため、既存のステップとハンドラーは変更される可能性があります。 [ マップステップ ](technical-specification.md#map-step)、[URL書き換えステップ ](technical-specification.md#url-rewrite-step)、ハンドラーなどのステップの動作を、クラスを拡張して上書きしないことを強くお勧めします。

一部の手順はマッピングをサポートしていないため、コードを変更せずに変更することはできません。 移行の最後にデータを変更する追加の手順を作成するか、[GitHub イシュー](https://github.com/magento/data-migration-tool/issues)を作成して、既存の手順に新しい拡張ポイントを求めることができます。
