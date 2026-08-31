---
title: 例外処理のベストプラクティス
description: Adobe Commerce プロジェクトの開発時に例外をログに記録する際に推奨される方法について説明します。
feature: Best Practices
role: Developer
exl-id: e7ad685b-3eaf-485b-8ab1-702f2e7ab89e
source-git-commit: 4bf8dd5c5320cc9a34cfaa552ec5e91d517d3617
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 0%

---

# 例外処理のベストプラクティス

例外モデルをコンテキストとして使用して`exception.log` ファイルに例外が書き込まれない場合、New Relicまたはその他のPSR-3 モノログ互換ログストレージで例外が認識されず、正しく分析されません。 例外の一部のみをログに記録する（または間違ったファイルにログに記録する）と、例外が見落とされたときに本番環境でバグが発生します。

## 例外処理の修正

次のチェックリストは、正しい例外処理を示す例を示しています。

### ![correct](../../../assets/yes.svg)例外ログへの書き込み

次のパターンを使用して例外ログに書き込みます。追加のアクションに関係なく、書き込まない説得力のある理由がない限り。

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
}
```

このアプローチは、[PSR-3 コンテキスト標準](https://www.php-fig.org/psr/psr-3/#13-context)に従って、ログメッセージに`$e->getMessage`を、コンテキストに`$e` オブジェクトを自動的に保存します。 これは`\Magento\Framework\Logger\Monolog::addRecord`で行われます。

### ![正解](../../../assets/yes.svg) ミュート信号

目的の操作フローの一部である例外をログに記録しないことで、信号をミュートします。 例外が発生した場合にフォローアップアクションは必要ないため、発生したときにログを記録して分析する必要はありません。 シグナルをミュートする理由と、それが意図的であることを示すコメントを追加します。 `phpcs:ignore`と組み合わせる。

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) { // phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch
    // Product already removed
}
```

### ![正しい](../../../assets/yes.svg) ダウングレードの例外

[PSR-3 コンテキスト標準](https://www.php-fig.org/psr/psr-3/#13-context)に従って、例外をダウングレードします。

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->debug($e->getMessage(), ['exception' => $e]);
}
```

### ![正しい](../../../assets/yes.svg) ログが常に最初に表示されます

ベストプラクティスとして、ログは常にコード内で最初に発生し、ログに書き込む前に別の例外または致命的なエラーがスローされるケースを防ぎます。

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
    $this->alternativeProcedure();
}
```

### ![正しい](../../../assets/yes.svg) ログメッセージと例外トレース全体

[PSR-3 コンテキスト標準](https://www.php-fig.org/psr/psr-3/#13-context)に従って、メッセージと例外トレース全体を記録します。

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e->getMessage(), ['exception' => $e, 'trace' => $e->getTrace()]);
}
```

## 誤った例外処理

次の例は、誤った例外処理を示しています。

### ログを記録する前の![不正な](../../../assets/no.svg) ロジック

ログを記録する前にロジックを実行すると、別の例外または致命的なエラーが発生する可能性があります。これにより、例外がログに記録されなくなり、[正しい例](#logging-always-comes-first)に置き換える必要があります。

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    $this->alternativeProcedure();
    $this->logger->critical($e);
}
```

### ![正しくない](../../../assets/no.svg)空の`catch`

空の`catch` ブロックは、意図しないミュートの兆候である可能性があり、[正しい例](#mute-signals)に置き換える必要があります。

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
}
```

### ![正しくない](../../../assets/no.svg)二重定位

検出されたローカライズされた例外がまだ翻訳されていない場合は、例外が最初にスローされた場所で問題を解決します。

```php
try {
    $this->productRepository->getById($sku);
} catch (LocalizedException $e) {
    throw new LocalizedException(__($e->getMessage()));
}
```

### ![不正確な](../../../assets/no.svg) ログメッセージとトレースを異なるログファイルに記録する

次のコードは、例外のスタックトレースを文字列としてログファイルに誤って記録します。

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->error($e->getMessage());
    $this->logger->debug($e->getTraceAsString());
}
```

この方法では、PSR-3に準拠していないメッセージに改行が発生します。 スタックトレースを含む例外は、メッセージコンテキストの一部として、New Relicまたはその他のPSR-3 モノログ互換ログストレージにメッセージと共に正しく保存できるようにする必要があります。

この問題を修正するには、[例外ログに書き込む](#write-to-the-exception-log)または[&#x200B; ダウングレード例外](#downgrade-exceptions)に示す正しい例に従ってコードを置き換えます。

### コンテキストのない![不正な](../../../assets/no.svg) ダウングレードの例外

例外はエラーにダウングレードされ、オブジェクトを渡すことができず、文字列のみが渡されないため、`getMessage()`が返されます。 これにより、トレースが失われ、[例外ログへの書き込み](#write-to-the-exception-log)または[&#x200B; ダウングレード例外](#downgrade-exceptions)に示す正しい例に置き換える必要があります。

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->error($e->getMessage());
}
```

### ![正しくない](../../../assets/no.svg)例外ログにメッセージのみを記録します

オブジェクト `$e`を渡す代わりに、`$e->getMessage()`のみが渡されます。 これにより、トレースが失われ、[例外ログへの書き込み](#write-to-the-exception-log)または[&#x200B; ダウングレード例外](#downgrade-exceptions)に示す正しい例に置き換える必要があります。

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->critical($e->getMessage());
}
```

### ![不正な](../../../assets/no.svg) `// phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch`がありません

`phpcs:ignore`行を省略すると、PHPCSで警告がトリガーされ、CIを渡してはなりません。 これは、[&#x200B; ミュート信号](#mute-signals)に示す正しい例に置き換える必要があります。

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    // Product already removed
}
```
