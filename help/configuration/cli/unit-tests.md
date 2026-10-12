---
title: 単体テストの実行
description: Adobe Commerce コードベースで定義された単体テストを実行する方法について説明します。 テストコマンド、実行オプション、結果レポートをご覧ください。
exl-id: 23200420-d15c-4910-8ce6-abd0cc070777
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
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
source-wordcount: '152'
ht-degree: 0%
---
# 単体テストの実行

{{file-system-owner}}

このコマンドは、Commerce 2のコードベースで定義された一連のテストを実行します。 すべてのテストを実行することも、選択したテストを実行することもできます。 サポートされていないタイプを指定すると、プログラムは終了し、使用可能なすべてのタイプが一覧表示されます。 実行後、テスト実行と結果を示す詳細レポートが表示されます。

## 前提条件

このコマンドを実行する前に、次の&#x200B;_は_&#x200B;である必要があります。

- `Magento_Developer` モジュールを有効にする必要があります。 次のように有効にできます。

  ```shell
  bin/magento module:enable [--force] Magento_Developer
  ```

  `--force` オプションは、必要な場合にのみ使用してください。

- 必要なテストを実行するようにシステムを設定する必要があります。

例えば、統合テストを実行するには、`dev/tests/integration/etc/install-config-mysql.php.dist`を`dev/tests/integration/etc/install-config-mysql.php`にコピーし、環境に合わせて変更する必要があります。

## 実行中のテスト

コマンドの使用状況：

```shell
bin/magento dev:tests:run <test>
```

使用可能なテストタイプを一覧表示するには：

```shell
bin/magento dev:tests:run --help
```

リターンの例：

```text
all, unit, integration, integration-all, static, static-all, integrity, legacy, default
```

例えば、統合テストを実行するには、次の手順を実行します。

```shell
bin/magento dev:tests:run integration
```
