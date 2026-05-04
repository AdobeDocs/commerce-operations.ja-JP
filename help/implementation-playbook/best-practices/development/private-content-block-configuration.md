---
title: プライベートコンテンツブロックのベストプラクティス
description: ストアフロントのパフォーマンスを最適化するために、プライベートコンテンツブロックを設定するためのベストプラクティスを説明します。
role: Developer
feature: Best Practices
exl-id: a6d2f324-f9b9-4b2b-997f-36df02c37465
source-git-commit: f9a135fc63574ccbecd3f564a87fc5c4ac03f009
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# プライベートコンテンツブロックのベストプラクティス

プライベートコンテンツブロックに`_isScopePrivate`変数が含まれている場合、ブロックはキャッシュできません。 プライベートブロックはキャッシュされないため、Adobe Commerceは各カスタマーリクエストに対して同じデータを取得する必要があり、サーバーの負荷が増加します。

プライベートコンテンツに`_isScopePrivate`変数を使用する代わりに、ブロックとテンプレートを作成して、ユーザーに依存しないデータを表示します。 このデータは、Adobe Commerce UI コンポーネントによってユーザー固有のデータに置き換えられ、事前レンダリングのデータをより効率的に処理します。 手順については、_[!DNL Commerce PHP Extensions Guide]_&#x200B;の[&#x200B; プライベートコンテンツ &#x200B;](https://developer.adobe.com/commerce/php/development/cache/page/private-content/)を参照してください。

## 影響を受ける製品とバージョン

[&#x200B; サポートされているすべてのバージョン &#x200B;](../../../release/versions.md) /:

- Adobe Commerce on cloud infrastructure
- Adobe Commerce オンプレミス

## 潜在的なパフォーマンスへの影響

`_isScopePrivate`個の変数を含むプライベートコンテンツブロックを持つサイトは、AJAX リクエストをトリガーして、各カスタマーリクエストに対して同じデータを取得します。 これにより、レスポンス時間が増加し、顧客登録、ショッピングカートの更新、注文送信、支払いトランザクションなど、よりビジネスに不可欠なストアフロント業務を処理するために使用できる追加リソースが追加されます。

## 追加情報

- [プライベートコンテンツ](../../../performance/configuration.md#client-side-optimization-settings)
- _[!DNL Commerce PHP Extensions Guide]_&#x200B;の[&#x200B; キャッシュ可能ブロックとプライベートブロック &#x200B;](https://developer.adobe.com/commerce/php/development/cache/page/private-content/#cacheable-and-private-blocks)
