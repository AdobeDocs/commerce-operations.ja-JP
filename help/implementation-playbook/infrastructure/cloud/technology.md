---
title: クラウドインフラストラクチャテクノロジー
description: クラウドインフラストラクチャー上のAdobe Commerceに対してAdobeが使用するテクノロジーのコレクションについて、詳しく説明します。
exl-id: de1b3a64-d32b-455f-bdb0-ad883dedd6d4
feature: Cloud
source-git-commit: c737a8e902c960c933e54e2521107475bb1e5a22
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 0%

---


# 技術

クラウドインフラストラクチャー上のAdobe Commerceでは、プラットフォームをサポートするために複数のソフトウェアソリューションを使用します。 の次のトピックを参照してください _クラウドガイド_ 詳しくは、以下を参照してください。

- [Pro 環境のアーキテクチャ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html#production-technology-stack)
- [スターター環境のアーキテクチャ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/starter-architecture.html#production-and-staging-technology-stack)

## 機能とメリット

- 3 つの個別のアベイラビリティーゾーンまたはデータセンターにまたがる弾力性のあるロードバランサーを備えた、仮想プライベートクラウド（VPC）内の 3 つの専用インスタンス。
- 単一のインスタンスに障害が発生する可能性のあるイベントに対する回復性が向上します。 例えば、AWSのアベイラビリティーゾーンまたはデータセンター全体の停止などです。
- Web、キャッシュ、検索、データベースを含むスタック全体にわたる、ダウンタイムなしのスケーリング。
