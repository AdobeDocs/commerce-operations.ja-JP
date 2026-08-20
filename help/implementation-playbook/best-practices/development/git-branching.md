---
title: Git分岐のベストプラクティス
description: ソースコード管理のさまざまな分岐戦略について説明します。
feature: Best Practices
role: Developer
exl-id: 7d7736e8-7023-4315-9965-71866b0be5c3
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# Git分岐のベストプラクティス

Source コードは、開発プロセス中に複数の安定性フェーズを経ます。

- アクティブな開発
- 最初のコード統合
- 品質保証（QA）のためのコード統合
- 最終ユーザー受け入れテスト（UAT）用のコード統合
- 実稼動リリースの最終コード統合

## 影響を受ける製品とバージョン

[&#x200B; サポートされているすべてのバージョン &#x200B;](../../../release/versions.md) /:

- Adobe Commerce on cloud infrastructure
- Adobe Commerce オンプレミス

## 分岐管理

コードの変更を追跡し、デプロイメントプロセスを促進するために、各開発フェーズにはGit内の対応するブランチが必要です。

- **タスクブランチ** – 開発者が機能やバグ修正などの特定のタスクを実装する際に、個々のコードの変更をコミットする場所。
- **開発ブランチ** – 複数の開発者が、自動化された統合テストのために、個々のタスクブランチからの変更を単一の開発ブランチにマージします。 このブランチは開発環境にデプロイされます。
- **QA ブランチ** – 開発が完了し、コードがすべての自動統合テストとコードレビューに合格した後に、開発者が変更をマージする場所。 このブランチは、手動QA テスト用にQA環境にデプロイされます。
- **Stable/UAT ブランチ**：手動のQA テストに合格した後にコードが結合される場所。 このブランチは、ユーザー受け入れテスト用にUAT環境にデプロイされます。
- **実稼動/リリースブランチ**：コードがUATを通過した後に結合される場所。 このブランチはリリース用に実稼動環境にデプロイされます。

>[!TIP]
>
>Adobe Commerceのクラウドインフラストラクチャプロジェクトには、さまざまな環境に対応する特定のブランチが含まれています。 _クラウドガイド_&#x200B;の[Pro プロジェクトワークフロー](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/architecture/pro-develop-deploy-workflow)および[&#x200B; スタータープロジェクトワークフロー](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/architecture/starter-develop-deploy-workflow)を参照してください。

## ブランチ戦略

ここでは、いくつかの分岐戦略を紹介します。 開発チームとプロジェクトの複雑さに最適な戦略を選びましょう。

詳しくは、次の外部リソースを参照してください。

- [分岐ワークフロー](https://git-scm.com/book/en/v2/Git-Branching-Branching-Workflows)
- [分散ワークフロー](https://git-scm.com/book/en/v2/Distributed-Git-Distributed-Workflows)
- [ソースコードのブランチを管理するためのパターン](https://martinfowler.com/articles/branching-patterns.html)
- [Git分岐モデルの成功](https://nvie.com/posts/a-successful-git-branching-model/)
- [GitHub フロー](https://docs.github.com/en/get-started/quickstart/github-flow)
- [GitLab フロー](https://about.gitlab.com/blog/2023/07/27/gitlab-flow-duo/)
