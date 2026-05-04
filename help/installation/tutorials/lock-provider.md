---
title: ロックプロバイダーの設定
description: Adobe Commerceのデプロイメントで、重複するcron ジョブとcron グループが実行されないようにするには、次の手順に従います。
exl-id: c54e05b7-38fd-4731-bc77-a873b44d0ae8
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# ロックプロバイダーの設定

このコマンドを実行する前に、次の&#x200B;*または*&#x200B;を実行する必要があります。アプリケーションを[ インストールする必要があります](../advanced.md):

* [デプロイメント設定の作成または更新](deployment.md)
* [データベーススキーマの作成](database.md)

## 安全なインストール

{{$include /help/_includes/secure-install.md}}

## ロックの設定

重複するcron ジョブとcron グループの起動を防ぐようにロックプロバイダーを設定します。 （Adobe Commerce 2.2.x、2.2.5以降、および2.3.3以降が必要です）。

Adobe Commerceでは、デフォルトでデータベースを使用してロックを保存します。 サーバーに複数のノードがある場合は、ロックプロバイダーとしてZookeeperを使用することをお勧めします。

Adobe Commerceをクラウドインフラストラクチャ上で実行している場合は、ロックプロバイダーの設定を行う必要はありません。 アプリケーションは、プロビジョニングプロセス中にPro プロジェクトのファイルロックプロバイダーを設定します。 [ クラウド変数](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud)を参照してください。

### コマンドの使用

```shell
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### パラメーターの説明

| 名前 | 値 | 必要ですか？ |
|--- |--- |--- |
| `--lock-provider` | ロックプロバイダー名：`db`、`zookeeper`または`file`。<br><br> デフォルトのロックプロバイダー：`db` | いいえ |
| `--lock-db-prefix` | `db` ロックプロバイダーの使用時にロックの競合を回避するための特定のdb プレフィックス。<br><br> デフォルト値：`NULL` | いいえ |
| `--lock-zookeeper-host` | `zookeeper` ロックプロバイダーを使用する際に、Zookeeper クラスターに接続するためのホストとポート。<br><br>例：`127.0.0.1:2181` | はい、`--lock-provider=zookeeper`を設定した場合 |
| `--lock-zookeeper-path` | Zookeeperがロックを保存するパス。<br><br> デフォルトパスは`/magento/locks`です | いいえ |
| `--lock-file-path` | ファイルロックが保存されるパス。 | はい、`--lock-provider=file`を設定した場合 |

<!-- Last updated from includes: 2022-09-08 11:33:05 -->
