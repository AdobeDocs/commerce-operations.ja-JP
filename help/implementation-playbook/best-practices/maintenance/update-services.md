---
title: 更新サービスのベストプラクティス
description: Adobe Commerce on クラウド基盤テクノロジースタックを最新の状態に保つ方法について説明します。
role: Developer
feature: Best Practices
exl-id: 62aeffe3-b5a6-49f8-a39b-3219b46cd486
source-git-commit: 5e3289b328b51eb50354efdc1571283791175b9a
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 0%

---

# 更新サービスのベストプラクティス

この記事では、Adobe Commerce on cloud infrastructure テクノロジースタックを最新の状態に保つための推奨事項と、役立つリソースへのリンクを提供します。

## 影響を受ける製品とバージョン

Adobe Commerce on cloud infrastructure 2.4.x以降

## サービスを更新

Adobe Commerceで使用するサービスとコンポーネントは、使用期限に達する前または使用期限に近づく前にアップグレードします。 これにより、PCI認定に対応し、セキュリティ脆弱性を低減できます。

スタータープランをご利用のお客様は、サービスのアップグレードをセルフサービスで利用できます。 この方法について詳しくは、[ サービスバージョンの変更](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/services-yaml#change-service-version)を参照してください。

Pro プランをご利用のお客様は、[統合環境](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter.html)でのサービスのアップグレードでのみセルフサービスを利用できます。 実稼動環境でのサービスのアップグレードの場合、アップグレードをリクエストするには、[ サポートチケット ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket)を送信する必要があります。

>[!WARNING]
>
>サービスのアップグレードを本番環境にプッシュするには、48営業時間前にAdobeのインフラストラクチャチームに通知する必要があります。 これは、Adobeがインフラストラクチャサポートエンジニアが、実稼動環境へのダウンタイムを最小限に抑えながら、必要な時間枠で設定を更新できることを確認するために必要です。 Adobeでは、サービスのアップグレード中にサイトをメンテナンスモードにすることをお勧めします。

サービスのバージョンとサポート終了日のリストは、[https://github.com/magento/ece-tools/blob/develop/config/eol.yaml](https://github.com/magento/ece-tools/blob/develop/config/eol.yaml)のファイルで表示できます。

>[!NOTE]
>
>このファイルを信頼できる唯一の情報源とみなすことはできません。 不明な点がある場合は、これらのテクノロジーの公式ベンダーのweb サイトを参照してください。

## 追加情報

[必要システム構成](../../../installation/system-requirements.md)
