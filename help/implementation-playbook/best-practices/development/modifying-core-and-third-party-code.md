---
title: コアおよびサードパーティのPHP コードを修正するためのベストプラクティス
description: コアのAdobe CommerceとサードパーティのPHP コードを変更する方法とタイミングについて説明します。
role: Developer
feature: Best Practices
last-substantial-update: 2023-12-8
exl-id: 32b3137d-fc00-4be8-ba02-5d8d48a51fe1
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '1747'
ht-degree: 0%

---

# コアおよびサードパーティのPHP コードを変更または上書きするためのベストプラクティス

このドキュメントでは、オーサリングを行っていない、または直接コントロールしていないコードの機能、結果、または入力を変更する必要が生じた場合のベストプラクティスについて説明します。 言い換えれば、コアコードとサードパーティコードです。 このドキュメントでは、主にバックエンド PHP コードに焦点を当てます。

## コードを修正する方法

コードを変更する場合は、変更の範囲を考慮することが重要です。 変更の「範囲」とは、コード変更の影響がどれほど広範囲に及んでいるかを指します。 ベストプラクティスとしては、フットプリントが最小でリソース使用量が最小のオプションに基づいて、最終的な実装の完了方法に関する決定を基にします。 コードのオーバーライドが広範囲に及ぶほど、開発チームがAdobe Commerceのコア機能から逸脱する可能性が高まり、バグの可能性が高まり、将来コードベースの保守に注力できるようになります。

### パッチ

パッチは、開発チームの直接の管理下にないファイル内でコードを直接変更する手順を含むファイルです。 これは、通常、他のオプションが存在しない場合に最後の手段として考慮すべきオプションです。 パッチは、一時的な解決策を目的としています。 パッチを作成する必要がある場合は、一般的なベストプラクティスとして、そのパッチを削除し、次の2～4週間以内に、より永続的な解決策を採用します。 

パッチが簡単に破損する。 パッチの対象となるファイルが更新されると、多くの場合、パッチの動作が停止します。 これは、パッチファイルに、パッチによって変更される内容を具体的に示す行番号と列番号が含まれているためです。 何かがパッチが期待していたものと一致しない場合は、適用を停止してコードを壊します。

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

何でも。 文字通り、対象ファイル内の任意の文字を変更できます。 パッチは、特定のファイルタイプやコード言語に限定されません。 通常は、パッチを使用して`vendor` ディレクトリ内のファイルをターゲットにします。 

#### パッチを使用するタイミング

他の選択肢がないことを認識している場合。 例えば、ベンダーがコードの修正をまだ公開していない場合、パッチを使用して、恒久的な解決策が出るのを待つ間、問題に一時的に対処することができます。

#### 欠点

パッチが簡単に破損する。 ターゲットとなるコードが変更されると、パッチは機能しなくなります。 これは短期的な解決策にすぎません。

### 環境設定

環境設定とは、Adobe Commerceの基盤に組み込まれたコンセプトです。 これは基本的に「PHP クラスの置換」です。

Adobe Commerce プラットフォームでは、「オブジェクトマネージャー」を使用してPHP クラスをインスタンス化します。これは、従来のPHP アプリケーションで行われていたように、新しいキーワードでPHP クラスをインスタンス化しないためです。 代わりに、オブジェクトマネージャーは、コンパイルされた設定に対してインスタンス化するPHP クラスの名前を相互参照し、任意のモジュールが元のクラスの環境設定を宣言しているかどうかを判断します。 PHP クラスの環境設定が見つかった場合は、代わりに指定されたクラスがオブジェクトマネージャーによってインスタンス化されます。

（通常）新しいPHP クラスは、元のPHP クラスを置き換えて、元のPHP クラスから拡張または継承します。 これは、次のような理由で行われます。

