---
title: メッセージコンシューマーの設定
description: 次の手順に従って、Adobe CommerceまたはメッセージキューコンシューマーのMagento Open Sourceを設定します。
exl-id: df292301-f4bd-49df-a241-7467c35bf1d8
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 0%

---

# メッセージコンシューマーの設定

このコマンドを実行する前に、次の操作を行う必要があります *または* 必ず [アプリケーションのインストール](../advanced.md):

* [デプロイメント設定を作成または更新する](deployment.md)
* [データベーススキーマの作成](database.md)

## 消費者行動の設定

消費者行動の設定は、設定関数内でキーと値のペアを送信することでおこなわれます。

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### パラメーターの説明

{{$include /help/_includes/cli-consumers.md}}
