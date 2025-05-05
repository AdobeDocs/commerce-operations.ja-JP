---
title: ' [!DNL Data Migration Tool] をカスタマイズします。'
description: Magento 1 とMagento 2 の間で、拡張機能で作成されたデータを転送する  [!DNL Data Migration Tool]  をカスタマイズする方法について説明します。
exl-id: a5c1575f-9d77-416e-91fe-a82905ef2e1c
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%

---

# [!DNL Data Migration Tool] の設定

[Magento](https://marketplace.magento.com/extensions.html) またはカスタムコードで作成されたデータのフォーマットと構造が、拡張機能 1 とMagento2 で異なる場合があります。 [!DNL Data Migration Tool] 内で拡張ポイントを使用して、このデータを移行します。 データの形式と構造が同じ場合、ユーザーの操作なしでツールを使用して自動的にデータを移行できます。

移行時に、[ マップステップ ](technical-specification.md#map-step) は、拡張機能によって作成されたテーブルを含む、すべてのMagento1 およびMagento2 のテーブルをスキャンして比較します。 テーブルが同じ場合、ツールは自動的にデータを移行します。 テーブルが異なる場合、ツールは終了し、ユーザーに通知します。

>[!NOTE]
>
>[!DNL Data Migration Tool] を拡張する前に、[ 技術仕様 ](technical-specification.md) をお読みください。 また、移行ツールの使用方法に関する一般的な情報については、[ 移行ガイド ](../overview.md) を参照してください。


## データ形式と構造のマイナーな変更

ほとんどの場合、[ マップステップ ](technical-specification.md#map-step) は、`map.xml` ファイルの次のメソッドを使用して、マイナーなデータ形式および構造の変更を十分に解決します。

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

- `great_blog_index` インデックス・テーブルから不要なデータを移行しないでください。
- Magento2 でテーブル `great_blog_publication` の名前が `great_blog_post` に変更されたため、データは新しいテーブルに移行されます。
   - `summary` フィールドの名前が `title` に変更されたので、データは新しいフィールドに移行されます。
   - `priority` フィールドは削除され、Magento 2 には存在しません。
   - `body` フィールドのデータは形式が変更されているため、カスタム ハンドラー `\Migration\Handler\GreatBlog\NewFormat` によって処理される必要があります。
- Magento 2 の「GreatBlog」拡張機能用に新しい評価機能が開発されました。
   - 新しい `great_blog_rating` テーブルが作成されました。
   - 新しい `great_blog_post.rating` フィールドが作成されました。

### 他の手順でのマッピングの拡張

[EAV ステップ ](technical-specification.md#eav-step) や顧客属性ステップなど、その他のステップはマッピングをサポートします。 次の手順では、Magentoテーブルの定義済みリストを移行します。 例えば、「GreatBlog」Magentoに `eav_attribute` テーブルのフィールドが追加されていて、拡張機能 2 で名前が変更されたとします。 テーブルは [EAV Step](technical-specification.md#eav-step) によって処理されるので、マッピングルールは `map-eav.xml` ファイルに書き込む必要があります。 `map.xml` ファイルと `map-eav.xml` ファイルは同じ `map.xsd` スキーマを使用するので、マッピングルールは同じままです。

## データ形式および構造の大幅な変更

`config.xml` ファイルには、マップ手順のほかに、形式や構造の大きな変更を加えてデータを移行する手順が次のように含まれています。

- [Url 書き換え手順](technical-specification.md#url-rewrite-step)
- OrderGrids ステップ
- [EAV ステップ](technical-specification.md#eav-step)

[ マップステップ ](technical-specification.md#map-step) とは異なり、これらのステップでは、すべてのテーブルではなく、事前に定義されたテーブルのリストをスキャンします。

データの形式および構造を大幅に変更する場合は、カスタムステップを作成します。

### カスタムステップの作成

同じ「GreatBlog」の例を使用して、Magento1 に 1 つのテーブルがあるものの、Magento2 に 2 つのテーブルを持つように再設計したとします。

Magento1 には、`greatblog_post` のテーブルが 1 つありました。

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
| tags      | TEXT     |
```

Magento 2 で、タグ `greatblog_post_tags` の新しいテーブルが導入されました。

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

古いテーブル構造から新しいテーブル構造にすべてのデータを移行するには、`config.xml` ファイルにカスタム ステップを作成します。 例：

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

ツールは、`config.xml` ファイル内の位置に応じて、上から順にステップを実行します。 この例では、`GreatBlog Step` が最後に実行されます。

手順には、次の 4 種類のクラスが含まれます。

- 整合性チェック
- データ配信
- ボリュームチェック
- Delta 配信

>[!NOTE]
>
>詳しくは、[ 設定 ](technical-specification.md#configuration)、[ ステップの内部 ](technical-specification.md#step-internals)、[ ステージ ](technical-specification.md#step-stages)、および [ 実行モード ](technical-specification.md#running-modes) を参照してください。


複雑な SQL クエリは、これらのクラス内で組み合わせて、データを取得および移行できます。 また、これらのテーブルは、既存のすべてのテーブルをスキャンし、`map.xml` ファイルの `<ignore>` タグにない限りデータの移行を試みるので [&#128279;](technical-specification.md#map-step) マップ手順  では「無視」する必要があります。

整合性チェックの場合は、追加のマップファイルを `config.xml` ファイルに定義して、テーブル構造が期待どおりであることを確認します。

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

マップ ファイル `map-greatblog.xml`:

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

整合性チェッククラス `Vendor\Migration\Step\GreatBlog\Integrity` は `Migration\App\Step\AbstractIntegrity` を拡張し、テーブル構造を検証する `perform` メソッドを含みます。

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

次に、データを処理してMagento2 データベース `Vendor\Migration\Step\GreatBlog\Data` ータに保存するためのクラスを作成する必要があります。

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

ボリューム・クラス `Vendor\Migration\Step\GreatBlog\Volume` では、データが完全に移行されたかどうかを確認します。

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

差分移行機能を追加するには、`deltalog.xml` ファイルに新しいグループを追加します。 `group` で、変更を確認する必要があるテーブルの名前を指定します。

```xml
<groups>
    ...
    <group name="delta_greatblog">
        <document key="post_id">greatblog_post</document>
    </group>
</groups>
```

次に、`Migration\App\Step\AbstractDelta` を拡張する `Delta` クラス `Vendor\Migration\Step\GreatBlog\Delta` を作成します。

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

これらの例に示すカスタムステップの実装の後、システムは単一のMagento 1 テーブルからデータを取得します。
クラス `Vendor\Migration\Step\GreatBlog\Data` 使用して処理し、2 つのMagento2 テーブルにデータを格納します。 新規および変更されたレコードは、`Vendor\Migration\Step\GreatBlog\Delta` クラスを使用してデルタ移行で配信されます。

## 禁止される拡張方法

[!DNL Data Migration Tool] とMagento2 は常に進化しているため、既存の手順やハンドラーは変更される可能性があります。 [ マップステップ ](technical-specification.md#map-step)、[URL 書き換えステップ ](technical-specification.md#url-rewrite-step)、ハンドラーなどのステップの動作は、クラスを拡張して上書きしないことを強くお勧めします。

一部の手順は、マッピングをサポートしておらず、変更するにはコードを変更する必要があります。 移行終了時にデータを変更する追加の手順を作成するか、[GitHub のイシューを作成し ](https://github.com/magento/data-migration-tool/issues) 既存の手順に新しい拡張ポイントを要求できます。
