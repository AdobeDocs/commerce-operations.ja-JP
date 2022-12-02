---
title: クラウドインフラストラクチャ上のコマース用リモートストレージ
description: クラウドインフラストラクチャ上のAdobe Commerceのリモートストレージを設定する方法に関するガイダンスを参照してください。
source-git-commit: 8102c083bb0216bbdcad2882f39f7711b9cee52b
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---


# クラウドインフラストラクチャ上のコマース用のリモートストレージの設定

リモートストレージソリューションをクラウドインフラストラクチャ上のAdobe Commerceプロジェクトで使用する場合は、 [Amazon S3](https://docs.fastly.com/en/guides/amazon-s3) 指導 _Fastly_ Fastly 画像の最適化がAWS S3 で確実に機能するようにするドキュメント。

準備を整えて [Fastly 認証情報](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#get-fastly-credentials). Pro プロジェクトでは、SSH を使用してサーバーに接続し、 `/mnt/shared/fastly_tokens.txt` ファイル。 ステージング環境と実稼動環境には、一意の資格情報が割り当てられます。 各環境の資格情報を取得する必要があります。

次のタスクを使用して、クラウドプロジェクトのリモートストレージの設定を続行します。

1. の設定 [Fastly のバックエンド統合](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/Edge-Modules/EDGE-MODULE-OTHER-CMS-INTEGRATION.md).

1. の VCL ロジックを作成 [AWS S3 認証](https://docs.fastly.com/en/guides/amazon-s3#using-an-amazon-s3-private-bucket).

1. の VCL ロジックを作成 [AWS S3 バケットに対するバックエンドリクエスト](https://developer.fastly.com/reference/vcl/variables/backend-connection/req-backend/).
