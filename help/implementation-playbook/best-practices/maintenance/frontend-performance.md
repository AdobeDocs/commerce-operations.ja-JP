---
title: フロントエンドパフォーマンスの監査
description: web パフォーマンスツールを使用して、Adobe Commerceストアフロントの業務を監査することで、サイトパフォーマンスに悪影響を与える問題を特定し、対処します。
role: Admin, User, Developer
feature: Best Practices
exl-id: bafae565-9d09-4cc0-8507-e89a11dbd915
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%
---
# フロントエンドのパフォーマンスに関するベストプラクティス

web パフォーマンスツールを使用して、Adobe Commerceストアのフロントエンドのパフォーマンスを確認します。
これらのツールでは、さまざまな指標を利用して、オンラインストアのパフォーマンスを向上させるための強力なインサイトとレコメンデーションを提供します。

## 影響を受ける製品とバージョン

[&#x200B; サポートされているすべてのバージョン &#x200B;](../../../release/versions.md) /:

- Adobe Commerce on cloud infrastructure
- Adobe Commerce オンプレミス

## フロントエンドのパフォーマンスを確認

web サイトストアのフロントエンドのパフォーマンスを確認するには：

1. 次のようなweb パフォーマンスツールを使用して、フロントエンドのパフォーマンスを監査します。

   - **[Google Lighthouse](https://web.dev/measure/)**:Lighthouseには、パフォーマンス、アクセシビリティ、プログレッシブ web アプリ、SEOなどの監査があります。 Lighthouseの様々な実行方法について詳しくは、[Lighthouseの概要](https://developer.chrome.com/docs/lighthouse/overview)を参照してください。）
   - **[Google PageSpeed Insights](https://pagespeed.web.dev/)** - PageSpeed Insightsは、web ページのパフォーマンスが低下する原因に関する詳細なレポートと、その解決方法に関する推奨事項をすばやく提供します。

1. 監査レポートを確認し、提供された推奨事項を実施して、ストアのパフォーマンスを向上させます。

## 追加情報

- [管理者ユーザーのインデックス管理](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [CLIを使用したインデックス管理](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html?lang=ja)
- [開発者向けインデックス作成の概要](https://developer.adobe.com/commerce/php/development/components/indexing/)
