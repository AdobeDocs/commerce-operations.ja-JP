---
title: プライベートコンテンツブロックのベストプラクティス
description: ストアフロントのパフォーマンスを最適化するための、プライベートコンテンツブロックの設定に関するベストプラクティスについて説明します。
role: Developer
feature: Best Practices
exl-id: a6d2f324-f9b9-4b2b-997f-36df02c37465
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 1%

---

# プライベートコンテンツブロックのベストプラクティス

プライベートコンテンツブロックに `_isScopePrivate` 変数が含まれている場合、ブロックはキャッシュできません。 プライベートブロックはキャッシュされないので、Adobe Commerceは顧客のリクエストごとに同じデータを取得する必要があり、サーバーの負荷が高くなります。

プライベートコンテンツに `_isScopePrivate` 変数を使用する代わりに、ユーザーに依存しないデータを表示するブロックとテンプレートを作成します。 このデータは、Adobe Commerce UI コンポーネントによってユーザー固有のデータに置き換えられ、プリレンダリングのデータをより効率的に処理できます。 手順については、_[!DNL Commerce PHP Extensions Guide]_&#x200B;の [ プライベートコンテンツ ](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) を参照してください。

## 影響を受ける製品とバージョン

[ サポートされているすべてのバージョン ](../../../release/versions.md):

- クラウドインフラストラクチャー上のAdobe Commerce
- Adobe Commerce オンプレミス

## パフォーマンスへの潜在的な影響

`_isScopePrivate` 変数を含むプライベートコンテンツブロックを持つサイトでは、AJAX リクエストをトリガーして、顧客リクエストごとに同じデータを取得します。 これにより、応答時間が長くなり、顧客登録、買い物かごの更新、注文の送信、支払いトランザクションなど、よりビジネスクリティカルなストアフロント操作を処理するのに使用できる追加のリソースが使用されます。

## 追加情報

- [非公開コンテンツ](../../../performance/configuration.md#client-side-optimization-settings)
- [ スループットの高いAJAX リクエストは、パフォーマンスの低下を引き起こします ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.html)
