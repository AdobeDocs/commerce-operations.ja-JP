---
title: リモートストレージの設定
description: オンプレミスのCommerce アプリケーション用にリモートストレージモジュールを設定する方法について説明します。
feature: Configuration, Storage
exl-id: 0428f889-46b0-44c9-8bd9-98c1be797011
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---

# リモートストレージの設定

リモートストレージモジュールは、メディアファイルを保存し、AWS S3 などのストレージサービスを使用して、永続的なリモートストレージコンテナでインポートとエクスポートをスケジュールするオプションを提供します。

デフォルトでは、Adobe Commerce アプリケーションは、アプリケーションを含んでいるのと同じファイルシステムにメディアファイルを保存します。 これは、複雑なマルチサーバ構成では非効率的であり、リソースを共有する際のパフォーマンスが低下する可能性があります。 リモート記憶域モジュールを使用すると、サーバー側のイメージのサイズ変更を利用して、メディア ファイルを `pub/media` ディレクトリに格納し、インポート/エクスポート ファイルをリモート オブジェクト ストレージの `var` ディレクトリに格納できます。

>[!BEGINSHADEBOX]

リモート記憶域 _とデータベース記憶域_ の両方を同時に有効にすることはできません。 リモート記憶域を有効にする前に、データベース記憶域を無効にしてください。

```bash
bin/magento config:set system/media_storage_configuration/media_database 0
```

リモートストレージを有効にすると、確立された開発エクスペリエンスに影響を与える可能性があります。 例えば、ある PHP ファイル関数が期待どおりに動作しない場合があります。 ファイル操作にCommerce Framework を強制的に使用する必要があります。 禁止されている PHP のネイティブ関数のリストは、[magento-coding-standard](https://github.com/magento/magento-coding-standard/blob/develop/Magento2/Sniffs/Functions/DiscouragedFunctionSniff.php) リポジトリで入手できます。

>[!ENDSHADEBOX]

>[!INFO]
>
>- リモートストレージは、Commerce バージョン 2.4.2 以降でのみ使用できます。 [2.4.2 リリースノート &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/magento-open-source/2-4-2) を参照してください。
>
>- リモートストレージモジュールは、クラウドインフラストラクチャ上のAdobe Commerceで _制限_ サポートされています。 Adobeが、サードパーティのストレージアダプタサービスのトラブルシューティングを完全に行えない。 クラウドプロジェクトにリモートストレージを実装する方法については、[&#x200B; クラウドインフラストラクチャ上のCommerceのリモートストレージの設定 &#x200B;](cloud-support.md) を参照してください。

![&#x200B; ローカルストレージとクラウドストレージの関係を示すリモートストレージ設定スキーマ図 &#x200B;](../../assets/configuration/remote-storage-schema.png)

## リモートストレージオプション

`remote-storage` CLI コマンド [`setup` で &#x200B;](../../installation/tutorials/deployment.md) オプションを使用してリモート ストレージを構成できます。 `remote-storage` オプションでは、次の構文を使用します。

```text
--remote-storage-<parameter-name>="<parameter-value>"
```

`parameter-name` は、特定のリモートストレージパラメーター名を参照します。 次の表に、リモートストレージの設定に使用できるパラメーターを示します。

| コマンドラインパラメーター | パラメーター名 | 説明 | デフォルト値 |
|--- |--- |--- |--- |
| `remote-storage-driver` | ドライバ | アダプター名 <br> 使用可能な値：<br>**file**: リモートストレージを無効にし、ローカルファイルシステムを使用します <br>**aws-s3**: [Amazon Simple Storage Service （Amazon S3）を使用 &#x200B;](remote-storage-aws-s3.md) | なし |
| `remote-storage-bucket` | バケット | オブジェクトストレージまたはコンテナ名 | なし |
| `remote-storage-prefix` | prefix | オプションのプレフィックス（オブジェクトストレージ内の場所） | 空 |
| `remote-storage-region` | 地域 | 地域名 | なし |
| `remote-storage-key` | アクセスキー | オプションのアクセスキー | 空 |
| `remote-storage-secret` | 秘密鍵 | オプションの秘密鍵 | 空 |

### ストレージアダプタ

デフォルトのストレージの場所は、ローカルファイルシステムにあります。 _ストレージアダプタ_ を使用すると、ストレージサービスに接続し、ファイルをどこにでも保存できます。 [!DNL Commerce] では、次のストレージサービスの設定をサポートしています。

- [Amazon Simple Storage Service （Amazon S3）](remote-storage-aws-s3.md)

## リモート記憶域を有効にする

リモートストレージは、Adobe Commerceのインストール時にインストールすることも、既存のCommerce インスタンスに追加することもできます。 次の例は、Commerceと CLI コマンドで一連の `remote-storage` パラメーターを使用した各方式を示し `setup` います。 最小で、ストレージ `driver`、`bucket`、`region` を提供する必要があります。

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
>クラウドインフラストラクチャー上のAdobe Commerceについては、[&#x200B; クラウドインフラストラクチャー上のCommerceのリモートストレージの設定 &#x200B;](cloud-support.md) を参照してください。

## コンテンツを移行

特定のアダプタに対してリモート記憶域を有効にした後、CLI を使用して既存の _メディア_ ファイルをリモート記憶域に移行できます。

```bash
./magento2ce/bin/magento remote-storage:sync
```

>[!INFO]
>
>sync コマンドは、`pub/media` ディレクトリ内のファイルのみを移行します __ ディレクトリ内のインポート/エクスポートファイルは移行しません `var`。 [2&rbrace;Commerce 2.4 ユーザーガイド &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-scheduled-import-export.html) の「スケジュールされた読み込み/書き出し」 _を参照してください。_

