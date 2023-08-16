---
title: データベーススキーマの作成
description: 以下の手順に従って、Adobe CommerceまたはMagento Open Source用のデータベースを作成します。
exl-id: 860c9918-44c4-4ef1-88a5-12614566307c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '52'
ht-degree: 0%

---

# データベーススキーマの作成

このコマンドを実行する前に、次の操作を行う必要があります。 [デプロイメント設定を作成または更新する](deployment.md).

## データベースの設定とデータの追加

コマンドの使用：

```bash
bin/magento setup:db-schema:upgrade
```

データベースのステータスを確認するには、「

```bash
bin/magento setup:db:status
```
