---
title: Logger インターフェイス
description: ロガーインターフェイスの基本を学ぶ
feature: Configuration, Logs
exl-id: fdb1b431-405a-4c32-aff1-9e50bf0a2c90
source-git-commit: 991bd5fb34a2ffe61aa194ec46e2b04b4ce5b3e7
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# Logger インターフェイス

ロガーの使用を開始するには、次のインスタンスを作成する必要があります： `\Psr\Log\LoggerInterface`. このインターフェイスを使用すると、次の関数を呼び出して、データをログファイルに書き込むことができます。

- [alert()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L43)
- [critical()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L55)
- [debug()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L111)
- [emergency()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L30)
- [error()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L66)
- [info()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L101)
- [log()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L122)
- [notice()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L89)
- [warning()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L79)

その方法の 1 つは、 [データベースアクティビティをログに記録](../logs/database-activity.md) 例：

別の方法は次のとおりです。

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

前述の例は、を示しています。 `SomeModel` を受信 `\Psr\Log\LoggerInterface` オブジェクトは、コンストラクタインジェクションを使用します。 メソッド内 `doSomething`（エラーが発生した場合は、メソッドに記録されます） `critical` (`$this->logger->critical($e);`) をクリックします。

[RFC 5424](https://datatracker.ietf.org/doc/html/rfc5424) は、8 つのログレベル (debug、info、notice、warning、error、critical、alert、emergency) を定義します。
