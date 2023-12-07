---
title: コアおよびサードパーティの PHP コードを変更する際のベストプラクティス
description: コアAdobe Commerceおよびサードパーティの PHP コードを変更する方法とタイミングについて説明します。
role: Developer, Architect
feature: Best Practices
last-substantial-update: 2023-12-8
source-git-commit: ab02552939d595627f0de83b8508c7cd21777642
workflow-type: tm+mt
source-wordcount: '1747'
ht-degree: 0%

---

# コアおよびサードパーティの PHP コードを変更または上書きするためのベストプラクティス

このドキュメントでは、作成しなかったコード、直接制御しなかったコードの機能、結果、入力を変更する必要が生じた場合のベストプラクティスについて説明します。 つまり、コアコードとサードパーティコードです。 このドキュメントでは、主にバックエンドの PHP コードに焦点を当てています。

## コードを変更する方法

コードを変更する場合は、変更の範囲を考慮することが重要です。 変更の「範囲」とは、コード変更の影響がどの程度まで及ぶかを指します。 ベストプラクティスとして、フットプリントが最も小さく、リソース使用量が最も少ないオプションに基づいて、最終的な実装の完了方法を決定します。 コードのオーバーライドを広く伝えるほど、開発チームがAdobe Commerceのコア機能から逸脱する傾向が強まり、バグの発生の可能性が高まり、将来コードベースを維持するための取り組みが増えます。

### パッチ

パッチとは、開発チームが直接管理していないファイル内のコードを直接変更する手順を含むファイルです。 これは、他のオプションが存在しない場合、通常は最後の手段と見なす必要があるオプションです。 パッチは一時的なソリューションになるように設計されています。 一般的なベストプラクティスとして、パッチを作成する必要がある場合は、次の 2～4 週間以内に、より永続的なソリューションを得るために、パッチを削除します。 

パッチは簡単に壊れます。 パッチの対象となるファイルが更新された場合、多くの場合、パッチの動作が停止します。 これは、パッチ・ファイルには、パッチによって何が変更されるかを示す行番号と列番号が含まれているからです。 パッチの期待値と一致しないものがある場合、適用は停止され、コードが壊れます。

```bash
diff --git a/vendor/magento/module-quote/Model/QuoteManagement.php b/vendor/magento/module-quote/Model/QuoteManagement.php
index 51b68411d40..ac4a3468322 100644
--- a/vendor/magento/module-quote/Model/QuoteManagement.php
+++ b/vendor/magento/module-quote/Model/QuoteManagement.php
@@ -424,8 +424,9 @@ class QuoteManagement implements CartManagementInterface
                 }
             }
             $quote->setCustomerIsGuest(true);
-            $groupId = $customer ? $customer->getGroupId() : GroupInterface::NOT_LOGGED_IN_ID;
-            $quote->setCustomerGroupId($groupId);
+            $quote->setCustomerGroupId(
+                $quote->getCustomerId() ? $customer->getGroupId() : GroupInterface::NOT_LOGGED_IN_ID
+            );
         }
  
         $remoteAddress = $this->remoteAddress->getRemoteAddress();
```

#### パッチを使用して変更できる内容

何でも。 文字どおり、ターゲットファイル内の任意の文字を変更できます。 パッチは、特定のファイルタイプやコード言語に限定されません。 通常、パッチを使用して、 `vendor` ディレクトリ。 

#### パッチを使用するタイミング

他に選択肢がないと気付いたら。 例えば、ベンダーがコードの修正をまだ公開していない場合は、パッチを使用して、永続的なソリューションを待つ間に、問題を一時的に解決できます。

#### 欠点

パッチは簡単に壊れます。 ターゲットコードが変更されると、パッチは機能しなくなります。 これらは、短期的なソリューションに過ぎません。

### 環境設定

環境設定とは、Adobe Commerceプラットフォームに設計された概念です。 これは基本的に「PHP クラスの置き換え」です。

Adobe Commerceプラットフォームは、PHP クラスをインスタンス化する際に「オブジェクトマネージャー」を使用します。これは、従来の PHP アプリケーションで行われているように、新しいキーワードで PHP クラスをインスタンス化しないからです。 代わりに、オブジェクトマネージャは、コンパイルされた設定に対してインスタンス化する PHP クラスの名前を相互参照し、モジュールが元のクラスのプリファレンスを宣言しているかどうかを判断します。 PHP クラスのプリファレンスが見つかった場合、オブジェクトマネージャは、指定したクラスをインスタンス化します。

