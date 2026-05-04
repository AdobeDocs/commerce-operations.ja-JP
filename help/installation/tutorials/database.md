---
title: データベーススキーマの作成
description: Adobe Commerce プロジェクトのデータベースを作成するには、次の手順に従います。
exl-id: 860c9918-44c4-4ef1-88a5-12614566307c
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---

# データベーススキーマの作成

このコマンドを実行する前に、[&#x200B; デプロイメント設定を作成または更新する必要があります](deployment.md)。

## データベースの設定とデータの追加

コマンドの使用状況：

```shell
bin/magento setup:db-schema:upgrade
```

データベースのステータスを表示するには、次のように入力します

```shell
bin/magento setup:db:status
```
