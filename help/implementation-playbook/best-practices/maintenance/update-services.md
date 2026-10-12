---
title: 更新サービスのベストプラクティス
description: Adobe Commerce on クラウド基盤テクノロジースタックを最新の状態に保つ方法について説明します。
role: Developer
feature: Best Practices
exl-id: 62aeffe3-b5a6-49f8-a39b-3219b46cd486
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%
---
# 更新サービスのベストプラクティス

この記事では、Adobe Commerce on cloud infrastructure テクノロジースタックを最新の状態に保つための推奨事項と、役立つリソースへのリンクを提供します。

## 影響を受ける製品とバージョン

Adobe Commerce on cloud infrastructure 2.4.x以降

## サービスを更新

Adobe Commerceで使用するサービスとコンポーネントは、使用期限に達する前または使用期限に近づく前にアップグレードします。 これにより、PCI認定に対応し、セキュリティ脆弱性を低減できます。

スタータープランをご利用のお客様は、サービスのアップグレードをセルフサービスで利用できます。 この方法について詳しくは、[&#x200B; サービスバージョンの変更](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml#change-service-version)を参照してください。

Pro プランをご利用のお客様は、[統合環境](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27242)でのサービスのアップグレードでのみセルフサービスを利用できます。 実稼動環境でのサービスのアップグレードの場合、アップグレードをリクエストするには、[&#x200B; サポートチケット &#x200B;](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket)を送信する必要があります。

>[!WARNING]
>
>サービスのアップグレードを本番環境にプッシュするには、48営業時間前にAdobeのインフラストラクチャチームに通知する必要があります。 これは、Adobeがインフラストラクチャサポートエンジニアが、実稼動環境へのダウンタイムを最小限に抑えながら、必要な時間枠で設定を更新できることを確認するために必要です。 Adobeでは、サービスのアップグレード中にサイトをメンテナンスモードにすることをお勧めします。

サービスのバージョンとサポート終了日のリストは、[https://github.com/magento/ece-tools/blob/develop/config/eol.yaml](https://github.com/magento/ece-tools/blob/develop/config/eol.yaml)のファイルで表示できます。

>[!NOTE]
>
>このファイルを信頼できる唯一の情報源とみなすことはできません。 不明な点がある場合は、これらのテクノロジーの公式ベンダーのweb サイトを参照してください。

## 追加情報

[必要システム構成](../../../installation/system-requirements.md)
