---
title: Logger インターフェイス
description: Adobe Commerceのロガーインターフェイスをカスタムロギングに使用する方法について説明します。 PSR-3の実装とログ関数を確認します。
feature: Configuration, Logs
exl-id: fdb1b431-405a-4c32-aff1-9e50bf0a2c90
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: 3c398179-d35a-51ba-b317-6c5b95feef5e
    internal-label: Logs
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%
---
# Logger インターフェイス

ロガーの操作を開始するには、`\Psr\Log\LoggerInterface`のインスタンスを作成する必要があります。 このインターフェイスでは、次の関数を呼び出して、ログファイルにデータを書き込むことができます。

- [alert （）](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L43)
- [critical （）](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L55)
- [debug （）](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L111)
- [emergency （）](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L30)
- [error （）](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L66)
- [info （）](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L101)
- [log （）](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L122)
- [notice （）](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L89)
- [warning （）](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L79)

そのひとつの方法は、[ ログデータベースアクティビティ ](../logs/database-activity.md)の例で説明されています。

もうひとつの方法は次のとおりです。

```php
class SomeModel
 {
     private $logger;

     public function __construct(\Psr\Log\LoggerInterface $logger)
     {
         $this->logger = $logger;
     }

     public function doSomething()
     {
         try {
             //do something
         } catch (\Exception $e) {
             $this->logger->critical('Error message', ['exception' => $e]);
         }
     }
 }
```

前述の例では、`SomeModel`がコンストラクターのインジェクションを使用して`\Psr\Log\LoggerInterface` オブジェクトを受信することを示しています。 メソッド `doSomething`では、エラーが発生した場合、メソッド `critical` （`$this->logger->critical($e);`）にログに記録されます。

[RFC 5424](https://datatracker.ietf.org/doc/html/rfc5424)は、8つのログ レベル （デバッグ、情報、通知、警告、エラー、重大、警告、緊急、および緊急）を定義します。
