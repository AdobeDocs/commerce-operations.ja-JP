---
title: Project Governance
description: Apply our project governance recommendations to your Adobe Commerce implementation.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---


# プロジェクトガバナンス

Project governance is an oversight function aligned with the organization’s governance structure and encompasses the project life cycle. It provides the project manager and team with structure, processes, decision-making models, and tools for managing and controlling the project, while also ensuring the successful delivery of the project. プロジェクトガバナンスは、特に複雑で戦略的なプロジェクトにとって重要な要素です。

ガバナンスモデルは、カスタムで効果的な慣行を定義、ドキュメント、伝達し、プロジェクトを制御し、成功を確実にするために各レベルで定期的に表示する包括的な方法を提供します。 It contains a framework for making decisions; defines roles, responsibilities, and liabilities for the accomplishment of the project; and governs the effectiveness. ガバナンスの構造は、実行チームからエグゼクティブ管理に至るまで、アクティビティ、レポート、エスカレーション、および情報フローを定義します。

![プロジェクトガバナンスの解説図](../../assets/playbooks/project-governance.svg)

At various levels, the teams look into specific sprint and project metrics to understand the progress and take corrective actions as necessary. これらのスプリントレベルの指標には、各スプリントの速度とバーンダウンが含まれます。

## Regular meeting details

- 四半期別のビジネスレビュー

   - 成長エスカレーション戦略の議論

   - 現在の成功と目標を強調

   - 今後の四半期に必要な結果に基づいて調整

- 月次運営委員会

   - プロジェクトの進行状況の調整とレビュー

   - 主要な影響項目に対する意思決定（存在する場合）

   - 電通は顧客満足度を確保し、問題を記録し、対処

- 週次プロジェクト委員会

   - 目標、計画、組織の決定

   - 必要に応じてアーキテクチャの決定を行う

   - Review &amp; act on project status reports

   - プラットフォームと機能のデモ

   - リクエスト/問題/提案のエスカレーション

- 毎日の会議

   - 現在のスプリント/ボード/未払いのチケットを含む、アクション項目について議論し、フォローアップする

   - プロジェクトの進行状況の監視

## Performance KPIs

Apart from the sprint metrics, it is also essential to measure project and quality performance KPIs. Not only does this help to ensure the level of quality throughout the plan, but it keeps the team on track and prevents the project from going off the rails.

## Storyboard and velocity

![かんばんボードの例](../../assets/playbooks/kanban-board-chart.svg)

## スプリントとリリースのバーンダウン

![スプリントとリリースのバーンダウンチャートの例](../../assets/playbooks/sprint-release-burndown.svg)

課題や変更は、プロジェクトの期間中、常に発生します。 課題が発生した場合に、適切な担当者が追跡、測定、ピボットを行えるようにすることで、目標を達成し、その結果に満足できるプロジェクトからの出発確率が高まります。

<table>
<thead>
  <tr>
    <th>主要なパフォーマンス測定</th>
    <th>単位</th>
    <th>レポートされる指標</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>テスト範囲</td>
    <td>%</td>
    <td>テストケースで扱われるテスト可能な要件の数 VS ベースラインでテスト可能な要件の合計</td>
  </tr>
  <tr>
    <td>欠陥密度</td>
    <td>%</td>
    <td># of valid Defects found VS Total of Test cases executed</td>
  </tr>
  <tr>
    <td>SIT/UAT/実稼動環境への欠陥の漏れ</td>
    <td>%</td>
    <td>生産で報告された不具合と生産で報告された不具合+ QA+UAT で報告された不具合</td>
  </tr>
  <tr>
    <td>テストの効果</td>
    <td>%</td>
    <td>発生した有効な欠陥/発生した有効な欠陥です。</td>
  </tr>
  <tr>
    <td>コード品質</td>
    <td># + %</td>
    <td>スプリントの複雑さ、LoC、違反、コードカバレッジ</td>
  </tr>
</tbody>
</table>
