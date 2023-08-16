---
title: 単体テストの実行
description: Adobe Commerceコードベースで定義された単体テストを実行します。
exl-id: 23200420-d15c-4910-8ce6-abd0cc070777
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---

# 単体テストの実行

{{file-system-owner}}

このコマンドは、Commerce 2 コードベースで定義された一連のテストを実行します。 すべてのテストまたは選択したテストを実行できます。 サポートされていないタイプが指定されると、プログラムは終了し、使用可能なすべてのタイプが一覧表示されます。 実行後、テスト実行と結果を示す詳細レポートが表示されます。

## 前提条件

このコマンドを実行する前に、次の手順を実行します。 _必須_ true の場合：

- The `Magento_Developer` モジュールを有効にする必要があります。 次のように有効にすることができます。

  ```bash
  bin/magento module:enable [--force] Magento_Developer
  ```

  以下を使用します。 `--force` オプションは、必要な場合にのみ選択します。

- 目的のテストを実行するには、システムを設定する必要があります。

例えば、統合テストを実行するには、 `dev/tests/integration/etc/install-config-mysql.php.dist` から `dev/tests/integration/etc/install-config-mysql.php` 環境に合わせて変更します。

## テストの実行

コマンドの使用：

```bash
bin/magento dev:tests:run <test>
```

使用可能なテストタイプをリストするには：

```bash
bin/magento dev:tests:run --help
```

戻り値の例：

```terminal
all, unit, integration, integration-all, static, static-all, integrity, legacy, default
```

例えば、統合テストを実行するには、次の手順に従います。

```bash
bin/magento dev:tests:run integration
```
