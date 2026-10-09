---
title: メッセージコンシューマーの設定
description: Adobe Commerce メッセージキューコンシューマーの動作を設定するには、次の手順に従います。
exl-id: df292301-f4bd-49df-a241-7467c35bf1d8
last-update: 2026-04-28
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
source-git-commit: a3c0eba7bdcd8017e88bdb4df1f45d77fe4bb351
workflow-type: tm+mt
source-wordcount: '65'
ht-degree: 0%
---
# メッセージコンシューマーの設定

このコマンドを実行する前に、次の&#x200B;*または*&#x200B;を実行する必要があります。アプリケーションを[ インストールする必要があります](../advanced.md):

* [デプロイメント設定の作成または更新](deployment.md)
* [データベーススキーマの作成](database.md)

## 消費者の動作の設定

コンシューマー動作の設定は、セットアップ関数内でキーと値のペアを送信することで行います。

```shell
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### パラメーターの説明

{{$include /help/_includes/cli-consumers.md}}

<!-- Last updated from includes: 2022-09-12 09:38:25 -->
