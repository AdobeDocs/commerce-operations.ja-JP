---
title: ロガーインターフェイス
description: ロガーインターフェイスの概要。
feature: Configuration, Logs
exl-id: fdb1b431-405a-4c32-aff1-9e50bf0a2c90
source-git-commit: 991bd5fb34a2ffe61aa194ec46e2b04b4ce5b3e7
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---

# ロガーインターフェイス

ロガーの使用を開始するには、のインスタンスを作成する必要があります `\Psr\Log\LoggerInterface`. このインターフェイスでは、次の関数を呼び出してデータをログファイルに書き込むことができます。

- [alert （）](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L43)
- [critical （）](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L55)
- [debug （）](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L111)
- [emergency （）](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L30)
- [error （）](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L66)
- [info （）](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L101)
- [log （）](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L122)
- [notice （）](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L89)
- [warning （）](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L79)

その方法の 1 つについては、を参照してください。 [データベースアクティビティを記録](../logs/database-activity.md) 例えば、のようになります。

もう 1 つの方法は次のとおりです。

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

前述の例は、次のことを示しています `SomeModel` を受信 `\Psr\Log\LoggerInterface` コンストラクターの挿入を使用するオブジェクト。 メソッド内 `doSomething`何らかのエラーが発生した場合は、メソッドに記録されます `critical` （`$this->logger->critical($e);`）に設定します。

[RFC 5424](https://datatracker.ietf.org/doc/html/rfc5424) 8 つのログレベル（デバッグ、情報、通知、警告、エラー、重大、アラート、緊急）を定義します。