- 依存関係の注入/タイプヒントが準拠していることを確認します。 それ以外の場合は、致命的なエラーが発生し、アプリケーションが破損します。
- コーディング作業を最小限に抑えることができます。 元のPHP クラスに10個のメソッドが含まれているが、1つのメソッドをオーバーライドするだけなら、通常は1つのメソッドだけを変更して、他の9つのメソッドをそのままにしておくことができます。 これは、プラットフォームが新しいバージョンにアップグレードされたときに、コア機能の更新をブロックしていないことを確認するために重要です。

#### 環境設定を宣言

これは、プリファレンスを宣言するためのかなり簡単なプロセスです。 モジュール内の`di.xml` ファイルに1行のコードを追加する必要があります。 これはグローバルに、または`frontend`、`adminhtml`、`graphql`、`webapi_rest`、`crontab`などの任意のAdobe Commerce「エリア」内で実行できます。

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

#### 環境設定で変更できること

環境設定で上書きできるのはPHP クラスのみです。 PHP クラス内では、パブリックおよび保護されたメソッドとプロパティを変更できます。 パブリックメソッドと保護されたメソッドの場合は、メソッドを完全に上書きするか、元の親メソッドに入る（または出てくる結果）引数を変更できます。

プライベートメソッドは技術的に上書きできません。 ただし、元のプライベートメソッドの代わりに独自の置換を作成できます。 任意の名前を付けることも、元の名前を使用することもできます。 プライベートメソッドは、それを含む実際のファイル内にのみ存在するため、問題ありません。 プライベートメソッドを上書きするには、元のプライベートメソッドを呼び出すパブリックメソッドまたは保護されたメソッドを上書きまたは変更する必要があり、独自の機能をその代わりに置き換える必要があります。

#### 環境設定を使用するタイミング

繰り返しますが、他のオプションが存在せず、依存関係インジェクション、プラグイン、オブザーバーで目標を達成できない場合は、環境設定を使用する必要があります。 プライベートまたは保護されたメソッドやプロパティを変更または上書きする必要がある場合は、環境設定が必要になることがあります。 環境設定は控えめに使用する必要があることに注意してください。 これらは、アプリケーションを変更するかなり「欲張り」な方法であり、PHP クラスの所有権を効果的に取得します。 これにより、サードパーティのモジュールとの競合や、コアクラスの更新のブロック、診断が困難なバグにつながる可能性があります。 Adobe Commerceプラットフォームは、より小さなフットプリントで基礎となるコードを変更できる他の手段を含むように設計されています。

#### 欠点

環境設定はコードを変更するための欲張りの方法であり、他のオプションが存在しない場合にのみ使用する必要があります。 好みがコードベース内で競合する場合が多く、さらに悪いことに、プラットフォームのアップグレードで発生するコア更新をブロックする可能性があります。 

### 観察者

オブザーバーは、多くのアプリケーション、プラットフォーム、ライブラリ、コーディング言語で見られるように、イベントリスナーの概念です。 このコンセプトは、Adobe Commerceプラットフォームだけのものではありません。 オブザーバーは、Magento 1の時代からプラットフォームに組み込まれており、コアコードとサードパーティコードを変更する方法の主要な選択肢であると考えられています。 

コアコードベースとサードパーティモジュールは、コード内の選択した場所にイベントをディスパッチできます。 `events.xml` ファイルで宣言され、ディスパッチされたイベントを名前でリッスンしているオブザーバーは、グローバルレベルで作業するか、`frontend`、`adminhtml`、`graphql`、`webapi_rest`および`crontab`などのAdobe Commerceの「領域」に制限できます。

#### オブザーバーを宣言する方法

オブザーバーは、グローバルまたは領域固有の`events.xml` ファイルで設定できます。

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

#### 観察者と何を変えるか

オブザーバーは、Adobe Commerce プラットフォーム内のPHP コードにのみ適用されます。 イベントのディスパッチで渡される特定のデータとオブジェクトのみを変更できます。

#### オブザーバーの使用例

