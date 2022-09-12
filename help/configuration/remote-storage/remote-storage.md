---
title: リモートストレージの構成
description: オンプレミスのコマースアプリケーション用にリモートストレージモジュールを構成する方法を説明します。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---

# リモートストレージの構成

リモートストレージモジュールでは、メディアファイルを保存し、AWS S3 などのストレージサービスを使用して、永続的なリモートストレージコンテナにインポート/エクスポートのスケジュールを設定できます。 デフォルトでは、 [!DNL Commerce] アプリケーションは、アプリケーションを含むのと同じファイルシステムにメディアファイルを格納します。 これは複雑なマルチサーバ構成に対しては非効率で、リソースを共有する際にパフォーマンスが低下する可能性があります。 リモートストレージモジュールを使用すると、メディアファイルを `pub/media` 内のファイルのインポート/エクスポート `var` サーバー側の画像のサイズ変更を利用するためのリモートオブジェクトストレージのディレクトリ。

>[!INFO]
>
>リモートストレージは、バージョン 2.4.2 以降でのみ使用できます。 詳しくは、 [2.4.2 リリースノート](https://devdocs.magento.com/guides/v2.4/release-notes/open-source-2-4-2.html).

>[!INFO]
>
>リモートストレージモジュールには _制限_ クラウドインフラストラクチャ上のAdobe Commerceのサポート。 Adobeがサードパーティのストレージアダプタサービスを完全にトラブルシューティングできない。

![スキーマ画像](../../assets/configuration/remote-storage-schema.png)

## リモートストレージオプション

リモートストレージは、 `remote-storage` オプションを [`setup` CLI コマンド][setup]. この `remote-storage` オプションでは次の構文を使用します。

```text
--remote-storage-<parameter-name>="<parameter-value>"
```

この `parameter-name` は、特定のリモートストレージパラメーター名を参照します。 次の表に、リモートストレージの設定に使用できるパラメータを示します。

| コマンドラインパラメータ | パラメーター名 | 説明 | デフォルト値 |
|--- |--- |--- |--- |
| `remote-storage-driver` | ドライバ | アダプタ名<br>可能な値：<br>**ファイル**:リモートストレージを無効にし、ローカルファイルシステムを使用&#x200B;<br>**aws-s3**:以下を使用： [Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md) | なし |
| `remote-storage-bucket` | バケット | オブジェクトのストレージまたはコンテナ名 | なし |
| `remote-storage-prefix` | prefix | オプションのプレフィックス（オブジェクトストレージ内の場所） | 空 |
| `remote-storage-region` | 地域 | 地域名 | なし |
| `remote-storage-key` | アクセスキー | オプションのアクセスキー | 空 |
| `remote-storage-secret` | 秘密鍵 | オプションの秘密鍵 | 空 |

### ストレージアダプタ

デフォルトの格納場所は、ローカルファイルシステムにあります。 A _ストレージアダプタ_ では、ストレージサービスに接続して、任意の場所にファイルを保存できます。 [!DNL Commerce] は、次のストレージサービスの構成をサポートしています。

- [Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md)

## リモートストレージを有効にする

新しい [!DNL Commerce] をインストールするか、次を使用して既存の Commerce インスタンスに追加します。 `remote-storage` パラメーター名と値のペア `setup` CLI コマンド 最低限、ストレージを提供する必要があります `driver`, `bucket`、および `region`.

次の例では、米国でAWS S3 ストレージアダプターを使用してリモートストレージを有効にします。

- 新規インストール [!DNL Commerce] リモートストレージを使用

   ```bash
   bin/magento setup:install --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
   ```

- 既存のリモートストレージを有効にする [!DNL Commerce]

   ```bash
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
   ```

## 制限事項

リモートストレージとデータベースストレージの両方を同時に有効にすることはできません。 リモートストレージを使用している場合は、データベースストレージを無効にします。

```bash
bin/magento config:set system/media_storage_configuration/media_database 0
```

リモートストレージを有効にすると、確立された開発環境に影響を与える場合があります。 例えば、特定の PHP ファイル関数は期待どおりに動作しない場合があります。 ファイル操作に対する Commerce Framework の使用を適用する必要があります。

PHP の使用禁止のネイティブ関数のリストは、 [Magentoコーディング規格] リポジトリ。

## コンテンツを移行

特定のアダプタのリモートストレージを有効にした後、CLI を使用して既存のアダプタを移行できます _メディア_ ファイルをリモートストレージに保存します。

```bash
./magento2ce/bin/magento remote-storage:sync
```

>[!INFO]
>
>sync コマンドは、 `pub/media` ディレクトリ _not_ のインポート/エクスポートファイル `var` ディレクトリ。 詳しくは、 [予定されているインポート/エクスポート][import-export] 内 _Commerce 2.4 ユーザーガイド_.

<!-- link definitions -->

[import-export]: https://docs.magento.com/user-guide/system/data-scheduled-import-export.html
[Magentoコーディング規格]: https://github.com/magento/magento-coding-standard/blob/develop/Magento2/Sniffs/Functions/DiscouragedFunctionSniff.php
[setup]: ../../installation/tutorials/deployment.md
