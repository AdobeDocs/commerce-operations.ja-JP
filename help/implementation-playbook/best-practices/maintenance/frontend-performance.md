---
title: フロントエンドパフォーマンスの監査
description: Web パフォーマンスツールを使用してAdobe Commerce ストアフロントの操作を監査することで、サイトのパフォーマンスに悪影響を与える問題を特定し、対処します。
role: Admin, User, Developer
feature: Best Practices
exl-id: bafae565-9d09-4cc0-8507-e89a11dbd915
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---

# フロントエンドパフォーマンスのベストプラクティス

Web パフォーマンスツールを使用して、Adobe Commerce ストアのフロントエンドパフォーマンスを確認します。
これらのツールでは、様々な指標を使用して強力なインサイトと推奨事項を提供し、オンラインストアのパフォーマンスを向上させます。

## 影響を受ける製品とバージョン

[サポートされているすべてのバージョン](../../../release/versions.md) （件中）:

- クラウドインフラストラクチャー上のAdobe Commerce
- Adobe Commerce オンプレミス

## フロントエンドパフォーマンスの確認

Web サイトストアのフロントエンドパフォーマンスを確認するには：

1. 次のような web パフォーマンスツールを使用して、フロントエンドのパフォーマンスを監査します。

   - **[Google灯台](https://web.dev/measure/)**—Lighthouse は、パフォーマンス、アクセシビリティ、プログレッシブ web アプリ、SEO などに関する監査を受けています。 lighthouse を実行する様々な方法について詳しくは、 [Lighthouse の概要](https://developer.chrome.com/docs/lighthouse/overview).）
   - **[Google PageSpeed インサイト](https://pagespeed.web.dev/)**—PageSpeed Insights は、web ページのパフォーマンスが遅くなる原因とその修正方法に関する推奨事項について、詳細なレポートをすばやく提供します。

1. 監査レポートを確認し、提示される推奨事項を実装して、ストアのパフォーマンスを向上させます。

## 追加情報

- [管理者ユーザー向けのインデックス管理](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [CLI を使用したインデックス管理](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)
- [開発者向けのインデックス作成の概要](https://developer.adobe.com/commerce/php/development/components/indexing/)
