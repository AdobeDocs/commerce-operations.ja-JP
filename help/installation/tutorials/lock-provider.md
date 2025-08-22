---
title: ロックプロバイダーの設定
description: 次の手順に従って、Adobe Commerce デプロイメントで重複した cron ジョブと cron グループが実行されないようにします。
exl-id: c54e05b7-38fd-4731-bc77-a873b44d0ae8
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# ロックプロバイダーの設定

このコマンドを実行する前に、次の操作を行う必要があります *または* アプリケーションをインストールする必要があります [&#128279;](../advanced.md)。

* [デプロイメント設定の作成または更新](deployment.md)
* [データベーススキーマの作成](database.md)

## 安全なインストール

{{$include /help/_includes/secure-install.md}}

## ロックの設定

ロックプロバイダーを設定して、重複する cron ジョブや cron グループの起動を防ぎます。 （Adobe Commerce 2.2.x、2.2.5 以降および 2.3.3 以降が必要です）。

Adobe Commerceは、デフォルトでロックを保存するためにこのデータベースを使用します。 サーバーに複数のノードがある場合は、Zookeeper をロックプロバイダーとして使用することをお勧めします。

クラウドインフラストラクチャー上でAdobe Commerceを実行している場合は、ロックプロバイダーを設定する必要はありません。 アプリケーションは、プロビジョニングプロセス中に、Pro プロジェクトのファイルロックプロバイダを設定します。 [ クラウド変数 ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud) を参照してください。

### コマンドの使用法

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### パラメーターの説明

| 名前 | 値 | 必須？ |
|--- |--- |--- |
| `--lock-provider` | プロバイダ名のロック：`db`、`zookeeper`、または `file`。<br><br> デフォルトのロックプロバイダー：`db` | 不可 |
| `--lock-db-prefix` | `db` ロックプロバイダーの使用時にロックの競合を回避するための、特定の db プレフィックスです。<br><br> デフォルト値：`NULL` | 不可 |
| `--lock-zookeeper-host` | `zookeeper` ロックプロバイダーを使用する場合に Zookeeper クラスターに接続するホストおよびポート。<br><br> 例：`127.0.0.1:2181` | はい（`--lock-provider=zookeeper` を設定した場合） |
| `--lock-zookeeper-path` | Zookeeper がロックを保存するパス。<br><br> デフォルトパスは `/magento/locks` です。 | 不可 |
| `--lock-file-path` | ファイルのロックが保存されるパス。 | はい（`--lock-provider=file` を設定した場合） |

<!-- Last updated from includes: 2022-09-08 11:33:05 -->
