---
title: 「 [!DNL Upgrade Compatibility Tool]"
description: 詳しくは、 [!DNL Upgrade Compatibility Tool] Adobe Commerceプロジェクトに役立つ情報です。
source-git-commit: ee949c72e42d329fdfb7f4068aeeb3cdc20e1758
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---


# ガイドの概要

{{commerce-only}}

このガイドは、Adobe Commerceの管理者およびソフトウェアエンジニアを対象としています。 ここには、 [!DNL Upgrade Compatibility Tool]、およびその設定と管理。 ここでは、コマースのコア設定と機能に関する基本的な知識を前提としています。

## の概要 [!DNL Upgrade Compatibility Tool]

この [!DNL Upgrade Compatibility Tool] は、インストールされているすべてのモジュールとコアコードを分析することで、Adobe Commerceのカスタマイズ済みインスタンスを特定のバージョンと照合するツールです。 新しいバージョンのAdobe Commerceにアップグレードする前に対処する必要がある重要な問題、エラーおよび警告のリストを返します。

## 以下を使用： [!DNL Upgrade Compatibility Tool]

以下を使用して、 [!DNL Upgrade Compatibility Tool] 経由：

- スタンドアロンとして [コマンドラインインターフェイス](../upgrade-compatibility-tool/run.md) ツール
- 統合 [!DNL Upgrade Compatibility Tool] と [[!DNL Site-Wide Analysis Tool]](../upgrade-compatibility-tool/integrate-analysis-tool.md).
- 内の実行設定 [MagentoPHPStorm プラグイン](../upgrade-compatibility-tool/run-configuration-phpstorm-plugin.md).

### ワークフロー

次の図に、 [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] 図](../../assets/upgrade-guide/uct-diagram-v5.png)

### 改善に役立つ [!DNL Upgrade Compatibility Tool]

このガイドに記載されていない情報や質問がある場合は、次のリソースを使用してください。

を [!DNL Upgrade Compatibility Tool] チーム、エンジニアリングSlackチャネルでお問い合わせください [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F). ツールの改善に役立つフィードバック、問題、提案をお聞かせください。

この [!DNL Upgrade Compatibility Tool] で定義されたルールを使用 [コーディング規格](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html) プロジェクトがAdobe Commerceのベストプラクティスに従っていること、およびの改善と拡張に役立っていることを確認する [!DNL Upgrade Compatibility Tool].

詳しくは、 [投稿](https://devdocs.magento.com/guides/v2.4/coding-standards/contributing.html) トピックを参照してください。

### リソース

Adobe Commerceのアップグレードについて理解するには、次のリソースを参照してください。

- この [アップグレードガイド](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html) では、一般的なAdobe CommerceまたはMagento Open Sourceアップグレードのジャーニーの概要と、そのジャーニーに従うためのベストプラクティスを示します。
- この [今後のリリース](https://devdocs.magento.com/release/) ページには、予定されているリリースおよび今後のリリースの日付が表示されます。
- この [コミュニティリソース](https://developer.adobe.com/commerce/contributor/community/) ページは、ディスカッションを開始するか、詳細を見つける場所です。
- 次を確認します。 [関連ツール](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/related-tools.html) ページを参照してください。
