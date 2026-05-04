---
title: AWS ElastiCacheでのRedisの設定
description: EC2でホストされているCommerce インスタンスの場合、ローカル Redis インスタンスの代わりにAWS ElastiCacheを使用する方法について説明します。 コマンドラインのセットアップ、設定オプション、検証手法について説明します。
feature: Configuration, Cache
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---


# AWS ElastiCacheでのRedisの設定

Commerce 2.4.3以降、Amazon EC2でホストされているインスタンスでは、ローカル Redis インスタンスの代わりにAWS ElastiCacheを使用できます。

>[!WARNING]
>
>このセクションは、Amazon EC2 VPCで動作するCommerce インスタンスにのみ適用されます。 オンプレミスのインストールでは機能しません。

## 前提条件

- **Create a Redis OSS serverless cache**- AWS Management Consoleから、EC2 インスタンスの同じリージョンとVPCにRedis キャッシュを作成します。 手順については、[AWS Elasticache ドキュメント ](https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/GettingStarted.serverless-redis.step1.html)を参照してください。

- **EC2 Commerce インスタンスへの接続を確認する**

   - EC2 インスタンスへのSSH接続を開きます
   - EC2 インスタンスで、Redis クライアントをインストールします。

     ```shell
     sudo apt-get install redis
     ```

   - EC2 セキュリティグループにインバウンドルールを追加します：タイプ `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - ElastiCache Cluster セキュリティグループにインバウンドルールを追加します：タイプ `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Redis CLIに接続します。

     ```shell
     redis-cli -h <ElastiCache Primary Endpoint host> -p <ElastiCache Primary Endpoint port>
     ```

### クラスターを使用するようにCommerceを設定する

Commerceは、複数のタイプのキャッシュ設定をサポートしています。 一般的に、キャッシュ設定はフロントエンドとバックエンドに分割されます。 フロントエンド キャッシュは`default`に分類され、任意のキャッシュ タイプに使用されます。 カスタマイズしたり、下位レベルのキャッシュに分割したりすることで、パフォーマンスを向上させることができます。 共通のRedis設定は、デフォルトのキャッシュとページキャッシュを独自のRedis Database （RDB）に分離することです。

`setup` コマンドを実行して、Redis エンドポイントを指定します。

Redis用Commerceをデフォルトのキャッシュとして設定するには：

```shell
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=<ElastiCache Primary Endpoint host> --cache-backend-redis-port=<ElastiCache Primary Endpoint port> --cache-backend-redis-db=0
```

Redis ページキャッシュ用にCommerceを設定するには：

```shell
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=<ElastiCache Primary Endpoint host> --page-cache-redis-port=<ElastiCache Primary Endpoint port> --page-cache-redis-db=1
```

セッションストレージにRedisを使用するようにCommerceを設定するには：

```shell
bin/magento setup:config:set --session-save=redis --session-save-redis-host=<ElastiCache Primary Endpoint host> --session-save-redis-port=<ElastiCache Primary Endpoint port> --session-save-redis-log-level=4 --session-save-redis-db=2
```

## 接続性の確認

**CommerceがElastiCacheと通信していることを確認するには**:

1. Commerce EC2 インスタンスへのSSH接続を開きます。
1. Redis モニターを起動します。

   ```shell
   redis-cli -h <ElastiCache-Primary-Endpoint-host> -p <ElastiCache-Primary-Endpoint-port> monitor
   ```

1. Commerce UIでページを開きます。
1. ターミナルの[ キャッシュ出力](#verify-the-redis-connection)を確認します。
