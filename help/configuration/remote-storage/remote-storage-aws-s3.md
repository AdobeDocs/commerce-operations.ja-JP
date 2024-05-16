---
title: リモートストレージ用のAWS S3 バケットの設定
description: Commerce プロジェクトを設定して、AWS S3 ストレージサービスをリモートストレージに使用します。
feature: Configuration, Storage
exl-id: e8aeade8-2ec4-4844-bd6c-ab9489d10436
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# リモートストレージ用のAWS S3 バケットの設定

この [Amazon Simple Storage Service （Amazon S3）][AWS S3] は、業界をリードするスケーラビリティ、データ可用性、セキュリティ、パフォーマンスを提供するオブジェクトストレージサービスです。 AWS S3 サービスでは、データストレージにバケットつまりコンテナを使用します。 この設定では、 _非公開_ バケット。 クラウドインフラストラクチャー上のAdobe Commerceについては、以下を参照してください。 [クラウドインフラストラクチャー上のCommerceにリモートストレージを設定](cloud-support.md).

>[!WARNING]
>
>Adobeは重大なセキュリティリスクをもたらすため、公共バケットの使用を強く勧めません。

**AWS S3 アダプターでリモート記憶域を有効にするには**:

1. Amazon S3 ダッシュボードにログインし、 _非公開_ バケット。

1. の設定 [AWS IAM] 役割。 または、アクセスキーと秘密鍵を生成します。

1. デフォルトのデータベースストレージを無効にします。

   ```bash
   bin/magento config:set system/media_storage_configuration/media_database 0
   ```

1. プライベートバケットを使用するようにCommerceを設定します。 参照： [リモートストレージオプション](remote-storage.md#remote-storage-options) パラメーターの完全なリスト。

   ```bash
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="<bucket-name>" --remote-storage-region="<region-name>" --remote-storage-prefix="<optional-prefix>" --remote-storage-key=<optional-access-key> --remote-storage-secret=<optional-secret-key> -n
   ```

1. メディア ファイルをリモート ストレージと同期します。

   ```bash
   bin/magento remote-storage:sync
   ```

## Nginx の設定

Nginx では、で認証を実行するために追加の設定が必要です `proxy_pass` ディレクティブ。 次のプロキシ情報をに追加します `nginx.conf` ファイル：

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

アクセスキーと秘密鍵を代わりに使用する場合 [AWS IAM] 役割には、を含める必要があります [`ngx_aws_auth` Nginx モジュール][ngx repo].

### 権限

S3 統合は、キャッシュされた画像を生成してローカルファイルシステムに保存する機能に依存しています。 したがって、次のフォルダー権限は： `pub/media` と同様のディレクトリは、ローカルストレージを使用する場合と S3 で同じです。

### ファイル操作

を使用することを強くお勧めします [!DNL Commerce] ファイルの記憶域の種類に関係なく、コーディングまたは拡張機能開発のファイル アダプターメソッド。 ストレージに S3 を使用する場合、次のようなネイティブの PHP ファイル I/O 操作は使用しないでください `copy`, `rename`、または `file_put_contents`S3 ファイルはファイルシステム内に配置されないので、 参照： [DriverInterface.php](https://github.com/magento/magento2/blob/2.4-develop/lib/internal/Magento/Framework/Filesystem/DriverInterface.php#L18) コードの例については、を参照してください。

<!-- link definitions -->

[AWS S3]: https://aws.amazon.com/s3
[AWS IAM]: https://aws.amazon.com/iam/
[ngx repo]: https://github.com/anomalizer/ngx_aws_auth
