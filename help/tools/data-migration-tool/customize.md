---
title: のカスタマイズ [!DNL Data Migration Tool]
description: カスタマイズ方法を学ぶ [!DNL Data Migration Tool] 拡張機能によって作成されたデータをMagento1 とMagento2 の間で転送するには、以下を実行します。
exl-id: a5c1575f-9d77-416e-91fe-a82905ef2e1c
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 0%

---

# を設定します。 [!DNL Data Migration Tool]

場合によっては、 [拡張機能](https://marketplace.magento.com/extensions.html) またはカスタムコードがMagento1 とMagento2 で異なる。 内で拡張ポイントを使用する [!DNL Data Migration Tool] をクリックして、このデータを移行します。 データの形式と構造が同じ場合、ユーザーの操作を必要とせずに、自動的にデータを移行できます。

移行中に、 [マッピングステップ](technical-specification.md#map-step) は、拡張機能で作成されたテーブルを含め、Magento1 とMagento2 のすべてのテーブルをスキャンおよび比較します。 テーブルが同じ場合、ツールは自動的にデータを移行します。 テーブルが異なる場合、ツールは終了し、ユーザーに通知します。

>[!NOTE]
>
>詳しくは、 [技術仕様](technical-specification.md) 拡張する前に [!DNL Data Migration Tool]. また、 [移行ガイド](../overview.md) 移行ツールの使用に関する一般的な情報については、を参照してください。


## データの小規模な形式と構造の変更

ほとんどの場合、 [マッピングステップ](technical-specification.md#map-step) で次のメソッドを使用して、小さなデータ形式と構造の変更を十分に解決できます。 `map.xml` ファイル：

- マッピングルールを使用してテーブル名またはフィールド名を変更する
- 既存のハンドラーまたはカスタムハンドラーを使用してデータ形式を変換する

次に、マッピングルールとハンドラーの両方を使用する例を示します。 この例では、Magento2 向けに改善された「GreatBlog」と呼ばれる仮のMagento1 拡張を使用しています。

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

- 不要なデータを `great_blog_index` インデックステーブル。
- テーブル `great_blog_publication` はに名前が変更されました。 `great_blog_post` Magento2 では、データは新しいテーブルに移行されます。
   - The `summary` フィールド名は「 」に変更されました。 `title`の場合、データは新しいフィールドに移行されます。
   - The `priority` フィールドが削除され、Magento2 には存在しなくなりました。
   - のデータ `body` フィールドの形式が変更されました。カスタムハンドラーで処理する必要があります。 `\Migration\Handler\GreatBlog\NewFormat`.
- Magento2 の「GreatBlog」拡張機能に対して、新しい評価機能が開発されました。
   - 新しい `great_blog_rating` テーブルが作成されました。
   - 新しい `great_blog_post.rating` フィールドが作成されました。

### 他の手順でのマッピングの拡張

その他の手順では、マッピングをサポートします ( 例： [EAV ステップ](technical-specification.md#eav-step) および顧客属性の手順を参照してください。 これらの手順では、事前に定義されたMagento表のリストを移行します。 例えば、「GreatBlog」拡張機能に、 `eav_attribute` 表と名前がMagento2 で変更されました。 テーブルは [EAV ステップ](technical-specification.md#eav-step)の場合、マッピングルールを記述して `map-eav.xml` ファイル。 The `map.xml` および `map-eav.xml` 同じ `map.xsd` スキーマの場合、マッピングルールは同じままです。

## データのフォーマットと構造の大きな変更

マップステップに加えて、 `config.xml` 大きな形式と構造の変更を含むデータを移行するファイル。次のものが含まれます。

- [Url 書き換えステップ](technical-specification.md#url-rewrite-step)
- OrderGrids ステップ
- [EAV ステップ](technical-specification.md#eav-step)

とは異なり、 [マッピングステップ](technical-specification.md#map-step)の場合、これらの手順では、すべてのテーブルではなく、定義済みのテーブルリストをスキャンします。

データの形式や構造を大幅に変更する場合は、カスタムステップを作成します。

### カスタムステップの作成

同じ「GreatBlog」の例を使用して、Magento1 に 1 つのテーブルがあるが、Magento2 に 2 つのテーブルがあるように再設計されたとします。

Magento1 には、 `greatblog_post` テーブル：

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
| tags      | TEXT     |
```

Magento2 で、タグの新しいテーブル `greatblog_post_tags` が導入されました。

```text
| Field      | Type     |
|------------|----------|
| post_id    | INT      |
| tag        | VARCHAR  |
| sort_order | SMALLINT |
```

MAGENTO2 `greatblog_post` テーブルは次のようになります。

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
```

すべてのデータを古いテーブル構造から新しい構造に移行するには、 `config.xml` ファイル。 例：

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

ツールは、 `config.xml` ファイル内に配置します。 この例では、 `GreatBlog Step` が最後に実行されます。

手順には、次の 4 つのタイプのクラスを含めることができます。

- 整合性チェック
- データ配信
- ボリュームチェック
- デルタ配信

>[!NOTE]
>
>参照： [設定](technical-specification.md#configuration), [ステップの内部](technical-specification.md#step-internals), [ステージ](technical-specification.md#step-stages)、および [実行モード](technical-specification.md#running-modes) を参照してください。


複雑な SQL クエリをこれらのクラス内に組み立てて、データを取得および移行できます。 また、これらのテーブルは [マッピングステップ](technical-specification.md#map-step) 既存のテーブルをすべてスキャンし、データを移行しようとするので、データが `<ignore>` タグ `map.xml` ファイル。

整合性チェックの場合は、 `config.xml` ファイルを使用して、テーブル構造が期待どおりであることを確認します。

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

整合性チェッククラス `Vendor\Migration\Step\GreatBlog\Integrity` extends `Migration\App\Step\AbstractIntegrity` とには、 `perform` メソッドを使用して、テーブル構造を検証します。

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

次に、データを処理してMagento2 データベースに保存するためのクラスを作成する必要があります `Vendor\Migration\Step\GreatBlog\Data`:

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

ボリュームクラス内 `Vendor\Migration\Step\GreatBlog\Volume`に設定されている場合、データが完全に移行されたかどうかを確認します。

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

差分移行機能を追加するには、 `deltalog.xml` ファイル。 In `group`、変更の確認が必要なテーブルの名前を指定します。

```xml
<groups>
    ...
    <group name="delta_greatblog">
        <document key="post_id">greatblog_post</document>
    </group>
</groups>
```

次に、 `Delta` クラス `Vendor\Migration\Step\GreatBlog\Delta` が拡張する `Migration\App\Step\AbstractDelta`:

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

この例で示すカスタム手順の実装後、システムは単一のMagento1 テーブルからデータを取得し、次を使用して処理します。 `Vendor\Migration\Step\GreatBlog\Data` クラスを使用し、2 つのMagento2 テーブルにデータを格納します。 新しいレコードと変更されたレコードは、 `Vendor\Migration\Step\GreatBlog\Delta` クラス。

## 禁止されている拡張メソッド

以降 [!DNL Data Migration Tool] とMagento2 は常に進化しており、既存の手順とハンドラーは変更される可能性があります。 手順 ( [マッピングステップ](technical-specification.md#map-step), [URL 書き換えステップ](technical-specification.md#url-rewrite-step)、およびハンドラーを拡張します。

一部の手順ではマッピングがサポートされず、コードを変更しない限り変更できません。 移行後にデータを変更する手順を追加するか、 [GitHub の問題](https://github.com/magento/data-migration-tool/issues) 既存のステップで新しい拡張ポイントを探します。
