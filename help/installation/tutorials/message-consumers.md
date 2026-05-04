---
title: メッセージコンシューマーの設定
description: Adobe Commerce メッセージキューコンシューマーの動作を設定するには、次の手順に従います。
exl-id: df292301-f4bd-49df-a241-7467c35bf1d8
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
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
