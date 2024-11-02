---
title: 更新サービスのベストプラクティス
description: クラウドインフラストラクチャテクノロジースタック上のAdobe Commerceを最新の状態に保つ方法について説明します。
role: Developer
feature: Best Practices
exl-id: 62aeffe3-b5a6-49f8-a39b-3219b46cd486
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# 更新サービスのベストプラクティス

この記事では、クラウドインフラストラクチャテクノロジースタック上のAdobe Commerceを常に最新の状態に保つための推奨事項と、役立つリソースへのリンクを示します。

## 影響を受ける製品とバージョン

クラウドインフラストラクチャー 2.4.x 以降でのAdobe Commerce

## サービスの更新

Adobe Commerceで使用されるサービスやコンポーネントが、提供終了日に達するか、提供終了日に近づく前にアップグレードする。 これにより、PCI コンプライアンスに対応でき、セキュリティの脆弱性を減らすことができます。

スタータープランをご利用のお客様は、サービスのアップグレードをセルフサービスで行うことができます。 この方法について詳しくは、[ サービスバージョンの変更 ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/services-yaml#change-service-version) を参照してください。

Pro プランのお客様は、[ 統合環境 ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter.html) でのサービスのアップグレードに関してのみセルフサービスを利用できます。 実稼動環境でのサービスのアップグレードの場合は、アップグレードをリクエストする [ サポートチケットを送信 ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) 必要があります。

>[!WARNING]
>
>サービスのアップグレードは、インフラストラクチャ・チームに 48 営業時間内に通知しない限り、本番環境にプッシュすることはできません。 実稼動環境のダウンタイムを最小限に抑え、目的の期間内に設定を更新できるインフラストラクチャサポートエンジニアを確保する必要があるので、これが必要になります。

サービス バージョンと提供終了日の一覧は、[https://github.com/magento/ece-tools/blob/develop/config/eol.yaml](https://github.com/magento/ece-tools/blob/develop/config/eol.yaml) のファイルで確認できます。

>[!NOTE]
>
>このファイルは、唯一の情報源と見なすことはできません。 これらのテクノロジーに関して不明な点がある場合は、ベンダーの公式 web サイトを参照してください。

## 追加情報

[必要システム構成](../../../installation/system-requirements.md)
