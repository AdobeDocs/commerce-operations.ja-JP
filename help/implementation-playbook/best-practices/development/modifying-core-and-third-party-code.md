---
title: コアおよびサードパーティの PHP コードを変更する際のベストプラクティス
description: コアのAdobe Commerceとサードパーティの PHP コードを変更する方法とタイミングについて説明します。
role: Developer, Architect
feature: Best Practices
last-substantial-update: 2023-12-8
exl-id: 32b3137d-fc00-4be8-ba02-5d8d48a51fe1
source-git-commit: d47567a8d69ccdae3db01e964f1db12e8ae26717
workflow-type: tm+mt
source-wordcount: '1747'
ht-degree: 0%

---

# コアおよびサードパーティの PHP コードの変更または上書きに関するベストプラクティス

このドキュメントでは、作成しなかったコードや直接制御しなかったコードの機能、結果、入力を変更する必要が生じた場合のベストプラクティスについて説明します。 つまり、コアコードとサードパーティコードです。 このドキュメントでは、主にバックエンドの PHP コードに焦点を当てています。

## コードの変更方法

コードを変更する場合は、変更の範囲を考慮することが重要です。 変更の「範囲」は、コードの変更の影響がどの程度大きいかを表します。 ベストプラクティスとして、最終的な実装を完了する方法の決定は、最小のフットプリントと最小のリソース使用量を持つオプションに基づいて行います。 コードのオーバーライドが広範囲に及ぶほど、開発チームがAdobe Commerceのコア機能から逸脱し、バグが発生する可能性が高まり、将来コードベースを維持する取り組みが増します。

### パッチ

パッチは、開発チームの直接管理下にないファイル内でコードを直接変更する手順が含まれるファイルです。 これは、他のオプションが存在しない場合に、通常は最後の手段と見なす必要があるオプションです。 パッチは一時的な解決策を意図しています。 一般的なベストプラクティスとしてパッチを作成する必要がある場合は、そのパッチを削除し、2～4 週間以内により永続的なソリューションを使用するようにします。 

斑点は容易に破れます。 パッチターゲットの対象となるファイルが更新されると、多くの場合、パッチが機能しなくなります。 これは、パッチファイルには、パッチによって変更される内容を明確に示す行番号と列番号が含まれているからです。 何かがパッチが期待していたものと一致しない場合、パッチは適用を停止し、コードを壊します。

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

#### パッチで変更できるもの

何でも。 文字通り、ターゲットファイル内の任意の文字を変更できます。 パッチは、特定のファイルタイプやコード言語に限定されません。 通常は、内のファイルをターゲットにするにはパッチを使用します `vendor` ディレクトリ。 

#### パッチを使用するタイミング

他のオプションが存在しないことに気付いた場合。 例えば、ベンダーがまだコードの修正を公開していない場合は、恒久的なソリューションを待つ間にパッチを使用して、問題に一時的に対処できます。

#### 欠点

斑点は容易に破れます。 ターゲットコードが変更されると、パッチは機能しなくなります。 短期的なソリューションのみを目的としています。

### 環境設定

環境設定とは、Adobe Commerceのプラットフォームに組み込まれた概念です。 これは基本的に「PHP クラスの置き換え」です。

Adobe Commerceのプラットフォームは、PHP クラスをインスタンス化するために「オブジェクトマネージャ」を使用します。これは、従来の PHP アプリケーションのように、新しいキーワードを使用して PHP クラスをインスタンス化しないためです。 代わりに、オブジェクトマネージャは、コンパイルされた設定に対してインスタンス化される PHP クラスの名前を相互参照し、元のクラスに対して環境設定を宣言したモジュールがあるかどうかを判断します。 PHP クラスの環境設定が見つかった場合、オブジェクトマネージャは指定されたクラスを代わりにインスタンス化します。

元の PHP クラスに置き換わる新しい PHP クラスは、元の PHP クラスから拡張または継承されることに注意してください。 これは、次のようないくつかの理由で行われます。

