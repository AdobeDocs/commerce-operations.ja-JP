---
title: カスタムログファイルに書き込む
description: カスタムログファイルの設定について説明します。
badge: label="Contributed by Atwix" type="Informative" url="https://www.atwix.com/" tooltip="Atwix"
source-git-commit: d7f32690b25c61fa31a99e6d02f9f1025de2bb99
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---


# カスタムログファイルに書き込む

この `Magento\Framework\Logger` モジュールには、次のハンドラークラスが含まれます。

| クラス | ログファイル |
| ----- | -------- |
| [Magento\Framework\Logger\Handler\Base][base] | - |
| [Magento\Framework\Logger\Handler\Debug][debug] | `/var/log/debug.log` |
| [Magento\Framework\Logger\Handler\Exception][exception] | `/var/log/exception.log` |
| [Magento\Framework\Logger\Handler\Syslog][syslog] | - |
| [Magento\Framework\Logger\Handler\System][system] | `/var/log/system.log` |

これらは、 `lib/internal/Magento/Framework/Logger/Handler` ディレクトリ。

カスタムファイルへのログインには、次のいずれかの方法を使用できます。

- カスタムログファイルを `di.xml`
- カスタムロガーハンドラークラスでのカスタムファイルの設定

## カスタムログファイルを `di.xml`

この例では、 [仮想タイプ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) ログに記録する `debug` 標準のログファイルではなくカスタムログファイルにメッセージを書き込む `/var/log/debug.log`.

1. 内 `di.xml` モジュールのファイル、カスタムログファイルを [仮想タイプ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types).

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomDebug" type="Magento\Framework\Logger\Handler\Base">
       <arguments>
           <argument name="fileName" xsi:type="string">/var/log/payment.log</argument>
        </arguments>
   </virtualType>
   ```

   この `name` 値 `Magento\Payment\Model\Method\MyCustomDebug` は一意である必要があります。

1. 別のハンドラーでハンドラーを定義する [仮想タイプ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) ユニークな `name`:

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
           </argument>
       </arguments>
   </virtualType>
   ```

1. を挿入 `MyCustomLogger` [仮想タイプ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) 内 `Magento\Payment\Model\Method\Logger` オブジェクト：

   ```xml
   <type name="Magento\Payment\Model\Method\Logger">
       <arguments>
           <argument name="logger" xsi:type="object">Magento\Payment\Model\Method\MyCustomLogger</argument>
       </arguments>
   </type>
   ```

1. 仮想クラス `Magento\Payment\Model\Method\MyCustomDebug` が `debug` のハンドラー `$logger` プロパティを `Magento\Payment\Model\Method\Logger` クラス。

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
   </argument>
   ```

例外メッセージは、 `/var/log/payment.log` ファイル。

## ロガーハンドラークラスでのカスタムログファイルの設定

この例では、カスタムロガーハンドラークラスを使用してログを記録する方法を示します `error` メッセージを特定のログファイルに書き込みます。

1. データを記録するクラスを作成します。 この例では、クラスは `app/code/Vendor/ModuleName/Logger/Handler/ErrorHandler.php`.

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

1. このクラスのハンドラーを [仮想タイプ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) モジュールの `di.xml` ファイル。

   ```xml
   <virtualType name="MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="error" xsi:type="object">Vendor\ModuleName\Logger\Handler\ErrorHandler</item>
           </argument>
       </arguments>
   </virtualType>
   ```

   `MyCustomLogger` は一意の識別子です。

1. 内 `type` 定義では、カスタムロガーハンドラーが挿入されるクラス名を指定します。 前の手順で作成した仮想型名を、この型の引数として使用します。

   ```xml
   <type name="Vendor\ModuleName\Observer\MyObserver">
       <arguments>
           <argument name="logger" xsi:type="object">MyCustomLogger</argument>
       </arguments>
   </type>
   ```

   のソースコード `Vendor\ModuleName\Observer\MyObserver` クラス：

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

1. クラス `Vendor\ModuleName\Logger\Handler\ErrorHandler` が `error` のハンドラー `$logger` プロパティを `Vendor\ModuleName\Observer\MyObserver`.

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="error" xsi:type="object">Vendor\ModuleName\Logger\Handler\ErrorHandler</item>
   </argument>
   ...
   ```

例外メッセージは、 `/var/log/my_custom_logger/error.log` ファイル。

<!-- link definitions -->

[base]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Base.php
[debug]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Debug.php
[exception]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Exception.php
[syslog]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Syslog.php
[system]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/System.php
