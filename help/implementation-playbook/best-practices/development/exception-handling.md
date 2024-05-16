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

例外がに書き込まれない場合 `exception.log` 例外モデルをコンテキストとして含むファイルは、New Relicまたは他の PSR-3 モノログ互換ログストレージで正しく認識および分析されません。 例外の一部のみをログに記録（または間違ったファイルに記録）すると、例外が見落とされた場合に、実稼動環境でバグが発生します。

## 正しい例外処理

次のチェックリストは、正しい例外処理を示す例を示しています。

### ![正解](../../../assets/yes.svg) 例外ログへの書き込み

やむを得ない理由がある場合を除き、それ以上のアクションに関係なく、次のパターンを使用して例外ログに書き込みます。

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
}
```

この方法では、が自動的に保存されます `$e->getMessage` ログメッセージに追加し、 `$e` オブジェクトをコンテキストに追加し、 [PSR-3 コンテキスト規格](https://www.php-fig.org/psr/psr-3/#13-context). これは、次の場所で行います。 `\Magento\Framework\Logger\Monolog::addRecord`.

### ![正解](../../../assets/yes.svg) シグナルのミュート

意図された操作フローの一部である例外をログに記録しないことでシグナルをミュートします。 例外が発生した場合は、フォローアップのアクションは必要ないので、例外が発生した場合にログに記録して分析する必要はありません。 シグナルをミュートする理由と、意図的なものであることを示すコメントを追加します。 と組み合わせる `phpcs:ignore`.

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) { // phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch
    // Product already removed
}
```

### ![正解](../../../assets/yes.svg) 例外のダウングレード

次の手順に従って、例外をダウングレードします [PSR-3 コンテキスト規格](https://www.php-fig.org/psr/psr-3/#13-context).

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->debug($e->getMessage(), ['exception' => $e]);
}
```

### ![正解](../../../assets/yes.svg) ログは常に最初に記録されます

ベストプラクティスとして、ログを書き込む前に別の例外や致命的なエラーがスローされるケースを防ぐために、常にコードの最初にログを記録します。

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
    $this->alternativeProcedure();
}
```

### ![正解](../../../assets/yes.svg) ログメッセージと例外トレース全体

次の手順に従って、メッセージおよび例外トレース全体を記録します [PSR-3 コンテキスト規格](https://www.php-fig.org/psr/psr-3/#13-context).

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e->getMessage(), ['exception' => $e, 'trace' => $e->getTrace()]);
}
```

## 間違った例外処理

次の例は、誤った例外処理を示しています。

### ![不正解](../../../assets/no.svg) ログに記録する前のロジック

ログに記録する前のロジックは、別の例外や致命的なエラーを引き起こす可能性があり、例外がログに記録されなくなり、に置き換える必要があります。 [正しい例](#logging-always-comes-first).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    $this->alternativeProcedure();
    $this->logger->critical($e);
}
```

### ![不正解](../../../assets/no.svg) 空 `catch`

空 `catch` ブロックは、意図しないミュートの兆候である可能性があり、 [正しい例](#mute-signals).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
}
```

### ![不正解](../../../assets/no.svg) 二重局在

キャッチされたローカライズされた例外がまだ翻訳されていない場合は、例外が最初にスローされた場所で問題を解決します。

```php
try {
    $this->productRepository->getById($sku);
} catch (LocalizedException $e) {
    throw new LocalizedException(__($e->getMessage()));
}
```

### ![不正解](../../../assets/no.svg) 様々なログファイルへのログメッセージとトレース

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

に示す正しい例に従ってコードを置き換えて、この問題を修正します。 [例外ログへの書き込み](#write-to-the-exception-log) または [例外のダウングレード](#downgrade-exceptions).

### ![不正解](../../../assets/no.svg) コンテキストのない例外のダウングレード

例外はエラーにダウングレードされます。このエラーでは、オブジェクトは渡されず、文字列のみが渡されるので、 `getMessage()`. これにより、トレースが失われ、に示す正しい例に置き換える必要があります。 [例外ログへの書き込み](#write-to-the-exception-log) または [例外のダウングレード](#downgrade-exceptions).

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->error($e->getMessage());
}
```

### ![不正解](../../../assets/no.svg) 例外ログにメッセージのみを記録する

オブジェクトを渡す代わりに `$e`、のみ `$e->getMessage()` が渡されます。 これによりトレースが失われるので、正しい例に置き換える必要があります [例外ログへの書き込み](#write-to-the-exception-log) または [例外のダウングレード](#downgrade-exceptions).

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->critical($e->getMessage());
}
```

### ![不正解](../../../assets/no.svg) なし `// phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch`

を省略する `phpcs:ignore` ライントリガーは PHPCS で警告を表示するため、CI を渡さないでください。 これを、に示す正しい例に置き換える必要があります。 [シグナルのミュート](#mute-signals).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    // Product already removed
}
```
