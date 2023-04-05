---
title: 非公開コンテンツブロックのベストプラクティス
description: ストアフロントのパフォーマンスを最適化するためのプライベートコンテンツブロックの設定に関するベストプラクティスについて説明します。
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---

# 非公開コンテンツブロックのベストプラクティス

非公開コンテンツブロックに `_isScopePrivate` 変数を使用する場合、ブロックはキャッシュできません。 プライベートブロックはキャッシュされないので、Adobe Commerceは顧客の要求ごとに同じデータを取得する必要があり、サーバーの読み込みが増加します。

を使用する代わりに、 `_isScopePrivate` 変数は、非公開コンテンツ用に、ユーザーに依存しないデータを表示するブロックとテンプレートを作成します。 このデータは、Adobe Commerce UI コンポーネントによってユーザー固有のデータに置き換えられ、このコンポーネントによって、レンダリング前のデータをより効率的に処理できます。 手順については、 [非公開コンテンツ](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) 内 _[!DNL Commerce PHP Extensions Guide]_.

## 影響を受ける製品およびバージョン

[サポートされているすべてのバージョン](../../../release/versions.md) /:

- Adobe Commerce an cloud infrastructure
- Adobe Commerceオンプレミス

## パフォーマンスへの影響の可能性

を含むプライベートコンテンツブロックを持つサイト `_isScopePrivate` 変数トリガーAJAXリクエストを使用して、各顧客リクエストに対して同じデータを取得します。 これにより、応答時間が増加し、顧客登録、買い物かごの更新、注文送信、支払いトランザクションなど、よりビジネスクリティカルなストアフロント操作を処理するために使用できる追加のリソースを使用します。

## 追加情報

- [非公開コンテンツ](../../../performance/configuration.md#client-side-optimization-settings)
- [高スループットのAJAXリクエストにより、パフォーマンスが低下する](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.html)


