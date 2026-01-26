---
title: AWS ElastiCache を使用して Redis を設定します
description: EC2 でホストされるCommerce インスタンスの場合、ローカル Redis インスタンスの代わりにAWS ElastiCache を使用する方法を説明します。 コマンドラインのセットアップ、設定オプション、検証方法について説明します。
feature: Configuration, Cache
source-git-commit: b66479ee1350d92c1d59212283222e5068c263a6
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---


# AWS ElastiCache を使用して Redis を設定します

Commerce 2.4.3 以降、Amazon EC2 でホストされるインスタンスは、ローカル Redis インスタンスの代わりにAWS ElastiCache を使用する場合があります。

>[!WARNING]
>
>このセクションは、Amazon EC2 VPC 上で稼働するCommerce インスタンスにのみ適用されます。 オンプレミスのインストールでは機能しません。

## 前提条件

- **Redis OSS サーバーレスキャッシュの作成** - AWS Management Console から、EC2 インスタンスの同じリージョンおよびVPCに Redis キャッシュを作成します。 手順については、[AWS Elasticache ドキュメント &#x200B;](https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/GettingStarted.serverless-redis.step1.html) を参照してください。

- **EC2 Commerce インスタンスへの接続の確認**

   - EC2 インスタンスへの SSH 接続を開きます。
   - EC2 インスタンスに、Redis クライアントをインストールします。

     ```bash
     sudo apt-get install redis
     ```

   - EC2 セキュリティグループにインバウンド規則を追加します：タイプ `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - ElastiCache クラスターセキュリティ グループに受信規則を追加します：タイプ `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Redis CLI に接続します。

     ```bash
     redis-cli -h <ElastiCache Primary Endpoint host> -p <ElastiCache Primary Endpoint port>
     ```

### クラスターを使用するようにCommerceを設定します

Commerceでは、複数のタイプのキャッシュ設定をサポートしています。 一般に、キャッシュ設定はフロントエンドとバックエンドに分かれます。 フロントエンドキャッシュは `default` に分類され、あらゆるキャッシュタイプで使用されます。 パフォーマンスを向上させるには、カスタマイズするか、下位レベルのキャッシュに分割します。 一般的な Redis 設定は、デフォルトのキャッシュとページキャッシュを独自の Redis データベース（RDB）に分離することです。

`setup` コマンドを実行して、Redis エンドポイントを指定します。

Commerceを Redis 用にデフォルトキャッシュとして設定するには：

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=<ElastiCache Primary Endpoint host> --cache-backend-redis-port=<ElastiCache Primary Endpoint port> --cache-backend-redis-db=0
```

Commerceを Redis ページキャッシュ用に設定するには：

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=<ElastiCache Primary Endpoint host> --page-cache-redis-port=<ElastiCache Primary Endpoint port> --page-cache-redis-db=1
```

セッションストレージに Redis を使用するようにCommerceを設定するには：

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=<ElastiCache Primary Endpoint host> --session-save-redis-port=<ElastiCache Primary Endpoint port> --session-save-redis-log-level=4 --session-save-redis-db=2
```

## 接続の検証

**Commerceが ElastiCache と通信していることを確認するには**:

1. Commerce EC2 インスタンスへの SSH 接続を開きます。
1. Redis モニタを起動します。

   ```bash
   redis-cli -h <ElastiCache-Primary-Endpoint-host> -p <ElastiCache-Primary-Endpoint-port> monitor
   ```

1. Commerce UI でページを開きます。
1. ターミナルで [cache output](#verify-the-redis-connection) を確認します。
