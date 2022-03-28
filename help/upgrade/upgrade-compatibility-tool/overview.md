---
title: の概要 [!DNL Upgrade Compatibility Tool]
description: 詳しくは、 [!DNL Upgrade Compatibility Tool] Adobe Commerceプロジェクトに役立つ情報です。
source-git-commit: fbe47245623469a93cce5cc5a83baf467a007bc4
workflow-type: tm+mt
source-wordcount: '608'
ht-degree: 0%

---


# の概要 [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

この [!DNL Upgrade Compatibility Tool] は、Adobe Commerceカスタマイズ済みのインスタンスを特定のバージョンと照合するために、インストールされているすべてのモジュールとコアコードを分析するコマンドラインツールです。 最新バージョンのAdobe Commerceにアップグレードする前に対処する必要がある重要な問題、エラーおよび警告のリストを返します。 また、新しいバージョンのAdobe Commerceにアップグレードする前にコードで修正する必要がある潜在的な問題も識別します。

この [!DNL Upgrade Compatibility Tool] では、いつコアコードがカスタマイズされた機能に変更されたかを識別できます。 詳しくは、 [ツールを実行](../upgrade-compatibility-tool/run.md) トピックを参照してください。

これは、Adobe Commerceバージョンのリリースごとに、Composer パッケージとして配布されます。 詳しくは、 [開発者](../upgrade-compatibility-tool/developer.md) トピックを参照してください。

詳しくは、 [インストール](../upgrade-compatibility-tool/install.md) の最初の手順のトピック [!DNL Upgrade Compatibility Tool].

## ワークフロー

次の図は、 [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] 図](../../assets/upgrade-guide/mvp-diagram-v3.png)

## この [!DNL Upgrade Compatibility Tool] 使用例

次の使用例では、Adobe Commerceパートナーがクライアントのインスタンスをアップグレードする際の一般的なプロセスを示します。

1. をダウンロードします。 [!DNL Upgrade Compatibility Tool] Adobe Commerceリポジトリ (`https://repo.magento.com/`) をクリックします。 詳しくは、 [をダウンロードします。 [!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/install.md#download-the-upgrade-compatibility-tool) トピックを参照してください。
1. を実行します。 [!DNL Upgrade Compatibility Tool] 期間中 [ベータ版](https://devdocs.magento.com/release/beta-program.html) 最新の段階 [Adobe Commerceリリース](https://devdocs.magento.com/release/).
1. 主なコマンドは次のとおりです。 `upgrade:check`. このコマンドは、インスタンスを分析し、インスタンス内のエラー、警告、および重要な問題を確認します。 結果を最適化するには：

   - オプションを追加 `--ignore-current-version-compatibility-issues` を使用して、現在のAdobe Commerceバージョンに対する既知の重要な問題、エラーおよび警告をすべて無視します。 目的のバージョンの結果のみを表示します。
   - オプションを使用 `--min-issue-level` をクリックして、最小の問題レベルを設定します。 アップグレードに関する最も重要な問題のみを優先順位付けするのに役立ちます。 特定のベンダー、モジュール、またはディレクトリのみを分析する場合は、パスも指定できます。 詳しくは、 [ツールを実行](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/run.html?lang=en) トピックを参照してください。

1. 現在インストールされている特定のバージョンのAdobe Commerce用のバニラインスタンスを生成します。 詳しくは、 [コントリビューターガイド](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) を参照してください。 `instance` コマンドを使用してバニラインストールを生成します。

   >[!NOTE]
   >
   >バニラインスタンスは、特定のリリースバージョン用に、指定したバージョンタグまたはブランチをクリーンインストールしたものです。

1. この [!DNL Upgrade Compatibility Tool] カスタマイズされた壊れた領域を識別します。 ソフトウェアエンジニアは、アップグレードの複雑さを理解し、作業量を見積もることができます。 この情報は、関係者と共有されます。
1. アップグレードの予算とタイムラインが定義されます。
1. その後、ソフトウェアエンジニアは、必要なコード変更を行って、破損したモジュールを修正できます。
1. この [!DNL Upgrade Compatibility Tool] を実行して、アップグレードの進行状況を追跡できます。
1. チェックアウトとエンジニアリングはすべて、コードをステージング環境にプッシュできるようになりました。回帰テストでは、すべてのテストが緑であることが確認され、Adobe Commerceのプレリリース日と同じ日に最新のAdobe Commerceバージョンを実稼動環境にリリースできます。

   ![[!DNL Upgrade Compatibility Tool] audience](../../assets/upgrade-guide/audience-uct-v3.png)

## 改善に役立つ [!DNL Upgrade Compatibility Tool]

を [!DNL Upgrade Compatibility Tool] チーム、エンジニアリングSlackチャネルでお問い合わせください [[!DNL Upgrade Compatibility Tool]](https://magentocommeng.slack.com/archives/C019Y143U9F). ツールの改善に役立つフィードバック、問題、提案をお聞かせください。

この [!DNL Upgrade Compatibility Tool] で定義されたルールを使用 [コーディング規格](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html) プロジェクトがAdobe Commerceのベストプラクティスに従っていること、およびの改善と拡張に役立っていることを確認する [!DNL Upgrade Compatibility Tool].

詳しくは、 [投稿](https://devdocs.magento.com/guides/v2.4/coding-standards/contributing.html)  このプロジェクトへの投稿の詳細については、トピックを参照してください。

## リソース

Adobe Commerceのアップグレードを理解できるよう、以下のリソースを開発しました。

- [アップグレードガイド](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html)
- [今後のリリース](https://devdocs.magento.com/release/)
- [コミュニティリソース](https://devdocs.magento.com/community/resources/resources.html) ページを参照してください。
