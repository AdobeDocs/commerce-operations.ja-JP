---
title: カスタムログファイルへの書き込み
description: Adobe Commerceでカスタムログファイルを作成および設定する方法について説明します。 ロガーハンドラーとカスタムロギング実装の詳細。
feature: Configuration, Logs
badge: label="Atwixによる投稿" type="Informative" url="https://www.atwix.com/" tooltip="Atwix"
exl-id: 875f45e7-30c9-4b1b-afe9-d1a8d51ccdf0
source-git-commit: b378f6da50e40b1868ae759cc7f3523a7e3ced4b
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# カスタムログファイルへの書き込み

`Magento\Framework\Logger` モジュールには、次のハンドラークラスが含まれています。

| クラス | ログファイル |
| ----- | -------- |
| [Magento\Framework\Logger\Handler\Base](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Base.php) | - |
| [Magento\Framework\Logger\Handler\Debug](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Debug.php) | `/var/log/debug.log` |
| [Magento\Framework\Logger\Handler\Exception](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Exception.php) | `/var/log/exception.log` |
| [Magento\Framework\Logger\Handler\Syslog](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Syslog.php) | - |
| [Magento\Framework\Logger\Handler\System](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/System.php) | `/var/log/system.log` |

`lib/internal/Magento/Framework/Logger/Handler` ディレクトリに表示されます。

カスタムファイルにログインするには、次のいずれかの方法を使用できます。

- `di.xml`でカスタム ログ ファイルを設定する
- カスタムロガーハンドラークラスでのカスタムファイルの設定

## `di.xml`でカスタム ログ ファイルを設定する

この例では、[仮想タイプ ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file#virtual-types)を使用して、`debug`件のメッセージを標準`/var/log/debug.log`ではなくカスタムログファイルに記録する方法を示します。

1. モジュールの`di.xml` ファイルで、カスタムログファイルを[仮想タイプ ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file#virtual-types)として定義します。

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomDebug" type="Magento\Framework\Logger\Handler\Base">
       <arguments>
           <argument name="fileName" xsi:type="string">/var/log/payment.log</argument>
        </arguments>
   </virtualType>
   ```

   `Magento\Payment\Model\Method\MyCustomDebug`の`name`値は一意である必要があります。

1. 一意の`name`を持つ別の[仮想タイプ ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file#virtual-types)でハンドラーを定義します。

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
           </argument>
       </arguments>
   </virtualType>
   ```

1. `Magento\Payment\Model\Method\Logger` オブジェクトに`MyCustomLogger` [仮想タイプ ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file#virtual-types)を挿入します。

   ```xml
   <type name="Magento\Payment\Model\Method\Logger">
       <arguments>
           <argument name="logger" xsi:type="object">Magento\Payment\Model\Method\MyCustomLogger</argument>
       </arguments>
   </type>
   ```

1. 仮想クラス `Magento\Payment\Model\Method\MyCustomDebug`は、`Magento\Payment\Model\Method\Logger` クラスの`$logger` プロパティの`debug` ハンドラーに挿入されます。

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
   </argument>
   ```

例外メッセージは`/var/log/payment.log` ファイルに記録されます。

## ロガーハンドラークラスでのカスタムログファイルの設定

この例では、カスタムロガーハンドラークラスを使用して、`error` メッセージを特定のログファイルに記録する方法を示します。

1. データをログに記録するクラスを作成します。 この例では、クラスは`app/code/Vendor/ModuleName/Logger/Handler/ErrorHandler.php`で定義されています。

   ```php
   <?php
   /**
    * @author Vendor
    * @copyright Copyright (c) 2019 Vendor (https://www.vendor.com/)
    */
   namespace Vendor\ModuleName\Logger\Handler;
   
   use Magento\Framework\Logger\Handler\Base as BaseHandler;
   use Monolog\Logger as MonologLogger;
   
   /**
    * Class ErrorHandler
    */
   class ErrorHandler extends BaseHandler
   {
       /**
        * Logging level
        *
        * @var int
        */
       protected $loggerType = MonologLogger::ERROR;
   
       /**
        * File name
        *
        * @var string
        */
       protected $fileName = '/var/log/my_custom_logger/error.log';
   }
   ```

1. このクラスのハンドラーを、モジュールの`di.xml` ファイルの[仮想タイプ ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file#virtual-types)として定義します。

   ```xml
   <virtualType name="MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="error" xsi:type="object">Vendor\ModuleName\Logger\Handler\ErrorHandler</item>
           </argument>
       </arguments>
   </virtualType>
   ```

   `MyCustomLogger`は一意のIDです。

1. `type`定義で、カスタムロガーハンドラーを挿入するクラス名を指定します。 前の手順の仮想タイプ名をこのタイプの引数として使用します。

   ```xml
   <type name="Vendor\ModuleName\Observer\MyObserver">
       <arguments>
           <argument name="logger" xsi:type="object">MyCustomLogger</argument>
       </arguments>
   </type>
   ```

   `Vendor\ModuleName\Observer\MyObserver` クラスのSource コード：

   ```php
   <?php
   /**
    * @author Vendor
    * @copyright Copyright (c) 2019 Vendor (https://www.vendor.com/)
    */
   declare(strict_types=1);
   
   namespace Vendor\ModuleName\Observer;
   
   use Psr\Log\LoggerInterface as PsrLoggerInterface;
   use Exception;
   use Magento\Framework\Event\ObserverInterface;
   use Magento\Framework\Event\Observer;
   
   /**
    * Class MyObserver
    */
   class MyObserver implements ObserverInterface
   {
       /**
        * @var PsrLoggerInterface
        */
       private $logger;
   
       /**
        * MyObserver constructor.
        *
        * @param PsrLoggerInterface $logger
        */
       public function __construct(
           PsrLoggerInterface $logger
       ) {
           $this->logger = $logger;
       }
   
       /**
        * @param Observer $observer
        */
       public function execute(Observer $observer)
       {
           try {
               // some code goes here
           } catch (Exception $e) {
               $this->logger->error($e->getMessage());
           }
       }
   }
   ```

1. クラス `Vendor\ModuleName\Logger\Handler\ErrorHandler`は、`Vendor\ModuleName\Observer\MyObserver`の`$logger` プロパティの`error` ハンドラーに挿入されます。

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="error" xsi:type="object">Vendor\ModuleName\Logger\Handler\ErrorHandler</item>
   </argument>
   ...
   ```

例外メッセージは`/var/log/my_custom_logger/error.log` ファイルに記録されます。

