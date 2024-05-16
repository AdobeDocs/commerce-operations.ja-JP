---
title: リモートストレージの設定
description: オンプレミスのCommerce アプリケーション用にリモートストレージモジュールを設定する方法について説明します。
feature: Configuration, Storage
exl-id: 0428f889-46b0-44c9-8bd9-98c1be797011
source-git-commit: 2a45fe77d5a6fac089ae2c55d0ad047064dd07b0
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---

# リモートストレージの設定

リモートストレージモジュールは、メディアファイルを保存し、AWS S3 などのストレージサービスを使用して、永続的なリモートストレージコンテナでインポートとエクスポートをスケジュールするオプションを提供します。 デフォルトでは、Adobe Commerce アプリケーションは、アプリケーションを含んでいるのと同じファイルシステムにメディアファイルを保存します。 これは、複雑なマルチサーバ構成では非効率的であり、リソースを共有する際のパフォーマンスが低下する可能性があります。 リモート記憶域モジュールを使用すると、メディア ファイルを `pub/media` のディレクトリおよびインポート/エクスポートファイル `var` サーバーサイドの画像サイズ変更を利用するためのリモートオブジェクトストレージのディレクトリ。

>[!INFO]
>
>リモートストレージは、Commerce バージョン 2.4.2 以降でのみ使用できます。 を参照してください。 [2.4.2 リリースノート](https://devdocs.magento.com/guides/v2.4/release-notes/open-source-2-4-2.html).

>[!INFO]
>
>リモート記憶域モジュールに次の機能があります _制限付き_ クラウドインフラストラクチャー上のAdobe Commerceでのサポート。 Adobeがサードパーティ製ストレージアダプタサービスのトラブルシューティングを完全に行えない。 参照： [クラウドインフラストラクチャー上のCommerceにリモートストレージを設定](cloud-support.md) クラウドプロジェクトにリモートストレージを実装する際のガイダンス。

![スキーマ画像](../../assets/configuration/remote-storage-schema.png)

## リモートストレージオプション

リモートストレージを設定するには、 `remote-storage` オプションと [`setup` CLI コマンド](../../installation/tutorials/deployment.md). この `remote-storage` オプションでは、次の構文を使用します。

```text
--remote-storage-<parameter-name>="<parameter-value>"
```

この `parameter-name` は、特定のリモートストレージパラメーター名を参照します。 次の表に、リモートストレージの設定に使用できるパラメーターを示します。

| コマンドラインパラメーター | パラメーター名 | 説明 | デフォルト値 |
|--- |--- |--- |--- |
| `remote-storage-driver` | ドライバ | アダプター名<br>使用可能な値：<br>**ファイル**：リモートストレージを無効にし、ローカルファイルシステムを使用します。<br>**aws-s3**：を使用します [Amazon Simple Storage Service （Amazon S3）](remote-storage-aws-s3.md) | なし |
| `remote-storage-bucket` | バケット | オブジェクトストレージまたはコンテナ名 | なし |
| `remote-storage-prefix` | prefix | オプションのプレフィックス（オブジェクトストレージ内の場所） | 空 |
| `remote-storage-region` | 地域 | 地域名 | なし |
| `remote-storage-key` | アクセスキー | オプションのアクセスキー | 空 |
| `remote-storage-secret` | 秘密鍵 | オプションの秘密鍵 | 空 |

### ストレージアダプタ

デフォルトのストレージの場所は、ローカルファイルシステムにあります。 A _ストレージアダプタ_ を使用すると、ストレージサービスに接続し、ファイルを任意の場所に保存できます。 [!DNL Commerce] では、次のストレージサービスの設定をサポートしています。

- [Amazon Simple Storage Service （Amazon S3）](remote-storage-aws-s3.md)

## リモート記憶域を有効にする

リモートストレージは、Adobe Commerceのインストール時にインストールすることも、既存のCommerce インスタンスに追加することもできます。 次の例は、一連のを使用した各メソッドを示しています `remote-storage` Commerceのパラメーター `setup` CLI コマンド。 最小で、ストレージを提供する必要があります `driver`, `bucket`、および `region`.

- 例：Commerceとリモートストレージのインストール

  ```bash
  bin/magento setup:install --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
  ```

- 例：既存のCommerceでリモートストレージを有効にする

  ```bash
  bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
  ```

>[!TIP]
>
>クラウドインフラストラクチャー上のAdobe Commerceについては、以下を参照してください。 [クラウドインフラストラクチャー上のCommerceにリモートストレージを設定](cloud-support.md).

## 制限事項

リモート記憶域とデータベース記憶域の両方を同時に有効にすることはできません。 リモートストレージを使用している場合は、データベースストレージを無効にします。

```bash
bin/magento config:set system/media_storage_configuration/media_database 0
```

リモートストレージを有効にすると、確立された開発エクスペリエンスに影響を与える可能性があります。 例えば、ある PHP ファイル関数が期待どおりに動作しない場合があります。 ファイル操作にCommerce Framework を強制的に使用する必要があります。

禁止されている PHP ネイティブ関数のリストは、以下で入手できます。 [magento-coding-standard リポジトリ][code-standard].

## コンテンツを移行

特定のアダプタに対してリモート記憶域を有効にした後は、CLI を使用して既存のものを移行できます _media_ リモートストレージへのファイル。

```bash
./magento2ce/bin/magento remote-storage:sync
```

>[!INFO]
>
>sync コマンドは、内のファイルのみを移行します。 `pub/media` ディレクトリ、 _ではない_ でのファイルのインポート/エクスポート `var` ディレクトリ。 参照： [スケジュールされた読み込み/書き出し](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-scheduled-import-export.html) が含まれる _Commerce 2.4 ユーザーガイド_.

<!-- link definitions -->

[import-export]: https://docs.magento.com/user-guide/system/data-scheduled-import-export.html
[code-standard]: https://github.com/magento/magento-coding-standard/blob/develop/Magento2/Sniffs/Functions/DiscouragedFunctionSniff.php
