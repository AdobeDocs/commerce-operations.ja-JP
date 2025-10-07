---
title: コードコンパイラー
description: コマンドラインからAdobe Commerce コードコンパイラを実行する方法を説明します。 コンパイルプロセスと最適化手法について説明します。
exl-id: 08dbf808-ea79-4956-a0bc-f464bb80eee7
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '169'
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

コード コンパイル クラスは、[\Magento\Setup\Module\Di\App\Task\Operation][operation] 名前空間にあります。

シングルテナントコンパイラーを実行するには：

```bash
bin/magento setup:di:compile
```

```
Generated code and dependency injection configuration successfully.
```

Commerce アプリケーションのインストール前にコードをコンパイルするには：

場合によっては、Commerce アプリケーションをインストールする前にコードをコンパイルする必要があります。

1. モジュールを有効にします。

   ```bash
   bin/magento module:enable --all [-c|--clear-static-content]
   ```

   静的コンテンツをクリアするには、`[-c|--clear-static-content]` オプションを使用します。 これは、以前にモジュールを有効または無効にしていて、以前にモジュールに対して生成された静的コンテンツをクリアする必要がある場合に必要です。

   [&#x200B; モジュールの有効化 &#x200B;](../../installation/tutorials/manage-modules.md) を参照してください。

1. コードをコンパイルします。

   ```bash
   bin/magento setup:di:compile
   ```

   ```
   Generated code and dependency injection configuration successfully.
   ```

データベースを使用せずにコードをコンパイルするには、[Magentoをインストールせずに静的ビューファイルをデプロイする &#x200B;](../cli/static-view-file-deployment.md) を参照してください。

<!-- link definitions -->

[operation]: https://github.com/magento/magento2/blob/2.4/setup/src/Magento/Setup/Module/Di/App/Task/Operation
