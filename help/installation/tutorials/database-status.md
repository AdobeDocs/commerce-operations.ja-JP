---
title: データベースのステータスの確認
description: 次の手順に従って、Adobe Commerce データベースのステータスを確認します。
exl-id: 33d9b30a-4504-4955-b11a-0a642f23209b
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 3%

---

# データベースのステータスの確認

このコマンドを実行する前に、次の操作が必要です [デプロイメント設定の作成または更新](deployment.md).

## コマンドの使用法

データベースのステータスを確認します。

```bash
bin/magento setup:db:status
```

このコマンドには引数やオプションはありません。

次に出力例を示します。

```terminal
All modules are up to date.
```

このコマンドは、次のいずれかの終了コードを返します。

| 終了コード | 説明 | 推奨されるアクション |
|--------------|--------------|---------------|
| 0 | 標準 | なし |
| 1 | 一部のモジュールでは、データベースよりも新しいまたは古いコードバージョンを使用します | 実行 [`magento setup:upgrade`](database-upgrade.md) データベーススキーマを更新してを実行するには、次の手順を実行します `composer update` アプリケーションのルートディレクトリからコンポーネントの依存関係を更新 |
| 2 | `magento setup:upgrade` は必須です | [`magento setup:upgrade`](database-upgrade.md) データベーススキーマを更新するには |
