---
title: データベーススキーマの作成
description: Adobe Commerce プロジェクトのデータベースを作成するには、次の手順に従います。
exl-id: 860c9918-44c4-4ef1-88a5-12614566307c
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%
---
# データベーススキーマの作成

このコマンドを実行する前に、[ デプロイメント設定を作成または更新する必要があります](deployment.md)。

## データベースの設定とデータの追加

コマンドの使用状況：

```shell
bin/magento setup:db-schema:upgrade
```

データベースのステータスを表示するには、次のように入力します

```shell
bin/magento setup:db:status
```
