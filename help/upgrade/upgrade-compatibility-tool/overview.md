---
title: の概要  [!DNL Upgrade Compatibility Tool]
description: ' [!DNL Upgrade Compatibility Tool]  と、Adobe Commerce プロジェクトに役立つ方法について説明します。'
exl-id: 9493406a-1690-462b-b119-1b685b026c0b
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# ガイドの概要

{{commerce-only}}

このガイドは、Adobe Commerceの管理者およびソフトウェアエンジニアを対象としています。 [!DNL Upgrade Compatibility Tool] のインストールに関する詳細情報と、設定および管理に関する情報が含まれています。 ここでは、Commerceのコア設定と機能に関する基本的な知識を前提としています。

## [!DNL Upgrade Compatibility Tool] の概要

[!DNL Upgrade Compatibility Tool] は、インストールされているすべてのモジュールとコアコードを分析して、Adobe Commerceのカスタマイズされたインスタンスを特定のバージョンと照合するツールです。 新しいバージョンのAdobe Commerceにアップグレードする前に対処する必要がある重要な問題、エラー、警告のリストを返します。

## [!DNL Upgrade Compatibility Tool] の使用

[!DNL Upgrade Compatibility Tool] は以下を介して使用できます。

- スタンドアロンの [ コマンドラインインターフェイス ](../upgrade-compatibility-tool/run.md) ツールとして。 使用可能なコマンドの完全なリストについては、[`bin/uct` リファレンスを参照してください ](../../tools/reference/uct.md)。
- [!DNL Upgrade Compatibility Tool] と [[!DNL Site-Wide Analysis Tool]](../upgrade-compatibility-tool/integrate-analysis-tool.md) の統合
- [Magento PHPStorm プラグイン ](../upgrade-compatibility-tool/run-configuration-phpstorm-plugin.md) 内の実行構成。

## ワークフロー

次の図は、[!DNL Upgrade Compatibility Tool] を実行した場合に可能なワークフローを示しています。

![[!DNL Upgrade Compatibility Tool] 図 ](../../assets/upgrade-guide/uct-diagram-v5.png)

## [!DNL Upgrade Compatibility Tool] デモ

[!DNL Upgrade Compatibility Tool] について詳しくは、このビデオをご覧ください。

>[!VIDEO](https://video.tv.adobe.com/v/341245?quality=12)

## [!DNL Upgrade Compatibility Tool] の改善に役立つ

情報が必要な場合や、このガイドで扱われていない質問がある場合は、次のリソースを使用してください。

[!DNL Upgrade Compatibility Tool] チームとつながるには、エンジニアリングSlackチャネル [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F) でお問い合わせください。 ツールの改善に役立てるため、フィードバック、問題、提案をお聞かせください。

この [!DNL Upgrade Compatibility Tool] では、アドビの [ コーディング標準 ](https://developer.adobe.com/commerce/php/coding-standards/) 内で定義されたルールを使用して、プロジェクトがAdobe Commerceのベストプラクティスに従っていることを確認し、プロジェクトの改善と拡 [!DNL Upgrade Compatibility Tool] に役立てます。

コーディング標準のコントリビューションの詳細については、[Contribute](https://developer.adobe.com/commerce/php/coding-standards/contributing/) を参照してください。

## リソース

Adobe Commerceのアップグレードについて理解するには、次のリソースを参照してください。

- [ アップグレードガイド ](../overview.md) では、Adobe Commerceの一般的なアップグレードジャーニーと、そのジャーニーに従うためのベストプラクティスの概要を説明します。
- [ 今後のリリース ](https://experienceleague.adobe.com/ja/docs/commerce-operations/release/planning/schedule) ページには、予定リリースと今後のリリースの日付が表示されます。
- [ コミュニティリソース ](https://developer.adobe.com/commerce/contributor/community/) ページでは、ディスカッションを開始したり、詳細情報を検索したりできます。
- 一般的なアップグレードジャーニーで役に立つツールについては、[ 関連ツール ](../upgrade-compatibility-tool/related-tools.md) ページを確認してください。
