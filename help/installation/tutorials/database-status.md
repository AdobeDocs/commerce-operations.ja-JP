---
title: データベースのステータスの確認
description: Adobe Commerce データベースのステータスを確認するには、次の手順に従います。
exl-id: 33d9b30a-4504-4955-b11a-0a642f23209b
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 3%

---

# データベースのステータスの確認

このコマンドを実行する前に、[ デプロイメント設定を作成または更新する必要があります](deployment.md)。

## コマンドの使用

データベースのステータスを確認します。

```shell
bin/magento setup:db:status
```

このコマンドには引数またはオプションがありません。

出力の例は次のとおりです。

```text
All modules are up to date.
```

このコマンドは、次のいずれかの終了コードを返します。

| 終了コード | 説明 | 推奨アクション |
|--------------|--------------|---------------|
| 0 | 標準 | なし |
| 1 | 一部のモジュールでは、データベースよりも新しいまたは古いコードバージョンを使用します | [`magento setup:upgrade`](database-upgrade.md)を実行してデータベース スキーマを更新し、アプリケーション ルート ディレクトリから`composer update`を実行してコンポーネントの依存関係を更新します |
| 2 | `magento setup:upgrade`が必要です | データベース スキーマを更新する[`magento setup:upgrade`](database-upgrade.md) |
