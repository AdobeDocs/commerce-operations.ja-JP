---
title: モジュール設定ファイル
description: 設定タイプを使用してモジュールをカスタマイズする方法を説明します。
exl-id: 87433c28-8e3d-43d0-b77e-3ff9a680af5f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1252'
ht-degree: 0%

---

# モジュール設定ファイルの概要

の責任 `config.xml` 以前のバージョンのCommerceで使用されていた設定ファイルが、様々なモジュールディレクトリに配置された複数のファイルに分割されるようになりました。 Commerceの複数の設定ファイルは、モジュールが特定の設定タイプをリクエストした場合にのみ、オンデマンドで読み込まれます。

これらのファイルは、次の名前でも使用できます _設定タイプ_- モジュールの動作の特定の側面をカスタマイズします。

複数のモジュールで、同じ設定タイプ（イベントなど）に影響を与える設定ファイルを宣言でき、これらの複数の設定ファイルは結合されます。

このトピックで使用される一般的な用語を次に示します。

- **設定オブジェクト** – 設定タイプの定義と検証を担当するCommerce ライブラリまたはクラス。 例えば、の設定オブジェクトです。 `config.xml` 等しい [Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php).

- **設定ステージ**- ステージは次のように定義されます _プライマリ_, _global_、および _面グラフ_. 各ステージでは、設定タイプを読み込んで、同じ名前の設定タイプと結合するタイミングを決定します。 例： `module.xml` ファイルは他の `module.xml` ファイル。

