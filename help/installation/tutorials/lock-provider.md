---
title: ロックプロバイダーの設定
description: 次の手順に従って、Adobe CommerceまたはMagento Open Sourceのデプロイメントで重複した cron ジョブおよび cron グループが実行されないようにします。
exl-id: c54e05b7-38fd-4731-bc77-a873b44d0ae8
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# ロックプロバイダーの設定

このコマンドを実行する前に、次の操作を行う必要があります *または* あなたは必要です [アプリケーションのインストール](../advanced.md):

* [デプロイメント設定の作成または更新](deployment.md)
* [データベーススキーマの作成](database.md)

## 安全なインストール

{{$include /help/_includes/secure-install.md}}

## ロックの設定

ロックプロバイダーを設定して、重複する cron ジョブや cron グループの起動を防ぎます。 （Adobe CommerceまたはMagento Open Source 2.2.x、2.2.5 以降および 2.3.3 以降が必要です）。

Adobe Commerceは、デフォルトでロックを保存するためにこのデータベースを使用します。 サーバーに複数のノードがある場合は、Zookeeper をロックプロバイダーとして使用することをお勧めします。

クラウドインフラストラクチャー上でAdobe Commerceを実行している場合は、ロックプロバイダーを設定する必要はありません。 アプリケーションは、プロビジョニングプロセス中に、Pro プロジェクトのファイルロックプロバイダを設定します。 参照： [クラウド変数](https://devdocs.magento.com/cloud/env/variables-cloud.html).

### コマンドの使用法

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### パラメーターの説明

| 名前 | 値 | 必須？ |
|--- |--- |--- |
| `--lock-provider` | プロバイダ名のロック： `db`, `zookeeper`、または `file`.<br><br>デフォルトのロックプロバイダーは次のとおりです。 `db` | 不可 |
| `--lock-db-prefix` | を使用する際にロックの競合を回避するための特定の db プレフィックス `db` プロバイダをロックします。<br><br>デフォルト値は次のとおりです。 `NULL` | 不可 |
| `--lock-zookeeper-host` | を使用するときに Zookeeper クラスターに接続するホストおよびポート `zookeeper` プロバイダをロックします。<br><br>例： `127.0.0.1:2181` | はい（設定する場合） `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | Zookeeper がロックを保存するパス。<br><br>デフォルトのパスはです。 `/magento/locks` | 不可 |
| `--lock-file-path` | ファイルのロックが保存されるパス。 | はい（設定する場合） `--lock-provider=file` |
