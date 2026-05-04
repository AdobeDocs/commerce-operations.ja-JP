---
title: クラウドインフラストラクチャ上のCommerceのリモートストレージ
description: クラウドインフラストラクチャ上にAdobe Commerceのリモートストレージを設定する方法に関するガイダンスを参照してください。
feature: Configuration, Cloud, Storage
exl-id: da352466-13f2-42e4-a589-3b0a89728467
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '667'
ht-degree: 0%

---

# Commerce on Cloud インフラストラクチャのリモートストレージの設定

`ece-tools` パッケージ 2002.1.5以降では、環境変数を使用してリモートストレージモジュールを有効にできますが、リモートストレージモジュールでは、Adobe Commerce on cloud infrastructureで&#x200B;_制限_&#x200B;がサポートされています。 Adobeでは、サードパーティ製ストレージアダプターサービスのトラブルシューティングを完全に実行できません。

## 環境変数

`REMOTE_STORAGE`変数は、クラウドインフラストラクチャプロジェクトの[ デプロイメントフェーズ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html)中に使用されます。

### `REMOTE_STORAGE`

- **既定**—_設定なし_
- **バージョン** - Commerce 2.4.2以降

AWS S3などのストレージサービスを使用して、永続的なリモートストレージコンテナにメディアファイルを保存するように&#x200B;_ストレージアダプタ_&#x200B;を設定します。 リモートストレージモジュールを有効にして、リソースを共有する必要がある複雑なマルチサーバー設定を使用して、クラウドプロジェクトのパフォーマンスを向上させます。 次に、`.magento.env.yaml` ファイルを使用したリモートストレージ設定の例を示します。

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

### Cloud CLIでの変数の設定

実稼動環境、ステージング環境、統合環境間でファイルが共有されないように、`REMOTE_STORAGE`変数を[環境レベル変数](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html)として設定します。 環境レベルで変数を設定すると、リモートストレージの統合環境の使用を除外するなど、一部の環境でリモートストレージのみを使用する柔軟性が得られます。

**Cloud CLI**&#x200B;を使用してリモートストレージ変数を追加するには：

```shell
magento-cloud variable:create --level environment --name REMOTE_STORAGE --json true --inheritable false --value '{"driver":"aws-s3","prefix":"uat","config":{"bucket":"aws-bucket-id","region":"eu-west-1","key":"optional-key","secret":"optional-secret"}}'
```

これにより、指定されたJSON設定で`REMOTE_STORAGE`変数が作成されます。 `REMOTE_STORAGE`変数は、JSON文字列を使用してリモートストレージを設定します。 次に、JSON設定の例を示します。

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

設定を作成してデプロイした後、デプロイメントログには、リモートストレージ設定（例：`INFO: Remote storage driver set to: "aws-s3"`）に関する情報が含まれている必要があります

### Project Web Interfaceで変数を設定

または、Project Web Interfaceを使用して、変数を適切な環境に追加することもできます。

**Project Web Interface**&#x200B;を使用してリモート ストレージ変数を追加するには：

1. _Project Web Interface_&#x200B;で、左側から環境を選択します。

1. **環境の設定** アイコンをクリックします。

1. _環境の設定_ ビューで、「**変数**」タブをクリックします。

1. 「**変数を追加**」をクリックします。

1. _名前_ フィールドに、`REMOTE_STORAGE`と入力します

1. _値_ フィールドにJSON設定を追加します。

1. **JSON値**&#x200B;と&#x200B;**機密性**&#x200B;を選択し、**子環境による継承**&#x200B;の選択を解除します。

1. 「**変数を追加**」をクリックします。

### オプションの認証を使用

`key`と`secret`はオプションです。 変数を作成する場合、`sensitive` オプションを選択して`key`と`secret`を非表示にできます。 この設定では、値はweb インターフェイスに表示されません。 _Commerce on Cloud Infrastructure ガイド_&#x200B;の[変数表示](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html#visibility)を参照してください。

別の認証方法を使用する場合は、JSON設定から`key`と`secret`を省略します。 別の認証方法を設定し、サーバーがS3 バケットに対して許可されていることを確認します。

### リモートストレージの同期

リモートストレージモジュールを有効にした後、現在のメディアファイルをリモートストアの場所に同期します。

**同期を開始するには**:

1. SSHを使用して、リモートストレージが設定されたリモート環境にログインします。

1. 同期を開始します。

```shell
bin/magento remote-storage:sync 
```

## Fastly設定

Adobe Commerce on cloud インフラストラクチャプロジェクトでリモートストレージソリューションを使用する場合は、_Fastly_ ドキュメントの[Amazon S3](https://docs.fastly.com/en/guides/amazon-s3) ガイダンスを使用して、Fastly Image OptimizationがAWS S3で動作することを確認してください。

[Fastlyの資格情報](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#get-fastly-credentials)を使用して準備してください。 Pro プロジェクトでは、SSHを使用してサーバーに接続し、`/mnt/shared/fastly_tokens.txt` ファイルからFastlyの資格情報を取得します。 ステージング環境と実稼動環境には一意の資格情報があります。 各環境の資格情報を取得する必要があります。

次のタスクを使用して、クラウドプロジェクトのリモートストレージの設定を続行します。

1. [Fastly バックエンド統合](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/Edge-Modules/EDGE-MODULE-OTHER-CMS-INTEGRATION.md)を設定します。

1. [AWS S3認証](https://docs.fastly.com/en/guides/amazon-s3#using-an-amazon-s3-private-bucket)のVCL ロジックを作成します。

1. AWS S3 バケット ](https://developer.fastly.com/reference/vcl/variables/backend-connection/req-backend/)に対する[ バックエンドリクエストのVCL ロジックを作成します。