（通常）元の PHP クラスに代わる新しい PHP クラスは、元の PHP クラスから拡張または継承されることに注意してください。 これは、いくつかの理由でおこなわれます。

- 依存関係のインジェクション/タイプヒンティングに準拠するようにする。 そうしないと、致命的なエラーが発生し、アプリケーションが中断します。
- 最小限のコード書き込みを可能にする。 元の PHP クラスに 10 個のメソッドが含まれていて、1 つのメソッドだけを上書きする必要がある場合、通常は 1 つのメソッドだけを変更し、他の 9 つのメソッドはそのまま残します。 プラットフォームが新しいバージョンにアップグレードされるので、コア機能の更新をブロックしないようにすることが重要です。

#### 環境設定を宣言

プリファレンスを宣言するのは、かなり簡単なプロセスです。 1 行のコードを `di.xml` ファイルを含める必要があります。 これは、グローバルに、またはAdobe Commerceの「領域」内で、次のように実行できます。 `frontend`, `adminhtml`, `graphql`, `webapi_rest`、および `crontab`.

```xml
<preference for="Magento\Elasticsearch7\SearchAdapter\Adapter" type="Vendor\Namespace\Adapter\AlgoliaElasticSearch7Adapter"/>
```

```php
<?php

declare(strict_types=1);

namespace Vendor\Namespace\Adapter;

class AlgoliaElasticSearchAdapter extends \Magento\Elasticsearch7\SearchAdapter\Adapter
{
}
```

#### プリファレンスで変更できる内容

PHP クラスのみが、プリファレンスで上書きできます。 PHP クラス内で、パブリックメソッドと保護されたメソッドおよびプロパティを変更できます。 パブリックメソッドおよび保護メソッドの場合は、メソッドを完全に上書きするか、元の親メソッドに対する引数（または結果）を変更できます。

プライベートメソッドは、技術的に上書きできません。 ただし、元のプライベートメソッドに代わる独自の置き換えを作成することはできます。 任意の名前を付けることも、元の名前を使用することもできます。 プライベートメソッドは、そのメソッドを含む実際のファイル内にのみ存在するので、問題はありません。 プライベートメソッドを上書きするには、元のプライベートメソッドを呼び出すパブリックメソッドまたは保護されたメソッドを上書きまたは変更する必要があります。また、その代わりに独自の機能を置き換える必要があります。

#### 環境設定を使用するタイミング

再度、他のオプションが存在せず、依存関係の挿入、プラグイン、監視者で目標を達成できない場合は、環境設定を使用する必要があります。 非公開または保護されたメソッドやプロパティを変更または上書きする必要がある場合は、環境設定が必要な場合があります。 環境設定は慎重に使用する必要があることに注意する必要があります。 これらは、アプリケーションを変更する「かなり貪欲な」方法で、PHP クラスの所有権を効果的に取得します。 これにより、サードパーティのモジュールと競合し、コアクラスの更新をブロックして、診断が困難なバグを引き起こす可能性があります。 Adobe Commerceプラットフォームは、その他の手段を含むように設計されており、基礎となるコードに対する変更をより小さなフットプリントでおこなうことができます。

#### 欠点

環境設定は、コードを変更する貪欲な方法で、他のオプションが存在しない場合にのみ使用してください。 環境設定は、コードベース内での競合を引き起こす可能性があり、さらに悪いことに、プラットフォームのアップグレード時に発生するコア更新をブロックできます。 

### 監視者

監視者とは、多くのアプリケーション、プラットフォーム、ライブラリ、コーディング言語で見られる、イベントリスナーの概念です。 概念は、Adobe Commerceプラットフォームに固有のものではありません。 オブザーバーはMagento1 の日以降、プラットフォームに組み込まれており、コアコードとサードパーティコードの変更方法の主な選択肢と見なされています。 

コアコードベースおよびその他のサードパーティモジュールは、コード内の選択した場所でイベントをディスパッチできます。 監視者（内で宣言） `events.xml` ファイルを作成し、名前別にディスパッチされるイベントをリッスンしている、グローバルレベルで機能する、またはAdobe Commerceの「領域」に制限される（など） `frontend`, `adminhtml`, `graphql`, `webapi_rest`、および `crontab`.

