---
title: 実装フェーズ
description: Adobe Commerce プロジェクトの実装フェーズに関するベストプラクティスについて説明します。
exl-id: c5272f79-7315-46dc-a191-a40004aaa812
feature: Best Practices
last-update: 2026-01-20
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: a3c0eba7bdcd8017e88bdb4df1f45d77fe4bb351
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 7%
---
# 実装のベストプラクティス

Adobe Commerce プロジェクトを実装するには、多くの方法があります。 この節で説明するベストプラクティスでは、Adobeがお客様やパートナーに対して特定のユースケースの実装を期待する方法について説明します。 これらのレコメンデーションは、サイトの設定とカスタマイズ、デプロイメント、運用、パフォーマンス、アップグレードに関する一般的な問題と、潜在的な問題を回避するために設計されています。

これらのベストプラクティスは、実装フェーズごとに整理されているため、ユースケースに適用される推奨事項を見つけることができます。

<table style="table-layout:fixed">
<tr>
  <td>
    <a href="planning/overview.md">
    <img alt="計画" src="../../assets/icons/enterprise.svg" width="80" height="80"/>
    </a>
    <div>
    <a href="planning/overview.md"><strong>計画</strong></a>
    </div>
    要件収集、アーキテクチャデザイン、カタログデザイン、プロジェクトスコープ、アカウントプロビジョニング、ユーザーアクセス、拡張機能の購入
    <br>
  </td>
  <td>
    <a href="development/overview.md">
      <img alt="開発" src="../../assets/icons/page-rule.svg" width="80" height="80">
    </a>
    <div>
    <a href="development/overview.md"><strong>開発</strong></a>
    </div>
    ローカルおよびステージング環境の設定、トラブルシューティング、コード管理、スプリント計画、スプリントレビュー、受け入れテスト、顧客のサインオフ
    <br>
  </td>
  <td>
    <a href="launch/overview.md">
      <img alt="Launch" src="../../assets/icons/launch.svg" width="80" height="80">
    </a>
    <div>
    <a href="launch/overview.md"><strong>起動</strong></a>
    </div>
    ローンチ前後の最終的なチェックリストのレビュー、本番環境への導入、セキュリティ設定、サービス検証、パフォーマンス監視  
    <br>
  </td>
  <td>
    <a href="maintenance/overview.md">
      <img alt="保守" src="../../assets/icons/gauge.svg" width="80" height="80">
    </a>
    <div>
    <a href="maintenance/overview.md"><strong> メンテナンス </strong></a>
    </div>
    サイト監視，カタログ管理，インデックス作成，設定，機能強化，バグ修正，マネージドサービス，アップグレード   
    <br>
  </td>
</tr>
</table>

{{$include /help/_includes/templated/whats-new-bp.md}}

<!-- Last updated from includes: 2026-01-15 15:39:03 -->
