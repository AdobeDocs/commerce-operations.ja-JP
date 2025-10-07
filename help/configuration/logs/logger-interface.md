---
title: ロガーインターフェイス
description: Adobe Commerceのロガーインターフェイスをカスタムログに使用する方法について説明します。 PSR-3 の実装とログ機能について説明します。
feature: Configuration, Logs
exl-id: fdb1b431-405a-4c32-aff1-9e50bf0a2c90
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# ロガーインターフェイス

ロガーの使用を開始するには、`\Psr\Log\LoggerInterface` のインスタンスを作成する必要があります。 このインターフェイスでは、次の関数を呼び出してデータをログファイルに書き込むことができます。

- [alert （） &#x200B;](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L43)
- [critical （） &#x200B;](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L55)
- [debug （） &#x200B;](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L111)
- [emergency （） &#x200B;](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L30)
- [error （） &#x200B;](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L66)
- [info （） &#x200B;](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L101)
- [log （） &#x200B;](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L122)
- [notice （） &#x200B;](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L89)
- [warning （） &#x200B;](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L79)

その方法の 1 つは、[&#x200B; ログデータベースアクティビティ &#x200B;](../logs/database-activity.md) 例で説明します。

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

前述の例は、コンストラクターの挿入 `SomeModel` 使用して `\Psr\Log\LoggerInterface` オブジェクトを受け取る場合を示しています。 メソッド `doSomething` で何らかのエラーが発生した場合は、メソッド `critical` （`$this->logger->critical($e);`）に記録されます。

[RFC 5424](https://datatracker.ietf.org/doc/html/rfc5424) は、8 つのログレベル（デバッグ、情報、通知、警告、エラー、重大、アラート、緊急）を定義します。
