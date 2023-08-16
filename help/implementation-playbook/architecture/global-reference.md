---
title: Adobe Commerce Global Reference Architecture
description: グローバルリファレンスアーキテクチャを活用して、Adobe Commerceの実装を最大限に活用します。
exl-id: a18529a3-da9b-4e1b-8048-0a906e65c740
feature: Deploy
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---

# グローバルリファレンスアーキテクチャ (GRA)

>[!VIDEO](https://video.tv.adobe.com/v/3410528/?quality=12&learn=on)

複数のブランドに複数のサイトを持つ企業を複数の現地市場（通貨、言語、メディア、共有カタログ、ユニーク買い物かご）で運営し、同じ機能と統合を実装する際に不要なコストを避けたい場合は、グローバル・リファレンス・アーキテクチャ (GRA) が常に最適です。

![建築の相違のコストを説明した表](../../assets/playbooks/divergent-architecture.svg)

![アーキテクチャに統合されたコストを説明する表](../../assets/playbooks/consolidated-architecture.svg)

GRA は次のようになります。

- 実装アプローチ
- デプロイメント戦略
- プロセスガバナンスモデル

GRA は次の条件を満たしていません。

- 製品の「機能」
- 任意のコマースプラットフォームに固有
- グローバルビジネスの使用例のみ

GRA の影響：

- コードの配信方法

   - 様々なエクスペリエンスを提供する目的固有のコードリポジトリに基づいて構築されています。

- ビジネスシステムの統合方法

   - ブランドや地域ごとにビジネスシステムへの接続を統合します。

- カスタマイズの開発と維持方法

   - カスタマイズは一元化され、ドメイン固有のものになるので、すべてのカスタマイズ作業をビジネスの総合的な視点から行うことができます。

- 新しい市場がどのように有効化されているか

   - 複数のチャネルと市場のリリースを簡素化し、それ以外の場合は、時間とコストが大幅に大幅に増加します。
