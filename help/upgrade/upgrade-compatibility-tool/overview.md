---
title: の概要 [!DNL Upgrade Compatibility Tool]
description: 詳しくは、 [!DNL Upgrade Compatibility Tool] Adobe Commerceプロジェクトに役立つ情報です。
source-git-commit: 5ff08d231269ea0bcb69f8c80aa546b171a5e4a0
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---


# ガイドの概要

このガイドは、Adobe Commerceの管理者およびソフトウェアエンジニアを対象としています。 ここには、 [!DNL Upgrade Compatibility Tool]、およびその設定と管理。 ここでは、コマースのコア設定と機能に関する基本的な知識を前提としています。

## の概要 [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

この [!DNL Upgrade Compatibility Tool] は、Adobe Commerceカスタマイズ済みのインスタンスを特定のバージョンと照合するために、インストールされているすべてのモジュールとコアコードを分析するコマンドラインツールです。 新しいバージョンのAdobe Commerceにアップグレードする前に対処する必要がある重要な問題、エラーおよび警告のリストを返します。

詳しくは、 [ツールを実行](../upgrade-compatibility-tool/run.md) を参照してください。

参照： [インストール](../upgrade-compatibility-tool/install.md) を使用して [!DNL Upgrade Compatibility Tool].

参照 [ビデオチュートリアル](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=en) (06:02): [!DNL Upgrade Compatibility Tool].

### ワークフロー

次の図に、 [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] 図](../../assets/upgrade-guide/uct-diagram-v5.png)

### この [!DNL Upgrade Compatibility Tool] 使用例

次の使用例では、Adobe Commerceパートナーがクライアントのインスタンスをアップグレードする際の一般的なプロセスを示します。

1. をダウンロードします。 [!DNL Upgrade Compatibility Tool] Adobe Commerceリポジトリ (`https://repo.magento.com/`) をクリックします。 詳しくは、 [をダウンロードします。 [!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/install.md#download-the-upgrade-compatibility-tool) トピックを参照してください。
1. を実行します。 [!DNL Upgrade Compatibility Tool] 期間中 [ベータ版](https://devdocs.magento.com/release/beta-program.html) 最新の段階 [Adobe Commerceリリース](https://devdocs.magento.com/release/).
1. 現在インストールされている特定のバージョンのAdobe Commerce用のバニラインスタンスを生成します。 詳しくは、 [コントリビューターガイド](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) を参照してください。 `instance` コマンドを使用してバニラインストールを生成します。

   >[!NOTE]
   >
   >バニラインスタンスは、特定のリリースバージョン用に、指定したバージョンタグまたはブランチをクリーンインストールしたものです。

1. この [!DNL Upgrade Compatibility Tool] ソフトウェアエンジニアがアップグレードの複雑さを理解し、アップグレードの労力を見積もるのに役立つアップグレードの問題を特定します。
1. この情報は、関係者と共有されます。
1. アップグレードの予算とタイムラインが定義されます。
1. その後、ソフトウェアエンジニアは、必要なコード変更を行って、破損したモジュールを修正できます。
1. この [!DNL Upgrade Compatibility Tool] を実行して、アップグレードの進行状況を追跡できます。
1. チェックアウトとエンジニアリングはすべて、コードをステージング環境にプッシュできるようになりました。回帰テストでは、すべてのテストが緑であることが確認され、Adobe Commerceのプレリリース日と同じ日に最新のAdobe Commerceバージョンを実稼動環境にリリースできます。

   ![[!DNL Upgrade Compatibility Tool] audience](../../assets/upgrade-guide/audience-uct-v3.png)

### 改善に役立つ [!DNL Upgrade Compatibility Tool]

このガイドに記載されていない情報や質問がある場合は、次のリソースを使用してください。

を [!DNL Upgrade Compatibility Tool] チーム、エンジニアリングSlackチャネルでお問い合わせください [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F). ツールの改善に役立つフィードバック、問題、提案をお聞かせください。

この [!DNL Upgrade Compatibility Tool] で定義されたルールを使用 [コーディング規格](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html) プロジェクトがAdobe Commerceのベストプラクティスに従っていること、およびの改善と拡張に役立っていることを確認する [!DNL Upgrade Compatibility Tool].

詳しくは、 [投稿](https://devdocs.magento.com/guides/v2.4/coding-standards/contributing.html)  トピックを参照してください。

### リソース

Adobe Commerceのアップグレードを理解できるよう、以下のリソースを開発しました。

- [アップグレードガイド](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html)
- [今後のリリース](https://devdocs.magento.com/release/)
- [コミュニティリソース](https://devdocs.magento.com/community/resources/resources.html) ページを参照してください。
- [関連ツール](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/related-tools.html)
