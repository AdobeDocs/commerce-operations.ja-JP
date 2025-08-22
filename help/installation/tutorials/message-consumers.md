---
title: メッセージコンシューマーの設定
description: 次の手順に従って、Adobe Commerce メッセージキューコンシューマーの動作を設定します。
exl-id: df292301-f4bd-49df-a241-7467c35bf1d8
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '65'
ht-degree: 0%

---

# メッセージコンシューマーの設定

このコマンドを実行する前に、次の操作を行う必要があります *または* アプリケーションをインストールする必要があります [](../advanced.md)。

* [デプロイメント設定の作成または更新](deployment.md)
* [データベーススキーマの作成](database.md)

## コンシューマー行動の設定

コンシューマーの動作の設定は、セットアップ関数内でキーと値のペアを送信することで行われます。

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### パラメーターの説明

{{$include /help/_includes/cli-consumers.md}}

<!-- Last updated from includes: 2022-09-12 09:38:25 -->