アクセス可能な場合はいつでも！ もしも観測者がより広く利用可能で柔軟ならば、観測者はこのリストの第2位の位置を取るだろう。 オブザーバーは、プラグインよりも処理上のオーバーヘッドが少なく、利用が困難で柔軟性が低くなります。

#### 欠点

オブザーバーはコードを傍受して変更するための優れた方法ですが、イベントのディスパッチをコアまたはサードパーティのコードに追加して、コードをリッスンできるようにする必要があります。 そのため、観察者を使う考え方は少し限定されています。 開発者がコードに含める先見性を持つイベントに限定されます。

また、オブザーバーの別の制限要因は、ディスパッチされたイベントが、開発者がイベントと一緒に渡すことを決定した特定のデータとオブジェクトへのアクセスのみを提供することです。

### プラグイン

プラグインは、Adobe Commerce プラットフォームに導入された柔軟なコンセプトです。 これにより、パブリック PHP メソッドをインターセプト、置換、変更できます。 プラグインを使用すると、ターゲットメソッドを実行する前にメソッドに入る引数を変更したり、ターゲットメソッドを実行した後に結果を変更したり、ターゲットメソッドを完全に置き換えたりできます。 1つのプラグインファイル内で、ターゲットとなるPHP クラスの多くのメソッドを変更できます。 また、`$subject`引数を使用して、対象のPHP クラスに存在する任意のパブリックメソッドを実行することもできます。

#### プラグインを宣言する方法

プラグインは、グローバルまたは地域固有の`di.xml` ファイルで設定できます。

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

この機能は、ターゲット PHP クラスでのみ使用できます。 パブリックメソッドの入力または出力を変更したり、プラグインを使用して他の機能をトリガーしたりできます。 複数のプラグインが同じPHP クラスをターゲットにしている場合、プラグインの実行のソート順序を設定して、プラグインを他のプラグインの前または後に実行できるようにすることができます。

#### プラグインを使用するタイミング

依存関係の置き換えが使用できない場合。 プラグインは、コアコードベース、サードパーティコード全体で一般的に使用され、独自のカスタムコードで一般的に使用できます。 通常、カスタムコードが所有または制御していない機能を変更する必要がある場合は、プラグインが最適な方法です。

#### 欠点

保護されたメソッドまたはプロパティを変更できません。 処理オーバーヘッドは観察者よりも高い。 それはプラグインを使用しない本当の引数ではありません、違いは些細です。 ただし、これは念頭に置いておくべきことです。

### 依存関係の置き換え

依存関係インジェクションは、必要な依存関係をコンストラクターを使用してクラスに渡す、標準的なオブジェクト指向コーディングの概念です。 しかし、Adobe Commerceの基盤は、XMLで依存関係を置き換える複数の手段を提供することで、さらに一歩進んでいます。 基本的には、依存関係の置き換え。 依存関係の置き換えはあらゆる状況に適しているわけではありませんが、コードの書き込みを最小限に抑え、オーバーヘッドを少なくでき、コードの正確な部分だけを絞り込んでターゲットにすることができます。 依存関係を置き換えて、プライベートおよび保護されたメソッドを変更できます。

#### 依存関係の置き換えの使用方法

依存関係の置換は、グローバルベースまたは地域固有に行うことができます。

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

これらの手順を実行すると、プライベートメソッドの動作が正常に変更されます。

#### 依存関係の置き換えで変更できるもの

Public メソッド、protected メソッド、private メソッドは、依存関係の置き換えによって変更できます。 プラグインと同様に、入ってくる引数を変更したり、関数を完全に置き換えたり、関数の出力を変更したりできます。

#### 依存関係の置き換えを使用する場合

これは、複雑すぎて実装する必要がないと仮定して、望ましい目標を実際に達成する優れた最初のオプションです。

#### 欠点

多くはないですね。 あらゆる状況で使用できるわけではありません。 主な欠点は、変更する機能を含む元のクラスを拡張する必要があることです。 それは「相続よりも構成」の原則に反する。
