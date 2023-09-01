---
title: プラットフォーム開発の原則
description: Adobe Commerceを使用する際の、基本的なプラットフォーム開発原則を理解します。
exl-id: 3d822a8c-0e81-4a80-a820-46cf2702e0bf
feature: Cloud
source-git-commit: 3c1a49c2dc3dc0d3d47e16c724d4099b6a456c77
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---


# プラットフォーム開発の原則

このトピックでは、以下を含む、Adobe Commerce開発の主な標準の一部について詳しく説明します。

- 開発プロセスに沿った機能および技術的範囲
- MVC アーキテクチャとの整合に関する開発のベストプラクティス
- GRA を含むアーキテクチャの考慮事項
- スクリプティングと悪用に対するセキュリティ標準
- 拡張機能の開発のベストプラクティス
- REST、SOAP およびGraphQLとの Web API 統合
- コーディングとインフラストラクチャのパフォーマンス向上
- ツール、戦略、方法をテスト

一部のソリューション実装者は、方法、プロセス、ツールに独自の好みを持つ場合がありますが、このプレイブックでは、ほとんどの実装で共有できる、受け入れられたベストプラクティスと方法論に焦点を当てています。

大規模な IT プロジェクトと同様に、Adobe Commerceは、ベストプラクティスと標準化を使用するコーディング標準と、Adobe Commerce内で確立された標準に基づいて構築されています [コーディング規格](https://developer.adobe.com/commerce/php/coding-standards/). これらの標準に従うことは、バグを削除し、カスタムビルドコードの品質と保守性を向上させるために重要です。

## Adobe Commerce an cloud infrastructure

Adobe Commerce on cloud infrastructure は、Adobe Commerceソフトウェア用の、管理された自動ホスティングプラットフォームです。 Adobe Commerce on cloud infrastructure には、オンプレミスのAdobe CommerceおよびMagento Open Sourceの実装とは別の、様々な機能が付属しています。 詳しくは、 [クラウドガイド](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/overview.html).
