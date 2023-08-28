---
title: 例外処理のベストプラクティス
description: Adobe Commerceプロジェクトを開発する際に例外をログに記録するための推奨される方法について説明します。
feature: Best Practices
role: Developer
source-git-commit: 94d37b6a95cae93f465daf8eb96363a198833e27
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---


# 例外処理のベストプラクティス

例外が `exception.log` 例外モデルをコンテキストとして含むファイルは、New Relicまたはその他の PSR-3 モノログ互換のログストレージでは、正しく認識および分析されません。 例外の一部のみをログに記録する（または間違ったファイルにログに記録する）と、例外が見落とされた場合に、実稼動環境のバグが発生します。

## 正しい例外処理

次のチェックリストは、正しい例外処理を示す例を示しています。

### ![正しい](../../../assets/yes.svg) 例外ログに書き込む

やむを得ない理由がない限り、その他のアクションに関係なく、次のパターンを使用して例外ログに書き込みます。

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
}
```

この方法では、 `$e->getMessage` をログメッセージに追加し、 `$e` オブジェクトをコンテキストに追加し、 [PSR-3 コンテキスト標準](https://www.php-fig.org/psr/psr-3/#13-context). これは、でおこないます。 `\Magento\Framework\Logger\Monolog::addRecord`.

### ![正しい](../../../assets/yes.svg) シグナルをミュート

意図した操作フローの一部である例外をログに記録しないことで、シグナルをミュートします。 例外が発生した場合は、フォローアップアクションは必要ないので、発生時にログに記録して分析する必要はありません。 シグナルをミュートする理由と意図的な理由を示すコメントを追加します。 組み合わせ `phpcs:ignore`.

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) { // phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch
    // Product already removed
}
```

### ![正しい](../../../assets/yes.svg) 例外をダウングレード

次の手順に従って例外をダウングレードする [PSR-3 コンテキスト標準](https://www.php-fig.org/psr/psr-3/#13-context).

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->debug($e->getMessage(), ['exception' => $e]);
}
```

### ![正しい](../../../assets/yes.svg) ログが常に最初に記録される

ベストプラクティスとして、ログは常にコードで最初に記録されるので、ログに書き込む前に別の例外や致命的なエラーがスローされるのを防ぎます。

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
    $this->alternativeProcedure();
}
```

### ![正しい](../../../assets/yes.svg) ログメッセージと例外トレース全体

ログメッセージと例外トレース全体を、 [PSR-3 コンテキスト標準](https://www.php-fig.org/psr/psr-3/#13-context).

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e->getMessage(), ['exception' => $e, 'trace' => $e->getTrace()]);
}
```

## 誤った例外処理

次の例は、誤った例外処理を示しています。

### ![誤った](../../../assets/no.svg) ログ記録前のロジック

ログ記録前のロジックにより、別の例外や致命的なエラーが発生する場合があり、これにより例外が記録されなくなり、次のように置き換える必要があります。 [正しい例](#correct-logging-always-comes-first).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    $this->alternativeProcedure();
    $this->logger->critical($e);
}
```

### ![誤った](../../../assets/no.svg) 空 `catch`

空 `catch` ブロックは、意図しないミュートの兆候である可能性があり、 [正しい例](#correct-mute-signals).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
}
```

### ![誤った](../../../assets/no.svg) 二重ローカリゼーション

キャッチされたローカライズされた例外がまだ翻訳されていない場合は、初めて例外がスローされる場所で問題を解決します。

```php
try {
    $this->productRepository->getById($sku);
} catch (LocalizedException $e) {
    throw new LocalizedException(__($e->getMessage()));
}
```

### ![誤った](../../../assets/no.svg) ログメッセージと別のログファイルへのトレース

次のコードは、例外のスタックトレースを文字列としてログファイルに誤って記録します。

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->error($e->getMessage());
    $this->logger->debug($e->getTraceAsString());
}
```

この方法では、PSR-3 に準拠していない改行がメッセージに含まれます。 例外（スタックトレースを含む）は、メッセージコンテキストの一部として、New Relicまたは他の PSR-3 モノログ互換のログストレージのメッセージと共に正しく保存される必要があります。

次に示す正しい例に従ってコードを置き換え、この問題を修正します。 [例外ログに書き込む](#correct-write-to-the-exception-log) または [例外をダウングレード](#correct-downgrade-exceptions).

### ![誤った](../../../assets/no.svg) コンテキストのない例外のダウングレード

例外は、エラーにダウングレードされます。このエラーでは、オブジェクトの渡しは許可されず、文字列のみが渡されるので、 `getMessage()`. これにより、トレースが失われ、に示す正しい例に置き換えられます。 [例外ログに書き込む](#correct-write-to-the-exception-log) または [例外をダウングレード](#correct-downgrade-exceptions).

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->error($e->getMessage());
}
```

### ![誤った](../../../assets/no.svg) メッセージのみを例外ログに記録

オブジェクトを渡す代わりに `$e`、のみ `$e->getMessage()` が渡された。 これにより、トレースが失われ、次に示す正しい例に置き換えられます。 [例外ログに書き込む](#correct-write-to-the-exception-log) または [例外をダウングレード](#correct-downgrade-exceptions).

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->critical($e->getMessage());
}
```

### ![誤った](../../../assets/no.svg) 見つかりません `// phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch`

の省略 `phpcs:ignore` の行は、PHPCS での警告をトリガーし、CI に合格しないでください。 これは、 [シグナルをミュート](#correct-mute-signals).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    // Product already removed
}
```
