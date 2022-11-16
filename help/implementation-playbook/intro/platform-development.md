---
title: プラットフォーム開発の原則
description: Adobe Commerceを使用する際の、基本的なプラットフォーム開発原則を理解します。
exl-id: 3d822a8c-0e81-4a80-a820-46cf2702e0bf
source-git-commit: 639dca9ee715f2f9ca7272d3b951d3315a85346c
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# プラットフォーム開発の原則

このプレイブックでは、以下を含むAdobe Commerce開発の主な基準の一部を詳しく説明します。

- 開発プロセスに沿った機能および技術的範囲
- MVC アーキテクチャと整合する開発のベストプラクティス
- GRA を含むアーキテクチャの考慮事項
- スクリプティングと悪用に対するセキュリティ標準
- 拡張機能の開発のベストプラクティス
- REST、SOAP および GraphQL との Web API 統合
- コーディングとインフラストラクチャのパフォーマンス向上
- ツール、戦略、方法をテスト

実装プロジェクト全体で使用される方法、プロセス、ツールに関しては、一部のソリューション実装者が独自の好みを持つ場合がありますが、このプレイブックでは、ほとんどの実装で共有できる、一般に認められたベストプラクティスと方法に焦点を当てています。

大規模な IT プロジェクトと同様に、Adobe Commerceは、基盤となるテクノロジー (PHP/Zend、Symfony、JavaScript、jQuery、HTMLなど ) のベストプラクティスと標準化を活用するコーディング標準と、Adobe Commerce Coding Standard 内で確立された標準に基づいて構築されています。 これらの標準に従うことは、バグを排除し、カスタムビルドコードの品質と保守性を向上させる絶対的な方法です。

## Adobe Commerce an cloud infrastructure

Adobe Commerce on cloud infrastructure は、Adobe Commerceソフトウェア用の、管理された自動ホスティングプラットフォームです。 Adobe Commerce on cloud infrastructure には、オンプレミスのAdobe CommerceおよびMagento Open Sourceの実装とは別の、様々な追加機能が付属しています。

![Adobe Commerceコンポーネントの情報グラフィック](../../assets/playbooks/commerce-cloud.svg)

Adobe Commerce on cloud infrastructure は、PHP、MySQL、Redis を含む、事前にプロビジョニングされたインフラストラクチャを提供します。 [!DNL RabbitMQ]、およびElasticsearch技術コードの変更が Platform as a Service(PaaS) 環境にプッシュされるたびに、効率的に迅速な開発と継続的なデプロイをおこなうための、自動ビルドとデプロイ操作を備えた Git ベースのワークフロー。高度にカスタマイズ可能な環境設定ファイルおよびツールオンラインの販売/小売業向けに、拡張性と安全性に優れた環境を提供する、AWSのホスティング。

![Adobe Commerceコンポーネントの情報グラフィック](../../assets/playbooks/cloud-tech-stack.svg)
