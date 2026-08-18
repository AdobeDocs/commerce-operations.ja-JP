---
title: フロントエンドパフォーマンスの監査
description: web パフォーマンスツールを使用して、Adobe Commerceストアフロントの業務を監査することで、サイトパフォーマンスに悪影響を与える問題を特定し、対処します。
role: Admin, User, Developer
feature: Best Practices
exl-id: bafae565-9d09-4cc0-8507-e89a11dbd915
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
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
- [CLIを使用したインデックス管理](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)
- [開発者向けインデックス作成の概要](https://developer.adobe.com/commerce/php/development/components/indexing/)
