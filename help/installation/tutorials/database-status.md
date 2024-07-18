---
title: データベースのステータスの確認
description: 次の手順に従って、Adobe Commerce データベースのステータスを確認します。
exl-id: 33d9b30a-4504-4955-b11a-0a642f23209b
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 3%

---

# データベースのステータスの確認

このコマンドを実行する前に、[ 展開構成を作成または更新 ](deployment.md) する必要があります。

## コマンドの使用法

データベースのステータスを確認します。

```bash
bin/magento setup:db:status
```

このコマンドには引数やオプションはありません。

次に出力例を示します。

```
All modules are up to date.
```

このコマンドは、次のいずれかの終了コードを返します。

| 終了コード | 説明 | 推奨されるアクション |
|--------------|--------------|---------------|
| 0 | 標準 | なし |
| 1 | 一部のモジュールでは、データベースよりも新しいまたは古いコードバージョンを使用します | [`magento setup:upgrade`](database-upgrade.md) を実行してデータベーススキーマを更新し、アプリケーションのルートディレクトリから `composer update` を実行して、コンポーネントの依存関係を更新します |
| 2 | `magento setup:upgrade` は必須です | データベーススキーマを更新できませ [`magento setup:upgrade`](database-upgrade.md) でした |