- 依存関係のインジェクション/タイプヒントが遵守されていることを確実にする。 そうしないと、致命的なエラーが発生し、アプリケーションが中断します。
- 最小限のコード書き込みを可能にする。 元の PHP クラスに 10 個のメソッドが含まれているが、1 個のメソッドをオーバーライドするだけの場合、通常は 1 個のメソッドだけを変更して、他の 9 個のメソッドはそのままにしておくことができます。 これは、プラットフォームが新しいバージョンにアップグレードされる際に、コア機能の更新をブロックしないようにするために重要です。

#### 環境設定を宣言

環境設定を宣言するのはかなり簡単なプロセスです。 に 1 行のコードを追加する必要があります。 `di.xml` モジュール内のファイル。 これは、グローバルに行うことも、Adobe Commerceの「エリア」内で行うこともできます。例えば、次のようなものがあります `frontend`, `adminhtml`, `graphql`, `webapi_rest`、および `crontab`.

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

#### 環境設定で変更できる内容

環境設定でオーバーライドできるのは、PHP クラスのみです。 PHP クラス内では、public および protected メソッドとプロパティを変更できます。 public および protected メソッドの場合、メソッドを完全にオーバーライドするか、元の親メソッドに渡される（または元の親メソッドから渡される）引数を変更することができます。

プライベートメソッドは、技術的にオーバーライドできません。 ただし、元のプライベートメソッドに代わる独自のメソッドを作成できます。 任意の名前を付けることもできます。元の名前を使用することもできます。 プライベートメソッドは、プライベートメソッドを含む実際のファイル内にのみ存在するので、問題ではありません。 プライベートメソッドを上書きするには、元のプライベートメソッドを呼び出すパブリックメソッドまたは protected メソッドを上書きまたは変更し、独自の機能を代わりに使用する必要があります。

#### 環境設定を使用するタイミング

もう一度、他のオプションが存在しない場合や、依存関係の挿入、プラグインまたはオブザーバーで目標を達成できない場合は、環境設定を使用する必要があります。 非公開または保護されたメソッドやプロパティを変更または上書きする必要がある場合は、環境設定が必要になることがあります。 環境設定は控えめに使用する必要があります。 アプリケーションを変更する方法として、かなり「貪欲」な方法で、PHP クラスの所有権を実質的に取得します。 これにより、サードパーティモジュールとの競合が発生し、コアクラスの更新がブロックされて、診断が困難なバグにつながる可能性があります。 Adobe Commerceのプラットフォームは、他の手段を取り入れるように設計されており、基盤となるコードに対する変更を、より小さなフットプリントで行うことができます。

#### 欠点

環境設定は、コードを変更するための貪欲な方法で、他のオプションが存在しない場合にのみ使用する必要があります。 環境設定は、多くの場合、コードベース内の競合を引き起こし、さらに悪い場合には、プラットフォームのアップグレードで発生するコアアップデートをブロックできます。 

### 監視者

オブザーバーとは、多くのアプリケーション、プラットフォーム、ライブラリ、コーディング言語で見られる、イベントリスナーの概念です。 この概念は、Adobe Commerceのプラットフォームに固有のものではありません。 オブザーバーはMagento1 の時代からプラットフォームに取り込まれており、コアコードとサードパーティコードの変更方法の主な選択肢と見なされています。 

コアコードベースとサードパーティモジュールは、コード内の選択された場所にイベントをディスパッチできます。 オブザーバー（ `events.xml` ディスパッチされたイベントを名前でリッスンしているファイルであり、グローバルレベルで機能できるか、Adobe Commerceの「領域」に制限されている可能性があります。以下に例を示します。 `frontend`, `adminhtml`, `graphql`, `webapi_rest`、および `crontab`.

#### オブザーバーの宣言方法

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

#### オブザーバーで変更できるもの

監視者は、Adobe Commerce プラットフォーム内の PHP コードにのみ適用されます。 変更できるのは、イベント ディスパッチで渡される特定のデータおよびオブジェクトのみです。