#### 監視者を宣言する方法

オブザーバーは、グローバルまたはエリア固有で設定できます `events.xml` ファイル。

```xml
    <event name="sales_model_service_quote_submit_before">
        <observer name="set_reward_flag_order" instance="Adobe\RewardAdjustments\Observer\SetOrderRewardFlag" />
    </event>
```

```php
<?php

declare(strict_types=1);

namespace Adobe\RewardAdjustments\Observer;

use Magento\Framework\Event\ObserverInterface;
use Magento\Framework\Event\Observer;
use Magento\Quote\Model\Quote;
use Magento\Sales\Api\Data\OrderInterface;

class SetOrderRewardFlag implements ObserverInterface
{
    /**
     * @param Observer $observer
     * @return void
     */
    public function execute(Observer $observer)
    {
        $event = $observer->getEvent();
        /* @var $order OrderInterface */
        $order = $event->getOrder();
        /** @var $quote Quote $quote */
        $quote = $event->getQuote();

        // do something to the order and/or quote object here
    }
}
```

#### 監視者が変更できるもの

オブザーバーは、Adobe Commerceプラットフォーム内の PHP コードにのみ適用されます。 変更できるのは、イベントディスパッチで渡される特定のデータとオブジェクトだけです。

#### 監視者を使用するタイミング

いつでも利用可能です。 監視者がより広く利用可能で柔軟な場合、監視者はこのリストの 2 番目の場所を取る。 オブザーバーは、プラグインよりも処理のオーバーヘッドが少なく、利用可能性が低く、柔軟性も低くなります。

#### 欠点

オブザーバーはコードを傍受および変更する優れた方法ですが、イベントのディスパッチをコアまたはサードパーティコードに追加して、コードがリッスンできるようにする必要があります。 これにより、オブザーバーの使用の概念が少し制限されます。 開発者がコードに含めるべき先見のあるイベントに限られます。

また、オブザーバーのもう 1 つの制限要因は、ディスパッチイベントが、開発者がイベントと共に通過すると決めた特定のデータおよびオブジェクトへのアクセスを提供するだけである点です。

### プラグイン

プラグインは、Adobe Commerceプラットフォームで導入された柔軟な概念です。 これにより、パブリック PHP メソッドを切り取り、置換、および変更できます。 プラグインを使用すると、ターゲットメソッドが実行される前にメソッド内の引数を変更したり、ターゲットメソッドが実行された後に結果を変更したり、ターゲットメソッドを完全に置き換えたりできます。 対象となる PHP クラスの多くのメソッドは、1 つのプラグインファイル内で変更できます。 また、 `$subject` 対象の PHP クラスに存在するパブリックメソッドを実行する引数。

#### プラグインの宣言方法

プラグインは、グローバルまたは領域固有の `di.xml` ファイル。

```xml
    <type name="Magento\Catalog\Api\CategoryRepositoryInterface">
        <plugin name="Adobe\CatalogAdjustments\Plugin\CategoryRepositoryPlugin" type="Adobe\CatalogAdjustments\Plugin\CategoryRepositoryPlugin"/>
    </type>
```

```php
<?php

declare(strict_types=1);

namespace Adobe\CatalogAdjustments\Plugin;

class CategoryRepositoryPlugin
{
    /**
     * @param \Magento\Catalog\Api\CategoryRepositoryInterface $subject
     * @param int $categoryId
     * @param int $storeId
     *
     * @return array
     */
    public function beforeGet($subject, $categoryId, $storeId = null): array
    {
        // modify the $categoryId or $storeId arguments or perform some other functionality prior to execution of the `get` method
        return [$categoryId, $storeId];
    }

    /**
     * @param \Magento\Catalog\Api\CategoryRepositoryInterface $subject
     * @param \Closure $origMethod
     * @param int $categoryId
     * @param int $storeId
     *
     * @return \Magento\Catalog\Api\Data\CategoryInterface
     */
    public function aroundGet($subject, $origMethod, $categoryId, $storeId = null): \Magento\Catalog\Api\Data\CategoryInterface
    {
        // here you can do something before calling the original method
        $result = $origMethod($categoryId, $storeId);
        // here you can do something after calling the original method
        // you can also NOT call the original method at all and instead, substitute our own functionality

        return $result;
    }

    /**
     * @param \Magento\Catalog\Api\CategoryRepositoryInterface $subject
     * @param \Magento\Catalog\Api\Data\CategoryInterface $result
     * @param int $categoryId
     * @param int $storeId
     *
     * @return \Magento\Catalog\Api\Data\CategoryInterface
     */
    public function afterGet($subject, $result, $categoryId, $storeId = null): \Magento\Catalog\Api\Data\CategoryInterface
    {
        // here you modify the result produced by the original `get` function or you can execute some other functionality
        // note that you also have access to the original function arguments. it's too late to modify them, but if needed, they are available for reading

        return $result;
    }
}
```

