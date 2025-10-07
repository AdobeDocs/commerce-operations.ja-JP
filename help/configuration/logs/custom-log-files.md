---
title: カスタムログファイルへの書き込み
description: Adobe Commerceでカスタムログファイルを作成および設定する方法について説明します。 ロガーハンドラーとカスタムログの実装について説明します。
feature: Configuration, Logs
badge: label="寄稿：Atwix" type="Informative" url="https://www.atwix.com/" tooltip="Atwix"
exl-id: 875f45e7-30c9-4b1b-afe9-d1a8d51ccdf0
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# カスタムログファイルへの書き込み

`Magento\Framework\Logger` モジュールには、次のハンドラークラスが含まれています。

| クラス | ログファイル |
| ----- | -------- |
| [Magento\Framework\Logger\Handler\Base][base] | - |
| [Magento\Framework\Logger\Handler\Debug][debug] | `/var/log/debug.log` |
| [Magento\Framework\Logger\Handler\Exception][exception] | `/var/log/exception.log` |
| [Magento\Framework\Logger\Handler\Syslog][syslog] | - |
| [Magento\Framework\Logger\Handler\System][system] | `/var/log/system.log` |

これらは `lib/internal/Magento/Framework/Logger/Handler` ディレクトリにある場合があります。

カスタムファイルへのログインには、次のいずれかの方法を使用できます。

- `di.xml` でのカスタムログファイルの設定
- カスタムロガーハンドラークラスのカスタムファイルを設定します。

## `di.xml` でのカスタムログファイルの設定

この例では、[ 仮想型 ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) を使用して、標準の `debug` ではなくカスタムログファイルにメッセージ `/var/log/debug.log` ログする方法を示します。

1. モジュールの `di.xml` ファイルで、カスタムログファイルを [ 仮想タイプ ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) として定義します。

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomDebug" type="Magento\Framework\Logger\Handler\Base">
       <arguments>
           <argument name="fileName" xsi:type="string">/var/log/payment.log</argument>
        </arguments>
   </virtualType>
   ```

   `name` の `Magento\Payment\Model\Method\MyCustomDebug` 値は一意である必要があります。

1. 一意の [ を使用して、別の ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) 仮想タイプ `name` でハンドラーを定義します。

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
           </argument>
       </arguments>
   </virtualType>
   ```

1. `MyCustomLogger` オブジェクトに [ ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) 仮想型 `Magento\Payment\Model\Method\Logger` を挿入します。

   ```xml
   <type name="Magento\Payment\Model\Method\Logger">
       <arguments>
           <argument name="logger" xsi:type="object">Magento\Payment\Model\Method\MyCustomLogger</argument>
       </arguments>
   </type>
   ```

1. 仮想クラス `Magento\Payment\Model\Method\MyCustomDebug` は、`debug` クラスの `$logger` プロパティの `Magento\Payment\Model\Method\Logger` ハンドラーに挿入されます。

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
   </argument>
   ```

例外メッセージは、`/var/log/payment.log` ファイルに記録されます。

## ロガーハンドラークラスのカスタムログファイルを設定します。

この例では、カスタムのロガーハンドラークラスを使用して、メッセージを特定 `error` ログファイルに記録する方法を示します。

1. データを記録するクラスを作成します。 この例では、クラスは `app/code/Vendor/ModuleName/Logger/Handler/ErrorHandler.php` で定義されています。

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

1. モジュールの [ ファイルで、このクラスのハンドラーを ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) 仮想型 `di.xml` として定義します。

   ```xml
   <virtualType name="MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="error" xsi:type="object">Vendor\ModuleName\Logger\Handler\ErrorHandler</item>
           </argument>
       </arguments>
   </virtualType>
   ```

   `MyCustomLogger` は一意の ID です。

1. `type` 定義で、カスタムロガーハンドラーが挿入されるクラス名を指定します。 このタイプの引数として、前の手順で指定した仮想タイプ名を使用します。

   ```xml
   <type name="Vendor\ModuleName\Observer\MyObserver">
       <arguments>
           <argument name="logger" xsi:type="object">MyCustomLogger</argument>
       </arguments>
   </type>
   ```

   クラスのSource コ `Vendor\ModuleName\Observer\MyObserver` ド：

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

1. クラス `Vendor\ModuleName\Logger\Handler\ErrorHandler` は、`error` の `$logger` プロパティの `Vendor\ModuleName\Observer\MyObserver` ハンドラーに挿入されます。

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="error" xsi:type="object">Vendor\ModuleName\Logger\Handler\ErrorHandler</item>
   </argument>
   ...
   ```

例外メッセージは、`/var/log/my_custom_logger/error.log` ファイルに記録されます。

<!-- link definitions -->

[base]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Base.php
[debug]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Debug.php
[exception]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Exception.php
[syslog]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Syslog.php
[system]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/System.php
