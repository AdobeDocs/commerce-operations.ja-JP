---
title: コードコンパイラー
description: コマンドラインからAdobe Commerce コードコンパイラーを実行する方法を説明します。 コンピレーションプロセスと最適化手法の詳細。
exl-id: 08dbf808-ea79-4956-a0bc-f464bb80eee7
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
source-wordcount: '184'
ht-degree: 0%
---
# コードコンパイラー

{{file-system-owner}}

コードのコンパイルには、次の内容が含まれます（特に順序は指定されていません）。

- アプリケーションコードの生成（工場、プロキシ）
- エリア設定の集計（エリアごとに最適化された依存関係インジェクション設定）
- インターセプタ生成（インターセプタの最適化されたコード生成）
- インターセプションキャッシュの生成
- リポジトリコード生成（API用に生成されたコード）
- サービスデータ属性の生成（データオブジェクト用に生成された拡張クラス）

コード コンパイル クラスは、[\Magento\Setup\Module\Di\App\Task\Operation](https://github.com/magento/magento2/blob/2.4.8/setup/src/Magento/Setup/Module/Di/App/Task/Operation)名前空間で見つけることができます。

シングルテナントコンパイラーを実行するには：

```shell
bin/magento setup:di:compile
```

```text
Generated code and dependency injection configuration successfully.
```

Commerce アプリケーションをインストールする前にコードをコンパイルするには：

場合によっては、Commerce アプリケーションをインストールする前にコードをコンパイルすることをお勧めします。

1. モジュールを有効にします。

   ```shell
   bin/magento module:enable --all [-c|--clear-static-content]
   ```

   静的コンテンツを消去するには、`[-c|--clear-static-content]` オプションを使用します。 これは、以前にモジュールを有効または無効にし、以前に生成した静的コンテンツをクリアする必要がある場合に必要です。

   [ モジュールを有効にする](../../installation/tutorials/manage-modules.md)を参照してください。

1. コードをコンパイルします。

   ```shell
   bin/magento setup:di:compile
   ```

   ```text
   Generated code and dependency injection configuration successfully.
   ```

データベースを使用せずにコードをコンパイルするには、[Magento](../cli/static-view-file-deployment.md)をインストールせずに静的ビューファイルをデプロイするを参照してください。