- **設定スコープ** – 設定ステージを補完するものとして、スコープが設定タイプモデルを定義します。 例： `adminhtml` は、他のモジュールと共にステージで読み込まれるエリアスコープです `adminhtml` 設定。 詳しくは、を参照してください [モジュールとエリア](https://developer.adobe.com/commerce/php/architecture/modules/areas/).

## 設定の読み込みと結合

この節では、設定ファイルの読み込みと結合方法について説明します。

### Commerceによる設定ファイルの読み込み方法

Commerceは、次の順序で設定ファイルを読み込みます（すべてのパスは、Commerce インストールディレクトリを基準とした相対パスです）。

- プライマリ設定（[app/etc/di.xml](https://github.com/magento/magento2/blob/2.4/app/etc/di.xml)）に設定します。 このファイルは、Commerceをブートストラップするために使用されます。
- モジュールからのグローバル設定（`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/*.xml`）に設定します。 すべてのモジュールから特定の設定ファイルを収集し、それらを結合します。
- モジュールからの領域固有の設定（`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/<area>/*.xml`）に設定します。 すべてのモジュールから構成ファイルを収集し、グローバル構成に結合します。 一部の領域固有の設定では、グローバル設定をオーバーライドまたは拡張できます。

ここで、

- `<your component base dir>` は、コンポーネントが配置されているベースディレクトリです。 一般的な値は次のとおりです `app/code` または `vendor` Commerce インストールディレクトリからの相対パスで指定します。
- `<vendorname>` は、コンポーネントのベンダー名です。例えば、Commerceのベンダー名はです `magento`.
- `<component-type>` は次のいずれかです。

   - `module-`：拡張機能またはモジュール。
   - `theme-`：テーマ。
   - `language-`：言語パッケージ。

>[!INFO]
>
>現在、テーマはの配下に配置されています `<magento_root>/app/design/frontend` または `<magento_root>/app/design/adminhtml`.

- `<component-name>`：で定義されているコンポーネントの名前 [composer.json](https://github.com/magento/magento2/blob/2.4/composer.json).

### 設定ファイルの結合

設定ファイルのノードは、で定義された特別な属性を持つ完全修飾 XPath に基づいて結合されます。 `$idAttributes` 識別子として宣言された配列。 この識別子は、同じ親ノードの下にネストされたすべてのノードで一意である必要があります。

Commerce アプリケーション結合アルゴリズム：

- ノード識別子が等しい（または識別子が定義されていない）場合、ノード内の基になるすべてのコンテンツ（属性、子ノード、スカラーコンテンツ）が上書きされます。
- ノードの識別子が等しくない場合、そのノードは親ノードの新しい子になります。
- 元のドキュメントに同じ識別子を持つ複数のノードがある場合、識別子を区別できないのでエラーがトリガーされます。

設定ファイルが結合されると、結合後の文書には元のファイルのすべてのノードが含まれます。

>[!INFO]
>
>次を使用できます [\Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) デバッグと、背後にあるロジックの理解のためのクラス [設定ファイルローダー](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L125) および [結合設定](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L144) プロセス。

## 設定のタイプ、オブジェクトおよびインターフェイス

次の節では、設定のタイプ、対応する設定オブジェクトおよびオブジェクトを操作するために使用できるインターフェイスについて説明します。

### 設定のタイプとオブジェクト

次の表に、各設定タイプと、それに関連するCommerce設定オブジェクトを示します。

| 設定ファイル | 説明 | ステージ | 設定オブジェクト |
| --- | --- | --- | --- |
| `address_formats.xml` | 住所形式宣言 | プライマリ、グローバル | [\Magento\Customer\Model\Address\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/Model/Address/Config.php) |
| `acl.xml` | [アクセス制御リスト](https://developer.adobe.com/commerce/webapi/get-started/authentication/#relationship-between-aclxml-and-webapixml) | global | [\Magento\Framework\Acl\AclResource\Provider](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Acl/AclResource/Provider.php) |
| `analytics.xml` | [高度なレポート](https://devdocs.magento.com/guides/v2.4/advanced-reporting/data-collection.html) | プライマリ、グローバル | [\Magento\Analytics\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/Model/Config/Reader.php) |
| `cache.xml` | キャッシュタイプの宣言 | プライマリ、グローバル | [\Magento\Framework\Cache\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Config/Data.php) |
| `catalog_attributes.xml` | カタログ属性の設定 | global | [\Magento\Catalog\Model\Attribute\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/Attribute/Config/Data.php) |
| `config.php` および `env.php` | [デプロイメント設定](../reference/deployment-files.md) | これらのファイルは、内部の config プロセッサによって読み取り/書き込み可能です。 | オブジェクトがないため、カスタマイズできません |
| `config.xml` | システム設定 | プライマリ、グローバル | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `communication.xml` | [メッセージキューシステムの側面を定義します](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#communicationxml) | global | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Communication](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Communication.php) |
| `crontab.xml` | [Cron グループを設定](../cron/custom-cron-reference.md#configure-cron-groups) | global | [\Magento\Cron\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Config/Data.php) |
| `cron_groups.xml` | [cron グループのオプションを指定します](../cron/custom-cron-reference.md) | global | [\Magento\Cron\Model\Groups\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Groups/Config/Data.php) |
| `db_schema.xml` | [宣言スキーマ](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) | global | [Magento\Framework\Setup\Declaration\Schema](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/Declaration/Schema/SchemaConfig.php) |
| `di.xml` | [依存関係の挿入](https://developer.adobe.com/commerce/php/development/components/dependency-injection/) 設定 | プライマリ，グローバル，領域 | [\Magento\Framework\ObjectManager\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/ObjectManager/Config/Config.php) |
| `eav_attributes.xml` | EAV 属性の設定を提供 | global | [\Magento\Eav\Model\Entity\Attribute\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Eav/Model/Entity/Attribute/Config.php) |
| `email_templates.xml` | メールテンプレートの設定 | global | [\Magento\Email\Model\Template\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Email/Model/Template/Config/Data.php) |
| `esconfig.xml` | [検索エンジンのロケールストップワード設定](../search/search-stopwords.md#create-stopwords-for-a-new-locale) | global | [\Magento\Elasticsearch\Model\Adapter\Index\Config\EsConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Elasticsearch/Model/Adapter/Index/Config/EsConfig.php) |
| `events.xml` | イベント/オブザーバー設定 | グローバル、領域 | [\Magento\Framework\Event](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Event.php) |
| `export.xml` | エンティティ設定をエクスポート | global | [\Magento\ImportExport\Model\Export\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Export/Config.php) |
| `extension_attributes.xml` | [拡張属性](https://developer.adobe.com/commerce/php/development/components/attributes/#extension-attributes) | global | [\Magento\Framework\Api\ExtensionAttribute\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Api/ExtensionAttribute/Config.php) |
| `fieldset.xml` | フィールドセットを定義します | global | [\Magento\Framework\DataObject\Copy\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DataObject/Copy/Config/Reader.php) |
| `indexer.xml` | [インデクサーを宣言](https://developer.adobe.com/commerce/php/development/components/indexing/custom-indexer/) | global | [\Magento\Framework\Indexer\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Indexer/Config/Reader.php) |
| `import.xml` | インポートエンティティを宣言します | global | [\Magento\ImportExport\Model\Import\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Import/Config.php) |
| `menu.xml` | 管理者のメニュー項目を定義します | adminhtml | [\Magento\Backend\Model\Menu\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Backend/Model/Menu/Config/Reader.php) |
| `module.xml` | モジュール設定データとソフト依存関係を定義します | プライマリ、グローバル | [\Magento\Framework\Module\ModuleList\Loader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Module/ModuleList/Loader.php) |
| `mview.xml` | [MView 構成](https://developer.adobe.com/commerce/php/development/components/indexing/custom-indexer/#mview-configuration) | プライマリ、グローバル | [\Magento\Framework\Mview\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Mview/Config/Data.php) |
| `payment.xml` | 支払いモジュールの設定 | プライマリ、グローバル | [\Magento\Payment\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Payment/Model/Config.php) |
| `persistent.xml` | [Magento_持続](https://developer.adobe.com/commerce/php/module-reference/module-persistent/) 設定ファイル | global | [\Magento\Persistent\Helper\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Persistent/Helper/Data.php) |
| `pdf.xml` | PDF設定 | global | [\Magento\Sales\Model\Order\Pdf\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config/Reader.php) |
| `product_options.xml` | 製品オプションを設定できます | global | [\Magento\Catalog\Model\ProductOptions\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductOptions/Config.php) |
| `product_types.xml` | 製品タイプを定義します | global | [\Magento\Catalog\Model\ProductTypes\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductTypes/Config.php) |
| `queue_consumer.xml` | [既存のキューとそのコンシューマーの関係を定義します](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_consumerxml) | global | [\Magento\Framework\MessageQueue\Consumer\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Consumer/Config/Xml/Reader.php) |
| `queue_publisher.xml` | [トピックが公開される取引所を定義します。](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_publisherxml) | global | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Publisher](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Publisher.php) |
| `queue_topology.xml` | [メッセージのルーティングルールを定義し、キューおよび交換を宣言します。](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_topologyxml) | global | [\Magento\Framework\MessageQueue\Topology\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Topology/Config/Xml/Reader.php) |
| `reports.xml` | [高度なレポート](https://devdocs.magento.com/guides/v2.4/advanced-reporting/report-xml.html) | global | [\Magento\Analytics\ReportXml\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config.php) |
| `resources.xml` | モジュールリソースを定義します | global | [\Magento\Framework\App\ResourceConnection\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/ResourceConnection/Config/Reader.php) |
| `routes.xml` | [ルート](https://developer.adobe.com/commerce/php/development/components/routing/) 設定 | 面グラフ | [Magento\Framework\App\Route\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Route/Config.php) |
| `sales.xml` | 売上合計のコンフィギュレーションを定義します | global | [\Magento\Sales\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Config/Data.php) |
| `search_engine.xml` | 検索エンジン設定を提供します。 | global | [Magento\Search\Model\SearchEngine\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Search/Model/SearchEngine/Config.php) |
| `search_request.xml` | カタログ検索設定を定義します | global | [\Magento\Framework\Search\Request\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Search/Request/Config.php) |
| `sections.xml` | プライベートコンテンツブロックのキャッシュ無効化をトリガーにするアクションを定義します | フロントエンド | [SectionInvalidationConfigReader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/di.xml#L137-L148) |
| `system.xml` | システム設定ページのオプションを定義します | adminhtml | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `validation.xml` | モジュール検証設定ファイル | global | [\Magento\Framework\Validator\Factory](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Validator/Factory.php) |
| `view.xml` | Vendor_Module 表示設定値を定義します | global | [\Magento\Framework\View\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Config.php) |
| `webapi.xml` | [Web API を設定します](https://developer.adobe.com/commerce/php/development/components/web-api/services/) | global | [\Magento\Webapi\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Webapi/Model/Config.php) |
| `webapi_async.xml` | [REST カスタムルートを定義します](https://developer.adobe.com/commerce/php/development/components/web-api/custom-routes/) | global | [\Magento\WebapiAsync\Model\ServiceConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Model/ServiceConfig.php) |
| `widget.xml` | ウィジェットを定義します | global | [\Magento\Widget\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Widget/Model/Config/Reader.php) |
| `zip_codes.xml` | 国ごとに郵便番号を定義します | global | [\Magento\Directory\Model\Country\Postcode\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Directory/Model/Country/Postcode/Config/Data.php) |

### 設定インターフェイス

の下のインターフェイスを使用して、設定ファイルを操作できます。 [Magento\Framework\Config](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Config).

次の場合に、これらのインターフェイスを使用できます [設定タイプの作成](../reference/config-create-types.md#create-configuration-types).

`Magento\Framework\Config` は次のインターフェイスを提供します。

- [Framework\Config\ConverterInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ConverterInterface.php)XML を、設定のメモリ内配列表現に変換します。
- [Framework\Config\DataInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/DataInterface.php)：指定したスコープ内の設定データを取得します。
- [Framework\Config\FileResolverInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/FileResolverInterface.php)：読み取るファイルの場所を識別します。 [Magento\Framework\Config\ReaderInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php).
- [Framework\Config\ReaderInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php)。ストレージから設定データを読み取り、読み取り元のストレージを選択します。

つまり、ファイルシステム、データベース、その他のストレージは、結合ルールに従って設定ファイルを結合し、検証スキーマを使用して設定ファイルを検証します。

- [Framework\Config\SchemaLocatorInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/SchemaLocatorInterface.php):XSD スキーマを見つけます。
- [Framework\Config\ScopeListInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ScopeListInterface.php)：範囲のリストを返します。
- [Framework\Config\ValidationStateInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ValidationStateInterface.php)：検証状態を取得します。
