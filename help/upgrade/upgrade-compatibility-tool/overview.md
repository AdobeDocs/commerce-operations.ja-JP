---
title: の概要 [!DNL Upgrade Compatibility Tool]
description: について説明します [!DNL Upgrade Compatibility Tool] Adobe Commerce プロジェクトにどのように役立つか、および役立つ情報を提供します。
exl-id: 9493406a-1690-462b-b119-1b685b026c0b
source-git-commit: fc1be3362863d3b0fa3468380fe62ca698abac43
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# ガイドの概要

{{commerce-only}}

このガイドは、Adobe Commerceの管理者およびソフトウェアエンジニアを対象としています。 のインストールに関する詳細情報が含まれています [!DNL Upgrade Compatibility Tool]、およびその設定と管理。 ここでは、Commerceのコア設定と機能に関する基本的な知識を前提としています。

## の概要 [!DNL Upgrade Compatibility Tool]

この [!DNL Upgrade Compatibility Tool] は、インストールされているすべてのモジュールとコアコードを分析して、Adobe Commerceのカスタマイズ済みインスタンスを特定のバージョンと照合するツールです。 新しいバージョンのAdobe Commerceにアップグレードする前に対処する必要がある重要な問題、エラー、警告のリストを返します。

## の使用 [!DNL Upgrade Compatibility Tool]

を使用できます [!DNL Upgrade Compatibility Tool] 次を使用：

- スタンドアロンとして [コマンドラインインターフェイス](../upgrade-compatibility-tool/run.md) ツール。 使用できるコマンドの完全なリストについては、を参照してください [`bin/uct` 参照](../../tools/reference/uct.md).
- の統合 [!DNL Upgrade Compatibility Tool] （を使用） [[!DNL Site-Wide Analysis Tool]](../upgrade-compatibility-tool/integrate-analysis-tool.md).
- 内での実行設定 [Magento PHPStorm プラグイン](../upgrade-compatibility-tool/run-configuration-phpstorm-plugin.md).

## ワークフロー

次の図は、 [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] 図](../../assets/upgrade-guide/uct-diagram-v5.png)

## [!DNL Upgrade Compatibility Tool] デモ

について詳しくは、このビデオをご覧ください [!DNL Upgrade Compatibility Tool]:

>[!VIDEO](https://video.tv.adobe.com/v/341245?quality=12)

## の改善に役立つ [!DNL Upgrade Compatibility Tool]

情報が必要な場合や、このガイドで扱われていない質問がある場合は、次のリソースを使用してください。

を使用してを接続するには [!DNL Upgrade Compatibility Tool] チーム、エンジニアリングSlackチャネルでお問い合わせ [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F). ツールの改善に役立てるため、フィードバック、問題、提案をお聞かせください。

この [!DNL Upgrade Compatibility Tool] 内で定義されたルールを使用 [コーディング基準](https://developer.adobe.com/commerce/php/coding-standards/) プロジェクトがAdobe Commerceのベストプラクティスに従っていることを確認し、を改善して拡張するのに役立ちます。 [!DNL Upgrade Compatibility Tool].

を参照してください。 [参加](https://developer.adobe.com/commerce/php/coding-standards/contributing/) コーディング標準のコントリビューションに関する詳細は、を参照してください。

## リソース

Adobe Commerceのアップグレードについて理解するには、次のリソースを参照してください。

- この [アップグレードガイド](../overview.md) Adobe Commerceの一般的なアップグレードジャーニーと、そのジャーニーに従うためのベストプラクティスの概要を説明します。
- この [今後のリリース](https://devdocs.magento.com/release/) このページには、予定されているリリースと今後のリリースの日付が表示されます。
- この [コミュニティリソース](https://developer.adobe.com/commerce/contributor/community/) ページは、ディスカッションを開始したり、詳細情報を検索したりするための場所です。
- を確認します [関連ツール](../upgrade-compatibility-tool/related-tools.md) 一般的なアップグレードジャーニーに役立つツールについて説明します。
