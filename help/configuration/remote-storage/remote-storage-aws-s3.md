---
title: リモートストレージ用AWS S3 バケットの設定
description: リモートストレージにAWS S3 ストレージサービスを使用するようにCommerce プロジェクトを設定します。
feature: Configuration, Storage
exl-id: e8aeade8-2ec4-4844-bd6c-ab9489d10436
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# リモートストレージ用AWS S3 バケットの設定

[Amazon Simple Storage Service （Amazon S3） ](https://aws.amazon.com/s3)は、業界をリードするスケーラビリティ、データ可用性、セキュリティ、パフォーマンスを提供するオブジェクト ストレージ サービスです。 AWS S3 サービスでは、データストレージにバケット（コンテナ）を使用します。 この設定では、_private_ バケットを作成する必要があります。 クラウド インフラストラクチャ上のAdobe Commerceについては、[ クラウド インフラストラクチャ上のCommerceのリモート ストレージの設定](cloud-support.md)を参照してください。

>[!WARNING]
>
>Adobeは深刻なセキュリティリスクを引き起こすため、パブリックバケットの使用を強くお勧めしません。
>
>お客様が提供するS3 バケットをアセットまたはメディアストレージに使用する場合、Adobeは、S3 バケットの設定、管理、または操作に関連する問題、データの損失、または停止について責任を負わず、サポートも提供しません。 S3 バケットのトラブルシューティングとメンテナンスはすべて、お客様の責任です。

**AWS S3 アダプタでリモート ストレージを有効にするには**:

1. Amazon S3 ダッシュボードにログインし、_private_ バケットを作成します。

1. [AWS IAM](https://aws.amazon.com/iam/)の役割を設定します。 または、アクセスキーと秘密鍵を生成します。

1. デフォルトのデータベースストレージを無効にします。

   ```shell
   bin/magento config:set system/media_storage_configuration/media_database 0
   ```

1. プライベートバケットを使用するようにCommerceを設定します。 パラメーターの完全なリストについては、[ リモートストレージオプション ](remote-storage.md#remote-storage-options)を参照してください。

   ```shell
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="<bucket-name>" --remote-storage-region="<region-name>" --remote-storage-prefix="<optional-prefix>" --remote-storage-key=<optional-access-key> --remote-storage-secret=<optional-secret-key> -n
   ```

1. メディアファイルをリモートストレージと同期します。

   ```shell
   bin/magento remote-storage:sync
   ```

## Nginxの設定

>[!NOTE]
>
>このアプローチは、Adobe Commerce on cloud インフラストラクチャプロジェクトには適用できません。 Adobe Commerce on cloud infrastructureでNginxを設定することはできません。 詳しくは、[ クラウド固有のドキュメント ](cloud-support.md)を参照してください。

Nginxでは、`proxy_pass` ディレクティブを使用して認証を実行するには、追加の設定が必要です。 次のプロキシ情報を`nginx.conf` ファイルに追加します。

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

[AWS IAM](https://aws.amazon.com/iam/) ロールの代わりにアクセスキーと秘密鍵を使用する場合は、[`ngx_aws_auth` Nginx モジュール ](https://github.com/anomalizer/ngx_aws_auth)を含める必要があります。

### 権限

S3統合は、キャッシュされた画像を生成してローカルファイルシステムに保存する機能に依存しています。 したがって、`pub/media`および類似のディレクトリに対するフォルダー権限は、ローカルストレージを使用する場合とS3に対して同じです。

### ファイル操作

ファイル ストレージの種類に関係なく、コーディングまたは拡張機能の開発で[!DNL Commerce] ファイル アダプターのメソッドを使用することを強くお勧めします。 S3 ファイルはファイルシステム内に存在しないため、ストレージにS3を使用する場合は、`copy`、`rename`、`file_put_contents`などのネイティブ PHP ファイル I/O操作を使用しないでください。 コード例については、[DriverInterface.php](https://github.com/magento/magento2/blob/2.4-develop/lib/internal/Magento/Framework/Filesystem/DriverInterface.php#L18)を参照してください。

