---
title: ' [!DNL Upgrade Compatibility Tool]の概要'
description: ' [!DNL Upgrade Compatibility Tool] と、それがAdobe Commerce プロジェクトにどのように役立つかについて説明します。'
exl-id: 9493406a-1690-462b-b119-1b685b026c0b
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# ガイド概要

{{commerce-only}}

このガイドは、Adobe Commerceの管理者およびソフトウェアエンジニアを対象としています。 [!DNL Upgrade Compatibility Tool]のインストールに関する詳細情報と、その設定と管理が含まれています。 Commerceのコア設定と機能に関する基本的な理解が必要です。

## [!DNL Upgrade Compatibility Tool]の概要

[!DNL Upgrade Compatibility Tool]は、Adobe Commerceでカスタマイズされたインスタンスを、そのインスタンスにインストールされているすべてのモジュールとコアコードを分析して、特定のバージョンと比較するツールです。 新しいバージョンのAdobe Commerceにアップグレードする前に対処する必要がある重大な問題、エラー、警告のリストが返されます。

## [!DNL Upgrade Compatibility Tool]を使用

[!DNL Upgrade Compatibility Tool]は次の方法で使用できます。

- スタンドアロンの[&#x200B; コマンドラインインターフェイス &#x200B;](../upgrade-compatibility-tool/run.md) ツールとして。 使用可能なコマンドの完全なリストについては、[`bin/uct` リファレンス &#x200B;](../../tools/reference/uct.md)を参照してください。
- [!DNL Upgrade Compatibility Tool]を[[!DNL Site-Wide Analysis Tool]](../upgrade-compatibility-tool/integrate-analysis-tool.md)と統合しています。
- [Magento PHPStorm プラグイン &#x200B;](../upgrade-compatibility-tool/run-configuration-phpstorm-plugin.md)内の実行設定。

## ワークフロー

次の図は、[!DNL Upgrade Compatibility Tool]を実行する際に考えられるワークフローを示しています。

![[!DNL Upgrade Compatibility Tool]図](../../assets/upgrade-guide/uct-diagram-v5.png)

## [!DNL Upgrade Compatibility Tool] デモ

[!DNL Upgrade Compatibility Tool]について詳しくは、このビデオをご覧ください。

>[!VIDEO](https://video.tv.adobe.com/v/344385?captions=jpn&quality=12)

## [!DNL Upgrade Compatibility Tool]の改善にご協力ください

このガイドで説明されていない情報や質問が必要な場合は、次のリソースを使用してください。

[!DNL Upgrade Compatibility Tool] チームとつながるには、エンジニアリング Slack チャンネル [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F)でお問い合わせください。 フィードバック、問題、提案を聞いて、ツールの改善に役立てたいと考えています。

[!DNL Upgrade Compatibility Tool]では、[&#x200B; コーディング標準](https://developer.adobe.com/commerce/php/coding-standards/)で定義されたルールを使用して、プロジェクトがAdobe Commerceのベストプラクティスに従っていることを確認し、[!DNL Upgrade Compatibility Tool]の改善と拡張を支援します。

コーディング標準の提供について詳しくは、[Contribute](https://developer.adobe.com/commerce/php/coding-standards/contributing) トピックを参照してください。

## リソース

Adobe Commerceのアップグレードについて理解するには、次の資料を参照してください。

- [&#x200B; アップグレードガイド &#x200B;](../overview.md)では、Adobe Commerceの一般的なアップグレードジャーニーとそのジャーニーに従うべきベストプラクティスの概要を説明しています。
- [今後のリリース &#x200B;](/help/release/schedule.md) ページには、スケジュール済みリリースと今後のリリースの日付が表示されます。
- [&#x200B; コミュニティリソース &#x200B;](https://developer.adobe.com/commerce/contributor/community/) ページは、ディスカッションを開始するか、より多くの情報を見つけるために配置されます。
- [関連ツール &#x200B;](../upgrade-compatibility-tool/related-tools.md) ページで、一般的なアップグレードジャーニーに役立つツールを確認してください。
