---
title: コードコンパイラー
description: コマンドラインからAdobe Commerce コードコンパイラーを実行する方法を説明します。 コンピレーションプロセスと最適化手法の詳細。
exl-id: 08dbf808-ea79-4956-a0bc-f464bb80eee7
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
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

   [&#x200B; モジュールを有効にする](../../installation/tutorials/manage-modules.md)を参照してください。

1. コードをコンパイルします。

   ```shell
   bin/magento setup:di:compile
   ```

   ```text
   Generated code and dependency injection configuration successfully.
   ```

データベースを使用せずにコードをコンパイルするには、「[Magentoをインストールせずに静的ビューファイルをデプロイする](../cli/static-view-file-deployment.md)」を参照してください。

