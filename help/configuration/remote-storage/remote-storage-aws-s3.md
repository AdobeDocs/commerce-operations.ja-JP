---
title: リモートストレージ用のAWS S3 バケットの設定
description: リモートストレージにAWS S3 ストレージサービスを使用するように Commerce プロジェクトを設定します。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# リモートストレージ用のAWS S3 バケットの設定

この [Amazon Simple Storage Service (Amazon S3)][AWS S3] は、業界をリードする拡張性、データ可用性、セキュリティ、パフォーマンスを提供するオブジェクトストレージサービスです。 AWS S3 サービスは、データストレージにバケット（コンテナ）を使用します。 この設定では、 _プライベート_ バケット。

>[!WARNING]
>
>Adobeは、重大なセキュリティリスクを引き起こすので、公開バケットの使用を非推奨にします。

**AWS S3 アダプターでリモートストレージを有効にするには**:

1. Amazon S3 ダッシュボードにログインし、 _プライベート_ バケット。

1. 設定 [AWS IAM] 役割。 または、アクセス権と秘密鍵を生成します。

1. デフォルトのデータベースストレージを無効にします。

   ```bash
   bin/magento config:set system/media_storage_configuration/media_database 0
   ```

1. コマースでプライベートバケットを使用するように設定します。 詳しくは、 [リモートストレージオプション](remote-storage.md#remote-storage-options) を参照してください。

   ```bash
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="<bucket-name>" --remote-storage-region="<region-name>" --remote-storage-prefix="<optional-prefix>" --remote-storage-key=<optional-access-key> --remote-storage-secret=<optional-secret-key> -n
   ```

## Nginx の設定

Nginx では、 `proxy_pass` ディレクティブ。 次のプロキシ情報を `nginx.conf` ファイル：

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

の代わりにアクセスおよび秘密鍵を使用する場合 [AWS IAM] の役割の場合、 [`ngx_aws_auth` Nginx モジュール][ngx repo].

### 権限

S3 統合は、キャッシュされた画像を生成してローカルファイルシステムに保存する機能に依存しています。したがって、 `pub/media` と同様のディレクトリは、ローカルストレージを使用する場合と同様、S3 でも同じです。

### ファイル操作

次を使用することを強くお勧めします。 [!DNL Commerce] ファイルアダプタメソッドは、ファイルストレージタイプに関係なく、コーディングまたは拡張機能の開発で使用します。 ストレージに S3 を使用する場合は、次のようなネイティブ PHP ファイルの I/O 操作を使用しないでください。 `copy`, `rename` または `file_put_contents`S3 ファイルがファイルシステム内に存在しないので、を呼び出す必要があります。 詳しくは、 [DriverInterface.php] コード例を参照してください。

<!-- link definitions -->

[AWS S3]: https://aws.amazon.com/s3
[AWS IAM]: https://aws.amazon.com/iam/
[ngx repo]: https://github.com/anomalizer/ngx_aws_auth
[DriverInterface.php]: https://github.com/magento/magento2/blob/2.4-develop/lib/internal/Magento/Framework/Filesystem/DriverInterface.php#L18
