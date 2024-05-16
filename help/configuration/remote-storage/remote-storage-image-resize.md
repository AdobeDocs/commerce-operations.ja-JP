---
title: リモートストレージの画像のサイズ変更の設定
description: サーバー側の画像のサイズ変更を設定して、ディスクリソースを最適化します。
feature: Configuration, Storage
exl-id: 51c2b9b3-0f5f-4868-9191-911d5df341ec
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# リモートストレージの画像のサイズ変更の設定

デフォルトでは、Adobe Commerceは、アプリケーション側での画像のサイズ変更をサポートします。 ただし、リモートストレージモジュールを有効にすると、Nginx を使用して画像のサイズ変更をサーバー側にオフロードでき、ディスクリソースを節約し、ディスク使用量を最適化できます。

次の図は、Nginx が画像を取得、サイズ変更、およびキャッシュに格納する方法を示しています。 サイズ変更は、URL に含まれているパラメーター（高さや幅など）によって決まります。

![画像のサイズ変更](../../assets/configuration/remote-storage-nginx-image-resize.png)

>[!TIP]
>
>クラウドインフラストラクチャプロジェクトのAdobe Commerceについては、次を参照してください [クラウドインフラストラクチャー上のCommerceにリモートストレージを設定](cloud-support.md)

## Adobe Commerceでの URL フォーマットの設定

サーバーサイドで画像のサイズを変更するには、Adobe Commerceを設定して、画像の高さ、幅および場所（URL）の引数を指定する必要があります。

**サーバーサイド画像のサイズ変更用にCommerceを設定するには**:

1. が含まれる _Admin_ パネル、クリック **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]**.

1. 右側のパネルで、を展開します **[!UICONTROL Url options]**.

1. が含まれる _カタログメディアの URL 形式_ セクション、クリア **[!UICONTROL Use system value]**.

1. 「」を選択します `Image optimization based on query parameters` URL （内） **_カタログメディアの URL 形式_** フィールド。

1. クリック **[!UICONTROL Save Config]**.

1. 続行します [Nginx 設定](#configure-nginx).

## Nginx の設定

サーバーサイドの画像のサイズ変更を引き続き設定するには、 `nginx.conf` ファイルおよびを指定 `proxy_pass` 選択したアダプタの値。

**Nginx でイメージのサイズを変更するには**:

1. のインストール [Nginx 画像フィルターモジュール][nginx-module].

   ```shell
   load_module /etc/nginx/modules/ngx_http_image_filter_module.so;
   ```

1. を作成 `nginx.conf` 含まれているテンプレートに基づくファイル `nginx.conf.sample` ファイル。 例：

   ```conf
   location ~* \.(jpg|jpeg|png|gif|webp)$ {
       set $width "-";
       set $height "-";
       if ($arg_width != '') {
           set $width $arg_width;
       }
       if ($arg_height != '') {
           set $height $arg_height;
       }
       image_filter resize $width $height;
       image_filter_jpeg_quality 90;
   }
   ```

1. [_オプション_] の設定 `proxy_pass` 特定のアダプターの値。

   - [Amazon Simple Storage Service （Amazon S3）](remote-storage-aws-s3.md)

<!-- link definitions -->

[nginx-module]: https://nginx.org/en/docs/http/ngx_http_image_filter_module.html
