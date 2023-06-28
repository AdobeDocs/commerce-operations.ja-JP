---
title: サービスのベストプラクティスの更新
description: クラウドインフラストラクチャのテクノロジースタックを更新したままにする方法を学びます。
role: Developer
feature: Best Practices
exl-id: 62aeffe3-b5a6-49f8-a39b-3219b46cd486
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# サービスのベストプラクティスの更新

この記事では、クラウドインフラストラクチャのテクノロジースタックを更新したままにしておくための推奨事項と、役立つリソースへのリンクを提供します。

## 影響を受ける製品およびバージョン

Adobe Commerce on cloud infrastructure 2.4.x 以降

## サービスを更新

Adobe Commerceが使用するサービスとコンポーネントを、提供終了日に達する前または提供終了日に近い前にアップグレードします。 これは、PCI コンプライアンスに追い付き、セキュリティの脆弱性を減らすのに役立ちます。

スタータープランのお客様は、サービスのアップグレード時にセルフサービスを利用できます。 参照： [サービスバージョンの変更](https://devdocs.magento.com/cloud/project/services.html#change-service-version) を参照してください。

Pro プランのお客様は、自社のサービスのアップグレードでのみセルフサービスを利用できます [統合環境](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter.html). 実稼動環境でサービスをアップグレードする場合は、 [サポートチケットを提出する](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) アップグレードをリクエストしています。

>[!WARNING]
>
>48 営業時間の通知をインフラストラクチャチームに受け付けないと、サービスのアップグレードを本番環境にプッシュすることはできません。 実稼動環境へのダウンタイムを最小限に抑えながら、必要な期間内に構成を更新できるインフラストラクチャサポートエンジニアを確保する必要があるので、これが必要です。

次のファイルで、サービスバージョンとサービス終了日のリストを表示できます。 [https://github.com/magento/ece-tools/blob/develop/config/eol.yaml](https://github.com/magento/ece-tools/blob/develop/config/eol.yaml).

>[!NOTE]
>
>このファイルは真実の単一の源とは見なせません。 疑わしい場合は、これらのテクノロジーの公式ベンダー Web サイトを参照してください。

## 追加情報

[必要システム構成](../../../installation/system-requirements.md)
