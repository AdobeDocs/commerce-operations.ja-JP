---
title: リモートストレージ用のAWS S3 バケットの設定
description: Commerce プロジェクトを設定して、AWS S3 ストレージサービスをリモートストレージに使用します。
feature: Configuration, Storage
exl-id: e8aeade8-2ec4-4844-bd6c-ab9489d10436
source-git-commit: 3690043019d70ad15332f757158937a7d5305043
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# リモートストレージ用のAWS S3 バケットの設定

[Amazon Simple Storage Service （Amazon S3） ][AWS S3] は、業界をリードするスケーラビリティ、データ可用性、セキュリティ、パフォーマンスを提供するオブジェクトストレージサービスです。 AWS S3 サービスでは、データストレージにバケットつまりコンテナを使用します。 この設定では、_private_ バケットを作成する必要があります。 クラウドインフラストラクチャー上のAdobe Commerceについては、[ クラウドインフラストラクチャー上のCommerceのリモートストレージの設定 ](cloud-support.md) を参照してください。

>[!WARNING]
>
>Adobeでは重大なセキュリティリスクがあるため、公開バケットの使用は避けるべきです。
>
>お客様が提供する S3 バケットをアセットまたはメディアストレージ用に使用する場合、Adobeは、S3 バケットの設定、管理または操作に関連する問題、データ損失または停止に対して責任を負わず、サポートを提供しません。 S3 バケットのすべてのトラブルシューティングとメンテナンスは、お客様の単独の責任です。

**AWS S3 アダプタでリモートストレージを有効にするには**:

1. Amazon S3 ダッシュボードにログインし、_プライベート_ バケットを作成します。

1. [AWS IAM] ロールを設定します。 または、アクセスキーと秘密鍵を生成します。

1. デフォルトのデータベースストレージを無効にします。

   ```bash
   bin/magento config:set system/media_storage_configuration/media_database 0
   ```

1. プライベートバケットを使用するようにCommerceを設定します。 パラメーターの完全なリストについては、[ リモートストレージオプション ](remote-storage.md#remote-storage-options) を参照してください。

   ```bash
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="<bucket-name>" --remote-storage-region="<region-name>" --remote-storage-prefix="<optional-prefix>" --remote-storage-key=<optional-access-key> --remote-storage-secret=<optional-secret-key> -n
   ```

1. メディア ファイルをリモート ストレージと同期します。

   ```bash
   bin/magento remote-storage:sync
   ```

## Nginx の設定

>[!NOTE]
>
>このアプローチは、クラウドインフラストラクチャプロジェクトのAdobe Commerceには適用されません。 Nginx は、クラウドインフラストラクチャー上のAdobe Commerceでは設定できません。 詳しくは、[ クラウド固有のドキュメント ](cloud-support.md) を参照してください。

Nginx では、`proxy_pass` ディレクティブを使用して認証を実行するために追加の構成が必要です。 `nginx.conf` ファイルに次のプロキシ情報を追加します。

>nginx.conf

```conf
location ~* \.(ico|jpg|jpeg|png|gif|svg|js|css|swf|eot|ttf|otf|woff|woff2)$ {
    # Proxying to AWS S3 storage.
    resolver 8.8.8.8;
    set $bucket "<s3-bucket-name>";
    proxy_pass https://s3.amazonaws.com/$bucket$uri;
    proxy_pass_request_body off;
    proxy_pass_request_headers off;
    proxy_intercept_errors on;
    proxy_hide_header "x-amz-id-2";
    proxy_hide_header "x-amz-request-id";
    proxy_hide_header "x-amz-storage-class";
    proxy_hide_header "Set-Cookie";
    proxy_ignore_headers "Set-Cookie";
}
```

### 認証

[AWS IAM] ロールの代わりにアクセス キーと秘密鍵を使用する場合は、[`ngx_aws_auth` Nginx モジュール ][ngx repo] を含める必要があります。

### 権限

S3 統合は、キャッシュされた画像を生成してローカルファイルシステムに保存する機能に依存しています。 したがって、`pub/media` および同様のディレクトリのフォルダーアクセス権は、ローカルストレージを使用する場合と S3 で同じです。

### ファイル操作

ファイルストレージのタイプに関係なく、コーディングまたは拡張機能開発で [!DNL Commerce] ファイルアダプタメソッドを使用することを強くお勧めします。 ストレージに S3 を使用する場合、S3 ファイルはファイルシステム内に配置されないので、`copy`、`rename`、`file_put_contents` などのネイティブの PHP ファイル I/O 操作を使用しないでください。 コード例については、[DriverInterface.php](https://github.com/magento/magento2/blob/2.4-develop/lib/internal/Magento/Framework/Filesystem/DriverInterface.php#L18) を参照してください。

<!-- link definitions -->

[AWS S3]: https://aws.amazon.com/s3
[AWS IAM]: https://aws.amazon.com/iam/
[ngx repo]: https://github.com/anomalizer/ngx_aws_auth
