---
title: 実装プレイブック
description: Commerce 実装プレイブックの目的
exl-id: 2f82c68c-60c7-4a62-837b-492afc06e0db
feature: Best Practices, Cloud, Integration
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 1%

---

# 実装プレイブック

このプレイブックの目的は、一般的なAdobe Commerce実装の最も包括的な概要を提供することです。

プロジェクトの範囲の初期段階から開発、統合、デプロイを通じて継続的なサポートに至るまで、Adobe Commerce プロジェクトを正常に開始するために考慮する必要がある多くの手法やベストプラクティスがあります。

さらに、以下のプロセスと考慮事項は、あらゆる種類のAdobe Commerce プロジェクトに当てはまります。

- 小規模、中規模、大規模の実装
- B2C、B2B、B2B2C のビジネスモデル
- モノリシックアーキテクチャまたはヘッドレスアーキテクチャ
- 単一市場または複数市場での展開
- ミドルウェアを含む/含まない広範な統合

このプレイブックが、通常は e コマースプロジェクトのイニシアチブに関与する様々な関係者に、次のようなインサイトとガイダンスを提供することを願っています。

- E コマースの展開に何が必要かを明確に把握している CEO と経営全般
- プラットフォーム自体でビジネスユーザーと連携する CMO とデジタルマネージャー
- テクノロジープロジェクトの実装のすべての段階で深く関わる CTO とテクニカルマネージャー
- コマースプロジェクトのイニシアチブを主導し、関連する情報をすべて手元に用意しておく必要があるプロジェクトマネージャーとプロジェクトチャンピオン

IT プロジェクトの成功は、コードを開発、カスタマイズ、統合、メンテナンスするチーム（通常はソリューションパートナー）の経験と専門知識に大きく依存しますが、Adobe Commerceの実装のベストプラクティスを理解することは、すべての関係者に関係があると考えています。

## このプレイブックについて

このプレイブックの構造は、Adobe Commerce実装プロジェクトの典型的なライフサイクルに従っています。 これにより、読者はすべての関連情報について、プロジェクトの関連セクションにすぐにスキップできるので、このドキュメント全体を簡単に移動できます。

- **プロジェクトの範囲** – 実装を成功に導くうえでブランドが理解および完了することが重要な、主な関係者、プロセス、タイムライン、要件の分類です。

- **開発と品質管理** – 多数のAdobe Commerce実装でテストおよび完成されたツール、ソリューション、プロセス、手法に加えて、特定のビジネスニーズと目標に最適なソリューションに関する推奨事項についても説明します。

- **計画とガバナンス** - ソリューションを時間通りに、予算通りに、そしてニーズを満たすものにするための計画を作成することに取り組み、成功の鍵を握ります。

- **アーキテクチャと統合** - Adobe Commerceを、市場で最も信頼され、信頼性の高い e コマースプラットフォームにしている機能、アーキテクチャおよび統合です。

- **インフラストラクチャと導入** – 実際のプラットフォーム自体の詳細に入り込み、Adobe Commerceを支えるインフラストラクチャと環境とそれを堅牢なプラットフォームにするソフトウェアソリューションを重点的に取り上げます。

- **ローンチとカットオーバープロセス** - サイトを確実に稼働させ、1 日目以降も有効性のレベルを維持するために必要な、ローンチ前からローンチ後までの戦術とアクションです。

- **継続的なサポートとメンテナンス** – 移行段階の詳細と、ローンチ後もブランドを継続的に前進させるための継続的なサポートプランに関するモデルと SLA の種類について説明します。
