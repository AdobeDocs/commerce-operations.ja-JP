---
title: Git ブランチのベストプラクティス
description: ソースコード管理のための様々なブランチ戦略について説明します。
feature: Best Practices
role: Developer
exl-id: 7d7736e8-7023-4315-9965-71866b0be5c3
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Git ブランチのベストプラクティス

ソースコードは、開発プロセスの間、複数の安定性フェーズを経ます。

- 積極的な開発
- 初期コード統合
- 品質保証（QA）のためのコード統合
- 最終的なユーザー受け入れテスト（UAT）のためのコード統合
- 実稼動リリースの最終コード統合

## 影響を受ける製品とバージョン

[サポートされているすべてのバージョン](../../../release/versions.md) （件中）:

- クラウドインフラストラクチャー上のAdobe Commerce
- Adobe Commerceオンプレミス

## 支店の管理

各開発フェーズには、コードの変更を追跡し、デプロイメントプロセスを容易にする対応するブランチを Git に含める必要があります。

- **タスク分岐** – 開発者が、機能やバグ修正などの特定のタスクを実装する際に、個々のコードの変更をコミットする場所。
- **開発課** – 複数の開発者が、個々のタスクの分岐から単一の開発の分岐に変更をマージして、自動統合テストを実行できる場合。 このブランチは開発環境にデプロイされます。
- **QA ブランチ** – 開発が完了し、コードがすべての自動統合テストとコードレビューに合格した後、開発者が変更を結合する場所。 このブランチは、手動で QA テストを行うために QA 環境にデプロイされます。
- **安定/UAT 分岐** – 手動の QA テストに合格した後にコードがマージされる場合。 このブランチは、ユーザー受け入れテスト用に UAT 環境にデプロイされます。
- **実稼働/リリースブランチ**- UAT を通過した後にコードがマージされる場合。 このブランチは、リリースの実稼動環境にデプロイされます。

>[!TIP]
>
>クラウドインフラストラクチャプロジェクト上のAdobe Commerceには、様々な環境に対応する特定のブランチが含まれます。 を参照してください。 [プロプロジェクトワークフロー](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html) および [スタータープロジェクトワークフロー](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/starter-develop-deploy-workflow.html) が含まれる _クラウドガイド_.

## ブランチ戦略

使用できる分岐戦略はいくつかあります。 開発チームとプロジェクトの複雑さに最適な戦略を選択します。

詳しくは、次の外部リソースを参照してください。

- [ワークフローのブランチ](https://git-scm.com/book/en/v2/Git-Branching-Branching-Workflows)
- [分散ワークフロー](https://git-scm.com/book/en/v2/Distributed-Git-Distributed-Workflows)
- [ソースコードブランチを管理するためのパターン](https://martinfowler.com/articles/branching-patterns.html)
- [成功した Git ブランチモデル](https://nvie.com/posts/a-successful-git-branching-model/)
- [GitHub フロー](https://docs.github.com/en/get-started/quickstart/github-flow)
- [GitLab フロー](https://about.gitlab.com/blog/2023/07/27/gitlab-flow-duo/)
