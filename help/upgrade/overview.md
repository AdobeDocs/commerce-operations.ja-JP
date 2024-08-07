---
title: アップグレードプロセスの概要
description: Adobe Commerce プロジェクトをアップグレードして、ストアフロントの安全を維持し、効率的に運用する方法について説明します。
exl-id: 40bd97ca-6648-40d4-9c61-7d159391976a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '895'
ht-degree: 1%

---

# アップグレードプロセスの概要

Adobe Commerce プロジェクトのアップグレードは、ストアのセキュリティを確保し、PCI に準拠し、最高の効率で運営するために重要です。 このガイドでは、アップグレードを準備する際の主な考慮事項について説明します。

このガイドでは、Adobe Commerceの一般的なアップグレードジャーニーの概要と、そのジャーニーに従うためのベストプラクティスを説明します。 また、アップグレードプロセスの技術的な詳細と、タイムリーな例、最新バージョンのAdobe Commerceへのアップグレードに関する手順についても説明します。 Adobe Commerce[ リリーススケジュール ](../release/schedule.md) を確認し、早くアップグレードの準備を開始することが重要です。 Adobeでは、マーチャントの計画プロセスを容易にするためにリリーススケジュールを毎年公開しており、各パッチリリースサイクルをアップグレードすることをお勧めします。 PCI 準拠を維持するには、マーチャントは最新のパッチまたはセキュリティパッチを使用する必要があります。

## このガイドは誰を対象としていますか？

このガイドの対象読者は次のとおりです。

- **E コマースマネージャーとテクニカルディレクター** - アップグレードジャーニー、定期的なアップグレードの重要性、アップグレードを計画および準備する最適な方法について説明します。
- **運用チームと開発チーム** – 最新バージョンのAdobe Commerceへのアップグレードに必要な技術手順と、プロセスをより簡単に、迅速に、より手頃な価格で利用できるツールについて説明します。

## アップグレードプロセス

Adobe Commerceを選択した理由の 1 つに、次のものが含まれる可能性があります。

- すぐに使用できる幅広い機能セット
- コアコードとは別に提供される SaaS 機能
- Marketplace 拡張機能の堅牢な製品
- 独自の機能により、無限の柔軟性を実現。ビジネスおよび顧客のニーズに最適に対応するようにサイトをカスタマイズできます。

ただし、拡張性とカスタマイズ性に優れた製品というメリットは、カスタマイズがベストプラクティスに従ってコーディングされていない場合にアップグレードに関する潜在的な問題を引き起こし、予想よりも高いアップグレードコストにつながる可能性があります。

_アップグレードする理由は何ですか？_

アップグレードにより、ビジネスは急速に変化する e コマース業界で機敏に動き続けることができます。また、プラットフォームはセールスとコンバージョンを最大化するための最新のAdobe Commerce機能と互換性があります。 定期的なメンテナンスプランにアップグレードを含めることは、ストアのセキュリティを確保し、PCI に準拠し、ピーク時の効率で運用するために重要です。

### セキュリティ

セキュリティインシデントの 83% が古いソフトウェアで発生しているので、セキュリティはアップグレードの主な理由の 1 つです。 [IBM](https://www.ibm.com/reports/data-breach) によると、データ漏洩の平均コストは 386 万ドルであり、アップグレードによってこのリスクを軽減するためのコストよりもはるかに高くなっています。 Adobeでは、年間を通じてストアのセキュリティを維持する 2 つの方法を提供しています。

- **パッチリリース** - セキュリティ、パフォーマンス、品質、優先度の高いバグ修正が含まれます。
- **セキュリティパッチリリース** - サイトのセキュリティを維持し、実装を容易にする修正および機能強化が含まれています。

### パフォーマンス

パフォーマンスもアップグレードの主な理由の 1 つです。 [HubSpot](https://blog.hubspot.com/marketing/page-load-time-conversion-rates) によると、最初の 5 秒間の読み込み時間はコンバージョン率に大きな影響を与え、その後は 1 秒ごとに待ち時間が–4.4% の影響を与えます。 これは、ページの速度が主要な SEO ランキング要因であるという事実と相まって、サイトのパフォーマンスが、維持し、定期的に改善するためのサイトの重要な要素である理由を示しています。 各パッチリリースにはパフォーマンスの向上が含まれているので、新しいリリースを活用することで、成長計画をサポートし、ビジネスの競争力を維持できます。

### 遅延コスト

プラットフォームのアップグレードを延期または延期する場合、多くの場合、直ちにコストが発生します。 ただし、古いバージョンのソフトウェアを実行する場合の実際のコストははるかに大きく、ビジネスに永続的な影響を与える可能性があります。

直観的には思えませんが、定期的なプラットフォームアップデートは、遅延によって蓄積された技術的負債が原因で、頻度の低いアップデートよりも全体的な労力がかからない場合があります。 Adobeは最近、頻繁に、一貫性のない（毎年またはそれ以上）アップグレードを行っていた小売業者を持つパートナーと働きました。 アップグレードへのアプローチ方法を変革し、12 か月にわたるAdobe推奨の定期的なアップグレードパスに従うことで、パートナーはクライアントの 4 週間分に相当する開発時間、労力、関連コストを節約することができました。 その後、これらのコストは、ビジネスの成長を促進するイニシアチブにリダイレクトできます。

アップデートが定期的に実行されると、変更は増分的に行われ、対応するアップグレード作業にはこれが反映されます。 プラットフォームのアップデートが長期間延期されると、それがより複雑なプロセスになる可能性があります。 さらに、[Adobe Commerce Marketplace](https://marketplace.magento.com/) やその他のサードパーティ製統合で使用する拡張機能も影響を受ける可能性があります。 最後に、アップグレードの調査、計画、遅延の実行に要する時間がすべて延長され、回避できる労力とコストが追加されます。

プロジェクトのアップグレードの作業レベルに影響を与える一般的な要因には、次のようなものがありますが、これらに限定されません。

| 技術的な複雑さ | 計画と戦略 |
|-----------------------------------------------------------|--------------------------------------------------------------|
| カスタマイズの範囲 | 要件の明確さ、決定の揺らぎ、範囲の抜け道 |
| 拡張機能の数 | アップグレードの頻度 |
| サードパーティ（OMS、ERP）との統合数 | テスト方法 |
| ベストプラクティスへのコーディング |                                                              |

デジタルコマース分野で成長が続くことで、企業はより速く、より頻繁に、そして予測不可能な方法で発展しなければならないというプレッシャーを強められている。 顧客の購買行動を常に把握し予測する取り組みの失敗は、最も大きく、最も確立されたブランドでさえ競争条件を平準化しました。 パフォーマンスと稼働時間を損なうことなく、すべてのタッチポイントにわたって堅牢でパーソナライズされたエクスペリエンスを提供できる必要があります。 グローバルな競合他社に先んじてイノベーションを行うには、限界なくイノベーションを加速させる能力が必要です。 アップグレードすることで、お客様のビジネスを将来的に実証し、動的な顧客ニーズに対するより優れたサービスを提供できるようになります。
