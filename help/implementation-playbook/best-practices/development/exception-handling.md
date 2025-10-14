---
title: 例外処理のベストプラクティス
description: Adobe Commerce プロジェクトを開発する際に例外をログに記録するために推奨される方法を説明します。
feature: Best Practices
role: Developer
exl-id: e7ad685b-3eaf-485b-8ab1-702f2e7ab89e
source-git-commit: 4bf8dd5c5320cc9a34cfaa552ec5e91d517d3617
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 0%

---

# 例外処理のベストプラクティス

例外モデルをコンテキストとして `exception.log` ファイルに書き込まない場合、New Relicまたは他の PSR-3 モノログ互換ログストレージで例外が正しく認識および分析されません。 例外の一部のみをログに記録（または間違ったファイルに記録）すると、例外が見落とされた場合に、実稼動環境でバグが発生します。

## 正しい例外処理

次のチェックリストは、正しい例外処理を示す例を示しています。

### ![&#x200B; 正しい &#x200B;](../../../assets/yes.svg) 例外ログに書き込みます

やむを得ない理由がある場合を除き、それ以上のアクションに関係なく、次のパターンを使用して例外ログに書き込みます。

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
}
```

このアプローチでは、`$e->getMessage`PSR-3 コンテキスト標準 `$e` に従って、ログメッセージへの [&#x200B; ータと &#x200B;](https://www.php-fig.org/psr/psr-3/#13-context) オブジェクトがコンテキストに自動的に保存されます。 これは `\Magento\Framework\Logger\Monolog::addRecord` で行われます。

### ![correct](../../../assets/yes.svg) 信号をミュートする

意図された操作フローの一部である例外をログに記録しないことでシグナルをミュートします。 例外が発生した場合は、フォローアップのアクションは必要ないので、例外が発生した場合にログに記録して分析する必要はありません。 シグナルをミュートする理由と、意図的なものであることを示すコメントを追加します。 を `phpcs:ignore` と組み合わせます。

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) { // phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch
    // Product already removed
}
```

### ![correct](../../../assets/yes.svg) 例外のダウングレード

[PSR-3 コンテキスト標準 &#x200B;](https://www.php-fig.org/psr/psr-3/#13-context) に従って、例外をダウングレードします。

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->debug($e->getMessage(), ['exception' => $e]);
}
```

### ![&#x200B; 正確 &#x200B;](../../../assets/yes.svg) 常にログが最初に表示されます

ベストプラクティスとして、ログを書き込む前に別の例外や致命的なエラーがスローされるケースを防ぐために、常にコードの最初にログを記録します。

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
    $this->alternativeProcedure();
}
```

### ![correct](../../../assets/yes.svg) ログメッセージと例外トレース全体

[PSR-3 コンテキスト標準 &#x200B;](https://www.php-fig.org/psr/psr-3/#13-context) に従って、ログメッセージと例外トレース全体を記録します。

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e->getMessage(), ['exception' => $e, 'trace' => $e->getTrace()]);
}
```

## 間違った例外処理

次の例は、誤った例外処理を示しています。

### ![&#x200B; 正しくありません &#x200B;](../../../assets/no.svg) ログに記録する前のロジック

ログに記録する前のロジックは、別の例外や致命的なエラーを引き起こす可能性があり、例外がログに記録されないので、（正しい例 [&#x200B; に置き換える必要があります &#x200B;](#logging-always-comes-first)。

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    $this->alternativeProcedure();
    $this->logger->critical($e);
}
```

### ![&#x200B; 不正確 &#x200B;](../../../assets/no.svg) 空の `catch`

空の `catch` ブロックは、意図しないミュートの兆候である可能性があり、[&#x200B; 正しい例 &#x200B;](#mute-signals) に置き換える必要があります。

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
}
```

### ![&#x200B; 不正確 &#x200B;](../../../assets/no.svg) 二重局在

キャッチされたローカライズされた例外がまだ翻訳されていない場合は、例外が最初にスローされた場所で問題を解決します。

```php
try {
    $this->productRepository->getById($sku);
} catch (LocalizedException $e) {
    throw new LocalizedException(__($e->getMessage()));
}
```

### ![&#x200B; 不正確 &#x200B;](../../../assets/no.svg) ログメッセージと別のログファイルへのトレース

次のコードでは、例外のスタックトレースを文字列としてログファイルに誤って記録します。

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->error($e->getMessage());
    $this->logger->debug($e->getTraceAsString());
}
```

このアプローチでは、PSR-3 に準拠していない改行がメッセージに導入されます。 スタックトレースを含む例外は、メッセージがNew Relicまたは他の PSR-3 モノログ互換ログストレージにメッセージと共に正しく保存されることを確認するために、メッセージコンテキストの一部である必要があります。

[&#x200B; 例外ログへの書き込み &#x200B;](#write-to-the-exception-log) または [&#x200B; 例外のダウングレード &#x200B;](#downgrade-exceptions) に示す正しい例に従ってコードを置き換えることで、この問題を修正します。

### ![&#x200B; 不正確 &#x200B;](../../../assets/no.svg) コンテキストなしの例外のダウングレード

例外はエラーにダウングレードされます。このエラーでは、オブジェクトは渡されず、文字列のみが渡されるので、`getMessage()` になります。 これによりトレースが失われるため、[&#x200B; 例外ログへの書き込み &#x200B;](#write-to-the-exception-log) または [&#x200B; ダウングレードの例外 &#x200B;](#downgrade-exceptions) に示す正しい例に置き換える必要があります。

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->error($e->getMessage());
}
```

### ![&#x200B; 不正確 &#x200B;](../../../assets/no.svg) 例外ログにはメッセージのみを記録します

オブジェクト `$e` を渡す代わりに、`$e->getMessage()` のみが渡されます。 これによりトレースが失われるため、正しい例 [&#x200B; 例外ログへの書き込み &#x200B;](#write-to-the-exception-log) または [&#x200B; 例外のダウングレード &#x200B;](#downgrade-exceptions) に置き換える必要があります。

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->critical($e->getMessage());
}
```

### ![&#x200B; 正しくありません &#x200B;](../../../assets/no.svg)`// phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch` がありません

`phpcs:ignore` 行を省略すると、PHPCS で警告がトリガーされ、CI を渡すことはできません。 これを [&#x200B; 信号のミュート &#x200B;](#mute-signals) に示す正しい例に置き換える必要があります。

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    // Product already removed
}
```
