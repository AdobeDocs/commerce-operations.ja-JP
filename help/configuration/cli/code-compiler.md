---
title: コードコンパイラー
description: コマンドラインからコードコンパイラーを実行する方法を説明します。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---


# コードコンパイラー

{{file-system-owner}}

コードのコンパイルには、以下が含まれます（特定の順序ではありません）。

- アプリケーションコードの生成（ファクトリ、プロキシ）
- 領域構成の集計（最適化） [依存注入](https://glossary.magento.com/dependency-injection) 地域ごとの設定
- インターセプターの生成（インターセプターの最適化されたコード生成）
- 傍受キャッシュの生成
- コードの生成（API 用に生成されたコード）をリポジトリーに送信
- サービスデータ属性の生成（生成済み） [拡張](https://glossary.magento.com/extension) データオブジェクト用のクラス

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

   以下を使用： `[-c|--clear-static-content]` クリアするオプション [静的コンテンツ](https://glossary.magento.com/static-content). これは、以前にモジュールを有効または無効にした場合に必要です。また、以前に生成した静的コンテンツをクリアする必要があります。

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
