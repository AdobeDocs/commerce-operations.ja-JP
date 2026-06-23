---
title: AWS ElastiCacheでのRedisの設定
description: EC2上のAdobe CommerceでAWS ElastiCacheをRedis バックエンドとして使用する方法について説明します。 コマンドラインの設定、設定、検証について説明します。
feature: Configuration, Cache
autotag-review: '2026-06-22T21:54:39.355Z'
TQID: 'https://experienceleague.adobe.com/p4-Pyc3yWwokyFOAyAjN3r1Ic26brx83bPf-GZQNSN8'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: fbb1d92d5f8537e6f1436cd985af120114883df6
workflow-type: tm+mt
source-wordcount: 289
ht-degree: 0%

---


# AWS ElastiCacheでのRedisの設定

Commerce 2.4.3以降、Amazon EC2でホストされているインスタンスでは、ローカル Redis インスタンスの代わりにAWS ElastiCacheを使用できます。

>[!WARNING]
>
>このセクションは、Amazon EC2 VPCで動作するCommerce インスタンスにのみ適用されます。

## 前提条件

- **Create a Redis OSS serverless cache**- AWS Management Consoleから、EC2 インスタンスの同じリージョンとVPCにRedis キャッシュを作成します。 手順については、[AWS Elasticache ドキュメント &#x200B;](https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/GettingStarted.serverless-redis.step1.html)を参照してください。

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
1. ターミナルの[&#x200B; キャッシュ出力](#verify-connectivity)を確認します。
