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

`ece-tools` パッケージ 2002.1.5 以降、環境変数を使用してリモートストレージモジュールを有効にできますが、クラウドインフラストラクチャ上のAdobe Commerceでは、リモートストレージモジュールがサポートされます _制限あり_。 Adobeが、サードパーティのストレージアダプタサービスのトラブルシューティングを完全に行えない。

## 環境変数

`REMOTE_STORAGE` 変数は、クラウドインフラストラクチャプロジェクトの [ デプロイフェーズ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html) で使用されます。

### `REMOTE_STORAGE`

- **Default**—_設定なし_
- **バージョン** - Commerce 2.4.2 以降

_ストレージアダプタ_ を設定して、AWS S3 などのストレージサービスを使用して、永続的なリモートストレージコンテナにメディアファイルを保存します。 リモートストレージモジュールを有効にして、リソースを共有する必要がある、複雑なマルチサーバー設定を含むクラウドプロジェクトのパフォーマンスを向上させます。 次に、`.magento.env.yaml` ファイルを使用したリモートストレージ設定の例を示します。

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

`REMOTE_STORAGE` 変数を [ 環境レベル変数 ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html) として設定して、実稼動環境、ステージング環境および統合環境でファイルが共有されないようにします。 環境レベルで変数を設定すると、統合環境でのリモートストレージの使用を除外するなど、一部の環境でのみリモートストレージを使用する柔軟性が得られます。

**Cloud CLI を使用してリモートストレージ変数を追加するには**:

```bash
magento-cloud variable:create --level environment --name REMOTE_STORAGE --json true --inheritable false --value '{"driver":"aws-s3","prefix":"uat","config":{"bucket":"aws-bucket-id","region":"eu-west-1","key":"optional-key","secret":"optional-secret"}}'
```

これにより、指定された JSON 設定を持つ `REMOTE_STORAGE` 変数が作成されます。 `REMOTE_STORAGE` 変数は、JSON 文字列を受け取って、リモートストレージを設定します。 以下は JSON 設定の例です。

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

設定を作成してデプロイした後、デプロイメントログには、リモートストレージの設定に関する情報（`INFO: Remote storage driver set to: "aws-s3"` など）を含める必要があります。

### Project Web インターフェイスで変数を設定する

または、Project Web Interface を使用して、適切な環境に変数を追加することもできます。

**Project Web Interface を使用してリモート記憶域変数を追加するには**:

1. _Project Web インターフェイス_ で、左側から環境を選択します。

1. **環境を設定** アイコンをクリックします。

1. _環境を設定_ ビューで、「**変数**」タブをクリックします。

1. **変数を追加** をクリックします。

1. 「_名前_」フィールドに「`REMOTE_STORAGE`」と入力します

1. 「_値_」フィールドに JSON 設定を追加します。

1. **JSON 値** および **機密** を選択し、**子環境によって継承可能** の選択を解除します。

1. **変数を追加** をクリックします。

### オプションの認証を使用

`key` と `secret` はオプションです。 変数を作成する場合は、「`key`」オプションを選択して、`secret` と `sensitive` を非表示にできます。 この設定では、値は web インターフェイスには表示されません。 [2}Cloud Infrastructure 上のCommerce ガイド ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html#visibility) の変数の表示 _を参照してください。_

別の認証方法を使用する場合は、`key` と `secret` を JSON 設定から削除します。 代替認証方法を設定し、サーバーが S3 バケットに対して許可されていることを確認します。

### リモートストレージの同期

リモート記憶域モジュールを有効にした後、現在のメディア ファイルをリモート ストアの場所に同期します。

**同期を開始するには**:

1. SSH を使用して、リモート記憶域が構成されたリモート環境にログインします。

1. 同期を開始します。

```bash
bin/magento remote-storage:sync 
```

## Fastly 設定

Adobe Commerce on cloud infrastructure プロジェクトでリモートストレージソリューションを使用する場合は、[Fastly](https://docs.fastly.com/en/guides/amazon-s3) ドキュメントの _Amazon S3_ ガイダンスを使用して、Fastly Image Optimization がAWS S3 で動作することを確認してください。

[Fastly 資格情報 ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#get-fastly-credentials) を使用して準備します。 Pro プロジェクトでは、SSH を使用してサーバーに接続し、`/mnt/shared/fastly_tokens.txt` ファイルから Fastly 資格情報を取得します。 ステージング環境と実稼動環境には、一意の資格情報があります。 各環境の資格情報を取得する必要があります。

次のタスクを使用して、クラウドプロジェクト用のリモートストレージの設定を続行します。

1. [Fastly バックエンド統合 ](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/Edge-Modules/EDGE-MODULE-OTHER-CMS-INTEGRATION.md) を設定します。

1. [AWS S3 認証 ](https://docs.fastly.com/en/guides/amazon-s3#using-an-amazon-s3-private-bucket) の VCL ロジックを作成します。

1. [AWS S3 バケットへのバックエンドリクエスト ](https://developer.fastly.com/reference/vcl/variables/backend-connection/req-backend/) 用の VCL ロジックを作成します。
