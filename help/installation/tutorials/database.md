---
title: データベーススキーマの作成
description: 以下の手順に従って、Adobe CommerceまたはMagento Open Source用のデータベースを作成します。
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
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

データベースのステータスを確認するには、

```bash
bin/magento setup:db:status
```
