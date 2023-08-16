---
title: ロックプロバイダーの設定
description: 次の手順に従って、Adobe CommerceまたはMagento Open Sourceのデプロイメントで重複する cron ジョブや cron グループが実行されないようにします。
exl-id: c54e05b7-38fd-4731-bc77-a873b44d0ae8
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# ロックプロバイダーの設定

このコマンドを実行する前に、次の操作を行う必要があります *または* 必ず [アプリケーションのインストール](../advanced.md):

* [デプロイメント設定を作成または更新する](deployment.md)
* [データベーススキーマの作成](database.md)

## 安全なインストール

{{$include /help/_includes/secure-install.md}}

## ロックの設定

ロックプロバイダーを設定して、重複する Cron ジョブと Cron グループが起動されないようにします。 (Adobe CommerceまたはMagento Open Source2.2.x、2.2.5 以降、2.3.3 以降が必要 )。

Adobe CommerceとMagento Open Sourceは、デフォルトで、データベースを使用してロックを保存します。 サーバーに複数のノードがある場合は、 Zookeeper をロックプロバイダーとして使用することをお勧めします。

クラウドインフラストラクチャ上でAdobe Commerceを実行している場合は、ロックプロバイダーの設定を構成する必要はありません。 プロビジョニングプロセス中に、Pro プロジェクトのファイルロックプロバイダーが設定されます。 詳しくは、 [クラウド変数](https://devdocs.magento.com/cloud/env/variables-cloud.html).

### コマンドの使用

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### パラメーターの説明

| 名前 | 値 | 必須？ |
|--- |--- |--- |
| `--lock-provider` | プロバイダー名をロック： `db`, `zookeeper`または `file`.<br><br>デフォルトのロックプロバイダーは次のとおりです。 `db` | いいえ |
| `--lock-db-prefix` | を使用する際にロックの競合を避けるための特定の db プレフィックス `db` プロバイダをロックします。<br><br>デフォルト値は次のとおりです。 `NULL` | いいえ |
| `--lock-zookeeper-host` | Zookeeper クラスタに接続するホストとポート ( `zookeeper` プロバイダをロックします。<br><br>例： `127.0.0.1:2181` | はい、 `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | Zookeeper がロックを保存するパス。<br><br>デフォルトのパスは次のとおりです。 `/magento/locks` | いいえ |
| `--lock-file-path` | ファイルのロックが保存されるパス。 | はい、 `--lock-provider=file` |
