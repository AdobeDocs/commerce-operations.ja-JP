---
title: モジュール設定ファイル
description: Adobe Commerceの設定タイプを使用してモジュールをカスタマイズする方法について説明します。 設定ファイル管理とモジュールのカスタマイズのベストプラクティスについて説明します。
exl-id: 87433c28-8e3d-43d0-b77e-3ff9a680af5f
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '2121'
ht-degree: 0%

---

# モジュール設定ファイルの概要

以前のバージョンのCommerceで使用されていた`config.xml`設定ファイルの責任は、様々なモジュールディレクトリにある複数のファイルに分割されるようになりました。 Commerceの複数の設定ファイルは、モジュールが特定の設定タイプをリクエストした場合にのみ、オンデマンドで読み込まれます。

これらのファイル（_設定タイプ_&#x200B;とも呼ばれます）を使用して、モジュールの動作の特定の側面をカスタマイズできます。

複数のモジュールで、同じ設定タイプ（イベントなど）に影響を与える設定ファイルを宣言でき、これらの複数の設定ファイルがマージされます。

このトピックで使用される一般的な用語は次のとおりです。

- **設定オブジェクト** – 設定タイプの定義と検証を担当するCommerce ライブラリまたはクラス。 例えば、`config.xml`の設定オブジェクトは[Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php)です。

- **設定ステージ** - ステージは&#x200B;_primary_、_global_、_area_&#x200B;として定義されます。 各ステージは、設定タイプが読み込まれ、同じ名前の設定タイプと結合されるタイミングを決定します。 例えば、`module.xml`個のファイルが他の`module.xml`個のファイルと結合されます。