#### オブザーバーを使用するタイミング

いつでも可能です。 監視者がより幅広く利用でき、柔軟性が高ければ、監視者はこのリストの第 2 位を取ることになります。 監視者は、プラグインよりも処理オーバーヘッドが少なく、利用しやすく、柔軟性に欠けます。

#### 欠点

オブザーバーはコードをインターセプトして変更する優れた方法ですが、コードがリッスンできるように、イベントのディスパッチをコアコードまたはサードパーティコードに追加する必要があります。 このため、オブザーバーの使用の概念は少し制限されます。 開発者がコードに含める見通しのあるイベントに制限されます。

また、オブザーバーのもう 1 つの制限要因は、ディスパッチされたイベントが、開発者がイベントと共に渡すことにした特定のデータとオブジェクトへのアクセスのみを提供することです。

### プラグイン

プラグインは、Adobe Commerce Platform で導入された柔軟な概念です。 これにより、パブリックな PHP メソッドをインターセプト、置換、変更することができます。 プラグインを使用すると、ターゲットメソッドが実行される前にメソッドに渡される引数を変更したり、ターゲットメソッドが実行された後に結果を変更したり、ターゲットメソッドを完全に置き換えたりできます。 1 つのプラグインファイル内で、ターゲットの PHP クラスの多くのメソッドを変更できます。 また、 `$subject` 対象の PHP クラスに存在するパブリックメソッドを実行するための引数。

#### プラグインの宣言方法

プラグインは、グローバルまたは領域固有で設定できます `di.xml` ファイル。

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

この機能は、PHP クラスのみを対象として使用できます。 公開メソッドの入力または出力を変更したり、プラグインを使用して他の機能をトリガーしたりできます。 複数のプラグインが同じ PHP クラスをターゲットとする場合、プラグインの実行の並べ替え順を設定して、他のプラグインの前後でプラグインを実行できます。

#### プラグインを使用するタイミング

依存関係の置き換えが利用できない場合。 プラグインは、コアコードベース全体、サードパーティコード全体で一般的に使用され、独自のカスタムコードで一般的に使用できます。 通常、カスタムコードが所有または制御していない機能を変更する必要がある場合は、プラグインが有効です。

#### 欠点

保護されたメソッドまたはプロパティは変更できません。 処理オーバーヘッドは、監視者の処理オーバーヘッドよりも大きい。 プラグインを使用しないという議論ではありません。違いはごくわずかです。 しかし、これは覚えておいてよいでしょう。

### 依存関係の置換

依存関係の挿入は、必要な依存関係をコンストラクターでクラスに渡す、標準のオブジェクト指向コーディング概念です。 ただし、Adobe Commerce プラットフォームでは、依存関係を XML で置き換える方法を複数提供することで、さらに一歩進んでいます。 基本的には、依存関係の置き換えです。 依存関係の置き換えはすべての状況に適しているわけではありませんが、最小限のコード記述、低いオーバーヘッド、厳密なコード部分のみをターゲットにすることができます。 プライベートメソッドや保護されたメソッドは、依存関係の置き換えを使用して変更できます。

#### 依存関係の置換の使用方法

依存関係の置き換えは、グローバルベースまたはエリア固有ベースで実行できます。

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

これらの手順を行うと、プライベートメソッドの動作が正常に変更されます。

#### 依存関係の置換で変更できる内容

public、protected、および private メソッドは、依存関係の置き換えを使用して変更できます。 プラグインと同様に、引数を変更したり、関数を完全に置き換えたり、関数の出力を変更したりできます。

#### 依存関係の置換を使用するタイミング

これは、複雑すぎて実装する必要がないことを前提として、実際に目的の目標を達成する場合の最初のオプションとして適しています。

#### 欠点

多くはない。 全ての場面で使えるわけではない。 主な欠点は、変更する機能を含む元のクラスを拡張する必要があることです。 これは「相続に対する構図」の原則に反する。
