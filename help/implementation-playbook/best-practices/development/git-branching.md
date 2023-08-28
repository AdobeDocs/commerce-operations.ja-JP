---
title: Git ブランチのベストプラクティス
description: ソースコード管理のための様々な分岐戦略について説明します。
feature: Best Practices
role: Developer
source-git-commit: 9b1c3f7ca56cb6baf262bbd4abc732a30a7eb0ed
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---


# Git ブランチのベストプラクティス

ソース・コードは、開発プロセス中に複数の安定性フェーズを経て処理されます。

- アクティブな開発
- 初期コード統合
- 品質保証のためのコード統合 (QA)
- 最終的なユーザー受け入れテスト (UAT) のためのコード統合
- 実稼動リリース用の最終コード統合

## 影響を受ける製品およびバージョン

[サポートされているすべてのバージョン](../../../release/versions.md) /:

- Adobe Commerce an cloud infrastructure
- Adobe Commerceオンプレミス

## 支店管理

コードの変更を追跡し、デプロイメントプロセスを容易にするために、各開発フェーズに Git 内に対応するブランチが必要です。

- **タスクブランチ** — 機能やバグ修正など、特定のタスクを実装する際に、開発者が個々のコード変更をコミットする場所。
- **開発ブランチ** — 複数の開発者が、個々のタスクブランチの変更を、自動統合テスト用の単一の開発ブランチにマージする場合。 このブランチは、開発環境にデプロイされます。
- **QA ブランチ** — 開発が完了し、コードがすべての自動統合テストとコードレビューに合格した後で、開発者が変更をマージする場合。 このブランチは、手動の QA テスト用に QA 環境にデプロイされます。
- **安定/UAT 分岐** — 手動の QA テストの合格後にコードが結合される場所。 このブランチは、ユーザー受け入れテスト用に UAT 環境にデプロイされます。
- **実稼動/リリースブランチ**— UAT を渡した後にコードが結合される場所。 このブランチは、リリース用に実稼動環境にデプロイされます。

>[!TIP]
>
>Adobe Commerce on cloud infrastructure プロジェクトには、異なる環境に対応する特定のブランチが含まれます。 詳しくは、 [Pro プロジェクトのワークフロー](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html) および [スタータープロジェクトワークフロー](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/starter-develop-deploy-workflow.html) （内） _クラウドガイド_.

## ブランチ戦略

使用できる分岐戦略はいくつかあります。 開発チームやプロジェクトの複雑さに最適な戦略を選択します。

詳しくは、次の外部リソースを参照してください。

- [分岐ワークフロー](https://git-scm.com/book/en/v2/Git-Branching-Branching-Workflows)
- [分散ワークフロー](https://git-scm.com/book/en/v2/Distributed-Git-Distributed-Workflows)
- [ソースコードブランチを管理するためのパターン](https://martinfowler.com/articles/branching-patterns.html)
- [成功した Git 分岐モデル](https://nvie.com/posts/a-successful-git-branching-model/)
- [GitHub フロー](https://docs.github.com/en/get-started/quickstart/github-flow)
- [GitLab フロー](https://about.gitlab.com/blog/2023/07/27/gitlab-flow-duo/)
