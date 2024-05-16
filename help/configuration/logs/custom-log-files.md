---
title: カスタムログファイルへの書き込み
description: カスタムログファイルの設定方法について説明します。
feature: Configuration, Logs
badge: label="寄稿：Atwix" type="Informative" url="https://www.atwix.com/" tooltip="Atwix"
exl-id: 875f45e7-30c9-4b1b-afe9-d1a8d51ccdf0
source-git-commit: 991bd5fb34a2ffe61aa194ec46e2b04b4ce5b3e7
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# カスタムログファイルへの書き込み

この `Magento\Framework\Logger` モジュールには、次のハンドラークラスが含まれます。

| クラス | ログファイル |
| ----- | -------- |
| [Magento\Framework\Logger\Handler\Base][base] | - |
| [Magento\Framework\Logger\Handler\Debug][debug] | `/var/log/debug.log` |
| [Magento\Framework\Logger\Handler\Exception][exception] | `/var/log/exception.log` |
| [Magento\Framework\Logger\Handler\Syslog][syslog] | - |
| [Magento\Framework\Logger\Handler\System][system] | `/var/log/system.log` |

以下で確認できます。 `lib/internal/Magento/Framework/Logger/Handler` ディレクトリ。

カスタムファイルへのログインには、次のいずれかの方法を使用できます。

- でのカスタムログファイルの設定 `di.xml`
- カスタムロガーハンドラークラスのカスタムファイルを設定します。

## でのカスタムログファイルの設定 `di.xml`

この例は、の使用方法を示しています [仮想タイプ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) ログに記録 `debug` 標準ではなくカスタム・ログ・ファイルへのメッセージ `/var/log/debug.log`.

1. が含まれる `di.xml` モジュールのファイル、カスタムログファイルをとして定義 [仮想タイプ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types).

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomDebug" type="Magento\Framework\Logger\Handler\Base">
       <arguments>
           <argument name="fileName" xsi:type="string">/var/log/payment.log</argument>
        </arguments>
   </virtualType>
   ```

   この `name` 次の値 `Magento\Payment\Model\Method\MyCustomDebug` 一意である必要があります。

1. 別のにハンドラーを定義します [仮想タイプ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) ユニークで `name`:

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
           </argument>
       </arguments>
   </virtualType>
   ```

1. を挿入する `MyCustomLogger` [仮想タイプ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) が含まれる `Magento\Payment\Model\Method\Logger` オブジェクト :

   ```xml
   <type name="Magento\Payment\Model\Method\Logger">
       <arguments>
           <argument name="logger" xsi:type="object">Magento\Payment\Model\Method\MyCustomLogger</argument>
       </arguments>
   </type>
   ```

1. 仮想クラス `Magento\Payment\Model\Method\MyCustomDebug` はに挿入されます。 `debug` のハンドラー `$logger` のプロパティ `Magento\Payment\Model\Method\Logger` クラス。

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
   </argument>
   ```

例外メッセージは、 `/var/log/payment.log` ファイル。

## ロガーハンドラークラスのカスタムログファイルを設定します。

この例では、カスタムのロガーハンドラークラスを使用してログを記録する方法を示します `error` メッセージを特定のログ・ファイルに保存する。

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

1. このクラスのハンドラーをとして定義 [仮想タイプ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) モジュールの `di.xml` ファイル。

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

1. が含まれる `type` 定義で、カスタムロガーハンドラーが挿入されるクラス名を指定します。 このタイプの引数として、前の手順で指定した仮想タイプ名を使用します。

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

1. クラス `Vendor\ModuleName\Logger\Handler\ErrorHandler` はに挿入されます。 `error` のハンドラー `$logger` のプロパティ `Vendor\ModuleName\Observer\MyObserver`.

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="error" xsi:type="object">Vendor\ModuleName\Logger\Handler\ErrorHandler</item>
   </argument>
   ...
   ```

例外メッセージのログは、 `/var/log/my_custom_logger/error.log` ファイル。

<!-- link definitions -->

[base]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Base.php
[debug]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Debug.php
[exception]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Exception.php
[syslog]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Syslog.php
[system]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/System.php
