---
title: コードコンパイラー
description: コマンドラインからコードコンパイラを実行する方法を説明します。
exl-id: 08dbf808-ea79-4956-a0bc-f464bb80eee7
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---

# コードコンパイラー

{{file-system-owner}}

コードのコンパイルには、以下が含まれます（特定の順序ではありません）。

- アプリケーションコードの生成（ファクトリ、プロキシ）
- エリア設定の集計（エリアごとの依存関係のインジェクション設定の最適化）
- インターセプターの生成（インターセプターのコード生成を最適化）
- 傍受キャッシュの生成
- リポジトリーコード生成（API 用に生成されたコード）
- サービスデータ属性の生成（データオブジェクト用に生成された拡張クラス）

コードのコンパイルクラスは、 [\Magento\Setup\Module\Di\App\Task\Operation][operation] 名前空間。

シングルテナントコンパイラーを実行するには：

```bash
bin/magento setup:di:compile
```

```terminal
Generated code and dependency injection configuration successfully.
```

Commerce アプリケーションのインストール前にコードをコンパイルするには：

場合によっては、Commerce アプリケーションをインストールする前にコードをコンパイルする必要があります。

1. モジュールを有効にします。

   ```bash
   bin/magento module:enable --all [-c|--clear-static-content]
   ```

   の使用 `[-c|--clear-static-content]` 静的なコンテンツを消去するオプション。 これは、以前にモジュールを有効または無効にしていて、以前にモジュールに対して生成された静的コンテンツをクリアする必要がある場合に必要です。

   参照： [モジュールを有効にする](../../installation/tutorials/manage-modules.md).

1. コードをコンパイルします。

   ```bash
   bin/magento setup:di:compile
   ```

   ```terminal
   Generated code and dependency injection configuration successfully.
   ```

データベースを使用せずにコードをコンパイルするには、次を参照してください。 [Magentoをインストールせずに静的ビューファイルを展開する](../cli/static-view-file-deployment.md).

<!-- link definitions -->

[operation]: https://github.com/magento/magento2/blob/2.4/setup/src/Magento/Setup/Module/Di/App/Task/Operation
