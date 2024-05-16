---
title: 単体テストの実行
description: Adobe Commerce コードベースで定義された単体テストの実行
exl-id: 23200420-d15c-4910-8ce6-abd0cc070777
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---

# 単体テストの実行

{{file-system-owner}}

このコマンドは、Commerce 2 コードベースで定義された一連のテストを実行します。 すべてのテストまたは選択したテストを実行できます。 サポートされていないタイプが指定されると、プログラムは終了し、使用可能なすべてのタイプが一覧表示されます。 実行後、テストの実行と結果を示す詳細なレポートが表示されます。

## 前提条件

このコマンドを実行する前に、次の操作を行います _が_ true:

- この `Magento_Developer` モジュールを有効にする必要があります。 有効にするには、次の手順を実行します。

  ```bash
  bin/magento module:enable [--force] Magento_Developer
  ```

  の使用 `--force` 必要な場合にのみオプションです。

- 目的のテストを実行するようにシステムを設定する必要があります。

例えば、統合テストを実行するには、次をコピーする必要があります `dev/tests/integration/etc/install-config-mysql.php.dist` 対象： `dev/tests/integration/etc/install-config-mysql.php` 環境に合わせて変更してください。

## テストの実行

コマンドの使用法：

```bash
bin/magento dev:tests:run <test>
```

使用可能なテストタイプを一覧表示するには、次の手順に従います。

```bash
bin/magento dev:tests:run --help
```

サンプルの戻り値：

```terminal
all, unit, integration, integration-all, static, static-all, integrity, legacy, default
```

例えば、統合テストを実行するには、次の手順を実行します。

```bash
bin/magento dev:tests:run integration
```
