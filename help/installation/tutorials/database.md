---
title: データベーススキーマの作成
description: Adobe Commerce プロジェクトのデータベースを作成するには、次の手順に従います。
exl-id: 860c9918-44c4-4ef1-88a5-12614566307c
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---

# データベーススキーマの作成

このコマンドを実行する前に、次の操作が必要です [デプロイメント設定の作成または更新](deployment.md).

## データベースの設定とデータの追加

コマンドの使用法：

```bash
bin/magento setup:db-schema:upgrade
```

データベースのステータスを確認するには、次のように入力します

```bash
bin/magento setup:db:status
```
