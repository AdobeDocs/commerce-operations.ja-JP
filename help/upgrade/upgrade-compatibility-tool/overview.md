---
title: の概要 [!DNL Upgrade Compatibility Tool]
description: 詳しくは、 [!DNL Upgrade Compatibility Tool] Adobe Commerceプロジェクトに役立つ情報です。
exl-id: 9493406a-1690-462b-b119-1b685b026c0b
source-git-commit: ad7f05eaa5f144b5a8616307d65be635a0c499eb
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# ガイドの概要

{{commerce-only}}

このガイドは、Adobe Commerceの管理者およびソフトウェアエンジニアを対象としています。 ここには、 [!DNL Upgrade Compatibility Tool]、およびその設定と管理。 ここでは、コマースのコア設定と機能に関する基本的な知識を前提としています。

## の概要 [!DNL Upgrade Compatibility Tool]

The [!DNL Upgrade Compatibility Tool] は、インストールされているすべてのモジュールとコアコードを分析することで、Adobe Commerceのカスタマイズ済みインスタンスを特定のバージョンと照合するツールです。 新しいバージョンのAdobe Commerceにアップグレードする前に対処する必要がある重要な問題、エラーおよび警告のリストを返します。

## 以下を使用します。 [!DNL Upgrade Compatibility Tool]

以下を使用すると、 [!DNL Upgrade Compatibility Tool] 経由：

- スタンドアロンとして [コマンドラインインターフェイス](../upgrade-compatibility-tool/run.md) ツールを使用します。 使用可能なコマンドの完全なリストについては、 [`bin/uct` 参照](/help/reference/uct.md).
- 統合 [!DNL Upgrade Compatibility Tool] と [[!DNL Site-Wide Analysis Tool]](../upgrade-compatibility-tool/integrate-analysis-tool.md).
- 内の実行設定 [MagentoPHPStorm プラグイン](../upgrade-compatibility-tool/run-configuration-phpstorm-plugin.md).

## ワークフロー

次の図に、 [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] 図](../../assets/upgrade-guide/uct-diagram-v5.png)

## [!DNL Upgrade Compatibility Tool] デモ

このビデオで [!DNL Upgrade Compatibility Tool]:

>[!VIDEO](https://video.tv.adobe.com/v/341245?quality=12)

## 改善に役立つ [!DNL Upgrade Compatibility Tool]

このガイドに記載されていない情報や質問がある場合は、次のリソースを使用してください。

を使用して [!DNL Upgrade Compatibility Tool] チーム、エンジニアリングSlackチャネルでお問い合わせください [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F). ツールの改善に役立つフィードバック、問題、提案をお聞かせください。

The [!DNL Upgrade Compatibility Tool] で定義されたルールを使用 [コーディング規格](https://developer.adobe.com/commerce/php/coding-standards/) プロジェクトがAdobe Commerceのベストプラクティスに従っていること、およびの改善と拡張に役立っていることを確認する [!DNL Upgrade Compatibility Tool].

詳しくは、 [Contribute](https://developer.adobe.com/commerce/php/coding-standards/contributing/) トピックを参照してください。

## リソース

Adobe Commerceのアップグレードについて理解するには、次のリソースを参照してください。

- The [アップグレードガイド](../overview.md) では、一般的なAdobe CommerceまたはMagento Open Sourceアップグレードのジャーニーの概要と、そのジャーニーに従うためのベストプラクティスを示します。
- The [今後のリリース](https://devdocs.magento.com/release/) ページには、予定されているリリースおよび今後のリリースの日付が表示されます。
- The [コミュニティリソース](https://developer.adobe.com/commerce/contributor/community/) ページは、ディスカッションを開始するか、詳細を見つける場所です。
- 次を確認します。 [関連ツール](../upgrade-compatibility-tool/related-tools.md) ページを参照してください。
