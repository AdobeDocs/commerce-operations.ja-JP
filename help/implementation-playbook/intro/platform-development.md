---
title: プラットフォーム開発の原則
description: Adobe Commerceを使用する際の基本的なプラットフォーム開発原則を理解する。
exl-id: 3d822a8c-0e81-4a80-a820-46cf2702e0bf
feature: Cloud
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---


# プラットフォーム開発の原則

このトピックでは、Adobe Commerce開発の主な標準を以下のように深く掘り下げます。

- 開発プロセスに沿った機能面および技術面のスコーピング
- MVC アーキテクチャに合わせた開発のベストプラクティス
- GRA を含むアーキテクチャに関する考慮事項
- スクリプティングや悪用に対するセキュリティ標準
- 拡張機能開発のベストプラクティス
- REST、SOAPおよびGraphQLとの Web API 統合
- コーディングとインフラストラクチャのパフォーマンスの向上
- テスト・ツール、戦略、方法論

一部のソリューション実装者は、方法、プロセス、ツールに関して独自の好みを持っているかもしれませんが、このプレイブックでは、ほとんどの実装で共有できる、受け入れられているベストプラクティスと方法論に焦点を当てています。

他の大規模な IT プロジェクトと同様に、Adobe Commerceは、ベストプラクティスと標準化を使用するコーディング標準と、Adobe Commerce[ コーディング標準 ](https://developer.adobe.com/commerce/php/coding-standards/) 内で確立された標準に基づいて構築されています。 これらの標準に従うことは、バグを排除し、カスタムビルドされたコードの品質と保守性を向上させるために重要です。

## クラウドインフラストラクチャー上のAdobe Commerce

クラウドインフラストラクチャー上のAdobe Commerceは、Adobe Commerce ソフトウェア用の管理された自動ホスティングプラットフォームです。 Adobe Commerce on cloud infrastructure には、オンプレミスのAdobe Commerce実装とは異なる様々な機能が用意されています。 [ クラウドガイド ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/overview.html) を参照してください。
