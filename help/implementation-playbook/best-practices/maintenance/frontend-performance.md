---
title: フロントエンドパフォーマンスの監査
description: Web パフォーマンスツールを使用してAdobe Commerceストアフロントの操作を監査することで、サイトのパフォーマンスに悪影響を与える問題を特定し、対処します。
role: Admin, User, Developer
feature: Best Practices
exl-id: bafae565-9d09-4cc0-8507-e89a11dbd915
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# フロントエンドパフォーマンスのベストプラクティス

Web パフォーマンスツールを使用して、Adobe Commerceストアのフロントエンドパフォーマンスを確認します。
これらのツールは、様々な指標を使用して、オンラインストアのパフォーマンスを向上させるための強力なインサイトとレコメンデーションを提供します。

## 影響を受ける製品およびバージョン

[サポートされているすべてのバージョン](../../../release/versions.md) /:

- Adobe Commerce an cloud infrastructure
- Adobe Commerceオンプレミス

## フロントエンドパフォーマンスの確認

Web サイトストアのフロントエンドパフォーマンスを確認するには：

1. 次のような Web パフォーマンスツールを使用して、フロントエンドパフォーマンスを監査します。

   - **[Google Lighthouse](https://web.dev/measure/)**—Lighthouse では、パフォーマンス、アクセシビリティ、プログレッシブ Web アプリ、SEO などの監査を実施しています。 Lighthouse を実行する様々な方法の詳細については、 [Lighthouse の概要](https://developer.chrome.com/docs/lighthouse/overview).)
   - **[Google PageSpeed Insights](https://pagespeed.web.dev/)**—PageSpeed Insights は、Web ページのパフォーマンスが低下する原因に関する詳細なレポートと、その修正方法に関する推奨事項をすばやく提供します。

1. 監査レポートを確認し、ストアのパフォーマンスを向上させるために提供された推奨事項を実装します。

## 追加情報

- [管理者ユーザー向けインデックス管理](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [CLI を使用したインデックス管理](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)
- [開発者向けのインデックス作成の概要](https://developer.adobe.com/commerce/php/development/components/indexing/)
