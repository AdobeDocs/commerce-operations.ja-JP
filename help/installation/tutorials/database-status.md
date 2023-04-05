---
title: データベースのステータスを確認
description: 以下の手順に従って、Adobe CommerceまたはMagento Open Sourceデータベースのステータスを確認します。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 2%

---


# データベースのステータスを確認

このコマンドを実行する前に、次の操作を行う必要があります。 [デプロイメント設定を作成または更新する](deployment.md).

## コマンドの使用

データベースのステータスを確認します。

```bash
bin/magento setup:db:status
```

このコマンドには、引数やオプションはありません。

出力例を次に示します。

```terminal
All modules are up to date.
```

このコマンドは、次のいずれかの終了コードを返します。

| 出口コード | 説明 | 推奨アクション |
|--------------|--------------|---------------|
| 0 | 標準 | なし |
| 1 | 一部のモジュールでは、データベースより新しいまたは古いバージョンのコードを使用します | 実行 [`magento setup:upgrade`](database-upgrade.md) データベーススキーマを更新してを実行するには、以下を実行します。 `composer update` アプリケーションのルートディレクトリからコンポーネントの依存関係を更新 |
| 2 | `magento setup:upgrade` 必須 | [`magento setup:upgrade`](database-upgrade.md) データベーススキーマを更新するには |
