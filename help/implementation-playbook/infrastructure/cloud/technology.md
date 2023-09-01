---
title: クラウドインフラストラクチャテクノロジー
description: クラウドインフラストラクチャ上のAdobe Commerceに使用されるテクノロジーAdobeのコレクションについて詳しく説明します。
exl-id: de1b3a64-d32b-455f-bdb0-ad883dedd6d4
feature: Cloud
source-git-commit: c737a8e902c960c933e54e2521107475bb1e5a22
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---


# 技術

Adobe Commerce on cloud infrastructure では、プラットフォームをサポートするために複数のソフトウェアソリューションを使用します。 詳しくは、 _クラウドガイド_ 詳しくは、以下を参照してください。

- [プロ環境のアーキテクチャ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html#production-technology-stack)
- [スターター環境のアーキテクチャ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/starter-architecture.html#production-and-staging-technology-stack)

## 機能とメリット

- 3 つの独立したアベイラビリティーゾーンまたはデータセンターをまたいだ弾性ロードバランサーを備えた、仮想プライベートクラウド (VPC) 内の 3 つの専用インスタンス。
- 単一のインスタンスの失敗を引き起こす可能性のあるイベントに対する回復性が高くなりました。 例えば、AWSの可用性ゾーンまたはデータセンター全体が停止したとします。
- Web、キャッシュ、検索、データベースを含む、スタック全体にわたるダウンタイムなしの拡張。