- **設定スコープ** – 設定ステージを補完する、スコープは設定タイプモデルを定義します。 例えば、`adminhtml`は、他のモジュールの`adminhtml`設定と共にステージで読み込まれるエリアスコープです。 詳しくは、[ モジュールとエリア ](https://developer.adobe.com/commerce/php/architecture/modules/areas/)を参照してください。

## 設定の読み込みと結合

この節では、設定ファイルの読み込みと結合の方法について説明します。

### Commerceによる設定ファイルの読み込み方法

Commerceは、次の順序で設定ファイルを読み込みます（すべてのパスはCommerce インストールディレクトリに関連しています）。

- プライマリ設定（[app/etc/di.xml](https://github.com/magento/magento2/blob/2.4/app/etc/di.xml)）。 このファイルは、Commerceのブートストラップに使用されます。
- モジュール （`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/*.xml`）のグローバル設定。 すべてのモジュールから特定の設定ファイルを収集し、それらを結合します。
- モジュール （`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/<area>/*.xml`）の領域固有の設定。 すべてのモジュールから設定ファイルを収集し、それらをグローバル設定にマージします。 一部の領域固有の設定は、グローバル設定を上書きまたは拡張できます。

どこで

- `<your component base dir>`は、コンポーネントが配置されているベース ディレクトリです。 一般的な値は、Commerce インストールディレクトリに対する`app/code`または`vendor`です。
- `<vendorname>`はコンポーネントのベンダー名です。例えば、Commerceのベンダー名は`magento`です。
- `<component-type>`は次のいずれかです：

   - `module-`：拡張機能またはモジュール。
   - `theme-`：テーマ。
   - `language-`：言語パッケージ。

>[!INFO]
>
>現在、テーマは`<magento_root>/app/design/frontend`または`<magento_root>/app/design/adminhtml`の下にあります。

- `<component-name>`: [composer.json](https://github.com/magento/magento2/blob/2.4/composer.json)で定義されているコンポーネントの名前。

### 設定ファイルの結合

設定ファイル内のノードは、完全修飾XPathに基づいてマージされます。このXPathには、`$idAttributes`配列で定義された特殊属性が識別子として宣言されています。 この識別子は、同じ親ノードの下にネストされたすべてのノードに対して一意である必要があります。

Commerce アプリケーションの結合アルゴリズム：

- ノード識別子が同じ場合（または識別子が定義されていない場合）、ノード内のすべての基になるコンテンツ（属性、子ノード、スカラーのコンテンツ）が上書きされます。
- ノード識別子が等しくない場合、ノードは親ノードの新しい子になります。
- 元の文書に同じ識別子を持つ複数のノードがある場合、識別子を区別できないため、エラーがトリガーされます。

設定ファイルを結合すると、元のファイルのすべてのノードが結果のドキュメントに含まれます。

>[!INFO]
>
>[\Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) クラスを使用して、[構成ファイル ローダー](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L125)および[結合の構成](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L144) プロセスの背後にあるロジックをデバッグおよび理解できます。

## 設定の種類、オブジェクト、インターフェイス

次の節では、設定タイプ、対応する設定オブジェクト、およびオブジェクトの操作に使用できるインターフェイスに関する情報を示します。

### 設定タイプとオブジェクト

次の表に、各設定タイプと、それに関連するCommerce設定オブジェクトを示します。

| 設定ファイル | 説明 | ステージ | 設定オブジェクト |
| --- | --- | --- | --- |
| `address_formats.xml` | アドレス形式宣言 | プライマリ、グローバル | [\Magento\Customer\Model\Address\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/Model/Address/Config.php) |
| `acl.xml` | [ アクセス制御リスト ](https://developer.adobe.com/commerce/webapi/get-started/authentication/#relationship-between-aclxml-and-webapixml) | グローバル | [\Magento\Framework\Acl\AclResource\Provider](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Acl/AclResource/Provider.php) |
| `analytics.xml` | [高度なレポート ](https://developer.adobe.com/commerce/php/development/advanced-reporting/data-collection/) | プライマリ、グローバル | [\Magento\Analytics\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/Model/Config/Reader.php) |
| `cache.xml` | キャッシュタイプの宣言 | プライマリ、グローバル | [\Magento\Framework\Cache\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Config/Data.php) |
| `catalog_attributes.xml` | カタログ属性設定 | グローバル | [\Magento\Catalog\Model\Attribute\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/Attribute/Config/Data.php) |
| `config.php`と`env.php` | [ デプロイメント設定](../reference/deployment-files.md) | これらのファイルは、内部コンフィギュレーションプロセッサーによって読み取り/書き込みが可能です。 | オブジェクトがありません。カスタマイズできません |
| `config.xml` | システム設定 | プライマリ、グローバル | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `communication.xml` | [ メッセージキューシステムの側面を定義](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#communicationxml) | グローバル | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Communication](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Communication.php) |
| `crontab.xml` | [cron グループを設定](../cron/custom-cron-reference.md#configure-cron-groups) | グローバル | [\Magento\Cron\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Config/Data.php) |
| `cron_groups.xml` | [cron グループのオプションを指定](../cron/custom-cron-reference.md) | グローバル | [\Magento\Cron\Model\Groups\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Groups/Config/Data.php) |
| `db_schema.xml` | [宣言型スキーマ ](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) | グローバル | [Magento\Framework\Setup\Declaration\Schema](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/Declaration/Schema/SchemaConfig.php) |
| `di.xml` | [依存関係インジェクション ](https://developer.adobe.com/commerce/php/development/components/dependency-injection/)設定 | プライマリ、グローバル、エリア | [\Magento\Framework\ObjectManager\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/ObjectManager/Config/Config.php) |
| `eav_attributes.xml` | EAV属性設定を提供します | グローバル | [\Magento\Eav\Model\Entity\Attribute\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Eav/Model/Entity/Attribute/Config.php) |
| `email_templates.xml` | メールテンプレート設定 | グローバル | [\Magento\Email\Model\Template\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Email/Model/Template/Config/Data.php) |
| `esconfig.xml` | [検索エンジンロケールのストップワード設定](../search/search-stopwords.md#create-stopwords-for-a-new-locale) | グローバル | [\Magento\Elasticsearch\Model\Adapter\Index\Config\EsConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Elasticsearch/Model/Adapter/Index/Config/EsConfig.php) |
| `events.xml` | イベント/オブザーバー設定 | グローバル、エリア | [\Magento\Framework\Event](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Event.php) |
| `export.xml` | エンティティ設定の書き出し | グローバル | [\Magento\ImportExport\Model\Export\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Export/Config.php) |
| `extension_attributes.xml` | [拡張機能の属性](https://developer.adobe.com/commerce/php/development/components/attributes/#extension-attributes) | グローバル | [\Magento\Framework\Api\ExtensionAttribute\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Api/ExtensionAttribute/Config.php) |
| `fieldset.xml` | フィールドセットの定義 | グローバル | [\Magento\Framework\DataObject\Copy\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DataObject/Copy/Config/Reader.php) |
| `indexer.xml` | [ インデクサーを宣言](https://developer.adobe.com/commerce/php/development/components/indexing/custom-indexer/) | グローバル | [\Magento\Framework\Indexer\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Indexer/Config/Reader.php) |
| `import.xml` | インポートエンティティを宣言 | グローバル | [\Magento\ImportExport\Model\Import\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Import/Config.php) |
| `menu.xml` | 管理者のメニュー項目を定義します | adminhtml | [\Magento\Backend\Model\Menu\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Backend/Model/Menu/Config/Reader.php) |
| `module.xml` | モジュール設定データとソフト依存関係を定義します | プライマリ、グローバル | [\Magento\Framework\Module\ModuleList\Loader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Module/ModuleList/Loader.php) |
| `mview.xml` | [MView設定](https://developer.adobe.com/commerce/php/development/components/indexing/custom-indexer/#mview-configuration) | プライマリ、グローバル | [\Magento\Framework\Mview\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Mview/Config/Data.php) |
| `payment.xml` | 支払いモジュール設定 | プライマリ、グローバル | [\Magento\Payment\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Payment/Model/Config.php) |
| `persistent.xml` | [Magento_Persistent](https://developer.adobe.com/commerce/php/module-reference/module-persistent/)設定ファイル | グローバル | [\Magento\Persistent\Helper\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Persistent/Helper/Data.php) |
| `pdf.xml` | PDFの設定 | グローバル | [\Magento\Sales\Model\Order\Pdf\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config/Reader.php) |
| `product_options.xml` | 製品オプション設定を提供します | グローバル | [\Magento\Catalog\Model\ProductOptions\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductOptions/Config.php) |
| `product_types.xml` | 製品タイプの定義 | グローバル | [\Magento\Catalog\Model\ProductTypes\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductTypes/Config.php) |
| `queue_consumer.xml` | [既存のキューとそのコンシューマーとの関係を定義します](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_consumerxml) | グローバル | [\Magento\Framework\MessageQueue\Consumer\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Consumer/Config/Xml/Reader.php) |
| `queue_publisher.xml` | [ トピックが公開される取引所を定義します。](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_publisherxml) | グローバル | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Publisher](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Publisher.php) |
| `queue_topology.xml` | [ メッセージのルーティングルールを定義し、キューと交換を宣言します](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_topologyxml) | グローバル | [\Magento\Framework\MessageQueue\Topology\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Topology/Config/Xml/Reader.php) |
| `reports.xml` | [詳細レポート ](https://developer.adobe.com/commerce/php/development/advanced-reporting/report-xml/) | グローバル | [\Magento\Analytics\ReportXml\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config.php) |
| `resources.xml` | モジュールリソースを定義します | グローバル | [\Magento\Framework\App\ResourceConnection\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/ResourceConnection/Config/Reader.php) |
| `routes.xml` | [ ルート ](https://developer.adobe.com/commerce/php/development/components/routing/)設定 | エリア | [Magento\Framework\App\Route\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Route/Config.php) |
| `sales.xml` | 売上合計の設定を定義 | グローバル | [\Magento\Sales\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Config/Data.php) |
| `search_engine.xml` | 検索エンジン設定を提供します | グローバル | [Magento\Search\Model\SearchEngine\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Search/Model/SearchEngine/Config.php) |
| `search_request.xml` | カタログ検索設定の定義 | グローバル | [\Magento\Framework\Search\Request\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Search/Request/Config.php) |
| `sections.xml` | プライベートコンテンツブロックのトリガーキャッシュ無効化アクションを定義します | フロントエンド | [SectionInvalidationConfigReader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/di.xml#L137-L148) |
| `system.xml` | システム設定ページのオプションを定義します | adminhtml | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `validation.xml` | モジュール検証設定ファイル | グローバル | [\Magento\Framework\Validator\Factory](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Validator/Factory.php) |
| `view.xml` | Vendor_Module ビューの設定値を定義します | グローバル | [\Magento\Framework\View\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Config.php) |
| `webapi.xml` | [Web APIを設定](https://developer.adobe.com/commerce/php/development/components/web-api/services/) | グローバル | [\Magento\Webapi\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Webapi/Model/Config.php) |
| `webapi_async.xml` | [REST カスタムルートを定義](https://developer.adobe.com/commerce/php/development/components/web-api/custom-routes/) | グローバル | [\Magento\WebapiAsync\Model\ServiceConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Model/ServiceConfig.php) |
| `widget.xml` | ウィジェットの定義 | グローバル | [\Magento\Widget\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Widget/Model/Config/Reader.php) |
| `zip_codes.xml` | 各国の郵便番号を定義します | グローバル | [\Magento\Directory\Model\Country\Postcode\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Directory/Model/Country/Postcode/Config/Data.php) |

### 設定インターフェイス

[Magento\Framework\Config](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Config)のインターフェイスを使用して、設定ファイルを操作できます。

これらのインターフェイスは、[設定タイプを作成](../reference/config-create-types.md#create-configuration-types)する場合に使用できます。

`Magento\Framework\Config`は次のインターフェイスを提供します。

- [Framework\Config\ConverterInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ConverterInterface.php)。XMLを設定のメモリ内の配列表現に変換します。
- [Framework\Config\DataInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/DataInterface.php)。指定されたスコープ内の設定データを取得します。
- [Framework\Config\FileResolverInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/FileResolverInterface.php)です。[Magento\Framework\Config\ReaderInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php)が読み取るファイルの場所を特定します。
- [Framework\Config\ReaderInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php)は、ストレージから構成データを読み取り、読み取り元のストレージを選択します。

つまり、ファイルシステム、データベース、その他のストレージは、結合ルールに従って設定ファイルを結合し、検証スキーマを使用して設定ファイルを検証します。

- [Framework\Config\SchemaLocatorInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/SchemaLocatorInterface.php)。XSD スキーマを検索します。
- [Framework\Config\ScopeListInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ScopeListInterface.php)。スコープのリストを返します。
- [Framework\Config\ValidationStateInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ValidationStateInterface.php)。検証状態を取得します。
