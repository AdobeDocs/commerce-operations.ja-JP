---
title: プライベートコンテンツブロックのベストプラクティス
description: ストアフロントのパフォーマンスを最適化するための、プライベートコンテンツブロックの設定に関するベストプラクティスについて説明します。
role: Developer
feature: Best Practices
exl-id: a6d2f324-f9b9-4b2b-997f-36df02c37465
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# プライベートコンテンツブロックのベストプラクティス

プライベートコンテンツブロックに `_isScopePrivate` 変数の場合、ブロックはキャッシュできません。 プライベートブロックはキャッシュされないので、Adobe Commerceは顧客のリクエストごとに同じデータを取得する必要があり、サーバーの負荷が高くなります。

を使用する代わりに `_isScopePrivate` 変数：プライベートコンテンツの場合は、ブロックとテンプレートを作成して、ユーザーに依存しないデータを表示します。 このデータは、Adobe Commerce UI コンポーネントによってユーザー固有のデータに置き換えられ、プリレンダリングのデータをより効率的に処理できます。 手順については、を参照してください [非公開コンテンツ](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) が含まれる _[!DNL Commerce PHP Extensions Guide]_.

## 影響を受ける製品とバージョン

[サポートされているすべてのバージョン](../../../release/versions.md) （件中）:

- クラウドインフラストラクチャー上のAdobe Commerce
- Adobe Commerce オンプレミス

## パフォーマンスへの潜在的な影響

を含むプライベートコンテンツブロックがあるサイト `_isScopePrivate` 変数は、各カスタマーリクエストに対して同じデータを取得するAJAX リクエストをトリガーします。 これにより、応答時間が長くなり、顧客登録、買い物かごの更新、注文の送信、支払いトランザクションなど、よりビジネスクリティカルなストアフロント操作を処理するのに使用できる追加のリソースが使用されます。

## 追加情報

- [非公開コンテンツ](../../../performance/configuration.md#client-side-optimization-settings)
- [スループットの高いAJAX リクエストが原因で、パフォーマンスが低下する](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.html)
