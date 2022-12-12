---
title: クラウドインフラストラクチャ上のコマース用リモートストレージ
description: クラウドインフラストラクチャ上のAdobe Commerceのリモートストレージを設定する方法に関するガイダンスを参照してください。
source-git-commit: 0653d90d92e264b62fcc648f2b1307c013e9be54
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 0%

---


# クラウドインフラストラクチャ上のコマース用のリモートストレージの設定

次で始まる `ece-tools` パッケージ 2002.1.5 では、環境変数を使用してリモートストレージモジュールを有効にすることができます。ただし、リモート・ストレージ・モジュールには _制限_ クラウドインフラストラクチャ上のAdobe Commerceのサポート。 Adobeがサードパーティのストレージアダプタサービスを完全にトラブルシューティングできない。

## 環境変数

この `REMOTE_STORAGE` 変数は、 [導入段階](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html) クラウドインフラストラクチャプロジェクトの

### `REMOTE_STORAGE`

- **デフォルト**—_未設定_
- **バージョン**—Commerce 2.4.2 以降

の設定 _ストレージアダプタ_ AWS S3 などのストレージサービスを使用して、メディアファイルを永続的なリモートストレージコンテナに保存する場合。 リモートストレージモジュールを有効にして、リソースを共有する必要のある複雑なマルチサーバー構成を持つクラウドプロジェクトのパフォーマンスを向上させます。 次に、 `.magento.env.yaml` ファイル：

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

### Cloud CLI で変数を設定

を `REMOTE_STORAGE` 変数 [環境変数](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html) したがって、実稼動、ステージング、統合の各環境間でファイルが共有されなくなります。 環境レベルで変数を設定すると、リモートストレージの統合環境での使用を除外するなど、選択した環境でのみリモートストレージを使用する柔軟性が得られます。

**Cloud CLI を使用してリモートストレージ変数を追加するには**:

```bash
magento-cloud variable:create --level environment --name REMOTE_STORAGE --json true --inheritable false --value '{"driver":"aws-s3","prefix":"uat","config":{"bucket":"aws-bucket-id","region":"eu-west-1","key":"optional-key","secret":"optional-secret"}}'
```

これにより、 `REMOTE_STORAGE` 変数に指定された JSON 設定を入力します。 この `REMOTE_STORAGE` 変数は、JSON 文字列を受け取ってリモートストレージを設定します。 以下に、JSON の設定例を示します。

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

構成と展開を作成した後、展開ログには、リモートストレージ構成に関する情報が含まれる必要があります。例： `INFO: Remote storage driver set to: "aws-s3"`

### Project Web インターフェイスで変数を設定

または、Project Web インターフェイスを使用して、適切な環境に変数を追加できます。

**Project Web インターフェイスを使用してリモートストレージ変数を追加するには**:

1. 内 _Project Web インターフェイス_」で、左から環境を選択します。

1. 次をクリック： **環境の設定** アイコン

1. 内 _環境を設定_ ビューを開き、 **変数** タブをクリックします。

1. クリック **変数を追加**.

1. 内 _名前_ フィールドに入力 `env:REMOTE_STORAGE`

1. 内 _値_ 「 」フィールドで、JSON 設定を追加します。

1. 選択 **JSON 値** および **機密**;選択解除 **子環境によって継承可能**.

1. クリック **変数を追加**.

### オプションの認証を使用

この `key` および `secret` はオプションです。 変数を作成する際に、 `key` および `secret` 選択 `sensitive` オプション。 この設定では、値は Web インターフェイスに表示されません。 詳しくは、 [変数の表示](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html#visibility) 内 _Commerce on Cloud Infrastructure ガイド_.

別の認証方法を使用する場合は、 `key` および `secret` を JSON 設定から、 代替認証方法を設定し、サーバーが S3 バケットに対して承認されていることを確認します。

### リモートストレージを同期

リモートストレージモジュールを有効にした後、現在のメディアファイルをリモートストアの場所に同期します。

**同期を開始するには**:

1. SSH を使用して、リモートストレージを設定したリモート環境にログインします。

1. 同期を開始します。

```bash
bin/magento remote-storage:sync 
```

## Fastly 設定

リモートストレージソリューションをクラウドインフラストラクチャ上のAdobe Commerceプロジェクトで使用する場合は、 [Amazon S3](https://docs.fastly.com/en/guides/amazon-s3) 指導 _Fastly_ Fastly 画像の最適化がAWS S3 で確実に機能するようにするドキュメント。

準備を整えて [Fastly 認証情報](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#get-fastly-credentials). Pro プロジェクトでは、SSH を使用してサーバーに接続し、 `/mnt/shared/fastly_tokens.txt` ファイル。 ステージング環境と実稼動環境には、一意の資格情報が割り当てられます。 各環境の資格情報を取得する必要があります。

次のタスクを使用して、クラウドプロジェクトのリモートストレージの設定を続行します。

1. の設定 [Fastly のバックエンド統合](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/Edge-Modules/EDGE-MODULE-OTHER-CMS-INTEGRATION.md).

1. の VCL ロジックを作成 [AWS S3 認証](https://docs.fastly.com/en/guides/amazon-s3#using-an-amazon-s3-private-bucket).

1. の VCL ロジックを作成 [AWS S3 バケットに対するバックエンドリクエスト](https://developer.fastly.com/reference/vcl/variables/backend-connection/req-backend/).
