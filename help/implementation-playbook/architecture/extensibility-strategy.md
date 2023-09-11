---
title: Adobe Commerce拡張戦略
description: Adobe Commerceの拡張モデルが実装をカスタマイズする力を与える方法を説明します。
exl-id: fac4630d-8a41-40dc-899a-01eabceaa61e
feature: Extensibility
source-git-commit: 4873a51fbf67d305fdd1898f3740c73ac5ccbad8
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# 拡張戦略

Adobe Commerceの拡張機能プラットフォームを使用すると、ブランドは、アップグレード性を維持しながら、プロセスの効率的なカスタマイズ、システムの統合、新しい機能のデプロイをおこなうことができます。

## Commerce 拡張戦略の概要

コマースプラットフォームの機能を拡張する方法には、次の大まかなアプローチが含まれます。

* コマースプラットフォームのネイティブ機能の拡張。 例えば、マーチャントは、プラットフォームのネイティブ機能を拡張および改良する Marketplace アプリケーション（多くの場合、サードパーティによって構築）をインストールできます。例えば、チェックアウト時に配送先住所を検証し、UPS 通信事業者住所 API と迅速に統合できます。

* サードパーティのアプリ/拡張機能をコマースプラットフォームと統合する。 開発者は、Commerce の既存の包括的な REST API とGraphQL API を使用して、Commerce をサードパーティのソリューションと直接統合できます。

ただし、プラットフォームアーキテクチャは、プラットフォームを拡張するための最適な戦略を決定します。 コマースは、ヘッドレスデプロイメントに対して、豊富な GQL および REST API の範囲を提供します。 コマースのコードベースは、よりモジュラー型のアーキテクチャと単一の統合レイヤーに向けて進化し続けています。このレイヤーは、新しく改善されたカスタマイズツールを提供します。

* [Adobe Commerceの App Builder](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/adobe-developer-app-builder/introduction-to-app-builder.html) は、開発インフラストラクチャ上に構築された開発フレームワークおよびAdobeセットです。 開発者は、これを使用して、ユーザーエクスペリエンス/ストアフロントのカスタマイズからミドルウェアおよびビジネスロジックの拡張に至るまで、様々なコマース拡張を作成できます。

* [Adobe Developer App Builder の API メッシュ](https://developer.adobe.com/graphql-mesh-gateway/) を使用すると、開発者は複数のデータソースを単一の API エンドポイントに組み合わせることができます。 これは、Adobe I/Oを使用して、プライベートおよびサードパーティの API や他のAdobeインターフェイスと、Adobe Commerce API や他のソフトウェア製品との API オーケストレーションまたは統合をサポートします。

* [Adobe CommerceのAdobe I/Oイベント](https://developer.adobe.com/commerce/events/get-started/) は、App Builder とサードパーティの Web フックを使用して開発されたアプリケーションでトランザクションデータを利用でき、イベント駆動型アプリケーションの作成をサポートします。

これらのツールを使用すると、Adobe DeveloperコンソールおよびAdobe開発者ツールにアクセスして、API を作成し、カスタムプラグインと統合を統合できます。

次の図は、コマースの拡張性戦略の主なコンポーネントを示しています。

![Adobe Commerceの拡張戦略図](../../assets/playbooks/extensibility-strategy-overview.png)
