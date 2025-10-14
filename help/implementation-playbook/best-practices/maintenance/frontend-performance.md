---
title: フロントエンドパフォーマンスの監査
description: Web パフォーマンスツールを使用してAdobe Commerce ストアフロントの操作を監査することで、サイトのパフォーマンスに悪影響を与える問題を特定し、対処します。
role: Admin, User, Developer
feature: Best Practices
exl-id: bafae565-9d09-4cc0-8507-e89a11dbd915
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 1%

---

# フロントエンドパフォーマンスのベストプラクティス

Web パフォーマンスツールを使用して、Adobe Commerce ストアのフロントエンドパフォーマンスを確認します。
これらのツールでは、様々な指標を使用して強力なインサイトと推奨事項を提供し、オンラインストアのパフォーマンスを向上させます。

## 影響を受ける製品とバージョン

[&#x200B; サポートされているすべてのバージョン &#x200B;](../../../release/versions.md):

- クラウドインフラストラクチャー上のAdobe Commerce
- Adobe Commerce オンプレミス

## フロントエンドパフォーマンスの確認

Web サイトストアのフロントエンドパフォーマンスを確認するには：

1. 次のような web パフォーマンスツールを使用して、フロントエンドのパフォーマンスを監査します。

   - **[Google Lighthouse](https://web.dev/measure/)** - Lighthouse は、パフォーマンス、アクセシビリティ、プログレッシブ web アプリ、SEO などに関する監査を実施しています。 lighthouse を実行する様々な方法について詳しくは、[Lighthouse の概要 &#x200B;](https://developer.chrome.com/docs/lighthouse/overview)）を参照してください。
   - **[Google PageSpeed Insights](https://pagespeed.web.dev/)** - PageSpeed Insights では、web ページのパフォーマンスが遅くなる原因に関する詳細なレポートとその修正方法に関する推奨事項をすばやく提供します。

1. 監査レポートを確認し、提示される推奨事項を実装して、ストアのパフォーマンスを向上させます。

## 追加情報

- [管理者ユーザー向けのインデックス管理](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [CLI を使用したインデックス管理 &#x200B;](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html?lang=ja)
- [&#x200B; 開発者向けのインデックス作成の概要 &#x200B;](https://developer.adobe.com/commerce/php/development/components/indexing/)
