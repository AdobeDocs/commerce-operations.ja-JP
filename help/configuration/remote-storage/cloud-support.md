---
title: クラウドインフラストラクチャー上のCommerceのリモートストレージ
description: クラウドインフラストラクチャー上でAdobe Commerceのリモートストレージを設定する方法については、ガイダンスを参照してください。
feature: Configuration, Cloud, Storage
exl-id: da352466-13f2-42e4-a589-3b0a89728467
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# クラウドインフラストラクチャー上のCommerceにリモートストレージを設定

で始まる `ece-tools` パッケージ 2002.1.5 では、環境変数を使用してリモート記憶域モジュールを有効にできますが、リモート記憶域モジュールには次の機能があります _制限付き_ クラウドインフラストラクチャー上のAdobe Commerceでのサポート。 Adobeがサードパーティ製ストレージアダプタサービスのトラブルシューティングを完全に行えない。

## 環境変数

この `REMOTE_STORAGE` 変数は、次の場合に使用されます [デプロイフェーズ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html) （クラウドインフラストラクチャプロジェクトの場合）

### `REMOTE_STORAGE`

- **デフォルト**—_未設定_
- **バージョン**—Commerce 2.4.2 以降

の設定 _ストレージアダプタ_ AWS S3 などのストレージサービスを使用して、永続的なリモートストレージコンテナにメディアファイルを保存する。 リモートストレージモジュールを有効にして、リソースを共有する必要がある、複雑なマルチサーバー設定を含むクラウドプロジェクトのパフォーマンスを向上させます。 次に、を使用したリモートストレージ設定の例を示します `.magento.env.yaml` ファイル：

```yaml
stage:
  deploy:
    REMOTE_STORAGE:
      driver: aws-s3 # Required
      prefix: cloud # Optional
      config:
        bucket: my-bucket # Required
        region: my-region # Required
        key: my-key # Optional
        secret: my-secret-key # Optional
```

### Cloud CLI での変数設定

を `REMOTE_STORAGE` 変数を [環境レベル変数](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html) 実稼動環境、ステージング環境および統合環境間でファイルが共有されないようにします。 環境レベルで変数を設定すると、統合環境でのリモートストレージの使用を除外するなど、一部の環境でのみリモートストレージを使用する柔軟性が得られます。

**Cloud CLI を使用してリモートストレージ変数を追加するには**:

```bash
magento-cloud variable:create --level environment --name REMOTE_STORAGE --json true --inheritable false --value '{"driver":"aws-s3","prefix":"uat","config":{"bucket":"aws-bucket-id","region":"eu-west-1","key":"optional-key","secret":"optional-secret"}}'
```

これにより、が作成されます `REMOTE_STORAGE` 指定した JSON 設定を持つ変数。 この `REMOTE_STORAGE` 変数は、JSON 文字列を受け取って、リモートストレージを設定します。 以下は JSON 設定の例です。

```json
{
  "driver": "aws-s3",
  "prefix": "uat",
  "config": {
    "bucket": "aws-bucket-id",
    "region": "aws-region-id",
    "key": "optional-key",
    "secret": "optional-secret"
  }
}
```

設定を作成してデプロイした後、デプロイメントログには、次のようなリモートストレージ設定に関する情報が含まれている必要があります `INFO: Remote storage driver set to: "aws-s3"`

### Project Web インターフェイスで変数を設定する

または、Project Web Interface を使用して、適切な環境に変数を追加することもできます。

**Project Web Interface を使用してリモート記憶域変数を追加するには**:

1. が含まれる _Project Web インターフェイス_&#x200B;左から「環境」を選択します。

1. 「」をクリックします **環境の設定** アイコン。

1. が含まれる _環境の設定_ を表示するには、 **変数** タブ。

1. クリック **変数を追加**.

1. が含まれる _名前_ フィールド、を入力 `REMOTE_STORAGE`

1. が含まれる _値_ フィールドに、JSON 設定を追加します。

1. を選択 **JSON 値** および **機密**；選択解除 **子環境で継承可能**.

1. クリック **変数を追加**.

### オプションの認証を使用

この `key` および `secret` はオプションです。 変数を作成する場合、を非表示にできます `key` および `secret` を選択します。 `sensitive` オプション。 この設定では、値は web インターフェイスには表示されません。 参照： [変数の表示](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html#visibility) が含まれる _クラウドインフラストラクチャー上のCommerce ガイド_.

別の認証方法を使用する場合は、を省略します `key` および `secret` json 設定から。 代替認証方法を設定し、サーバーが S3 バケットに対して許可されていることを確認します。

### リモートストレージの同期

リモート記憶域モジュールを有効にした後、現在のメディア ファイルをリモート ストアの場所に同期します。

**同期を開始するには**:

1. SSH を使用して、リモート記憶域が構成されたリモート環境にログインします。

1. 同期を開始します。

```bash
bin/magento remote-storage:sync 
```

## Fastly 設定

Adobe Commerce on cloud infrastructure プロジェクトでリモートストレージソリューションを使用する場合は、 [Amazon S3](https://docs.fastly.com/en/guides/amazon-s3) のガイダンス _Fastly_ fastly での画像の最適化がAWS S3 で動作することを確認するためのドキュメント。

準備が整っている [Fastly 資格情報](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#get-fastly-credentials). Pro プロジェクトでは、SSH を使用してサーバーに接続し、から Fastly 資格情報を取得します。 `/mnt/shared/fastly_tokens.txt` ファイル。 ステージング環境と実稼動環境には、一意の資格情報があります。 各環境の資格情報を取得する必要があります。

次のタスクを使用して、クラウドプロジェクト用のリモートストレージの設定を続行します。

1. の設定 [Fastly バックエンド統合](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/Edge-Modules/EDGE-MODULE-OTHER-CMS-INTEGRATION.md).

1. の VCL ロジックの作成 [AWS S3 認証](https://docs.fastly.com/en/guides/amazon-s3#using-an-amazon-s3-private-bucket).

1. の VCL ロジックの作成 [AWS S3 バケットに対するバックエンドリクエスト](https://developer.fastly.com/reference/vcl/variables/backend-connection/req-backend/).
