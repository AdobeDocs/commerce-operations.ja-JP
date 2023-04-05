---
title: コードコンパイラー
description: コマンドラインからコードコンパイラーを実行する方法を説明します。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---


# コードコンパイラー

{{file-system-owner}}

コードのコンパイルには、以下が含まれます（特定の順序ではありません）。

- アプリケーションコードの生成（ファクトリ、プロキシ）
- 領域構成の集計（領域ごとに最適化された依存関係射出構成）
- インターセプターの生成（インターセプターの最適化されたコード生成）
- 傍受キャッシュの生成
- コードの生成（API 用に生成されたコード）をリポジトリーに送信
- サービスデータ属性の生成（データオブジェクト用に生成された拡張クラス）

コードコンパイルクラスは、 [\Magento\Setup\Module\Di\App\Task\Operation][operation] 名前空間。

シングルテナントコンパイラを実行するには：

```bash
bin/magento setup:di:compile
```

```terminal
Generated code and dependency injection configuration successfully.
```

Commerce アプリケーションをインストールする前にコードをコンパイルするには：

場合によっては、Commerce アプリケーションをインストールする前にコードをコンパイルする必要があります。

1. モジュールを有効にします。

   ```bash
   bin/magento module:enable --all [-c|--clear-static-content]
   ```

   以下を使用： `[-c|--clear-static-content]` オプションを使用して静的コンテンツをクリアできます。 これは、以前にモジュールを有効または無効にした場合に必要です。また、以前に生成した静的コンテンツをクリアする必要があります。

   詳しくは、 [モジュールの有効化](../../installation/tutorials/manage-modules.md).

1. コードをコンパイルします。

   ```bash
   bin/magento setup:di:compile
   ```

   ```terminal
   Generated code and dependency injection configuration successfully.
   ```

データベースを使用せずにコードをコンパイルする場合は、 [静的ビューファイルをデプロイする際にMagento](../cli/static-view-file-deployment.md).

<!-- link definitions -->

[operation]: https://github.com/magento/magento2/blob/2.4/setup/src/Magento/Setup/Module/Di/App/Task/Operation