#### プラグインで変更できるもの

この機能は、PHP クラスを対象とする場合にのみ使用できます。 パブリックメソッドの入力または出力を変更し、プラグインを使用して他の機能をトリガーできます。 複数のプラグインが同じ PHP クラスをターゲットにする場合、プラグインの実行の並べ替え順を設定して、他のプラグインの前後にプラグインを実行できるようにすることができます。

#### プラグインを使用するタイミング

依存関係の置換が使用できない場合は常に使用します。 プラグインは、コアコードベースやサードパーティコード全体で一般的に使用され、独自のカスタムコードで一般的に使用できます。 通常、カスタムコードが所有または制御していない機能を変更する必要がある場合は、プラグインを使用します。

#### 欠点

保護されたメソッドまたはプロパティを変更できません。 処理オーバーヘッドは、監視者の処理オーバーヘッドよりも高い。 プラグインを使わないという議論ではなく、違いは些細なものです。 しかし、これは心に留めておくべき良いことです。

### 依存関係の置換

依存関係インジェクションは、必要な依存関係をコンストラクタを使用してクラスに渡す、標準のオブジェクト指向のコーディング概念です。 ただし、Adobe Commerceプラットフォームでは、依存関係を XML に置き換える複数の手段を提供することで、この手順をさらに進めています。 基本的に、依存関係の置き換えです。 依存関係の置き換えはあらゆる状況に適していませんが、最小限のコード書き込みと低いオーバーヘッドが可能で、狭い範囲で正確なコードのみをターゲットにできます。 依存関係の置き換えを使用して、プライベートおよび保護されたメソッドを変更できます。

#### 依存関係の置き換えの使用方法

依存関係の置き換えは、グローバルベースまたは領域固有のベースで行うことができます。

```php
<?php

class SomeClass
{
    public function __construct(
        private readonly AllowedCountries $allowedCountriesReader
    ) {}

    /**
     * Check is address allowed for store
     *
     * @param AddressInterface $address
     * @param int|null $storeId
     * @return bool
     */
    private function isAddressAllowedForWebsite(AddressInterface $address, $storeId): bool
    {
        $allowedCountries = $this->allowedCountriesReader->getAllowedCountries(ScopeInterface::SCOPE_STORE, $storeId);

        return in_array($address->getCountryId(), $allowedCountries);
    }
}
```

```php
<?php

use Magento\Store\Model\ScopeInterface;

class OverrideAllowedCountries extends AllowedCountries
{
    /**
     * Retrieve all allowed countries for scope or scopes
     *
     * @param string $scope
     * @param string|null $scopeCode
     * @return array
     * @since 100.1.2
     */
    public function getAllowedCountries(
        $scope = ScopeInterface::SCOPE_WEBSITE,
        $scopeCode = null
    ) {
        // do some stuff here
        // you can call the original method or override it completely
        
        return $something;
    }
}
```

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <type name="Vendor\Namespace\SomeClass">
        <arguments>
            <argument name="allowedCountriesReader" xsi:type="object">OverrideAllowedCountries</argument>
        </arguments>
    </type>
</config>
```

これらの手順に従った後、プライベートメソッドの動作が正常に変更されました。

#### 依存関係の置き換えで変更できるもの

パブリック、保護、プライベートの各メソッドは、依存関係の置き換えを使用して変更できます。 プラグインと同様に、引数の変更、関数の完全な置き換え、関数の出力の変更が可能です。

#### 依存関係の置き換えを使用するタイミング

実装に複雑すぎる作業は何も必要ないので、実際に目的の目標を達成する場合は、これが最初の方法として適しています。

#### 欠点

多くはありません。 どの状況でも使えるわけではありません 主な欠点は、変更する機能を含む元のクラスを拡張する必要がある点です。 これは「継承を越えた構成」の原則に反する。
